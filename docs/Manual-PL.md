> 🌐 &nbsp; [🇬🇧 EN](Manual-EN.md) &nbsp;|&nbsp; [🇩🇪 DE](Manual-DE.md) &nbsp;|&nbsp; [🇫🇷 FR](Manual-FR.md) &nbsp;|&nbsp; [🇳🇱 NL](Manual-NL.md) &nbsp;|&nbsp; [🇪🇸 ES](Manual-ES.md) &nbsp;|&nbsp; [🇮🇹 IT](Manual-IT.md) &nbsp;|&nbsp; 🇵🇱 PL &nbsp;|&nbsp; [🇨🇿 CS](Manual-CS.md) &nbsp;|&nbsp; [🇩🇰 DA](Manual-DA.md) &nbsp;|&nbsp; [🇳🇴 NO](Manual-NO.md) &nbsp;|&nbsp; [🇸🇪 SV](Manual-SV.md) &nbsp;|&nbsp; [🇭🇺 HU](Manual-HU.md) &nbsp;|&nbsp; [🇵🇹 PT](Manual-PT.md)

# Instrukcja modułów przekaźnikowych OS

![](all.png)

## Wprowadzenie

Niniejszy dokument opisuje moduły przekaźnikowe OS używane w projektach Open Source Model Railway Electronics: — **OS-General-Purpose-Relay** (podwójny moduł przekaźnikowy) — **OS-Latching-Relay** (pojedynczy moduł przekaźnika bistabilnego)

Oba typy przekaźników występują w wersjach **THT** i **SMD** i mogą być podłączane bezpośrednio do dekoderów OS lub używane jako samodzielne moduły.

------------------------------------------------------------------------

## 1. OS-General-Purpose-Relay

Moduł OS-General-Purpose-Relay zawiera **dwa przekaźniki monostabilne**, każdy z: — **1× wspólnym (COM)** — **1× normalnie otwartym (NO)** — **1× normalnie zamkniętym (NC)**

![](image-1.png)
*Styki przekaźników ogólnego przeznaczenia*

![](General-Purpose-THT.png)
*OS-General-Purpose-Relay — wersja THT*

![](General-Purpose-SMD.png)
*OS-General-Purpose-Relay — wersja SMD*

### Właściwości

-   Kompatybilny z **OS-Solenoid-Decoder** i **OS-Servo-Decoder**
-   Nadaje się do:
    -   Przełączania akcesoriów (oświetlenie, semafory, animacje)
    -   Polaryzacji sercówki zwrotnicy **Electrofrog**
    -   Polaryzacji sercówki zwrotnicy **Unifrog**
    -   **Zasilania sekcji torowych**

### Przykładowe zastosowania

-   Przełączanie zasilania do izolowanych odcinków torowych
-   Tworzenie automatycznego przełączania biegunowości sercówki
-   Sterowanie zewnętrzną elektroniką, taką jak LED, dzwonki lub silniki
-   Konfiguracje zwrotnic z prowadzeniem prądu

------------------------------------------------------------------------

## 2. OS-Latching-Relay

OS-Latching-Relay to **pojedynczy przekaźnik bistabilny (zatrzaskowy)**.\
**Pozostaje w ostatniej pozycji bez ciągłego zasilania**.

![](Latching-Relay-THT.png)
*OS-Latching-Relay — wersja THT*

![](Latching-Relay-SMD.png)
*OS-Latching-Relay — wersja SMD*

### Ważne uwagi

-   Nie może być używany ze zwrotnicami **electrofrog**\
    (electrofrog wymaga ciągłej, nielatczącej zmiany biegunowości)
-   Działa doskonale ze zwrotnicami **unifrog**
-   Cewka przekaźnika może być podłączona **równolegle** z cewką solenoidu zwrotnicy — nie wymaga dodatkowych dekoderów

### Zastosowania z dekoderami DCC

-   **Polaryzacja sercówki unifrog**
-   Samodzielnie działające zwrotnice / prowadzenie prądu
-   Przełączanie akcesoriów
-   Praca autonomiczna z dowolnym dekoderem solenoidowym

------------------------------------------------------------------------

## 3. Używanie przekaźników z dekoderami OS

### Z OS-Solenoid-Decoder

-   Obsługuje oba typy:
    -   OS-General-Purpose-Relay\
    -   OS-Latching-Relay (tylko dla unifrog)



### Z OS-Servo-Decoder

-   Obsługuje wyłącznie:
    -   **OS-General-Purpose-Relay**
-   Typowe zastosowania:
    -   Przełączanie biegunowości sercówki
    -   Przełączanie akcesoriów



------------------------------------------------------------------------

## 4. Użytkowanie autonomiczne

Oba moduły przekaźnikowe mogą być używane bez dekoderów OS.

### Wymagania

