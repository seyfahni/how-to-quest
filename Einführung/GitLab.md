# Inhalt

[[_TOC_]]

# Allgemein

Hier wird im Folgenden das Konzept von Git erklärt und genauer auf GitLab eingegangen. Wer etwas nicht versteht, sollte besser noch mal nachfragen oder einen ausführlichen Artikel lesen wie zum Beispiel "[Learn git concepts, not commands](https://dev.to/unseenwizzard/learn-git-concepts-not-commands-4gjc)", auch wenn Mann dann nicht um einen englischen Artikel herum kommt. Hier soll darauf hingewiesen werden, dass der Wiki Eintrag nur wichtige und für uns relevante Konzepte betrachtet.

# Workflow

Um den Workflow nachzuvollziehen ist folgendes Bild hilfreich  
![Concept](https://cdn.discordapp.com/attachments/520955035832811521/615837217562165259/MgaV9.png)  
Dein `locale repository` besteht aus drei "Instanzen", die von Git verwaltet werden. 
Die Vierte "Instanz" ist GitLab, das sogenannte `remote repository`. Dieses ist eine Art Cloud speicher, in dem alle Änderungen zusammen laufen.

Die drei Instanzen des `locale repository`:
1. Die erste ist dein `Workspace`, welcher die echten Dateien auf deinem PC enthält, in und mit diesen arbeitest du. Dieser ist also dein tatsächliches Verzeichnis mit allen Daten auf deinem PC.
2. Die zweite ist der `Index`, dieser zeigt deine aktuellen Änderungen an, diese sind aber noch nicht im `local` oder `remote` Repository.
3. Erst wenn du Änderungen bestätigst, landen diese auch im sogenannten `local repository`. Dieses enthält in der Regel das `remote repository` und von dir durchgeführte Änderungen. Der aktuellste stand im `locale repository` nennt sich "HEAD".

## Add/Stash & Commit & Push

Mit `add` beziehungsweise `stash` fügst du eine Änderung aus dem `workspace` zum `index` hinzu.  
Mit dem `commit` fügst du nun die Änderungen aus dem `index` in dein `local repository` hinzu.  
Mit `push` lädst du diese Änderungen im `local repository` hoch ins `remote repository`.  

## Branching

Branches werden benutzt, um verschiedene Funktionen isoliert voneinander zu entwickeln. Dies ist vergleichbar, mit einer Kopie des Originalen Ordners. Der `master`-Branch ist der "Standard"-Branch, wenn du ein neues `repository` erstellst. Du solltest aber für die Entwicklung neuer Dinge andere Branches verwenden/erstellen und diese dann in den Master-Branch zusammenführen (`mergen`). Beim Zusammenführen werden die Änderungen aus beiden Ordnern vereint.

![Concept](https://cdn.discordapp.com/attachments/520955035832811521/615846516799701001/68747470733a2f2f63646e2d696d616765732d312e6d656469756d2e636f6d2f6d61782f313630302f312a69485050613732.png)

Ein Branch ist nicht für andere verfügbar, bis du diesen in das `remote repository` hochlädst oder der Branch wurde direkt in GitLab angelegt.

## Update & Merge

Um dein `local repository` und `workspace` mit den neuesten Änderungen zu aktualisieren, verwende `pull`.
Bei einem `pull` wird zunächst das `local repository` aktualisiert (`fetch`) und dann die Änderungen mit deinem `workspace` zusammengeführt (`merge`).  
Wenn du einen anderen Branch mit deinem aktuellen (z. B. master) zusammenführen willst, benutzt man auch  `merge`. In deisem fall, wird nicht dein `workspace`, sondern die Änderungen zweier Branches zusammengeführt.  
Git wird jetzt versuchen automatisch diese Änderungen zusammenzuführen. Unglücklicherweise ist dies nicht immer möglich und endet in Konflikten. Solche Konflikte müssen händisch gelöst werden. Ist dies getan, so muss das Ergebnis daraus wieder mit `push` hochgeladen werden. Solltest du einmal in dieser Situation sein, scheue nicht davon nach Hilfe zu fragen.

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