#  1. Einleitung

### herlich willkom, Mein Name ist Atréus Engelniederhammer, ichs telle euch Heute 
### meine Projektarbeit zum Thema Entwicklung eines Chatbots für Microsoft Teams und die dazugehörige Middleware vor 
### gerichtet ist diese vorstellung an den den Prüfungsauschluss nach dieser kleinen Begrüßung könenn wir auch direkt anfangen

### Ziel war es Informationen zu finden welche wichtig sind für den tägliche gebrauch im Seitwerk und
### um diese dann intuitiver und schneller bereitzustellen als über das Intranet des Seitwerks

# 2. Agenda zeigen

#  3. Projektumfeld 
### die Seitwerk gmbh ist eine Medienagentur mit aktuell 80 Mitarbeitern in den Berreichen Grafikdesign, Multimedia und Entwicklung zu den Dienstleistungen gehören Webseiten sowie Mobile Apps
### gegründet wurde das seitwerk 2004 und liegt derzeit in Uffing am staffelsee 

# Agenda zeigen

# 4. IST zustand
### im Seitwerk wird  alsHauptinformaton quelle das local gehostet Intranet verwendet bzw die weboberfläche davon 
### doch die informations beschaffung gestalltet sich dort nicht sehr effzient und intuitiv verschuldet durch veraltete oberfläche und CMS system 
### nur von innherhalb des netwerks erreichbar und sommit informationenbeschaffung nur begrenzt möglich 

# 5. Soll zustand
### Wichtige Informationen herausfinden um diese dann bereitzustellen 
### Intuitiver und efiizzentes erlangen der informationen 
### Informtionen sicher auch von außen bereitstellen 


# 6. Risikoanalyse 
### dort habe ich versucht alle Risiko Punkte zu erkennen mit den während des Projekts Gerechnet werden muss so  
### Datenschutzrisiken,--- Zugriff von außerhalb auf interne Netzwerke,---- Sicherheitslücken verwendeter systeme ---Sichere Datenübertragung
### diese punkte habe ich zu einer risikoanalyse zusammnegafsst um sie dann mit meinem Projektbegeliter während der Projektplanung zu besprechen wie damit umgegangen werden kann

# 7. Die Projektplanung 
### die projektplannung lief wie folgt ab ich habe mich mit meinem Abteilungsleitern besprochen der viel auf informationen im Intranet zugreifen muss
### sowie Mitarbeitern die überwiegend im support mit kunden arbeiten und mit diesen informationen gesammelt welche öft abgerufen werden müssen und/oder umständlich zu erreichen 
### dabei haben wir uns auf drei verschiedene information gruppen beschrenkt
### persönliche teilnahme an Projekte
### Spezifische informationen zu einem Projekt 
### Informationen über Kunden 



### während der Projektplanung viel noch die entgültige entscheidung als benutzeroberfläche teams zu verwenden da dies als haupt kommunikation mittel in der firma bereits verwndet wird 
### nachdem ich einen groben überblick hatte habe ich dann Aufagben packete erstellt die ich dann abarbeiten konnte bzw vertiefen  


# 8. die architektur planunng 
###  die architektur planunng fand direkt anschluss der besprechung mit den Projektbegleiter statt da ich nun die anforderungen hatte welche umgesetzt werden müssen
### bevor ich darauf eingehe warum ich mich für diese Architektur entschieden habe erkläre ich erstmal an hand des bildes wie der ganze datentransver funktioniert 
### um den vorgegebenen sicherheitsstandarts gerechts zu werden habe ich mich für den einsatz einr Middleware entschieden warum diese in zusammenarbeit mit einer firewall den sicheren transfer von Daten gewährleisten kann 
###  zeige ich nun an diesem Arichtekturplan, """"erklären von wo die daten kommen und wo sie hingehen"""""
### wie hier, wie hier zusehen ist sind die gefahren punkte markiert bei diesem in der mitte ist natürlich das größte risiko da dort jegliche Anfragen aus dem internet kommen können,
### dafür wurde aber die schon vorhandenen firewall so eingestellt dass nur ein fester IP-adressen Berreich von Azure an den port der middlware anfragen darf, dieser ip berreich wird von azure vorgegeben 
wwwwwwwwwww
### nach dem ich dann einen festen Archtektur plan hatte habe ich mich noch für die technologien entschieden die ich dafür brauche da es viele möglichkeite gäbe es umzusetzten 
### grundsätzlich ist alles in javascript geschireben udn ich habe veraschieden erweiterungen noch zusaätzlich verwendet wie 
### nodejs als grundlegende javascript enviroment 
### express.js, ist ein erweiterung für nodejs und bringt funktionien mit um einen http server zu erstellen
### Microsoft bot Framework ist die grundlage für den Teams bot auch eine nodejs erweiterung 
### und das Microsoft tools kit eine erweiterung für den visualstudio Code Editor, die für das testen und deployen des bots benötigt wird 


# 9. die  Implementierung

## middleware
### NUN KOMMEN WIR zur implentationphase hier werde ich kurz jeden von !!!! die funktiunalität bespechen und auf die sicherheitsvorkehrungen einghen 
### starten wir mit der middlware diese wurde wie schon erwähnt mit node.js und express umgesetzt die express erweiterung gibt einen die möglichkeite routen für einen http server sehr simpel und schnell anzlegen 
### jede route ist jeweils für eine Informations gruppe zusändig also eine die route gibt die informationen für ein spezifische Projekt zurück und einnmal für die kunden und die eignen projkete
### diese routen können in meinem fall über die http methode get erreicht werden und führen dann den dazugehörigen code aus der dann die gewünschtendaten im intranet angefragt werden und zurück kommen im json format 

