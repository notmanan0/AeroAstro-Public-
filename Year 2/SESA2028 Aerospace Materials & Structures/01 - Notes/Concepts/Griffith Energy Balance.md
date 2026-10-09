---
title: "Griffith Energy Balance"
module: "SESA2028 Aerospace Materials & Structures"
type: concept
stream: "Materials"
tags: [sesa2028, materials, fracture-mechanics, energy]
status: complete
parent: ["[[SESA2028 M1 - Fracture, Toughness and Fracture Mechanics]]"]
related: ["[[Stress Intensity Factor]]", "[[Strain Energy]]"]
---

# Griffith Energy Balance

Griffith's approach asks a **global energy** question: does growing the crack release more stored elastic energy than it costs to create the new surfaces?

- **Cost** (resists growth): two new surfaces, $2\gamma$ per unit crack area. $\gamma=\gamma_e$ (surface energy) for an ideally brittle solid, or $\gamma_e+\gamma_p$ if a plastic zone has to be dragged along with the tip.
- **Supply** (drives growth): release of strain energy from the material around the crack.

For a crack of length $2a$ in a large plate:

$$
\sigma_f=\sqrt{\frac{E\,G_c}{\pi a}},\qquad G_c=2(\gamma_e+\gamma_p),
$$

where $G_c$ is the **critical strain energy release rate**.

## Link to $K$

$$
K_c=Q\sigma_f\sqrt{\pi a}=\sqrt{E\,G_c}\quad(\text{plane stress}).
$$

The global energy view and the local crack-tip stress view ([[Stress Intensity Factor]]) give the same criterion.

## Why metals are tough

$\gamma_e\sim1\ \mathrm{J/m^2}$, but $\gamma_p$ can be $10^3$-$10^5\ \mathrm{J/m^2}$. Almost all the resistance is **plastic work at the crack tip**, which is why ductile materials are so much tougher than brittle ones with similar bond strength.

See [[Strain Energy]] (SESA2028 structures) for the strain-energy density that is released.
