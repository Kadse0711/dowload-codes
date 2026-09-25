Download Codes
Download Codes ist ein WordPress-Plugin zum Erstellen und Verwalten von Downloadcodes. Ein Code kann einen direkten Remote-Link oder eine Datei aus dem internen Speicher freigeben. Empfänger geben den Code auf einer WordPress-Seite ein oder erhalten ihn per E-Mail.

Funktionen
Downloadcodes automatisch erzeugen oder einen eigenen Code festlegen
Ablaufdatum und maximales Downloadlimit pro Code konfigurieren
HTTPS- und HTTP-Remote-Links hinterlegen
Eine Datei beim Erstellen eines Codes in den WordPress-Uploadbereich oder einen konfigurierten Speicherpfad hochladen
Codes aktivieren, deaktivieren oder löschen
Empfängeradresse und eine von zwei konfigurierbaren E-Mail-Vorlagen je Code auswählen
E-Mails als Text oder HTML versenden
Downloadversuche und Status im Adminbereich protokollieren
Updates über veröffentlichte GitHub-Releases erkennen
Voraussetzungen
Eine WordPress-Installation
PHP 7.0 oder neuer
Für E-Mail-Versand muss WordPress-E-Mail (wp_mail) auf dem Server funktionieren
Für interne Dateien benötigt der PHP-Prozess Lese- und Schreibzugriff auf den gewählten Speicherpfad
Die maximal erlaubte Uploadgröße richtet sich zusätzlich nach der PHP- und Serverkonfiguration, insbesondere upload_max_filesize und post_max_size.

Installation
Lade das Plugin-ZIP in WordPress unter Plugins > Plugin hinzufügen > Plugin hochladen hoch.
Installiere und aktiviere Download Codes.
Öffne im WordPress-Adminmenü Download Codes > Einstellungen.
Erstelle eine WordPress-Seite für die Codeeingabe und füge den Shortcode [download] ein.
Trage die vollständige URL dieser Seite im Feld Download-Seite ein.
Prüfe Absendername, Absender-E-Mail und E-Mail-Text. Sende bei Bedarf eine Testmail, um die Mailkonfiguration deines Servers zu kontrollieren.
Schnellstart
1. Download-Seite einrichten
Lege eine Seite an, zum Beispiel „Download“, und setze diesen Shortcode in den Seiteninhalt:


Besucher sehen ein Eingabefeld für ihren Downloadcode. Der optionale Titel ändert die Beschriftung des Absende-Buttons:


Der ältere Alias [nas_download] wird weiterhin unterstützt.

2. Seitenadresse konfigurieren
Gehe zu Download Codes > Einstellungen und trage im Feld Download-Seite die vollständige URL der Seite mit dem Shortcode ein, zum Beispiel:


Diese Adresse wird für Download-Links in E-Mails verwendet. Wenn das Feld leer ist, verwendet das Plugin als Ersatz die Startseite der Website. Für verlässliche Code-Links sollte die tatsächliche Download-Seite eingetragen werden.

3. Downloadcode erstellen
Öffne Download Codes > Download-Codes und fülle das Formular aus:

Empfänger-E-Mail: optional. Ist eine gültige Adresse eingetragen, sendet WordPress den Code nach dem Erstellen per E-Mail.
E-Mail-Vorlage: Standard oder eine der beiden Vorlagen aus den Einstellungen.
Code: optional. Bleibt das Feld leer, erzeugt das Plugin einen Code. Eigene Codes werden auf Großbuchstaben und Ziffern reduziert und in Gruppen formatiert.
Ablaufdatum: optional. Der Code ist bis zum Ende des gewählten Tages gültig.
Max Downloads: 0 bedeutet unbegrenzt. Ein positiver Wert begrenzt die Zahl der Einlösungen.
Dateiquelle: Remote-Link oder interner Speicher.
Remote-Link: vollständige URL zur Datei. Ein direkter HTTPS-Link wird empfohlen.
Datei: bei interner Speicherung die hochzuladende Datei.
Link-Bezeichnung: optionaler Anzeigename, der in der E-Mail anstelle des URL- oder Dateinamens verwendet wird.
Das aktuelle Erstellungsformular nimmt pro neuem Code eine Dateiquelle entgegen. Codes erscheinen danach in der Liste Bestehende Codes. Dort kannst du sie aktivieren, deaktivieren oder löschen.

