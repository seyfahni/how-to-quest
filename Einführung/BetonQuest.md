# Inhalt

[[_TOC_]]

# Allgemein

Hier wird alles zu BetonQuest erklärt, dass du nicht in der Doku findet oder missverständlich ist.  
Die Doku findest du hier: https://github.com/bundabrg/BetonQuest/tree/preview/docs.
Geschriebene Quests oder Quest Pakete werden einfach in den Ordner von BetonQuest im plugins Ordner Kopiert.

# Quest schreiben & Konventionen
## Eine neue Quest beginnen
Wenn du eine neue Quest schreiben möchtest, so solltest du wie folgend beschrieben vorgehen:
1. Überlege dir einen `Namen` der Eindeutig ist, dieser darf `nicht länger als 20 Buchstaben` sein.
2. Lasse dir für deine Quest einen neuen Branch im GitLab anlegen, dieser hat dann den Namen deiner Quest.
3. Wechsele in deinen Branch, kopiere das `#Template` Package und benenne es in deinen Quest Namen um.
## Die neue Quest vorbereiten
Im `config` Package liegen globale Variablen und Einstellungen sowie Items für Menüs und einiges mehr. Denke stets daran und verwende diese wenn möglich.
1. Nun begib dich in die `main.yml`. Dort gibst du unter `variables` deiner Quest ihren Namen, gibst die ID des NPCs an, der die Quest startet und gibst den Namen dieses NPCs an. Alles weitere notwendige ist bereits fertig und muss jetzt nur noch von dir, im Laufe der Zeit, erweitert werden.
   - Denke stets daran deine Quest, bei einem Abbruch, wenn möglich, aufzuräumen, aber auch wenn diese beendet ist:
      - `Tags löschen`
      - `Journaleinträge löschen`
      - `Objectives löschen, wenn möglich`
2. In der `events.yml` findest du einige vorgefertigte Events, die das Template bereits benötigt. Diese müssen normalerweise nicht verändert werden.
   - Denke stets daran, Quest eindeutig zu taggen, so kann man diese auch später weiter benutzen:
      - Ist eine Quest gestartet, sollte dies immer mit dem Tag `started` markiert werden.
      - Ist eine Quest beendet, sollte dies immer mit dem Tag `finished` markiert werden.
3. In der `custom.yml` findest du die Implementierung des Ausrufungszeichens, welches NPCs die eine Quest haben, über dem Kopf tragen.
4. In der `conditions.yml` findest du einige vorgefertigte Conditions, die das Template bereits benötigt. Diese müssen normalerweise nicht verändert werden.
5. In der `items.yml` und in der `objectives.yml` steht nichts.
   - Wenn ihr Items in einer Quest verwendet haltet euch an die vorhandenen Farben für die [Seltenheitsgrade](https://www.lyriaserver.de/community/wiki/grundlagen/feature_plugin_tutorials/itemsitemfarben-r99/).
6. In der `journal.yml` findest du einen Beispiel Journal Eintrag, nach dem gleichen Schema kannst du weitere Einträge erstellen.
   - Denkt stets daran:
      - Die Beschreibung des Eintrags darf eine Buchseite nicht überschreiten.
      - Einträge sollten stets die aktuelle Aufgabe beschreiben.
      - Es kann vorkommen, das eine Zeile abgeschnitten wird im Buch, in diesem Fall muss man mit \n einen Zeilenumbruch machen.
7. In der `conversation.yml` findest du ein Beispiel für ein Gespräch mit einem NPC.
   - Denkt stets daran:
      - Wenn ein NPC einen mehrzeiligen Text sagt, so muss dieser so formatiert sein:
      ```
      text: |
            
          Hallo %player.display%.
          Ich bin $quester_name$
      ```
## Quest-Wiki-GitLab
1. Alle Entscheidungsmöglichkeiten aufzeigen.
2. Alle Quest-Items und Loot auflisten, sowohl bei Abgabe wie bei Erhalt.
3. (Grobe) Positionen der Quest-Ziele.
4. Gesunden Menschenverstand beim dokumentieren.
## Journal-Mainpage
1. Es gibt eine Legende, welche im `config` Package definiert ist, die Questnamen werden farbig markiert, je nach Status.  
   Es gibt folgende stadien:
   - `&cBereit`
   - `&eGestartet`
   - `&2Abgeschlossen`
   - `&7Fehlgeschlagen`
2. Bei Fehlgeschlagenen Quests, die eine ganze Reihe von weiteren Quests mit sich ziehen, wird nur die Erste angezeigt.

# Wissenswertes
1. Itemframes lassen sich nicht per action Objective angesteuert, da sie nicht als Block, sondern als Entität angesprochen werden.  
`test: interact any item_frame 1 events:msg cancel`
2. Wenn eine conversation während einer anderen conversation gestartet werden soll, dann muss das dazugehörige Event einen delay haben.
   ```yml
   con2_folder: folder con2 delay:1
   con2: conversation NPC2
   ```
3. Wenn ihr die variable Objective braucht, wird diese hier nochmal erklärt. Da die docs sehr verwirrend sein können.
   - Diese Objective ist dazu da beliebige Variablen für einen Spieler zu speichern. Dazu muss die Objective aktiv bleiben. Wird die objective gelöscht wird auch die Variable gelöscht.
   - Damit ein Spieler keinen Zugriff auf die Variable hat, sollte stets "no-chat" an das Objective gehängt werden.
   - Ändern kann man eine Variable per Event. Die Syntax sieht wie folgt aus
`variable: variable obj_ID var_name VARIABLENINHALT`
   - Dieses Objective kann mehrere Variablen speichern, deshalb ist ein Variablenname nötig.
   - Abrufen könnt ihr die Variable mit %objective.obj_ID.var_name%. Ausgegeben wird dann der Variableninhalt.
   - Wenn ihr einen Text als Inhalt haben wollt, müsst ihr im Inhalt alle Leerzeichen durch Unterstriche ersetzen.
4. Für die, die NpcDestinations zusammen mit BetonQuest zur Steuerung von NPCs benutzen, gibt es Conditions und Events, die in BetonQuest implementiert sind. Diese sind [hier](https://github.com/Nutty101/NPC_Destinations2/issues/23#issuecomment-427551593) zu finden.  
   - Die Conditions sind dazu da, um abzufragen, ob der NPC sich in einem bestimmten Bereich befindet.  
   - Das Event ist dazu da, um den NPC an eine vordefinierte Position zu schicken. Hierbei muss beachtet werden, dass `{duration to stay}` nicht `0` sein darf, ansonsten wird der NPC nicht laufen.
   ```yml
   event: npcdest_goloc {npcId} {loc#} {duration to stay}
   loc# can be either the number or UUID
   Send NPC to the location for duration seconds
   
   condition: npcdest_currentlocation {npcId} {loc#}
   loc# can be either the number or UUID
   Returns true if npc is at location
   
   condition: npcdest_distancetolocation {npcId} {loc#} {distance}
   loc# can be either the number or UUID
   Returns true if the npc is distance or less from location
   ```