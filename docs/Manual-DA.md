> 🌐 &nbsp; [🇬🇧 EN](Manual-EN.md) &nbsp;|&nbsp; [🇩🇪 DE](Manual-DE.md) &nbsp;|&nbsp; [🇫🇷 FR](Manual-FR.md) &nbsp;|&nbsp; [🇳🇱 NL](Manual-NL.md) &nbsp;|&nbsp; [🇪🇸 ES](Manual-ES.md) &nbsp;|&nbsp; [🇮🇹 IT](Manual-IT.md) &nbsp;|&nbsp; [🇵🇱 PL](Manual-PL.md) &nbsp;|&nbsp; [🇨🇿 CS](Manual-CS.md) &nbsp;|&nbsp; 🇩🇰 DA &nbsp;|&nbsp; [🇳🇴 NO](Manual-NO.md) &nbsp;|&nbsp; [🇸🇪 SV](Manual-SV.md) &nbsp;|&nbsp; [🇭🇺 HU](Manual-HU.md) &nbsp;|&nbsp; [🇵🇹 PT](Manual-PT.md)

# OS Relay-moduler Manual

![](all.png)

## Introduktion

Dette dokument beskriver OS-relæmodulerne, der bruges i Open Source Model
Railway Electronics-projekter: - **OS-General-Purpose-Relay** (dobbelt relæ
modul) - **OS-Latching-Relay** (enkelt bistabilt relæmodul)

Begge relætyper findes i **THT**- og **SMD**-versioner og kan
tilsluttes direkte til OS-dekodere eller bruges selvstændigt.

------------------------------------------------------------------------

## 1. OS-General-Purpose-Relay

OS-General-Purpose-Relay-modulet indeholder **to monostabile relæer**,
hvert med: - **1× Common (COM)** - **1× Normally Open (NO)** - **1×
Normally Closed (NC)**

![](image-1.png)
*Kontakter på General Purpose-relæer*

![](General-Purpose-THT.png)
*OS-General-Purpose-Relay — THT-version*

![](General-Purpose-SMD.png)
*OS-General-Purpose-Relay — SMD-version*

### Egenskaber

-   Kompatibel med **OS-Solenoid-Decoder** og **OS-Servo-Decoder**
-   Velegnet til:
    -   Tilbehørsskift (lys, signaler, animationer)
    -   **Electrofrog** sporskifte-hjertestykke-polarisering
    -   **Unifrog** sporskifte-hjertestykke-polarisering
    -   **Strømstyrede sidespor**

### Eksempler på anvendelse

-   Skifte strøm til isolerede sporstrækninger
-   Oprette automatisk hjertestykke-polaritetsskift
-   Styre ekstern elektronik som LED'er, klokker eller motorer
-   Strømstyrede sporskiftekonfigurationer

------------------------------------------------------------------------

## 2. OS-Latching-Relay

OS-Latching-Relay er et **enkelt bistabilt (selvholdende) relæ**.\
Det **forbliver i sin seneste position uden konstant strøm**.

![](Latching-Relay-THT.png)
*OS-Latching-Relay — THT-version*

![](Latching-Relay-SMD.png)
*OS-Latching-Relay — SMD-version*

### Vigtige noter

-   Kan ikke bruges til **Electrofrog**-sporskifter\
    (Electrofrog kræver et kontinuerligt, ikke-selvholdende polaritetsskift)
-   Fungerer perfekt med **Unifrog**-sporskifter
-   Relæspolen kan forbindes **parallelt** med sporskiftets solenoidspole — det kræver ikke ekstra dekodere

### Anvendelsestilfælde med DCC-dekodere

-   **Unifrog hjertestykke-polarisering**
-   Selvstyrende sporskifter / strømstyring
-   Tilbehørsskift
-   Selvstændig drift med enhver solenoid-dekoder

------------------------------------------------------------------------

## 3. Brug af relæerne med OS-dekodere

### Med OS-Solenoid-Decoder

-   Understøtter begge:
    -   OS-General-Purpose-Relay\
    -   OS-Latching-Relay (kun til Unifrog)



