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

![alt text](https://raw.githubusercontent.com/Respectzorg/Documentatie/main/Images/git_history_verwijderen_01.png?token=AQEYP3JH7CQDEHUGKEH4HTLA3LYCG "Overzicht vooraf")

![alt text](https://raw.githubusercontent.com/Respectzorg/Documentatie/main/Images/git_history_verwijderen_02.png?token=AQEYP3MKQYY3BNQDBVU7OTTA3LYGC "Aantal vooraf")

Achteraf:

![alt text](https://raw.githubusercontent.com/Respectzorg/Documentatie/main/Images/git_history_verwijderen_03.png?token=AQEYP3L25ZTWH3XUNCUDQ4TA3LYIA "Overzicht achteraf")

![alt text](https://raw.githubusercontent.com/Respectzorg/Documentatie/main/Images/git_history_verwijderen_04.png?token=AQEYP3KSGOIMF2VATZK6ZJDA3LYJI "Aantal achteraf")

##### Sources

- Code:
  https://stackoverflow.com/questions/9683279/make-the-current-commit-the-only-initial-commit-in-a-git-repository/13102849#13102849
- Betekenis ` --orphan`:
  https://stackoverflow.com/questions/19980631/what-is-git-checkout-orphan-used-for/19981375
