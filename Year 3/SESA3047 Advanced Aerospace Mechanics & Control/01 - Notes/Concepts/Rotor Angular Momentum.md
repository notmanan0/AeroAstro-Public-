---
title: "Rotor Angular Momentum"
module: "SESA3047 Advanced Aerospace Mechanics & Control"
type: concept
stream: "Chapter 4: Dynamic Equations and 6-DOF Model"
aliases: ["internal rotor dynamics", "propeller gyroscopic contribution", "spinning internal rotors", "gyroscopic moment", "engine angular momentum"]
tags: [sesa3047, concept, rotor, angular-momentum]
status: complete
coverage: "Chapter 4 §4.1.4; lectured in L12 ll. 222–350 and L13 ll. 1–86 (Thu 22 Oct); Eq. 4.25 from the handout only"
parent_lectures: ["[[SESA3047 4.1 - Inertia Models and Rotor Dynamics]]"]
related_concepts: ["[[Rotational Dynamic Equation]]", "[[Momentum Bias and Gyroscopic Rigidity]]"]
sources: ["02 - Sources/Lectures/Chapter_4.pdf", "02 - Sources/Lectures/L12 - SESA3047.txt", "02 - Sources/Lectures/L13 - SESA3047.txt"]
---

# Rotor Angular Momentum

A rotor spinning relative to its supporting body carries extra angular momentum $\mathbf h_R$. For a balanced, axisymmetric, fixed-axis rotor, $\mathbf h_R=I_R\Omega_R\mathbf e_R$, and with $\mathbf J$ the locked inertia of the whole assembly the total is

$$\mathbf h=\mathbf J\boldsymbol\omega+\mathbf h_R.$$

Differentiating the total with the [[Transport Theorem]] gives

$$
\mathbf M=\mathbf J\dot{\boldsymbol\omega}
+{}^b\dot{\mathbf h}_R
+\boldsymbol\omega\times(\mathbf J\boldsymbol\omega+\mathbf h_R),
$$

so the rotor adds a correction to the rigid-body angular acceleration,

$$
\boxed{\dot{\boldsymbol\omega}_{add}
=-\mathbf J^{-1}
(\boldsymbol\omega\times\mathbf h_R+{}^b\dot{\mathbf h}_R).}
$$

If the rotor's momentum is constant in the body frame, its body derivative drops out, but the $\boldsymbol\omega\times\mathbf h_R$ term (the gyroscopic moment, in textbook terms) does not. Spinning the rotor up changes the momentum's magnitude and adds the second term. If the rotor axis moves, the derivative has to be kept and the constant-inertia approximation checked.

## As lectured

L12 assumed constant rotor momentum (ll. 295–297) and split the result into a base part and an additional part (ll. 336–349; Eq. 4.20):

$$
\dot{\boldsymbol\omega}
=\underbrace{\mathbf J^{-1}(\mathbf M-\tilde{\boldsymbol\omega}\mathbf J\boldsymbol\omega)}_{\text{base: the rigid-body equation}}
\ \underbrace{-\ \mathbf J^{-1}\tilde{\boldsymbol\omega}\mathbf h_R}_{\text{additional: the rotors}}.
$$

Each rate gets its own correction, $\dot p=\dot p_{base}+\dot p_{add}$ and so on (L13 ll. 35–52), and the form of the correction depends on $\mathbf J$ (L13 ll. 82–86). On principal axes it reduces to

$$
\dot p_{add}=\frac{rh_y-qh_z}{J_{xx}},\qquad
\dot q_{add}=\frac{ph_z-rh_x}{J_{yy}},\qquad
\dot r_{add}=\frac{qh_x-ph_y}{J_{zz}}.
$$

The rigid-body equations survive at all because an axisymmetric rotor doesn't move the centre of mass as it turns (L12 ll. 234–242).

## Numbers

With $\mathbf h_R=[40,0,0]^T$ and $\boldsymbol\omega=[0.5,0.1,0.05]^T$, the extra moment on the right-hand side is $-\boldsymbol\omega\times\mathbf h_R=[0,-2,4]^T$ N m. Apply the full inverse inertia to it; off-diagonal inertia can spread it into acceleration about all three axes.

For a real propeller, $I_R=1.6$ kg m² at 2400 rpm (clockwise seen from the cockpit, so along $+x_b$) gives $h_x=402.1$ kg m²/s. In a 0.2 rad/s pull-up, $-\boldsymbol\omega\times\mathbf h_R=[0,0,+80.4]^T$ N m, so the nose yaws right; raising the tail on take-off ($q<0$) yaws it left. Worked in [[SESA3047 4.1 - Inertia Models and Rotor Dynamics#Worked engine-rotor contribution in a pull-up (suggested)|4.1]].

## Related

- Full derivation, aircraft scalar form, quadcopter case and spin-up example: [[SESA3047 4.1 - Inertia Models and Rotor Dynamics#5. Spinning internal rotors (4.15–4.25)|4.1 §5]].
- [[Momentum Bias and Gyroscopic Rigidity]] (SESA2024) · [[Rotational Dynamic Equation]]
- Source: Chapter_4.pdf pp. 5–7, Eqs. (4.15)–(4.25); L12 ll. 222–350, L13 ll. 1–86.
