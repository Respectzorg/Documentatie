## Extra: Lessons learned - Docker & Azure

Initiëel zouden de use cases geautomatisserd worden via de interne servers. Omdat Docker niet goed met Hyper-V op Windows Server 2019 met elkaar kan communiceren werd gekozen om Azure te verkennen als alternatieve oplossing. Dit kent echter ook zijn uitdagingen die gezamelijk met verkende services in dit document worden beschreven.

#### Verkende reousources in Azure

- Container Registry
- Container Instances
- Key Vault

#### Container Regristry

Voor de automatiseering in Azure wordt gebruik gemaakt van Docker. Om instances gemakkelijk in de cloud aan te kunnen maken bestaat de Container Registry service. Hier kunnen docker images in gepubliceerd worden om bij de Container Instances service selecteerdbaar te maken. De officiele documentatie bied voldoende en heldere uitleg om dit te doen.

https://docs.microsoft.com/en-us/azure/container-instances/container-instances-using-azure-container-registry

Hierbij wordt bij de limitaties aangegeven dat je niet direct gebruik kan maken van de IAM die Azure aanbied. Er is wel een preview functie rondom `managed identities`. Hierdoor kan je wel vanuit een Docker Container die in het container registry zit toegang vragen vanuit de Azure Key Vault.

#### Container Instances

Azure Container Instances zijn Docker containers die opgestart kunnen worden vanuit de Azure Container Registry.

##### Aanmaken

Een nieuwe aanmaken is een eenvoudig proces vanuit de portal. Stap 6 en 7 zijn alleen nodig als je gebruik wilt maken van Azure Key Vault:

1. Klik op de knop `maken` aan de linke kant in de menu balk.
2. Kies een Resourcegroep of maak een nieuwe aan.
3. Geef je container een naam.
4. Selecteer bij `Bron van installatiekopie` de `Azure Container Registry`.
5. Selecteer je register waar het docker container in staat en bijbehorende image die je wilt draaien.
6. Als je moet communiceren met de Azure Key Vault ga dan eerst naar het tab `Gevananceerd` voordat je verder gaat.
7. Hier kan je environment variabelen aan de container meegeven. In het geval van Azure Key Vault wil je hier de `VAULT_URL` meegeven en als beveiligd markeren.
8. Afsluitend klik je op `Beoordelen en maken`.

##### Managed identities

Om `managed identities` aan te zetten moet je de container instance openen in de portal en bij Identiteit de status op `aan` zetten.

##### IP adres

Alleen Container Instances die runnen bezitten een IP adres. Om met de lokale ONS database van Respect te kunnen communiceren zal deze gewhitelist moeten worden. Dit is daarentegen niet wenselijk omdat het IP adres elke keer als de container opnieuw opgestart wordt een nieuw IP adres toegewezen krijgt.

Om een static IP adres te krijgen of een VPN op te zetten kan je gebruik maken van Azure Virtual Network. Nadeel is dat Managed Identities niet ondersteund worden als Container Instances in het Virtual Network draaien. Zie [Virtual Network documentatie](https://docs.microsoft.com/en-us/azure/container-instances/container-instances-virtual-network-concepts).

#### Azure Key Vault integratie met Azure Container Instances

Voor de veiligheid zullen gegevens zoals wachtwoorden, username en server adressen niet in de container opgeslagen worden, maar in de Azure Key Vault.

Volledig stappenplan met Azure CLI image als voorbeeld staat [hier](https://docs.microsoft.com/en-us/azure/container-instances/container-instances-managed-identity) uitgelegd.

**Belangrijk:** Het stappenplan doet lijken dat je in moet loggen met je container in de Azure CLI. Dat is niet nodig! Je moet wel `managed identities` in je container instance aanzetten. Daarna kan je in de Azure Key Vault onder het kopje `Toegangsbeleid` de identity id of naam van de container toevoegen.

### Docker & Azure integration

##### Docker

Je kunt vanuit je CMD docker images builden in Azure. Hiervoor heeft Docker `context` nodig. Dit doe je als volgt;

1. Voer in CMD in `docker login azure`
2. Login in Azure via de browser
3. Voer in CMD in `docker context create aci <naam_context>`

##### VS Code

Daarnaast bied VS Code ook een gemakkelijke interface waar je images kunt builden en deployen in Azure nadat je bent ingelogd. Hiervoor heb je het volgende nodig:

- Docker extention
- Azure CLI

Na installatie gebruik de Azure CLI met het volgende commando: `az login`. Log vervolgens in via de browser. Binnen de Docker Extentie in VS Code zie je nu je registries en images.

Als je in de context van je locale machine zit, dan heb je meer opties dan als je in de context van Azure zit.

Je interacteert in VS Code extentie door rechts te klikken op de registry of image. Je ziet vervolgens de opties die je ter beschikking hebt.
