> 🌐 &nbsp; [🇬🇧 EN](Manual-EN.md) &nbsp;|&nbsp; [🇩🇪 DE](Manual-DE.md) &nbsp;|&nbsp; 🇫🇷 FR &nbsp;|&nbsp; [🇳🇱 NL](Manual-NL.md) &nbsp;|&nbsp; [🇪🇸 ES](Manual-ES.md) &nbsp;|&nbsp; [🇮🇹 IT](Manual-IT.md) &nbsp;|&nbsp; [🇵🇱 PL](Manual-PL.md) &nbsp;|&nbsp; [🇨🇿 CS](Manual-CS.md) &nbsp;|&nbsp; [🇩🇰 DA](Manual-DA.md) &nbsp;|&nbsp; [🇳🇴 NO](Manual-NO.md) &nbsp;|&nbsp; [🇸🇪 SV](Manual-SV.md) &nbsp;|&nbsp; [🇭🇺 HU](Manual-HU.md) &nbsp;|&nbsp; [🇵🇹 PT](Manual-PT.md)

# Manuel des modules relais OS

![](all.png)

## Introduction

Ce document décrit les modules relais OS utilisés dans les projets Open Source Model
Railway Electronics : - **OS-General-Purpose-Relay** (module relais double)
- **OS-Latching-Relay** (module relais bistable simple)

Les deux types de relais existent en versions **THT** et **SMD** et peuvent être
branchés directement dans les décodeurs OS ou utilisés de manière autonome.

------------------------------------------------------------------------

## 1. OS-General-Purpose-Relay

Le module OS-General-Purpose-Relay contient **deux relais monostables**,
chacun avec : - **1× Commun (COM)** - **1× Normalement Ouvert (NO)** - **1×
Normalement Fermé (NC)**

![](image-1.png)
*Contacts des relais à usage général*

![](General-Purpose-THT.png)
*OS-General-Purpose-Relay — version THT*

![](General-Purpose-SMD.png)
*OS-General-Purpose-Relay — version SMD*

### Caractéristiques

-   Compatible avec **OS-Solenoid-Decoder** et **OS-Servo-Decoder**
-   Adapté pour :
    -   Commutation d'accessoires (éclairages, signaux, animations)
    -   Polarisation du cœur d'aiguille **Electrofrog**
    -   Polarisation du cœur d'aiguille **Unifrog**
    -   **Voies de garage à alimentation routée**

### Exemples d'utilisation

-   Commutation de l'alimentation vers des sections de voie isolées
-   Création d'une commutation automatique de polarité de cœur
-   Commande d'électronique externe telle que LED, cloches ou moteurs
-   Configurations d'aiguilles à alimentation routée

------------------------------------------------------------------------

## 2. OS-Latching-Relay

Le OS-Latching-Relay est un **relais bistable (à accrochage) simple**.\
Il **reste dans sa dernière position sans alimentation continue**.

![](Latching-Relay-THT.png)
*OS-Latching-Relay — version THT*

![](Latching-Relay-SMD.png)
*OS-Latching-Relay — version SMD*

### Remarques importantes

-   Ne peut pas être utilisé pour les aiguilles **Electrofrog**\
    (electrofrog nécessite un changement de polarité continu, non bistable)
-   Fonctionne parfaitement avec les aiguilles **Unifrog**
-   La bobine du relais peut être connectée **en parallèle** avec la bobine
    solénoïde de l'aiguille, sans nécessiter de décodeurs supplémentaires

### Cas d'utilisation avec décodeurs DCC

-   **Polarisation du cœur Unifrog**
-   Aiguilles autonomes / alimentation routée
-   Commutation d'accessoires
-   Fonctionnement autonome avec n'importe quel décodeur solénoïde

------------------------------------------------------------------------

## 3. Utilisation des relais avec les décodeurs OS

### Avec OS-Solenoid-Decoder

-   Prend en charge :
    -   OS-General-Purpose-Relay\
    -   OS-Latching-Relay (pour Unifrog uniquement)



### Avec OS-Servo-Decoder

-   Prend en charge uniquement :
    -   **OS-General-Purpose-Relay**
-   Utilisations typiques :
    -   Commutation de polarité du cœur
    -   Commutation d'accessoires



------------------------------------------------------------------------

## 4. Utilisation autonome

Les deux modules relais peuvent être utilisés sans décodeurs OS.

### Prérequis

-   Un signal de commande logique 5V
-   Alimentation adaptée au type de relais
-   Tout microcontrôleur, Arduino ou décodeur tiers capable de
    piloter un petit relais

