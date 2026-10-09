---
title: "Aerodynamic Centre and Centre of Pressure"
module: "SESA2022 Aerodynamics"
type: concept
stream: "Topic 4: Thin Aerofoil Theory"
aliases: ["aerodynamic centre", "centre of pressure", "AC", "CP", "quarter chord"]
tags: [sesa2022, concept, thin-aerofoil-theory]
status: complete
parent_lectures: ["[[SESA2022 T4 - Thin Aerofoil Theory]]"]
related_concepts: ["[[Trailing-Edge Flap in Thin Aerofoil Theory]]", "[[Neutral Point and Static Margin]]"]
sources: ["02 - Sources/Airfoils and Wings/Topic 4 Thin airfoil theory_v3.pdf"]
---

# Aerodynamic Centre and Centre of Pressure

## Definition

> [!note] Definition
> - **Centre of pressure** $x_{cp}$: the point about which the aerodynamic moment is **zero**, i.e. where the resultant force acts. It moves with $\alpha$.
> - **Aerodynamic centre** $x_{ac}$: the point about which the moment is **independent of $\alpha$**. In TAT, $x_{ac} = c/4$.

## Explanation
**TAT results** (moments nose-up positive):

$$
C_{m,LE} = -\frac\pi2\left(A_0+A_1-\frac{A_2}{2}\right) = C_{m,c/4}-\frac{C_l}{4},\qquad C_{m,c/4} = \frac\pi4(A_2-A_1)
$$

$C_{m,c/4}$ depends only on camber ($A_1$, $A_2$), not on $\alpha$, so $c/4$ is the AC.

**Centre of pressure**:

$$
\frac{x_{cp}}{c} = -\frac{C_{m,LE}}{C_l} = \frac14-\frac{C_{m,c/4}}{C_l}
$$

- **Symmetric aerofoil**: $C_{m,c/4} = 0$, so the CP stays at $c/4$.
- **Positive camber**: $C_{m,c/4}<0$ (nose-down). The CP lies **aft** of $c/4$ and moves further aft as $C_l\to0$, heading to infinity at zero lift. That's why the constant AC moment is the preferred way to describe aerofoil loads.
- **Moment transfer**: $C_{m,x_1} = C_{m,x_2}+C_l\frac{x_1-x_2}{c}$ (with $x$ measured aft and nose-up positive).
- For **real aerofoils** the AC is at about $0.23$–$0.25c$ subsonic, moving to about $0.5c$ supersonic.

## Examples
- $x_{cp}$ for a NACA 2412-type section: [[SESA2022 Exam 2020-21 Solutions]] B Q3.
- $C_{m,LE}$ and $x_{cp} = 0.3154c$: [[SESA2022 Exam 2021-22 Solutions]] B Q1.
- $C_{m,c/4}$ against $\alpha$ is a horizontal line: [[SESA2022 Exam 2018-19 Solutions]] Q2(iv).
- Trimming tandem wings: [[SESA2022 Exam 2017-18 Solutions]] Q2.

## Related
- Parent lectures: [[SESA2022 T4 - Thin Aerofoil Theory]]
- Related concepts: [[Trailing-Edge Flap in Thin Aerofoil Theory]], [[Neutral Point and Static Margin]]

## Sources
- `02 - Sources/Airfoils and Wings/Topic 4 Thin airfoil theory_v3.pdf`
