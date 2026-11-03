---
title: "Kármán–Trefftz Transformation"
module: "SESA3043 Advanced Aeronautics"
type: concept
stream: "Chapter 2: Exact Solutions and Methods for Potential Flow"
aliases: ["Karman-Trefftz transformation", "KT aerofoil", "Karman-Trefftz aerofoil", "Karman Treffetz transformation", "KT transformation", "trailing-edge included angle"]
tags: [sesa3043, concept, potential-flow, conformal-mapping, aerofoil]
status: complete
parent_lectures: ["[[SESA3043 2.1 - Complex Functions and Conformal Mapping]]"]
related_concepts: ["[[Joukowski Transformation]]", "[[Conformal Mapping]]", "[[Panel Method]]"]
sources: ["02 - Sources/Lectures/Ch2 Exact Solution and methods for potential flow.pdf"]
---

# Kármán–Trefftz Transformation

The Kármán–Trefftz transformation generalises Joukowski to give a trailing edge with a finite angle $\tau$:

$$z=2b\,\frac{(\bar z+b)^p+(\bar z-b)^p}{(\bar z+b)^p-(\bar z-b)^p},\qquad p=2-\frac\tau\pi.$$

With $p=2$ it reduces to Joukowski. Near $\bar z=b$ the map behaves like $(\bar z-b)^p$, which turns the smooth circle into a wedge of included angle $\tau$. The chord follows from

$$\frac bc=\frac{(1+\varepsilon)^p-\varepsilon^p}{4(1+\varepsilon)^p}.$$

With the slide's $2b$ prefactor, $z\approx(2/p)\bar z$ far from the body, so the stream in the circle plane has to be $(2/p)U_\infty$ to give $U_\infty$ in the physical plane.

The finite trailing-edge angle makes it a good test case for panel methods, which cusped Joukowski sections are not. The coursework generates a KT aerofoil with the code provided and runs potential-flow calculations on it.

## Related

- [[SESA3043 2.1 - Complex Functions and Conformal Mapping#5. The Kármán–Trefftz aerofoil (slides 19–20)]] · [[SESA3043 2.3 - Panel Methods#7. Validation against exact solutions]]
