

Hier ist dein bearbeitetes Skript mit professioneller Sprache und passenden Übergängen:


1. Einleitung
   Herzlich willkommen. Mein Name ist Atréus Engelniederhammer. Heute stelle ich Ihnen meine Projektarbeit zum Thema "Entwicklung eines Chatbots für Microsoft Teams und die dazugehörige Middleware" vor. Diese Präsentation richtet sich an den Prüfungsausschuss. Nach dieser kurzen Begrüßung können wir direkt beginnen.
   Ziel des Projekts war es, wichtige Informationen für den täglichen Gebrauch im Seitwerk zu identifizieren und diese intuitiver und schneller bereitzustellen als über das bestehende Intranet.
   Übergang zur Agenda:
   Lassen Sie uns nun einen Blick auf die Agenda werfen, um den Ablauf der Präsentation zu skizzieren.
2. Agenda zeigen
3. Projektumfeld
   Die Seitwerk GmbH ist eine Medienagentur mit aktuell 80 Mitarbeitern. Sie ist in den Bereichen Grafikdesign, Multimedia und Entwicklung tätig und bietet Dienstleistungen wie Webseiten sowie Mobile Apps an. Gegründet wurde Seitwerk 2004 und befindet sich in Uffing am Staffelsee.
   Übergang zum Ist-Zustand:
   Nachdem wir das Projektumfeld beschrieben haben, möchte ich nun den aktuellen Ist-Zustand näher erläutern.
4. Ist-Zustand
   Im Seitwerk wird als Hauptinformationsquelle das lokal gehostete Intranet verwendet. Allerdings gestaltet sich die Informationsbeschaffung dort aufgrund der veralteten Oberfläche nicht sehr effizient und intuitiv. Das Intranet ist nur von innerhalb des Netzwerks erreichbar, was die Informationsbeschaffung zusätzlich einschränkt.
   Übergang zum Soll-Zustand:
   Um diese Probleme zu lösen, habe ich den Soll-Zustand definiert, den ich Ihnen nun vorstellen möchte.
5. Soll-Zustand
   Ziel war es, wichtige Informationen zu identifizieren und bereitzustellen. Diese sollen intuitiver und effizienter abrufbar sein. Zudem sollen die Informationen sicher auch von außerhalb des Netzwerks bereitgestellt werden können.
   Übergang zur Risikoanalyse:
   Um sicherzustellen, dass das Projekt erfolgreich umgesetzt werden kann, haben wir eine umfassende Risikoanalyse durchgeführt.
6. Risikoanalyse
   Während der Risikoanalyse habe ich versucht, alle relevanten Risiken zu identifizieren, die während des Projekts auftreten könnten. Dazu gehören Datenschutzrisiken, der Zugriff von außerhalb auf interne Netzwerke, Sicherheitslücken in den verwendeten Systemen und die sichere Datenübertragung. Diese Punkte wurden zusammengefasst und mit meinem Projektbegleiter während der Projektplanung besprochen, um entsprechende Maßnahmen zu entwickeln.
   wie ich diese Maßnahmen durchgesetzt habe sehen schauen wir uns dann in der Implementationsphase an 

   nach der den gewonnen erkenntnissen bin ich dann direkt in Planungpahse umgestiegen

   Diese begann mit Besprechungen mit meinen Abteilungsleitern, die regelmäßig auf Informationen im Intranet zugreifen müssen, sowie mit Mitarbeitern, die hauptsächlich im Kundensupport tätig sind. Gemeinsam haben wir herausgefunden, welche Informationen häufig abgerufen werden müssen und welche schwer zugänglich sind.
   Dabei sind wir uns auf drei Informationsgruppen gekommen die ich effizenter bereitstellen wollte:

7. <persönliche Teilnahme an Projekten, spezifische Informationen zu einem Projekt und Informationen über Kunden.
7. 
   Während der Projektplanung fiel auch die Entscheidung, Microsoft Teams als Benutzeroberfläche zu verwenden, da dies bereits als Hauptkommunikationsmittel in der Firma genutzt wird. Anschließend wurden Aufgabenpakete erstellt, die ich abarbeiten und vertiefen konnte.
   Übergang zur Architekturplanung:
   Nach der groben erstellung der Aufgabenpakete wie das auseinandersetzten mit den microsoft azure produkten die ich brauche und wie ich die sicherehits vorkehrungen einhalten kann. habe ich direkt angefangen mit der Architekturplanung 
8. Die Architekturplanung
   Die Architekturplanung Um den vorgegebenen Sicherheitsstandards gerecht zu werden, entschied ich mich für den Einsatz einer Middleware, die in Zusammenarbeit mit einer Firewall den sicheren Datentransfer gewährleistet.
   Auf diesem Architekturplan erkläre ich nun, wie der Datentransfer funktioniert. Wie hier zu sehen ist, sind die Gefahrenpunkte markiert. Besonders kritisch ist die Stelle in der Mitte, da dort jegliche Anfragen aus dem Internet kommen können.
   Die bereits vorhandene Firewall wurde so konfiguriert, dass nur ein fester IP-Adressenbereich von Azure Anfragen an den Port der Middleware stellen darf. Dieser IP-Bereich wird von Azure vorgegeben.
   Nachdem der Architekturplan festgelegt war, entschied ich mich für die notwendigen Technologien, da es viele Möglichkeiten zur Umsetzung gibt. Alles wurde in JavaScript geschrieben und ich habe verschiedene Erweiterungen verwendet:
   Node.js als grundlegende JavaScript-Umgebung
   Express.js, eine Erweiterung für Node.js, die Funktionen zum Erstellen eines HTTP-Servers bietet
   Microsoft Bot Framework, die Grundlage für den Teams-Bot, ebenfalls eine Node.js-Erweiterung
   Microsoft Teams Toolkit, eine Erweiterung für Visual Studio Code, die für das Testen und Deployen des Bots benötigt wird.
   Übergang zur Implementierung:
   Nachdem die Architektur und die Technologien festgelegt waren, konnte die Implementierungsphase beginnen.
