---
title: "Joukowski Transformation"
module: "SESA3043 Advanced Aeronautics"
type: concept
stream: "Chapter 2: Exact Solutions and Methods for Potential Flow"
aliases: ["Joukowski aerofoil", "Joukowsky transformation"]
tags: [sesa3043, concept, potential-flow, conformal-mapping, aerofoil]
status: complete
parent_lectures: ["[[SESA3043 2.1 - Complex Functions and Conformal Mapping]]"]
related_concepts: ["[[Conformal Mapping]]", "[[Kármán–Trefftz Transformation]]", "[[Kutta Condition]]"]
sources: ["02 - Sources/Lectures/Ch2 Exact Solution and methods for potential flow.pdf"]
---

# Joukowski Transformation

## Definition

> [!note] Definition
>
> $$z=\bar z+\frac{b^2}{\bar z},\qquad\frac{\mathrm dz}{\mathrm d\bar z}=1-\frac{b^2}{\bar z^2}\ (=0\text{ at }\bar z=\pm b).$$

## Shapes from a circle of radius $a$, centre $\bar z_0$

| Circle | Body |
|---|---|
| $a=b$, centred | flat plate $[-2b,2b]$ |
| $a>b$, centred | ellipse |
| through $b$, centre $-\varepsilon b$ | symmetric aerofoil (thickness $\approx1.3\varepsilon$ for small $\varepsilon$) |
| centre $-\varepsilon b+ia\sin\beta$, $a\cos\beta=b(1+\varepsilon)$ | cambered aerofoil (camber $\approx\beta/2$) |

## Results

- Chord: $b/c=(1+2\varepsilon)/[4(1+\varepsilon)^2]$, $c\approx4b$.
- Kutta: $\Gamma=4\pi aU_\infty\sin(\alpha+\beta)$; $C_L=\dfrac{8\pi a}{c}\sin(\alpha+\beta)$, $\alpha_{L=0}=-\beta$.
- The trailing edge is **cusped** (zero angle).

![[aa_joukowski_aerofoil.png|700]]

## Related

- [[SESA3043 2.1 - Complex Functions and Conformal Mapping#4. The Joukowski aerofoil (slides 15–18)]] · [[Kutta Condition]] · [[Kutta-Joukowski Theorem]]
