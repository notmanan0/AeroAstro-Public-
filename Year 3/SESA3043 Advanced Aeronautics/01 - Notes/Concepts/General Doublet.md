---
title: "General Doublet"
module: "SESA3043 Advanced Aeronautics"
type: concept
stream: "Chapter 1: Conservation Laws"
aliases: ["doublet at angle nu", "general doublet", "inclined doublet", "dipole"]
tags: [sesa3043, concept, potential-flow, doublet]
status: complete
parent_lectures: ["[[SESA3043 1.3 - Complex Potential, Wedge Flows and Unsteady Bernoulli]]"]
related_concepts: ["[[Complex Velocity Potential]]", "[[Elementary Potential Flows]]", "[[Panel Method]]"]
sources: ["02 - Sources/Lectures/CH1-3 Potential Flow.pdf"]
---

# General Doublet

A general doublet is the limit of a sink $-m$ at the origin and a source $+m$ at $le^{i\nu}$ as $l\to0$ with $\mu=ml$ held fixed:

$$\Phi=-\frac{\mu}{2\pi}\frac{e^{i\nu}}{z},\qquad u=\frac{\mu\cos(2\theta-\nu)}{2\pi r^2},\quad v=\frac{\mu\sin(2\theta-\nu)}{2\pi r^2}.$$

The derivation takes a couple of lines. The pair has $\Phi=\frac{m}{2\pi}\ln\left(1-\frac{le^{i\nu}}{z}\right)$, and for small $l$, $\ln(1-\varepsilon)\approx-\varepsilon$ gives $\Phi\approx-\frac{ml}{2\pi}\frac{e^{i\nu}}{z}$. Differentiating, $\mathrm d\Phi/\mathrm dz=\frac{\mu}{2\pi}e^{i\nu}z^{-2}=\frac{\mu}{2\pi r^2}e^{-i(2\theta-\nu)}$.

With $\nu=\pi$ (source upstream) this is the doublet in the standard tables, $\Phi=\mu/(2\pi z)$ and $\phi=\mu\cos\theta/(2\pi r)$. With $\nu=\pi/2$, pointing in $+z$, it is the element used in a doublet panel. Adding a uniform stream aligned with the doublet gives flow past a cylinder of radius $\sqrt{\mu/2\pi U}$.

![[aa_general_doublet.png|700]]

## Related

- [[SESA3043 1.3 - Complex Potential, Wedge Flows and Unsteady Bernoulli#5. The general doublet (derivation)]] · [[Panel Method]] · [[Complex Velocity Potential]]
