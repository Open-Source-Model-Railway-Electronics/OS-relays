> 🌐 &nbsp; [🇬🇧 EN](Manual-EN.md) &nbsp;|&nbsp; [🇩🇪 DE](Manual-DE.md) &nbsp;|&nbsp; [🇫🇷 FR](Manual-FR.md) &nbsp;|&nbsp; [🇳🇱 NL](Manual-NL.md) &nbsp;|&nbsp; [🇪🇸 ES](Manual-ES.md) &nbsp;|&nbsp; [🇮🇹 IT](Manual-IT.md) &nbsp;|&nbsp; [🇵🇱 PL](Manual-PL.md) &nbsp;|&nbsp; 🇨🇿 CS &nbsp;|&nbsp; [🇩🇰 DA](Manual-DA.md) &nbsp;|&nbsp; [🇳🇴 NO](Manual-NO.md) &nbsp;|&nbsp; [🇸🇪 SV](Manual-SV.md) &nbsp;|&nbsp; [🇭🇺 HU](Manual-HU.md) &nbsp;|&nbsp; [🇵🇹 PT](Manual-PT.md)

# Manuál relé modulů OS

![](all.png)

## Úvod

Tento dokument popisuje OS relé moduly používané v projektech Open Source Model
Railway Electronics: - **OS-General-Purpose-Relay** (dvojitý relé
modul) - **OS-Latching-Relay** (jednoduchý bistabilní relé modul)

Oba typy relé existují ve verzích **THT** a **SMD** a lze je
zapojit přímo do OS dekodérů nebo použít jako samostatné moduly.

------------------------------------------------------------------------

## 1. OS-General-Purpose-Relay

Modul OS-General-Purpose-Relay obsahuje **dvě monostabilní relé**,
každé s: - **1× Common (COM)** - **1× Normally Open (NO)** - **1×
Normally Closed (NC)**

![](image-1.png)
*Kontakty relé pro obecné použití*

![](General-Purpose-THT.png)
*OS-General-Purpose-Relay — verze THT*

![](General-Purpose-SMD.png)
*OS-General-Purpose-Relay — verze SMD*

### Vlastnosti

-   Kompatibilní s **OS-Solenoid-Decoder** a **OS-Servo-Decoder**
-   Vhodné pro:
    -   Přepínání příslušenství (světla, návěstidla, animace)
    -   Polarizaci srdcovky výhybky **Electrofrog**
    -   Polarizaci srdcovky výhybky **Unifrog**
    -   **Napájení odstavných kolejí**

### Příklady použití

-   Přepínání napájení na izolované kolejové úseky
-   Vytváření automatického přepínání polarity srdcovky
-   Ovládání externí elektroniky jako jsou LED, zvonky nebo motory
-   Konfigurace výhybek s vedením napájení

------------------------------------------------------------------------

## 2. OS-Latching-Relay

OS-Latching-Relay je **jednoduchý bistabilní (aretační) reléový** modul.\
**Zůstává v poslední poloze bez trvalého napájení**.

![](Latching-Relay-THT.png)
*OS-Latching-Relay — verze THT*

![](Latching-Relay-SMD.png)
*OS-Latching-Relay — verze SMD*

### Důležité poznámky

-   Nelze použít pro výhybky **electrofrog**\
    (electrofrog vyžaduje trvalou, nenaretační změnu polarity)
-   Perfektně funguje s výhybkami **unifrog**
-   Cívku relé lze připojit **paralelně** k solenoidové cívce výhybky, nevyžaduje extra dekodéry

### Případy použití s DCC dekodéry

-   **Polarizace srdcovky unifrog**
-   Samočinné výhybky / vedení napájení
-   Přepínání příslušenství
-   Samostatný provoz s libovolným solenoidovým dekodérem

------------------------------------------------------------------------

## 3. Použití relé s OS dekodéry

### S OS-Solenoid-Decoder

-   Podporuje oba typy:
    -   OS-General-Purpose-Relay\
    -   OS-Latching-Relay (pouze pro unifrog)



