---
title: "Joukowski Transformation"
module: "SESA3043 Advanced Aeronautics"
type: concept
stream: "Chapter 2: Exact Solutions and Methods for Potential Flow"
aliases: ["Joukowski aerofoil", "Joukowsky transformation", "Zhukovsky transformation", "Joukowski airfoil", "transfer constant"]
tags: [sesa3043, concept, potential-flow, conformal-mapping, aerofoil]
status: complete
parent_lectures: ["[[SESA3043 2.1 - Complex Functions and Conformal Mapping]]"]
related_concepts: ["[[Conformal Mapping]]", "[[Kármán–Trefftz Transformation]]", "[[Kutta Condition]]"]
sources: ["02 - Sources/Lectures/Ch2 Exact Solution and methods for potential flow.pdf"]
---

# Joukowski Transformation

The Joukowski transformation is the conformal map

$$z=\bar z+\frac{b^2}{\bar z},\qquad\frac{\mathrm dz}{\mathrm d\bar z}=1-\frac{b^2}{\bar z^2},$$

whose critical points are at $\bar z=\pm b$. Applied to a circle of radius $a$ centred at $\bar z_0$, it gives a family of shapes:

| Circle | Body |
|---|---|
| $a=b$, centred | flat plate $[-2b,2b]$ |
| $a>b$, centred | ellipse |
| through $b$, centre $-\varepsilon b$ | symmetric aerofoil (thickness $\approx1.3\varepsilon$ for small $\varepsilon$) |
| centre $-\varepsilon b+ia\sin\beta$, $a\cos\beta=b(1+\varepsilon)$ | cambered aerofoil (camber $\approx\beta/2$) |

The lecture on 9 October built the aerofoil in three moves: an ellipse ($b<a$), then a shift of the circle to the left by $\varepsilon b$ so that it passes through $\bar z=b$, giving a sharp trailing edge and blunt leading edge (thickness), then a shift upward by $\beta$ (camber).

The chord is $c\approx4b$, more precisely $b/c=(1+2\varepsilon)/[4(1+\varepsilon)^2]$. Applying the Kutta condition gives $\Gamma=4\pi aU_\infty\sin(\alpha+\beta)$, so

$$C_L=\frac{8\pi a}{c}\sin(\alpha+\beta),\qquad\alpha_{L=0}=-\beta.$$

The trailing edge is cusped, with zero included angle, which is why the coursework uses the [[Kármán–Trefftz Transformation|Kármán–Trefftz]] map instead. In the demo sweep at $\alpha=3^\circ$, raising $\varepsilon$ from 0 to 0.1 takes $C_L$ from 0.329 to 0.359, while raising $\beta$ from 0 to 0.1 rad takes it to 1.045 ([[SESA3043 2.1 - Complex Functions and Conformal Mapping#The demo recording reproduced|2.1]]).

In the exam this is examined as logic rather than calculation: know the steps from cylinder to aerofoil, but you won't be asked to compute a Joukowski or KT flow by hand (9 Oct, ll. 490–495).

![[aa_joukowski_aerofoil.png|700]]

## Related

- [[SESA3043 2.1 - Complex Functions and Conformal Mapping#4. The Joukowski aerofoil (slides 15–18)]] · [[Kutta Condition]] · [[Kutta-Joukowski Theorem]]
