> 🌐 &nbsp; [🇬🇧 EN](Manual-EN.md) &nbsp;|&nbsp; [🇩🇪 DE](Manual-DE.md) &nbsp;|&nbsp; [🇫🇷 FR](Manual-FR.md) &nbsp;|&nbsp; 🇳🇱 NL &nbsp;|&nbsp; [🇪🇸 ES](Manual-ES.md) &nbsp;|&nbsp; [🇮🇹 IT](Manual-IT.md) &nbsp;|&nbsp; [🇵🇱 PL](Manual-PL.md) &nbsp;|&nbsp; [🇨🇿 CS](Manual-CS.md) &nbsp;|&nbsp; [🇩🇰 DA](Manual-DA.md) &nbsp;|&nbsp; [🇳🇴 NO](Manual-NO.md) &nbsp;|&nbsp; [🇸🇪 SV](Manual-SV.md) &nbsp;|&nbsp; [🇭🇺 HU](Manual-HU.md) &nbsp;|&nbsp; [🇵🇹 PT](Manual-PT.md)

# OS Relais­modules Handleiding

![](all.png)

## Inleiding

Dit document beschrijft de OS-relais­modules die worden gebruikt in Open Source Model
Railway Electronics-projecten: - **OS-General-Purpose-Relay** (dubbele relais­module) - **OS-Latching-Relay** (enkele bistabiele relais­module)

Beide relais­typen zijn beschikbaar in **THT** en **SMD** versies en kunnen rechtstreeks in OS-decoders worden gestoken of zelfstandig worden gebruikt.

------------------------------------------------------------------------

## 1. OS-General-Purpose-Relay

De OS-General-Purpose-Relay-module bevat **twee mono­stabiele relais**,
elk met: - **1× Common (COM)** - **1× Normally Open (NO)** - **1×
Normally Closed (NC)**

![](image-1.png)
*Contacten van de General Purpose relais*

![](General-Purpose-THT.png)
*OS-General-Purpose-Relay — THT versie*

![](General-Purpose-SMD.png)
*OS-General-Purpose-Relay — SMD versie*

### Kenmerken

-   Compatibel met **OS-Solenoid-Decoder** en **OS-Servo-Decoder**
-   Geschikt voor:
    -   Accessoire­schakeling (verlichting, seinen, animaties)
    -   Hartpunt­polarisering van **Electrofrog**-wissels
    -   Hartpunt­polarisering van **Unifrog**-wissels
    -   **Voedings­gestuurde emplacement­sporen**

### Gebruiksvoorbeelden

-   Voeding schakelen naar geïsoleerde baansecties
-   Automatische hartpunt­polarisering creëren
-   Externe elektronica aansturen zoals LED's, bellen of motoren
-   Voedings­gestuurde wisselconfiguraties

------------------------------------------------------------------------

## 2. OS-Latching-Relay

De OS-Latching-Relay is een **enkel bistabiel (zelfhoudend) relais**.\
Het **blijft in zijn laatste stand zonder continue voeding**.

![](Latching-Relay-THT.png)
*OS-Latching-Relay — THT versie*

![](Latching-Relay-SMD.png)
*OS-Latching-Relay — SMD versie*

### Belangrijke opmerkingen

-   Kan **niet** worden gebruikt voor **electrofrog**-wissels\
    (electrofrog vereist een continue, niet-zelfhoudende polariteits­wisseling)
-   Werkt uitstekend met **unifrog**-wissels
-   De relaisspoel kan **parallel** worden geschakeld aan de wisselspoel,
    er zijn geen extra decoders nodig

### Gebruiksmogelijkheden met DCC-decoders

-   **Unifrog-hartpunt­polarisering**
-   Zelf­denkende wissels / voedings­routing
-   Accessoire­schakeling
-   Zelfstandige werking met elke magneet­decoder

------------------------------------------------------------------------

## 3. Relais gebruiken met OS-decoders

### Met OS-Solenoid-Decoder

-   Ondersteunt zowel:
    -   OS-General-Purpose-Relay\
    -   OS-Latching-Relay (alleen voor unifrog)



