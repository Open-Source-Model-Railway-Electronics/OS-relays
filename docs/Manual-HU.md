> 🌐 &nbsp; [🇬🇧 EN](Manual-EN.md) &nbsp;|&nbsp; [🇩🇪 DE](Manual-DE.md) &nbsp;|&nbsp; [🇫🇷 FR](Manual-FR.md) &nbsp;|&nbsp; [🇳🇱 NL](Manual-NL.md) &nbsp;|&nbsp; [🇪🇸 ES](Manual-ES.md) &nbsp;|&nbsp; [🇮🇹 IT](Manual-IT.md) &nbsp;|&nbsp; [🇵🇱 PL](Manual-PL.md) &nbsp;|&nbsp; [🇨🇿 CS](Manual-CS.md) &nbsp;|&nbsp; [🇩🇰 DA](Manual-DA.md) &nbsp;|&nbsp; [🇳🇴 NO](Manual-NO.md) &nbsp;|&nbsp; [🇸🇪 SV](Manual-SV.md) &nbsp;|&nbsp; 🇭🇺 HU &nbsp;|&nbsp; [🇵🇹 PT](Manual-PT.md)

# OS Relés Modulok Kézikönyve

![](all.png)

## Bevezetés

Ez a dokumentum az Open Source Model Railway Electronics projektekben használt OS relés modulokat írja le: - **OS-General-Purpose-Relay** (dupla relés modul) - **OS-Latching-Relay** (egyedi bisztabil relés modul)

Mindkét relétípus **THT** és **SMD** kivitelben kapható, és közvetlenül bedugható OS dekóderekbe, vagy önállóan is használható.

------------------------------------------------------------------------

## 1. OS-General-Purpose-Relay

Az OS-General-Purpose-Relay modul **két monostabil relét** tartalmaz, mindegyik: - **1× Közös (COM)** - **1× Normálisan nyitott (NO)** - **1× Normálisan zárt (NC)** érintkezővel

![](image-1.png)
*Az általános célú relék érintkezői*

![](General-Purpose-THT.png)
*OS-General-Purpose-Relay — THT kivitel*

![](General-Purpose-SMD.png)
*OS-General-Purpose-Relay — SMD kivitel*

### Jellemzők

-   Kompatibilis az **OS-Solenoid-Decoder**-rel és az **OS-Servo-Decoder**-rel
-   Alkalmas:
    -   Kiegészítők kapcsolásához (fények, jelzők, animációk)
    -   **Electrofrog** kitérők szárpolarizálásához
    -   **Unifrog** kitérők szárpolarizálásához
    -   **Kitérési vágányok tápellátásának irányításához**

### Példa Felhasználási Esetek

-   Tápellátás kapcsolása szigetelt pályaszakaszokhoz
-   Automatizált szárpolaritás-váltás megvalósítása
-   Külső elektronika vezérlése, például LED-ek, csengők vagy motorok
-   Tápellátás-irányítású kitérő konfigurációk

------------------------------------------------------------------------

## 2. OS-Latching-Relay

Az OS-Latching-Relay egy **egyedi bisztabil (reteszelő) relé**.\
**Folyamatos tápellátás nélkül is megtartja utolsó állását**.

![](Latching-Relay-THT.png)
*OS-Latching-Relay — THT kivitel*

![](Latching-Relay-SMD.png)
*OS-Latching-Relay — SMD kivitel*

### Fontos Megjegyzések

-   Nem használható **electrofrog** kitérőkhöz\
    (az electrofrog folyamatos, nem reteszelő polaritásváltást igényel)
-   Tökéletesen működik **unifrog** kitérőkkel
-   A relé tekercse beköthet **párhuzamosan** a kitérő szolonoidtekercsével, nem igényel extra dekódereket

### Felhasználási Esetek DCC Dekóderekkel

-   **Unifrog szárpolarizálás**
-   Öngondoskodó kitérők / tápellátás-irányítás
-   Kiegészítők kapcsolása
-   Önálló üzemeltetés bármely szolonoid dekóderrel

------------------------------------------------------------------------

## 3. A Relék Használata OS Dekóderekkel

### OS-Solenoid-Decoder-rel

-   Mindkettőt támogatja:
    -   OS-General-Purpose-Relay\
    -   OS-Latching-Relay (csak unifrog-hoz)



