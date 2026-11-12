---
title: "FEEG1002 Statics 1 Tutorial 1 - Forces, Equilibrium, Stress and Strain Solutions"
module: "FEEG1002 Mechanics, Materials and Structures"
type: tutorial
stream: "Part A: Statics 1"
tags: [feeg1002, tutorial-solutions, statics, equilibrium, stress, strain]
sheet: "Statics-1 Tutorial problem sheet 1"
theory_notes: ["[[FEEG1002 A1 - Forces, Equilibrium, Stress and Strain]]"]
key_concepts: ["[[Free Body Diagram and Equilibrium]]", "[[Stress, Strain and Young's Modulus]]"]
status: complete
sources: ["02 - Sources/Statics 1/Tutorials/Tutorial Sheet 01 - Forces and Equilibrium, Stress and Strain.pdf", "02 - Sources/Statics 1/Tutorials/Tutorial Sheet 01 - Forces and Equilibrium, Stress and Strain - Solutions.pdf"]
---

# FEEG1002 Statics 1 Tutorial 1 - Forces, Equilibrium, Stress and Strain Solutions

> [!abstract] Sheet info
> Three core questions (crane tipping, hinge design, bolt preload) and three additional problems (bascule bridge, hole punch, a bar loaded through a collar). Every printed answer is reproduced, with $g=9.81$ m/s², and every number was recomputed in Python. The methods follow the official solutions; where a note adds something they do not contain, it says so.

