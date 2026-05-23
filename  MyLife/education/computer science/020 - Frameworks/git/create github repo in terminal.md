---
id: "create github repo in terminal"
aliases:
Topic:
Related:
Tags:
  - w
Date:
Updated:
Source:
---
# create github repo in terminal

Ja, das kannst du! Dein Fehler passiert, weil `git remote add` nur eine "Verknüpfung" in deinem lokalen Ordner erstellt. GitHub weiß davon aber noch nichts – für GitHub existiert das Repository einfach noch nicht, deshalb sagt er `not found`.

Um ein Repository zu erstellen, ohne den Browser zu öffnen, hast du zwei Möglichkeiten:

### 1. Der Profi-Weg: GitHub CLI (`gh`)

Das ist das offizielle Tool von GitHub für genau diesen Zweck. Falls du es noch nicht hast, installiere es kurz:

`brew install gh`

Danach machst du einfach das hier in deinem Ordner:

1. **Einloggen:** `gh auth login` (Musst du nur einmal machen).
    
2. **Repo erstellen:**
    
    Bash
    
    ```
    gh repo create 3d-cube-cpp --public --source=. --remote=origin --push
    ```
    

**Was dieser Befehl macht:**

- Erstellt das Repo auf GitHub unter deinem Namen.
    
- Setzt die Sichtbarkeit auf öffentlich (`--public`).
    
- Verknüpft deinen lokalen Ordner (`--source=.`).
    
- Setzt den Remote Namen (`--remote=origin`).
    
- Pusht direkt deinen ersten Commit (`--push`).
    

---

### 2. Der "Quick & Dirty" Weg: API mit `curl`

Wenn du kein extra Tool installieren willst, kannst du GitHubs API direkt ansprechen. Du brauchst dafür aber ein **Personal Access Token (PAT)** von GitHub.

Bash

```
curl -u "Goldinyan" https://api.github.com/user/repos -d '{"name":"3d-cube-cpp"}'
```

_(Danach wirst du nach deinem Passwort/Token gefragt. Wenn das Repo erstellt ist, funktioniert dein `git push -u origin main` sofort.)_

---

### Warum dein aktueller Versuch gescheitert ist:

Git selbst (das Programm in deinem Terminal) hat keine Berechtigung, auf GitHub einfach Dinge zu _erstellen_. Es kann nur Daten in bereits _existierende_ Container hochladen oder von dort ziehen. `git remote add` ist im Grunde nur ein Eintrag in einer Textdatei innerhalb deines `.git` Ordners, der sagt: _"Wenn ich 'origin' sage, meine ich diese URL"_.

**Mein Tipp:** Installier dir `gh`. Wenn man viel mit Yabai/skhd und im Terminal arbeitet (so wie du), ist das GitHub CLI ein absoluter Gamechanger für den Workflow.

Versuch mal den `gh repo create` Befehl, das spart dir in Zukunft extrem viel Zeit!