# Git history verwijderen

Dit is een stappenplan om de git repository history te verwijderen. Hiermee worden alle branches en voorgaande commits verwijderd. Na het verwijderen beschik je over een nieuwe master branch met één initiele commit.

#### Stappenplan

1. Maak een nieuwe branch aan vanuit de commit of branch waar die de nieuwe initiele commit moet worden. Check na het toevoegen of alle bestanden en de folderstructuur zoals gewenst is.

```git
git checkout --orphan Init
git add -A  # Add all files and commit them
git commit -m "init"
```

2. Verwijder de oorspronkelijke masterbranch.

```git
git branch -D master  # Deletes the master branch
```

3. Wijzig de huidige branch naam naar master en forceer dat dit de nieuwe master branch wordt.

```git
git branch -m master  # Rename the current branch to master
git push -f origin master  # Force push master branch to github
```

4. Verwijderen alle andere branches in de repository

```git
git gc --aggressive --prune=all     # remove the old files
```

#### Voorbeeld resultaat in GitHub

Vooraf:

![alt text](https://github.com/Respectzorg/Documentatie/Images/git_history_verwijderen_01.png "Overzicht vooraf")

![alt text](https://github.com/Respectzorg/Documentatie/Images/git_history_verwijderen_02.png "Aantal vooraf")

Achteraf:

![alt text](https://github.com/Respectzorg/Documentatie/Images/git_history_verwijderen_03.png "Overzicht achteraf")

![alt text](https://github.com/Respectzorg/Documentatie/Images/git_history_verwijderen_04.png "Aantal achteraf")
