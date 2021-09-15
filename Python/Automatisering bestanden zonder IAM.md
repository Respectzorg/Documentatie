# Automatisering bestanden zonder IAM

Dit document is voor het automatiseren van use cases die inzichten verschaffen m.b.v. excel of andere bestanden. Documenten die geupdate inzicht verschaffen zonder Identity and Access Management (IAM) functionaliteit. Meestal zijn dit inzichten die niet via een BI-tool gedeelt worden.

Hiervoor heb je het volgende nodig:

- Een scheduler die scripts aanroept.
- Een script die data ophaalt, verwerkt en in een document opslaat.
- Een script die het document deelt via de mail.

##### Schedulers opties

- Windows Task Scheduler
- [Python module schedule](https://pypi.org/project/schedule/)
- [Luigi scheduler](https://luigi.readthedocs.io/en/stable/central_scheduler.html)
- [Apache Airflow](https://airflow.apache.org/docs/)

##### Data Processing script

Use case specifiek script. Aanbevolen om met behulp van Jupyter notebooks het script uit te schrijven en vervolgens met de volgende command in een terminal te converten naar een python bestand.

`jupyter nbconvert --to script <bestandsnaam>`

In de productie omgeving wil je dat een python bestand gerunt wordt.

##### Bestanden delen via de mail

Zie [hier](Mailen via Outlook SMTP.md).
