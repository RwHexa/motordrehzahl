 #  ![Mein Logo](logorw96.png)  Projektübersicht Reinhard Wermeling

Eigene Softwareprojekte, Elektronikentwicklungen und technische Analysen  
Quelle: Facebook-Profil "Reiny Wer" - facebook.com/re.we.1884  
Stand: Mai 2026

| # | Projekt | Datum | Kategorie |
|---:|---|---|---|
| 1 | Eisdiele BestellSoftware | 11. Mai 2026 | Software / Kassensystem |
| 2 | SmartHome von Rw | 01. April 2026 | Home-Automation / IoT |
| 3 | Fussball-Turnier-Verwaltung | 18. April 2026 | Web-App / Sport |
| 4 | Waschmaschinen-Melder ESP32 | 17. Januar 2026 | Hardware / Microcontroller |
| 5 | Waschmaschinen-Inverter Analyse | Mai 2026 | Elektronik / Leistungselektronik / Motorsteuerung |

---

## 01 Eisdiele BestellSoftware

**Datum:** 11. Mai 2026  
**Kategorie:** Software-Entwicklung / Kassensystem

Browser-basierte Kassensoftware fuer eine Eisdiele, entwickelt in Delphi 12.1 mit TMS Web Core und pas2js 2.3.1. Die Anwendung laeuft im Browser auf Windows und Android-Tablets, ist touch-optimiert und fuer eine spaetere TSE-Anbindung vorbereitet.

**Projektname:** "Eisdiele San Remo V0.1"

### Funktionen

- Tisch-Verwaltung fuer Tisch 1-8, Theke und Mitnahme.
- Eigener Warenkorb pro Tisch mit automatischer Speicherung bei Tischwechsel.
- Tisch-Leiste zeigt jederzeit alle offenen Tische mit Summen.
- MwSt-Logik: Vor Ort 19%, Mitnahme 7%, Getraenke immer 19%, pro Tisch umschaltbar.
- Artikel-Kacheln in vier Kategorien: Eis, Becher, Waffel und Getraenk.
- Netto/MwSt/Brutto-Splitting fuer spaetere Bondruck-Ausgabe.
- Bar/Karte/Storno-Buttons als Platzhalter fuer TSE- und Kartenterminal-Anbindung.
- Responsives Layout: Der Warenkorb rutscht am Tablet hochkant unter die Kacheln.

**Technologien:** Delphi 12.1, TMS Web Core, pas2js, HTML/Browser, Android

---

## 02 SmartHome von Rw

**Datum:** 01. April 2026  
**Kategorie:** Home-Automation / IoT

Eigenentwickeltes SmartHome-System mit Shelly-Geraeten und ESP32-Microcontrollern. Die Steuerungssoftware wurde in Delphi entwickelt und bietet eine individuelle Anpassung sowie eine eigene Visualisierungsoberflaeche fuer das Heimnetzwerk.

### Funktionen

- Integration von Shelly-Geraeten fuer Licht, Steckdosen und Schalter.
- ESP32-Microcontroller als lokale Steuereinheiten.
- Entwickelt in Delphi mit individueller Oberflaeche statt Standard-App.
- Eigene Visualisierung des Haus-Zustands in Echtzeit.
- Unabhaengig von Cloud-Diensten durch lokale Verarbeitung im Heimnetz.

**Technologien:** Delphi, Shelly API, ESP32, WLAN/MQTT

---

## 03 Fussball-Turnier-Verwaltung

**Datum:** 18. April 2026  
**Kategorie:** Web-Applikation / Sport-Management

Webbasierte Turnierverwaltungssoftware speziell fuer Fussballturniere. Die Anwendung ermoeglicht eine einfache Verwaltung von Gruppenphasen und Jeder-gegen-Jeden-Formaten ohne Excel-Fehler und ohne Cloud-Abhaengigkeit.

### Funktionen

- Teamverwaltung fuer bis zu 8 Teams.
- Automatische Tabellenberechnung in Echtzeit ohne Excel-Fehler.
- Mobile Ergebniseintragung direkt vor Ort.
- Live-Ergebnisse fuer Teams und Zuschauer sichtbar.
- Speicherung im Browser, DSGVO-konform und ohne Cloud.
- Responsives Design fuer PC, Tablet und Smartphone.
- Android-App verfuegbar.
- Kostenlos nutzbar, Basisversion bis 4 Teams.

**Technologien:** Web-Technologien, JavaScript, Responsive Design, Android-App  
**Web:** ftmanager.de

---

## 04 Waschmaschinen-Melder ESP32

**Datum:** 17. Januar 2026  
**Kategorie:** Hardware-Entwicklung / IoT / Microcontroller

Eigenentwickeltes IoT-Geraet, das automatisch eine Benachrichtigung sendet, sobald die Waschmaschine ihren Waschgang beendet hat. Fuer dieses Projekt wurde eine eigene Leiterplatine entworfen und gefertigt.

### Funktionen

- Erkennt automatisch das Ende des Waschgangs.
- Sendet sofortige Benachrichtigung bei Programmende.
- Eigene Leiterplatine von Grund auf entworfen und gefertigt.
- Microcontroller: ESP32.
- Kompaktes, eigenstaendiges Geraet ohne externe Software.

**Technologien:** ESP32, eigene PCB-Platine, IoT, Elektronik-Entwicklung

---

## 05 Waschmaschinen-Inverter Analyse

**Datum:** Mai 2026  
**Kategorie:** Elektronik / Leistungselektronik / Motorsteuerung

