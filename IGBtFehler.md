# Zusatz zur Abhandlung: Sinnvolle Messungen zur Fehleranalyse an einem Waschmaschinen-Inverter mit IR2101 und IGBT

## 1. Zweck dieses Zusatzes

Dieser Zusatz beschreibt sinnvolle Messungen zur Fehleranalyse an einem Inverter einer Waschmaschine mit Drehstrom-Asynchronmotor, IGBTs und IR2101-Halbbrückentreibern.

Ziel ist nicht, eine Reparaturanleitung für Arbeiten unter Netzspannung zu ersetzen, sondern eine strukturierte Übersicht zu geben, welche Messpunkte grundsätzlich hilfreich sind und welche Aussagen sich daraus ableiten lassen.

Die Messungen betreffen vor allem diese Baugruppen:

- Netzeingang und Gleichrichtung,
- DC-Zwischenkreis,
- Hilfsspannungen,
- IR2101-Gate-Treiber,
- Bootstrap-Schaltung,
- IGBT-Halbbrücken,
- Motoranschlüsse,
- Strommessung und Schutzschaltungen,
- Sensorik des Motors.

## 2. Wichtige Sicherheitsregeln

In einem Waschmaschinen-Inverter treten lebensgefährliche Spannungen auf. Der Zwischenkreis kann bei Betrieb etwa 325 V DC führen. Auch nach dem Ausschalten können Zwischenkreiskondensatoren noch geladen sein.

Vor jeder Messung gilt:

- Nur messen, wenn ausreichende Fachkenntnisse vorhanden sind.
- Gerät vor Widerstands- und Diodenmessungen vollständig spannungsfrei machen.
- Zwischenkreiskondensator kontrolliert entladen.
- Spannungsfreiheit mit geeignetem Messgerät überprüfen.
- Niemals blind auf Leiterplattenmasse vertrauen.
- DC- ist nicht automatisch Schutzleiter oder Erde.
- Bei Messungen im Betrieb nur geeignete isolierte Messmittel verwenden.
- Ein normales Oszilloskop mit Schutzleiter-Masseclip darf nicht beliebig an den Zwischenkreis oder an Schaltknoten angeschlossen werden.
- Für High-Side- und Halbbrückenmessungen sind Differentialtastköpfe oder isolierte Messsysteme erforderlich.
- Schmuck, lose Leitungen und provisorische Messspitzen vermeiden.
- Möglichst mit Trenntransformator, Strombegrenzung und vorgeschalteter Schutzmaßnahme arbeiten, sofern fachlich korrekt eingesetzt.

Ein besonders gefährlicher Fehler ist das Anschließen der Oszilloskop-Masse an einen Punkt, der nicht auf Erdpotential liegt. Dadurch kann ein Kurzschluss über den Schutzleiter entstehen.

## 3. Empfohlene Messgeräte

Für eine sinnvolle Fehleranalyse sind folgende Messmittel hilfreich:

| Messgerät | Zweck |
|---|---|
| Digitalmultimeter | Spannungen, Widerstände, Diodentest, Durchgang |
| Isolationsmessgerät | Prüfung von Motorwicklung gegen Gehäuse, nur fachgerecht einsetzen |
| Oszilloskop | PWM, Gate-Signale, Treibersignale, Ripple |
| Differentialtastkopf | Messung an Schaltknoten, Gate-Emitter High-Side, Zwischenkreis |
| Stromzange | Motorstrom und Netzstrom, möglichst True-RMS |
| ESR-Meter | Zustand von Elektrolytkondensatoren, nur spannungsfrei |
| Labornetzteil | Prüfung von Hilfsspannungszweigen, wenn Schaltung geeignet ist |
| Serienlampe oder Strombegrenzung | Begrenzung bei Erstinbetriebnahme nach Reparatur |

Eine Serienlampe kann bei klassischen Netzteilen hilfreich sein, ist bei getakteten Invertersteuerungen aber nicht immer eindeutig interpretierbar. Sie ersetzt keine fachgerechte Schutz- und Prüftechnik.

