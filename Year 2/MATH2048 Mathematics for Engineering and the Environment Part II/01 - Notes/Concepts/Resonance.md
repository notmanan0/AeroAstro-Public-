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

## Definition

> [!note] Definition
> Forcing an undamped oscillator $\ddot y+\omega_0^2y=\cos\omega_st$ **at its natural frequency** ($\omega_s=\omega_0$) gives a particular integral whose amplitude grows without bound:
>
> $$y_p=\frac{t}{2\omega_0}\sin\omega_0t .$$

## Explanation
- For $\omega_s\neq\omega_0$: $y_p=\dfrac{\cos\omega_st}{\omega_0^2-\omega_s^2}$, which is bounded but large near $\omega_0$. The full solution beats between the two frequencies.
- For $\omega_s=\omega_0$: the forcing *is* a complementary function, so the trial needs an extra factor $t$ (the clash rule of [[Method of Undetermined Coefficients]]). The factor $t$ is the linear growth.
- **Derivation**: with $y_p=t(A\cos\omega_0t+B\sin\omega_0t)$, the terms proportional to $t$ cancel against $\omega_0^2y_p$. This leaves $2\omega_0(B\cos-A\sin)=\cos$, so $A=0$ and $B=\tfrac1{2\omega_0}$.
- Damping ($c>0$) keeps the amplitude finite but peaked near $\omega_0$. See SESA2027 [[Frequency Response Function]].

![[m2048_ode_resonance.png|600]]

## Examples
- The Tacoma Narrows Bridge (1940) is the lecture's motivating example. (Strictly, it was aeroelastic flutter: self-excited forcing locked to a structural mode.)

## Related
- [[Method of Undetermined Coefficients]] · [[Auxiliary Equation]]

## Year 1 foundation
- Physical SDOF resonance and FRFs: [[FEEG1002 D6 - Single Degree of Freedom Vibration]].

## Sources
- Lecture 3 slide 18
