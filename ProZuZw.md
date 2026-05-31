---
title: "Projektübersicht Reinhard Wermeling"
author: "Reinhard Wermeling"
date: "Mai 2026"
---

<style>
@page {
  size: A4;
  margin: 18mm 16mm 18mm 16mm;
}

body {
  font-family: Arial, Helvetica, sans-serif;
  color: #222222;
  font-size: 11pt;
  line-height: 1.45;
}

h1 {
  color: #0b5cab;
  font-size: 24pt;
  border-bottom: 3px solid #0b5cab;
  padding-bottom: 8px;
  margin-top: 0;
  margin-bottom: 12px;
}

h2 {
  color: #0b5cab;
  font-size: 17pt;
  border-bottom: 1px solid #b7cde3;
  padding-bottom: 4px;
  margin-top: 26px;
  margin-bottom: 10px;
  page-break-after: avoid;
}

h3 {
  color: #1f6fb2;
  font-size: 13pt;
  margin-top: 18px;
  margin-bottom: 8px;
  page-break-after: avoid;
}

p {
  margin: 7px 0;
}

blockquote {
  background: #f1f3f5;
  border-left: 5px solid #0b5cab;
  margin: 12px 0 14px 0;
  padding: 10px 14px;
  color: #333333;
  page-break-inside: avoid;
}

blockquote p {
  margin: 4px 0;
}

table {
  width: 100%;
  border-collapse: collapse;
  margin: 14px 0 20px 0;
  font-size: 10.5pt;
  page-break-inside: avoid;
}

th {
  background: #0b5cab;
  color: #ffffff;
  padding: 7px 8px;
  text-align: left;
  font-weight: bold;
}

td {
  border: 1px solid #d8dde3;
  padding: 7px 8px;
  vertical-align: top;
}

tr:nth-child(even) td {
  background: #f5f6f8;
}

ul {
  margin-top: 6px;
  margin-bottom: 12px;
  padding-left: 22px;
}

li {
  margin-bottom: 4px;
}

strong {
  color: #1b1b1b;
}

hr {
  border: 0;
  border-top: 1px solid #d0d7de;
  margin: 24px 0;
}

.small {
  color: #666666;
  font-size: 10pt;
}

.warn {
  background: #fff3cd;
  border-left: 5px solid #d39e00;
  padding: 10px 14px;
  margin: 12px 0 14px 0;
  page-break-inside: avoid;
}
</style>

# ![Mein Logo](logorw96.jpg)  Projektübersicht Reinhard Wermeling

**Eigene Softwareprojekte, Elektronikentwicklungen und technische Analysen**

> **Quelle:** Facebook-Profil "Reiny Wer" - facebook.com/re.we.1884  
> **Stand:** Mai 2026  
> **Erstellt:** Mai 2026

## Übersicht

| # | Projekt | Datum | Kategorie |
|---:|---|---|---|
| 1 | Eisdiele BestellSoftware | 11. Mai 2026 | Software / Kassensystem |
| 2 | SmartHome von Rw | 01. April 2026 | Home-Automation / IoT |
| 3 | Fussball-Turnier-Verwaltung | 18. April 2026 | Web-App / Sport |
| 4 | Waschmaschinen-Melder ESP32 | 17. Januar 2026 | Hardware / Microcontroller |
| 5 | Waschmaschinen-Inverter Analyse | Mai 2026 | Elektronik / Leistungselektronik / Motorsteuerung |

---

## 01 Eisdiele BestellSoftware

> **Datum:** 11. Mai 2026  
> **Kategorie:** Software-Entwicklung / Kassensystem  
> **Projektname:** "Eisdiele San Remo V0.1"

Browser-basierte Kassensoftware für eine Eisdiele, entwickelt in **Delphi 12.1** mit **TMS Web Core** und **pas2js 2.3.1**. Die Anwendung läuft im Browser auf Windows und Android-Tablets, ist touch-optimiert und für eine spätere TSE-Anbindung vorbereitet.

### Funktionen

- Tisch-Verwaltung für Tisch 1-8, Theke und Mitnahme.
- Eigener Warenkorb pro Tisch mit automatischer Speicherung bei Tischwechsel.
- Tisch-Leiste zeigt jederzeit alle offenen Tische mit Summen.
- MwSt-Logik: Vor Ort 19%, Mitnahme 7%, Getränke immer 19%, pro Tisch umschaltbar.
- Artikel-Kacheln in vier Kategorien: Eis, Becher, Waffel und Getränk.
- Netto/MwSt/Brutto-Splitting für spätere Bondruck-Ausgabe.
- Bar/Karte/Storno-Buttons als Platzhalter für TSE- und Kartenterminal-Anbindung.
- Responsives Layout: Der Warenkorb rutscht am Tablet hochkant unter die Kacheln.

