---
title: "Stress Intensity Factor"
module: "SESA2028 Aerospace Materials & Structures"
type: concept
stream: "Materials"
tags: [sesa2028, materials, fracture-mechanics, lefm]
status: complete
parent: ["[[SESA2028 M1 - Fracture, Toughness and Fracture Mechanics]]"]
related: ["[[Fracture Toughness and LEFM Validity]]", "[[Paris Law]]", "[[Stress Singularities]]"]
---

# Stress Intensity Factor

The stress intensity factor $K$ is a single number that sets the size of the **elastic stress field around a sharp crack tip**. It combines the applied stress, the crack size and the geometry.

$$
K=Q\,\sigma\sqrt{\pi a}\qquad[\mathrm{MPa\sqrt m}]
$$

- $\sigma$: remote (nominal) stress normal to the crack, in MPa.
- $a$: crack depth for a surface crack, **half-length** for an internal (through) crack, in **metres**.
- $Q$ (or $Y$): dimensionless geometry factor. $Q=1$ for a centre crack in an infinite plate, about 1.12 for an edge crack, and $Q=1.2$ is used in almost every SESA2028 exam.

## Crack-tip field

$$
\sigma_{ij}(r,\theta)=\frac{K}{\sqrt{2\pi r}}f_{ij}(\theta)+\dots
$$

Every crack of the same type, whatever its size and load, has the **same shape** of stress field. $K$ only scales it. That is why one critical value, $K_{Ic}$, can govern fracture of any geometry of the same material.

## Uses

| Use | Formula |
|---|---|
| Fast fracture criterion | $K=K_{Ic}$ |
| Critical crack size | $a_c=\dfrac1\pi\left(\dfrac{K_{Ic}}{Q\sigma_{max}}\right)^2$ |
| Fatigue driving force | $\Delta K=Q\,\Delta\sigma\sqrt{\pi a}$, with the tensile part of the cycle only |
| Energy link | $K_c=\sqrt{E\,G_c}$ ([[Griffith Energy Balance]]) |

## Checks

- Units: stress in MPa and $a$ in m give $\mathrm{MPa\sqrt m}$.
- $K$ depends on **stress and crack size**; $K_{Ic}$ is a **material property**. Do not mix them up.
- $K$ is valid only while the plastic zone is small ([[Fracture Toughness and LEFM Validity]]).

Compare the stress concentration factor $K_t$ in [[Stress Concentration Factor and Factor of Safety]], which is dimensionless and becomes infinite for a sharp crack; that is why $K$ replaces it. See [[Stress Singularities]] for the $1/\sqrt r$ field in FEA.
