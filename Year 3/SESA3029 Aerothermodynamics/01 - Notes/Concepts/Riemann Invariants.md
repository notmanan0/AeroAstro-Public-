---
title: "Riemann Invariants"
module: "SESA3029 Aerothermodynamics"
type: concept
stream: "Block 3: Nozzles and the Method of Characteristics"
aliases: ["Riemann invariant", "compatibility conditions", "compatibility condition", "R+ and R-", "K+ and K-"]
tags: [sesa3029, concept, method-of-characteristics, riemann-invariants]
status: complete
parent_lectures: ["[[SESA3029 W05 - Method of Characteristics and Minimum-Length Nozzle Design]]"]
related_concepts: ["[[Method of Characteristics]]", "[[Prandtl-Meyer Function]]", "[[Homentropic Flow]]"]
sources: ["02 - Sources/Lectures/Lecture3-1.pdf", "02 - Sources/Lectures/Lecture3-2.pdf", "02 - Sources/Lectures/Supplementary Note for MoC.pdf", "02 - Sources/Lectures/Lecture 3-1.txt", "02 - Sources/Lectures/Lecture 3-2.txt", "02 - Sources/Lectures/Lecture 3-3.txt"]
---

# Riemann Invariants

## Definition

> [!note] Definition (SESA3029 convention)
> $$R^+=\nu-\theta\quad\text{is constant along a }C^+\text{ characteristic},\qquad R^-=\nu+\theta\quad\text{is constant along a }C^-\text{ characteristic}.$$
>
> $\nu$ is the [[Prandtl-Meyer Function|Prandtl–Meyer angle]] and $\theta$ the flow inclination to the $x$-axis. These two statements are the **compatibility conditions**.

## Explanation

**Derivation, in outline** (full version in [[SESA3029 W05 - Method of Characteristics and Minimum-Length Nozzle Design#7. Compatibility conditions and Riemann invariants (3.1 slides 9–12)|W05 §7]]):

1. Mass, $l$-momentum, homentropy and zero vorticity on a streamtube give two PDEs in $\nu$ and $\theta$:
   $$\partial\nu/\partial l-\tan\mu\,\partial\theta/\partial n=0,\qquad\partial\theta/\partial l-\tan\mu\,\partial\nu/\partial n=0.$$
2. Subtracting and adding them gives $\partial(\nu\mp\theta)/\partial l\pm\tan\mu\,\partial(\nu\mp\theta)/\partial n=0$.
3. The bracket is the rate of change along a line at $\pm\mu$ to the flow, i.e. along a Mach line.

The same result comes from diagonalising the $2\times2$ system: $\hat R=\underline E^{-1}[\nu,\theta]^T=[\nu-\theta,\ \nu+\theta]^T$.

**Using them.** Two crossing lines give the state at the crossing:

$$
\nu=\tfrac12(R^++R^-),\qquad\theta=\tfrac12(R^--R^+).
$$

More generally, the four numbers $R^+$, $R^-$, $\nu$ and $\theta$ are linked by two equations, so **any two fix the other two** (L3-3, ll. 32–36). At a wall, one invariant comes in along its line and the wall gives $\theta$. On the centreline, $\theta=0$.

> [!warning] No factor of a half in the definitions (L3-3, ll. 28–31)
> The recording once says *"R plus is nu minus theta over 2"*. The invariants are $R^\pm=\nu\mp\theta$. The $\tfrac12$ appears only when you solve back for $\nu$ and $\theta$.

**Other notation.** Anderson uses $K^+=-R^+=\theta-\nu$ and $K^-=R^-=\theta+\nu$. The physics is identical; pick one and stay consistent. The SESA3029 signs follow Liepmann & Roshko.

**Simple regions.** Where one invariant is the same everywhere, for example $R^+$ through a Prandtl–Meyer fan fed by uniform flow, the region is **simple**. Then $\nu-\theta=\nu_1$ reproduces $\nu_2=\nu_1+\theta$ from W03.

> [!warning] Transcript slip (L3-1, ll. 338–343)
> The recording says *"mu minus theta is preserved"*. It is **nu** minus theta.

![[at_moc_characteristic_geometry.png|760]]

## Related

- [[Method of Characteristics]] · [[Prandtl-Meyer Function]] · [[Homentropic Flow]]
- Practice: [[SESA3029 Example Sheet 2 - Solutions#Q2. Characteristics and Riemann invariants|ES2 Q2]]
