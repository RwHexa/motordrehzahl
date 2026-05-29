# Abhandlung: Bootstrap-Kondensator im 3-Phasen-Inverter einer Waschmaschine mit IR2101 und IGBT ![Lokales Bild](logorw96.png)

## 1. Einleitung

In modernen Waschmaschinen werden häufig Drehstrommotoren eingesetzt, obwohl das Gerät selbst nur an einem normalen einphasigen 230-V-Wechselstromnetz angeschlossen ist. Der benötigte dreiphasige Strom für den Motor wird intern durch eine Leistungselektronik erzeugt. Diese Leistungselektronik wird üblicherweise als Frequenzumrichter oder Inverter bezeichnet.

Bei einem Drehstrom-Asynchronmotor besteht der Leistungsteil des Inverters aus drei Halbbrücken. Jede Halbbrücke erzeugt eine der drei Motorphasen. Eine Halbbrücke besteht aus einem oberen und einem unteren Leistungsschalter, beispielsweise aus IGBTs. Zur Ansteuerung dieser IGBTs werden Gate-Treiber verwendet. Ein häufig verwendeter Treiberbaustein für eine solche Halbbrücke ist der IR2101.

Der IR2101 kann sowohl einen unteren Leistungsschalter, die sogenannte Low-Side, als auch einen oberen Leistungsschalter, die sogenannte High-Side, ansteuern. Die Ansteuerung des unteren IGBTs ist vergleichsweise einfach, da dessen Emitter meist auf dem Bezugspotential des Zwischenkreises liegt. Die Ansteuerung des oberen IGBTs ist dagegen anspruchsvoller, weil dessen Emitter mit dem Schaltknoten der Halbbrücke verbunden ist und sich dessen Potential während des Betriebs stark verändert.

Hier kommt der Bootstrap-Kondensator ins Spiel. Er stellt eine mitwandernde Hilfsspannung bereit, mit der der obere IGBT zuverlässig eingeschaltet werden kann.


## 2. Grundprinzip des Inverters

Die Waschmaschine erhält aus dem Stromnetz eine einphasige Wechselspannung von 230 V AC bei 50 Hz. Diese Netzspannung wird zunächst gleichgerichtet. Nach der Gleichrichtung und Glättung durch einen Zwischenkreiskondensator entsteht eine Gleichspannung von ungefähr 325 V DC.

Die Höhe dieser Gleichspannung ergibt sich näherungsweise aus dem Scheitelwert der Netzspannung:

$$
U_\text{DC} \approx 230\,\text{V} \cdot \sqrt{2} \approx 325\,\text{V}
$$

Aus dieser Zwischenkreisspannung erzeugt der Inverter drei pulsweitenmodulierte Ausgangsspannungen. Diese werden an die drei Motoranschlüsse U, V und W geführt. Durch geeignete zeitliche Ansteuerung entsteht im Motor ein rotierendes Magnetfeld. Dieses Drehfeld ist die Voraussetzung dafür, dass der Drehstrom-Asynchronmotor ein Drehmoment entwickeln kann.

Der Mikrocontroller der Waschmaschine erzeugt dazu mehrere PWM-Signale. Diese Signale steuern über Gate-Treiber die IGBTs der drei Halbbrücken. Die Frequenz und das Tastverhältnis der PWM bestimmen, welche effektive Spannung und Frequenz am Motor anliegen.

## 3. Aufgabe des Gate-Treibers

Ein IGBT wird nicht direkt durch eine Motorspannung gesteuert, sondern über seine Gate-Emitter-Spannung. Damit ein IGBT zuverlässig einschaltet, benötigt er üblicherweise eine Gate-Emitter-Spannung im Bereich von etwa 10 V bis 15 V. Zum sicheren Ausschalten wird das Gate wieder auf das Emitterpotential entladen.

Für den unteren IGBT ist das einfach. Sein Emitter liegt auf dem negativen Zwischenkreispotential, also auf DC-. Wenn die Treiberversorgung 15 V beträgt, kann der Treiber das Gate des unteren IGBTs auf ungefähr 15 V gegenüber DC- anheben. Dadurch ergibt sich eine Gate-Emitter-Spannung von etwa 15 V.

