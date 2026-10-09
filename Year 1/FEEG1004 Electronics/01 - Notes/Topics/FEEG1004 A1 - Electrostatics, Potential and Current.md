---
title: "FEEG1004 A1 - Electrostatics, Potential and Current"
module: "FEEG1004 Electronics"
type: topic
stream: "Part A: Electrical Fundamentals and DC Circuits"
order: 1
tags: [feeg1004, fundamentals, electrostatics, electric-field, potential, current, power]
aliases: ["Lecture 1a-1b", "Electrostatics", "Electric current", "Voltage and electric field"]
date: 2026-09-27
status: complete
parent: ["[[FEEG1004 Electronics Hub]]"]
prerequisites: []
next_topics: ["[[FEEG1004 A2 - Magnetism, Induction and the Lorentz Force]]"]
key_concepts: ["[[Coulomb's Law and Electric Field]]", "[[Electric Potential and Voltage]]", "[[Electric Current and Electrical Power]]"]
tutorial_sheets: ["[[FEEG1004 Tutorial 1 - Electrostatics, Magnetism and Resistors Solutions]]"]
sources: ["02 - Sources/S1 Fundamentals/S1-W02-1ab Electrostatics and Electric Current - Recorded.pdf", "02 - Sources/S1 Fundamentals/S1-W02 Electrostatics - Interactive.pdf", "02 - Sources/S1 Fundamentals/S1 Equations Sheet.pdf"]
---

# FEEG1004 A1 - Electrostatics, Potential and Current

> [!abstract] Summary
> Charge is the source of everything in this module.
> - Charges exert forces on each other (**Coulomb**). A charge distribution fills space with an **electric field** $\mathbf E = \mathbf F/q$, the force per unit positive test charge.
> - The **potential difference** (voltage) between two points is the energy per coulomb to move charge between them: $V = W/q$ [J/C = V]. The field is the slope of the potential, $E_x = -dV/dx$, so in a uniform field $V = EL$.
> - A **current** is a flow of charge, $I = dQ/dt$. A current $I$ falling through a potential difference $V$ converts power $P = VI$.
>
> These three ideas ($\mathbf E$, $V$, $I$) are all you need to start circuit analysis in [[FEEG1004 A3 - DC Circuit Laws - Ohm, KCL, KVL and Dividers]].

