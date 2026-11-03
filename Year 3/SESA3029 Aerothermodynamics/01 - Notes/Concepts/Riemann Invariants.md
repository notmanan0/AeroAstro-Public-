---
title: "Riemann Invariants"
module: "SESA3029 Aerothermodynamics"
type: concept
stream: "Block 3: Nozzles and the Method of Characteristics"
aliases: ["Riemann invariant", "compatibility conditions", "compatibility condition", "compatibility relations", "compatibility equations", "characteristic invariants", "R+ and R-", "K+ and K-"]
tags: [sesa3029, concept, method-of-characteristics, riemann-invariants]
status: complete
parent_lectures: ["[[SESA3029 W05a - Method of Characteristics]]"]
related_concepts: ["[[Method of Characteristics]]", "[[Prandtl-Meyer Function]]", "[[Homentropic Flow]]"]
sources: ["02 - Sources/Lectures/Lecture3-1.pdf", "02 - Sources/Lectures/Lecture3-2.pdf", "02 - Sources/Lectures/Supplementary Note for MoC.pdf", "02 - Sources/Lectures/Lecture 3-1.txt", "02 - Sources/Lectures/Lecture 3-2.txt", "02 - Sources/Lectures/Lecture 3-3.txt"]
---

# Riemann Invariants

In SESA3029's convention the Riemann invariants are

$$R^+=\nu-\theta\quad\text{constant along a }C^+\text{ characteristic},\qquad R^-=\nu+\theta\quad\text{constant along a }C^-\text{ characteristic},$$

where $\nu$ is the [[Prandtl-Meyer Function|Prandtl–Meyer angle]] and $\theta$ is the flow inclination to the $x$-axis. The two statements together are the **compatibility conditions**.

## Where they come from

The full derivation is in [[SESA3029 W05a - Method of Characteristics#7. Compatibility conditions and Riemann invariants (3.1 slides 9–12)|W05a §7]]. Applying mass, $l$-momentum, homentropy and zero vorticity to a streamtube gives two PDEs in $\nu$ and $\theta$:

$$\partial\nu/\partial l-\tan\mu\,\partial\theta/\partial n=0,\qquad\partial\theta/\partial l-\tan\mu\,\partial\nu/\partial n=0.$$

Subtracting and adding them gives $\partial(\nu\mp\theta)/\partial l\pm\tan\mu\,\partial(\nu\mp\theta)/\partial n=0$. The left-hand side is the rate of change along a line at $\pm\mu$ to the flow, which is a Mach line, so $\nu\mp\theta$ does not change along it. Diagonalising the $2\times2$ system gives the same thing: $\hat R=\underline E^{-1}[\nu,\theta]^T=[\nu-\theta,\ \nu+\theta]^T$.

> [!warning] No factor of a half in the definitions (L3-3, ll. 28–31)
> The recording once says *"R plus is nu minus theta over 2"*. The invariants are $R^\pm=\nu\mp\theta$; the $\tfrac12$ only appears when you solve back for $\nu$ and $\theta$. Elsewhere (L3-1, ll. 338–343) it says *"mu minus theta is preserved"*, which should be nu minus theta.

## Using them

Where two characteristics cross, their invariants fix the state:

$$
\nu=\tfrac12(R^++R^-),\qquad\theta=\tfrac12(R^--R^+).
$$

More generally, $R^+$, $R^-$, $\nu$ and $\theta$ are linked by two equations, so any two of them fix the other two (L3-3, ll. 32–36). At a wall, one invariant arrives along its line and the wall supplies $\theta$. On the centreline, $\theta=0$.

Where one invariant is the same everywhere, for example $R^+$ throughout a Prandtl–Meyer fan fed by uniform flow, the region is a **simple flow region** (L3.3 slides 8 and 10; textbooks say simple-wave region). Then $\nu-\theta=\nu_1$, which is just $\nu_2=\nu_1+\theta$ from W03.

Anderson uses $K^+=-R^+=\theta-\nu$ and $K^-=R^-=\theta+\nu$. The physics is the same; the SESA3029 signs follow Liepmann & Roshko. Pick one and stick to it.

![[at_moc_characteristic_geometry.png|760]]

## Related

- [[Method of Characteristics]] · [[Prandtl-Meyer Function]] · [[Homentropic Flow]]
- Practice: [[SESA3029 Example Sheet 2 - Solutions#Q2. Characteristics and Riemann invariants|ES2 Q2]]