Beim oberen IGBT ist die Situation anders. Sein Emitter ist nicht fest mit DC- verbunden, sondern liegt am Schaltknoten der Halbbrücke. Dieser Schaltknoten ist gleichzeitig die jeweilige Motorphase. Je nach Schaltzustand liegt dieser Punkt nahe DC- oder nahe der positiven Zwischenkreisspannung von etwa 325 V.

Damit der obere IGBT eingeschaltet werden kann, muss sein Gate etwa 10 V bis 15 V über seinem Emitter liegen. Wenn der Schaltknoten also auf 325 V liegt, muss das Gate des oberen IGBTs ungefähr auf 335 V bis 340 V angehoben werden. Eine normale 15-V-Treiberversorgung gegen DC- reicht dafür nicht aus.

Der Gate-Treiber benötigt deshalb für die High-Side eine eigene, schwebende Versorgung. Diese Versorgung wird beim IR2101 typischerweise mit einer Bootstrap-Schaltung erzeugt.

## 4. Der Bootstrap-Kondensator als schwebende Hilfsspannung

Der Bootstrap-Kondensator ist zwischen den Anschlüssen VB und VS des High-Side-Treibers angeschlossen. VS ist der Bezugspunkt der High-Side und liegt am Schaltknoten der Halbbrücke. VB ist die positive Versorgung der High-Side-Treiberstufe.

Der Bootstrap-Kondensator wird geladen, wenn der Schaltknoten VS auf einem niedrigen Potential liegt, also nahe DC-. In diesem Zustand kann Strom aus der 15-V-Treiberversorgung über eine Bootstrap-Diode in den Kondensator fließen. Der Kondensator lädt sich dabei ungefähr auf die Treiberspannung abzüglich der Durchlassspannung der Diode auf.

Bei einer Treiberspannung von 15 V und einer Diodenflussspannung von etwa 0,7 V ergibt sich ungefähr:

$$
U_\text{Boot} \approx 15\,\text{V} - 0{,}7\,\text{V} = 14{,}3\,\text{V}
$$

Diese Spannung liegt nicht gegen Erde oder Schutzleiter an, sondern zwischen VB und VS. Der Kondensator ist also eine kleine lokale Energiequelle für die High-Side-Treiberstufe.

Wenn nun der obere IGBT eingeschaltet wird, steigt der Schaltknoten VS auf die positive Zwischenkreisspannung. Der Bootstrap-Kondensator bleibt aber zwischen VB und VS geladen. Dadurch wird auch VB um denselben Betrag mit nach oben gezogen. Liegt VS beispielsweise bei 325 V und der Kondensator ist auf 14 V geladen, dann liegt VB bei ungefähr 339 V.

Der High-Side-Treiber kann nun das Gate des oberen IGBTs auf ein Potential nahe VB ziehen. Dadurch erhält der obere IGBT eine Gate-Emitter-Spannung von etwa 14 V, obwohl sein Emitter bereits auf einem sehr hohen Potential liegt.

Für den IGBT zählt dabei nicht die absolute Spannung gegen Erde, sondern die Differenz zwischen Gate und Emitter:

$$
U_\text{GE} = U_\text{Gate} - U_\text{Emitter}
$$

Wenn das Gate bei 339 V und der Emitter bei 325 V liegt, ergibt sich:

$$
U_\text{GE} = 339\,\text{V} - 325\,\text{V} = 14\,\text{V}
$$

Damit ist der obere IGBT leitend.

## 5. Lade- und Entladevorgang

Der Bootstrap-Kondensator arbeitet zyklisch. Er wird geladen, wenn der Schaltknoten niedrig ist, und er wird entladen, während der obere IGBT eingeschaltet ist.

Während der Ladephase ist entweder der untere IGBT eingeschaltet oder der Motorstrom zieht den Schaltknoten über Freilaufpfade in die Nähe des negativen Zwischenkreises. In diesem Moment kann die Bootstrap-Diode leiten und der Kondensator wird aus der Treiberversorgung nachgeladen.

