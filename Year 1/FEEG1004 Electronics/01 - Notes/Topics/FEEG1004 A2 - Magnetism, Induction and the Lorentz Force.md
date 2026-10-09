---
title: "FEEG1004 A2 - Magnetism, Induction and the Lorentz Force"
module: "FEEG1004 Electronics"
type: topic
stream: "Part A: Electrical Fundamentals and DC Circuits"
order: 2
tags: [feeg1004, fundamentals, magnetism, flux, faraday, lenz, lorentz, maxwell]
aliases: ["Lecture 2a-2b", "Magnetism and induction", "Faraday's law", "Electromagnetism"]
date: 2026-09-27
status: complete
parent: ["[[FEEG1004 Electronics Hub]]"]
prerequisites: ["[[FEEG1004 A1 - Electrostatics, Potential and Current]]"]
next_topics: ["[[FEEG1004 A3 - DC Circuit Laws - Ohm, KCL, KVL and Dividers]]"]
key_concepts: ["[[Magnetic Flux and Flux Density]]", "[[Faraday's Law and Lenz's Law]]", "[[Lorentz Force]]"]
tutorial_sheets: ["[[FEEG1004 Tutorial 1 - Electrostatics, Magnetism and Resistors Solutions]]", "[[FEEG1004 Tutorial 5 - Faraday, Generators and Transformers Solutions]]"]
sources: ["02 - Sources/S1 Fundamentals/S1-W03-2ab Magnetism and Induction - Recorded.pdf", "02 - Sources/S1 Fundamentals/S1-W03 Magnetism - Interactive.pdf"]
---

# FEEG1004 A2 - Magnetism, Induction and the Lorentz Force

> [!abstract] Summary
> Two effects underpin every inductor, transformer, motor, generator, relay and inductive sensor in this module:
> - **Induction**, from **Faraday's law** $\mathcal E = -N\,d\Phi/dt$. A *changing* flux through a coil produces an EMF. The minus sign (**Lenz**) says the induced current opposes the change.
> - **Force**, from the **Lorentz law** $\mathbf F = q(\mathbf E + \mathbf v\times\mathbf B)$. For a current-carrying wire this gives $F = BIL$.
>
> Currents create magnetic fields (right-hand grip rule, Ampère). Maxwell's equations tie it all together.

## Key Concepts
- [[Magnetic Flux and Flux Density]] · [[Faraday's Law and Lenz's Law]] · [[Lorentz Force]]

---

## 1. Magnetic field and flux (L2a)
- **Flux density** $B$ [T] is shown by the density of field lines. Lines run from **N to S** outside a magnet and form **closed loops**: there are no monopoles.
- **Flux** through a coil is the integral of the **normal** component of $B$ over the coil area:

$$
\Phi = \int\mathbf B\cdot d\mathbf A\quad[\mathrm{Wb} = \mathrm{T\,m^2} = \mathrm{V\,s}];\qquad \Phi = BA\cos\theta\ \text{(uniform field)}
$$

- Drawing conventions: **×** means into the page (the tail of a cross-head screw); **•** means out of the page (the point).

## 2. Faraday's law and Lenz's law

$$
\mathcal E = -N\frac{d\Phi}{dt}
$$

- The EMF around an $N$-turn coil is $N$ times the rate of change of flux through it.
- **Lenz**: the induced current creates a field that **opposes the change**. It is energy conservation: if it aided the change you would get power for free.
- Faraday's law is **not** electrostatics. The induced field circulates, so the "potential landscape" picture of [[FEEG1004 A1 - Electrostatics, Potential and Current]] does not apply around the loop.
- **Graphical rule**: the EMF is minus the **gradient** of the flux–time graph. It is zero where the flux is at a turning point and largest where the flux changes fastest.

![[ee_a2_magnet_through_coil.png|760]]

> [!example] Tutorial 5 Q1: bar magnet falling through a coil at constant speed
> - The flux rises as the leading pole enters, is **maximum** with the magnet centred (point **B**), then falls.
> - The EMF is two opposite-sign pulses. It is maximum at **A**, where the flux changes fastest as a pole passes the coil, and **zero at B**.

> [!example] Tutorial 1 Q5: rotating coil
> - A 10-turn, 0.1 m² coil spins at 20 Hz in 2 T, so $\theta = 40\pi t$.
> - $\Phi = BA\cos\theta = 0.2\cos40\pi t$ Wb per turn.
> - $\mathcal E = -N\,d\Phi/dt = 80\pi\sin40\pi t$ ≈ **251 sin(40πt) V**. The sign depends on the coil's positive direction.
>
> ![[ee_t1_q5_rotating_coil.png|700]]

This is exactly the AC generator of [[FEEG1004 C2 - AC Synchronous Generators and Three-Phase Systems]].