## 4. Messungen im spannungsfreien Zustand

Viele Fehler lassen sich bereits ohne Netzspannung finden. Diese Messungen sind sicherer und sollten vor Messungen im Betrieb erfolgen.

### 4.1 Sichtprüfung

Eine sorgfältige Sichtprüfung ist oft der erste und wichtigste Schritt.

Zu prüfen sind:

- geplatzte oder gewölbte Elektrolytkondensatoren,
- verbrannte Widerstände,
- gerissene Lötstellen,
- dunkle Stellen unter Leistungshalbleitern,
- beschädigte Leiterbahnen,
- lose Steckverbinder,
- Korrosion oder Feuchtigkeitsspuren,
- gebrochene Relais- oder Steckerlötstellen,
- verfärbte Gate-Widerstände,
- beschädigte Shunt-Widerstände,
- aufgeplatzte IGBTs oder Treiber-ICs.

Besonders bei Waschmaschinen sind Feuchtigkeit, Waschmittelrückstände und Vibrationen typische Ursachen für Fehler.

### 4.2 Sicherung und Einschaltstrombegrenzung

Mit dem Multimeter im Durchgangs- oder Widerstandsbereich lassen sich Sicherung, NTC und Leiterbahnen prüfen.

Typische Punkte:

| Bauteil | Erwartung |
|---|---|
| Netzsicherung | niederohmig, sofern intakt |
| NTC-Einschaltstrombegrenzer | meist einige Ohm bis einige zehn Ohm bei Raumtemperatur |
| Leiterbahn vom Netzeingang | niederohmig, keine Unterbrechung |
| Relaiskontakte, falls vorhanden | je nach Zustand offen oder niederohmig |

Ist die Sicherung ausgelöst, sollte sie nicht einfach ersetzt werden. Häufig liegt ein Kurzschluss im Gleichrichter, Zwischenkreis oder IGBT-Leistungsteil vor.

### 4.3 Brückengleichrichter prüfen

Der Brückengleichrichter kann mit der Diodentestfunktion geprüft werden. Dabei sollten die einzelnen Diodenstrecken jeweils in Durchlassrichtung eine typische Diodenspannung anzeigen und in Sperrrichtung hochohmig sein.

Auffällige Befunde:

| Messbefund | Mögliche Ursache |
|---|---|
| Kurzschluss zwischen AC und DC+ | Gleichrichter defekt |
| Kurzschluss zwischen AC und DC- | Gleichrichter defekt |
| Kurzschluss zwischen DC+ und DC- | Gleichrichter, Elko oder IGBT-Stufe defekt |
| In beide Richtungen leitend | Diodenstrecke defekt |
| In beide Richtungen offen | Unterbrechung oder Messfehler |

Ein defekter Gleichrichter geht häufig zusammen mit einer ausgelösten Sicherung einher.

### 4.4 DC-Zwischenkreis auf Kurzschluss prüfen

Zwischen DC+ und DC- sollte im spannungsfreien Zustand kein harter Kurzschluss messbar sein. Direkt nach dem Anlegen der Messspitzen kann der Widerstand durch das Laden des Zwischenkreiskondensators zunächst niedrig erscheinen und dann ansteigen.

Typische Interpretation:

| Messung DC+ gegen DC- | Bewertung |
|---|---|
| Widerstand steigt langsam an | Kondensator lädt über Messgerät, oft normal |
| dauerhaft sehr niederohmig | Verdacht auf Kurzschluss |
| nahezu 0 Ohm | schwerer Fehler im Gleichrichter, Elko oder IGBT-Zweig |
| völlig offen | kann je nach Schaltung normal sein oder Unterbrechung bedeuten |

Bei einem harten Kurzschluss sollte die Platine nicht ans Netz angeschlossen werden.

### 4.5 Zwischenkreiskondensator prüfen

Der große Elektrolytkondensator im Zwischenkreis ist stark belastet. Sichtprüfung und ESR-Messung können Hinweise geben.

Zu prüfen sind:

