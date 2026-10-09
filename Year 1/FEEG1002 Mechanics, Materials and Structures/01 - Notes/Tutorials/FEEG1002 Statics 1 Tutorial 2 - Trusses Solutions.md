---
title: "FEEG1002 Statics 1 Tutorial 2 - Trusses Solutions"
module: "FEEG1002 Mechanics, Materials and Structures"
type: tutorial
stream: "Part A: Statics 1"
tags: [feeg1002, tutorial-solutions, statics, trusses]
sheet: "Statics-1 Tutorial problem sheet 2"
theory_notes: ["[[FEEG1002 A2 - Pin-Jointed Trusses]]"]
key_concepts: ["[[Method of Joints and Method of Sections]]", "[[Williot Displacement Diagram]]", "[[Static Determinacy]]"]
status: complete
sources: ["02 - Sources/Statics 1/Tutorials/Tutorial Sheet 02 - Trusses.pdf", "02 - Sources/Statics 1/Tutorials/Tutorial Sheet 02 - Trusses - Solutions.pdf"]
---

# FEEG1002 Statics 1 Tutorial 2 - Trusses Solutions

> [!abstract] Sheet Info
> A bike frame, a six-bay Warren truss, two extra trusses and one displacement problem. Every truss below was also solved as a full joint-equilibrium linear system (all joints at once), which checks each hand result and shows **every** bar force, not just the ones asked for. All printed answers are reproduced ✔.
> **Colour key**: blue = tension (+), red = compression (−), dashed grey = zero-force member. Line thickness ∝ |force|.

## Theory Links
- [[FEEG1002 A2 - Pin-Jointed Trusses]] · [[Method of Joints and Method of Sections]] · [[Williot Displacement Diagram]]

---

## Q1: Bike frame, rider load $F = 750$ N at B
### (a) Tension or compression? (predict first)
Ask what would happen if the bar were removed: would its end joints move apart (tension) or together (compression)?
- Prediction: **tension** in CD and AC; **compression** in BD, AB and BC.

### (b) Forces in BD and CD
- Reactions: moments about A give $F_D = F/2$, and then $F_A = F/2$ (by symmetry, since B is at mid-span).
- **Joint D** (two unknowns):
  - $\sum F_V$: $-\tfrac12F - \sin45^\circ F_{BD} = 0$, so $F_{BD} = -\tfrac{\sqrt2}{2}F = \mathbf{-530}$ **N** (compression) ✔
  - $\sum F_H$: $-F_{CD} - \cos45^\circ F_{BD} = 0$, so $F_{CD} = \tfrac12F = \mathbf{+375}$ **N** (tension) ✔

The full solution confirms the prediction: $F_{AB} = -375$, $F_{AC} = +530$ and $F_{BC} = -375$ N.

![[s1_t2_q1_bike_frame.png|640]]

---

## Q2: Warren truss, 15 kN at G and at F, span 24 m, height 3 m
Reactions: $H_A = 0$, and moments about A give $24V_E = 8(15) + 16(15)$, so $V_E = 15$ kN and $V_A = 15$ kN. Diagonal geometry: a 3–4–5 triangle, so $\sin\theta = 3/5$ and $\cos\theta = 4/5$.

- **$F_{DE}$ (joint E)**: $\sum F_V$: $15 + F_{DE}\sin\theta = 0$, so $F_{DE} = \mathbf{-25}$ **kN** ✔
- **$F_{GF}$ (section through BC, GC, GF; take the right part)**: moments about C remove $F_{BC}$ and $F_{GC}$:

$$\sum M_C:\ 3(-F_{GF}) + 4(-15) + 12(15) = 0 \Rightarrow F_{GF} = \mathbf{+40}\ \text{kN}\ ✔$$

- **$F_{GC}$ (same section)**: $\sum F_V$: $15 - 15 - F_{GC}\sin\theta = 0$, so $F_{GC} = \mathbf{0}$ ✔. The centre panel carries no shear, just as a symmetric beam has $Q = 0$ between its two equal loads.

![[s1_t2_q2_warren_truss.png|900]]

---

