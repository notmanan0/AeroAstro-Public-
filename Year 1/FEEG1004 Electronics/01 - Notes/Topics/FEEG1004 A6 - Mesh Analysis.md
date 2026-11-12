---
title: FEEG1004 A6 - Mesh Analysis
module: FEEG1004 Electronics
type: topic
stream: 'Part A: Electrical Fundamentals and DC Circuits'
order: 6
tags:
- feeg1004
- fundamentals
- mesh-analysis
- kvl
- matrices
- loop-currents
aliases:
- Lecture 5c / 6
- Mesh analysis
- Loop currents
date: 2026-09-27
status: lectured
parent:
- "[[FEEG1004 Electronics Hub]]"
prerequisites:
- "[[FEEG1004 A3 - DC Circuit Laws - Ohm, KCL, KVL and Dividers]]"
next_topics:
- "[[FEEG1004 A7 - Thevenin, Superposition and Relays]]"
key_concepts:
- "[[Mesh Current Method]]"
- "[[Kirchhoff's Current and Voltage Laws]]"
tutorial_sheets:
- "[[FEEG1004 Tutorial 2 - DC Circuit Analysis and Kirchhoff's Laws Solutions]]"
sources:
- 02 - Sources/S1 Fundamentals/S1-W05-6 Mesh Analysis - Recorded.pdf
- 02 - Sources/S1 Fundamentals/S1-W05 Inductors Resonance and Mesh Analysis - Interactive.pdf
- 02 - Sources/Lectures/FEEG1004 Lecture 2020-10-13 - 6 Mesh Analysis.txt
- 02 - Sources/S1 Fundamentals/S1-W06 Thevenin and Superposition - Interactive.pdf
- 02 - Sources/Lectures/FEEG1004 Lecture 5.txt
coverage: 6 Mesh Analysis (ll. 3-135); Lecture 5 (ll. 186-193) supplies the two-mesh alternative for the W06 circuit
---


# FEEG1004 A6 - Mesh Analysis

> [!abstract] Summary
> Mesh analysis assigns a reference current to each window of a planar circuit and uses KVL to form simultaneous equations. A shared resistor carries the algebraic difference of neighbouring clockwise mesh currents. Collecting coefficients gives $\mathbf R\mathbf I=\mathbf V$; physical branch currents are then recovered from sums and differences of the solved mesh currents.

