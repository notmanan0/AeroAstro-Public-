---
title: "Rotor Thrust and Power Coefficients"
module: "SESA3043 Advanced Aeronautics"
type: concept
stream: "Chapter 4: Rotor Aerodynamics"
aliases: ["rotor thrust coefficient", "rotor power coefficient", "induced power coefficient", "inflow ratio", "non-dimensional downwash velocity", "lambda_i", "rotor standard parameters", "tip speed", "rotor tip velocity"]
tags: [sesa3043, concept, rotor, hover, non-dimensional]
status: complete
parent_lectures: ["[[SESA3043 4.1 - Rotor in Hover]]"]
related_concepts: ["[[Hover Induced Velocity and Disc Loading]]", "[[Blade Element Theory]]", "[[Figure of Merit]]"]
sources: ["02 - Sources/Lectures/CH4 Rotor Aerodynamics.pdf", "02 - Sources/Lectures/19 November 2026 at 13_51_11.txt"]
---

# Rotor Thrust and Power Coefficients

Rotor forces and powers are made non-dimensional with the tip velocity $V_T=\Omega R$ and the disc area $A=\pi R^2$. They carry a factor $\tfrac12$, like wing coefficients:

$$
C_T=\frac{T}{\tfrac12\rho V_T^2A},\qquad C_P=\frac{P}{\tfrac12\rho V_T^3A},\qquad C_{P_i}=\frac{P_i}{\tfrac12\rho V_T^3A},\qquad\lambda_i=\frac{v_i}{V_T}.
$$

They play the part $C_L$ and $C_D$ play for a wing. A wing's coefficients use the dynamic pressure of the oncoming flow; a hovering rotor has none, so the tip velocity takes its place and the rotor radius is the key length. The power coefficients carry $V_T^3$ rather than $V_T^2$ because power is force times velocity.

$\lambda_i$, the non-dimensional downwash velocity (inflow ratio), links them in hover. Dividing $v_0=\sqrt{T/2\rho A}$ by $V_T$ gives $\lambda_i=\sqrt{C_T/4}=C_T^{1/2}/2$, so $C_T=4\lambda_i^2$, and dividing $P_i=Tv_i$ by $\tfrac12\rho V_T^3A$ gives $C_{P_i}=C_T\lambda_i=C_T^{3/2}/2$ ([[SESA3043 4.1 - Rotor in Hover#6. Standard parameters|4.1 §6]]).

Blade element theory adds the rotor solidity $s=Nc/\pi R$ (blade area over disc area). For untwisted blades with uniform inflow, $C_T/sa=\theta_0/3-\lambda_i/2$, and the total power coefficient is induced plus profile, $C_P=C_T\lambda_i+\tfrac14sC_{D0}$.

The factor $\tfrac12$ matters. Leishman, Johnson and most US sources define $C_T=T/\rho A(\Omega R)^2$, half the value above, for which $\lambda_i=\sqrt{C_T/2}$ and $C_P=C_T^{3/2}/\sqrt2$ in ideal hover. Formulae must not be mixed between the two conventions. A typical helicopter has $C_T\approx0.01$–$0.02$ with the $\tfrac12$ (the Lynx at maximum take-off has 0.0139) and $\lambda_i\approx0.05$–$0.07$.

## Related

- Parent lecture: [[SESA3043 4.1 - Rotor in Hover]]
- Related concepts: [[Hover Induced Velocity and Disc Loading]] · [[Blade Element Theory]] · [[Figure of Merit]] · [[Induced Power Factor]]