-   Sygnał sterujący 5V na poziomie logicznym
-   Zasilanie odpowiednie do danego typu przekaźnika
-   Dowolny mikrokontroler, Arduino lub dekoder innej firmy zdolny do sterowania małym przekaźnikiem

### Typowe autonomiczne zastosowania

-   Przełączanie LED lub semaforów
-   Prowadzenie prądu na bocznicach
-   Sterowanie biegunowością sercówki w modułach zwrotnicowych
-   Zadania automatyzacji przy małych prądach

------------------------------------------------------------------------

## Tabela podsumowująca

| Typ przekaźnika | Unifrog | Electrofrog | Przełączanie akcesoriów | Samodzielne bocznice | Współpraca z |
|---------------------------|---------|-------------|----------------------|------------------------|--------------------------|
| **OS-General-Purpose-Relay** | ✔ | ✔ | ✔ | ✔ | Dekodery serw i solenoidów |
| **OS-Latching-Relay** | ✔ | ✖ | ✔ | ✔ | Wyłącznie dekodery solenoidów |


------------------------------------------------------------------------

## Przykłady okablowania

![](unifrog_bistable.png)
*Dekoder OS-Solenoid z 8 podłączonymi OS-latching-relay*

![](GP_relay_as_elekro_frog_solenoid.png)
*Przekaźnik OS-General-Purpose podłączony do OS-Solenoid-Decoder do zwrotnic electrofrog*

![](GP_relay_as_unifrog_servo.png)
*Przekaźnik OS-General-Purpose podłączony do OS-Servo-Decoder do zwrotnic unifrog*

![](GP_relay_as_elekro_frog_servo.png)
*Przekaźnik OS-General-Purpose podłączony do OS-Servo-Decoder do zwrotnic electrofrog*

## 5. Dodatkowe instrukcje zamawiania PCB

Wszystkie OS-Relays zostały zaprojektowane tak, aby można je było zamawiać w tak zwanych panelach. Gdy są zamawiane w panelach, mają takie same odległości jak gniazda dekoderów OS. PCB można również zamawiać jako osobne, oddzielne jednostki, ale w panelach cena za jednostkę jest niższa.

Aby zamówić je jako panel, kliknij **Panel by JLCPCB** przy opcji **Delivery format**. Otworzy się nowe okno, w którym należy ustawić liczbę kolumn i wierszy. Obowiązują 2 zasady:

- JLCPCB wymaga, aby panele miały rozmiar większy niż 70×70 mm; przekaźniki mają około 50 mm długości i 15 mm szerokości.
- Jeśli mają być używane w połączeniu z dekoderami solenoidowymi lub serwomechanizmów OS, warto mieć grupy po 4 jednostki, choć nie jest to obowiązkowe.

Aby spełnić pierwsze wymaganie, potrzebujesz co najmniej paneli o 2 wierszach i 5 kolumnach. Aby spełnić drugie, zalecam zwiększenie do 8 kolumn. Daje to w efekcie 4 zestawy.

To, czy zamawiać panele, czy luźne PCB, zależy również od tego, ile chcesz zamówić. Minimalna ilość zamówienia to 5 jednostek. Może to być 5 przekaźników lub 5 paneli po 10–16 modułów przekaźnikowych każdy. Cenę wraz z wysyłką możesz sprawdzić na ostatnim etapie przed zapłatą, więc możesz zrezygnować z zamówienia w dowolnym momencie.

![](ORDERING_PANEL1.png)
*Układ panelu — szyny krawędziowe po lewej i prawej stronie*

![](ORDERING_PANEL2.png)
*Ustawienia konfiguracji panelu w JLCPCB*

### Wersja SMD — wymagany dodatkowy element

Wersja SMD wykorzystuje **pionowe gniazdo zaciskowe** (śrubowe), które nie jest montowane przez serwis SMT. Ten złącze należy zamówić osobno i przylutować ręcznie.

- **Część:** XY2500F-F-3.5-3P
- **Numer części LCSC:** C560231

![](screwTerminalPlug.png)
*Pionowa wtyczka zaciskowa — XY2500F-F-3.5-3P (C560231)*

Składając zamówienie na montaż SMT w JLCPCB, dodaj następującą uwagę w polu **Special PCB Remarks**:

> Element C560231 musi zostać włożony w pionowe gniazdo.

JLCPCB skontaktuje się z Tobą po złożeniu zamówienia i naliczy małą dodatkową opłatę za to ręczne umieszczenie.

---

Dalsze instrukcje dotyczące zamawiania PCB znajdziesz [tutaj](https://github.com/Open-Source-Model-Railway-Electronics/docs/blob/master/Ordering_bare_PCB/Ordering_bare_PCB-EN.md) dla nagich płytek i [tutaj](https://github.com/Open-Source-Model-Railway-Electronics/docs/blob/master/Ordering_SMT_ASSEMBLED_PCB/Ordering_Assembled_PCBs_JLCPCB-EN.md) dla płytek zmontowanych metodą SMT
