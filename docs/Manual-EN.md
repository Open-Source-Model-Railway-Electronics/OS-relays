> 🌐 &nbsp; 🇬🇧 EN &nbsp;|&nbsp; [🇩🇪 DE](Manual-DE.md) &nbsp;|&nbsp; [🇫🇷 FR](Manual-FR.md) &nbsp;|&nbsp; [🇳🇱 NL](Manual-NL.md) &nbsp;|&nbsp; [🇪🇸 ES](Manual-ES.md) &nbsp;|&nbsp; [🇮🇹 IT](Manual-IT.md) &nbsp;|&nbsp; [🇵🇱 PL](Manual-PL.md) &nbsp;|&nbsp; [🇨🇿 CS](Manual-CS.md) &nbsp;|&nbsp; [🇩🇰 DA](Manual-DA.md) &nbsp;|&nbsp; [🇳🇴 NO](Manual-NO.md) &nbsp;|&nbsp; [🇸🇪 SV](Manual-SV.md) &nbsp;|&nbsp; [🇭🇺 HU](Manual-HU.md) &nbsp;|&nbsp; [🇵🇹 PT](Manual-PT.md)

# OS Relay Modules Manual

![](all.png)

## Introduction

This document describes the OS relay modules used in Open Source Model Railway Electronics projects:

- **OS-General-Purpose-Relay** — dual monostable relay module
- **OS-Latching-Relay** — single bistable relay module

Both relay types are available in **THT** and **SMD** versions and can be plugged directly into OS decoders or used standalone.

> **THT vs SMD** — The THT version is designed for hand-soldering. The SMD version is intended to be ordered pre-assembled from JLCPCB. Functionally they are identical.

---

## 1. OS-General-Purpose-Relay

The OS-General-Purpose-Relay module contains **two monostable relays**, each with:

- **1× Common (COM)**
- **1× Normally Open (NO)**
- **1× Normally Closed (NC)**

![](image-1.png)
*Contacts of General Purpose Relays*

![](General-Purpose-THT.png)
*OS-General-Purpose-Relay — THT version*

![](General-Purpose-SMD.png)
*OS-General-Purpose-Relay — SMD version*

### Features

- Compatible with **OS-Solenoid-Decoder** and **OS-Servo-Decoder**
- Suitable for:
  - Accessory switching (lights, signals, animations)
  - **Electrofrog** turnout frog polarization
  - **Unifrog** turnout frog polarization
  - **Power-routing sidings**

### Example Use Cases

- Switching power to isolated track sections
- Creating automated frog polarity switching
- Controlling external electronics such as LEDs, bells, or motors
- Power-routing turnout configurations

---

## 2. OS-Latching-Relay

The OS-Latching-Relay is a **single bistable (latching) relay**.
It **remains in its last position without continuous power**.

![](Latching-Relay-THT.png)
*OS-Latching-Relay — THT version*

![](Latching-Relay-SMD.png)
*OS-Latching-Relay — SMD version*

### Important Notes

- **Not recommended for electrofrog** turnouts when wired directly in parallel with the solenoid coil.
  The reason is timing: wired in parallel, the relay switches at the same instant as the solenoid fires.
  Electrofrog polarization requires the frog to first disconnect, then reconnect with the correct polarity
  *after* the mechanical throw is complete. This sequence cannot be achieved with a simple parallel connection.
  The OS-Solenoid-Decoder's built-in electrofrog mode (using its dedicated buddy-pin outputs) handles
  this timing correctly and is the recommended approach for electrofrog.
- Works perfectly with **unifrog** turnouts.
- The relay coil can be connected **in parallel** with the turnout solenoid coil — no extra decoder output needed.

### Use Cases with DCC Decoders

- **Unifrog frog polarization**
- Self-routing turnouts / power-routing sidings
- Accessory switching
- Standalone operation with any solenoid decoder

---

## 3. Using the Relays with OS Decoders

### With OS-Solenoid-Decoder

Supports both:

- OS-General-Purpose-Relay
- OS-Latching-Relay (unifrog only)

### With OS-Servo-Decoder

Supports only:

- **OS-General-Purpose-Relay**

Typical uses:

