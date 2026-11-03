---
title: "Aerodynamic Centre and Centre of Pressure"
module: "SESA2022 Aerodynamics"
type: concept
stream: "Topic 4: Thin Aerofoil Theory"
aliases: ["aerodynamic centre", "centre of pressure", "AC", "CP", "quarter chord", "aerodynamic center", "center of pressure"]
tags: [sesa2022, concept, thin-aerofoil-theory]
status: complete
parent_lectures: ["[[SESA2022 T4 - Thin Aerofoil Theory]]"]
related_concepts: ["[[Trailing-Edge Flap in Thin Aerofoil Theory]]", "[[Neutral Point and Static Margin]]"]
sources: ["02 - Sources/Airfoils and Wings/Topic 4 Thin airfoil theory_v3.pdf", "02 - Sources/Lectures/SESA2022 Lecture 2025-10-28.txt … 2025-11-05.txt (2025-26 transcripts)"]
---

# Aerodynamic Centre and Centre of Pressure

The **centre of pressure** $x_{cp}$ is the point about which the aerodynamic moment is zero, where the resultant force acts; it moves with $\alpha$. The **aerodynamic centre** $x_{ac}$ is the point about which the moment doesn't change with $\alpha$, and thin aerofoil theory puts it at $c/4$.

With moments positive nose-up, thin aerofoil theory gives

$$
C_{m,LE} = -\frac\pi2\left(A_0+A_1-\frac{A_2}{2}\right) = C_{m,c/4}-\frac{C_l}{4},\qquad C_{m,c/4} = \frac\pi4(A_2-A_1).
$$

$C_{m,c/4}$ depends only on the camber coefficients $A_1$ and $A_2$, not on $\alpha$, which is what makes $c/4$ the aerodynamic centre. The centre of pressure follows from the moment about the leading edge:

$$
\frac{x_{cp}}{c} = -\frac{C_{m,LE}}{C_l} = \frac14-\frac{C_{m,c/4}}{C_l} .
$$

For a symmetric aerofoil $C_{m,c/4} = 0$ and the centre of pressure stays at $c/4$. With positive camber $C_{m,c/4}<0$ (nose-down), so the centre of pressure lies aft of $c/4$ and runs further aft as $C_l\to0$, heading to infinity at zero lift. That is why aerofoil loads are described by the lift at the aerodynamic centre plus a constant moment, rather than by a moving centre of pressure. To move a moment from one point to another, $C_{m,x_1} = C_{m,x_2}+C_l(x_1-x_2)/c$, with $x$ measured aft and nose-up positive. On real aerofoils the aerodynamic centre sits at about $0.23$–$0.25c$ in subsonic flow and moves to about $0.5c$ supersonically.

Past-paper uses: $x_{cp}$ for a NACA 2412-type section ([[SESA2022 Exam 2020-21 Solutions]] B Q3); $C_{m,LE}$ and $x_{cp} = 0.3154c$ ([[SESA2022 Exam 2021-22 Solutions]] B Q1); $C_{m,c/4}$ against $\alpha$ as a horizontal line ([[SESA2022 Exam 2018-19 Solutions]] Q2(iv)); trimming tandem wings ([[SESA2022 Exam 2017-18 Solutions]] Q2).

## Related

- Full derivation and worked examples: [[SESA2022 T4 - Thin Aerofoil Theory#6. Moments, aerodynamic centre, centre of pressure (4 Nov lecture)|T4 §6]]
- [[Trailing-Edge Flap in Thin Aerofoil Theory]] · [[Neutral Point and Static Margin]]
