> 🌐 &nbsp; [🇬🇧 EN](Manual-EN.md) &nbsp;|&nbsp; [🇩🇪 DE](Manual-DE.md) &nbsp;|&nbsp; [🇫🇷 FR](Manual-FR.md) &nbsp;|&nbsp; [🇳🇱 NL](Manual-NL.md) &nbsp;|&nbsp; 🇪🇸 ES &nbsp;|&nbsp; [🇮🇹 IT](Manual-IT.md) &nbsp;|&nbsp; [🇵🇱 PL](Manual-PL.md) &nbsp;|&nbsp; [🇨🇿 CS](Manual-CS.md) &nbsp;|&nbsp; [🇩🇰 DA](Manual-DA.md) &nbsp;|&nbsp; [🇳🇴 NO](Manual-NO.md) &nbsp;|&nbsp; [🇸🇪 SV](Manual-SV.md) &nbsp;|&nbsp; [🇭🇺 HU](Manual-HU.md) &nbsp;|&nbsp; [🇵🇹 PT](Manual-PT.md)

# Manual de los Módulos de Relé OS

![](all.png)

## Introducción

Este documento describe los módulos de relé OS utilizados en los proyectos de Open Source Model
Railway Electronics: - **OS-General-Purpose-Relay** (módulo de doble relé) - **OS-Latching-Relay** (módulo de relé biestable simple)

Ambos tipos de relé existen en versiones **THT** y **SMD** y pueden
enchufarse directamente en los decodificadores OS o utilizarse de forma independiente.

------------------------------------------------------------------------

## 1. OS-General-Purpose-Relay

El módulo OS-General-Purpose-Relay contiene **dos relés monoestables**,
cada uno con: - **1× Común (COM)** - **1× Normalmente abierto (NO)** - **1×
Normalmente cerrado (NC)**

![](image-1.png)
*Contactos de los relés de uso general*

![](General-Purpose-THT.png)
*OS-General-Purpose-Relay — versión THT*

![](General-Purpose-SMD.png)
*OS-General-Purpose-Relay — versión SMD*

### Características

-   Compatible con **OS-Solenoid-Decoder** y **OS-Servo-Decoder**
-   Adecuado para:
    -   Conmutación de accesorios (luces, señales, animaciones)
    -   Polarización de frog en agujas **Electrofrog**
    -   Polarización de frog en agujas **Unifrog**
    -   **Encaminamiento de corriente en vías muertas**

### Ejemplos de Uso

-   Conmutar alimentación a secciones de vía aisladas
-   Crear conmutación automática de polaridad de frog
-   Controlar electrónica externa como LED, timbres o motores
-   Configuraciones de agujas con encaminamiento de corriente

------------------------------------------------------------------------

## 2. OS-Latching-Relay

El OS-Latching-Relay es un **relé biestable (enclavado) simple**.\
**Permanece en su última posición sin necesidad de alimentación continua**.

![](Latching-Relay-THT.png)
*OS-Latching-Relay — versión THT*

![](Latching-Relay-SMD.png)
*OS-Latching-Relay — versión SMD*

### Notas Importantes

-   No puede utilizarse en agujas **electrofrog**\
    (el electrofrog requiere un cambio de polaridad continuo y no enclavado)
-   Funciona perfectamente con agujas **unifrog**
-   La bobina del relé puede conectarse **en paralelo** con la bobina del solenoide de la aguja, no requiere decodificadores adicionales

### Casos de Uso con Decodificadores DCC

-   **Polarización de frog en agujas unifrog**
-   Agujas autónomas / encaminamiento de corriente
-   Conmutación de accesorios
-   Funcionamiento independiente con cualquier decodificador de solenoide

------------------------------------------------------------------------

## 3. Uso de los Relés con Decodificadores OS

### Con OS-Solenoid-Decoder

-   Compatible con ambos:
    -   OS-General-Purpose-Relay\
    -   OS-Latching-Relay (solo para unifrog)



### Con OS-Servo-Decoder

-   Compatible únicamente con:
    -   **OS-General-Purpose-Relay**
-   Usos típicos:
    -   Conmutación de polaridad de frog
    -   Conmutación de accesorios



------------------------------------------------------------------------

## 4. Uso Independiente

Ambos módulos de relé pueden utilizarse sin decodificadores OS.

### Requisitos

-   Una señal de control de nivel lógico de 5 V
-   Fuente de alimentación adecuada al tipo de relé
-   Cualquier microcontrolador, Arduino o decodificador de terceros capaz de
    accionar un relé pequeño