**Technologien:** Delphi 12.1, TMS Web Core, pas2js, HTML/Browser, Android

---

## 02 SmartHome von Rw

> **Datum:** 01. April 2026  
> **Kategorie:** Home-Automation / IoT

Eigenentwickeltes SmartHome-System mit **Shelly-Geräten** und **ESP32-Microcontrollern**. Die Steuerungssoftware wurde in Delphi entwickelt und bietet eine individuelle Anpassung sowie eine eigene Visualisierungsoberfläche für das Heimnetzwerk.

### Funktionen

- Integration von Shelly-Geräten für Licht, Steckdosen und Schalter.
- ESP32-Microcontroller als lokale Steuereinheiten.
- Entwickelt in Delphi mit individueller Oberfläche statt Standard-App.
- Eigene Visualisierung des Haus-Zustands in Echtzeit.
- Unabhängig von Cloud-Diensten durch lokale Verarbeitung im Heimnetz.

**Technologien:** Delphi, Shelly API, ESP32, WLAN/MQTT

---

## 03 Fussball-Turnier-Verwaltung

> **Datum:** 18. April 2026  
> **Kategorie:** Web-Applikation / Sport-Management  
> **Web:** ftmanager.de

Webbasierte Turnierverwaltungssoftware speziell für **Fussballturniere**. Die Anwendung ermöglicht eine einfache Verwaltung von Gruppenphasen und Jeder-gegen-Jeden-Formaten ohne Excel-Fehler und ohne Cloud-Abhängigkeit.

### Funktionen

- Teamverwaltung für bis zu 8 Teams.
- Automatische Tabellenberechnung in Echtzeit ohne Excel-Fehler.
- Mobile Ergebniseintragung direkt vor Ort.
- Live-Ergebnisse für Teams und Zuschauer sichtbar.
- Speicherung im Browser, DSGVO-konform und ohne Cloud.
- Responsives Design für PC, Tablet und Smartphone.
- Android-App verfügbar.
- Kostenlos nutzbar, Basisversion bis 4 Teams.

**Technologien:** Web-Technologien, JavaScript, Responsive Design, Android-App

---

## 04 Waschmaschinen-Melder ESP32

> **Datum:** 17. Januar 2026  
> **Kategorie:** Hardware-Entwicklung / IoT / Microcontroller

Eigenentwickeltes IoT-Gerät, das automatisch eine Benachrichtigung sendet, sobald die **Waschmaschine** ihren Waschgang beendet hat. Für dieses Projekt wurde eine eigene Leiterplatine entworfen und gefertigt.

### Funktionen

- Erkennt automatisch das Ende des Waschgangs.
- Sendet sofortige Benachrichtigung bei Programmende.
- Eigene Leiterplatine von Grund auf entworfen und gefertigt.
- Microcontroller: ESP32.
- Kompaktes, eigenständiges Gerät ohne externe Software.

**Technologien:** ESP32, eigene PCB-Platine, IoT, Elektronik-Entwicklung

---

## 05 Waschmaschinen-Inverter Analyse

> **Datum:** Mai 2026  
> **Kategorie:** Elektronik / Leistungselektronik / Motorsteuerung

Technische Analyse und Dokumentation einer Waschmaschinen-Motorsteuerung mit **Drehstrom-Asynchronmotor**. Untersucht wurde der Aufbau des Inverters mit **IGBT-Leistungsteil**, **IR2101-Halbbrückentreibern**, **Bootstrap-Schaltung** und **DC-Zwischenkreis**.

Die Ausarbeitung erklärt praxisnah, wie aus einem einphasigen **230-V-AC-Anschluss** über Gleichrichtung, Zwischenkreis und 3-Phasen-Inverter eine geregelte dreiphasige Motoransteuerung entsteht. Zusätzlich wurden Hintergrundwissen zur High-Side-Ansteuerung und sinnvolle Messungen zur Fehleranalyse dokumentiert.

### Inhaltliche Schwerpunkte