### Applications autonomes typiques

-   Commutation de LED ou de signaux
-   Alimentation routée dans les voies de garage
-   Commande de polarité du cœur dans les modules d'aiguilles
-   Tâches d'automatisation à faible courant

------------------------------------------------------------------------

## Tableau récapitulatif

| Type de relais | Unifrog | Electrofrog | Commutation accessoires | Voies de garage autonomes | Compatible avec |
|---------------------------|---------|-------------|----------------------|------------------------|--------------------------|
| **OS-General-Purpose-Relay** | ✔ | ✔ | ✔ | ✔ | Décodeurs servo + solénoïde |
| **OS-Latching-Relay** | ✔ | ✖ | ✔ | ✔ | Décodeurs solénoïde uniquement |


------------------------------------------------------------------------

## Exemples de câblage

![](unifrog_bistable.png)
*Décodeur OS-Solenoid avec 8 OS-latching-relays branchés*

![](GP_relay_as_elekro_frog_solenoid.png)
*Relais OS-General-Purpose câblé sur OS-Solenoid-Decoder pour aiguilles electrofrog*

![](GP_relay_as_unifrog_servo.png)
*Relais OS-General-Purpose connecté à OS-Servo-Decoder pour aiguilles unifrog*

![](GP_relay_as_elekro_frog_servo.png)
*Relais OS-General-Purpose connecté à OS-Servo-Decoder pour aiguilles electrofrog*

## 5. Instructions supplémentaires pour la commande de PCB

Tous les OS-Relays ont été conçus pour pouvoir être commandés sous forme de panneaux. Commandés en panneaux, ils ont les mêmes distances que les prises des décodeurs OS. Les PCB peuvent également être commandés comme unités séparées, mais en panneaux les PCB sont moins chers à l'unité.

Pour les commander en panneau, vous devez cliquer sur **Panel by JLCPCB** derrière **Delivery format**. Cela ouvrira une nouvelle fenêtre dans laquelle vous devrez définir le nombre de colonnes et de rangées. Il y a 2 règles :

- JLCPCB exige que les panneaux fassent plus de 70x70 mm, les relais mesurent environ 50 mm de long et 15 mm de large.
- S'ils doivent être utilisés en combinaison avec les décodeurs solénoïde ou servo OS, il est préférable d'avoir des groupes de 4 unités, bien que ce ne soit pas obligatoire.

Pour satisfaire la première exigence, vous avez besoin d'au moins des panneaux de 2 rangées et 5 colonnes. Pour satisfaire la seconde, je recommande d'augmenter à 8 colonnes, ce qui vous donne essentiellement 4 jeux.

Le choix entre panneaux ou PCB séparés dépend également de la quantité souhaitée. La quantité de commande minimale est de 5 unités. Cela peut donc être 5 relais ou 5 panneaux de 10 à 16 modules relais chacun. Vous pouvez toujours vérifier le prix avec les frais d'expédition à la dernière étape, avant de payer. Vous pouvez donc arrêter votre commande à tout moment.

![](ORDERING_PANEL1.png)
*Disposition du panneau — rails de bord à gauche et à droite*

![](ORDERING_PANEL2.png)
*Paramètres de configuration du panneau dans JLCPCB*

### Version SMD — composant supplémentaire requis

La version SMD utilise un **connecteur à vis vertical** qui n'est pas placé par le service d'assemblage SMT. Ce connecteur doit être commandé séparément et soudé à la main.

- **Référence :** XY2500F-F-3.5-3P
- **Numéro de pièce LCSC :** C560231

![](screwTerminalPlug.png)
*Connecteur à vis vertical — XY2500F-F-3.5-3P (C560231)*

Lors de la passation d'une commande d'assemblage SMT sur JLCPCB, ajoutez la note suivante dans le champ **Special PCB Remarks** :

> Le composant C560231 doit être inséré dans le connecteur vertical.

JLCPCB vous contactera après la commande et facturera un petit supplément pour ce placement manuel.

---

Pour plus d'instructions sur la commande de PCB, consultez [ici](https://github.com/Open-Source-Model-Railway-Electronics/docs/blob/master/Ordering_bare_PCB/Ordering_bare_PCB-EN.md) pour les cartes nues et [ici](https://github.com/Open-Source-Model-Railway-Electronics/docs/blob/master/Ordering_SMT_ASSEMBLED_PCB/Ordering_Assembled_PCBs_JLCPCB-EN.md) pour les cartes assemblées SMT.
