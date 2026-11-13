---
title: FEEG1004 B6 - Sequential Logic - Flip-Flops, Registers and Counters
module: FEEG1004 Electronics
type: topic
stream: 'Part B: Electronics'
order: 6
tags:
- feeg1004
- electronics
- digital-electronics
- sequential-logic
- flip-flops
- shift-registers
- counters
- memory
aliases:
- EL5 sequential logic
- Sequential logic
date: 2026-09-27
status: lectured
parent:
- "[[FEEG1004 Electronics Hub]]"
prerequisites:
- "[[FEEG1004 B5 - Combinational Logic - Boolean Algebra and Karnaugh Maps]]"
next_topics:
- "[[FEEG1004 C1 - Magnetic Circuits, Faraday's Law and Force on Conductors]]"
key_concepts:
- "[[D-Type Flip-Flop]]"
- "[[Shift Registers and Binary Counters]]"
sources:
- 02 - Sources/S1 Electronics/S1 Electronics Notes - Diodes Transistors Op-Amps and Digital - Mills.pdf
- 02 - Sources/S1 Electronics/S1-W15-EL5 Digital Logic 2 Sequential - Interactive.pdf
- 02 - Sources/Lectures/FEEG1004 Lecture 5a.txt
- 02 - Sources/Lectures/FEEG1004 Lecture 5b.txt
- 02 - Sources/Tutorial Sheets/Tutorial Sheet 04 - Electronics B - Operational Amplifiers.pdf
coverage: Lecture 5a (ll. 1–190, sequential vs combinational logic, cross-coupled NAND R-S latch, clocked R-S latch, transparent D latch, and master-slave falling-edge-triggered D-type flip-flop), Lecture 5b (ll. 1–172, 4-bit serial-to-parallel shift register, LED scrolling display, 4-bit ripple-through binary up-counter, divide-by-2 frequency division, real-time clock, and SRAM/DRAM/Flash memory), W15-EL5 interactive session (divide-by-2 D-flip-flop, 2-bit twisted-ring synchronous state table, and AC-driven LED conduction window)
---

# FEEG1004 B6 - Sequential Logic - Flip-Flops, Registers and Counters

> [!abstract] Summary
> Sequential logic adds feedback to logic gates so that a circuit has memory: its output depends on the present inputs and on a state stored earlier. The one-bit storage element develops from the cross-coupled NAND R-S latch, through the clocked latch, to the edge-triggered D-type flip-flop, which copies its data input to its output only on an active clock edge, $Q^{(k+1)} = D^{(k)}$. Chains of D flip-flops form shift registers, ripple counters and frequency dividers, and arrays of storage cells form SRAM, DRAM and Flash memory.

