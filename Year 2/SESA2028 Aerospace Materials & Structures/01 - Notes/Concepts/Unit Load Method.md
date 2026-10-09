---
title: "Unit Load Method"
module: "SESA2028 Aerospace Materials & Structures"
type: concept
stream: "Structures"
tags: [sesa2028, structures, virtual-work]
status: complete
parent: ["[[SESA2028 S8 - Virtual Work and Castigliano Theorems]]"]
---

# Unit Load Method

**What it is:** the virtual-force form of the [[Principle of Virtual Work]], used to find **one displacement** in a linear elastic structure.

## Recipe

1. **Real system**: find the internal moment $M(x)$ (and $N$, $T$ if relevant) from the actual loads.
2. **Virtual system**: remove all real loads. Apply a **unit force** at the point and in the direction of the wanted displacement, or a **unit moment** for a rotation. Find $m(x)$ (and $n$, $t$).
3. Integrate over every member:
$$
\delta=\int\frac{Mm}{EI}dx+\int\frac{Nn}{EA}dx+\int\frac{Tt}{GJ}dx.
$$
4. A positive result means the displacement is in the direction of the unit load.

## Worked example

Simply supported beam, span $L$, central point load $W$; find the mid-span deflection. By symmetry, integrate over half the span and double. $M=Wx/2$ and $m=x/2$ for $0\le x\le L/2$:

$$
\delta=2\int_0^{L/2}\frac{(Wx/2)(x/2)}{EI}dx=\frac{W}{2EI}\cdot\frac{(L/2)^3}{3}=\frac{WL^3}{48EI}.\ \checkmark
$$

## Bookkeeping rules

- Use the **same coordinate $x$ and sign convention** for $M$ and $m$ in each segment.
- Split the integral wherever $M$, $m$ or $EI$ changes form: at loads, supports, hinges, frame corners and section changes.
- For frames, include axial terms only if asked (they are usually small).
- Product integrals of standard shapes (e.g. triangle × triangle $=\tfrac13$ length × heights) save time.

It is mathematically identical to Castigliano: $\partial M/\partial P=m$. See [[Castigliano Theorem]].