- Kapazitätsverlust,
- erhöhter ESR,
- aufgeblähter Deckel,
- ausgelaufener Elektrolyt,
- schlechte Lötstellen,
- lose Anschlussdrähte.

Ein schlechter Zwischenkreiskondensator kann zu Brummen, Fehlstarts, Abschaltungen, Überspannungsfehlern oder instabilem Inverterbetrieb führen.

### 4.6 IGBTs mit Diodentest prüfen

IGBTs besitzen häufig antiparallele Freilaufdioden. Mit dem Diodentest kann man grob prüfen, ob Kurzschlüsse zwischen Kollektor und Emitter vorliegen.

Wichtige Prüfungen je IGBT:

| Messstrecke | Erwartung |
|---|---|
| Kollektor zu Emitter | kein harter Kurzschluss |
| Emitter zu Kollektor | Freilaufdiode je nach Richtung messbar |
| Gate zu Emitter | hochohmig |
| Gate zu Kollektor | hochohmig |

Ein Kurzschluss zwischen Gate und Emitter oder Gate und Kollektor deutet auf einen zerstörten IGBT hin. Ein Kurzschluss zwischen Kollektor und Emitter ist ebenfalls ein schwerer Defekt.

Bei eingebauten IGBTs können Parallelpfade die Messung verfälschen. Im Zweifel muss mindestens ein Anschluss ausgelötet oder das Datenblatt des Leistungsteils berücksichtigt werden.

### 4.7 Gate-Widerstände prüfen

Gate-Widerstände liegen zwischen Treiberausgang und IGBT-Gate. Sie begrenzen den Gate-Strom und beeinflussen die Schaltgeschwindigkeit.

Zu prüfen sind:

- Widerstandswert,
- Unterbrechung,
- Verfärbung,
- kalte Lötstelle,
- Unterschied zwischen den drei Phasen.

Typische Werte können im Bereich weniger Ohm bis einige zehn Ohm liegen. Der exakte Wert hängt von der Schaltung ab.

Ein unterbrochener Gate-Widerstand führt dazu, dass der IGBT nicht mehr richtig angesteuert wird. Ein stark veränderter Wert kann Schaltfehler, Erwärmung oder ungleichmäßigen Betrieb verursachen.

### 4.8 Gate-Emitter-Widerstände prüfen

Oft liegt zwischen Gate und Emitter ein Widerstand, der den IGBT sicher ausgeschaltet hält, wenn der Treiber hochohmig ist.

Typische Werte liegen häufig im Bereich einiger Kiloohm bis einige zehn Kiloohm.

Ein unterbrochener Gate-Emitter-Widerstand kann dazu führen, dass das Gate undefiniert schwebt. Ein zu niedriger Wert kann die Gate-Ansteuerung belasten.

### 4.9 Bootstrap-Diode prüfen

Die Bootstrap-Diode lädt den Bootstrap-Kondensator aus der Treiberversorgung. Sie sollte in Durchlassrichtung leiten und in Sperrrichtung sperren.

Mögliche Fehler:

| Fehler | Wirkung |
|---|---|
| Diode unterbrochen | High-Side-Bootstrap wird nicht geladen |
| Diode kurzgeschlossen | Rückspeisung in die Treiberversorgung, Treiberfehler möglich |
| Diode zu langsam oder gealtert | instabile High-Side-Ansteuerung |
| schlechte Lötstelle | sporadischer Ausfall |

Bei einer defekten Bootstrap-Diode kann die Low-Side noch funktionieren, während die High-Side ausfällt oder nur kurzzeitig arbeitet.

### 4.10 Bootstrap-Kondensator prüfen

Der Bootstrap-Kondensator sollte auf Kapazität, Kurzschluss und schlechte Lötstellen geprüft werden.

Typische Fehler:

- Kapazitätsverlust,
- Keramikkondensator gerissen,
- Kurzschluss,
- kalte Lötstelle,
- falscher Ersatztyp,
- zu geringe Spannungsfestigkeit.

Ein zu kleiner oder defekter Bootstrap-Kondensator führt dazu, dass die High-Side-Spannung während der Einschaltzeit zusammenbricht.

