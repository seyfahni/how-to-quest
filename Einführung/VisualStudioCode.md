# Inhalt

[[_TOC_]]

# Allgemein

Rahasia verwendet zum Skripten von Quest die Entwicklungsumgebung Visual Studio Code. Im Folgenden wird nun darauf eingegangen, wie ihr Visual Studio Code einrichtet und verwendet.

Zunächst solltet ihr euch [Visual Studio Code](https://code.visualstudio.com/) (VSC) herunterladen und installieren.
Parallel dazu lade dir [Git](https://git-scm.com/downloads) herunter und installiere es ebenfalls.

# Einrichten

1. Einrichtung von GitLab
    1. Hinzufügen eines SSH Keys.
       Prüfe hierzu zunächst ob du bereits einen SSH key Besitzt, dazu gehst du in dein Benutzerverzeichnis auf deinem PC und navigierst in den Ordner `.ssh` Ordner und suche nach einer Datei mit der endung `.pub`. Ist der Ordner oder die Datei nicht vorhanden, So müssen wir diese nun erstellen.  
       Um einen ssh Key zu erstellen, mache einen Rechts Klick in einem beliebigen Ordner und klick auf `Git Bash Here`. Führe nun entweder `ssh-keygen` aus(lasse dabei das Passwort, nach dem du gafragt wirdt leer) oder wenn du ihn mit Passwort möchtest führe `ssh-keygen -o` aus(ein Passwort muss jedes mal eingegeben werden, wenn du `pull` oder `push` machst).  
       Wenn die Datei bereits existierte oder du sie nun erstellt hast, öffne die Datei mit der Endung `.pub`. Den inhalt aus dieser Datei kopierst du nun aus diese Seite https://gitlab.com/-/profile/keys und gebe dem Key noch einen aussagekräftigen Namen(z.B. `PC-Privat`).
    2. Importieren des Projektes in VSC
       Schließe in VSC alle Dateien und Ordner, die du offen hast. Nun wechsle an der Linken Seite in den Tab `Source Control` und Klicke auf `Clone Repository`. Nun kopiere von GitLab die SSH URL, diese findest du auf der Startseite des entsprechenden Repositories oben rechts wenn du auf `Clone` klickst. hast du die URL in VSC eingefügt und Enter gedrückt, wähle einen Ordner, in dem du zukünftig arbeiten willst.
    3. Nun kannst du den Ordner in VSC öffnen
2. Git User Name und E-Mail Adresse
   Mache einen Rechts Klick in einem beliebigen Ordner und klick auf `Git Bash Here`. Nun gebe diese beiden Befehle ein und ersetze deinen Namen und dein E-Mail adresse.  
  `git config --global user.name "USER_NAME"`  
  `git config --global user.email "E-MAIL_ADDRESS"`
3. VSC einrichten addons
    1. navigiere in den Tab `Extensions` und installiere die beiden Erweiterungen
    2. `BetonQuest Code Snippets` Dieses fügt eine Autovervollständigung für BQ hinzu.
    3. `Live Share` Ermöglicht es in Echtzeit zusammen zu arbeiten.
    4. `File Sync` Ermöglicht es z.B. deinen Test Server für einzelne oder alle Quests synchron mit dem Repository zu halten

# VSC und Git

Zunächst solltet ihr den Wikieintag zu [GitLab](/Einführung/GitLab) gelesen und verstanden haben, um ein sinnvolles und korrektes arbeiten mit Git durchzuführen. Im Folgenden wird nämlich nur beschrieben, wie in VSC Git verwendet wird, jedoch nicht wie Git funktioniert oder eingesetzt wird.

Alle zu Git gehörigen Aktionen findest du im `Source Control` Tab.  
![Git](https://cdn.discordapp.com/attachments/520942709205237760/795019473161682954/unknown.png)
Mit dem harken kannst du deine Änderungen `committen` Hier kannst du, wenn du dies das erste mal macht auch auch permanent den `stash` schritt überspringen. Wenn du nun Das ganze hochlädst, gib dem ganzen noch eine aussagekräftige Beschreibung, was du geändert hast.  
Alle weiteren Aktionen findest du unter den drei Punkten. Die Aktionen darin solltest du aus dem Git Artikel kennen.