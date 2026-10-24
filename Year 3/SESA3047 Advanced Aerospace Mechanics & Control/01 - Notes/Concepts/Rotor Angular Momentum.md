---
title: "Rotor Angular Momentum"
module: "SESA3047 Advanced Aerospace Mechanics & Control"
type: concept
stream: "Chapter 4: Dynamic Equations and 6-DOF Model"
aliases: ["internal rotor dynamics", "propeller gyroscopic contribution"]
tags: [sesa3047, concept, rotor, angular-momentum]
status: complete
coverage: "Chapter 4 §4.1.4; lectured in L12 ll. 222–350 and L13 ll. 1–86 (Thu 22 Oct); Eq. 4.25 from the handout only"
parent_lectures: ["[[SESA3047 4.1 - Inertia Models and Rotor Dynamics]]"]
related_concepts: ["[[Rotational Dynamic Equation]]", "[[Momentum Bias and Gyroscopic Rigidity]]"]
sources: ["02 - Sources/Lectures/Chapter_4.pdf", "02 - Sources/Lectures/L12 - SESA3047.txt", "02 - Sources/Lectures/L13 - SESA3047.txt"]
---

# Rotor Angular Momentum

> [!note] Definition
> A rotor spinning relative to its supporting body contributes additional momentum $\mathbf h_R$. For a balanced axisymmetric fixed-axis rotor, $\mathbf h_R=I_R\Omega_R\mathbf e_R$. With $\mathbf J$ the complete assembly's locked inertia,
>
> $$\mathbf h=\mathbf J\boldsymbol\omega+\mathbf h_R.$$

Differentiate total momentum using the [[Transport Theorem]]:

$$
\mathbf M=\mathbf J\dot{\boldsymbol\omega}
+{}^b\dot{\mathbf h}_R
+\boldsymbol\omega\times(\mathbf J\boldsymbol\omega+\mathbf h_R).
$$

Therefore the correction to the baseline derivative is

$$
\boxed{\dot{\boldsymbol\omega}_{add}
=-\mathbf J^{-1}
(\boldsymbol\omega\times\mathbf h_R+{}^b\dot{\mathbf h}_R).}
$$

Constant body-frame momentum removes its body derivative, but not the gyroscopic term. Spin-up changes momentum magnitude and produces the second reaction contribution. Moving rotor axes requires retaining the derivative and checking whether the constant-inertia approximation still applies.

## Base plus additional (as lectured)

L12 assumed constant rotor momentum (ll. 295–297) and split the result in two (ll. 336–349; Eq. 4.20):

$$
\dot{\boldsymbol\omega}
=\underbrace{\mathbf J^{-1}(\mathbf M-\tilde{\boldsymbol\omega}\mathbf J\boldsymbol\omega)}_{\text{base: the rigid-body equation}}
\ \underbrace{-\ \mathbf J^{-1}\tilde{\boldsymbol\omega}\mathbf h_R}_{\text{additional: the rotors}}.
$$

Each rate gets its own correction, $\dot p=\dot p_{base}+\dot p_{add}$ and so on (L13 ll. 35–52). The form of the correction depends on $\mathbf J$ (L13 ll. 82–86). For **principal axes** it reduces to

$$
\dot p_{add}=\frac{rh_y-qh_z}{J_{xx}},\qquad
\dot q_{add}=\frac{ph_z-rh_x}{J_{yy}},\qquad
\dot r_{add}=\frac{qh_x-ph_y}{J_{zz}}.
$$

Why the rigid-body equations survive at all: an **axisymmetric** rotor does not move the centre of mass as it turns (L12 ll. 234–242).

## Sign check

With $\mathbf h_R=[40,0,0]^T$ and $\boldsymbol\omega=[0.5,0.1,0.05]^T$, the effective additional right-hand-side moment is

$$
-\boldsymbol\omega\times\mathbf h_R=[0,-2,4]^T\ \mathrm{N\,m}.
$$

Apply the full inertia inverse to this vector. Off-diagonal inertia can turn this into acceleration about all three axes.

**A real propeller.** For $I_R=1.6$ kg m² at 2400 rpm (clockwise from the cockpit, so $+x_b$), $h_x=402.1$ kg m²/s. In a 0.2 rad/s pull-up, $-\boldsymbol\omega\times\mathbf h_R=[0,0,+80.4]^T$ N m: the nose yaws right, and raising the tail on take-off ($q<0$) yaws it left. Worked in [[SESA3047 4.1 - Inertia Models and Rotor Dynamics#Worked engine-rotor gyroscopics in a pull-up (suggested)|4.1]].

## Related

- Full derivation, aircraft scalar form, quadcopter case and spin-up example: [[SESA3047 4.1 - Inertia Models and Rotor Dynamics#5. Spinning internal rotors (4.15–4.25)|4.1 §5]].
- [[Momentum Bias and Gyroscopic Rigidity]] (SESA2024) · [[Rotational Dynamic Equation]]
- Source: Chapter_4.pdf pp. 5–7, Eqs. (4.15)–(4.25); L12 ll. 222–350, L13 ll. 1–86.
