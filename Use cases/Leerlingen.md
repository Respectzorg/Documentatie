# Leerlingen inzichten

Leerlingen use bevat twee notebook met alle grafieken die gebruikt zijn om inzichten te verschaffen rondom leerlingen. De notebooks zijn in de Data Exploration map te vinden i.p.v. de Deployment omdat deze use case nog niet geautomatiseerd is.

De grafieken kunnen ververst worden als het bestand `In- en Uitstroom Leerlingen.xlsx` in de folder `Sample_Data` ververst wordt.

De grafieken worden in dit document beschreven maar niet weergegeven omdat het gevoelige persoonsgebonden informatie kan bevatten.

### Grafieken overzicht:

- Duur in dienst van huidige leerlingen
- Duur in dienst van leerlingen met volledig dienstverlening
- Leeftijds histogram van lange, medium en korte dienstverleningen
- Aantal van reden uitstroom per dienstverlening lengte
- Instroom en uitstroom over de tijd
- Percentage niveau te hoog bij leerlingen per opleider/opleiding
- Piechart verdeling opleidingen
- Slagingspercentages

#### Duur in dienst van huidige leerlingen

- Een long tail distribution. De meeste leerlingen die nog in dienst zijn, zijn relatief kort in dienst t.o.v. de leerlingen die het langst in dienst zijn.
- De meeste clienten zijn tussen 300 en 400 dagen in dienst.
- De meest lange dienstverlening die nog actief is is meer dan 1400 dagen lang.

#### Duur in dienst van leerlingen met volledige dienstverlening

- Kijkende naar de distributie dan zijn drie plateaus te herkennen.
  - rond 1100 dagen
  - rond 300 dagen
  - rond 100 dagen
- Door het stijlste punt tussen de plateaus te kiezen als segmentatie krijg je dienstverleningen van lange, medium en korte duur.

#### Leeftijds histogram van lange, medium en korte dienstverleningen

- Bij Leerlingen met lange dienstverleningen en medium diensverleningen zijn de meeste leerlingen tussen 22 en 30 jaar oud.
- Bij Leerlingen met een korte dienstverlening zijn de meeste leerlingen 20 jaar oud.
- Bij Leerlingen met korte dienstverlening neemt de hoeveelheid leerlingen die ouder zijn dan 30 sterk af.
- Bij Leerlingen met een lange en medium dienstverlening neemt de hoeveelheid leerlingen die ouder zijn dan 30 langzaam af.

#### Aantal van reden uitstroom per dienstverlening lengte

- _Diploma_ is de meest genoemde hoofdreden van uitstroom.
- _Niveau te hoog_ is op één na meest genoemde hoofdreden van uitstroom, wel ca. 1/4 minder vaak voorkomend dan _Diploma_
- Opvallend dat leerlingen met een korte dienstverlening relatief veel leerlingen bevat die _Niveau te hoog_ noemen t.o.v. leerlingen met een lange dienstverlening. Het tegenovergestelde is te zien bij hoofdreden _Diploma_.
- De overige reden komen dermaten weinig voor dat deze te verwaarlozen zijn.

#### Instroom en uitstroom over de tijd

- Er is aanzienlijk meer Instroom dan leerlingen die Uitstroomen of een Diploma behalen. Dit is logisch gezien leerlingen pas jaren na instroom een diploma kunnen behalen.
- Uitstroom in 2020 is erg hoog i.v.m. jaren ervoor kijkende naar totale aantallen. In verhouding met Instroom is de evenredig gestegen.

#### Percentage niveau te hoog bij leerlingen per opleider/opleiding

- Als je kleine getallen buiten beschouwing houdt, dan zie je dat HBO-V en MZ de moeilijkste opleidingen zijn, gezien deze het hoogste percentage _Niveau te hoog_ hebben.
- Kijkende naar opleider, dan is het hoogste percentage _Niceau te hoog_ bij Albeda en de Haagse Hogeschool.
- Als je opleiding en opleider combineert, dan scoort opleider Albeda met opleiding MZ en opleiding Helpende het hoogst waar leerlingen stoppen die aangeven dat het _Nivecau te hoog_ is.

#### Piechart verdeling opleidingen

- De meest voorkomende opleiding is VIG met 46% gevolgd door Helpende Plus (14%), Helpende (12%) en Werkbegeleiding (10%).
- VIG, Helpende Plus en Werkbegeleiding vormen hiermee 82% van alle opleidingen bij Respect.

#### Slagingspercentages

- Vrouwen (n=23) slagen aanzienlijk vaker dan mannen (n=293). 71% bij vrouwen vs 48% bij mannen. Hierbij zijn alleen leerlingen opgenomen die niet meer operationeel zijn. Diegene die nog operationeel zijn, zijn per definitie niet geslaagd en misvormt het beeld als je de totale populatie van leerlingen pakt.
