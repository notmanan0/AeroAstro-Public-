---
title: "Line Integrals"
module: "MATH2048 Mathematics for Engineering and the Environment Part II"
type: concept
stream: "Block 5: Vector Calculus"
aliases: ["Work integral", "Circulation", "Path integral"]
tags: [math2048, concept, vector-calculus]
status: complete
parent_lectures: ["[[MATH2048 VC3 - Line Integrals and Conservative Fields]]"]
related_concepts: ["[[Conservative Vector Fields]]", "[[Stokes' Theorem]]"]
sources: ["02 - Sources/Lectures & Problem Sheets/Vector Calculus/Lecture22_vector02.pdf"]
---

# Line Integrals

## Definition

> [!note] Definition
>
> $$\int_C\mathbf F\cdot d\mathbf r=\int_a^b\mathbf F(\mathbf r(t))\cdot\frac{d\mathbf r}{dt}\,dt .$$
>
> This is the work done by $\mathbf F$ along $C$. Around a closed loop, $\oint_C\mathbf F\cdot d\mathbf r$ is the **circulation**.

## Explanation
**Recipe**:
1. Parametrise the curve, making sure it runs in the right direction.
2. Substitute $\mathbf r(t)$ into $\mathbf F$.
3. Dot with $\dot{\mathbf r}$.
4. Integrate over $t$.

**Properties**:
- The value does not depend on how the curve is parametrised.
- It **changes sign** if the direction is reversed.
- In general it depends on the path. It depends only on the endpoints iff $\mathbf F$ is conservative, in which case $\int\nabla\phi\cdot d\mathbf r=\phi(B)-\phi(A)$.

**Shortcuts**:
- If $\nabla\times\mathbf F=\mathbf 0$, find the potential $\phi$ and just evaluate it at the endpoints.
- For a closed loop, Stokes's theorem may be easier: $\oint=\iint(\nabla\times\mathbf F)\cdot d\mathbf S$.

## Examples
- $\mathbf F=(2xy,\ x^2-z^2,\ -3xz^2)$ from $(0,0,0)$ to $(2,1,3)$:
  - along $(2t,t^3,3t^2)$ the integral is $-323/7$;
  - along the straight line it is $-79/2$.

  The two paths give different answers, so $\mathbf F$ is not conservative.
- PS8 Q7c, a helix: $4\pi+16\pi^2/3$.

## Related
- [[Conservative Vector Fields]] · [[Stokes' Theorem]] · [[Kelvin's Circulation Theorem]]

## Sources
- Lectures 21–22; Lecture Notes §8.2.1
