> 🌐 &nbsp; [🇬🇧 EN](Manual-EN.md) &nbsp;|&nbsp; 🇩🇪 DE &nbsp;|&nbsp; [🇫🇷 FR](Manual-FR.md) &nbsp;|&nbsp; [🇳🇱 NL](Manual-NL.md) &nbsp;|&nbsp; [🇪🇸 ES](Manual-ES.md) &nbsp;|&nbsp; [🇮🇹 IT](Manual-IT.md) &nbsp;|&nbsp; [🇵🇱 PL](Manual-PL.md) &nbsp;|&nbsp; [🇨🇿 CS](Manual-CS.md) &nbsp;|&nbsp; [🇩🇰 DA](Manual-DA.md) &nbsp;|&nbsp; [🇳🇴 NO](Manual-NO.md) &nbsp;|&nbsp; [🇸🇪 SV](Manual-SV.md) &nbsp;|&nbsp; [🇭🇺 HU](Manual-HU.md) &nbsp;|&nbsp; [🇵🇹 PT](Manual-PT.md)

# OS Relaismodule Handbuch

![](all.png)

## Einführung

Dieses Dokument beschreibt die OS-Relaismodule, die in Open-Source-Modellbahn-Elektronikprojekten verwendet werden: - **OS-General-Purpose-Relay** (duales Relaismodul) - **OS-Latching-Relay** (einzelnes bistabiles Relaismodul)

Beide Relaistypen sind in **THT**- und **SMD**-Versionen erhältlich und können direkt in OS-Decoder eingesteckt oder eigenständig verwendet werden.

------------------------------------------------------------------------

## 1. OS-General-Purpose-Relay

Das OS-General-Purpose-Relay-Modul enthält **zwei monostabile Relais**, jeweils mit: - **1× Gemeinsam (COM)** - **1× Normalerweise offen (NO)** - **1× Normalerweise geschlossen (NC)**

![](image-1.png)
*Kontakte der Universalrelais*

![](General-Purpose-THT.png)
*OS-General-Purpose-Relay — THT-Version*

![](General-Purpose-SMD.png)
*OS-General-Purpose-Relay — SMD-Version*

### Merkmale

-   Kompatibel mit **OS-Solenoid-Decoder** und **OS-Servo-Decoder**
-   Geeignet für:
    -   Zubehörschaltung (Beleuchtung, Signale, Animationen)
    -   **Electrofrog**-Weichen-Herzstück-Polarisierung
    -   **Unifrog**-Weichen-Herzstück-Polarisierung
    -   **Stromführende Abstellgleise**

### Beispielanwendungen

-   Schalten der Stromversorgung zu isolierten Gleisabschnitten
-   Erstellen automatischer Herzstück-Polaritätsschaltungen
-   Steuerung externer Elektronik wie LEDs, Glocken oder Motoren
-   Weichenkonfigurationen mit Stromführung

------------------------------------------------------------------------

## 2. OS-Latching-Relay

Das OS-Latching-Relay ist ein **einzelnes bistabiles (selbsthaltendes) Relais**.\
Es **verbleibt in seiner letzten Stellung ohne Dauerbestromung**.

![](Latching-Relay-THT.png)
*OS-Latching-Relay — THT-Version*

![](Latching-Relay-SMD.png)
*OS-Latching-Relay — SMD-Version*

### Wichtige Hinweise

-   Kann **nicht** für **Electrofrog**-Weichen verwendet werden\
    (Electrofrog erfordert eine kontinuierliche, nicht selbsthaltende Polaritätsänderung)
-   Funktioniert einwandfrei mit **Unifrog**-Weichen
-   Die Relaisspule kann **parallel** zur Weichenspule angeschlossen werden, es sind keine zusätzlichen Decoder erforderlich

### Anwendungsfälle mit DCC-Decodern

-   **Unifrog-Herzstück-Polarisierung**
-   Selbstschaltende Weichen / stromführende Abstellgleise
-   Zubehörschaltung
-   Eigenständiger Betrieb mit jedem Magnetartikeldecoder

------------------------------------------------------------------------

## 3. Verwendung der Relais mit OS-Decodern

### Mit OS-Solenoid-Decoder

-   Unterstützt beide:
    -   OS-General-Purpose-Relay\
    -   OS-Latching-Relay (nur für Unifrog)



### Mit OS-Servo-Decoder

-   Unterstützt nur:
    -   **OS-General-Purpose-Relay**
-   Typische Anwendungen:
    -   Herzstück-Polaritätsschaltung
    -   Zubehörschaltung



------------------------------------------------------------------------

## 4. Eigenständige Verwendung

Beide Relaismodule können ohne OS-Decoder verwendet werden.

### Anforderungen

-   Ein 5V-Logikpegel-Steuersignal
-   Geeignete Stromversorgung für den jeweiligen Relaistyp
-   Jeder Mikrocontroller, Arduino oder Drittanbieter-Decoder, der ein kleines Relais ansteuern kann