Während der High-Side-Einschaltphase versorgt der Bootstrap-Kondensator die High-Side-Treiberstufe. Er liefert die Ladung für das Gate des oberen IGBTs und zusätzlich den Betriebsstrom für den internen High-Side-Treiber. Außerdem treten kleine Verluste durch Leckströme auf.

Die wichtigsten Entladeursachen sind:

- die Gate-Ladung des oberen IGBTs,
- der Ruhestrom des High-Side-Treibers,
- Leckströme im Treiber, im Kondensator, in der Diode und im IGBT,
- ein eventuell vorhandener Gate-Emitter-Widerstand,
- Umladevorgänge bei jedem Schaltvorgang.

Da sich der Bootstrap-Kondensator während der High-Side-Zeit entlädt, kann der obere IGBT nicht beliebig lange eingeschaltet bleiben. Der Kondensator muss regelmäßig nachgeladen werden. Das ist eine wesentliche Eigenschaft von Bootstrap-Schaltungen.

## 6. Begrenzung der Einschaltdauer

Eine Bootstrap-Versorgung eignet sich sehr gut für PWM-Betrieb, weil bei der PWM-Ansteuerung regelmäßig Schaltzustände auftreten, in denen der Schaltknoten niedrig liegt. In diesen Zeitabschnitten kann der Bootstrap-Kondensator nachgeladen werden.

Problematisch wird es, wenn die High-Side sehr lange oder dauerhaft eingeschaltet bleiben soll. Dann sinkt die Spannung am Bootstrap-Kondensator allmählich ab. Sobald sie zu niedrig wird, kann der High-Side-Treiber den oberen IGBT nicht mehr sicher einschalten. Der IGBT würde dann nur teilweise leitend sein, stärker erwärmen und möglicherweise zerstört werden.

Viele Gate-Treiber besitzen deshalb eine Unterspannungsabschaltung. Diese Funktion wird als Undervoltage Lockout bezeichnet. Sinkt die Versorgungsspannung des Treibers unter einen bestimmten Mindestwert, wird der Ausgang abgeschaltet. Dadurch soll verhindert werden, dass der IGBT mit zu niedriger Gate-Spannung betrieben wird.

Bei einer Inverteransteuerung muss die Software daher sicherstellen, dass jede Bootstrap-Schaltung regelmäßig nachgeladen wird. Besonders bei sehr niedrigen Drehzahlen, sehr großen Tastverhältnissen oder speziellen Brems- und Haltezuständen muss dies berücksichtigt werden.

## 7. Bedeutung der Totzeit

Bei einer Halbbrücke dürfen der obere und der untere IGBT niemals gleichzeitig eingeschaltet sein. Wären beide gleichzeitig leitend, entstünde ein direkter Kurzschluss zwischen dem positiven und dem negativen Zwischenkreispotential. Dieser Zustand wird als Shoot-through bezeichnet und kann die IGBTs innerhalb kürzester Zeit zerstören.

Zwischen dem Ausschalten eines IGBTs und dem Einschalten des gegenüberliegenden IGBTs wird deshalb eine kurze Verzögerung eingefügt. Diese Verzögerung nennt man Totzeit oder Deadtime.

Der IR2101 stellt zwar die Treiberstufen für High-Side und Low-Side bereit, die korrekte zeitliche Ansteuerung muss jedoch von der Steuerelektronik kommen. Der Mikrocontroller muss also komplementäre PWM-Signale mit ausreichender Totzeit erzeugen. Die benötigte Totzeit hängt unter anderem von den verwendeten IGBTs, den Gate-Widerständen, den Schaltgeschwindigkeiten und der Treiberschaltung ab.

Eine zu kurze Totzeit erhöht das Risiko eines Zwischenkreiskurzschlusses. Eine zu lange Totzeit verschlechtert dagegen die Qualität der Ausgangsspannung und kann zu höheren Verzerrungen im Motorstrom führen. Die Totzeit ist daher ein wichtiger Parameter bei der Auslegung eines Inverters.

