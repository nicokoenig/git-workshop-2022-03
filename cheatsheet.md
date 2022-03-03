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