### OS-Servo-Decoder-rel

-   Csak ezt támogatja:
    -   **OS-General-Purpose-Relay**
-   Tipikus felhasználás:
    -   Szárpolaritás-váltás
    -   Kiegészítők kapcsolása



------------------------------------------------------------------------

## 4. Önálló Használat

Mindkét relés modul használható OS dekóderek nélkül.

### Követelmények

-   5 V-os logikai szintű vezérlőjel
-   A relétípusnak megfelelő tápellátás
-   Bármely mikrovezérlő, Arduino vagy harmadik feles dekóder, amely képes kis relét meghajtani

### Tipikus Önálló Alkalmazások

-   LED-ek vagy jelzők kapcsolása
-   Tápellátás irányítása vágányokon
-   Szárpolaritás vezérlése kitérő modulokban
-   Kis áramú automatizálási feladatok

------------------------------------------------------------------------

## Összefoglaló Táblázat

| Relétípus | Unifrog | Electrofrog | Kiegészítők kapcsolása | Öngondoskodó vágányok | Kompatibilis eszközök |
|---------------------------|---------|-------------|----------------------|------------------------|--------------------------|
| **OS-General-Purpose-Relay** | ✔ | ✔ | ✔ | ✔ | Szervó + Szolonoid dekóderek |
| **OS-Latching-Relay** | ✔ | ✖ | ✔ | ✔ | Csak szolonoid dekóderek |


------------------------------------------------------------------------

## Bekötési Példák

![](unifrog_bistable.png)
*OS-Solenoid dekóder 8 bedugott OS-latching-relay-jel*

![](GP_relay_as_elekro_frog_solenoid.png)
*OS-General-Purpose relé bekötve OS-Solenoid-Decoder-hez electrofrog kitérőkhöz*

![](GP_relay_as_unifrog_servo.png)
*OS-General-Purpose relé csatlakoztatva OS-Servo-Decoder-hez unifrog kitérőkhöz*

![](GP_relay_as_elekro_frog_servo.png)
*OS-General-Purpose relé csatlakoztatva OS-Servo-Decoder-hez electrofrog kitérőkhöz*

## 5. További PCB-rendelési Útmutató

Minden OS-relé úgy van tervezve, hogy ún. paneleken rendelhető. Panel rendelésekor az OS-dekóder foglalatokkal megegyező távolságok adódnak. A PCB-k lazán szétválasztva is rendelhetők, de panelen olcsóbb az egységár.

Panelként való rendeléshez a **Szállítási formátum** mögötti **Panel by JLCPCB** lehetőséget kell választani. Ez megnyit egy új ablakot, ahol be kell állítani az oszlopok és sorok számát. Két szabályt kell betartani:

- A JLCPCB megköveteli, hogy a panelek nagyobbak legyenek 70×70 mm-nél; a relék kb. 50 mm hosszúak és 15 mm szélesek.
- Ha OS Solenoid vagy szervódekóderekkel együtt kívánod használni őket, 4-es csoportokban érdemes rendelni, bár ez nem kötelező.

Az első feltétel teljesítéséhez legalább 2 soros és 5 oszlopos panel szükséges. A második feltétel teljesítéséhez 8 oszlopra javaslom bővíteni. Ez lényegében 4 készletet ad.

Az is befolyásolja a döntést, hogy panelt vagy különálló PCB-t rendelj-e, hogy mennyi szükséges belőlük. A minimális rendelési mennyiség 5 egység, ami lehet 5 relé, de akár 5 panel is, egyenként 10–16 relés modullal. A szállítással együtt számított végső árat mindig megnézheted a fizetés előtt, tehát bármikor le is állíthatod a rendelést.

![](image.png)

A PCB-rendelésre vonatkozó további útmutatásért kattints [ide](https://github.com/Open-Source-Model-Railway-Electronics/docs/blob/master/Ordering_bare_PCB/Ordering_bare_PCB-EN.md) a csupasz lapokhoz, és [ide](https://github.com/Open-Source-Model-Railway-Electronics/docs/blob/master/Ordering_SMT_ASSEMBLED_PCB/Ordering_Assembled_PCBs_JLCPCB-EN.md) az SMT összeszereléssel rendelendő lapokhoz.
