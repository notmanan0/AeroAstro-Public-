---
title: "Method of Characteristics"
module: "SESA3029 Aerothermodynamics"
type: concept
stream: "Block 3: Nozzles and the Method of Characteristics"
aliases: ["MoC", "method of characteristics", "MoC unit process", "unit process"]
tags: [sesa3029, concept, method-of-characteristics, supersonic, nozzle-design]
status: complete
parent_lectures: ["[[SESA3029 W05a - Method of Characteristics]]", "[[SESA3029 W05b - Minimum-Length Nozzle Design]]"]
related_concepts: ["[[Riemann Invariants]]", "[[Homentropic Flow]]", "[[Minimum-Length Nozzle]]", "[[Prandtl-Meyer Function]]", "[[Mach Waves and Mach Angle]]"]
sources: ["02 - Sources/Lectures/Lecture3-1.pdf", "02 - Sources/Lectures/Lecture3-2.pdf", "02 - Sources/Lectures/Lecture3-3.pdf", "02 - Sources/Lectures/Supplementary Note for MoC.pdf", "02 - Sources/Lectures/Lecture 3-2.txt", "02 - Sources/Lectures/Lecture 3-3.txt", "02 - Sources/Lectures/Lecture 3-4.txt"]
---

# Method of Characteristics

## Definition

> [!note] Definition
> A way of solving steady, two-dimensional, [[Homentropic Flow|homentropic]], irrotational **supersonic** flow by marching along the Mach lines. Along each Mach line one [[Riemann Invariants|Riemann invariant]] is constant:
>
> $$R^+=\nu-\theta\ \text{along }C^+\ (\text{inclined at }\theta+\mu),\qquad R^-=\nu+\theta\ \text{along }C^-\ (\text{inclined at }\theta-\mu).$$

## Explanation

**Why it works.** The governing PDEs in $\nu$ and $\theta$ form a **hyperbolic** system, with eigenvalues $\pm\tan\mu$, only when $M>1$. Diagonalising them leaves one unknown per equation, and each one says "no change along this direction". So the flow is found by bookkeeping, not integration.

**The unit process.** A below P (its $C^+$ reaches P), B above P (its $C^-$ reaches P):

$$
\nu_P=\tfrac12\left(R^+_A+R^-_B\right),\qquad\theta_P=\tfrac12\left(R^-_B-R^+_A\right),
$$

then $M_P$ from the tables and $\mu_P=\sin^{-1}(1/M_P)$. The characteristics **bend** at every crossing, because $\mu$ changes with $M$ (L3-2, ll. 299–318). So the position uses the averaged slopes

$$
\alpha_{AP}=\tfrac12[(\theta+\mu)_A+(\theta+\mu)_P],\qquad\alpha_{BP}=\tfrac12[(\theta-\mu)_B+(\theta-\mu)_P],
$$

$$
x_P=\frac{x_B\tan\alpha_{BP}-x_A\tan\alpha_{AP}-(y_B-y_A)}{\tan\alpha_{BP}-\tan\alpha_{AP}},\qquad y_P=y_A+(x_P-x_A)\tan\alpha_{AP}.
$$

**Boundary conditions.**

| Boundary | State rule | Position rule |
|---|---|---|
| prescribed wall (reflects) | $\nu_W=R^+_A+\theta_W$; reflected $R^-_W=R^+_A+2\theta_W$ | intersect the $C^+$ with the wall |
| designed wall (cancels) | $\theta_W=\theta_A$, so $M_W=M_A$ | $\alpha_{AW}=(\theta+\mu)_A$, $\alpha_{BW}=\tfrac12(\theta_B+\theta_W)$ |
| symmetry plane (an inviscid wall with $\theta_W=0$, L3-3, l. 93) | $\theta_P=0$, $\nu_P=R^-_B$, $R^+_P=R^-_P$ | $x_P=x_B-y_B/\tan\alpha_{BP}$ |

> [!warning] Check the physics, not just the rules (L3-4, ll. 206–281)
> A prescribed wall reflects only if the arriving flow is **not** already parallel to it ($\theta_A\neq\theta_W$). In the 3.4 generic example, blind bookkeeping produces a reflection at point 3 and a point 5 that *"doesn't exist"*. *"Always think about the results, whether it makes sense or not"* ([[SESA3029 W05b - Minimum-Length Nozzle Design#15. The generic MoC example (Lecture 3.4)|W05b §15]]).

**Zones.** The characteristics through P bound its **zone of dependence** (upstream) and **zone of influence** (downstream).

**Limits.** No shocks, so entropy stays uniform, and $M>1$ everywhere. In planar flow the states do not depend on the coordinates. In axisymmetric flow they do, and the invariants change along the lines as $\partial R^\pm/\partial\eta=\sin\mu\sin\theta/r$.

**Worked**: the 3.2 slide 9 example gives $M_3=1.7039$, $\theta_3=8.9367^\circ$ and $(1.3591,\ 0.2814)$ ([[SESA3029 W05a - Method of Characteristics#Worked example (3.2 slide 9)|W05a §10]]).

![[at_moc_unit_process.png|760]]

## Related

- [[Riemann Invariants]] · [[Homentropic Flow]] · [[Minimum-Length Nozzle]] · [[Prandtl-Meyer Function]] · [[Mach Waves and Mach Angle]]
- Detail: [[SESA3029 W05a - Method of Characteristics]] (theory, unit process) · [[SESA3029 W05b - Minimum-Length Nozzle Design]] (boundary conditions, nozzle design) · Practice: [[SESA3029 Example Sheet 2 - Solutions#Q3. Flow in a symmetric 2D duct|ES2 Q3]]
- Maths: [[Eigenvalues and Eigenvectors]]