## 8. Dimensionierung des Bootstrap-Kondensators

Die Dimensionierung des Bootstrap-Kondensators hängt von mehreren Faktoren ab. Entscheidend ist, dass die Spannung am Kondensator während der längsten High-Side-Einschaltzeit nicht zu weit absinkt.

Eine vereinfachte Beziehung lautet:

$$
C_\text{Boot} \ge \frac{Q_\text{gesamt}}{\Delta U_\text{Boot}}
$$

Dabei ist $$C_\text{Boot}$$ die benötigte Kapazität, $$Q_\text{gesamt}$$ die insgesamt entnommene Ladung und $$\Delta U_\text{Boot}$$ der maximal erlaubte Spannungsabfall am Bootstrap-Kondensator.

Die Gesamtladung setzt sich aus mehreren Anteilen zusammen:

$$
Q_\text{gesamt} \approx Q_\text{Gate} + I_\text{HB} \cdot t_\text{on} + Q_\text{Leckage}
$$

$$Q_\text{Gate}$$ ist die Gate-Ladung des IGBTs. $$I_\text{HB}$$ ist der Betriebsstrom der High-Side-Treiberstufe. $$t_\text{on}$$ ist die maximale Einschaltzeit der High-Side. $$Q_\text{Leckage}$$ beschreibt die Ladungsverluste durch Leckströme und andere Nebeneffekte.

In der Praxis wird der Bootstrap-Kondensator deutlich größer gewählt, als es die reine Gate-Ladung erfordern würde. Häufig verwendet man einen Sicherheitsfaktor im Bereich von 10 bis 20. Typische Werte liegen je nach Leistungsteil, Schaltfrequenz und IGBT häufig im Bereich von 100 nF bis 1 µF.

Der Kondensator sollte eine geeignete Spannungsfestigkeit besitzen und für schnelle Impulsströme geeignet sein. In vielen Schaltungen werden Keramikkondensatoren oder Folienkondensatoren verwendet. Wichtig ist außerdem eine kurze, niederinduktive Verbindung zum Treiberbaustein.

## 9. Bootstrap-Diode

Die Bootstrap-Diode verbindet die 15-V-Treiberversorgung mit dem Bootstrap-Kondensator. Sie leitet nur während der Ladephase, wenn VS niedrig ist. Sobald der obere IGBT eingeschaltet wird und VS auf hohe Spannung steigt, sperrt die Diode. Dadurch verhindert sie, dass die hohe Bootstrap-Spannung in die 15-V-Versorgung zurückfließt.

Die Diode muss ausreichend schnell sperren und die auftretende Sperrspannung aushalten. Da VB im Betrieb auf ein Potential oberhalb der Zwischenkreisspannung steigen kann, muss die Diode entsprechend spannungsfest sein. Außerdem sollte sie geringe Schaltverluste und eine geeignete Strombelastbarkeit besitzen.

In vielen Anwendungen wird eine schnelle Diode oder eine Schottky-Diode verwendet, sofern deren Spannungsfestigkeit ausreicht. Die konkrete Auswahl hängt von der Zwischenkreisspannung, der Schaltfrequenz und dem Treiberstrom ab.

## 10. Anwendung im Waschmaschinen-Inverter

In einer Waschmaschine mit einem Drehstrom-Asynchronmotor besteht der Inverter typischerweise aus drei Halbbrücken. Jede Halbbrücke treibt eine Motorphase. Für jede Halbbrücke kann ein IR2101 oder ein vergleichbarer Halbbrückentreiber eingesetzt werden.

Die drei Motorphasen werden mit einer zeitlich versetzten PWM angesteuert. Bei einem Asynchronmotor wird häufig eine U/f-Kennlinie verwendet. Dabei wird die Motorspannung ungefähr proportional zur Frequenz erhöht. Bei niedriger Frequenz erhält der Motor eine niedrigere Spannung, bei höherer Frequenz eine höhere Spannung. Dadurch bleibt der magnetische Fluss im Motor näherungsweise konstant.

