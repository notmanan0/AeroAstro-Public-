---
title: "Figure of Merit"
module: "SESA3043 Advanced Aeronautics"
type: concept
stream: "Chapter 4: Rotor Aerodynamics"
aliases: ["FM", "rotor figure of merit", "hover efficiency", "hovering efficiency"]
tags: [sesa3043, concept, rotor, hover, performance]
status: complete
parent_lectures: ["[[SESA3043 4.1 - Rotor in Hover]]"]
related_concepts: ["[[Rotor Thrust and Power Coefficients]]", "[[Blade Element Theory]]", "[[Induced Power Factor]]"]
sources: ["02 - Sources/Lectures/CH4 Rotor Aerodynamics.pdf"]
---

# Figure of Merit

The figure of merit (FM) is the hover efficiency of a rotor: the ideal induced power of an actuator disc producing the same thrust, divided by the actual rotor power.

With the blade-element power coefficient $C_P=C_T\lambda_i+sC_{D0}/4$ and the hover inflow $\lambda_i=\sqrt{C_T}/2$ ([[SESA3043 4.1 - Rotor in Hover#11. Coefficients and the figure of merit|4.1 §11]]),

$$
\mathrm{FM}=\frac{C_T\lambda_i}{C_T\lambda_i+sC_{D0}/4}=\frac{C_T^{3/2}}{C_T^{3/2}+sC_{D0}/2}.
$$

FM = 1 would mean no profile drag and uniform inflow; most rotors lie between 0.7 and 0.8. High solidity $s$ (more blades, longer chord) raises the profile power and lowers FM, and low-drag aerofoils or low solidity raise it. Because induced power grows as $C_T^{3/2}$ while profile power is fixed by $sC_{D0}$, FM rises with thrust coefficient, so rotors should only be compared by FM at the same disc loading. A Lynx-sized rotor at $C_T=0.0139$ with $s=0.08$ and $C_{D0}=0.01$ has FM = 0.80.

This formula takes the induced power as ideal. Including the [[Induced Power Factor]], $\mathrm{FM}=\dfrac{C_T^{3/2}/2}{k_iC_T^{3/2}/2+sC_{D0}/4}$, which for the same rotor with $k_i=1.077$ gives 0.76.

## Related

- Parent lecture: [[SESA3043 4.1 - Rotor in Hover]]
- Related concepts: [[Rotor Thrust and Power Coefficients]] · [[Blade Element Theory]] · [[Induced Power Factor]] · [[Hover Induced Velocity and Disc Loading]]