## Key Concepts
- [[Coulomb's Law and Electric Field]] · [[Electric Potential and Voltage]] · [[Electric Current and Electrical Power]]

---

## 1. Electric charge (L1a)
- Charges come in two signs; **like charges repel, unlike attract**.
- Charge is **conserved** and **quantised** in units of $e = 1.602\times10^{-19}$ C, so 1 C is about $6.24\times10^{18}$ electrons.
- **Triboelectric charging**: rubbing two materials moves electrons to the more electronegative one ("static"; the Greek *ēlektron* is amber). This matters to engineers because static discharge destroys electronics, ignites fuel vapour (aircraft refuelling bonds the hose to the airframe for this reason) and attracts dust.
- **Induced charge**: a charge brought near a neutral insulator polarises it. The near side acquires the opposite sign, so the net force is **always attractive**, whatever the sign of the inducing charge.

## 2. Coulomb's law and the electric field
$$
F = \frac{1}{4\pi\varepsilon_0}\frac{q_1q_2}{r^2},\qquad \varepsilon_0 = 8.85\times10^{-12}\ \mathrm{F/m},\qquad \mathbf E = \frac{\mathbf F}{q}\ \ [\mathrm{N/C} = \mathrm{V/m}]
$$

- Field lines show the force on a **positive** test charge. They point away from $+$ and towards $-$ charges; their density shows the field strength.
- **Superposition**: the field of many charges is the **vector sum** of the individual fields. Resolve into components, add, then recombine. The interactive example with 5 µC and 8 µC contributions at 3 m gives $E = 9\times10^9\sqrt{(5\times10^{-6}/9)^2 + (8\times10^{-6}/9)^2}$ = **9.4 kN/C**.

![[ee_a1_two_charge_field.png|760]]

> [!example] Tutorial 1 Q1: two +1 mC charges at $x = \pm10$ cm
> - Force on either charge: $F = 8.99\times10^9(10^{-3})^2/0.2^2$ = **2.25 × 10⁵ N**, repulsive (the left charge is pushed left).
> - Between them the fields oppose: $E(x) = \dfrac{10^{-3}}{4\pi\varepsilon_0}\left[\dfrac{1}{(0.1+x)^2} - \dfrac{1}{(0.1-x)^2}\right]$ N/C, zero at the midpoint.
> - The expression is only valid for $|x| < 0.1$ m. Outside, both contributions point the same way.

## 3. Electric potential: the gravity analogy
| Gravity | Electrostatics |
|---|---|
| height $h$ in a landscape | potential $V$ in a charge distribution |
| potential difference = energy per kg [J/kg] | potential difference = energy per coulomb [J/C = V] |
| work $= mg\Delta h$ | work $= q\Delta V$ |
| force = mass × slope | force = charge × slope: $F_x = -q\,dV/dx$ |

- **Field is the slope of potential**: $E_x = -dV/dx$. In a uniform field between plates $L$ apart, $V = EL$.
- The course draws a **voltage arrow with its head at the more positive end**.

> [!example] Interactive examples (W2, W3)
> - **Plates 4 m apart at 0 V and 5 V**: $E = 5/4$ = **1.25 V/m**.
> - **Proton accelerator** (100 V across 0.1 m): $E$ = **1000 V/m**. Accelerating 0.1 C of protons releases $W = qV$ = **10 J**. If that charge flows steadily over 2 s, $I$ = **0.05 A**, left to right.
> - **Electron and proton** released from opposite plates at 1000 V: both gain the **same kinetic energy** $eV$, but the proton is ~1836× heavier, so it arrives **slower** (answer C).
> - **Unknown particle** of charge $e$ reaching $8.5\times10^4$ m/s through 750 V: $m = 2qV/v^2$ = **3.32 × 10⁻²⁶ kg** (about 20 u).

## 4. Current and conduction (L1b)
- **Conventional current** is the direction positive carriers would move. In metals the carriers are electrons, moving the **opposite** way.
- **Drift velocity is tiny.** With $n = 8.5\times10^{22}$ electrons/cm³ in copper, equating $I = 1$ A to $n e A v$:

$$
v = \frac{I}{neA}
$$

  - For a 0.1 cm **diameter** wire, $v\approx0.0094$ cm/s (34 cm per hour). The slide's "0.002 cm/s = 7.2 cm/h" corresponds to using 0.1 cm as the **radius**. Either way it is centimetres per **hour**.
  - Random thermal speed is ~10⁵ m/s. The *signal* travels near the speed of light because the field that pushes the electrons is set up at that speed, not because the electrons move fast.

## 5. Power
The energy to move charge $q$ through $V$ is $qV$, so the rate is

$$
P = V\frac{dq}{dt} = VI\ \ [\mathrm W]
$$

**The power delivered to an element is the voltage across it times the current through it.** Combined with Ohm's law this gives $P = I^2R = V^2/R$ ([[FEEG1004 A3 - DC Circuit Laws - Ohm, KCL, KVL and Dividers]]).

## Year 2 bridge
- $E = -dV/dx$ is the 1D form of $\mathbf E = -\nabla V$ ([[MATH2048 VC1 - Scalar and Vector Fields, Gradient and Directional Derivatives]]). Charge conservation and Gauss's law are divergence statements ([[MATH2048 VC5 - Volume Integrals, the Divergence Theorem and Stokes' Theorem]]).
- A potential field with a gradient force is the same structure as gravity and conservative forces ([[Conservative Forces and Potential Energy]], [[Conservative Vector Fields]]).
- **Capacitive sensors and touch screens** exploit the stored-charge picture developed here ([[FEEG1004 A4 - Capacitors]], [[Capacitive Displacement Sensor]]).
- **Spacecraft charging**: plasma in orbit charges surfaces to kV levels. Discharges are a failure mode, which is why spacecraft surfaces are bonded to a common ground ([[SESA1015 A02 - Space Environment]], [[Space Environment Hazards]]).
- **Electrostatic ion thrusters** accelerate ions through a grid potential: exit KE $= qV$, exactly the accelerator example above ([[Electric (Ion) Propulsion]], [[SESA2024 07 - Spacecraft Propulsion]]).

## Links
- Next: [[FEEG1004 A2 - Magnetism, Induction and the Lorentz Force]]
- Worked problems: [[FEEG1004 Tutorial 1 - Electrostatics, Magnetism and Resistors Solutions]]

## Sources
- Recorded lecture 1a (electrostatics) and 1b (current flow), P. Glynne-Jones; Week 2 interactive session; S1 Equations Sheet A.