## 3. The Lorentz force (L2b)

$$
\mathbf F = q(\mathbf E + \mathbf v\times\mathbf B)
$$

- The electric part is Coulomb's law. The magnetic part is **perpendicular** to both $\mathbf v$ and $\mathbf B$, so it does no work and only turns the charge.
- **Direction**: Fleming's **left-hand** rule for the force on a *current* or positive charge (First finger Field, seCond finger Current, thuMb Motion). Reverse it for negative charges.
- **Force on a wire** (the revision exercise): for charge $q$ moving at $v$ along a length $L$, $qv = IL$, so

$$
F = BIL\qquad(\mathbf B\perp\mathbf L)
$$

> [!example] Lorentz-force checks (W3 interactive)
> - Field to the right, positive charge moving left: $\mathbf v\parallel\mathbf B$, so the **force is zero**.
> - Negative charge moving up in a field to the right: the force is **left** (as the slide states).
> - **Four tracks in a field out of the page** (answer B): track 1 curves the "negative" way, track 2 is straight (neutral), tracks 3 and 4 are positive.
> - **Tutorial 5 Q3**: 1 kA through 10 m of cable across the Earth's $10^{-4}$ T field gives $F = BIL$ = **1 N**. The force is vertical: up for current flowing east (E × N = up), down for west.

## 4. Fields from currents and forces between wires
- **Right-hand grip rule** (Ampère): thumb along the current, fingers curl with $\mathbf B$.
- **Two wires with opposite currents repel**; parallel currents attract. Use the grip rule for the field of wire 1 at wire 2, then the left-hand rule for the force on wire 2.

**Maxwell's equations** (for context only, not examined):

| Law | Physics |
|---|---|
| Gauss | static charges create $\mathbf E$ |
| Gauss for magnetism | $\mathbf B$ lines close: no monopoles |
| Faraday | a changing $\mathbf B$ creates a circulating $\mathbf E$ |
| Ampère–Maxwell | currents (and a changing $\mathbf E$) create $\mathbf B$ |
| + Lorentz force | the forces that result |

> [!example] The falling conducting ring (MIT TEAL animation, W3)
> - A ring falls onto a magnet. The motion of its electrons through $\mathbf B$ (Lorentz) drives a circulating current. Equivalently, the changing flux induces an EMF (Faraday).
> - That current's field opposes the approach (Lenz), so the ring **bounces**. Resistance dissipates energy, so the bounces decay.
> - Energy moves between gravitational, kinetic and magnetic stores and is lost as heat.
> - The animation contains a deliberate error: with yellow electrons, the drawn field does not follow the grip rule.

## Conventions summary
- $\mathbf E$ points from + to −. Voltage arrows point to the more positive end.
- $\mathbf B$ points N → S outside a magnet.
- Conventional current flows opposite to electron flow.
- Current → field: right-hand grip rule. Force on a current: left-hand rule. Induced EMF (generator): right-hand rule.

## Year 2 bridge
- $\mathcal E = -d\Phi/dt$ and Ampère's law are **Stokes' theorem** statements of $\nabla\times\mathbf E = -\partial\mathbf B/\partial t$ ([[Stokes' Theorem]], [[Divergence, Curl and the Laplacian]]).
- **Magnetorquers** on spacecraft are current loops in the Earth's field: torque $= \mathbf m\times\mathbf B$ with $\mathbf m = NI\mathbf A$, the rotational form of $F = BIL$ ([[Attitude Sensors and Torquers]], [[SESA2024 06 - Attitude Control]]). **Magnetometers** sense $\mathbf B$ for attitude determination.
- **Reaction wheels** are brushless DC motors ([[Reaction Wheels and Momentum Dumping]], [[FEEG1004 C5 - DC Motors - Torque, Back EMF and Efficiency]]).
- **Inductive sensors** (the LVDT) rely on Faraday's law ([[Linear Variable Differential Transformer]], [[SESA2027 C1 - Sensing Systems, Sensor Principles and Sensor Fusion]]).

## Links
- Previous: [[FEEG1004 A1 - Electrostatics, Potential and Current]] · Next: [[FEEG1004 A3 - DC Circuit Laws - Ohm, KCL, KVL and Dividers]]
- Machines built on this: [[FEEG1004 C1 - Magnetic Circuits, Faraday's Law and Force on Conductors]]
- Worked problems: [[FEEG1004 Tutorial 1 - Electrostatics, Magnetism and Resistors Solutions]] (Q5) · [[FEEG1004 Tutorial 5 - Faraday, Generators and Transformers Solutions]] (Q1, Q3)

## Sources
- Recorded lecture 2a (magnetism and induction) and 2b (other electromagnetic effects), P. Glynne-Jones; Week 3 interactive session.
