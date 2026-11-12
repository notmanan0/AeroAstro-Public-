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

> [!abstract] Sheet info
> Two core questions (a bike frame and a three-panel Warren truss) and three additional problems (a truss with an upward load, a braced tower, and the displacement of a three-bar truss). Every truss was also solved as a full joint-equilibrium system, which checks each hand result and gives every bar force, not just those asked for. All printed answers are reproduced. In the figures blue is tension (+), red compression (−) and dashed grey a zero-force member; line thickness grows with the size of the force.

Theory: [[FEEG1002 A2 - Pin-Jointed Trusses]] · [[Method of Joints and Method of Sections]] · [[Williot Displacement Diagram]]

---

## Q1 - Bike frame

Taught in: [[FEEG1002 A2 - Pin-Jointed Trusses#Worked example - bike frame by the method of joints|A2, bike frame]] · [[FEEG1002 A2 - Pin-Jointed Trusses#3. The method of joints|A2, method of joints]]

Joint A (head tube) is pinned and D (rear axle) is on a roller. With A at the origin, B is 0.5 m to the right, C 0.5 m below B, and D 0.5 m to the right of C, so AC and BD are at 45°. The rider's weight $F=750$ N acts down at B.

### (a) Tension or compression

Ask what would happen if each bar were removed: if its end joints would move apart, the bar holds them together and is in tension; if they would move together, it is in compression. CD and AC are in tension; BD, AB and BC in compression.

### (b) Forces in BD and CD

Moments about A give $F_D(1.0)=750(0.5)$, so $F_D=375$ N, and vertically $F_A=375$ N, as symmetry about B suggests. Joint D has only two bars. Vertically, with the tensile force in BD pointing up and to the left:

$$
375+F_{BD}\sin45^\circ=0\quad\Rightarrow\quad F_{BD}=-530\ \mathrm N
$$

Horizontally, with CD pulling left:

$$
-F_{CD}-F_{BD}\cos45^\circ=0\quad\Rightarrow\quad F_{CD}=+375\ \mathrm N
$$

The full solution confirms the prediction: $F_{AB}=-375$ N, $F_{AC}=+530$ N and $F_{BC}=-375$ N.

![[s1_t2_q1_bike_frame.png|700]]

## Q2 - Warren truss

Taught in: [[FEEG1002 A2 - Pin-Jointed Trusses#Worked example - Warren truss by the method of sections|A2, Warren truss]] · [[FEEG1002 A2 - Pin-Jointed Trusses#4. The method of sections|A2, method of sections]]

The bottom joints A, G, F, E are at $x=0$, 8, 16, 24 m and the top joints B, C, D at $x=4$, 12, 20 m, 3 m above; A is pinned, E on a roller, and 15 kN hangs from each of G and F. Each diagonal is a 3–4–5 triangle, $\sin\theta=3/5$, $\cos\theta=4/5$. Reactions: $H_A=0$ and, from moments about A, $24V_E=8(15)+16(15)$, so $V_E=V_A=15$ kN.

**DE, by joint E:** $15+F_{DE}\sin\theta=0$, so $F_{DE}=-25$ kN.

**GF, by a section through BC, GC and GF**, keeping the right part and taking moments about C, where BC and GC meet:

$$
-3F_{GF}-4(15)+12(15)=0\quad\Rightarrow\quad F_{GF}=+40\ \mathrm{kN}
$$

**GC, from the same section:** BC and GF are horizontal, so vertically $15-15-F_{GC}\sin\theta=0$ and $F_{GC}=0$. The middle panel carries no shear between the two equal loads, like a symmetric beam between two equal loads.

![[s1_t2_q2_warren_truss.png|900]]

---

## Extra Q1 - Truss with an upward load

Taught in: [[FEEG1002 A2 - Pin-Jointed Trusses#4. The method of sections|A2, method of sections]]

E is pinned to a wall at the top left, with A on a wall roller below it. The top chord runs E–D–C with $ED=L$ and $DC=2L$; the bottom chord A–B is $2L$ long; the height is $L$, with diagonals AD, DB and BC. A force $F=80$ N acts upward at C, and $L=3$ m.

No whole-truss FBD is needed. Cut through ED, AD and AB and keep the right-hand part. The lines of action of $F_{ED}$ and $F_{AD}$ both pass through D, so take moments about D:

$$
2LF-LF_{AB}=0\quad\Rightarrow\quad F_{AB}=2F=160\ \mathrm N
$$

![[s1_t2_x1_truss.png|800]]

## Extra Q2 - Braced tower

Taught in: [[FEEG1002 A2 - Pin-Jointed Trusses#4. The method of sections|A2, method of sections]] · [[FEEG1002 A2 - Pin-Jointed Trusses#Zero-force members|A2, zero-force members]]

The tower has panels of width $\ell$: A–B at the top, then C–D, E–F, G–H, with diagonals BC, DE and FG; 20 kN acts horizontally to the right at B, D and F. G is pinned and H on a roller.

At joint A, bars AB and AC are perpendicular and there is no load, so both are zero-force members. At joint B, horizontally $20-F_{BC}\cos45^\circ=0$, so $F_{BC}=20\sqrt2$ kN, and vertically $-F_{BC}\sin45^\circ-F_{BD}=0$, so $F_{BD}=-20$ kN.

For DF, cut below D and take moments about E (the official solution cuts DF, EF and EG; cutting CE, DE and DF and taking moments about E gives the same equation):

$$
-2\ell(20)-\ell(20)-\ell F_{DF}=0\quad\Rightarrow\quad F_{DF}=-60\ \mathrm{kN}
$$

For FH, cut below F and take moments about G:

$$
-3\ell(20)-2\ell(20)-\ell(20)-\ell F_{FH}=0\quad\Rightarrow\quad F_{FH}=-120\ \mathrm{kN}
$$

The leeward legs BD, DF, FH are in compression at −20, −60 and −120 kN and the windward legs AC, CE, EG in tension at 0, +20 and +60 kN. The forces grow in the ratio 1 : 3 : 6 going down, in step with the overturning moment, like the bending moment of a cantilever under point loads.

![[s1_t2_x2_tower.png|600]]

## Extra Q3 - Displacement of a three-bar truss

Taught in: [[FEEG1002 A2 - Pin-Jointed Trusses#7. Truss deformation|A2, truss deformation]] · [[FEEG1002 A2 - Pin-Jointed Trusses#The displacement diagram|A2, displacement diagram]]

B is pinned to a wall at $(0,2)$, A is on a wall roller (horizontal reaction only) at $(0,0)$, and C is at $(2,0)$. A 200 N load acts at C at 45°, upwards and to the right. $L=2$ m, $A=600$ mm², $E=70$ GPa.

**Reactions.** $V_B=-200/\sqrt2$ N. The load is perpendicular to BC, which has length $2\sqrt2$ m, so moments about B give $2H_A+200(2\sqrt2)=0$ and $H_A=-200\sqrt2$ N; then $H_B=200/\sqrt2$ N. Check: $-200\sqrt2+200/\sqrt2+200/\sqrt2=0$.

**Bar forces.** Joint A: $F_{AC}=200\sqrt2=+283$ N and $F_{AB}=0$. Joint C: $F_{BC}\sin45^\circ+200\sin45^\circ=0$, so $F_{BC}=-200$ N.

**Extensions.**

| Bar | Force (N) | Length | $\Delta L=FL/AE$ |
|---|---|---|---|
| AB | 0 | $L$ | 0 |
| AC | $+200\sqrt2$ | $L$ | $+\delta$ |
| BC | $-200$ | $\sqrt2L$ | $-\delta$ |

with

$$
\delta=\frac{200\sqrt2(2)}{(600\times10^{-6})(70\times10^9)}=13.47\ \mu\mathrm m
$$

Both bars change length by the same amount.

**Displacement of C.** C moves $+\delta$ along AC, to the right, and $-\delta$ along BC, towards B. With $\mathbf e_{BC}=(1,-1)/\sqrt2$:

$$
u_x=\delta,\qquad\frac{u_x-u_y}{\sqrt2}=-\delta\quad\Rightarrow\quad u_y=(1+\sqrt2)\delta=2.414\delta
$$

$$
\Delta x_C=13\ \mu\mathrm m\ (\rightarrow),\qquad\Delta y_C=32\ \mu\mathrm m\ (\uparrow)
$$

The official solution finds the same from a displacement diagram, writing $\Delta y_C=\delta/\tan22.5^\circ\approx2.4\delta$; $1/\tan22.5^\circ=1+\sqrt2$, so the two agree.

![[s1_t2_q3_three_bar.png|700]]

## Sources

- Tutorial Sheet 02 and its official solutions: Q1 pp. 1–2, Q2 pp. 3–4, additional Q1 p. 5, additional Q2 pp. 6–9, additional Q3 pp. 10–13.
- Bar forces cross-checked with the joint-equilibrium solver in `Figures/generate_statics1_figures.py`.
- The official solution's 2.4 for $1+\sqrt2$ (p. 13) gives 13.45 μm for $\delta$; the exact value is 13.47 μm, and the rounded answers are unaffected.