Theory: [[FEEG1002 A1 - Forces, Equilibrium, Stress and Strain]] · [[Free Body Diagram and Equilibrium]] · [[Stress, Strain and Young's Modulus]]

---

## Q1 - Crane with a suspended box

Taught in: [[FEEG1002 A1 - Forces, Equilibrium, Stress and Strain#Worked example - crane tipping|A1, crane tipping]] · [[FEEG1002 A1 - Forces, Equilibrium, Stress and Strain#Example: the seesaw, and choosing the moment point|A1, choosing the moment point]]

The crane has mass 5000 kg. The box hangs 4 m in front of the front axle A, the crane's centre of gravity is 3 m behind A, and the rear axle B is 2 m further back, 5 m behind A. The ground reactions $F_A$ and $F_B$ are vertical.

![[s1_crane_tipping_fbd.png|900]]

### (a) Maximum box mass

As the box gets heavier the rear axle is unloaded. The crane tips when the rear axle lifts off, $F_B=0$, and it then pivots about A. Taking moments about A removes the unknown $F_A$, whose line of action passes through A:

$$
4F_{g,box}+0\cdot F_A-3F_{g,crane}+5F_B=0
$$

With $F_B=0$:

$$
m_{box}=\tfrac34m_{crane}=\tfrac34(5000)=3750\ \mathrm{kg}
$$

### (b) Axle loads with a 1000 kg box

The same moment equation gives the rear axle load:

$$
F_B=\frac{3(5000)g-4(1000)g}{5}=21.6\ \mathrm{kN}
$$

and vertical equilibrium the front axle load:

$$
F_A=(1000+5000)g-F_B=37.3\ \mathrm{kN}
$$

Check: $37.3+21.6=58.9$ kN $=6000g$.

## Q2 - Pinned hinge

Taught in: [[FEEG1002 A1 - Forces, Equilibrium, Stress and Strain#Worked example - equally strong rod and pin|A1, rod and pin]] · [[FEEG1002 A1 - Forces, Equilibrium, Stress and Strain#Shear stress|A1, shear stress]]

Two identical round rods are joined by a pin through a fork. The working load is $F=5000$ N; the allowable tensile stress is 400 MPa and the allowable shear stress 240 MPa.

### (a) Diameters for equal strength

The rod is in tension and needs area $A=F/\sigma$:

$$
D_{rod}=\sqrt{\frac{4F}{\pi\sigma}}=\sqrt{\frac{4(5000)}{\pi(400\times10^6)}}=4.0\ \mathrm{mm}
$$

The pin is in shear. To pull out, the middle of the pin must shear across two planes, one each side of the eye, each carrying $F/2=2500$ N:

$$
D_{pin}=\sqrt{\frac{4(2500)}{\pi(240\times10^6)}}=3.6\ \mathrm{mm}
$$

### (b) Other factors

The official solution lists stress concentrations around the pin holes and at the transition from the round to the square cross-section, and safety factors so that the hinge does not fail under its normal working load. Beyond the official answer, the bearing (crushing) stress between pin and hole, tear-out of the eye, and fatigue if the load cycles ([[FEEG1002 C9 - Fatigue, Creep and Corrosion]]) also matter in practice.

## Q3 - Bolt clamping force

Taught in: [[FEEG1002 A1 - Forces, Equilibrium, Stress and Strain#Worked example - bolt clamping force|A1, bolt clamping force]] · [[FEEG1002 A1 - Forces, Equilibrium, Stress and Strain#A bar is a spring|A1, a bar is a spring]]

A steel bolt of diameter 6 mm and length 350 mm, $E=209$ GPa, clamps two plates assumed perfectly rigid. The nut advances 0.5 mm per turn.

### (a) Turns for a 4000 N clamping force

| Step | Result |
|---|---|
| $\sigma=F/(\pi D^2/4)$ | 141.5 MPa |
| $\varepsilon=\sigma/E$ | $6.77\times10^{-4}$ |
| $\Delta L=\varepsilon L$ | 0.237 mm |
| turns $=\Delta L/\text{pitch}$ | 0.47, about half a turn |

### (b) Real plates deform

The plates are compressed as the nut is tightened, so part of the nut's travel goes into squashing the plates. For the same number of turns the bolt stretches less and the clamping force is smaller than 4000 N; the nut has to be turned further. In spring terms (not in the official solution), bolt and plates act in series, with combined stiffness $(1/k_b+1/k_p)^{-1}$.

---

## Extra Q1 - Bascule bridge

Taught in: [[FEEG1002 A1 - Forces, Equilibrium, Stress and Strain#Free body diagrams|A1, free body diagrams]] · [[FEEG1002 A1 - Forces, Equilibrium, Stress and Strain#Moment of a force|A1, moment of a force]]

**(a) Free body diagrams.** The cables stay vertical, so they transmit purely vertical forces and the directions of the forces on each part do not change as the bridge opens. If the upper arms were shorter, the cables would be inclined and horizontal reactions would appear at the pivots.

**(b) Counterweight for a 50 t deck**, with the bridge perfectly balanced and the upper arms' weight ignored. The deck's centre of gravity is 5 m from its pivot and the cable acts 10 m from it, so moments about the deck pivot give a cable tension of $W_{deck}/2$. On the upper arm the cable pulls 10 m from the pivot and the counterweight hangs 5 m from it, so the counterweight must be twice the cable tension:

$$
W_{cw}=2\times\frac{W_{deck}}{2}=W_{deck}
$$

The counterweight is 50 t, equal to the deck, because the two lever-arm ratios (5/10 and 10/5) cancel.

## Extra Q2 - Hole punch

Taught in: [[FEEG1002 A1 - Forces, Equilibrium, Stress and Strain#Shear stress|A1, shear stress]]

A punch of diameter $D=12$ mm makes a hole in a sheet $H=2$ mm thick; the allowable shear stress is 200 MPa. The slug is sheared out around its cylindrical surface, of area $\pi DH$:

$$
F=\tau_{max}\pi DH=(200\times10^6)\pi(0.012)(0.002)=15.08\ \mathrm{kN}
$$

The 300 MPa normal-stress limit is not used, because the failure is in shear.

## Extra Q3 - Bar loaded through a collar

Taught in: [[FEEG1002 A1 - Forces, Equilibrium, Stress and Strain#A bar is a spring|A1, a bar is a spring]]

A square bar of side $W=6$ mm and length $2L$, with $L=70$ mm, is fixed at both ends and loaded at mid-length through a collar by $F=200$ N, which moves the collar $D=3$ mm. The upper half is stretched and the lower half compressed, both by $D$, so the two halves act as springs in parallel:

$$
F=2\frac{EA}{L}D
$$

$$
E=\frac{FL}{2W^2D}=\frac{(200)(0.07)}{2(0.006)^2(0.003)}=64.81\ \mathrm{MPa}
$$

A very compliant, rubber-like material.

## Sources

- Tutorial Sheet 01 and its official solutions: Q1 pp. 1–2, Q2 p. 3, Q3 p. 4, additional Q1 pp. 5–6, additional Q2 p. 7, additional Q3 p. 8.
- Every value recomputed in Python and checked against the printed answers.
