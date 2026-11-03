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

A **minimum-length nozzle** is the shortest planar supersonic nozzle that delivers uniform, shock-free flow at $M_e$. All of the expansion happens in a Prandtl–Meyer fan at a sharp expansion corner at the throat, and the wall downstream is shaped to be non-reflecting, so every wave that reaches it is cancelled. Its maximum slope, at the corner, is

$$
\theta_{max}=\frac{\nu(M_e)}{2}.
$$

The factor of a half comes from the invariants. The throat is sonic, so $\nu=0$ there, and the fan at the corner C takes the flow to $\nu_C=\theta_{max}$. The last line of the fan is a $C^-$ carrying $R^-=\nu+\theta=2\theta_{max}$. It ends on the centreline at the first point of uniform flow, where $\theta=0$ and $\nu=\nu(M_e)$, so $2\theta_{max}=\nu(M_e)$.

Because it is the shortest design it is also likely the lightest, which matters for rockets and launchers. Real nozzles round the expansion corner slightly.

## Regions

The course names three regions (L3.3 slides 8 and 10, Supplementary Note p. 10). The **complex region** sits behind the expansion corner, where both families of characteristics cross; textbooks call it the kernel or a non-simple region. The **simple flow region** lies next to the designed wall and has *"characteristics from one direction only"* (a simple-wave region in textbooks). Beyond both is the **uniform flow region**, with $M=M_e$ and $\theta=0$.

## Designing one

1. Set $\theta_{max}=\nu(M_e)/2$.
2. Choose $n$ lines of the expansion fan, from a small $\delta$ (not zero) up to $\theta_{max}$. On each one $\nu=\theta$, so $R^-=2\theta$.
3. Apply the unit process, treating the centreline as a mirror and the wall as non-reflecting.
4. Compute the coordinates from left to right.

With $n$ lines the net has $n(n+3)/2$ points, $n$ of them on the wall: 14 for $n=4$ and 20 for $n=5$.

For $M_e=2.4$ (3.3 slides 11–21), $\theta_{max}=18.373^\circ$. Four lines starting at $0.375^\circ$ put the exit at $x_e/r_a=8.069$, $y_e/r_a=2.400$. Lengths are scaled by $r_a$, *"the nozzle throat's half-width"* (slide 21), so $y_e/r_a$ is the exit half-width.

> [!check] Built-in check
> Mass conservation requires $y_e/r_a\to A_e/A^*$, here $2.4031$. MoC gives $2.4003$ with four lines and $2.4028$ with 300. 1D theory gives the exit half-width but not the length; that is what MoC adds.

The MoC coursework uses $n=5$ lines from $0.125^\circ$, with $M_e=3.x$ where $x$ is the last digit of your student ID, for CO₂ with $\gamma=1.289$. It is due 23:59 on Sunday 15 November (L3-4, ll. 367–418; [[SESA3029 W05b - Minimum-Length Nozzle Design#Announcements and deadlines|W05b]]).

> [!warning] $\theta_{max}=\nu(M_e)/2$ holds for any γ, but ν depends on γ
> At $\gamma=1.289$ the IFT (built for $\gamma=1.4$) gives the wrong $\nu$, $\theta_{max}$ and $A_e/A^*$. Use the general-$\gamma$ formulas. Only $\mu=\sin^{-1}(1/M)$ is the same for every gas.

## Reading the exit Mach number off the throat

Measure the wall's maximum slope at the throat and $\nu(M_e)=2\theta_{max}$ gives the design Mach number without a wind tunnel (L3-3, ll. 204–214). A slope of $26.74^\circ$, for example, means $M_e=3.20$.

This $\theta_{max}$ is the largest wall slope, not the oblique-shock maximum deflection (L3-3, ll. 137–139). It also only works for a sharp-corner design. In a gradual-expansion nozzle the flow at the slope maximum has already been expanded by reflected waves, so $\theta_{max}\le\nu(M_e)/2$ and the trick underestimates $M_e$ ([[SESA3029 W05b - Minimum-Length Nozzle Design#13. The minimum-length nozzle (3.3 slide 10)|W05b §13]]).

![[at_moc_mach_angle_throat_angle.png|760]]

![[at_moc_min_length_nozzle.png|760]]

## Related

- [[Method of Characteristics]] · [[Riemann Invariants]] · [[Prandtl-Meyer Function]] · [[Isentropic Nozzle Flow]] · [[Over- and Under-Expanded Jets]]
- Detail: [[SESA3029 W05b - Minimum-Length Nozzle Design#13. The minimum-length nozzle (3.3 slide 10)|W05b §13–14]]
