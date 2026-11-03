---
title: "Resonance"
module: "MATH2048 Mathematics for Engineering and the Environment Part II"
type: concept
stream: "Block 1: Ordinary Differential Equations"
aliases: ["Resonant forcing", "Tacoma Narrows"]
tags: [math2048, concept, odes]
status: complete
parent_lectures: ["[[MATH2048 ODE2 - Euler Equations and Inhomogeneous ODEs]]"]
related_concepts: ["[[Method of Undetermined Coefficients]]", "[[Auxiliary Equation]]"]
sources: ["02 - Sources/Lectures & Problem Sheets/ODEs/Lecture3_ODE.pdf (slide 18)"]
---

# Resonance

**Resonance** is the unbounded growth of an undamped oscillator forced at its natural frequency: for $\ddot y+\omega_0^2y=\cos\omega_st$ with $\omega_s=\omega_0$, the particular integral is

$$
y_P=\frac{t}{2\omega_0}\sin\omega_0t .
$$

Off resonance, $\omega_s\neq\omega_0$, the response $y_P=\cos\omega_st/(\omega_0^2-\omega_s^2)$ is bounded but grows as the forcing frequency approaches $\omega_0$. At $\omega_s=\omega_0$ the forcing is itself a complementary function, so the guess needs an extra factor $t$ (the clash rule of the [[Method of Undetermined Coefficients]]), and that factor is the linear growth. With $y_P=t(A\cos\omega_0t+B\sin\omega_0t)$, the terms proportional to $t$ cancel against $\omega_0^2y_P$, leaving $2\omega_0(B\cos\omega_0t-A\sin\omega_0t)=\cos\omega_0t$, so $A=0$ and $B=1/(2\omega_0)$. Damping keeps the amplitude finite but sharply peaked near $\omega_0$, which is the frequency response of SESA2027 ([[Frequency Response Function]]).

![[m2048_ode_resonance.png|600]]

The lecture slides use the 1940 Tacoma Narrows bridge collapse as the motivating example. Strictly, that was aeroelastic flutter, a self-excited forcing locked onto a structural mode, rather than forcing by an external periodic load.

## Related

- Derivation: [[MATH2048 ODE2 - Euler Equations and Inhomogeneous ODEs#Resonance (L3 slide 18)|ODE2]]
- [[Method of Undetermined Coefficients]] · [[Auxiliary Equation]]
- Year 1: physical single-degree-of-freedom resonance in [[FEEG1002 D6 - Single Degree of Freedom Vibration]]
