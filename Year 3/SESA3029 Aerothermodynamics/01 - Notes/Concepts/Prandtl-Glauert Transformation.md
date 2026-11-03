---
title: "Prandtl-Glauert Transformation"
module: "SESA3029 Aerothermodynamics"
type: concept
stream: "Block 4: High-speed aerodynamics"
aliases: ["Prandtl-Glauert transformation", "Prandtl–Glauert rule", "Prandtl-Glauert correction", "compressibility correction", "Karman-Tsien", "Kármán–Tsien rule", "von Karman-Tsien correction", "transonic aerofoil theory"]
tags: [sesa3029, concept, compressible-flow, subsonic, compressibility-correction]
status: complete
parent_lectures: ["[[SESA3029 W07b - Compressible Potential Flow and the Prandtl-Glauert Transformation]]"]
related_concepts: ["[[Linearised Compressible Potential Equation]]", "[[Critical Mach Number]]", "[[Ackeret Theory]]"]
sources: ["02 - Sources/Lectures/Lecture4-4.pdf"]
---

# Prandtl-Glauert Transformation

The Prandtl–Glauert transformation turns the subsonic linearised potential equation $\beta^2\phi_{xx}+\phi_{yy}=0$, with $\beta=\sqrt{1-M_\infty^2}$, into Laplace's equation by the change of variables $\phi_0=\beta\phi$, $x_0=x$, $y_0=\beta y$ (4.4 slide 2). The incompressible solution $\phi_0$ is therefore the compressible one in disguise, and the pressure coefficients are related by

$$
C_p=\frac{C_{p0}}{\sqrt{1-M_\infty^2}},\qquad C_l=\frac{C_{l0}}{\sqrt{1-M_\infty^2}},\qquad C_m=\frac{C_{m0}}{\sqrt{1-M_\infty^2}} .
$$

So any incompressible result (thin-aerofoil theory, a panel method, a low-speed test) is corrected for compressibility by dividing by $\sqrt{1-M_\infty^2}$. Because $C_l$ and $C_m$ scale together, the aerodynamic centre stays at $c/4$. The rule compares the same aerofoil at two Mach numbers: thin-aerofoil theory applies the tangency condition at $y=0$, where the stretch of $y$ has no effect on the slope.

Physically, compressibility makes the disturbance at the surface $1/\beta$ times stronger and makes it reach $1/\beta$ times further from the body. The rule fails near $M_\infty=1$, where it predicts infinite lift. The course quotes $M_\infty<0.8$ and calls this range "transonic aerofoil theory"; textbooks call it subsonic compressible flow.

The Kármán–Tsien rule is more accurate at higher subsonic Mach numbers (4.4 slide 10):

$$
C_p=\frac{C_{p0}}{\sqrt{1-M_\infty^2}+\dfrac{M_\infty^2}{1+\sqrt{1-M_\infty^2}}\,\dfrac{C_{p0}}{2}} .
$$

## Related

- [[SESA3029 W07b - Compressible Potential Flow and the Prandtl-Glauert Transformation#6. The Prandtl–Glauert transformation (4.4 slides 2–3)|W07b §§6–9]]
- [[Linearised Compressible Potential Equation]] · [[Critical Mach Number]] · [[Ackeret Theory]] (the supersonic counterpart)
- [[SESA2022 T4 - Thin Aerofoil Theory]] (the incompressible $C_{p0}$)
