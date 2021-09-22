# Personeelsplanning EMZ

Deze documentatie is voor de [Personeelplanning EMZ repository](https://github.com/Respectzorg/Extramuraal-Personeelplanning).

Voor de extramurale personeelsplanning wordt een Excel bestand gegenereerd met het aantal zorgminuten die in de planning staan. Hierdoor heb je de verwachte inzet en kan je beter inschatten hoeveel zorgmedewerkers nodig zijn.

Het overizcht is per team en zorgarragement ingedeelt.

De zorgminuten zijn opgeteld per team, zorgarragement en dagdeel. Een dagdeel is 1/4 van de dag verdeeld in ochtend, middag, avond en nacht. Dagdelen van maandag t/m zondag zijn beschikbaar in hetzelfde overzicht.

![Afbeelding van het Excel bestand](https://raw.githubusercontent.com/Respectzorg/Documentatie/main/Images/personeelsplanning_emz_excel_01.png?token=AQEYP3JH7CQDEHUGKEH4HTLA3LYCG "Afbeelding van het Excel bestand")

In totaal worden drie bestanden gegenereerd:

- All: Betekend dat zorgminuten van alle clienten opgeteld worden.
- Available: Betekend dat alleen zorgminuten van beschikbare clienten worden opgeteld.
- Users: Het aantal van alle clienten is opgeteld i.p.v. het aantal zorgminuten.

## Automatisering

Het wordt geautomatiseerd hoe dat [hier](https://github.com/Respectzorg/Documentatie/blob/main/Python/Automatisering%20bestanden%20zonder%20IAM.md) beschreven is. Het programma wordt gehost in [Azure via Docker images](https://github.com/Respectzorg/Documentatie/blob/main/Azure/Lessons%20Learned%20-%20Automatisering.md).

Hierbij is `scheduler.py` het script dat om de maand `Roosterplanning_EM_Moves.py` aanroept. `Roosterplanning_EM_moves.py` wordt gegenereerd binnen de `Docker/Dockerfile.txt` van `Roosterplanning_EM_moves.ipynb`. Als `Roosterplanning_EM_moves.py` aangeroepen is, haalt dit bestand alle benodigde gegevens op en verwerkt deze. Nadere uitleg over de verwerking is in [code](https://github.com/Respectzorg/Extramuraal-Personeelplanning/blob/master/Code/Deployment/Roosterplanning_EM_Moves.ipynb) zelf te vinden.

De gegenereerde bestanden worden in de `Output` folder geplaatst en zijn te herkennen aan de volgende naamgevening:

```
<jaar>-<maand>-<dag>_care_arragements_all.xlsx
<jaar>-<maand>-<dag>_care_arragements_available.xlsx
<jaar>-<maand>-<dag>_care_arragements_users.xlsx
```

Het is de bedoeling dat het excel overzicht maandelijks via de mail verstuurd wordt naar de roosterplanning. Hiervoor wordt gebruik gemaakt van [Mailen via Outlook SMTP](https://github.com/Respectzorg/Documentatie/blob/main/Python/Mailen%20via%20Outlook%20SMTP.md).
