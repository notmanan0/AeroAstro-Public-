---
title: "FEEG1002 A7 - Euler Buckling of Struts"
module: "FEEG1002 Mechanics, Materials and Structures"
type: topic
stream: "Part A: Statics 1"
order: 7
tags: [feeg1002, statics, buckling, euler, effective-length, stability]
aliases: ["Statics 1 Lecture 12", "Buckling", "Euler critical load"]
date: 2026-09-25
status: complete
parent: ["[[FEEG1002 Mechanics, Materials and Structures Hub]]"]
prerequisites: ["[[FEEG1002 A5 - Beam Deflection and Macaulay's Method]]"]
next_topics: ["[[FEEG1002 A8 - Torsion of Circular Shafts]]"]
key_concepts: ["[[Euler Buckling]]", "[[Effective Length]]", "[[Slenderness Ratio]]"]
tutorial_sheets: ["[[FEEG1002 Statics 1 Tutorial 6 - Buckling, Torsion and Shear Stress Solutions]]"]
sources: ["02 - Sources/Statics 1/Lectures/Lecture 12 - Buckling.pdf"]
---

# FEEG1002 A7 - Euler Buckling of Struts

> [!abstract] Summary
> A short, stocky column fails by crushing or yielding. A **slender** strut fails first by **buckling**: at a critical load it becomes unstable and bows sideways, often while the stress is still well below yield. Writing the moment on the **deflected** shape, $M = Pv$, turns $EIv'' = -M$ into the eigenvalue problem $v'' + (P/EI)v = 0$. The lowest non-trivial solution is the Euler load
>
> $$P_{cr} = \frac{\pi^2EI}{L_e^2}$$
>
> The **effective length** $L_e$ captures the end conditions, and $I$ is the **smallest** second moment of area.

## Key Concepts
- [[Euler Buckling]] · [[Effective Length]] · [[Slenderness Ratio]]

---

## 1. Why buckling is different (L12a)
- Earlier topics analysed the undeformed geometry. Here the load's effect **depends on the deflection itself**: the moment arm is $v(x)$.
- For a pin-ended strut with compressive load $P$, taking moments at a cut gives $M(x) = Pv(x)$. The more it bends, the larger the moment, so the situation feeds on itself.

## 2. The governing equation (L12a–b)

$$
EI\frac{d^2v}{dx^2} = -Pv\quad\Rightarrow\quad \frac{d^2v}{dx^2} + n^2v = 0,\qquad n^2 = \frac{P}{EI}
$$

$$
v = A\sin nx + B\cos nx
$$

- $v(0) = 0$ gives $B = 0$.
- $v(L) = 0$ gives $A\sin nL = 0$, which has two ways out:
  1. $A = 0$: the strut stays **straight** (trivial solution, stable).
  2. $\sin nL = 0$, so $nL = \pi, 2\pi, 3\pi, \dots$ The lowest gives

$$
P_{cr} = \frac{\pi^2EI}{L^2},\qquad v = A\sin\frac{\pi x}{L}
$$

The amplitude $A$ is **arbitrary**: at $P_{cr}$ the strut is in **neutral equilibrium**, and any small sideways shape can hold. Below $P_{cr}$ it stays straight; above it, it collapses. Higher modes ($4P_{cr}$, $9P_{cr}$, ...) need lateral restraint at the nodes of the lower modes.

> [!note] Linear theory only predicts the onset
> Small-deflection theory cannot give the post-buckling amplitude, and real struts are never perfectly straight. They start bowing *before* $P_{cr}$. See [[SESA2028 S6 - Imperfect Columns, Beam-Columns and Plate Buckling]].

## 3. Direction of buckling
$P_{cr}\propto I$, so the strut buckles about the axis with the **least** $I$ (with the **largest** $L_e$ if restraints differ between the two planes). A flat ruler buckles about its thin direction.