- Analyse des 3-Phasen-Inverters einer Waschmaschine.
- Erklärung von Gleichrichtung, DC-Zwischenkreis und PWM-Motoransteuerung.
- Beschreibung des IR2101 als High-/Low-Side-Gate-Treiber.
- Erklärung der Bootstrap-Schaltung für die High-Side-Ansteuerung.
- Betrachtung von Totzeit, Shoot-through-Vermeidung und IGBT-Schutz.
- Praxisorientierte Übersicht sinnvoller Messungen zur Fehlersuche.
- Einordnung des Drehstrom-Asynchronmotors im Betrieb an einem 230-V-Hausanschluss.

### Technischer Hintergrund

Obwohl die Waschmaschine nur an einem normalen **230-V-Wechselstromanschluss** betrieben wird, kann intern ein Drehstrom-Asynchronmotor verwendet werden. Dazu wird die Netzspannung zuerst gleichgerichtet. Aus 230 V AC entstehen im Zwischenkreis ungefähr **325 V DC**.

Aus dieser Gleichspannung erzeugt der Inverter mit sechs IGBTs drei pulsweitenmodulierte Motorphasen. Die drei Phasen werden zeitlich versetzt angesteuert, sodass im Motor ein rotierendes Magnetfeld entsteht. Dieses Drehfeld erzeugt das Drehmoment des Asynchronmotors.

Der **IR2101** dient dabei als Halbbrückentreiber. Pro Motorphase wird eine Halbbrücke aus einem oberen und einem unteren IGBT angesteuert. Für die High-Side-Ansteuerung wird ein Bootstrap-Kondensator verwendet, der als schwebende Hilfsspannung arbeitet. Dadurch kann das Gate des oberen IGBTs auch dann noch etwa 10-15 V über dessen Emitter angehoben werden, wenn der Schaltknoten bereits auf hoher Zwischenkreisspannung liegt.

### Nutzen der Dokumentation

Die erstellte Dokumentation dient als technische Grundlage zur Fehlersuche an einer Waschmaschinen-Motorsteuerung. Sie beschreibt nicht nur die Funktion einzelner Bauteile, sondern erklärt auch die Zusammenhänge zwischen Versorgungsspannung, Gate-Treiber, Bootstrap-Schaltung, PWM-Signalen und Motorverhalten.

Besonders hilfreich ist die strukturierte Messübersicht. Sie zeigt, welche Prüfungen zuerst spannungsfrei erfolgen sollten und welche Messungen im Betrieb nur mit geeigneter Ausrüstung und Fachkenntnis sinnvoll sind.

### Typische Analysepunkte

- Sichtprüfung der Leistungselektronik.
- Prüfung von Sicherung, NTC, Gleichrichter und Zwischenkreis.
- Messung der Zwischenkreisspannung.
- Prüfung der Hilfsspannungen für Logik und Gate-Treiber.
- Messung von VCC, COM, HIN, LIN, LO, HO, VB und VS am IR2101.
- Prüfung von Bootstrap-Diode und Bootstrap-Kondensator.
- Kontrolle der Gate-Widerstände und Gate-Emitter-Widerstände.
- Prüfung der IGBTs auf Kurzschluss oder Gate-Defekte.
- Vergleich der Motorwicklungswiderstände.
- Prüfung von Motorisolation, Temperaturfühler und Zusatzsensorik.

<div class="warn">

**Sicherheitshinweis:** Bei der untersuchten Schaltung treten lebensgefährliche Spannungen auf. Der DC-Zwischenkreis kann etwa **325 V** führen und auch nach dem Ausschalten noch geladen sein. Messungen an Netzspannung, Zwischenkreis, IGBT-Halbbrücken und High-Side-Treibern dürfen nur mit geeigneter Ausrüstung und entsprechender Fachkenntnis durchgeführt werden.

</div>

**Technologien:** Drehstrom-Asynchronmotor, IGBT, IR2101, Bootstrap-Schaltung, PWM, Frequenzumrichter, Leistungselektronik

---

## Zusammenfassung

> Die aufgeführten Projekte zeigen verschiedene Entwicklungsbereiche: browserbasierte Software, lokale SmartHome-Systeme, webbasierte Sportverwaltung, ESP32-Hardwareentwicklung und technische Analyse von Leistungselektronik.
>
> Der Schwerpunkt liegt auf praxisnahen Eigenentwicklungen mit direktem Nutzwert. Dabei reichen die Projekte von Delphi- und Web-Anwendungen über IoT-Geräte bis hin zur Analyse komplexer Motorsteuerungen mit Invertertechnik.

<p class="small">

**Quelle:** Facebook-Profil "Reiny Wer" - facebook.com/re.we.1884  
**Erstellt:** Mai 2026

</p>