### 4.11 Shunt-Widerstand prüfen

Viele Inverter messen den Motor- oder Zwischenkreisstrom über einen niederohmigen Shunt. Dieser liegt oft im negativen Zwischenkreis oder in den Phasen.

Zu prüfen sind:

- Unterbrechung,
- sichtbare Überlastung,
- exakter Widerstandswert,
- Lötstellen,
- Leiterbahnverbindungen zur Auswertung.

Da Shunts sehr niederohmig sind, ist eine normale Zweileitermessung oft ungenau. Für genaue Werte ist eine Vierleitermessung sinnvoll.

Ein defekter Shunt kann dazu führen, dass die Steuerung falsche Überstromwerte erkennt oder einen echten Überstrom nicht erkennt.

## 5. Messungen an der Motorseite

Vor dem Verdacht auf die Elektronik sollte auch der Motor geprüft werden.

### 5.1 Wicklungswiderstände messen

Bei einem dreiphasigen Asynchronmotor sollten die Widerstände zwischen den drei Motoranschlüssen annähernd gleich sein.

Zu messen sind:

| Messung | Erwartung |
|---|---|
| U gegen V | Widerstandswert A |
| V gegen W | Widerstandswert B |
| W gegen U | Widerstandswert C |

Die drei Werte sollten möglichst ähnlich sein. Deutliche Abweichungen weisen auf Wicklungsschäden, Kontaktprobleme oder falsche Zuordnung der Anschlüsse hin.

Sehr kleine Motoren können niedrige Widerstände haben. Deshalb sind absolute Werte allein weniger aussagekräftig als der Vergleich der drei Phasen.

### 5.2 Isolation gegen Motorgehäuse prüfen

Die Wicklungen dürfen keine leitende Verbindung zum Motorgehäuse haben. Diese Prüfung sollte mit einem geeigneten Isolationsmessgerät erfolgen.

Zu prüfen sind:

- U gegen Gehäuse,
- V gegen Gehäuse,
- W gegen Gehäuse.

Ein niedriger Isolationswiderstand ist ein schwerer Sicherheitsfehler. Der Motor darf dann nicht weiter betrieben werden.

Bei Elektronik mit angeschlossenem Motor sollte die Isolationsmessung nur so durchgeführt werden, dass keine empfindliche Elektronik beschädigt wird. Häufig muss der Motor dafür von der Steuerung getrennt werden.

### 5.3 Temperaturfühler oder Motorschutz prüfen

Waschmaschinenmotoren können zusätzliche Anschlüsse für Temperaturfühler, Thermoschalter oder Motorschutz besitzen.

Typische Bauteile:

| Bauteil | Verhalten |
|---|---|
| NTC | Widerstand sinkt bei steigender Temperatur |
| PTC | Widerstand steigt stark bei Temperatur |
| Thermoschalter | öffnet oder schließt bei Grenztemperatur |
| Tacho | erzeugt drehzahlabhängige Spannung |
| Hallgeber | erzeugt digitale Positionssignale |

Ein defekter Temperaturfühler kann dazu führen, dass die Steuerung den Motor nicht freigibt oder frühzeitig abschaltet.

## 6. Messungen im Betrieb

Messungen im Betrieb sind deutlich gefährlicher und sollten nur mit geeigneter Ausrüstung und Fachkenntnis erfolgen.

### 6.1 Netzspannung prüfen

Am Eingang sollte die Netzspannung im zulässigen Bereich liegen. In Deutschland sind typischerweise etwa 230 V AC zu erwarten.

Zu prüfen sind:

| Messpunkt | Erwartung |
|---|---|
| L gegen N | etwa 230 V AC |
| L gegen PE | etwa 230 V AC |
| N gegen PE | nahe 0 V, abhängig von Installation |

Abweichungen können auf Netzprobleme, schlechte Steckverbindungen oder Installationsfehler hinweisen.

### 6.2 Zwischenkreisspannung messen