### Typische Standalone-Anwendungen

-   Schalten von LEDs oder Signalen
-   Stromführung in Abstellgleisen
-   Steuerung der Herzstück-Polarität in Weichenmodulen
-   Automatisierungsaufgaben mit geringem Strom

------------------------------------------------------------------------

## Übersichtstabelle

| Relaistyp | Unifrog | Electrofrog | Zubehörschaltung | Selbstschaltende Abstellgleise | Funktioniert mit |
|---------------------------|---------|-------------|----------------------|------------------------|--------------------------|
| **OS-General-Purpose-Relay** | ✔ | ✔ | ✔ | ✔ | Servo- + Magnetartikel-Decoder |
| **OS-Latching-Relay** | ✔ | ✖ | ✔ | ✔ | Nur Magnetartikel-Decoder |


------------------------------------------------------------------------

## Verdrahtungsbeispiele

![](unifrog_bistable.png)
*OS-Solenoid-Decoder mit 8 eingesteckten OS-Latching-Relais*

![](GP_relay_as_elekro_frog_solenoid.png)
*OS-General-Purpose-Relais an OS-Solenoid-Decoder für Electrofrog-Weichen verdrahtet*

![](GP_relay_as_unifrog_servo.png)
*OS-General-Purpose-Relais an OS-Servo-Decoder für Unifrog-Weichen angeschlossen*

![](GP_relay_as_elekro_frog_servo.png)
*OS-General-Purpose-Relais an OS-Servo-Decoder für Electrofrog-Weichen angeschlossen*

## 5. Zusätzliche Hinweise zur PCB-Bestellung

Alle OS-Relays wurden so konzipiert, dass sie als sogenannte Panels bestellt werden können. Bei Bestellung als Panels haben sie die gleichen Abstände wie die OS-Decoder-Sockel. Die PCBs können auch als einzelne getrennte Einheiten bestellt werden, aber als Panels sind die PCBs günstiger pro Stück.

Um sie als Panel zu bestellen, muss unter **Lieferformat** auf **Panel by JLCPCB** geklickt werden. Dadurch öffnet sich ein neues Fenster, in dem die Anzahl der Spalten und Zeilen eingestellt werden muss. Es gibt 2 Regeln:

- JLCPCB verlangt, dass Panels größer als 70x70mm sein müssen. Die Relais sind ca. 50mm lang und 15mm breit.
- Wenn sie in Kombination mit OS-Solenoid- oder Servo-Decodern verwendet werden sollen, empfehlen sich Gruppen von 4 Einheiten, obwohl dies nicht zwingend erforderlich ist.

Um die erste Anforderung zu erfüllen, werden mindestens Panels mit 2 Zeilen und 5 Spalten benötigt. Um die zweite Anforderung zu erfüllen, empfehle ich eine Erhöhung auf 8 Spalten. Dies ergibt im Wesentlichen 4 Sets.

Ob Panels oder einzelne PCBs bestellt werden sollten, hängt auch davon ab, wie viele benötigt werden. Die Mindestbestellmenge beträgt 5 Einheiten. Das können also 5 Relais oder 5 Panels mit je 10–16 Relaismodulen sein. Der Preis mit Versand kann jederzeit im letzten Schritt überprüft werden, bevor bezahlt wird. Die Bestellung kann also jederzeit abgebrochen werden.

![](ORDERING_PANEL1.png)
*Panellayout — Randrails links und rechts*

![](ORDERING_PANEL2.png)
*Panelkonfigurationseinstellungen in JLCPCB*

### SMD-Version — zusätzliches Bauteil erforderlich

Die SMD-Version verwendet eine **vertikale Schraubklemmen-Buchse**, die vom SMT-Bestückungsservice nicht bestückt wird. Dieser Steckverbinder muss separat bestellt und von Hand gelötet werden.

- **Teil:** XY2500F-F-3.5-3P
- **LCSC-Teilenummer:** C560231

![](screwTerminalPlug.png)
*Vertikaler Schraubklemmen-Stecker — XY2500F-F-3.5-3P (C560231)*

Fügen Sie beim Aufgeben einer SMT-Bestückungsbestellung bei JLCPCB den folgenden Hinweis im Feld **Special PCB Remarks** ein:

> Bauteil C560231 muss in die vertikale Buchse eingesetzt werden.

JLCPCB wird sich nach der Bestellung bei Ihnen melden und eine kleine zusätzliche Gebühr für diese manuelle Bestückung berechnen.

---

Weitere Anweisungen zur Bestellung von PCBs findest du [hier](https://github.com/Open-Source-Model-Railway-Electronics/docs/blob/master/Ordering_bare_PCB/Ordering_bare_PCB-EN.md) für blanke Platinen und [hier](https://github.com/Open-Source-Model-Railway-Electronics/docs/blob/master/Ordering_SMT_ASSEMBLED_PCB/Ordering_Assembled_PCBs_JLCPCB-EN.md) für SMT-bestückte Platinen.