Remote-Links und interne Dateien
Remote-Link
Gib einen direkten Link zur Datei an, nicht zu einer HTML-Seite mit einem Downloadbutton. Bei einem einzelnen Remote-Link leitet das Plugin den Besucher nach erfolgreicher Codeprüfung direkt zur Zieladresse weiter.

Die Datei wird in diesem Fall nicht durch WordPress übertragen. Zugriff, Downloadverfügbarkeit und zusätzliche Schutzmaßnahmen hängen daher auch vom Server ab, auf dem die Remote-Datei liegt. Nach der Weiterleitung kann der Empfänger die Zieladresse sehen und weitergeben. Ein Downloadlimit zählt die erfolgreiche Weiterleitung, nicht den Abschluss der Dateiübertragung auf dem entfernten Server.

Interne Datei
Bei leerem Interner Speicherpfad unter Einstellungen speichert das Plugin die hochgeladene Datei im WordPress-Uploadverzeichnis. Alternativ kannst du dort einen absoluten Pfad angeben, etwa einen auf dem Server eingebundenen NAS- oder KAS-Pfad.

Der Pfad muss für den PHP-Prozess erreichbar und beschreibbar sein. Bei einem Netzwerkspeicher muss der Mount dauerhaft verfügbar sein und mit passenden Berechtigungen eingebunden werden. Ein lokaler Dateipfad ist nicht die URL einer Website.

Wichtig: Dateien im WordPress-Uploadverzeichnis können je nach Serverkonfiguration auch direkt über den Webserver erreichbar sein. Für vertrauliche Dateien sollte ein Speicherort außerhalb des öffentlich erreichbaren Webverzeichnisses verwendet und der Serverzugriff entsprechend abgesichert werden. Teste den Zugriff auf Dateien mit einem nicht eingelösten Code, bevor du vertrauliche Inhalte verteilst.

E-Mail-Einstellungen
Unter Download Codes > Einstellungen kannst du Absendername, Absenderadresse, Betreff und Standardtext bearbeiten. Zusätzlich gibt es zwei benannte Vorlagen. Ihre Namen erscheinen beim Erstellen eines Codes im Auswahlfeld.

Folgende Platzhalter werden ersetzt:

Platzhalter	Inhalt
{code}	Der Downloadcode
{url}	Die URL zur Downloadseite mit dem Code
{files}	Die Dateinamen beziehungsweise Anzeigenamen des Codes
Beispiel für eine Textvorlage:


Für HTML-E-Mails aktiviere E-Mail als HTML senden. Diese Einstellung gilt für den Standardtext und beide Vorlagen. Ob E-Mails tatsächlich zugestellt werden, hängt von der WordPress- und Server-Mailkonfiguration ab. Bei Problemen empfiehlt sich ein SMTP-Plugin oder die Unterstützung des Hosting-Anbieters.

Codeprüfung und Downloads
Beim Einlösen prüft das Plugin, ob der Code vorhanden und aktiv ist, ob sein Ablaufdatum erreicht wurde und ob das Downloadlimit überschritten ist. Ein einzelner Remote-Link führt direkt zur Zieladresse. Eine interne Datei wird über WordPress ausgeliefert.

Für Codes mit mehreren Dateien zeigt das Plugin eine Auswahlseite an. Das aktuelle Adminformular erstellt pro Code zunächst eine Dateiquelle; die Mehrdateien-Auswahl greift, wenn einem Code mehrere Dateien zugewiesen sind.

Downloadzahlen werden bei der Weiterleitung beziehungsweise beim Start der internen Dateiauslieferung erhöht. Sie bestätigen nicht, dass ein Empfänger die Datei vollständig gespeichert hat.

Dashboard und Protokolle
Das Dashboard zeigt die Anzahl aktiver Codes, die in den letzten 24 Stunden protokollierten Downloads und die letzten Einträge. Unter Download Codes > Logs findest du die jüngsten Downloadereignisse mit Datum, Code, Datei, Benutzer, IP-Adresse, Status und Nachricht.

Die Protokolle enthalten personenbezogene beziehungsweise technische Daten, insbesondere IP-Adressen und User-Agent-Angaben. Informiere deine Besucher in der Datenschutzerklärung über diese Verarbeitung und lege fest, wie lange du die Protokolle aufbewahrst. Das Plugin stellt derzeit keine eigene automatische Löschfrist für Logs bereit.