### das funktioniert so das wenn jemand bzw in dem fall der bot per http methode get und der richtigen routen url an die middlware anfrägt wird der code innherhalb der route ausgeführt  der dann in meinem fall die anfrage der gwüschten daten im Intranet ausführt 
### die schnittstellen im intranet waren bereits vorhanden und es muss leiglich mit den richtigen parametern angefragt werden 

## Sicherheit von middlware
### als sicherheits Mechanismus hat middlware ein client secred und client passwort mit der sie sich an der token schnittstelle des intranets einen token erstellen lassen kann und dieser token wird dann bei jeder zukünftigen schnittstellen Anfrage mitgeschcikt und vom intranet überprüft


## BOT
### den bot habe ich erstellt mit hilfe des teams toolkits da man dort direkt in visual studio code die grundstrucktur des bots erstellt bekommt und man ihn auch direkt loakl testen kann über ide
### das der bot auf anfragen von mitabrebiter reagieren kann habe ich 3 command händler erstellt wofüür ein commnd für eine route auf der middlware zuständig ist also auch eine art von informationen zurückgeben kann 
### diese sogenannten command handler funktinieren ähnlich wie die routen der middlware nur das sie nicht von http methoden angesprochen werden sonder soball im chat mit dem bot ein schlüsselbegriif für einen command fällt 
### zumbeispiel für die Kunden informationen wäre es das wort "Kunde" und ein namen dahinter sobald diese wort fällt führt der Bot den passenden comamnd handler aus, dieser überprüft erst ob der jenige der dem bot geschrieben hat überhaupt teilnehmer der Firma ist
### da auch gast Accounts auf unserem teams eingeladen sind, das wird überprüft anhand der email die auf seitwerk.de enden muss und der aktuellen mitarbeiter liste aus der graph api 
### sobald die überprüfung erfolgreich wird die url für den fetch an die middlware erzeugt dabei werden obligatorische parameter aus dem chat gezogen wie name des absenders und zb in diesem fall den kunden namen
### die middlware antwortet dann und schickt die gewünschten daten im json format zurück an den bot der sie dann formatiert und als nachricht im chat antwortet 


<li>Der Bot wurde mit Hilfe des Teams Toolkits erstellt, das direkt in Visual Studio Code die Grundstruktur des Bots generiert und lokale Tests ermöglicht.</li>
		<li>Um auf Anfragen von Mitarbeitern zu reagieren, wurden drei Command-Handler erstellt, wobei jeder Command für eine spezifische Route auf der Middleware zuständig ist und eine bestimmte Art von Informationen zurückgibt.</li>
		<li>Diese sogenannten Command-Handler funktionieren ähnlich wie die Routen der Middleware, werden jedoch nicht durch HTTP-Methoden angesprochen, sondern durch Schlüsselbegriffe im Chat aktiviert.</li>
		<li>Beispielsweise für Kundeninformationen ist der Schlüsselbegriff "Kunde" gefolgt von einem Namen. Sobald dieses Wort fällt, führt der Bot den passenden Command-Handler aus.</li>
		<li>Der Command-Handler überprüft zunächst, ob der Benutzer, der den Bot kontaktiert hat, tatsächlich ein Mitarbeiter der Firma ist. Diese Überprüfung erfolgt anhand der E-Mail-Adresse, die auf seitwerk.de enden muss, und der aktuellen Mitarbeiterliste aus der Graph API.</li>
		<li>Sobald die Überprüfung erfolgreich ist, wird die URL für den Fetch an die Middleware erzeugt. Dabei werden obligatorische Parameter aus dem Chat extrahiert, wie der Name des Absenders und beispielsweise der Kundenname.</li>
		<li>Die Middleware antwortet dann und schickt die gewünschten Daten im JSON-Format zurück an den Bot, der sie formatiert und als Nachricht im Chat antwortet.</li>
		<li>Beim Öffnen des Chats zeigt der Bot ein Auswahlfenster an, in dem alle drei Commands angezeigt und kurz erklärt werden. Dies erleichtert den Mitarbeitern die Auswahl und Nutzung der verfügbaren Funktionen.</li>


# 10. testing depleyn 
### nun kommen wir zum testing, wie ich schon in der implemntationpahse geannt habe konnte ich den Bot sehr leicht auf seine funktionlaität local testen mit hilfe des teamstoolkit 
### die middlware habe ich ebenso local auf meinem rechner testen können in dem ich sie gestartet und mit curl befeheln im terminal  die fetch anfragen des Bots imitiert habe 
### die kommunikation zwischen den systemen und die firewall reglen konnte ich erst testen nachdem ich die middlware auf einem schon vorhanden ubuntu server deployed habe, ich habe mich dabei entschieden dies per ssh und dem git clone verfahren zu machen
###  um so auf fehler oder zukünftige erweiterungen schnell regieren zu könnenn... nach dem die middlware erfolgreich deplyed war musste ich nur noch den bot auf die bereits vorhanden und konfikurtierten azure resource deployen
### dafür musste ebenfalls wie fürs testen des bot meinen microsoft acc verbinden und aus der ide deployen 

# 11. Fazit/Ausblick
### als letztes kommen wir noch zu meinem Fazit und zwar wurde das Projektziel erreicht und der Bot wird von mitarbeitern Verwendet und spaart diesen Zeit
### zum lession learnd punkt kann ich sagen das ich nun aufjedenfall weiß das sobald man mit Azure Produkten arbeitet man sich viel zeit für die doku nehemn muss 
### und für die zukunft ist schon eine erweiterungen für die inventar verwaltung geplant  