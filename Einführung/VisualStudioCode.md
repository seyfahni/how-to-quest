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
2. VSC einrichten addons
    1. navigiere in den Tab `Extensions` und installiere die beiden Erweiterungen
    2. `BetonQuest Code Snippets` Dieses fügt eine Autovervollständigung für BQ hinzu.
    3. `Live Share` Ermöglicht es in Echtzeit zusammen zu arbeiten.
    4. `File Sync` Ermöglicht es z.B. deinen Test Server für einzelne oder alle Quests synchron mit dem Repository zu halten

# Eclipse und GitLab

Zunächst solltet ihr den Wikieintag zu [GitLab](/Einführung/GitLab) gelesen und verstanden haben, um ein sinnvolles und korrektes arbeiten mit Git durchzuführen. Im Folgenden wird nämlich nur beschrieben, wie in Eclipse Git verwendet wird, jedoch nicht wie Git funktioniert oder eingesetzt wird.

Alle zu GitLab gehörenden Funktionen findet ihr, wenn ihr auf das entsprechende Projekt einen Rechtsklick ausführt und dann in den Unterpunkt Team Navigiert. Hier findet ihr nahezu alles, was wir zum Arbeiten brauchen, auch wenn es noch mehr Funktionen gibt. Ich werde jetzt nur die wichtigen und für unseren nutzen notwendigen Funktionen erklären.
## Projekt Übersicht  
   ![Projekt](https://cdn.discordapp.com/attachments/520955035832811521/613702467045163027/unknown.png)  
   Hier steht zuerst der Projektname.  
   In der eckigen Klammer könnt ihr dann zuerst das Repository sehen und dann in welchem Branch ihr seid.