### S OS-Servo-Decoder

-   Podporuje pouze:
    -   **OS-General-Purpose-Relay**
-   Typické použití:
    -   Přepínání polarity srdcovky
    -   Přepínání příslušenství



------------------------------------------------------------------------

## 4. Samostatné použití

Oba relé moduly lze použít bez OS dekodérů.

### Požadavky

-   Řídicí signál na logické úrovni 5 V
-   Napájení odpovídající typu relé
-   Libovolný mikrokontrolér, Arduino nebo dekodér třetí strany schopný pohánět malé relé

### Typické samostatné aplikace

-   Přepínání LED nebo návěstidel
-   Vedení napájení v odstavných kolejích
-   Ovládání polarity srdcovky v modulech výhybek
-   Automatizační úkoly s nízkým příkonem

------------------------------------------------------------------------

## Souhrnná tabulka

| Typ relé                 | Unifrog | Electrofrog | Přepínání příslušenství | Samočinné odstavné koleje | Funguje s               |
|---------------------------|---------|-------------|----------------------|------------------------|--------------------------|
| **OS-General-Purpose-Relay** | ✔       | ✔           | ✔                    | ✔                      | Servo + solenoidové dekodéry |
| **OS-Latching-Relay**        | ✔       | ✖           | ✔                    | ✔                      | Pouze solenoidové dekodéry     |


------------------------------------------------------------------------

## Příklady zapojení

![](unifrog_bistable.png)
*OS-Solenoid dekodér s 8 zapojenými OS-latching-relays*

![](GP_relay_as_elekro_frog_solenoid.png)
*OS-General-Purpose relay zapojený k OS-Solenoid-Decoder pro výhybky electrofrog*

![](GP_relay_as_unifrog_servo.png)
*OS-General-Purpose relay připojený k OS-Servo-Decoder pro výhybky unifrog*

![](GP_relay_as_elekro_frog_servo.png)
*OS-General-Purpose relay připojený k OS-Servo-Decoder pro výhybky electrofrog*

## 5. Další pokyny pro objednání PCB

Všechny OS-Relays byly navrženy tak, aby je bylo možné objednat v tzv. panelech. Při objednání v panelech mají stejné rozteče jako zásuvky OS dekodérů. PCB lze objednat také jako volné oddělené kusy, ale v panelech jsou PCB levnější za kus.

Pro objednání jako panel klikněte na **Panel by JLCPCB** za položkou **Delivery format**. Otevře se nové okno, kde je třeba nastavit počet sloupců a řad. Platí 2 pravidla:

- JLCPCB požaduje, aby panely byly větší než 70×70 mm; relé jsou přibližně 50 mm dlouhé a 15 mm široké.
- Pokud mají být použity v kombinaci s OS Solenoid nebo servo dekodéry, je vhodné mít skupiny po 4 kusech, i když to není povinné.

Pro splnění prvního požadavku potřebujete panely alespoň 2 řady a 5 sloupců. Pro splnění druhého požadavku doporučuji zvýšit na 8 sloupců. To vám v podstatě dá 4 sady.

To, zda objednat panely nebo volné PCB, závisí také na tom, kolik kusů chcete. Minimální množství objednávky je 5 kusů. Může to být tedy 5 relé nebo 5 panelů po 10–16 relé modulech. Cenu se šippingem si vždy můžete zkontrolovat na poslední stránce před zaplacením. Objednávku tedy můžete kdykoli zrušit.

![](image.png)

Další pokyny k objednávání PCB najdete [zde](https://github.com/Open-Source-Model-Railway-Electronics/docs/blob/master/Ordering_bare_PCB/Ordering_bare_PCB-EN.md) pro holé desky a [zde](https://github.com/Open-Source-Model-Railway-Electronics/docs/blob/master/Ordering_SMT_ASSEMBLED_PCB/Ordering_Assembled_PCBs_JLCPCB-EN.md) pro SMT osazené desky.