### Med OS-Servo-Decoder

-   Understøtter kun:
    -   **OS-General-Purpose-Relay**
-   Typiske anvendelser:
    -   Hjertestykke-polaritetsskift
    -   Tilbehørsskift



------------------------------------------------------------------------

## 4. Selvstændig brug

Begge relæmoduler kan bruges uden OS-dekodere.

### Krav

-   Et 5 V logik-niveau styresignal
-   Strømforsyning passende til relætypen
-   Enhver microcontroller, Arduino eller tredjeparts-dekoder, der kan
    styre et lille relæ

### Typiske selvstændige anvendelser

-   Skifte LED'er eller signaler
-   Strømstyring i sidespor
-   Styre hjertestykke-polaritet i sporskiftemoduler
-   Lavstrøms automatiseringsopgaver

------------------------------------------------------------------------

## Oversigtstabel

| Relætype                 | Unifrog | Electrofrog | Tilbehørsskift | Selvstyrende sidespor | Virker med               |
|---------------------------|---------|-------------|----------------------|------------------------|--------------------------|
| **OS-General-Purpose-Relay** | ✔       | ✔           | ✔                    | ✔                      | Servo + solenoid-dekodere |
| **OS-Latching-Relay**        | ✔       | ✖           | ✔                    | ✔                      | Kun solenoid-dekodere     |


------------------------------------------------------------------------

## Kabeltrækningseksempler

![](unifrog_bistable.png)
*OS-Solenoid-dekoder med 8 OS-latching-relays tilsluttet*

![](GP_relay_as_elekro_frog_solenoid.png)
*OS-General-Purpose-relæ kabelforbundet til OS-Solenoid-Decoder til Electrofrog-sporskifter*

![](GP_relay_as_unifrog_servo.png)
*OS-General-Purpose-relæ forbundet til OS-Servo-Decoder til Unifrog-sporskifter*

![](GP_relay_as_elekro_frog_servo.png)
*OS-General-Purpose-relæ forbundet til OS-Servo-Decoder til Electrofrog-sporskifter*

## 5. Yderligere PCB-bestillingsvejledning

Alle OS-relæer er designet, så de kan bestilles som såkaldte paneler. Når de bestilles som paneler, har de de samme afstande som OS-dekoder-stikkene. PCB'erne kan også bestilles som løse, adskilte enheder, men som paneler er PCB'erne billigere per enhed.

For at bestille dem som et panel skal du klikke på **Panel by JLCPCB** bag **Delivery format**. Dette åbner et nyt vindue, hvor du skal angive antal kolonner og rækker. Der gælder 2 regler:

- JLCPCB kræver, at paneler skal være større end 70x70mm; relæerne er ca. 50mm lange og 15mm brede.
- Hvis de skal bruges i kombination med OS-solenoid- eller servo-dekodere, er det ønskeligt at have grupper af 4 enheder, selvom dette ikke er obligatorisk.

For at opfylde det første krav har du brug for mindst paneler på 2 rækker og 5 kolonner. For at opfylde det andet krav anbefaler jeg at øge til 8 kolonner. Dette giver dig i realiteten 4 sæt.

Hvorvidt du skal bestille paneler eller løse PCB'er afhænger også af, hvor mange du ønsker. Minimumsordreantallet er 5 enheder. Det kan altså være 5 relæer, eller det kan være 5 paneler af 10–16 relæmoduler hver. Du kan altid undersøge prisen med forsendelse i det sidste trin, inden du betaler. Så du kan afbryde din bestilling til enhver tid.

![](image.png)

For yderligere vejledning om bestilling af PCB'er, se [her](https://github.com/Open-Source-Model-Railway-Electronics/docs/blob/master/Ordering_bare_PCB/Ordering_bare_PCB-EN.md) for bare boards og [her](https://github.com/Open-Source-Model-Railway-Electronics/docs/blob/master/Ordering_SMT_ASSEMBLED_PCB/Ordering_Assembled_PCBs_JLCPCB-EN.md) for SMT-monterede boards