> [!example] Tutorial 6 Q1: stainless I-section, $L = 5$ m, $E = 213$ GPa, pin-ended
> - $I_{zz} = 3.38\times10^{-7}$ m⁴, but $I_{yy} = 1.07\times10^{-7}$ m⁴ (the flanges contribute little sideways).
> - So $P_{cr} = \pi^2(213\times10^9)(1.07\times10^{-7})/5^2 = 9.0$ kN.
> - A pinned support at midspan halves $L_e$ and **quadruples** $P_{cr}$.

## 4. End conditions and effective length (L12c)
Compare each buckled shape with a pin-ended half sine wave:

![[s1_buckling_mode_shapes.png|760]]

| Ends | Mode shape | $L_e$ | $P_{cr}$ |
|---|---|---|---|
| Pinned–pinned | half sine | $L$ | $\pi^2EI/L^2$ |
| Built-in–free (flagpole) | quarter sine | $2L$ | $\pi^2EI/4L^2$ |
| Built-in–built-in (no sway) | full cosine | $L/2$ | $4\pi^2EI/L^2$ |
| Built-in–pinned | not a sine: $\tan nL = nL$ | $0.699L$ | $2.05\pi^2EI/L^2$ |

More end constraint means a shorter $L_e$ and a higher $P_{cr}$. $L_e$ enters **squared**, so the end conditions often matter more than the section.

For the built-in–pinned strut, the mode shape $v\propto\sin nx + nL(1-\cos nx) - nx$ satisfies $v(0) = v'(0) = 0$ and $v(L) = v''(L) = 0$. The first root is $nL = 4.4934$, so $L_e = \pi/4.4934\,L = 0.699L$.

## 5. Buckling or yield?
Dividing by area and using the radius of gyration $r = \sqrt{I/A}$:

$$
\sigma_{cr} = \frac{P_{cr}}{A} = \frac{\pi^2E}{(L_e/r)^2}
$$

Buckling governs when $\sigma_{cr} < \sigma_y$, i.e. when the [[Slenderness Ratio]] $L_e/r > \pi\sqrt{E/\sigma_y}$. That threshold is about 91 for A36 steel and about 42 for a high-strength aluminium alloy.

![[s1_euler_column_curve.png|680]]

## 6. Design implications
- In trusses, make the **long** members carry tension and keep compression members short (L12 bracing example).
- Hollow sections raise $I$, and hence $r$, for the same area. That is why struts are tubes.
- Intermediate restraints (bracing, stringers, ribs) cut $L_e$. A stiffened aircraft panel is the classic example.

## Year 2 bridge
- [[SESA2028 S5 - Euler Buckling and Effective Length]] rederives the same eigenproblem in its own convention, generalises $L_e = KL$, and checks the weak principal axis for unsymmetric sections ([[Principal Axes of a Section]]).
- [[SESA2028 S6 - Imperfect Columns, Beam-Columns and Plate Buckling]] covers:
  - initial imperfection and eccentric load ([[Secant Formula]]);
  - the $1/(1-P/P_E)$ amplification ([[Beam-Column Amplification]]);
  - thin **plates** ([[Plate Buckling]], $\sigma_{cr} = k\pi^2E(t/b)^2/12(1-\nu^2)$). This is the dominant failure mode of aircraft skins.
- Buckling as an eigenvalue problem connects to modal analysis ([[Natural Frequencies and Mode Shapes]]) and to nonlinear FEA ([[SESA2029 B9 - Nonlinear FE Analysis]]).
- For material choice for a light strut, the [[Specific Stiffness and Strength]] index $E^{1/2}/\rho$ follows directly from $P_{cr}\propto EI$.

## Links
- Previous: [[FEEG1002 A6 - Statically Indeterminate Beams]] · Next: [[FEEG1002 A8 - Torsion of Circular Shafts]]
- Worked problems: [[FEEG1002 Statics 1 Tutorial 6 - Buckling, Torsion and Shear Stress Solutions]]

## Sources
- Statics 1 Lecture 12a–c (introduction; solving the buckling problem; boundary conditions and effective length)