9. Die Implementierung
   Middleware
   Nun kommen wir zur Implementierungsphase. Ich werde kurz die Funktionalität der einzelnen Komponenten besprechen und auf die Sicherheitsvorkehrungen eingehen.
   Die Middleware wurde mit Node.js und Express umgesetzt. Die Express-Erweiterung ermöglicht es, Routen für einen HTTP-Server sehr einfach und schnell anzulegen. Jede Route ist jeweils für eine Informationsgruppe zuständig. Eine Route gibt Informationen für ein spezifisches Projekt zurück, eine andere für Kunden und eine für eigene Projekte.
   Diese Routen können in meinem Fall über die HTTP-Methode GET erreicht werden und führen dann den dazugehörigen Code aus, der die gewünschten Daten im Intranet anfragt und im JSON-Format zurückgibt.
   Als Sicherheitsmechanismus besitzt die Middleware ein Client Secret und ein Client Password, mit denen sie sich an der Token-Schnittstelle des Intranets einen Token erstellen lassen kann. Dieser Token wird dann bei jeder zukünftigen Schnittstellenanfrage mitgeschickt und vom Intranet überprüft.
   Bot
   Den Bot habe ich mit Hilfe des Teams Toolkits erstellt. Das Toolkit generiert direkt in Visual Studio Code die Grundstruktur des Bots und ermöglicht lokale Tests. Um auf Anfragen von Mitarbeitern zu reagieren, habe ich drei Command-Handler erstellt. Jeder Command ist für eine spezifische Route auf der Middleware zuständig und gibt eine bestimmte Art von Informationen zurück.
   Diese Command-Handler funktionieren ähnlich wie die Routen der Middleware, werden jedoch nicht durch HTTP-Methoden angesprochen, sondern durch Schlüsselbegriffe im Chat aktiviert. Zum Beispiel ist für Kundeninformationen der Schlüsselbegriff "Kunde" gefolgt von einem Namen. Sobald dieses Wort fällt, führt der Bot den passenden Command-Handler aus.
   Der Command-Handler überprüft zunächst, ob der Benutzer, der den Bot kontaktiert hat, tatsächlich ein Mitarbeiter der Firma ist. Diese Überprüfung erfolgt anhand der E-Mail-Adresse, die auf seitwerk.de enden muss, und der aktuellen Mitarbeiterliste aus der Graph API. Sobald die Überprüfung erfolgreich ist, wird die URL für den Fetch an die Middleware erzeugt. Dabei werden obligatorische Parameter aus dem Chat extrahiert, wie der Name des Absenders und beispielsweise der Kundenname.
   Die Middleware antwortet dann und schickt die gewünschten Daten im JSON-Format zurück an den Bot, der sie formatiert und als Nachricht im Chat antwortet.
   Beim Öffnen des Chats zeigt der Bot ein Auswahlfenster an, in dem alle drei Commands angezeigt und kurz erklärt werden. Dies erleichtert den Mitarbeitern die Auswahl und Nutzung der verfügbaren Funktionen.
   Übergang zu Testing und Deployment:
   Nach der Implementierung folgte die Phase des Testings und Deployments.
10. Testing und Deployment
    Nun kommen wir zum Testing. Wie bereits in der Implementierungsphase erwähnt, konnte ich den Bot sehr leicht auf seine Funktionalität lokal testen, dank des Teams Toolkits. Die Middleware konnte ich ebenfalls lokal auf meinem Rechner testen, indem ich sie startete und mit Curl-Befehlen im Terminal die Fetch-Anfragen des Bots imitierte.
    Die Kommunikation zwischen den Systemen und die Firewall-Regeln konnte ich erst testen, nachdem ich die Middleware auf einem bereits vorhandenen Ubuntu-Server deployed hatte. Ich entschied mich, dies per SSH und dem Git-Clone-Verfahren zu machen, um schnell auf Fehler oder zukünftige Erweiterungen reagieren zu können.
    Nachdem die Middleware erfolgreich deployed war, musste ich nur noch den Bot auf die bereits vorhandenen und konfigurierten Azure-Ressourcen deployen. Dafür verband ich meinen Microsoft-Account und deployte direkt aus der IDE.
    Übergang zum Fazit:
    Abschließend möchte ich Ihnen noch mein Fazit und einen Ausblick geben.
11. Fazit/Ausblick
    Zusammenfassend lässt sich sagen, dass das Projektziel erreicht wurde. Der Bot wird von den Mitarbeitern genutzt und spart ihnen Zeit.
    Was die Lessons Learned betrifft, so habe ich gelernt, dass man sich bei der Arbeit mit Azure-Produkten viel Zeit für die Dokumentation nehmen muss.
    Für die Zukunft sind bereits Erweiterungen für die Inventarverwaltung geplant.
