---
title: "SESA2028 S5 - Euler Buckling and Effective Length"
module: "SESA2028 Aerospace Materials & Structures"
type: topic
stream: "Structures"
order: 5
tags: [sesa2028, structures, buckling, euler]
status: complete
parent: ["[[SESA2028 Aerospace Materials & Structures Hub]]"]
prerequisites: ["[[SESA2028 S2 - Beam Deflection and Bending Design]]"]
next_topics: ["[[SESA2028 S6 - Imperfect Columns, Beam-Columns and Plate Buckling]]"]
key_concepts: ["[[Euler Buckling]]", "[[Effective Length]]", "[[Slenderness Ratio]]"]
tutorial_sheets: ["[[SESA2028 Structures Tutorial 4 - Buckling Solutions]]"]
sources: ["02 - Sources/Structures Lectures/SL6 Instability and Euler buckling theory.pdf", "02 - Sources/Structures Lectures/Structures Additional session_buckling.pdf"]
---

# SESA2028 S5 - Euler Buckling and Effective Length

> [!abstract] Summary
> Buckling is a stability failure, not a material-strength failure. An ideal straight column can lose lateral stiffness at the Euler load even though its direct compressive stress is well below yield.

## 1. Governing equation

For a pin-ended column under a centric compressive force $P$,

$$
EI\frac{d^2v}{dx^2}+Pv=0.
$$

Let $\mu^2=P/(EI)$. The non-trivial solution satisfying $v(0)=v(L)=0$ exists when

$$
\sin(\mu L)=0.
$$

Therefore

$$
P_{cr,n}=\frac{n^2\pi^2EI}{L^2},
$$

and the first mode $n=1$ governs an ideal column.

## 2. Effective length

For other end conditions,

$$
P_{cr}=\frac{\pi^2EI}{(KL)^2}.
$$

| End conditions | $K$ | Qualitative mode |
|---|---:|---|
| fixed-free | 2.0 | quarter sine wave |
| pinned-pinned | 1.0 | half sine wave |
| fixed-pinned | about 0.7 | between pinned and fixed-fixed |
| fixed-fixed | 0.5 | double curvature |

![[Figures/structures_euler_buckling_end_conditions.png]]

## 3. Weak axis and slenderness

The radius of gyration is

$$
r_g=\sqrt{\frac IA},\qquad \lambda=\frac{KL}{r_g}.
$$

Euler stress is

$$
\sigma_E=\frac{P_{cr}}A=\frac{\pi^2E}{\lambda^2}.
$$

Always calculate $P_{cr}$ about both principal axes and use the smaller value. The weak axis is the one with smaller $I$, not necessarily the visually narrower direction.

## 4. Validity

Euler theory assumes a straight, slender, prismatic, elastic column; a perfectly centric load; small rotations before bifurcation; and idealised end restraints. It becomes unreliable when yielding, local plate buckling, shear deformation or imperfect restraint controls first.

A quick comparison is

$$
P_{failure}\le\min(P_{cr},A\sigma_{allow}).
$$

## 5. Physical interpretation

The straight equilibrium path still exists mathematically above $P_{cr}$, but it is unstable. Any tiny lateral disturbance grows rather than being restored. Real columns have initial crookedness and load eccentricity, so their response is a rapidly amplifying deflection rather than a perfectly sudden bifurcation.

## 6. Exam workflow

1. Identify the weakest bending axis and calculate $I$.
2. Select $K$ from the actual end restraints.
3. Calculate $P_{cr}$ and the corresponding average stress.
4. Compare with yield or allowable load.
5. If eccentricity, lateral load or initial curvature is given, move to the beam-column treatment in [[SESA2028 S6 - Imperfect Columns, Beam-Columns and Plate Buckling]].

## Year 1 foundation
- [[FEEG1002 A7 - Euler Buckling of Struts]]: $P_{cr} = \pi^2EI/L_e^2$, end conditions and effective length.
