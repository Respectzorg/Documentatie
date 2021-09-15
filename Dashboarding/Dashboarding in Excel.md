# Dashboarding in Excel

Om dashboards te maken in excel is het handig om van de data connector functie gebruik te maken. Deze functionaliteit maakt het mogelijk om een Dashboard en een Brondata bestand aan te maken.

- Het Dashboard excel document bevat alle visualisaties, KPIs en filters.
- Het Brondata excel document bevat alle gegevens. Dit bestand zal doormiddel van scripting geupdate worden, waardoor altijd de meest recente informatie beschikbaar is.

### Het gebruiken van de Data Connector

Om gebruik te maken van de data connector moet het Brondata excel bestand al beschikbaar zijn.

##### Stappenplan

1. Klik binnen Excel op het `Data` tab.
2. Klik in de linke bovenhoek van de menu balk op `Get Data`
3. Selecteer `From file` en vervolgens `From Workbook`
4. Navigeer naar de locatie van het Brondata excel bestand en open deze.
5. Selecteer de tabellen met de gegevens die je wilt tonen in het Dashboard.
6. Klik op Load

Je hebt nu een datamodel binnen Excel dat je kan verversen. Het datamodel kan je koppelen aan Filters en Charts.

### Het gebruik van Pivot Charts

Om interactiviteit te bieden zijn pivot charts nodig. Na het aanmaken kunnen filters / slicers toegepast worden.

##### Stappenplan

1. Klik binnen Excel op het `Insert` tab.
2. Klik in het midden van de menu balk op de pijl van `PivotChart`.
3. Klik op `PivotChart & PivotTable`.
4. Selecteer `Use this workbook's Data Model` en klik op `OK`.
5. Sleep de gewenste data naar de velden eronder. Alle aanpassingen worden gevisualiseerd weergegeven. Maak aanpassingen totdat je de gewenste grafiek hebt.

### Het gebruik van filters, slicers en timeline

Om alleen gewenste informatie overzichtelijk weer te geven is het voor de gebruiker van belang om selecties te kunnen maken. Hiervoor zijn filters zoals een slicer of timeline bedoeld.

##### Stappenplan

1. Selecteer je PivotChar en anders je PivotTable om de tab `PivotChart Analyze` weer te geven.
2. Klik op tab `PivotChart Analyze`.
3. Klik in de menu balk onder het kopje Filter op `Insert Slicer` of `Insert Timeline`.
