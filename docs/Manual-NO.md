> 🌐 &nbsp; [🇬🇧 EN](Manual-EN.md) &nbsp;|&nbsp; [🇩🇪 DE](Manual-DE.md) &nbsp;|&nbsp; [🇫🇷 FR](Manual-FR.md) &nbsp;|&nbsp; [🇳🇱 NL](Manual-NL.md) &nbsp;|&nbsp; [🇪🇸 ES](Manual-ES.md) &nbsp;|&nbsp; [🇮🇹 IT](Manual-IT.md) &nbsp;|&nbsp; [🇵🇱 PL](Manual-PL.md) &nbsp;|&nbsp; [🇨🇿 CS](Manual-CS.md) &nbsp;|&nbsp; [🇩🇰 DA](Manual-DA.md) &nbsp;|&nbsp; 🇳🇴 NO &nbsp;|&nbsp; [🇸🇪 SV](Manual-SV.md) &nbsp;|&nbsp; [🇭🇺 HU](Manual-HU.md) &nbsp;|&nbsp; [🇵🇹 PT](Manual-PT.md)

# OS Relé-moduler Manual

![](all.png)

## Innledning

Dette dokumentet beskriver OS relé-modulene som brukes i Open Source Model
Railway Electronics-prosjekter: - **OS-General-Purpose-Relay** (dobbelt relé-modul) - **OS-Latching-Relay** (enkelt bistabilt relé-modul)

Begge relétypene finnes i **THT**- og **SMD**-versjoner og kan plugges direkte inn i OS-dekodere eller brukes frittstående.

------------------------------------------------------------------------

## 1. OS-General-Purpose-Relay

OS-General-Purpose-Relay-modulen inneholder **to monostabile reléer**,
hvert med: - **1× Common (COM)** - **1× Normally Open (NO)** - **1×
Normally Closed (NC)**

![](image-1.png)
*Kontakter for General Purpose-reléer*

![](General-Purpose-THT.png)
*OS-General-Purpose-Relay — THT-versjon*

![](General-Purpose-SMD.png)
*OS-General-Purpose-Relay — SMD-versjon*

### Egenskaper

-   Kompatibel med **OS-Solenoid-Decoder** og **OS-Servo-Decoder**
-   Egnet for:
    -   Tilbehørskobling (lys, signaler, animasjoner)
    -   **Electrofrog** sporskifte-frog-polarisering
    -   **Unifrog** sporskifte-frog-polarisering
    -   **Strømstyring av sidespor**

### Eksempler på brukstilfeller

-   Koble strøm til isolerte sporpartier
-   Opprette automatisk frog-polaritetskobling
-   Styre ekstern elektronikk som LED-er, bjeller eller motorer
-   Strømstyringskonfigurasjoner for sporskifter

------------------------------------------------------------------------

## 2. OS-Latching-Relay

OS-Latching-Relay er et **enkelt bistabilt (selvholdende) relé**.\
Det **forblir i sin siste posisjon uten kontinuerlig strøm**.

![](Latching-Relay-THT.png)
*OS-Latching-Relay — THT-versjon*

![](Latching-Relay-SMD.png)
*OS-Latching-Relay — SMD-versjon*

### Viktige merknader

-   Kan ikke brukes for **electrofrog**-sporskifter\
    (electrofrog krever en kontinuerlig, ikke-selvholdende polaritetsendring)
-   Fungerer perfekt med **unifrog**-sporskifter
-   Relésolen kan kobles **parallelt** med sporskiftesolenoidspolen, det krever ingen ekstra dekodere

### Brukstilfeller med DCC-dekodere

-   **Unifrog frog-polarisering**
-   Selvtenkende sporskifter / strømstyring
-   Tilbehørskobling
-   Frittstående drift med enhver solenoid-dekoder

------------------------------------------------------------------------

## 3. Bruk av reléene med OS-dekodere

### Med OS-Solenoid-Decoder

-   Støtter begge:
    -   OS-General-Purpose-Relay\
    -   OS-Latching-Relay (kun for unifrog)



### Med OS-Servo-Decoder

-   Støtter kun:
    -   **OS-General-Purpose-Relay**
-   Typiske bruksområder:
    -   Frog-polaritetskobling
    -   Tilbehørskobling



------------------------------------------------------------------------

## 4. Frittstående bruk

Begge relé-modulene kan brukes uten OS-dekodere.

### Krav

