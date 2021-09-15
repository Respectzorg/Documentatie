# Mailen via Outlook SMTP

Met behulp van modules [email](https://docs.python.org/3/library/email.html) en [smtplib](https://docs.python.org/3/library/smtplib.html#module-smtplib) is het mogelijk om mails te versturen via een python script. Generelle code is [hier](https://cppsecrets.com/users/76261101011049746107111110100100117114117504964103109971051084699111109/Python-SMTP-Steps-to-Send-Mail-with-attachments-using-SMTP-smtplib.php) uitgeschreven en uitgelegt.

Om deze code bruikbaar te maken voor Respect zullen er wat wijzigingen nodig zijn:

1. Sla nooit login gegevens op in een code bestand. Maak gebruik van key vaults (bijv. Azure Key Vault), environment variables of configuration files (bijv. yaml). In het gebeval van configuration files horen deze toegevoegd te worden aan de gitignore.
2. In de generelle code wordt een gmail adres gebruikt, deze moet met de servers van google communiceren. In het geval van Respect wil je met de servers van Outlook praten. Controleer de volgende gegevens in de code:

```python
server = "smtp.office365.com"
port   = 587
```

Een voorbeeld voor een uitgewerkte versie voor Respect is [hier](https://github.com/Respectzorg/Extramuraal-Personeelplanning/blob/master/Code/Deployment/mail.py) te vinden.

### Attachments

Om bestanden toe te voegen aan je mail moet je gebruik maken van MIME (Multipurpose Internet Mail Extentions). Kijkende naar de generelle code, dan is deze code snippet ervoor verantwoordelijk:

```python
attach_file_name = 'path/to/file.pdf'
attach_file = open(attach_file_name, 'rb') # Open the file as binary mode
payload = MIMEBase('application', 'octate-stream')
payload.set_payload((attach_file).read())
encoders.encode_base64(payload) #encode the attachment
#add payload header with filename
payload.add_header('Content-Decomposition', 'attachment', filename=attach_file_name)
message.attach(payload)
```

In het geval dat je meerdere files wilt toevoegen kan je meerdere payloads attachen. Maak bijvoorbeeld een list met paths aan waar je doorheen loopt. In het uitgewerkte [voorbeeld](https://github.com/Respectzorg/Extramuraal-Personeelplanning/blob/master/Code/Deployment/mail.py) voor Respect is dit het volgende code snippet:

```python
files = ['path/to/file_A.xlsx', 'path/to/file_B.xlsx']
if len(files) > 0: # Check if there are files
    for path in files:
        part = MIMEBase('application', "octet-stream")
        with open(path, 'rb') as file:
            part.set_payload(file.read())
        encoders.encode_base64(part)
        part.add_header(
            'Content-Disposition',
            'attachment; filename="{}"'.format(Path(path).name)
        )
        msg.attach(part)
```