> [!summary]- Exam use: quick path
> - **Use it when:** a resistor network has several loops and cannot be reduced conveniently by series/parallel combinations.
> - **Assumptions:** a planar circuit; ideal wires; the direct resistance-matrix form here uses resistors and independent voltage sources.
> - **Method:** 1. Assign clockwise mesh currents. 2. Traverse each mesh, adding source rises and subtracting resistor drops. 3. Collect coefficients into the matrix. 4. Solve if required. 5. Recover branch currents and check KCL or power.
> - **Common mistakes:** adding neighbouring clockwise mesh currents in a shared resistor; treating a mesh current as the physical current in every branch of its loop.
> - **Practise:** [[#Worked examples]] · [[FEEG1004 Tutorial 2 - DC Circuit Analysis and Kirchhoff's Laws Solutions#Q1: Mesh equations for the four-window network|Tutorial 2 Q1]]

A circuit can contain many closed paths, but their KVL equations are not all independent. Writing every possible loop equation adds work without necessarily adding information. Mesh analysis chooses the smallest windows in a planar drawing so that the independent current variables and voltage equations match.

Each mesh current is a mathematical reference circulating around one window. A wire on the outer edge belongs to one mesh, while an internal branch can belong to two. The physical current in that shared branch combines both contributions, taking their directions into account.

This arrangement builds charge conservation into the current description. When the mesh contributions are combined at a node, their incoming and outgoing terms cancel. KVL then determines the mesh-current values consistent with the component voltage drops and sources.

## 1. Choosing currents and voltage signs

A **mesh** is a loop enclosing no smaller loop in a planar circuit. Assign a clockwise current $I_k$ to each mesh. These capital-letter currents differ from the lower-case branch currents $i_k$ used in the source diagrams.

Traverse each mesh clockwise, starting at its bottom-left corner for consistency. A voltage source crossed from negative to positive gives a positive rise. Across a resistor, subtract resistance times the current component in the traversal direction. This follows the passive sign convention established in [[FEEG1004 A3 - DC Circuit Laws - Ohm, KCL, KVL and Dividers]].

For a single loop, KVL gives

$$
V-IR_1-IR_2-IR_3=0.
$$

Collecting the resistor terms,

$$
V-I(R_1+R_2+R_3)=0.
$$

Therefore

$$
I=\frac{V}{R_1+R_2+R_3}.
$$

Clockwise is a reference direction, not a prediction. A negative solved current reverses that reference. Multiplying an entire KVL equation by minus one also leaves the physical result unchanged.

## 2. Shared resistors and matrix coefficients

Suppose meshes 1 and 2 share resistance $R_s$. In the clockwise traversal of mesh 1, its own current points forwards and mesh 2's current points backwards. The branch current in that direction is

$$
i_s=I_1-I_2.
$$

The corresponding voltage drop is

$$
v_s=R_s(I_1-I_2).
$$

For mesh 2 the traversal is reversed, so its drop is $R_s(I_2-I_1)$. The same physical resistor appears in both equations with opposite branch-current references.

If $I_2$ contributes downwards and $I_3$ upwards through a shared resistor, the physical upward current is $I_3-I_2$. Reversing a requested branch direction reverses the sign of the whole expression.

For two meshes with unshared resistances $R_a,R_b$ and net clockwise source rises $V_1,V_2$, KVL gives

$$
V_1-R_aI_1-R_s(I_1-I_2)=0,
$$

$$
V_2-R_bI_2-R_s(I_2-I_1)=0.
$$

Expand the shared terms:

$$
V_1-R_aI_1-R_sI_1+R_sI_2=0,
$$

$$
V_2-R_bI_2-R_sI_2+R_sI_1=0.
$$

Collect the current coefficients:

$$
(R_a+R_s)I_1-R_sI_2=V_1,
$$

$$
-R_sI_1+(R_b+R_s)I_2=V_2.
$$

The matrix form is

$$
\begin{pmatrix}
R_a+R_s&-R_s\\
-R_s&R_b+R_s
\end{pmatrix}
\begin{pmatrix}I_1\\I_2\end{pmatrix}
=\begin{pmatrix}V_1\\V_2\end{pmatrix}.
$$

Each diagonal entry sums the resistance around that mesh. Each off-diagonal entry is minus the resistance shared by the corresponding pair. The resistance matrix is symmetric for this network of resistors and consistently oriented mesh currents. Its entries have units of ohms, so each row times current gives volts.

The direct form above does not include a current source shared between meshes; that would need an additional constraint. The worked resistance-matrix problems here contain voltage sources.

## 3. The three-mesh source example

The circuit has a $10\,\mathrm V$ supply. Mesh 1 is the lower-left window, mesh 2 the lower-right and mesh 3 the upper window. Meshes 1 and 2 share $4\,\Omega$, meshes 1 and 3 share $2\,\Omega$, and meshes 2 and 3 share another $2\,\Omega$. The outer top resistor is $4\,\Omega$ and the outer right resistor is $3\,\Omega$.

For compactness, resistance coefficients in the next equations are in ohms, currents in amperes and source terms in volts. Mesh 1 gives

$$
10-2(I_1-I_3)-4(I_1-I_2)=0,
$$

$$
10-2I_1+2I_3-4I_1+4I_2=0,
$$

$$
6I_1-4I_2-2I_3=10.
$$

Mesh 2 has no source:

$$
-4(I_2-I_1)-2(I_2-I_3)-3I_2=0,
$$

$$
-4I_2+4I_1-2I_2+2I_3-3I_2=0,
$$

$$
-4I_1+9I_2-2I_3=0.
$$

For mesh 3,

$$
-4I_3-2(I_3-I_2)-2(I_3-I_1)=0,
$$

$$
-4I_3-2I_3+2I_2-2I_3+2I_1=0,
$$

$$
-2I_1-2I_2+8I_3=0.
$$

Together these give

$$
\begin{pmatrix}6&-4&-2\\-4&9&-2\\-2&-2&8\end{pmatrix}
\begin{pmatrix}I_1\\I_2\\I_3\end{pmatrix}
=\begin{pmatrix}10\\0\\0\end{pmatrix}.
$$

### Recovering the five branch currents

In the source drawing, $i_1$ points right through the left $2\,\Omega$ resistor; $i_2$ points right through the other $2\,\Omega$ resistor; $i_3$ points down through the central $4\,\Omega$; $i_4$ points right through the top resistor; and $i_5$ points down through the right resistor. Their mesh contributions give

$$
\begin{aligned}
i_1&=I_1-I_3,\\
i_2&=I_2-I_3,\\
i_3&=I_1-I_2,\\
i_4&=I_3,\\
i_5&=I_2.
\end{aligned}
$$

Thus the second matrix is

$$
\begin{pmatrix}i_1\\i_2\\i_3\\i_4\\i_5\end{pmatrix}
=\begin{pmatrix}1&0&-1\\0&1&-1\\1&-1&0\\0&0&1\\0&1&0\end{pmatrix}
\begin{pmatrix}I_1\\I_2\\I_3\end{pmatrix}.
$$

The coefficients in this matrix are dimensionless. At the central node, $i_1=i_2+i_3$, since $(I_2-I_3)+(I_1-I_2)=I_1-I_3$. This identity shows how the mesh representation satisfies KCL before numerical values are known.

## Worked examples

### Two meshes solved by hand and in Python

The W6 circuit has a $10\,\mathrm V$ source through $10\,\Omega$ on the left, a $20\,\mathrm V$ source through $20\,\Omega$ on the right and a shared $40\,\Omega$ load. Both sources have their positive terminals at the top. Define both mesh currents clockwise and load current downwards.

![[ee_a6_two_mesh.png|900]]

The left-loop equation is

$$
10\,\mathrm V-(10\,\Omega)I_1-(40\,\Omega)(I_1-I_2)=0.
$$

The right loop traverses its source from positive to negative:

$$
-20\,\mathrm V-(20\,\Omega)I_2-(40\,\Omega)(I_2-I_1)=0.
$$

Collecting terms gives the full system

$$
\begin{pmatrix}50&-40\\-40&60\end{pmatrix}\,\Omega
\begin{pmatrix}I_1\\I_2\end{pmatrix}
=\begin{pmatrix}10\\-20\end{pmatrix}\,\mathrm V.
$$

For hand elimination, use numerical coefficients in ohms and volts. Multiply the first row by 4 and the second by 5:

$$
200I_1-160I_2=40,
$$

$$
-200I_1+300I_2=-100.
$$

Add the rows:

$$
140I_2=-60.
$$

Divide by the coefficient:

$$
I_2=-\frac37\,\mathrm A.
$$

Substitute into the first original row:

$$
50I_1-40\left(-\frac37\right)=10,
$$

$$
50I_1+\frac{120}{7}=10,
$$

$$
50I_1=-\frac{50}{7},
$$

$$
I_1=-\frac17\,\mathrm A.
$$

Both actual mesh directions are anticlockwise. The load current is

$$
i_L=I_1-I_2,
$$

$$
i_L=-\frac17\,\mathrm A-\left(-\frac37\,\mathrm A\right)=\frac27\,\mathrm A=0.285714\,\mathrm A.
$$

Solving the same matrix in Python confirms the hand result:

```python
import numpy as np
R = np.array([[50., -40.], [-40., 60.]])  # ohms
V = np.array([10., -20.])                # volts
I1, I2 = np.linalg.solve(R, V)           # amperes
i_load = I1 - I2
# I1 = -0.14285714 A; I2 = -0.42857143 A
# i_load = 0.28571429 A
```

The negative left current means some energy enters the $10\,\mathrm V$ source. It is not a sign error: the higher-voltage source drives both the load and that source.

> [!check] KCL at the load node
> The right branch supplies $3/7\,\mathrm A$ to the top node. The left branch takes $1/7\,\mathrm A$ away and the load takes $2/7\,\mathrm A$. Incoming current equals outgoing current exactly.

### Four meshes in Tutorial 2

Tutorial Sheet 2 Q1 gives the network below and asks for both matrices. The branch directions are as shown, including the bottom branch pointing right, and the three battery cell symbols are read directly from the printed sheet (`20 V` positive at top, `10 V` positive on the left plate, and `15 V` positive at top).

![[ee_t2_q1_mesh.png|900]]

With clockwise mesh currents, KVL gives (since clockwise $I_3$ traverses the bottom `10 V` battery from right negative to left positive, a $+10\,\mathrm V$ rise, while clockwise $I_4$ traverses the right-wall `15 V` battery from top positive to bottom negative, a $-15\,\mathrm V$ drop):

$$
20-5I_1-4(I_1-I_3)=0,
$$

$$
-6I_2-2(I_2-I_3)=0,
$$

$$
10-4(I_3-I_1)-2(I_3-I_2)-(I_3-I_4)=0,
$$

$$
-15-3I_4-(I_4-I_3)=0.
$$

Collecting coefficients in the same row order,

$$
\begin{aligned}
9I_1-4I_3&=20,\\
8I_2-2I_3&=0,\\
-4I_1-2I_2+7I_3-I_4&=10,\\
-I_3+4I_4&=-15.
\end{aligned}
$$

Hence

$$
\begin{pmatrix}9&0&-4&0\\0&8&-2&0\\-4&-2&7&-1\\0&0&-1&4\end{pmatrix}
\begin{pmatrix}I_1\\I_2\\I_3\\I_4\end{pmatrix}
=\begin{pmatrix}20\\0\\10\\-15\end{pmatrix}.
$$

The branch relations follow directly from the arrows:

$$
\begin{aligned}
i_1&=I_1,\\
i_2&=I_3-I_2,\\
i_3&=I_1-I_3,\\
i_4&=-I_3,\\
i_5&=I_3-I_4,\\
i_6&=I_2,\\
i_7&=I_4.
\end{aligned}
$$

Therefore

$$
\begin{pmatrix}i_1\\i_2\\i_3\\i_4\\i_5\\i_6\\i_7\end{pmatrix}
=\begin{pmatrix}1&0&0&0\\0&-1&1&0\\1&0&-1&0\\0&0&-1&0\\0&0&1&-1\\0&1&0&0\\0&0&0&1\end{pmatrix}
\begin{pmatrix}I_1\\I_2\\I_3\\I_4\end{pmatrix}.
$$

Python gives $\mathbf I=(3.726708,\ 0.846273,\ 3.385093,\ -2.903727)^{\mathsf T}\,\mathrm A$. Multiplying by the branch matrix gives $\mathbf i=(3.726708,\ 2.538820,\ 0.341615,\ -3.385093,\ 6.288820,\ 0.846273,\ -2.903727)^{\mathsf T}\,\mathrm A$. Negative branch values ($i_4$ and $i_7$) flow opposite to their drawn arrows. (If the $10\,\mathrm V$ and $15\,\mathrm V$ cell symbols are read with opposite polarity, $\mathbf V=(20,\ 0,\ -10,\ 15)^{\mathsf T}\,\mathrm V$, giving $\mathbf I=(2.484472,\ 0.147516,\ 0.590062,\ 3.897516)^{\mathsf T}\,\mathrm A$.)

For example, the first KVL row checks as $(9\,\Omega)(3.726708\,\mathrm A)-(4\,\Omega)(3.385093\,\mathrm A)=20.0000\,\mathrm V$. The displayed currents are rounded; calculations retain full precision.

> [!check] Total power balance
> Net source output is $(20\,\mathrm V)I_1+(10\,\mathrm V)I_3-(15\,\mathrm V)I_4=151.9410\,\mathrm W$. The sum $5i_1^2+2i_2^2+4i_3^2+i_5^2+6i_6^2+3i_7^2$, with resistances in ohms and currents in amperes, gives the same $151.9410\,\mathrm W$ of resistor heating.

## Links

- Parent: [[FEEG1004 Electronics Hub]]
- Previous: [[FEEG1004 A5 - Inductors and Electrical Resonance]]
- Next: [[FEEG1004 A7 - Thevenin, Superposition and Relays]]
- Concepts: [[Mesh Current Method]] · [[Kirchhoff's Current and Voltage Laws]]

## Sources

- `S1-W05-6 Mesh Analysis - Recorded.pdf`, pp. 2–14; `FEEG1004 Lecture 2020-10-13 - 6 Mesh Analysis.txt` (ll. 3–135), including independent work on meshes 2 and 3 at ll. 95–116 and branch-matrix checking at ll. 130–133.
- `S1-W05 Inductors Resonance and Mesh Analysis - Interactive.pdf`, pp. 13–14; an upward shared-resistor current is $I_3-I_2$ for its specified arrows.
- `S1-W06 Thevenin and Superposition - Interactive.pdf`, p. 10; `FEEG1004 Lecture 5.txt` (ll. 186–193) explicitly identifies two-mesh analysis as an alternative for the $40\,\Omega$ circuit.
- `Tutorial Sheet 02 - DC Circuit Analysis & Kirchhoff's Laws.pdf`, Q1, including the source polarities and all seven branch arrows.
- Both worked systems and numerical checks computed in Python. Three-mesh coefficients and the branch map were checked against the displayed circuit; the two-mesh solution was also obtained by hand elimination.

## Self-study tasks

### Core

- [ ] Write both matrices for the four-window network (Tutorial Sheet 2 Q1). → [[FEEG1004 Tutorial 2 - DC Circuit Analysis and Kirchhoff's Laws Solutions#Q1: Mesh equations for the four-window network|Tutorial 2 Q1]]; [[#Four meshes in Tutorial 2]].
- [ ] Write the second and third KVL equations for the source example (mesh transcript ll. 95–116). → [[#3. The three-mesh source example]].
- [ ] Check all five rows mapping mesh currents to branches (mesh transcript ll. 130–133). → [[#Recovering the five branch currents]].

### Further practice

- [ ] Recover the upward current through the shared resistor, reversing the downward reference (W5 interactive p. 14). → [[#2. Shared resistors and matrix coefficients]].
- [ ] Reproduce the two-mesh elimination, then check its node currents (suggested, not lecturer-set). → [[#Two meshes solved by hand and in Python]].

## Transcript and slide slips

> [!warning] Branch variables also require current constraints
> Where: [[#2. Shared resistors and matrix coefficients]]
> The mesh transcript l. 51 suggests needing a loop equation for every branch when working with branch currents. Independent KVL equations alone do not provide one independent equation per branch; branch-current analysis also needs KCL constraints. Mesh currents incorporate those current constraints and leave one KVL equation per independent mesh for the voltage-source networks considered here.
