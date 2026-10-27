---
title: "Minimum-Length Nozzle"
module: "SESA3029 Aerothermodynamics"
type: concept
stream: "Block 3: Nozzles and the Method of Characteristics"
aliases: ["minimum length nozzle", "minimum-length nozzle design", "MLN", "sharp-corner nozzle", "theta max", "maximum slope", "maximum wall angle", "complex region", "kernel", "non-simple region", "simple flow region", "simple region", "simple-wave region", "uniform flow region", "throat half-width", "throat half-height", "expansion corner", "throat corner"]
tags: [sesa3029, concept, nozzle-design, method-of-characteristics]
status: complete
parent_lectures: ["[[SESA3029 W05b - Minimum-Length Nozzle Design]]"]
related_concepts: ["[[Method of Characteristics]]", "[[Riemann Invariants]]", "[[Prandtl-Meyer Function]]", "[[Isentropic Nozzle Flow]]"]
sources: ["02 - Sources/Lectures/Lecture3-3.pdf", "02 - Sources/Lectures/Supplementary Note for MoC.pdf", "02 - Sources/Lectures/Lecture 3-3.txt", "02 - Sources/Lectures/Lecture 3-4.txt"]
---

# Minimum-Length Nozzle

## Definition

> [!note] Definition
> The shortest planar supersonic nozzle that delivers **uniform, shock-free** flow at $M_e$. All the expansion happens in a Prandtl–Meyer expansion fan at a sharp expansion corner at the throat. The wall downstream is designed to be **non-reflecting**, so every wave that reaches it is cancelled, and the wall's maximum slope is
>
> $$\theta_{max}=\frac{\nu(M_e)}{2}.$$

## Explanation

**Why half.** The sonic throat has $\nu=0$, so the expansion fan at the corner C gives $\nu_C=\theta_{max}$, and the last line of the fan, a $C^-$, carries $R^-=2\theta_{max}$. That line ends on the centreline at the first uniform-flow point, where $\theta=0$ and $\nu=\nu(M_e)$. Equal invariants give $2\theta_{max}=\nu(M_e)$.

**Regions** (course names; L3.3 slides 8 and 10, Supplementary Note p. 10).

- **Complex region**: both families cross, behind the expansion corner (textbooks call it the *kernel* or a *non-simple region*).
- **Simple flow region**: *"characteristics from one direction only"*, next to the designed wall (textbooks: *simple-wave region*).
- **Uniform flow region**: $M=M_e$, $\theta=0$.

**Design recipe.**

1. $\theta_{max}=\nu(M_e)/2$.
2. Pick $n$ lines of the expansion fan, from a small $\delta$ (not 0) to $\theta_{max}$. On each, $\nu=\theta$ and $R^-=2\theta$.
3. Apply the unit process, with the centreline as a mirror and the wall non-reflecting.
4. Compute the coordinates left to right.

**Numbers for $M_e=2.4$** (3.3 slides 11–21): $\theta_{max}=18.373^\circ$. With four lines from $0.375^\circ$, the exit is at $x_e/r_a=8.069$, $y_e/r_a=2.400$.

> [!check] Built-in check
> Mass conservation forces $y_e/r_a\to A_e/A^*$, here $2.4031$. MoC gives $2.4003$ with four lines and $2.4028$ with 300. 1D theory gives the exit half-width but cannot give the length.

Lengths are scaled by $r_a$, *"the nozzle throat's half-width"* (slide 21), so $y_e/r_a$ is the exit half-width.

**Point count.** With $n$ lines in the expansion fan the net has $n(n+3)/2$ points, $n$ of them on the wall: 14 for $n=4$, 20 for $n=5$. The MoC coursework uses $n=5$ lines from $0.125^\circ$ and $M_e=3.x$, where $x$ is the last digit of the student ID, for **CO₂ with $\gamma=1.289$**. It is due 23:59, Sun 15 Nov (L3-4, ll. 367–418; [[SESA3029 W05b - Minimum-Length Nozzle Design#Announcements and deadlines|W05b]]).

> [!warning] $\theta_{max}=\nu(M_e)/2$ holds for any $\gamma$, but $\nu$ itself depends on $\gamma$
> With $\gamma=1.289$ the IFT ($\gamma=1.4$) gives the wrong $\nu$, $\theta_{max}$ and $A_e/A^*$. Compute them from the general-$\gamma$ formulas instead. Only $\mu=\sin^{-1}(1/M)$ is the same for every gas.

**Why use it.** It is the shortest design, so it is likely the lightest. That matters for rockets and launchers. In practice the expansion corner is rounded slightly.

**The exit Mach number from the throat** (L3-3, ll. 204–214). Measure the wall's maximum slope at the throat and $\nu(M_e)=2\theta_{max}$ gives the design Mach number, with no wind tunnel needed. For example, $26.74^\circ$ gives $M_e=3.20$.

> [!warning] Two things this $\theta_{max}$ is not
> - It is **not** the oblique-shock maximum deflection. It is the largest wall slope (L3-3, ll. 137–139).
> - It does **not** give $M_e$ for a gradual-expansion nozzle. There the flow at the slope maximum has already been expanded by reflected waves, so $\theta_{max}\le\nu(M_e)/2$ ([[SESA3029 W05b - Minimum-Length Nozzle Design#13. The minimum-length nozzle (3.3 slide 10)|W05b §13]]).

![[at_moc_mach_angle_throat_angle.png|760]]

![[at_moc_min_length_nozzle.png|760]]

## Related

- [[Method of Characteristics]] · [[Riemann Invariants]] · [[Prandtl-Meyer Function]] · [[Isentropic Nozzle Flow]] · [[Over- and Under-Expanded Jets]]
- Detail: [[SESA3029 W05b - Minimum-Length Nozzle Design#13. The minimum-length nozzle (3.3 slide 10)|W05b §13–14]]
