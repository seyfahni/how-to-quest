# Inhalt

[[_TOC_]]

# Allgemein

In diesem Eintrag wird erklärt, wie ihr euren eigenen Minecraft Server zum Testen aufsetzt und einstellt. Hierfür verwenden wir Spigot.

# Voraussetzungen
1. Du musst Java 8 oder eine aktuellere Version installiert haben.
2. Lade dir eine Aktuelle Paper Version herunter. https://papermc.io/downloads
3. Lege einen Ordner für den Server an, in den du die Spigot jar legst.

# Installation
Entpacke [Server_Configs.zip](uploads/4ab281b9791ec307d25cafdf18757e64/Server_Configs.zip) in deinem test Server Ordner.
## Windows
1. Lege eine Datei in deinem Server Ordner an und kopiere den folgenden Text hinein. Dann speichere die Datei als "start.bat".
2. ```
   @Echo OFF
   echo "Starting Server..."
   java -Xms1G -Xmx2G -Dfile.endcoding=UTF-8 -jar spigot.jar --world-dir worlds --level-name Lyria --log-strip-color
   echo "Server Stopped"
   PAUSE
   ```
3. Starte den Server in dem du Doppelt auf die "start.bat" klickst
## Linux
1. Lege eine Datei in deinem Server Ordner an und kopiere den folgenden Text hinein. Dann speichere die Datei als "start.sh".
   ```
   #!/bin/sh
   java -Xms1G -Xmx1G -XX:+UseConcMarkSweepGC -jar spigot.jar
   ```
3. Führe das Folgende im Terminal aus:
   ```
   chmod +x start.sh
   ```
4. Führe das Startskript  aus:
   ```
   ./start.sh
   ```
## Weiteres
- Joine auf deinen Server über die IP `localhost`
- Gib dir rechte auf deinem Server in dem du in der Konsole `op NAME` eingibst
- Es ist empfehlenswert, mit WorldDownloader, den Spawn herunter zu laden und diesen als Welt auf dem Test Server zu Packen.

# Plugins
Alle Pugins kommen in den "plugins" Ordner im Server Ordner. Normalerweise legt jedes Plugin darin einen gleichnamigen Ordner an, in dem alle Configs usw. liegen. Achte bitte darauf die jeweilige aktuellste Version der Plugins für die Entsprechende Spigot Version herunterzuladen.

## BetonQuest
Website: [BetonQuest](https://github.com/BetonQuest/BetonQuest)

BetonQuest dient dazu, die Quests zu schreiben.  
Dies ist ein komplexes Plugin, mit dem du in Zukunft Quest Schreiben wirst. Weitere Informationen findest du im Wiki Beitrag [BetonQuest](/Einführung/BetonQuest).  
Begib dich nun in die Config von BetonQuest und stelle Folgende dinge um:
   - `language` auf `de`
   - `default_journal_slot` auf `-1`
   - `default_conversation_IO` auf `tellraw`
   - `display_chat_after_conversation` auf `false `
   - `journal.one_entry_per_page` auf `true`
   - `journal.full_main_page` auf `true`
   - `journal.hide_date` auf `true`

## Weitere Plugins
Es können weitere Plugins verwendet werden, die von BetonQuest unterstützt werden. Eine Liste alle unterstützten Plugins findest du hier: https://betonquest.github.io/BetonQuest/DEV/User-Documentation/Compatibility/
Nicht alle diese Plugins sind auf Rahasia installiert, bei fragen an ein Team Mitglied wenden!