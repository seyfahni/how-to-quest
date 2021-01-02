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
    2. `BetonQuest Code Snippets` addon. Dieses fügt eine Autovervollständigung für BQ hinzu.
    3. `Live Share` addon. Ermöglicht es in Echtzeit zusammen zu arbeiten.

# FileSync einrichten

FileSync hält euren Testserver auf dem aktuellen stand. Einmal eingerichtet, müsst ihr eure Quests nicht mehr zwischen Eclipe und eurem Testserver hin und her kopieren. Dazu müsst ihr zuvor eure [Testumgebung](/Einführung/Testumgebung) eingerichtet haben.  
1. Rechtsklick auf euer Projekt und ganz unten auf "Properties" klicken
2. Setze einen harken bei "Enable FileSync builder for project"
3. Klicke auf "Add Folder..." nun hast du mehrer Möglichkeiten, ich empfehle die folgende:
   - Setze den Harken für das ganze Projekt und klicke auf "OK"
   - Klappe das Projekt auf, und editiere "Excluded: "
   - Klicke im unteren Bereich "Exclusion patterns" auf "Add Multiple..."
   - Nun wähle alle folgenden Einträge aus, indem du "STRG" gedrückt hältst und bestätige mit "OK":
      - ".settings"
      - "#Template"
      - ".gitignore"
      - ".project"
4. Bestätige erneut mit "OK"
5. Nun Navigiere unten in "Default target folder:" zu deinem Test Server und dann "\Quest Server\plugins\BetonQuest"
6. Bestätige mit "Apply and Close"

# Testumgebung in Eclipse starten

Hier erklären wir, wie ihr aus Eclipse heraus, eure [Testumgebung](/Einführung/Testumgebung) startet. Diese solltest ihr zuvor eingerichtet haben. Sinn macht dies hier nur, wenn ihr zuvor FileSync eingerichtet habt.  
1. Klicke auf den Pfeil das Rechte Symbol in Eclipse ![Ison](https://cdn.discordapp.com/attachments/520955035832811521/619116310323789864/unknown.png)
2. Klicke auf "External Tools Configurations..."
3. Mache einen Doppelkick auf "Program"
4. Gib deiner Konfiguration einen Namen wie z.B. "Testumgebung"
5. Klicke bei "Location:" auf "Browse File System..." und wähle von deiner Java Installation die "javaw.exe" aus. Dass kann dann so aussehen: "C:\Program Files\Java\jdk-9.0.4\bin\javaw.exe"
6. Klicke bei "Working Directory:" auf "Browse File System..." und wähle den Ordner deiner Testumgebung aus.
7. Kopiere in "Arguments:" folgendes:
   ```
   -Xms1G -Xmx2G -Dfile.endcoding=UTF-8 -Dlog4j.skipJansi=true -jar spigot.jar --world-dir worlds --level-name Lyria --log-strip-color
   ```
Wenn du nun auf "Run" Klickst, oder auf das im Bild umrahmte Icon klickst, startet dein Server nun in Eclipse. Es öffnet sich nun eine "Console" die das gleiche ist, wie ein CMD Fenster.

# Eclipse und GitLab

Zunächst solltet ihr den Wikieintag zu [GitLab](/Einführung/GitLab) gelesen und verstanden haben, um ein sinnvolles und korrektes arbeiten mit Git durchzuführen. Im Folgenden wird nämlich nur beschrieben, wie in Eclipse Git verwendet wird, jedoch nicht wie Git funktioniert oder eingesetzt wird.

Alle zu GitLab gehörenden Funktionen findet ihr, wenn ihr auf das entsprechende Projekt einen Rechtsklick ausführt und dann in den Unterpunkt Team Navigiert. Hier findet ihr nahezu alles, was wir zum Arbeiten brauchen, auch wenn es noch mehr Funktionen gibt. Ich werde jetzt nur die wichtigen und für unseren nutzen notwendigen Funktionen erklären.
## Projekt Übersicht  
   ![Projekt](https://cdn.discordapp.com/attachments/520955035832811521/613702467045163027/unknown.png)  
   Hier steht zuerst der Projektname.  
   In der eckigen Klammer könnt ihr dann zuerst das Repository sehen und dann in welchem Branch ihr seid.
## Projekt Pfeile  
   ![Projekt](https://cdn.discordapp.com/attachments/520955035832811521/613702522703446026/unknown.png)  
   Der Pfeil nach oben mit der 1 Zeigt, dass eine Änderung noch nicht Gepushed wurde.  
   Der Pfeil nach unten mit der 1 Zeigt, dass eine Änderung noch nicht Gepulled wurde.
## Icons  
   ![Projekt](https://cdn.discordapp.com/attachments/520955035832811521/613701629509763073/IconDecorations.png)  

   | Bezeichnung   | Beschreibung   |
   |:--- |:--- |
   | dirty (folder)   | Mindestens eine Datei im Ordner ist nicht mehr aktuell. Das bedeutet, dass es Änderungen im Workspace gibt, die weder im Index noch im Repository vorhanden sind.
   | tracked          | Die Ressource ist dem Git-Repository bekannt.
   | untracked        | Die Ressource ist dem Git-Repository nicht bekannt.
   | ignored          | Die Ressource wird vom Git-Repository ignoriert. Die Voreinstellungen finden sich unter "Team/Ignored Resources". Die .gitignore-Datei wird nicht berücksichtigt.
   | dirty            | Die Ressource weist Änderungen im Workspace auf, die weder im Index noch im Repository vorhanden sind.
   | staged           | Die Ressource enthält Änderungen, die dem Index hinzugefügt werden. Nicht, dass das Hinzufügen zum Index derzeit möglich ist, aber im Commitdialog wurde die Ressource bereits hinzugefügt.
   | partially-staged | Die Ressource verfügt über Änderungen, die dem Index hinzugefügt werden, sowie über Änderungen im Workspace, die weder im Index noch im Repository vorhanden sind.
   | added            | Die Ressource wird in dem Git-Repository hinzugefügt.
   | removed          | Die Ressource wird aus dem Git-Repository entfernen.
   | conflict         | Die Ressource  hat merge conflicts.
   | assume-valid     | Die Ressource hat das Flag "assume unchanged". Das bedeutet, dass Git die Ressource nicht mehr auf mögliche Änderungen überprüft. Sie müssen daher das Bit manuell deaktivieren, um Git mitzuteilen, wenn sich die Ressource ändert. Diese Einstellung kann mit der Menüaktion "Team/Assume unchanged" aktiviert werden.

## Team  
   ![Projekt](https://cdn.discordapp.com/attachments/520955035832811521/615593997150322689/unknown.png)  
   Die wichtigsten Befehle im Untermenü Team, die nicht selbsterklärend sind.

   | Bezeichnung   | Beschreibung   |
   |:--- |:--- |
   | Switch To   | Wechseln der Branches
   | Reset       | Zurücksetzen des Projektes auf den Repository zustand