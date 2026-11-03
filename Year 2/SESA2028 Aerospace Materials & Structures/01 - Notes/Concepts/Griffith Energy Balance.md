---
title: "Griffith Energy Balance"
module: "SESA2028 Aerospace Materials & Structures"
type: concept
stream: "Materials"
aliases: ["Griffith criterion", "Strain energy release rate"]
tags: [sesa2028, materials, fracture-mechanics, energy]
status: lectured
parent: ["[[SESA2028 M1 - Fracture, Toughness and Fracture Mechanics]]"]
related: ["[[Stress Intensity Factor]]", "[[Strain Energy]]"]
---

# Griffith Energy Balance

Griffith's criterion says a pre-existing crack grows when the elastic strain energy released by a small extension is at least the energy needed to create the new crack surfaces, which gives the fracture stress $\sigma_f=\sqrt{EG_c/\pi a}$.

The approach is global: it ignores the complicated stresses at the tip and simply balances energy. Growing the crack costs energy because two new surfaces appear, at $\gamma_e$ per unit area in an ideally brittle solid. In a metal the plastic zone has to be carried along with the tip as well, which costs plastic work $\gamma_p$ per unit area, so $\gamma=\gamma_e+\gamma_p$. The energy is supplied by the strain energy stored round the crack, which is released as the crack opens.

For a through crack of length $2a$ in a large plate of unit thickness under remote stress $\sigma$, the released strain energy is $\pi a^2\sigma^2/E$ and the surface energy is $4a\gamma$. Equating their rates of change with $a$ gives $2\pi a\sigma^2/E=4\gamma$, so $\sigma_f=\sqrt{2E\gamma/\pi a}$. Writing the critical strain energy release rate as $G_c=2\gamma$ gives the lecture form above; the full derivation is in [[SESA2028 M1 - Fracture, Toughness and Fracture Mechanics#Griffith's energy balance|M1]].

Multiplying through by $\sqrt{\pi a}$ shows $\sigma_f\sqrt{\pi a}=\sqrt{EG_c}$. The left side is the stress intensity factor at fracture, and the right side contains only material properties, so the critical stress intensity $K_c=\sqrt{EG_c}$ is a material constant ([[Stress Intensity Factor]]). The local stress view and the global energy view give the same criterion.

The size of $\gamma_p$ explains why metals are tough. Surface energies are of order 1 J/m², while a steel with $K_{Ic}=50$ MPa√m has $G_c=K_{Ic}^2/E\approx1.2\times10^4$ J/m²: nearly all of the resistance is plastic work at the tip. The strain energy being released is the same quantity met in the structures half of the module ([[Strain Energy]]).

## Related

- Topic: [[SESA2028 M1 - Fracture, Toughness and Fracture Mechanics|M1]] · [[SESA2028 S7 - Strain Energy and Conservation of Energy|S7]]
- Concepts: [[Stress Intensity Factor]] · [[Fracture Toughness and LEFM Validity]] · [[Strain Energy]]
