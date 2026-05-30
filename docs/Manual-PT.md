> 🌐 &nbsp; [🇬🇧 EN](Manual-EN.md) &nbsp;|&nbsp; [🇩🇪 DE](Manual-DE.md) &nbsp;|&nbsp; [🇫🇷 FR](Manual-FR.md) &nbsp;|&nbsp; [🇳🇱 NL](Manual-NL.md) &nbsp;|&nbsp; [🇪🇸 ES](Manual-ES.md) &nbsp;|&nbsp; [🇮🇹 IT](Manual-IT.md) &nbsp;|&nbsp; [🇵🇱 PL](Manual-PL.md) &nbsp;|&nbsp; [🇨🇿 CS](Manual-CS.md) &nbsp;|&nbsp; [🇩🇰 DA](Manual-DA.md) &nbsp;|&nbsp; [🇳🇴 NO](Manual-NO.md) &nbsp;|&nbsp; [🇸🇪 SV](Manual-SV.md) &nbsp;|&nbsp; [🇭🇺 HU](Manual-HU.md) &nbsp;|&nbsp; 🇵🇹 PT

# Manual dos Módulos de Relé OS

![](all.png)

## Introdução

Este documento descreve os módulos de relé OS utilizados nos projectos de Open Source Model
Railway Electronics: - **OS-General-Purpose-Relay** (módulo de relé duplo) - **OS-Latching-Relay** (módulo de relé bistável simples)

Ambos os tipos de relé existem em versões **THT** e **SMD** e podem ser
ligados directamente nos decoders OS ou utilizados de forma autónoma.

------------------------------------------------------------------------

## 1. OS-General-Purpose-Relay

O módulo OS-General-Purpose-Relay contém **dois relés monostáveis**,
cada um com: - **1× Comum (COM)** - **1× Normalmente Aberto (NO)** - **1×
Normalmente Fechado (NC)**

![](image-1.png)
*Contactos dos Relés de Uso Geral*

![](General-Purpose-THT.png)
*OS-General-Purpose-Relay — versão THT*

![](General-Purpose-SMD.png)
*OS-General-Purpose-Relay — versão SMD*

### Características

-   Compatível com **OS-Solenoid-Decoder** e **OS-Servo-Decoder**
-   Adequado para:
    -   Comutação de acessórios (luzes, sinais, animações)
    -   Polarização de frog em agulhas **Electrofrog**
    -   Polarização de frog em agulhas **Unifrog**
    -   **Encaminhamento de energia em ramais**

### Exemplos de Utilização

-   Comutação de alimentação para secções de via isoladas
-   Criação de comutação automática de polaridade de frog
-   Controlo de electrónica externa como LED, sinos ou motores
-   Configurações de agulha com encaminhamento de energia

------------------------------------------------------------------------

## 2. OS-Latching-Relay

O OS-Latching-Relay é um **relé bistável (de retenção) simples**.\
**Mantém a sua última posição sem necessidade de alimentação contínua**.

![](Latching-Relay-THT.png)
*OS-Latching-Relay — versão THT*

![](Latching-Relay-SMD.png)
*OS-Latching-Relay — versão SMD*

### Notas Importantes

-   Não pode ser utilizado para agulhas **electrofrog**\
    (o electrofrog requer uma mudança de polaridade contínua e não retentiva)
-   Funciona perfeitamente com agulhas **unifrog**
-   A bobine do relé pode ser ligada **em paralelo** com a bobine solenóide da agulha; não requer decoders adicionais

### Casos de Utilização com Decoders DCC

-   **Polarização de frog Unifrog**
-   Agulhas autónomas / encaminhamento de energia
-   Comutação de acessórios
-   Funcionamento autónomo com qualquer decoder solenóide

------------------------------------------------------------------------

## 3. Utilização dos Relés com Decoders OS

### Com OS-Solenoid-Decoder

-   Suporta ambos:
    -   OS-General-Purpose-Relay\
    -   OS-Latching-Relay (apenas para unifrog)



### Com OS-Servo-Decoder

-   Suporta apenas:
    -   **OS-General-Purpose-Relay**
-   Utilizações típicas:
    -   Comutação de polaridade de frog
    -   Comutação de acessórios



------------------------------------------------------------------------

## 4. Utilização Autónoma

Ambos os módulos de relé podem ser utilizados sem decoders OS.

### Requisitos

