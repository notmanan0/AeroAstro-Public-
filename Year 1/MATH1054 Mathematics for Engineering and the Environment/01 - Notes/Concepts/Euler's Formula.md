---
title: "Euler's Formula"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: concept
stream: "Block 2: Complex Numbers"
aliases: ["e^{jθ}", "Euler identity"]
tags: [math1054, concept, complex-numbers]
status: complete
parent_lectures: ["[[MATH1054 M05 - Complex Numbers I]]", "[[MATH1054 M22 - Complex Numbers II]]"]
related_concepts: ["[[Complex Numbers - Cartesian, Polar and Exponential Forms]]", "[[Hyperbolic Functions]]", "[[Phasor Representation]]", "[[Auxiliary Equation]]"]
sources: ["James, Modern Engineering Mathematics (6th ed.) §3.2.8", "MATH1054 Module Booklet, Module 5"]
---

# Euler's Formula

## Definition

> [!note] Definition
> $$e^{\mathrm j\theta}=\cos\theta+\mathrm j\sin\theta,\qquad\cos\theta=\frac{e^{\mathrm j\theta}+e^{-\mathrm j\theta}}2,\qquad\sin\theta=\frac{e^{\mathrm j\theta}-e^{-\mathrm j\theta}}{2\mathrm j}$$

## Explanation
- It follows by comparing the Maclaurin series of $e^{\mathrm j\theta}$, $\cos\theta$ and $\sin\theta$.
- It makes the polar rules automatic: $e^{\mathrm ja}e^{\mathrm jb}=e^{\mathrm j(a+b)}$.
- **Consequences**:
  - De Moivre's theorem;
  - complex trig and log functions;
  - $\cos\mathrm jy=\cosh y$;
  - the ODE solution $e^{(\alpha\pm\mathrm j\beta)t}=e^{\alpha t}(\cos\beta t\pm\mathrm j\sin\beta t)$ ([[Auxiliary Equation]]).
- **Engineering**: AC phasors $Ve^{\mathrm j\omega t}$ ([[Phasor Representation]]).

## Examples
- $e^{\mathrm j\pi}=-1$.
- $\cos\alpha$ and $\sin\alpha$ in exponential form (Specimen Test 5, Q5).

## Related
- Topics: [[MATH1054 M05 - Complex Numbers I]] · [[MATH1054 M22 - Complex Numbers II]]
- Concepts: [[Complex Numbers - Cartesian, Polar and Exponential Forms]] · [[Hyperbolic Functions]] · [[Phasor Representation]] · [[Auxiliary Equation]]

## Sources
- James, Modern Engineering Mathematics (6th ed.) §3.2.8
- MATH1054 Module Booklet, Module 5