Nach dem Gleichrichter und dem Zwischenkreiskondensator sollte bei 230 V AC Netzspannung ungefähr 325 V DC anliegen.

Die Näherung lautet:

$$
U_\text{DC} \approx U_\text{AC} \cdot \sqrt{2}
$$

Bei 230 V AC ergibt sich:

$$
U_\text{DC} \approx 325\,\text{V}
$$

Typische Interpretation:

| Gemessene Zwischenkreisspannung | Mögliche Bedeutung |
|---|---|
| ca. 300 V bis 330 V DC | normal, abhängig von Netzspannung und Last |
| deutlich zu niedrig | Gleichrichter, Vorwiderstand, Relais, Elko oder Netzproblem |
| stark pulsierend | Zwischenkreiskondensator schwach |
| 0 V | keine Netzversorgung, Sicherung, Gleichrichter oder Leiterbahnfehler |
| deutlich zu hoch | Messfehler, Netzfehler oder Rückspeisung beim Bremsen |

Beim Bremsen eines Motors kann Energie in den Zwischenkreis zurückgespeist werden. Falls keine geeignete Brems- oder Regelstrategie vorhanden ist, kann die Zwischenkreisspannung ansteigen.

### 6.3 Hilfsspannungen prüfen

Der IR2101 benötigt eine Treiberversorgung, häufig 12 V bis 15 V. Zusätzlich benötigt die Steuerung meist 5 V oder 3,3 V.

Typische Hilfsspannungen:

| Spannung | Zweck |
|---|---|
| 15 V | Gate-Treiber-Versorgung |
| 12 V | Relais, Treiber, Hilfszweige |
| 5 V | Mikrocontroller, Sensorik |
| 3,3 V | moderne Logik oder Mikrocontroller |

Fehlen diese Spannungen oder brechen sie unter Last ein, kann der Inverter nicht korrekt arbeiten.

Wichtig ist auch die Restwelligkeit. Eine scheinbar richtige Gleichspannung kann durch starken Ripple trotzdem unbrauchbar sein.

### 6.4 VCC am IR2101 messen

Zwischen VCC und COM des IR2101 sollte die Treiberversorgung anliegen. Je nach Schaltung liegt sie häufig bei etwa 12 V bis 15 V.

Bewertung:

| Messung VCC-COM | Bedeutung |
|---|---|
| ca. 12 V bis 15 V | typischer Arbeitsbereich |
| deutlich darunter | Treiber kann abschalten oder IGBT nicht sauber ansteuern |
| 0 V | Versorgung fehlt |
| stark schwankend | Überlast, defekter Treiber, defekte Versorgung |
| zu hoch | Gefahr für Treiber und Gate |

Bei zu niedriger VCC greift eventuell die Unterspannungsabschaltung des Treibers. Dann bleiben die Ausgänge aus.

### 6.5 Logikeingänge HIN und LIN prüfen

Die Eingänge HIN und LIN erhalten PWM-Signale vom Mikrocontroller. Mit dem Oszilloskop kann geprüft werden, ob diese Signale vorhanden sind.

Zu beachten:

- HIN steuert die High-Side.
- LIN steuert die Low-Side.
- Beide Signale einer Halbbrücke dürfen nicht gleichzeitig aktiv sein.
- Zwischen den Umschaltvorgängen muss Totzeit vorhanden sein.
- Die Pegel müssen zum IR2101 passen.

Mögliche Befunde:

| Beobachtung | Mögliche Ursache |
|---|---|
| kein PWM-Signal | Mikrocontroller sperrt Inverter, Fehlerbedingung, Versorgung fehlt |
| nur LIN aktiv | Startzustand, Bootstrap-Ladung oder High-Side-Fehler |
| HIN und LIN überlappen | gefährlicher Steuerungsfehler |
| falsche Pegelhöhe | Logikversorgung oder Treiberinkompatibilität |
| unruhige Signale | Störung, Masseproblem oder Controllerfehler |

### 6.6 LO-Ausgang prüfen

LO ist der Ausgang für den unteren IGBT. Er wird gegen COM gemessen.

Ein aktives LO-Signal