Codes deaktivieren und löschen
Deaktivieren: Der Code bleibt gespeichert, kann aber nicht eingelöst werden. Du kannst ihn später wieder aktivieren.
Löschen: Entfernt den Code aus der Datenbank. Ein gelöschter Code kann nicht wiederhergestellt werden.
Ablaufdatum: Nach Ablauf wird der Code abgelehnt.
Downloadlimit: Bei 0 unbegrenzt; ansonsten wird der Code nach Erreichen des Limits abgelehnt.
Das Löschen eines Codes entfernt nicht automatisch die zugehörige Datei aus dem Speicher.

Automatische Updates über GitHub
Der Updater fragt das konfigurierte öffentliche GitHub-Repository nach dem neuesten veröffentlichten Release ab. Damit WordPress ein Update anbieten kann:

Erhöhe die Plugin-Version im Plugin-Header und den Wert von NDM_VERSION in nas-download-manager.php.
Übertrage die Änderungen in das GitHub-Repository.
Veröffentliche dort einen stabilen GitHub-Release mit einem Versions-Tag, zum Beispiel v1.1.2. Der Tag muss neuer sein als die installierte Plugin-Version.
WordPress erkennt das Update beim nächsten Update-Check. Update-Prüfungen können von WordPress zwischengespeichert werden.
Der Updater verwendet ein ZIP-Asset des Releases, falls vorhanden; andernfalls verwendet er das von GitHub bereitgestellte Quellcode-Archiv. Ein Release muss öffentlich erreichbar sein. Ein Commit oder Tag allein ohne veröffentlichten Release reicht für den aktuellen Updater nicht aus.

Fehlerbehebung
Der Shortcode zeigt kein Eingabefeld an

Prüfe, ob [download] im Seiteninhalt steht und das Plugin aktiviert ist.
Prüfe, ob ein Page-Builder oder Cache-Plugin den Shortcode-Inhalt verändert oder zwischenspeichert.
Der E-Mail-Link öffnet die falsche Seite

Trage unter Einstellungen > Download-Seite die vollständige Adresse der Seite mit dem Shortcode ein.
Prüfe, ob die Website HTTPS verwendet und die Adresse erreichbar ist.
Der Code wird abgelehnt

Prüfe, ob der Code korrekt eingegeben wurde und noch aktiv ist.
Prüfe Ablaufdatum und Downloadlimit in der Codeübersicht.
Deaktiviere testweise Caching auf der Download-Seite oder schließe die Codeeingabe und Download-URL vom Seiten-Cache aus.
Eine interne Datei kann nicht gespeichert oder ausgeliefert werden

Prüfe, ob der Speicherpfad existiert und der PHP-Prozess dort lesen und schreiben darf.
Prüfe bei NAS-Mounts, ob der Mount im Kontext des Webserver-Prozesses verfügbar ist.
Prüfe die Uploadgrößenlimits von PHP und Webserver.
Eine E-Mail kommt nicht an

Kontrolliere die Absenderadresse und die Mailkonfiguration des Servers.
Prüfe Spam-Ordner und Mail-Logs. WordPress kann einen Versand anfordern, aber die Zustellung nicht garantieren.
WordPress zeigt kein Plugin-Update an

Prüfe, ob ein öffentlicher GitHub-Release veröffentlicht wurde.
Prüfe, ob der Release-Tag eine höhere Version als die installierte Plugin-Version enthält.
Starte in WordPress eine erneute Update-Prüfung; durch Caching kann die Erkennung verzögert sein.
Deinstallation und Datensicherung
Das Deaktivieren des Plugins löscht die Codes und Protokolle nicht. Wenn du das Plugin über WordPress löschst, entfernt uninstall.php die Plugin-Datenbanktabellen und gespeicherten Einstellungen. Die eigentlichen hochgeladenen Dateien werden dabei nicht automatisch gelöscht. Sichere benötigte Daten und Dateien vor einer Deinstallation.

Datenschutz und Sicherheit
Verwende für Website, Download-Seite und Remote-Ziele nach Möglichkeit HTTPS.
Teile Codes nur mit den vorgesehenen Empfängern; Codes sind Zugriffsschlüssel.
Vertrauliche Dateien sollten nicht in einem öffentlich erreichbaren Upload-Verzeichnis liegen.
Beschränke Administratorzugriff auf Personen, die Codes und Dateien verwalten müssen.
Berücksichtige IP-Adressen und User-Agent-Daten in Logs in deiner Datenschutzerklärung.
Verwende für zuverlässigen E-Mail-Versand eine korrekt konfigurierte Mail- beziehungsweise SMTP-Infrastruktur.