### Met OS-Servo-Decoder

-   Ondersteunt alleen:
    -   **OS-General-Purpose-Relay**
-   Typische toepassingen:
    -   Hartpunt­polarisering
    -   Accessoire­schakeling



------------------------------------------------------------------------

## 4. Zelfstandig gebruik

Beide relais­modules kunnen worden gebruikt zonder OS-decoders.

### Vereisten

-   Een 5V logica­niveau stuur­signaal
-   Voeding passend bij het relaistype
-   Elke microcontroller, Arduino of decoder van derden die in staat is
    een klein relais aan te sturen

### Typische zelfstandige toepassingen

-   LED's of seinen schakelen
-   Voedings­routing in emplacement­sporen
-   Hartpunt­polarisering besturen in wisselmodules
-   Laag­stroom automatiserings­taken

------------------------------------------------------------------------

## Overzichts­tabel

| Relaistype | Unifrog | Electrofrog | Accessoire­schakeling | Zelf­denkende emplacement­sporen | Werkt met |
|------------|---------|-------------|----------------------|----------------------------------|-----------|
| **OS-General-Purpose-Relay** | ✔ | ✔ | ✔ | ✔ | Servo + Magneet­decoders |
| **OS-Latching-Relay** | ✔ | ✖ | ✔ | ✔ | Alleen magneet­decoders |


------------------------------------------------------------------------

## Bedradingsvoorbeelden

![](unifrog_bistable.png)
*OS-Solenoid-decoder met 8 OS-latching-relays aangesloten*

![](GP_relay_as_elekro_frog_solenoid.png)
*OS-General-Purpose relay aangesloten op OS-Solenoid-Decoder voor electrofrog-wissels*

![](GP_relay_as_unifrog_servo.png)
*OS-General-Purpose relay aangesloten op OS-Servo-Decoder voor unifrog-wissels*

![](GP_relay_as_elekro_frog_servo.png)
*OS-General-Purpose relay aangesloten op OS-Servo-Decoder voor electrofrog-wissels*

## 5. Aanvullende instructies voor PCB-bestelling

Alle OS-Relays zijn ontworpen zodat ze kunnen worden besteld als zogenaamde panelen. Wanneer ze als panelen worden besteld, hebben ze dezelfde afstanden als de OS-decoder­sockets. De PCB's kunnen ook als losse afzonderlijke eenheden worden besteld, maar als panelen zijn de PCB's goedkoper per eenheid.

Om ze als paneel te bestellen, moet u op **Panel by JLCPCB** klikken achter **Delivery format**. Dit opent een nieuw venster waar u het aantal kolommen en rijen moet instellen. Er zijn 2 regels:

- JLCPCB eist dat panelen groter zijn dan 70x70mm; de relais zijn circa 50mm lang en 15mm breed.  
- Als ze worden gebruikt in combinatie met OS-Solenoid- of servo­decoders, wilt u groepen van 4 eenheden hebben, hoewel dit niet verplicht is.

Om aan de eerste eis te voldoen, heeft u minimaal panelen van 2 rijen en 5 kolommen nodig. Om aan de tweede eis te voldoen, raad ik aan te verhogen naar 8 kolommen. Dit geeft u in wezen 4 sets.

Of u panelen of losse PCB's moet bestellen, hangt ook af van hoeveel u wilt. Het minimum bestelaantal is 5 eenheden. Dit kan 5 relais zijn, of 5 panelen van elk 10–16 relais­modules. U kunt de prijs inclusief verzending altijd bekijken in de laatste stap, vóór het betalen. U kunt uw bestelling op elk moment stopzetten.

![](image.png)

Voor verdere instructies over het bestellen van PCB's kijk [hier](https://github.com/Open-Source-Model-Railway-Electronics/docs/blob/master/Ordering_bare_PCB/Ordering_bare_PCB-EN.md) voor kale PCB's en [hier](https://github.com/Open-Source-Model-Railway-Electronics/docs/blob/master/Ordering_SMT_ASSEMBLED_PCB/Ordering_Assembled_PCBs_JLCPCB-EN.md) voor SMT-gemonteerde PCB's.