### Aplicaciones Independientes Típicas

-   Conmutación de LED o señales
-   Encaminamiento de corriente en vías muertas
-   Control de polaridad de frog en módulos de aguja
-   Tareas de automatización de baja corriente

------------------------------------------------------------------------

## Tabla Resumen

| Tipo de relé                 | Unifrog | Electrofrog | Conmutación de accesorios | Vías muertas autónomas | Compatible con               |
|---------------------------|---------|-------------|----------------------|------------------------|--------------------------|
| **OS-General-Purpose-Relay** | ✔       | ✔           | ✔                    | ✔                      | Decodificadores Servo y Solenoide |
| **OS-Latching-Relay**        | ✔       | ✖           | ✔                    | ✔                      | Solo decodificadores Solenoide     |


------------------------------------------------------------------------

## Ejemplos de Cableado

![](unifrog_bistable.png)
*Decodificador OS-Solenoid con 8 OS-latching-relays enchufados*

![](GP_relay_as_elekro_frog_solenoid.png)
*Relé OS-General-Purpose cableado al OS-Solenoid-Decoder para agujas electrofrog*

![](GP_relay_as_unifrog_servo.png)
*Relé OS-General-Purpose conectado al OS-Servo-Decoder para agujas unifrog*

![](GP_relay_as_elekro_frog_servo.png)
*Relé OS-General-Purpose conectado al OS-Servo-Decoder para agujas electrofrog*

## 5. Instrucciones adicionales para el pedido de PCB

Todos los OS-Relays han sido diseñados para poder pedirse en los llamados paneles. Cuando se piden en paneles, las distancias coinciden con las de las tomas de los decodificadores OS. Los PCB también pueden pedirse como unidades sueltas separadas, pero en paneles el coste por unidad es menor.

Para pedirlos en panel, hay que hacer clic en **Panel by JLCPCB** junto a **Delivery format**. Se abrirá una nueva ventana donde deberá establecer el número de columnas y filas. Hay 2 reglas:

- JLCPCB exige que los paneles tengan un tamaño superior a 70x70 mm; los relés miden aproximadamente 50 mm de largo y 15 mm de ancho.
- Si van a utilizarse en combinación con decodificadores OS Solenoid o servo, se recomiendan grupos de 4 unidades, aunque esto no es obligatorio.

Para cumplir el primer requisito se necesitan como mínimo paneles de 2 filas y 5 columnas. Para cumplir el segundo requisito, se recomienda aumentar a 8 columnas. Esto proporciona esencialmente 4 conjuntos.

Si conviene pedir paneles o PCB sueltos también depende de la cantidad que se desee. La cantidad mínima de pedido es de 5 unidades. Pueden ser 5 relés o 5 paneles de 10 a 16 módulos de relé cada uno. Siempre puede revisar el precio con el envío en el último paso, antes de pagar. Por tanto, puede cancelar el pedido en cualquier momento.

![](ORDERING_PANEL1.png)
*Distribución del panel — rieles de borde izquierda y derecha*

![](ORDERING_PANEL2.png)
*Configuración del panel en JLCPCB*

### Versión SMD — componente adicional necesario

La versión SMD utiliza un **conector de bornes vertical** que no es colocado por el servicio de montaje SMT. Este conector debe pedirse por separado y soldarse a mano.

- **Pieza:** XY2500F-F-3.5-3P
- **Número de pieza LCSC:** C560231

![](screwTerminalPlug.png)
*Conector de bornes vertical — XY2500F-F-3.5-3P (C560231)*

Al realizar un pedido de montaje SMT en JLCPCB, añada la siguiente nota en el campo **Special PCB Remarks**:

> El componente C560231 debe insertarse en el conector vertical.

JLCPCB se pondrá en contacto con usted después del pedido y cobrará una pequeña tarifa adicional por esta colocación manual.

---

Para más instrucciones sobre cómo pedir PCB, consulte [aquí](https://github.com/Open-Source-Model-Railway-Electronics/docs/blob/master/Ordering_bare_PCB/Ordering_bare_PCB-EN.md) para placas desnudas y [aquí](https://github.com/Open-Source-Model-Railway-Electronics/docs/blob/master/Ordering_SMT_ASSEMBLED_PCB/Ordering_Assembled_PCBs_JLCPCB-EN.md) para placas ensambladas SMT.