-   Um sinal de controlo de nível lógico de 5V
-   Fonte de alimentação adequada ao tipo de relé
-   Qualquer microcontrolador, Arduino ou decoder de terceiros capaz de
    accionar um pequeno relé

### Aplicações Autónomas Típicas

-   Comutação de LED ou sinais
-   Encaminhamento de energia em ramais
-   Controlo de polaridade de frog em módulos de agulha
-   Tarefas de automação de baixa corrente

------------------------------------------------------------------------

## Tabela Resumo

| Tipo de Relé                 | Unifrog | Electrofrog | Comutação de Acessórios | Ramais Autónomos | Compatível com               |
|---------------------------|---------|-------------|----------------------|------------------------|--------------------------|
| **OS-General-Purpose-Relay** | ✔       | ✔           | ✔                    | ✔                      | Decoders Servo + Solenóide |
| **OS-Latching-Relay**        | ✔       | ✖           | ✔                    | ✔                      | Apenas Decoders Solenóide     |


------------------------------------------------------------------------

## Exemplos de Ligação

![](unifrog_bistable.png)
*Decoder OS-Solenoid com 8 OS-latching-relays ligados*

![](GP_relay_as_elekro_frog_solenoid.png)
*OS-General-Purpose relay ligado ao OS-Solenoid-Decoder para agulhas electrofrog*

![](GP_relay_as_unifrog_servo.png)
*OS-General-Purpose relay ligado ao OS-Servo-Decoder para agulhas unifrog*

![](GP_relay_as_elekro_frog_servo.png)
*OS-General-Purpose relay ligado ao OS-Servo-Decoder para agulhas electrofrog*

## 5. Instruções adicionais para encomenda de PCBs

Todos os OS-Relays foram concebidos para poderem ser encomendados em painéis. Quando encomendados em painéis, têm as mesmas distâncias que os sockets dos decoders OS. As PCBs também podem ser encomendadas como unidades separadas soltas, mas em painéis o custo por unidade é mais baixo.

Para as encomendar em painel, clique em **Panel by JLCPCB** junto a **Delivery format**. Isso abre uma nova janela onde tem de definir o número de colunas e linhas. Existem 2 regras:

- A JLCPCB exige que os painéis tenham dimensões superiores a 70×70 mm; os relés têm cerca de 50 mm de comprimento e 15 mm de largura. 
- Se forem utilizados em conjunto com decoders OS Solenoid ou servo, convém ter grupos de 4 unidades, embora tal não seja obrigatório.

Para cumprir a primeira exigência são necessários pelo menos painéis de 2 linhas e 5 colunas. Para cumprir a segunda exigência, recomendo aumentar para 8 colunas. Isto dá essencialmente 4 conjuntos.

Se deve encomendar painéis ou PCBs soltas depende também da quantidade desejada. A quantidade mínima de encomenda é 5 unidades. Portanto, podem ser 5 relés ou 5 painéis de 10 a 16 módulos de relé cada. Pode sempre verificar o preço com o envio no último passo, antes de pagar. Pode por isso cancelar a encomenda em qualquer momento.

![](ORDERING_PANEL1.png)
*Disposição do painel — calhas laterais à esquerda e à direita*

![](ORDERING_PANEL2.png)
*Definições de configuração do painel no JLCPCB*

### Versão SMD — componente adicional necessário

A versão SMD utiliza um **conector de parafuso vertical** que não é colocado pelo serviço de montagem SMT. Este conector deve ser encomendado separadamente e soldado à mão.

- **Componente:** XY2500F-F-3.5-3P
- **Número de peça LCSC:** C560231

![](screwTerminalPlug.png)
*Conector de parafuso vertical — XY2500F-F-3.5-3P (C560231)*

Ao realizar um pedido de montagem SMT na JLCPCB, adicione a seguinte nota no campo **Special PCB Remarks**:

> O componente C560231 deve ser inserido no conector vertical.

A JLCPCB contactará após a encomenda e cobrará uma pequena taxa adicional por esta colocação manual.

---

Para instruções mais detalhadas sobre a encomenda de PCBs consulte [aqui](https://github.com/Open-Source-Model-Railway-Electronics/docs/blob/master/Ordering_bare_PCB/Ordering_bare_PCB-EN.md) para placas nuas e [aqui](https://github.com/Open-Source-Model-Railway-Electronics/docs/blob/master/Ordering_SMT_ASSEMBLED_PCB/Ordering_Assembled_PCBs_JLCPCB-EN.md) para placas com montagem SMT
