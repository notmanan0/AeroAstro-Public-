---
title: "Kármán–Trefftz Transformation"
module: "SESA3043 Advanced Aeronautics"
type: concept
stream: "Chapter 2: Exact Solutions and Methods for Potential Flow"
aliases: ["Karman-Trefftz transformation", "KT aerofoil", "Karman-Trefftz aerofoil"]
tags: [sesa3043, concept, potential-flow, conformal-mapping, aerofoil]
status: complete
parent_lectures: ["[[SESA3043 2.1 - Complex Functions and Conformal Mapping]]"]
related_concepts: ["[[Joukowski Transformation]]", "[[Conformal Mapping]]", "[[Panel Method]]"]
sources: ["02 - Sources/Lectures/Ch2 Exact Solution and methods for potential flow.pdf"]
---

# Kármán–Trefftz Transformation

## Definition

> [!note] Definition
>
> $$z=2b\,\frac{(\bar z+b)^p+(\bar z-b)^p}{(\bar z+b)^p-(\bar z-b)^p},\qquad p=2-\frac\tau\pi,$$
>
> where $\tau$ is the trailing-edge included angle. $p=2$ recovers Joukowski.

## Key points

- Near $\bar z=b$ the map behaves like $(\bar z-b)^p$, turning the smooth circle into a wedge of angle $\tau$.
- Chord: $\dfrac bc=\dfrac{(1+\varepsilon)^p-\varepsilon^p}{4(1+\varepsilon)^p}$.
- With the slide's $2b$ prefactor, $z\approx(2/p)\bar z$ far away, so the circle-plane stream must be $(2/p)U_\infty$.
- **Coursework:** generate a KT aerofoil with the given code and perform potential-flow calculations on it.
- A finite TE angle makes it a good test case for panel methods (cusped Joukowski sections are not).

## Related

- [[SESA3043 2.1 - Complex Functions and Conformal Mapping#5. The Kármán–Trefftz aerofoil (slides 19–20)]] · [[SESA3043 2.3 - Panel Methods#7. Validation against exact solutions]]