-   Et 5V logikknivå-styresignal
-   Strømforsyning egnet for relé-typen
-   Enhver mikrokontroller, Arduino eller tredjeparts dekoder som er i stand til å drive et lite relé

### Typiske frittstående bruksområder

-   Koble LED-er eller signaler
-   Strømstyring i sidespor
-   Styre frog-polaritet i sporskiftemodulær
-   Lavstrøms automatiseringsoppgaver

------------------------------------------------------------------------

## Sammendragstabell

| Relétype                   | Unifrog | Electrofrog | Tilbehørskobling | Selvtenkende sidespor | Fungerer med               |
|---------------------------|---------|-------------|----------------------|------------------------|--------------------------|
| **OS-General-Purpose-Relay** | ✔       | ✔           | ✔                    | ✔                      | Servo + Solenoid-dekodere |
| **OS-Latching-Relay**        | ✔       | ✖           | ✔                    | ✔                      | Kun solenoid-dekodere     |


------------------------------------------------------------------------

## Koblingseksempler

![](unifrog_bistable.png)
*OS-Solenoid-dekoder med 8 OS-latching-reléer plugget inn*

![](GP_relay_as_elekro_frog_solenoid.png)
*OS-General-Purpose relé koblet til OS-Solenoid-Decoder for electrofrog-sporskifter*

![](GP_relay_as_unifrog_servo.png)
*OS-General-Purpose relé koblet til OS-Servo-Decoder for unifrog-sporskifter*

![](GP_relay_as_elekro_frog_servo.png)
*OS-General-Purpose relé koblet til OS-Servo-Decoder for electrofrog-sporskifter*

## 5. Ytterligere PCB-bestillingsinstruksjoner

Alle OS-Relays er designet slik at de kan bestilles i såkalte paneler. Når de bestilles som paneler, har de samme avstand som OS-dekodersoklene. PCB-ene kan også bestilles som løse separate enheter, men som paneler er PCB-ene billigere per enhet.

For å bestille dem som et panel må du klikke på **Panel by JLCPCB** bak **Delivery format**. Dette åpner et nytt vindu der du må angi antall kolonner og rader. Det er 2 regler:

- JLCPCB krever at paneler må være større enn 70×70 mm; reléene er ca. 50 mm lange og 15 mm brede.
- Hvis de skal brukes i kombinasjon med OS Solenoid- eller servo-dekodere, bør du ha grupper på 4 enheter, selv om dette ikke er obligatorisk.

For å oppfylle det første kravet trenger du minst paneler med 2 rader og 5 kolonner. For å oppfylle det andre kravet anbefaler jeg å øke til 8 kolonner. Dette gir deg i praksis 4 sett.

Om du bør bestille paneler eller løse PCB-er avhenger også av hvor mange du ønsker. Minimumsbestillingsantallet er 5 enheter. Så dette kan være 5 reléer eller 5 paneler med 10–16 relé-moduler hver. Du kan alltid sjekke prisen med frakt i siste trinn, før du betaler. Så du kan avbryte bestillingen når som helst.

![](ORDERING_PANEL1.png)
*Panellayout — kantskinner til venstre og høyre*

![](ORDERING_PANEL2.png)
*Panelkonfigurasjoninnstillinger i JLCPCB*

### SMD-versjon — ekstra komponent påkrevd

SMD-versjonen bruker en **vertikal skrueklemme** som ikke plasseres av SMT-monteringstjenesten. Denne kontakten må bestilles separat og loddes for hånd.

- **Del:** XY2500F-F-3.5-3P
- **LCSC-delnummer:** C560231

![](screwTerminalPlug.png)
*Vertikal skrueklemmekontakt — XY2500F-F-3.5-3P (C560231)*

Når du legger inn en SMT-monteringsordre på JLCPCB, legg til følgende merknad i feltet **Special PCB Remarks**:

> Komponent C560231 må settes inn i den vertikale kontakten.

JLCPCB vil kontakte deg etter bestillingen og belaste et lite ekstra gebyr for denne manuelle plasseringen.

---

For ytterligere instruksjoner om bestilling av PCB-er, se [her](https://github.com/Open-Source-Model-Railway-Electronics/docs/blob/master/Ordering_bare_PCB/Ordering_bare_PCB-EN.md) for nakne kort og [her](https://github.com/Open-Source-Model-Railway-Electronics/docs/blob/master/Ordering_SMT_ASSEMBLED_PCB/Ordering_Assembled_PCBs_JLCPCB-EN.md) for SMT-monterte kort