> [!summary]- Exam use: quick path
> - **Use it when:** tracing the state sequence of a D flip-flop circuit, a shift register or a ripple counter, or finding the output frequencies of a divider chain.
> - **Assumptions:** ideal logic levels; edge-triggered flip-flops that sample $D$ instantly on the active edge (a triangle $\triangleright$ at the clock input: rising edge $0 \to 1$ for an unbarred $C$, falling edge $1 \to 0$ for a barred $\overline{C}$). The gate-level wiring of the master–slave flip-flop is not required, but tracing state sequences of D flip-flop circuits is (W15-EL5 interactive).
> - **Method:** 1. Decide whether the flip-flops are synchronously clocked (all clock pins on one master clock) or ripple clocked (each clock driven by an output such as $\overline{Q}$ of the previous stage), and whether the active edge is rising or falling. 2. Tabulate the present outputs $Q_i$ and the data inputs $D_i$ immediately before each edge. 3. On each active edge, copy each pre-edge $D_i$ into $Q_i$ and set $\overline{Q}_i$ to its complement. 4. Read a counter word as $DCBA_2$, with the most significant bit (slowest stage $D$, weight $2^3 = 8$) on the left and the least significant bit (fastest stage $A$, weight $2^0 = 1$) on the right. 5. For a divider chain, stage $m$ runs at $f_{\text{clock}}/2^m$ and $N$ stages give $2^N$ states.
> - **Common mistakes:** updating synchronous stages one after another within a single edge, so that a stage uses its neighbour's new output instead of the pre-edge value; reading a counter word in schematic order $ABCD$ instead of $DCBA$.
> - **Practise:** [[#Worked examples]] · [[#Two-bit synchronous state machine]]

Combinational gates ([[FEEG1004 B5 - Combinational Logic - Boolean Algebra and Karnaugh Maps]]) cannot count events, store a byte or step through a timed control sequence, because their outputs change as soon as their inputs change. Combining gates with memory elements gives **state machines**, whose next state is computed from both the current stored state and the external inputs. A digital circuit that retains information about past inputs is an **information register**, and its basic one-bit cell is the flip-flop.

Memory comes from feedback. When the output of each of two gates is fed into the other, the pair has two self-reinforcing states and stays in whichever one it was last pushed into. Adding a clock restricts when the state may change, and placing two such latches in series makes the change happen only at the instant of a clock edge. That edge-triggered behaviour is what allows flip-flops to be chained into registers and counters without data racing through several stages at once.

## 1. From the R-S latch to the edge-triggered D flip-flop

### Basic R-S flip-flop

The simplest one-bit memory cell is the **basic R-S flip-flop**, or R-S latch (Mills §3.3.1). Two 2-input NAND gates are cross-coupled: the output $Q$ of the upper gate feeds one input of the lower gate, and the complementary output $\overline{Q}$ of the lower gate feeds one input of the upper gate.

The two external inputs act when pulled to logic 0, so they are labelled $\overline{S}$ (NOT-Set, active low) and $\overline{R}$ (NOT-Reset, active low). A 2-input NAND gate outputs 0 only when both inputs are 1, so forcing either input to 0 forces its output to 1 regardless of the other input ($\overline{0 \cdot X} = \overline{0} = 1$). This property governs the five-step sequence of events:

1. Initially $\overline{S} = 1$, $\overline{R} = 1$, $Q = 1$ and $\overline{Q} = 0$. The lower gate sees $(1, 1)$ and holds $\overline{Q} = \overline{1 \cdot 1} = 0$; that 0 feeds back to the upper gate, which holds $Q = \overline{1 \cdot 0} = 1$. The outputs reinforce each other and are stable, hence the name **bistable**: the circuit can rest in either of two stable states, $Q = 1$ or $Q = 0$.
2. $\overline{R}$ is pulsed to 0 while $\overline{S} = 1$. The lower gate is forced to $\overline{Q} = \overline{Q \cdot 0} = 1$. The upper gate now sees $(1, 1)$ and switches to $Q = \overline{1 \cdot 1} = 0$, and $Q = 0$ feeds back to lock $\overline{Q} = 1$.
3. $\overline{R}$ returns to 1. Because $Q = 0$ already holds the lower gate's output at 1, nothing changes, and further pulses on $\overline{R}$ have no effect. The circuit has stored the fact that Reset was the last input pulsed low, with $Q = 0$ and $\overline{Q} = 1$.
4. $\overline{S}$ is pulsed to 0 while $\overline{R} = 1$. The upper gate is forced to $Q = \overline{0 \cdot \overline{Q}} = 1$, which with $\overline{R} = 1$ drives the lower gate to $\overline{Q} = \overline{1 \cdot 1} = 0$, which in turn holds $Q = 1$.
5. $\overline{S}$ returns to 1. The outputs stay latched at $Q = 1$, $\overline{Q} = 0$, storing the fact that Set was the last input pulsed low.

| $\overline{S}$ (active-low Set) | $\overline{R}$ (active-low Reset) | Output $Q$ | Output $\overline{Q}$ | Operating mode |
| :---: | :---: | :---: | :---: | :--- |
| $1$ | $1$ | $Q_{\text{prev}}$ (unchanged) | $\overline{Q}_{\text{prev}}$ (unchanged) | Hold (stores the last active pulse) |
| $1$ | $0$ | $0$ | $1$ | Reset (stores 0 at $Q$) |
| $0$ | $1$ | $1$ | $0$ | Set (stores 1 at $Q$) |
| $0$ | $0$ | $1$ | $1$ | Forbidden ($Q = \overline{Q} = 1$ violates complementarity) |

> [!warning] The forbidden state and the power-up race
> Pulling $\overline{S} = 0$ and $\overline{R} = 0$ together forces both NAND gates to output 1, giving the contradictory state $Q = 1$ and $\overline{Q} = 1$. If both inputs are then released to 1 at the same time, or when the chip is first powered up, the final state depends on which input crosses the logic-high threshold a nanosecond before the other: a **race condition**.

Flip-flop packages bring out both $Q$ and $\overline{Q}$ because the cross-coupled pair generates $\overline{Q}$ internally anyway, and providing it on a pin saves an external NOT gate whenever downstream logic needs the complement.

### Clocked R-S flip-flop and transparent D latch

In a large digital system such as a microprocessor, signals at different points change at slightly different times because of gate delays. To stop the resulting glitches from corrupting stored bits, sequential circuits use a system-wide square-wave **clock** $C$ to set when state changes are allowed.

Two steering NAND gates placed ahead of the basic latch make the **clocked R-S flip-flop** (Mills §3.3.2, Figure 3.3.2). One receives $S$ and $C$ and drives the internal node $\overline{S} = \overline{S \cdot C}$; the other receives $R$ and $C$ and drives $\overline{R} = \overline{R \cdot C}$. This front end inverts the input sense, so $S$ and $R$ become active high (normally 0, pulsed to 1 to set or reset). It also gates both inputs with the clock: while $C = 0$, both steering gates output 1 whatever $S$ and $R$ are, which freezes the latch in its hold state. Only while $C = 1$ can $S = 1$ pull $\overline{S}$ to 0, or $R = 1$ pull $\overline{R}$ to 0.

The forbidden $S = R = 1$ condition is removed by connecting a single **data** input $D$ directly to the upper steering gate ($S = D$) and through an inverter to the lower one ($R = \overline{D}$). $S$ and $R$ are then always complements and can never both be 1. While $C = 1$, $D = 1$ sets $Q = 1$ and $D = 0$ resets $Q = 0$; the latch is **transparent**, because $Q$ follows every change on $D$ for as long as $C = 1$. When $C$ goes low the latch closes and holds the value $D$ had just before $C$ fell.

### Master–slave edge-triggered D flip-flop

A level-triggered transparent latch still fails in counters and shift registers. If the clock stays high for even a few microseconds, several transitions on $D$, including the flip-flop's own output fed back to $D$, can pass straight through the latch during one high period.

The **edge-triggered D-type flip-flop** (Mills §3.3.3, Figure 3.3.3.1) cascades two clocked latches in a **master–slave** arrangement, with an inverter on the clock line between them. While $C = 1$, the master latch is enabled and tracks $D$, and the inverter holds the slave's clock at $\overline{C} = 0$, so the output $Q$ cannot change. At the instant the clock falls from 1 to 0 (the **falling edge**), the master freezes the value of $D$ present at that moment, and $\overline{C}$ rises to 1, enabling the slave to copy the captured bit to $Q$.

![[ee_b6_flipflop_counter_timing.png|900]]

The output therefore updates only at the active clock transition. For the circuit of Figure 3.3.3.1 this is the falling edge, marked on block symbols by a small triangle $\triangleright$ at a clock input labelled $\overline{C}$; placing the clock inverter on the master stage instead gives a rising-edge ($0 \to 1$) device, marked by $\triangleright$ at an unbarred input $C$. Changes on $D$ while the clock is steady at 1, steady at 0, or moving in the inactive direction are ignored, as panel (a) of the figure shows. Writing $k$ for the active edge, the update rule is

$$
Q^{(k+1)} = D^{(k)}, \qquad \overline{Q}^{(k+1)} = \overline{D^{(k)}}
$$

and between active edges $Q$ and $\overline{Q}$ stay latched whatever happens on $D$.

## 2. Shift registers

$N$ edge-triggered D flip-flops on a **common clock line**, with the output $Q$ of each wired to the data input $D$ of the next, form an $N$-bit **shift register** (Mills §3.3.4).

![[ee_b6_shift_register.png|900]]

In the 4-bit falling-edge-triggered register of Figure 3.3.4.1, data enter the leftmost flip-flop one bit at a time as a **serial input**, the four stage outputs $A, B, C, D$ are **parallel outputs** available simultaneously, and the last stage output $D$ is also a **serial output**. At each falling edge the bit at the serial input is latched into stage $A$ ($Q_A \leftarrow D_{\text{serial}}$), while the previous contents of $A, B, C$ move into $B, C, D$ ($Q_B \leftarrow Q_A$, $Q_C \leftarrow Q_B$, $Q_D \leftarrow Q_C$).

The new bit in stage $A$ does not race on into $B$, $C$ and $D$ on the same edge, because each edge-triggered flip-flop has a small but finite **propagation delay** after the edge before its output changes. Stage $B$ therefore samples the old value of $Q_A$ that was sitting on $D_B$ just before the edge.

After four falling edges, a 4-bit word applied bit by bit at the input sits across the four flip-flops and can be read at once from $A, B, C, D$: **serial-in, parallel-out** conversion. Eight flip-flops store one **byte** ($8\ \text{bits}$). Further clock pulses shift the stored bits out one by one at the serial output.

Besides serial-to-parallel conversion in communication interfaces, shift registers drive **scrolling LED message signs** (Mills Figure 3.3.4.2). Each row of LEDs in a waiting-room or transport display is driven by the parallel outputs of a long shift register clocked at a steady rate of a few hertz. Feeding the serial output of the last flip-flop back to the serial input of the first makes a circular loop, so the text scrolls continuously across the display and repeats.

## 3. Binary ripple counters and frequency division

### Divide-by-2 toggle stage

If the complementary output of a D flip-flop is wired back to its own data input ($D = \overline{Q}$), then before every active edge $D$ holds the opposite of the present output, and each edge flips $Q$:

$$
Q^{(k+1)} = D^{(k)} = \overline{Q}^{(k)}
$$

Starting from $Q = 0$ (so $D = \overline{Q} = 1$), the first rising edge sets $Q = 1$ (and $D = 0$), and the second resets $Q = 0$ (and $D = 1$). Two input clock periods are needed for one full period of $Q$ ($0 \to 1 \to 0$), so $Q$ and $\overline{Q}$ run at half the clock frequency, with twice the period:

$$
f_Q = \frac{f_{\text{clock}}}{2}
$$

A D flip-flop with $\overline{Q}$ tied to $D$ is therefore a **divide-by-2 counter**, or frequency divider.

### Four-bit ripple-through binary up-counter

Four rising-edge-triggered divide-by-2 stages $A, B, C, D$, in which the $\overline{Q}$ of each stage feeds both its own $D$ input and the clock input of the next stage, form a 4-bit **ripple-through binary up-counter** (Mills §3.3.5, Figure 3.3.5; panel (b) of the timing figure).

> [!warning] Junction dots and wire crossovers
> In Mills Figure 3.3.5, a solid dot marks where two wires are joined; wires that cross at right angles without a dot are **not** connected. The feedback wire from $\overline{Q}$ loops up to the $D$ input and crosses the $Q$ output line without a dot, so $D$ is connected to $\overline{Q}$, not to $Q$.

Starting from the reset state $Q_A = Q_B = Q_C = Q_D = 0$, each stage's pre-edge input $D = \overline{Q}$ is 1. Stage $A$, the least significant bit (weight $2^0 = 1$), is driven by the external clock, so $Q_A$ toggles on every rising edge and $f_A = f_{\text{in}}/2$. The clock input of stage $B$ (weight $2^1 = 2$) is $\overline{Q}_A$, so $B$ toggles only when $\overline{Q}_A$ rises, which is exactly when $Q_A$ falls from 1 to 0: once every two input pulses, giving $f_B = f_{\text{in}}/4$. In the same way stage $C$ (weight $2^2 = 4$) toggles when $Q_B$ falls, once every four input pulses ($f_C = f_{\text{in}}/8$), and stage $D$, the most significant bit (weight $2^3 = 8$), toggles when $Q_C$ falls, once every eight input pulses ($f_D = f_{\text{in}}/16$). In general stage $m$ (with stage 1 the least significant) runs at

$$
f_m = \frac{f_{\text{clock}}}{2^m}
$$

The full sequence over 16 input pulses is tabulated below, giving $Q$ and $(\overline{Q} = D)$ for each stage in schematic order $A, B, C, D$, and the count read in positional order $DCBA_2 = 8D + 4C + 2B + 1A$:

| Clock pulse # | Input edge | Stage $A$: $Q_A\ (\overline{Q}_A)$ | Stage $B$: $Q_B\ (\overline{Q}_B)$ | Stage $C$: $Q_C\ (\overline{Q}_C)$ | Stage $D$: $Q_D\ (\overline{Q}_D)$ | Binary word $DCBA_2$ | Decimal count |
| :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| $0$ (init) | $0$ | $0\ (1)$ | $0\ (1)$ | $0\ (1)$ | $0\ (1)$ | $0000_2$ | $0$ |
| $1$ | $\uparrow\ (0\to 1)$ | $1\ (0)$ | $0\ (1)$ | $0\ (1)$ | $0\ (1)$ | $0001_2$ | $1$ |
| $2$ | $\uparrow\ (0\to 1)$ | $0\ (1)$ | $1\ (0)$ | $0\ (1)$ | $0\ (1)$ | $0010_2$ | $2$ |
| $3$ | $\uparrow\ (0\to 1)$ | $1\ (0)$ | $1\ (0)$ | $0\ (1)$ | $0\ (1)$ | $0011_2$ | $3$ |
| $4$ | $\uparrow\ (0\to 1)$ | $0\ (1)$ | $0\ (1)$ | $1\ (0)$ | $0\ (1)$ | $0100_2$ | $4$ |
| $5$ | $\uparrow\ (0\to 1)$ | $1\ (0)$ | $0\ (1)$ | $1\ (0)$ | $0\ (1)$ | $0101_2$ | $5$ |
| $6$ | $\uparrow\ (0\to 1)$ | $0\ (1)$ | $1\ (0)$ | $1\ (0)$ | $0\ (1)$ | $0110_2$ | $6$ |
| $7$ | $\uparrow\ (0\to 1)$ | $1\ (0)$ | $1\ (0)$ | $1\ (0)$ | $0\ (1)$ | $0111_2$ | $7$ |
| $8$ | $\uparrow\ (0\to 1)$ | $0\ (1)$ | $0\ (1)$ | $0\ (1)$ | $1\ (0)$ | $1000_2$ | $8$ |
| $9$ | $\uparrow\ (0\to 1)$ | $1\ (0)$ | $0\ (1)$ | $0\ (1)$ | $1\ (0)$ | $1001_2$ | $9$ |
| $10$ | $\uparrow\ (0\to 1)$ | $0\ (1)$ | $1\ (0)$ | $0\ (1)$ | $1\ (0)$ | $1010_2$ | $10$ |
| $11$ | $\uparrow\ (0\to 1)$ | $1\ (0)$ | $1\ (0)$ | $0\ (1)$ | $1\ (0)$ | $1011_2$ | $11$ |
| $12$ | $\uparrow\ (0\to 1)$ | $0\ (1)$ | $0\ (1)$ | $1\ (0)$ | $1\ (0)$ | $1100_2$ | $12$ |
| $13$ | $\uparrow\ (0\to 1)$ | $1\ (0)$ | $0\ (1)$ | $1\ (0)$ | $1\ (0)$ | $1101_2$ | $13$ |
| $14$ | $\uparrow\ (0\to 1)$ | $0\ (1)$ | $1\ (0)$ | $1\ (0)$ | $1\ (0)$ | $1110_2$ | $14$ |
| $15$ | $\uparrow\ (0\to 1)$ | $1\ (0)$ | $1\ (0)$ | $1\ (0)$ | $1\ (0)$ | $1111_2$ | $15$ |
| $16$ | $\uparrow\ (0\to 1)$ | $0\ (1)$ | $0\ (1)$ | $0\ (1)$ | $0\ (1)$ | $0000_2$ | $0$ (rollover) |

On pulse 8 (and again on pulse 16), $Q_A$ falls ($\overline{Q}_A$ rises), which makes $Q_B$ fall ($\overline{Q}_B$ rises), which makes $Q_C$ fall ($\overline{Q}_C$ rises), which finally toggles $Q_D$. The carry propagates down the chain one stage at a time, each stage waiting for the propagation delay of the one before, which is why this is called a **ripple-through counter**.

Combining a binary counter with gates that detect a chosen count and reset the flip-flops makes a counter that divides by any integer $M$, not only by powers of two. A $1\ \text{Hz}$ (one pulse per second) oscillator feeding a divide-by-60 counter gives one pulse per minute; a second divide-by-60 counter gives one pulse per hour; and a divide-by-24 counter after that gives one pulse per day. This chain is a digital **real-time clock**.

## 4. Semiconductor memory: SRAM, DRAM and Flash

A shift register only gives data back in the order in which they were shifted in. A **random access memory** (RAM) chip arranges thousands or millions of storage cells in an addressable array, so that any bit or byte can be read or written in any order (Mills §3.3.6). The three memory technologies are:

| Memory type | Bit-storage mechanism | Volatility (power removed) | Refresh needed? | Characteristics |
| :--- | :--- | :---: | :---: | :--- |
| SRAM (static RAM) | Flip-flop latch (cross-coupled transistor gates per bit) | Volatile (data lost) | No (holds its state while DC power is supplied) | Very fast access; lower density (4–6 transistors per bit); used for CPU caches and registers |
| DRAM (dynamic RAM) | Charge on the insulated gate capacitance of a single MOSFET (charged: MOSFET on, 1; discharged: off, 0) | Volatile (data lost) | Yes (the gate charge leaks away and must be periodically read and rewritten) | Much higher density and lower cost per bit than SRAM (1 MOSFET per bit); used for main system RAM |
| Flash memory (EEPROM family) | Charge trapped on a fully insulated **floating gate** inside a MOS transistor | Non-volatile (keeps its charge indefinitely with power off) | No | Electrically erasable and reprogrammable; used for portable storage, solid-state drives and microcontroller firmware |

## Worked examples

### Two-bit synchronous state machine

Two rising-edge-triggered D flip-flops, storing $Q_1$ and $Q_0$, share a common clock (W15-EL5 interactive). The output $Q_0$ of the second flip-flop is wired to the data input of the first ($D_1 = Q_0$), and the complementary output $\overline{Q}_1$ of the first is wired to the data input of the second ($D_0 = \overline{Q}_1$). Starting from $Q_1 Q_0 = 00$, the task is the sequence of states over the first four rising edges.

Because both flip-flops share the clock, both sample their pre-edge inputs $D_1^{(k)} = Q_0^{(k)}$ and $D_0^{(k)} = \overline{Q}_1^{(k)}$ simultaneously at each rising edge:

$$
Q_1^{(k+1)} = D_1^{(k)} = Q_0^{(k)}, \qquad Q_0^{(k+1)} = D_0^{(k)} = \overline{Q}_1^{(k)}
$$

Edge by edge:

1. Before edge 1 ($Q_1 = 0, Q_0 = 0$): $D_1 = Q_0 = 0$ and $D_0 = \overline{Q}_1 = \overline{0} = 1$, so edge 1 gives $Q_1 \leftarrow 0$, $Q_0 \leftarrow 1$ (state $01$).
2. Before edge 2 ($Q_1 = 0, Q_0 = 1$): $D_1 = Q_0 = 1$ and $D_0 = \overline{Q}_1 = \overline{0} = 1$, so edge 2 gives $Q_1 \leftarrow 1$, $Q_0 \leftarrow 1$ (state $11$).
3. Before edge 3 ($Q_1 = 1, Q_0 = 1$): $D_1 = Q_0 = 1$ and $D_0 = \overline{Q}_1 = \overline{1} = 0$, so edge 3 gives $Q_1 \leftarrow 1$, $Q_0 \leftarrow 0$ (state $10$).
4. Before edge 4 ($Q_1 = 1, Q_0 = 0$): $D_1 = Q_0 = 0$ and $D_0 = \overline{Q}_1 = \overline{1} = 0$, so edge 4 gives $Q_1 \leftarrow 0$, $Q_0 \leftarrow 0$ (state $00$, the initial state).

| Clock edge $k$ | Present state $Q_1$ | Present state $Q_0$ | Pre-edge $D_1 = Q_0$ | Pre-edge $D_0 = \overline{Q}_1$ | Next state $Q_1^{(k+1)}$ | Next state $Q_0^{(k+1)}$ |
| :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| Initial ($0$) | $0$ | $0$ | — | — | $0$ | $0$ |
| $1$ | $0$ | $0$ | $0$ | $1$ | $0$ | $1$ |
| $2$ | $0$ | $1$ | $1$ | $1$ | $1$ | $1$ |
| $3$ | $1$ | $1$ | $1$ | $0$ | $1$ | $0$ |
| $4$ | $1$ | $0$ | $0$ | $0$ | $0$ | $0$ |

The sequence is $00 \to 01 \to 11 \to 10 \to 00 \dots$. This circuit is a twisted-ring (**Johnson**) counter, and its states follow the 2-bit Gray code.

> [!check] Simulation in Python
> Simulating the synchronous update `Q1, Q0 = Q0, 1 - Q1` from `(0, 0)` with `q = (0, 0); [q := (q[1], 1 - q[0]) for _ in range(4)]` gives `[(0, 1), (1, 1), (1, 0), (0, 0)]`, the sequence `00, 01, 11, 10, 00`. The counter divides the clock frequency by 4, with one bit changing on each edge.

### Four-bit serial-in, parallel-out shift register

A 4-bit falling-edge-triggered serial-in, parallel-out register (Figure 3.3.4.1, stages $A, B, C, D$ from left to right) starts cleared at $Q_A Q_B Q_C Q_D = 0000$. The serial data $D_{\text{in}} = 1, 0, 1, 1$ are applied before four successive falling edges ($k = 1, 2, 3, 4$), followed by $D_{\text{in}} = 0$. The task is to trace the parallel outputs over the first five edges, and to find the time needed to load an 8-bit byte into an 8-stage register clocked at $f_{\text{clock}} = 2.0\ \text{MHz}$.

On each falling edge every stage updates simultaneously, with $Q_A^{(k)} = D_{\text{in}}^{(k)}$, $Q_B^{(k)} = Q_A^{(k-1)}$, $Q_C^{(k)} = Q_B^{(k-1)}$ and $Q_D^{(k)} = Q_C^{(k-1)}$:

| Falling clock edge $k$ | Serial input $D_{\text{in}}^{(k)}$ | $Q_A$ (Stage 1) | $Q_B$ (Stage 2) | $Q_C$ (Stage 3) | $Q_D$ (Stage 4 / Serial out) |
| :---: | :---: | :---: | :---: | :---: | :---: |
| $0$ (initial) | — | $0$ | $0$ | $0$ | $0$ |
| $1$ | $1$ | $\mathbf{1}$ | $0$ | $0$ | $0$ |
| $2$ | $0$ | $0$ | $\mathbf{1}$ | $0$ | $0$ |
| $3$ | $1$ | $1$ | $0$ | $\mathbf{1}$ | $0$ |
| $4$ | $1$ | $1$ | $1$ | $0$ | $\mathbf{1}$ |
| $5$ | $0$ | $0$ | $1$ | $1$ | $0$ |

The first input bit (bold) moves one column to the right on each falling edge ($Q_A \to Q_B \to Q_C \to Q_D$) and reaches $Q_D$ on the fourth edge, when the whole 4-bit word $Q_A Q_B Q_C Q_D = 1101$ is available on the parallel outputs.

For the 8-bit byte at $2.0\ \text{MHz}$, one clock period is

$$
T_{\text{clock}} = \frac{1}{f_{\text{clock}}} = \frac{1}{2.0 \times 10^6\ \text{Hz}} = 0.50 \times 10^{-6}\ \text{s} = 0.50\ \mu\text{s}
$$

and shifting $N = 8$ bits into an 8-stage register takes 8 periods:

$$
t_{\text{load}} = N T_{\text{clock}} = 8 \times 0.50\ \mu\text{s} = 4.0\ \mu\text{s}
$$

> [!check] Bit-position invariant
> Since $Q_m^{(k)} = D_{\text{in}}^{(k - m + 1)}$ for stage $m \in \{1, 2, 3, 4\}$, after edge $k = 4$ the parallel outputs are $(Q_A^{(4)}, Q_B^{(4)}, Q_C^{(4)}, Q_D^{(4)}) = (D_{\text{in}}^{(4)}, D_{\text{in}}^{(3)}, D_{\text{in}}^{(2)}, D_{\text{in}}^{(1)}) = (1, 1, 0, 1)$, matching row $k = 4$ of the table.

### Ripple counter frequencies and a divide-by-60 stage

Part (a): a 4-bit rising-edge-triggered ripple up-counter (stages $A, B, C, D$) is driven by a $f_{\text{in}} = 32\ \text{kHz}$ square-wave clock from $DCBA_2 = 0000_2$. Find the frequency and period at each stage, and the state after 53 rising edges. Part (b): find the minimum number of D flip-flops for a divide-by-60 seconds-to-minutes stage of a real-time clock.

For part (a), stage $m \in \{1, 2, 3, 4\}$ divides $f_{\text{in}} = 32\ \text{kHz}$ by $2^m$:

$$
\begin{aligned}
f_A &= \frac{f_{\text{in}}}{2^1} = \frac{32\ \text{kHz}}{2} = 16\ \text{kHz}, & T_A &= \frac{1}{16\ \text{kHz}} = 62.5\ \mu\text{s} \\[4pt]
f_B &= \frac{f_{\text{in}}}{2^2} = \frac{32\ \text{kHz}}{4} = 8.0\ \text{kHz}, & T_B &= \frac{1}{8.0\ \text{kHz}} = 125\ \mu\text{s} \\[4pt]
f_C &= \frac{f_{\text{in}}}{2^3} = \frac{32\ \text{kHz}}{8} = 4.0\ \text{kHz}, & T_C &= \frac{1}{4.0\ \text{kHz}} = 250\ \mu\text{s} \\[4pt]
f_D &= \frac{f_{\text{in}}}{2^4} = \frac{32\ \text{kHz}}{16} = 2.0\ \text{kHz}, & T_D &= \frac{1}{2.0\ \text{kHz}} = 500\ \mu\text{s}
\end{aligned}
$$

A 4-bit counter rolls over to $0000_2$ every $2^4 = 16$ pulses, so the count after 53 edges is $53$ modulo 16:

$$
\begin{aligned}
53 &= (3 \times 16) + 5 \\[4pt]
\text{Count}_{53} &\equiv 53 \pmod{16} = 5_{10}
\end{aligned}
$$

Writing $5_{10} = (0 \times 8) + (1 \times 4) + (0 \times 2) + (1 \times 1)$ in 4-bit binary:

$$
DCBA_2 = 0101_2 \qquad (Q_D = 0,\ Q_C = 1,\ Q_B = 0,\ Q_A = 1)
$$

For part (b), an $N$-bit counter has $2^N$ distinct states, so $2^N \ge 60$ is needed. Five flip-flops give $2^5 = 32 < 60$, which is too few; six give $2^6 = 64 \ge 60$. At least **6 D flip-flops** are required, with combinational reset logic that returns the counter to $000000_2$ when it reaches $60_{10} = 111100_2$.

### LED driven by a sinusoidal source

In this exam-style question (W15-EL5 interactive), a $5.0\ \text{V}_{\text{rms}}$, $50\ \text{Hz}$ sinusoidal source $v_{\text{in}}(t)$ drives a light-emitting diode (forward threshold $V_F = 2.8\ \text{V}$) in series with a current-limiting resistor $R = 200\ \Omega$. Part (a) asks for the peak voltage $V_{\text{peak}}$, the period $T$, and the instants $t_{\text{on}}$ and $t_{\text{off}}$ in the first cycle ($0 \le t \le T$) at which the LED switches on and off. Part (b) asks for the LED current $i_{\text{LED}}(t)$ while conducting and its peak value $I_{\text{peak}}$.

For part (a), the peak amplitude and period are

$$
\begin{aligned}
V_{\text{peak}} &= \sqrt{2}\,V_{\text{rms}} = \sqrt{2} \times 5.0\ \text{V} = 7.071\ \text{V} = 7.07\ \text{V}\quad(3\text{ s.f.}) \\[4pt]
T &= \frac{1}{f} = \frac{1}{50\ \text{Hz}} = 0.020\ \text{s} = 20.0\ \text{ms}
\end{aligned}
$$

so $v_{\text{in}}(t) = 5\sqrt{2}\,\sin(2\pi \cdot 50\,t)\ \text{V}$. In the constant-voltage-drop model ([[FEEG1004 B1 - Semiconductors and Diodes]]), the LED conducts only while $v_{\text{in}}(t) > V_F = 2.8\ \text{V}$. Setting $v_{\text{in}}(t_{\text{on}}) = 2.8\ \text{V}$ on the rising quarter-cycle:

$$
\begin{aligned}
5\sqrt{2}\,\sin(100\pi t_{\text{on}}) &= 2.8\ \text{V} \\[6pt]
\sin(100\pi t_{\text{on}}) &= \frac{2.8}{5\sqrt{2}} = 0.39598 \\[6pt]
t_{\text{on}} &= \frac{1}{100\pi} \arcsin\!\left(\frac{2.8}{5\sqrt{2}}\right) = \frac{0.40707\ \text{rad}}{314.16\ \text{rad}\,\text{s}^{-1}} = 1.296 \times 10^{-3}\ \text{s} = 1.30\ \text{ms}\quad(3\text{ s.f.})
\end{aligned}
$$

By the symmetry of the positive half-cycle about $T/4$, the LED switches off on the falling slope at

$$
t_{\text{off}} = \frac{T}{2} - t_{\text{on}} = 10.0\ \text{ms} - 1.296\ \text{ms} = 8.704\ \text{ms} = 8.70\ \text{ms}\quad(3\text{ s.f.})
$$

For the rest of the period ($8.70\ \text{ms} \le t \le 20.0\ \text{ms}$), $v_{\text{in}}(t) \le 2.8\ \text{V}$ and the LED is off.

For part (b), while the LED conducts ($1.30\ \text{ms} < t < 8.70\ \text{ms}$), KVL around the series loop gives the resistor voltage $v_R(t) = v_{\text{in}}(t) - V_F = 5\sqrt{2}\,\sin(100\pi t) - 2.8\ \text{V}$. With Ohm's law and $i_{\text{LED}} = i_R$ (KCL),

$$
i_{\text{LED}}(t) = \frac{v_R(t)}{R} = \frac{5\sqrt{2}\,\sin(100\pi t) - 2.8}{200}\ \text{A} \qquad (1.30\ \text{ms} \le t \le 8.70\ \text{ms})
$$

The current peaks at the crest $t = T/4 = 5.0\ \text{ms}$, where $\sin(100\pi t) = 1$:

$$
I_{\text{peak}} = \frac{7.071\ \text{V} - 2.8\ \text{V}}{200\ \Omega} = \frac{4.271\ \text{V}}{200\ \Omega} = 0.02136\ \text{A} = 21.4\ \text{mA}\quad(3\text{ s.f.})
$$

> [!check] KVL at turn-on and at the peak
> At $t = t_{\text{on}} = 1.296\ \text{ms}$, $v_{\text{in}} = 7.071\sin(100\pi \times 1.296 \times 10^{-3}) = 2.800\ \text{V}$, so $i_{\text{LED}} = (2.800 - 2.800)/200 = 0.00\ \text{mA}$. At $t = 5.0\ \text{ms}$, the resistor drop is $I_{\text{peak}} R = 0.021355\ \text{A} \times 200\ \Omega = 4.271\ \text{V}$, which with $V_F = 2.800\ \text{V}$ sums to $7.071\ \text{V} = V_{\text{peak}}$. The LED conducts for $\Delta t = t_{\text{off}} - t_{\text{on}} = 8.704\ \text{ms} - 1.296\ \text{ms} = 7.41\ \text{ms}$, or $37.0\%$ of each $20\ \text{ms}$ mains cycle.

## Links

- Parent: [[FEEG1004 Electronics Hub]]
- Previous: [[FEEG1004 B5 - Combinational Logic - Boolean Algebra and Karnaugh Maps]]
- Next: [[FEEG1004 C1 - Magnetic Circuits, Faraday's Law and Force on Conductors]]
- Concepts: [[D-Type Flip-Flop]] · [[Shift Registers and Binary Counters]] · [[Boolean Algebra and De Morgan's Theorems]] · [[MOSFET]]

## Sources

- J. Mills, *Diodes, Transistors, Op-amps and Digital Electronics* (`S1 Electronics Notes - Diodes Transistors Op-Amps and Digital - Mills.pdf`), Section 3.3, *Sequential Logic*, pp. 84–94: §3.3.1 cross-coupled NAND R-S flip-flop and its five-step sequence of events (pp. 84–87); §3.3.2 clocked R-S flip-flop (pp. 87–88); §3.3.3 master–slave falling-edge-triggered D flip-flop and timing diagram (pp. 88–89); §3.3.4 4-bit serial-to-parallel shift register and scrolling LED display (pp. 89–91); §3.3.5 4-bit ripple-through binary up-counter and Table 3.3.5 (pp. 91–93); §3.3.6 memory chips: SRAM, DRAM and Flash (pp. 93–94).
- `S1-W15-EL5 Digital Logic 2 Sequential - Interactive.pdf`: scope guidance (slide 3), divide-by-2 D flip-flop (slide 5), 2-bit synchronous state sequence (slide 6), and the AC-driven LED exam question (slides 7–9).
- `FEEG1004 Lecture 5a.txt` (ll. 1–190: combinational and sequential logic, state machines, cross-coupled NAND R-S latch, forbidden state, clocked R-S latch, transparent D latch and master–slave negative-edge-triggered D flip-flop); `FEEG1004 Lecture 5b.txt` (ll. 1–172: 4-bit shift register, scrolling LED array, 4-bit ripple counter, divide-by-2 frequency division, real-time clock and SRAM/DRAM/Flash memory).

## Self-study tasks

### Core

- [ ] Sketch a rising-edge-triggered D flip-flop with $\overline{Q}$ fed back to $D$, draw $C$, $D$ and $Q$ over four clock periods, and explain why $f_Q = f_{\text{in}}/2$ (W15-EL5 interactive, slide 5; Lecture 5b, ll. 48–95). → [[#Divide-by-2 toggle stage]]
- [ ] Two synchronously clocked D flip-flops have $D_1 = Q_0$ and $D_0 = \overline{Q}_1$, starting from $Q_1 Q_0 = 00$. Construct the state table and verify the sequence $00, 01, 11, 10, 00, \dots$ (option B) (W15-EL5 interactive, slide 6). → [[#Two-bit synchronous state machine]]
- [ ] Trace the 4-bit rising-edge-triggered ripple counter ($D_i = \overline{Q}_i$, next-stage clock $C_{i+1} = \overline{Q}_i$) from $0000_2$ through 8 clock pulses, and explain why the count must be read as $DCBA_2$ (Mills §3.3.5, Table 3.3.5, pp. 92–93; Lecture 5b, ll. 64–128). → [[#Four-bit ripple-through binary up-counter]]
- [ ] For a $5\ \text{V}_{\text{rms}}$, $50\ \text{Hz}$ sine wave driving an LED ($V_F = 2.8\ \text{V}$) through $200\ \Omega$, show that the LED switches on at $t = 1.30\ \text{ms}$ and off at $t = 8.70\ \text{ms}$ in the first cycle, and find its peak current (W15-EL5 interactive, slides 7–9). → [[#LED driven by a sinusoidal source]]

### Further practice

- [ ] Trace the parallel outputs $Q_A, Q_B, Q_C, Q_D$ of the 4-bit shift register of Figure 3.3.4.1 over five falling edges for the serial input $1, 0, 1, 1, 0$, starting from $0000$ (suggested, not lecturer-set). → [[#Four-bit serial-in, parallel-out shift register]]
- [ ] In the ripple counter of Figure 3.3.5, drive each stage's clock $C_{i+1}$ from $Q_i$ instead of $\overline{Q}_i$, keeping $D_i = \overline{Q}_i$. Trace the first four rising edges from $DCBA_2 = 0000_2$ and show that the counter counts down ($0000_2 \to 1111_2 \to 1110_2 \to 1101_2 \dots$) (suggested, not lecturer-set). → [[#Four-bit ripple-through binary up-counter]]

## Transcript and slide slips

### Self-corrected slip on the ripple-counter feedback connection

> [!warning] "D input is connected to its Q output"
> Where: [[#Four-bit ripple-through binary up-counter]]
> In `FEEG1004 Lecture 5b.txt` (l. 35), the 4-bit ripple counter is first described with "the D input of each flip-flop is connected to its Q output", corrected on ll. 36–37 to "Its NOT Q output is fed back to D on each of the flip-flops". With $D$ connected to $Q$, the flip-flop would re-latch its existing state and never toggle; $D$ must connect to $\overline{Q}$, crossing the $Q$ wire without a junction dot (Mills p. 93).

### Level-triggered phrasing for the ripple-counter clock

> [!warning] "Clocked when the clock is high" for a rising-edge-triggered flip-flop
> Where: [[#Four-bit ripple-through binary up-counter]]
> In `FEEG1004 Lecture 5b.txt` (ll. 40–43), contrasting the unbarred clock label $C$ on the ripple counter with the barred $\overline{C}$ on the shift register, the transcript reads "it's being clocked when the clock is high, there's no bar above clock, so it's being clocked when we get a logic one on the clock input... in other words D gets copied to Q when we go from logic zero to logic one". The triangle ($\triangleright$) at input $C$ marks an **edge-triggered** flip-flop: $D$ is copied to $Q$ only at the instant of the $0 \to 1$ rising edge, not continuously while the clock stays at 1.