## Q3: Three-bar truss, displacement of C
$L = 2$ m, $A = 600\times10^{-6}$ m², $E = 70$ GPa. A 200 N load acts at C at 45°, upwards and to the right. B is pinned to the wall; A is on a wall roller (horizontal reaction only).

**Reactions**
- $V_B = -200/\sqrt2$ N.
- $\sum M_B$: the 200 N force is perpendicular to BC, whose length gives a moment arm of $2\sqrt2$ m, so $2H_A + 200(2\sqrt2) = 0$. This gives $H_A = -200\sqrt2$ N; $\sum F_H$ then gives $H_B = 200/\sqrt2$ N.
- Check: $\sum F_H = -200\sqrt2 + 200/\sqrt2 + 200/\sqrt2 = 0$ ✔

**Bar forces**
- Joint A: $F_{AC} = 200\sqrt2 = +283$ N and $F_{AB} = 0$.
- Joint C: $F_{BC}\sin45^\circ + 200\sin45^\circ = 0$, so $F_{BC} = -200$ N.

**Extensions**

| Bar | Force | Length | $\Delta L = FL/AE$ |
|---|---|---|---|
| AB | 0 | $L$ | 0 |
| AC | $+200\sqrt2$ | $L$ | $+\delta$ |
| BC | $-200$ | $\sqrt2L$ | $-\delta$ |

with $\delta = \dfrac{200\sqrt2(2)}{(600\times10^{-6})(70\times10^9)} = 13.47\ \mu$m. Both bars change length by the same magnitude.

**Displacement diagram.** C moves $+\delta$ along AC (to the right) and $-\delta$ along BC, i.e. towards B:

$$u_x = \delta,\qquad \frac{u_x - u_y}{\sqrt2} = -\delta\;\Rightarrow\; u_y = (1+\sqrt2)\,\delta = 2.414\,\delta$$

$$
\Delta x_C = \mathbf{13}\ \mu\text{m}\ (\rightarrow),\qquad \Delta y_C = \mathbf{32}\ \mu\text{m}\ (\uparrow)\ ✔
$$

The sheet writes this as $\delta/\tan22.5^\circ\approx2.4\delta$, which is the same number, since $1/\tan22.5^\circ = 1+\sqrt2$. The displacements are far smaller than the 2 m bar lengths, so the small-deformation assumption holds.

![[s1_t2_q3_three_bar.png|620]]

---

## Extra Q1: Truss with $F = 80$ N upwards at C ($L = 3$ m): force in AB
No whole-truss FBD is needed. Cut through ED, AD and AB and keep the right-hand part. The lines of action of $F_{ED}$ and $F_{AD}$ both pass through D, so take moments about D:

$$
\sum M_D:\ 2LF - LF_{AB} = 0\;\Rightarrow\; F_{AB} = 2F = \mathbf{160}\ \text{N}\ ✔
$$

![[s1_t2_x1_truss.png|700]]

## Extra Q2: Braced tower, 20 kN horizontal loads at B, D, F
- **Joint A first**: bars AB and AC are perpendicular and there is no load at A, so both are **zero-force members**.
- **Joint B**: $\sum F_H$: $20 - F_{BC}\cos45^\circ = 0$, so $F_{BC} = 20\sqrt2$ kN. Then $\sum F_V$: $-F_{BC}\sin45^\circ - F_{BD} = 0$, so $F_{BD} = \mathbf{-20}$ **kN** ✔
- **Section below D**, moments about E: $-2l(20) - l(20) - lF_{DF} = 0$, so $F_{DF} = \mathbf{-60}$ **kN** ✔
- **Section below F**, moments about G: $-3l(20) - 2l(20) - l(20) - lF_{FH} = 0$, so $F_{FH} = \mathbf{-120}$ **kN** ✔

The windward legs are in tension and the leeward legs in compression, growing linearly downwards. This is the truss version of a cantilever bending-moment diagram.

![[s1_t2_x2_tower.png|560]]

## Sources
- Source sheet and official solutions: Statics-1 Tutorial problem sheet 2
- Bar forces cross-checked with the joint-equilibrium solver in `Figures/feeg1002_style.py`
