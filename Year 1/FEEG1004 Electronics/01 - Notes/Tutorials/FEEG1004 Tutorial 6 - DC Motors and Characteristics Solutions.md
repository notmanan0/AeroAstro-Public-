---
title: "FEEG1004 Tutorial 6 - DC Motors and Characteristics Solutions"
module: "FEEG1004 Electronics"
type: tutorial
stream: "Part C: Electric Machines"
tags: [feeg1004, tutorial-solutions, dc-motor, back-emf, efficiency, torque, gearbox]
sheet: "Problems on Electric Machines 2"
theory_notes: ["[[FEEG1004 C4 - DC Generators and the Commutator]]", "[[FEEG1004 C5 - DC Motors - Torque, Back EMF and Efficiency]]", "[[FEEG1004 C6 - DC Motor Characteristics and Speed Control]]"]
key_concepts: ["[[Back EMF and Torque Constants]]", "[[Electric and Magnetic Loading]]", "[[Torque-Speed Characteristics of DC Motors]]"]
status: complete
sources: ["02 - Sources/Tutorial Sheets/Tutorial Sheet 06 - Electric Machines 2 - DC Motors & Characteristics.pdf"]
---

# FEEG1004 Tutorial 6 - DC Motors and Characteristics Solutions

> [!abstract] Sheet Info
> One small PM DC motor is characterised step by step: $K_E$ from an open-circuit test, $R_a$ and losses from a no-load test, then efficiency on load. Then come the torque–size derivation, the gearbox argument and the characteristic curves.
> - No answers are printed. The numerical work was **verified numerically**.

## Theory Links
- [[FEEG1004 C4 - DC Generators and the Commutator]] · [[FEEG1004 C5 - DC Motors - Torque, Back EMF and Efficiency]] · [[FEEG1004 C6 - DC Motor Characteristics and Speed Control]] · [[Back EMF and Torque Constants]]

---

## Q1: Back-EMF constant from an open-circuit test
- On open circuit no current flows, so there is no $iR_a$ drop: the terminal voltage **is** the EMF.
- $\omega = 1000\times2\pi/60$ = 104.7 rad/s:
$$K_E = \frac{E}{\omega} = \frac{10}{104.7} = 0.0955\ \mathrm{V\,s/rad}\ (= K_T = 0.0955\ \mathrm{N\,m/A})$$

## Q2: Running light as a motor at 1000 rpm: 10.2 V, 1 A
- **Why the voltage is higher**:
  - As a **motor**, the supply must provide the back EMF *plus* the armature drop: $V = E + iR_a$.
  - The speed is unchanged, so $E$ is still 10 V (it depends only on ω). The extra 0.2 V is $iR_a$.
  - Contrast the generator, where $V = E - iR_a$.
- **Armature resistance**: $R_a = 0.2/1$ = **0.2 Ω**.
- **No-load losses**:
  - $P_{in} = 10.2\times1$ = 10.2 W, of which $i^2R_a$ = 0.2 W is copper loss.
  - The electromagnetic power $Ei$ = **10 W** produces no useful output, so it all goes into **friction, windage and core losses** at 1000 rpm.

## Q3: Driving a pump at 1000 rpm with 5 A
- The speed is the same, so $E$ = 10 V. $V = E + iR_a = 10 + 5(0.2)$ = **11 V**.
- Power flow:
  - $P_{in} = 11\times5$ = 55 W;
  - copper loss $5^2\times0.2$ = 5 W;
  - $P_{em} = Ei$ = 50 W;
  - minus the 10 W rotational loss (unchanged at the same speed) leaves $P_{out}$ = 40 W.
- $\eta = 40/55$ = **72.7 %**. The shaft torque is $(50 - 10)/104.7$ = 0.38 N m, while the electromagnetic torque is $K_Ti$ = 0.48 N m.

## Q4: Show $T = \tfrac{1}{2}BZi_cDL = 2BAV_R$
- Each of the $Z$ conductors carries $i_c$ in a field $B$ over length $L$: $F_c = Bi_cL$.
- At radius $D/2$ this gives torque $T_c = Bi_cLD/2$. All conductors under the poles add (the commutator keeps them in step):

$$
T = ZBi_cL\frac{D}{2}
$$

- Introduce the **electric loading** $A = Zi_c/(\pi D)$ (current per metre of rotor circumference) and the **rotor volume** $V_R = \pi D^2L/4$:

$$
T = ZBi_cL\frac{D}{2} = B\,(\pi DA)\,L\frac{D}{2} = 2B\,A\left(\frac{\pi D^2L}{4}\right) = 2BAV_R\ ✔
$$

## Q5: Why use a step-down gearbox with a slow load?
- $B$ (steel saturation) and $A$ (cooling) are roughly fixed across machines, so **torque ∝ rotor volume**.
- A slow load needs high torque at low speed. Driving it directly would need a **large, heavy, expensive** motor.
- With $P = T\omega$, a motor running $n$ times faster needs only $1/n$ of the torque, hence about $1/n$ of the volume. The gearbox multiplies torque by $n$ (minus gear losses).
- Example: 1 kW at 10 rad/s needs 100 N m directly, or 10 N m from a motor at 100 rad/s via 10:1 gearing.

## Q6: Torque–speed characteristics, shunt vs series
- **Shunt** (field across the supply, so $\Phi$ is constant):
  - $\omega = V/K - (R_a/K^2)T$ is a straight line with a slight droop: nearly **constant speed**.
  - It has a finite no-load speed $V/K$. Suits fans, pumps and machine tools.
- **Series** (field carries the armature current):
  - $\Phi\propto i$, so $T\propto i^2$; $E\propto\Phi\omega\propto i\omega$ gives $\omega\propto1/\sqrt T$ (neglecting resistance).
  - Very high **starting torque**, but the speed rises steeply as the load falls and **runs away** at no load.
  - Suits traction and engine starters, loads that are never removed.

![[ee_c6_torque_speed_types.png|760]]

## Sources
- FEEG1004 Problems on Electric Machines 2; derived and verified numerically.
