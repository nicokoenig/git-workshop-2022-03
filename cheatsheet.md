# Git Cheatsheet

## Setup von Git

### Namen in Config setzen

```sh
git config --global user.name "Dein Name"
```

### Email in Config setzen

```sh
git config --global user.email "deinname@email.com"
```

### Gesetzte Werte aus der Config anzeigen

```sh
git config --global --list
```

## Repository erstellen

### Neues Repository auf eigenem Rechner erstellen

> Erstellt im aktuellen Ordner ein neues lokales Repository ⚠️

```sh
git init
```

### Existierended Repository auf lokalen Rechner clonen

```sh
```

## Grundbefehle im täglichen Umgang mit Git

### Status den lokalen Repositories ermitteln

```sh
git status
```

Der Status Befehlt teilt uns mit
- Aktueller Branch
- Gibt es Unterschiede zwischen Remote und Lokalem Repository
- Info über untracked Changes
- Info über gestagete Changes

### Untracked Changes auf Index setzen

```sh
git add <filespec>
```

Filespec kann sein
- `.` für alle Dateien im Ordner
- `*` für alle Dateien im Ordner
- konkreter Dateiname z.B. `datei.xxx`

### Tracked Change vom Index entfernen

> Konsole gibt Hinweis wie man das macht, nachdem `git status` eingegeben wurde.

```sh
git reset -- <filespec>
# git restore --stage <file>
```

### Dateien auf Index committen

```sh
git commit -m "message"
# git commit --message "message"
```

> Wenn `-m` vergessen wird, öffnet sich der Default-Editor um Commit Message einzugeben.

### Lokal den aktuellen Branch umbenennen

> Wichtig, sobald Branches auf einen Remote gepusht wurden, birgt das lokale Umbenennen großes Fehlerpotential ⚠️

```sh
git branch -m <neuerName>
```

## Branching and Merging mit Git

### Neuen lokalen Branch erstellen

> Erstellt neuen Branch (abbiegend vom aktuellen Branch + HEAD)

```sh
git branch <branchName>
```

### Zu anderem Branch wechseln

```sh
git checkout <branchName>
```

### Zu anderem Branch wechseln und diesen gleichzeitig erstellen, wenn dieser noch nicht existiert

```sh
git checkout -b <branchName>
```

## Remotes verwalten

### Existierende Remote Verbindungen anzeigen

```sh
git remote
git remote -v
```

### Neuen Remote hinzufügen

```sh
git remote add <name> <url>
```

### Alten Remote löschen

```sh
git remote remove <name>
```

## Synchronisation zwischen lokalem Repository und Remote Repository

### Lokale Commits für aktuellen Branch nach Remote synchronisieren

```sh
git push
```

### Änderungen des Remote Repository in lokales Repository synchronisieren

```sh
git pull
```

### Upsteam Branch setzen

```sh
# Bei git pull
git pull <origin> <origin-branch>

# Bei git push
git push -u <origin> <origin-branch>
```

## Konflikte

### Szenario

- Wir start von `main` Branch und erzeugen neuen Feature Branch
- Arbeiten auf Feature Branch und machen Commits

> In der zwischenzeit gibt es einen neuen Commit mit Konflikt auf Eltern-Brach (`main`) auf GitHub

> Die Änderungen von GitHub sind uns lokal nicht bekannt

- Feature Branch wird nach GitHub gepusht
- Auf GitHub Pull Request wird geöffnet

> Pull Request weißt mich auf Konflikte hin

Folgende Möglichkeiten
1. Auflösungen des Konflikts auf GitHub in der Oberfläche
  - Nachteil: ich kann das Gelöste nicht testen
  
> Außer: Die CI ist entsprechend konfiguriert

2. TLDR: Pullen den Ziel-Branch lokal und mergen diesen in den Feature Branch
  - `git checkout main` und pullen --> Alle letzten Änderungen des Main von Remote auch lokal verfügbar
  - Wechseln zurück in den Feature Branch --> `git checkout <feature-branch>`
  - Mergen der neuen Commits von main nach feature Branch --> `git merge main` bzw. Names des Hauptbranches
  - Konflikt auflösen
  - Die Dateien die Konflikte enthalten haben mit `git add` hinzufügen
  - Merge Commit machen --> `git commit -m 'merge message'`
  - Push des Feature Branches in Richtung GitHub
  - Pull Request nochmal prüfen und mergen (die Änderungen übernehmen)

    
## Sonstige Befehle

### git stash

Mit `git stash` werden die aktuellen Änderungen auf Index weggespeichert.

Gut um schnell irgendwo ein Feuer zu löschen.

Mit `git stash pop` werden die zuvor gestashten Änderungen wieder "geholt".

> git stash kann auch benannt werden, so das man verschiedene gespeicherte Stapel hat.

### git reset

`git reset <commithash>` kann genutzt werden auf einen alten Commit zurückzuspringen.

Alle seit dem gemachten Änderungen sind nicht verloren, sondern werden als aktuelle Änderungen angezeigt

> `git reset HEAD~n`kann eingesetzt werden um n commits in zurückzusetzen, z.B. `git reset HEAD~1` geht einen Commit zurück

### git tag

`git tag <tageName>` kann Tags (label, releaes, markierungen) erzeugen.

Diese müssen mit gepusht werden --> `git push --tags`

## Git Ignore

die Datei `.gitignore` kann im Root des Repositories hinterlegt werden.

Diese gibt dann an, welche Dateien grundsätzlich nicht über git getracked werden sollen.

https://www.atlassian.com/de/git/tutorials/saving-changes/gitignore