Die Grundidee lautet:

$$
\frac{U}{f} \approx \text{konstant}
$$

Bei einem 230-V-Inverter kann der Motor bei 50 Hz ungefähr mit 230 V Drehspannung betrieben werden, sofern der Motor dafür geeignet und entsprechend verschaltet ist. Bei einem klassischen 230/400-V-Drehstrommotor bedeutet das üblicherweise Betrieb in Dreieckschaltung.

Die Waschmaschinensteuerung kann über den Inverter die Drehzahl sehr fein regeln. Beim Waschen werden niedrige Frequenzen und niedrige Drehzahlen verwendet. Beim Schleudern werden deutlich höhere Drehzahlen benötigt. Der Inverter ermöglicht weichen Anlauf, kontrolliertes Bremsen, Drehrichtungswechsel und Anpassung an unterschiedliche Beladungen.

## 11. Grenzen und typische Fehlerquellen

Eine Bootstrap-Schaltung ist einfach, preiswert und zuverlässig, hat aber klare Grenzen. Die wichtigste Grenze ist, dass die High-Side-Versorgung regelmäßig nachgeladen werden muss. Ein dauerhafter High-Side-Einschaltzustand ist mit einer reinen Bootstrap-Versorgung nicht ohne Weiteres möglich.

Typische Fehlerquellen sind:

- zu kleiner Bootstrap-Kondensator,
- zu langsame oder ungeeignete Bootstrap-Diode,
- zu lange High-Side-Einschaltdauer ohne Nachladung,
- zu niedrige Treiberspannung,
- zu hohe Leckströme,
- schlechte Leiterplattenführung mit zu hohen Induktivitäten,
- fehlende oder zu kleine Totzeit,
- ungeeignete Gate-Widerstände,
- fehlender Schutz gegen Überstrom oder Überspannung.

Wenn die Bootstrap-Spannung zu stark absinkt, wird der obere IGBT nicht mehr vollständig eingeschaltet. Dadurch steigt seine Verlustleistung. Der IGBT erwärmt sich stärker und kann beschädigt werden. Wenn zusätzlich die Totzeit nicht korrekt eingehalten wird, kann es zu einem gefährlichen Kurzschluss im Zwischenkreis kommen.

## 12. Sicherheitsaspekte

In einer solchen Waschmaschinensteuerung treten lebensgefährliche Spannungen auf. Der Zwischenkreis liegt bei Betrieb an ungefähr 325 V DC. Diese Gleichspannung ist besonders gefährlich, weil Zwischenkreiskondensatoren auch nach dem Ausschalten noch geladen bleiben können.

Beim Messen an solchen Schaltungen ist besondere Vorsicht erforderlich. Ein normales Oszilloskop mit geerdetem Masseanschluss darf nicht beliebig an Punkte der Leistungselektronik angeschlossen werden. Der negative Zwischenkreis ist nicht automatisch identisch mit Schutzleiter oder Erde. Falsches Messen kann zu Kurzschlüssen, zerstörten Messgeräten oder lebensgefährlichen Berührspannungen führen.

Für Messungen an High-Side-Schaltungen sind geeignete isolierte Messgeräte oder Differenztastköpfe erforderlich. Vor Arbeiten an der Platine müssen die Zwischenkreiskondensatoren sicher entladen und die Spannungsfreiheit überprüft werden.

Arbeiten an netzbetriebener Leistungselektronik sollten nur von Personen durchgeführt werden, die mit den Gefahren und Schutzmaßnahmen vertraut sind.

## 13. Zusammenfassung

Der Bootstrap-Kondensator ist ein zentrales Bauteil in der High-Side-Ansteuerung eines Halbbrücken-Inverters. Er stellt eine schwebende Hilfsspannung bereit, mit der der obere IGBT eingeschaltet werden kann.

Der Kondensator wird geladen, wenn der Schaltknoten der Halbbrücke niedrig liegt. Wird anschließend der obere IGBT eingeschaltet

