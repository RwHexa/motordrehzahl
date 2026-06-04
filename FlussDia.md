# SmartHomeRw Anlagen-Aufbau & Flussdiagramm  ![Rw](logorw96.png)

Dieses Dokument beschreibt die Architektur und den Datenfluss einer selbst Entwickelten SmartHome.

![Alternativtext](flussbild.png)


---

## 1. Flussdiagramm (Mermaid)

```mermaid
graph TD
    %% Physikalische Komponenten im Haus
    subgraph Haus [Im Haus verbaut]
        Sensoren[Sensoren / Schalter / Motoren] -->|Eingangssignale| Shelly[SmartHome Shelly]
        Sensoren -->|Eingangssignale| ESP32[Controller ESP32]
        
        %% Parallele Anordnung erzwingen
        Shelly -. Parallel .- ESP32
    end

    %% Netzwerkinfrastruktur (Parallele Anbindung an den Router)
    Shelly -->|WLAN| Router[Router mit SIM-Karte]
    ESP32 -->|WLAN| Router

    %% Cloud und Protokolle
    Router -->|Internet via MQTT| Cloud[Cloud]
    Cloud <-->|Broker-Dienste| MQTT_Broker[MQTT-Broker]

    %% Endgeräte (Fernzugriff)
    MQTT_Broker -->|Datenverkehr / Visu| PC[PC / Visualisierung]
    MQTT_Broker -->|Meldungen / Alarme| Handy[Handy / Meldungen]

    %% Styling für bessere Übersicht in VS-Code
    style ESP32 fill:#dcdcdc,stroke:#333,stroke-width:2px
    style Shelly fill:#ffcccc,stroke:#ff0000,stroke-width:2px
    style Router fill:#fff,stroke:#000,stroke-width:2px
    style Cloud fill:#e6f2ff,stroke:#0066cc,stroke-width:2px
    style PC fill:#fff,stroke:#00a3e0,stroke-width:2px
    style Handy fill:#fff,stroke:#008000,stroke-width:2px
```

---

## 2. Beschreibung der Systemarchitektur

Die Anwendung realisiert einen zuverlässigen **Fernzugriff** und eine **Visualisierung** von Steuerungs- und Haustechnikkomponenten über das Internet mittels des IoT-Protokolls **MQTT**.

### Feld- und Steuerungsebene (Im Haus verbaut)
* **Sensoren, Schalter & Motoren:** Physikalische Peripheriegeräte zur Erfassung von Zuständen und Ausführung von Aktionen (z. B. Lichtschalter, Relais, Antriebe).
* **SmartHome Shelly & ESP32 Controller (Parallelbetrieb):** Beide Komponenten arbeiten parallel auf der Steuerungsebene. Sie erfassen Eingangssignale der Peripherie unabhängig voneinander oder ergänzen sich in ihren Schalt- und Messfunktionen.

### Netzwerkinfrastruktur & Internetanbindung
* **WLAN:** Sowohl der Shelly als auch der ESP32-Controller übertragen ihre Daten parallel und drahtlos zum lokalen Gateway.
* **Router (mit SIM-Karte):** Ein Mobilfunk-Router, der die Anlage über das Mobilfunknetz ungebunden von Festnetzanschlüssen mit dem Internet verbindet.

### Cloud- und Vermittlungsschicht
* **Internet / MQTT:** Das schlanke Message Queuing Telemetry Transport Protokoll sorgt für einen ressourcenschonenden Datenaustausch.
* **Cloud & MQTT-Broker:** Die zentrale Instanz im Web, die Nachrichten von der Anlage empfängt (Publish) und an die registrierten Endgeräte verteilt (Subscribe).

### Monitoring & Benutzerschnittstelle (Fernzugriff)
* **PC (Visu):** Stationäre oder detaillierte grafische Benutzeroberfläche zur Anlagenüberwachung und Konfiguration.
* **Handy (Meldungen):** Mobiler Empfang von Statusmeldungen, Störungsmeldungen oder Alarmen in Echtzeit.
