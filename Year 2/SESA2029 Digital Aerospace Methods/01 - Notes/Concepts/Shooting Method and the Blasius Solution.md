---
title: "Shooting Method and the Blasius Solution"
module: "SESA2029 Digital Aerospace Methods"
type: concept
stream: "Part A: Computational Fluid Dynamics"
aliases: ["Blasius equation", "shooting method", "similarity solution", "laminar flat plate"]
tags: [sesa2029, concept, numerical-methods, boundary-layers]
status: complete
parent_lectures: ["[[SESA2029 A6 - Higher-Order Time Integration, Runge-Kutta and the Blasius Equation]]"]
related_concepts: ["[[Runge-Kutta Methods]]", "[[Law of the Wall]]", "[[Displacement and Momentum Thickness]]"]
sources: ["02 - Sources/CFD/All_lectures_as_delivered.pdf (L7)", "02 - Sources/CFD/CFD.txt"]
---

# Shooting Method and the Blasius Solution

## Definition

> [!note] Definition
> The **Blasius equation** $f'''+ff'' = 0$ gives the similarity profile $u/U_e = f'(\eta)$ of a laminar flat-plate boundary layer, with $\eta = y/\delta$ and $\delta = \sqrt{2\nu x/U_e}$. It has no analytic solution. The **shooting method** turns this boundary-value problem into an initial-value problem: guess the missing wall value $f''(0)$, integrate outward, and correct the guess until the far-field condition $f'(\infty) = 1$ is met.

## Explanation

- **Boundary conditions**: $f(0) = 0$ (the wall is a streamline), $f'(0) = 0$ (no slip), $f'(\infty) = 1$. Two are at the wall and one at infinity.
- **First-order system**: $f_0' = f_1$, $f_1' = f_2$, $f_2' = -f_0f_2$. Integrate with RK45 to $\eta_{max}\approx6$–8, which stands in for infinity.
- Adjust $f''(0)$ like the elevation of a cannon: 0.3 under-shoots ($f'(8) = 0.742$) and 0.6 over-shoots (1.177). The answer is $f''(0) = 0.4696$. A root-finder can automate this.
- **Results**: $\delta^* = 1.7208\,x/\sqrt{Re_x}$, $\theta = 0.664\,x/\sqrt{Re_x}$, $H = 2.591$, $\delta_{99}\approx4.91\,x/\sqrt{Re_x}$ and $C_f = 0.664/\sqrt{Re_x}$.
- **Check the numerical parameters**: $\eta_{max} = 4$ is too small, and too few output points bias the trapezoid integrals.
- **Physics**: Prandtl (1904) introduced the boundary layer, which resolved [[D'Alembert's Paradox]]. Blasius (1907) assumed a self-similar profile.

## Examples

![[dam_blasius_shooting.png|480]]

- A laminar Navier–Stokes CFD solution of a flat plate, plotted as $u/U_e$ against $y/\delta^*$, should collapse onto the Blasius curve at every station once developed.

## Related

- Parent lectures: [[SESA2029 A6 - Higher-Order Time Integration, Runge-Kutta and the Blasius Equation]]
- Related concepts: [[Runge-Kutta Methods]] · [[Law of the Wall]] · [[Displacement and Momentum Thickness]]
- Boundary layers: [[SESA2022 T2 - Boundary Layers]]

## Sources

- 02 - Sources/CFD/All_lectures_as_delivered.pdf (L7)
- 02 - Sources/CFD/CFD.txt