- Frog polarity switching
- Accessory switching

---

## 4. Standalone Usage

Both relay modules can be used without OS decoders.

### Requirements

- A 5 V logic-level control signal (e.g. from an Arduino or microcontroller GPIO pin)
- A power supply matching the relay coil voltage (5 V or 12 V depending on the variant ordered)
- Any microcontroller or third-party decoder capable of driving a small relay coil

### Typical Standalone Applications

- Switching LEDs or signals
- Power routing in sidings
- Controlling frog polarity in turnout modules
- Low-current automation tasks

---

## Summary Table

> **Power-routing sidings / Self-routing turnouts** — a layout technique where the turnout frog relay also switches power to the siding track, so a locomotive parked in the siding only receives power when the turnout is set towards it.

| Relay Type | Unifrog | Electrofrog | Accessory Switching | Power-Routing Sidings | Works With |
|---|---|---|---|---|---|
| **OS-General-Purpose-Relay** | ✔ | ✔ | ✔ | ✔ | Servo decoder, Solenoid decoder, Standalone |
| **OS-Latching-Relay** | ✔ | ✖ | ✔ | ✔ | Solenoid decoder, Standalone |

---

## Wiring Examples

![](unifrog_bistable.png)
*OS-Solenoid-Decoder with 8 OS-Latching-Relays plugged in*

![](GP_relay_as_elekro_frog_solenoid.png)
*OS-General-Purpose-Relay wired to OS-Solenoid-Decoder for electrofrog turnouts*

![](GP_relay_as_unifrog_servo.png)
*OS-General-Purpose-Relay connected to OS-Servo-Decoder for unifrog turnouts*

![](GP_relay_as_elekro_frog_servo.png)
*OS-General-Purpose-Relay connected to OS-Servo-Decoder for electrofrog turnouts*

---

## 5. PCB Ordering Instructions

All OS-Relay PCBs are designed to be ordered as **panels**. In panel form the spacing between modules matches the connector pitch of OS decoder expansion headers exactly, making them cheaper per unit and ready to plug straight in.

### Ordering as a panel

In JLCPCB, select **Panel by JLCPCB** under **Delivery format**. A window opens where you set the number of columns and rows. Two rules apply:

- JLCPCB requires panels to be larger than 70 × 70 mm. Each relay module is approximately 50 mm × 15 mm.
- For use with OS-Solenoid-Decoder or OS-Servo-Decoder, order in multiples of 4 modules (though this is not mandatory).

To satisfy the minimum size requirement you need at least **2 rows × 5 columns**. To get a full set of 4 for one decoder, **8 columns** is recommended — this gives you two sets of 4 per panel order.

The panels are designed with **edge rails on the left and right side**, as shown below:

![](ORDERING_PANEL1.png)
*Panel layout — edge rails on left and right*

![](ORDERING_PANEL2.png)
*Panel configuration settings in JLCPCB*

### Loose units vs panels

The minimum order at JLCPCB is 5 units — this can be 5 individual relay PCBs or 5 panels of 10–16 modules each. Always check the final price including shipping before confirming, as you can adjust quantities freely before paying.

### SMD version — additional component required

The SMD version uses a **vertical screw terminal socket** that is not placed by the SMT assembly service. This connector must be ordered separately and soldered by hand.

- **Part:** XY2500F-F-3.5-3P
- **LCSC part number:** C560231

![](screwTerminalPlug.png)
*Vertical screw terminal plug — XY2500F-F-3.5-3P (C560231)*

When placing an SMT assembly order on JLCPCB, add the following note in the **Special PCB Remarks** field:

> Component C560231 must be inserted in the vertical socket.

JLCPCB will contact you after the order and charge a small additional fee for this manual placement.

---

For further instructions about ordering PCBs, see:
- [Ordering bare PCBs](https://github.com/Open-Source-Model-Railway-Electronics/docs/blob/master/Ordering_bare_PCB/Ordering_bare_PCB-EN.md)
- [Ordering SMT assembled PCBs](https://github.com/Open-Source-Model-Railway-Electronics/docs/blob/master/Ordering_SMT_ASSEMBLED_PCB/Ordering_Assembled_PCBs_JLCPCB-EN.md)
