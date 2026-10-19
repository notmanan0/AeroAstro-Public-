---
title: "Rotor Angular Momentum"
module: "SESA3047 Advanced Aerospace Mechanics & Control"
type: concept
stream: "Chapter 4: Dynamic Equations and 6-DOF Model"
aliases: ["internal rotor dynamics", "propeller gyroscopic contribution"]
tags: [sesa3047, concept, rotor, angular-momentum]
status: complete
coverage: "Chapter 4 §4.1.4; written from the handout, awaiting transcript"
parent_lectures: ["[[SESA3047 4.1 - Inertia Models and Rotor Dynamics]]"]
related_concepts: ["[[Rotational Dynamic Equation]]", "[[Momentum Bias and Gyroscopic Rigidity]]"]
sources: ["02 - Sources/Lectures/Chapter_4.pdf"]
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

## Sign check

With $\mathbf h_R=[40,0,0]^T$ and $\boldsymbol\omega=[0.5,0.1,0.05]^T$, the effective additional right-hand-side moment is

$$
-\boldsymbol\omega\times\mathbf h_R=[0,-2,4]^T\ \mathrm{N\,m}.
$$

Apply the full inertia inverse to this vector. Off-diagonal inertia can turn this into acceleration about all three axes.

## Related

- Full derivation, aircraft scalar form and spin-up example: [[SESA3047 4.1 - Inertia Models and Rotor Dynamics#5. Spinning internal rotors (4.15–4.25)|4.1 §5]].
- [[Momentum Bias and Gyroscopic Rigidity]] (SESA2024) · [[Rotational Dynamic Equation]]
- Source: Chapter_4.pdf pp. 5–7, Eqs. (4.15)–(4.25); no matching transcript yet.
