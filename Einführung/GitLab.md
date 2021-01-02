# Inhalt

[[_TOC_]]

# Allgemein

Hier wird im Folgenden das Konzept von Git erklärt und genauer auf GitLab eingegangen. Wer etwas nicht versteht, sollte besser noch mal nachfragen oder einen ausführlichen Artikel lesen wie zum Beispiel "[Learn git concepts, not commands](https://dev.to/unseenwizzard/learn-git-concepts-not-commands-4gjc)", auch wenn Mann dann nicht um einen englischen Artikel herum kommt. Hier soll darauf hingewiesen werden, dass der Wiki Eintrag nur wichtige und für uns relevante Konzepte betrachtet.

# Workflow

Um den Workflow nachzuvollziehen ist folgendes Bild hilfreich  
![Concept](https://cdn.discordapp.com/attachments/520955035832811521/615837217562165259/MgaV9.png)  
Dein lokales Repository besteht aus drei "Instanzen", die von Git verwaltet werden. 
Die Vierte "Instanz" ist GitLab, das sogenannte "remote repository". Dieses ist eine Art Cloud speicher, in dem alle Änderungen zusammen laufen.

Die Drei Instanzen des lokalen Repositories:
1. Die erste ist dein "Workspace", welcher die echten Dateien auf deinem PC enthält, in und mit diesen arbeitest du. Dieser ist also dein tatsächliches Verzeichnis mit allen Daten auf deinem PC.
2. Die zweite ist der "Index", dieser zeigt deine Aktuellen Änderungen an, diese sind aber noch nicht im "local" oder "remote" Repository.
3. Erst wenn du Änderungen bestätigst, landen diese auch im sogenannten "local repository". Dieses enthält in der Regel das "remote repository" und von dir durchgeführte Änderungen. Der aktuellste stand im Lokalen Repository nennt sich "HEAD".

## Add & Commit

Du kannst Änderungen vorschlagen (zum Index hinzufügen) mit Add.  
Das ist der erste Schritt im Git Workflow, du bestätigst deine Änderungen mit einem Commit.
Jetzt befindet sich die Änderung im HEAD, aber noch nicht im entfernten Repository.

## Änderungen hochladen

Die Änderungen sind jetzt im HEAD deines lokalen Repositories. Um die Änderungen an dein entferntes Repository zu senden, führe einen Push aus. Ob du in den master kannst du auch ändern, mehr über Branches erfährst du später.   

## Branching

Branches werden benutzt, um verschiedene Funktionen isoliert voneinander zu entwickeln. Der master-Branch ist der "Standard"-Branch, wenn du ein neues Repository erstellst. Du solltest aber für die Entwicklung andere Branches verwenden und diese dann in den Master-Branch zusammenführen (mergen). Auch das lernst du später.

![Concept](https://cdn.discordapp.com/attachments/520955035832811521/615846516799701001/68747470733a2f2f63646e2d696d616765732d312e6d656469756d2e636f6d2f6d61782f313630302f312a69485050613732.png)

Ein Branch ist nicht für andere verfügbar, bis du diesen in dein entferntes Repository hochlädst oder der Branch wurde direkt in GitLab angelegt.

## Update & Merge

Um dein lokales Repository mit den neuesten Änderungen zu aktualisieren, verwende Pull in deinem Workspace, um die Änderungen erst herunterzuladen (fetch) und dann mit deinem Stand zusammenzuführen (merge).
Wenn du einen anderen Branch mit deinem aktuellen (z. B. master) zusammenführen willst, benutze Merge.  
In beiden Fällen versucht git die Änderungen automatisch zusammenzuführen. Unglücklicherweise ist dies nicht immer möglich und endet in Konflikten. Du bist verantwortlich, diese Konflikte durch manuelles Editieren der betroffenen Dateien zu lösen. Bist du damit fertig, musst du das Git mitteilen in dem du Add machst.
Bevor du Änderungen zusammenführst, kannst du dir die Differenzen auch anschauen mit Diff.

## Tagging

Es wird empfohlen, für Software Releasestags zu verwenden. Du kannst einen neuen Tag namens 1.0.0 erstellen.
Versionen Taggen wir nur im Master, um Fortschritte zu markieren.  
Die Erste Stelle steht für eine neue Quest.  
Die Zweite Stelle steht für eine Änderung in einer Quest.  
Die Dritte Stelle steht für einen Bug fix in einer Quest.

## Änderungen rückgängig machen

Falls du mal etwas falsch machst (was natürlich nie passiert ;) ) kannst du die lokalen Änderungen mit "Checkout" auf den letzten Stand im HEAD zurücksetzen. Änderungen, die du bereits zum Index hinzugefügt hast, bleiben bestehen.  
Wenn du aber deine lokalen Änderungen komplett entfernen möchtest, holst du dir den letzten Stand vom remote Repository mit "reset".

# Tickets & Meilensteine

Ein Meilenstein beschreibt ein zu entwickelndes Feature. Dabei gehen wir davon aus, dass eine Quest oder ähnliches ein Meilenstein ist. Pro Meilenstein sollte ein eigener dafür vorgesehener Branch verwendet werden, der entsprechend benannt ist. Der Meilenstein sollte einen Überblick beschrieben und es sollte zugeordnete Tickets geben. Durch die Tickets soll der Meilenstein möglichst genau und vollständig abgebildet sein.

Tickets beschreiben ein Problem, ein Bug oder ein kleineres zu entwickelndes Feature. Ein Ticket sollte stets so genau wie möglich formuliert sein und alles besprochene enthalten.