Technische Analyse und Dokumentation einer Waschmaschinen-Motorsteuerung mit Drehstrom-Asynchronmotor. Untersucht wurde der Aufbau des Inverters mit IGBT-Leistungsteil, IR2101-Halbbrueckentreibern, Bootstrap-Schaltung und DC-Zwischenkreis.

Die Ausarbeitung erklaert praxisnah, wie aus einem einphasigen 230-V-AC-Anschluss ueber Gleichrichtung, Zwischenkreis und 3-Phasen-Inverter eine geregelte dreiphasige Motoransteuerung entsteht. Zusaetzlich wurden Hintergrundwissen zur High-Side-Ansteuerung und sinnvolle Messungen zur Fehleranalyse dokumentiert.

### Inhaltliche Schwerpunkte

- Analyse des 3-Phasen-Inverters einer Waschmaschine.
- Erklaerung von Gleichrichtung, DC-Zwischenkreis und PWM-Motoransteuerung.
- Beschreibung des IR2101 als High-/Low-Side-Gate-Treiber.
- Erklaerung der Bootstrap-Schaltung fuer die High-Side-Ansteuerung.
- Betrachtung von Totzeit, Shoot-through-Vermeidung und IGBT-Schutz.
- Praxisorientierte Uebersicht sinnvoller Messungen zur Fehlersuche.
- Einordnung des Drehstrom-Asynchronmotors im Betrieb an einem 230-V-Hausanschluss.

### Technischer Hintergrund

Obwohl die Waschmaschine nur an einem normalen 230-V-Wechselstromanschluss betrieben wird, kann intern ein Drehstrom-Asynchronmotor verwendet werden. Dazu wird die Netzspannung zuerst gleichgerichtet. Aus 230 V AC entstehen im Zwischenkreis ungefaehr 325 V DC.

Aus dieser Gleichspannung erzeugt der Inverter mit sechs IGBTs drei pulsweitenmodulierte Motorphasen. Die drei Phasen werden zeitlich versetzt angesteuert, sodass im Motor ein rotierendes Magnetfeld entsteht. Dieses Drehfeld erzeugt das Drehmoment des Asynchronmotors.

Der IR2101 dient dabei als Halbbrueckentreiber. Pro Motorphase wird eine Halbbruecke aus einem oberen und einem unteren IGBT angesteuert. Fuer die High-Side-Ansteuerung wird ein Bootstrap-Kondensator verwendet, der als schwebende Hilfsspannung arbeitet. Dadurch kann das Gate des oberen IGBTs auch dann noch etwa 10-15 V ueber dessen Emitter angehoben werden, wenn der Schaltknoten bereits auf hoher Zwischenkreisspannung liegt.

### Nutzen der Dokumentation

Die erstellte Dokumentation dient als technische Grundlage zur Fehlersuche an einer Waschmaschinen-Motorsteuerung. Sie beschreibt nicht nur die Funktion einzelner Bauteile, sondern erklaert auch die Zusammenhaenge zwischen Versorgungsspannung, Gate-Treiber, Bootstrap-Schaltung, PWM-Signalen und Motorverhalten.

Besonders hilfreich ist die strukturierte Messuebersicht. Sie zeigt, welche Pruefungen zuerst spannungsfrei erfolgen sollten und welche Messungen im Betrieb nur mit geeigneter Ausruestung und Fachkenntnis sinnvoll sind.

### Typische Analysepunkte

- Sichtpruefung der Leistungselektronik.
- Pruefung von Sicherung, NTC, Gleichrichter und Zwischenkreis.
- Messung der Zwischenkreisspannung.
- Pruefung der Hilfsspannungen fuer Logik und Gate-Treiber.
- Messung von VCC, COM, HIN, LIN, LO, HO, VB und VS am IR2101.
- Pruefung von Bootstrap-Diode und Bootstrap-Kondensator.
- Kontrolle der Gate-Widerstaende und Gate-Emitter-Widerstaende.
- Pruefung der IGBTs auf Kurzschluss oder Gate-Defekte.
- Vergleich der Motorwicklungswiderstaende.
- Pruefung von Motorisolation, Temperaturfuehler und Zusatzsensorik.

### Sicherheitshinweis

Bei der untersuchten Schaltung treten lebensgefaehrliche Spannungen auf. Der DC-Zwischenkreis kann etwa 325 V fuehren und auch nach dem Ausschalten noch geladen sein. Messungen an Netzspannung, Zwischenkreis, IGBT-Halbbruecken und High-Side-Treibern duerfen nur mit geeigneter Ausruestung und entsprechender Fachkenntnis durchgefuehrt werden.

**Technologien:** Drehstrom-Asynchronmotor, IGBT, IR2101, Bootstrap-Schaltung, PWM, Frequenzumrichter, Leistungselektronik

---

## Zusammenfassung

Die aufgefuehrten Projekte zeigen verschiedene Entwicklungsbereiche: browserbasierte Software, lokale SmartHome-Systeme, webbasierte Sportverwaltung, ESP32-Hardwareentwicklung und technische Analyse von Leistungselektronik.

Der Schwerpunkt liegt auf praxisnahen Eigenentwicklungen mit direktem Nutzwert. Dabei reichen die Projekte von Delphi- und Web-Anwendungen ueber IoT-Geraete bis hin zur Analyse komplexer Motorsteuerungen mit Invertertechnik.

**Quelle:** Facebook-Profil "Reiny Wer" - facebook.com/re.we.1884  
**Erstellt:** Mai 2026
