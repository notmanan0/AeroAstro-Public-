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

> [!abstract] Sheet Info
> Three core questions (crane tipping, hinge design, bolt preload) and three extra questions (bascule bridge, hole punch, a bar in tension and compression). All printed answers are reproduced ✔ and were checked numerically with $g = 9.81$ m/s².

## Theory Links
- [[FEEG1002 A1 - Forces, Equilibrium, Stress and Strain]] · [[Free Body Diagram and Equilibrium]] · [[Stress, Strain and Young's Modulus]]

---

## Q1: Crane with a suspended box ($m_{crane} = 5000$ kg)
Geometry: the box hangs 4 m in front of the front axle A, the crane's centre of gravity is 3 m behind A, and the rear axle B is 5 m behind A.

![[s1_crane_tipping_fbd.png|820]]

### (a) Maximum box mass
As the box gets heavier, the rear-axle load $F_B$ falls. **Tipping starts when $F_B = 0$**, and the crane then pivots about A. Take moments about A so that $F_A$ drops out:

$$
\sum M_A = 0:\quad 4F_{g,box} + 0\cdot F_A - 3F_{g,crane} + 5F_B = 0
$$

With $F_B = 0$: $m_{box} = \tfrac34 m_{crane} = \mathbf{3750}$ **kg** ✔

### (b) Axle loads with $m_{box} = 1000$ kg
- Moments about A: $F_B = \dfrac{3(5000)g - 4(1000)g}{5} = \mathbf{21.6}$ **kN** (rear) ✔
- Vertical equilibrium: $F_A = (1000 + 5000)g - F_B = \mathbf{37.3}$ **kN** (front) ✔

Check: $37.3 + 21.6 = 58.9$ kN $= 6000g$ ✔

---

## Q2: Pinned hinge, $F = 5000$ N, $\sigma_{allow} = 400$ MPa, $\tau_{allow} = 240$ MPa
### (a) Equal strength
- **Rod** (tension): $A = F/\sigma$, so $D_{rod} = \sqrt{\dfrac{4F}{\pi\sigma}} = \sqrt{\dfrac{4(5000)}{\pi(400\times10^6)}} = \mathbf{4.0}$ **mm** ✔
- **Pin** (double shear): to pull out, the pin must shear through **two** planes, each carrying $F/2 = 2500$ N. So $D_{pin} = \sqrt{\dfrac{4(2500)}{\pi(240\times10^6)}} = \mathbf{3.6}$ **mm** ✔

### (b) Other factors
- Stress concentrations at the pin holes ($K_T\approx3$) and at the round-to-square transition.
- A safety factor on the working load, since $\sigma_{allow}$ here is the failure stress.
- Bearing (crushing) stress between pin and hole, $F/(Dt)$.
- Tear-out of the eye, and fatigue if the load cycles ([[FEEG1002 C9 - Fatigue, Creep and Corrosion]]).

---

## Q3: Bolt preload, $D = 6$ mm, $L = 350$ mm, $E = 209$ GPa, pitch 0.5 mm
### (a) Turns for a 4000 N clamp (rigid plates)

| Step | Result |
|---|---|
| $\sigma = F/(\pi D^2/4)$ | $141.5$ MPa |
| $\varepsilon = \sigma/E$ | $6.77\times10^{-4}$ |
| $\Delta L = \varepsilon L$ | $0.237$ mm |
| turns $= \Delta L/p$ | $0.47\approx$ **½ turn** ✔ |

### (b) Real plates deform
The plates compress, so for the same nut rotation the bolt stretches **less** and the clamp force is **smaller**. The nut must be turned further. Bolt and plates act as springs in series, and the effective stiffness is $(1/k_b + 1/k_p)^{-1}$.

---

## Extra Q1: Bascule bridge (FBDs and counterweight)
- **FBDs**: vertical cables transmit purely vertical forces, so the force directions do not change as the bridge opens. Shorter upper arms would angle the cables and introduce horizontal pivot reactions.
- **Counterweight for a 50 t deck**, perfectly balanced:
  - the deck's centre of gravity is 5 m from its pivot and the cable acts at 10 m, so the cable tension is $W_{deck}/2$;
  - on the upper arm the cable pulls at 10 m and the counterweight hangs at 5 m, so the counterweight is $2\times W_{deck}/2$.
  - Counterweight = **50 t**. The whole mechanism is a seesaw.

## Extra Q2: Hole punch, $D = 12$ mm, $H = 2$ mm, $\tau_{max} = 200$ MPa
The slug is sheared out around its cylindrical surface, of area $A = \pi DH$:

$$
F = \tau_{max}\,\pi DH = 200\times10^6\,\pi(0.012)(0.002) = \mathbf{15.08}\ \text{kN}\ ✔
$$

The 300 MPa normal-stress limit is irrelevant here, because the failure mode is shear.

## Extra Q3: Square bar fixed at both ends, collar load at mid-length
The upper half ($L = 70$ mm) is stretched and the lower half compressed, both by $D = 3$ mm. The two halves act as **two springs in parallel**:

$$
F = 2\frac{EA}{L}D\;\Rightarrow\; E = \frac{FL}{2W^2D} = \frac{200(0.07)}{2(0.006)^2(0.003)} = \mathbf{64.81}\ \text{MPa}\ ✔
$$

This is a very compliant, polymer-like material (compare $E\approx2$–$4$ GPa for rigid plastics). See [[FEEG1002 C10 - Polymers - Structure and Mechanics]].

## Sources
- Source sheet and official solutions: Statics-1 Tutorial problem sheet 1
- Verification: numerical check script run while building these notes (all values agree to 3 s.f.)
