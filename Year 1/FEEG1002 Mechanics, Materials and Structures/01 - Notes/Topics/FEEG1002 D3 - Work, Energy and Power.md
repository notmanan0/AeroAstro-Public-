---
title: "FEEG1002 D3 - Work, Energy and Power"
module: "FEEG1002 Mechanics, Materials and Structures"
type: topic
stream: "Part D: Dynamics"
order: 3
tags: [feeg1002, dynamics, work, energy, potential-energy, power, efficiency]
aliases: ["Dynamics Lecture 3", "Work-energy principle", "Conservation of energy", "Power and efficiency"]
date: 2026-09-25
status: complete
parent: ["[[FEEG1002 Mechanics, Materials and Structures Hub]]"]
prerequisites: ["[[FEEG1002 D2 - Curvilinear Motion]]"]
next_topics: ["[[FEEG1002 D4 - Linear Impulse and Momentum]]"]
key_concepts: ["[[Work-Energy Principle]]", "[[Conservative Forces and Potential Energy]]", "[[Power and Efficiency]]"]
tutorial_sheets: ["[[FEEG1002 Dynamics Tutorial 3 - Work, Energy and Power Solutions]]"]
sources: ["02 - Sources/Dynamics/Lectures/Lecture 03 - Work, Energy and Power.pdf"]
---

# FEEG1002 D3 - Work, Energy and Power

> [!abstract] Summary
> Integrating $\sum F_t = mv\,dv/ds$ **over displacement** turns Newton's law into a scalar energy balance:
> $$KE_1 + V_1 + \sum U^{nc}_{1-2} = KE_2 + V_2,\qquad KE = \tfrac12mv^2,\quad V = V_g + V_e$$
> - **Conservative forces** have path-independent work and are counted as potential energy: weight $V_g = mgy$ (or $-GMm/r$) and springs $V_e = \tfrac12k\,\Delta l^2$.
> - **Everything else** (friction, applied forces, drag) goes into $U^{nc}$.
>
> Use energy when the question links **speed and position**, not time. **Power** $P = \mathbf F\cdot\mathbf v$ is the rate of doing work; **efficiency** $\eta = P_{out}/P_{in} < 1$.

## Key Concepts
- [[Work-Energy Principle]] · [[Conservative Forces and Potential Energy]] · [[Power and Efficiency]]

---

## 1. Work of a force (L3.1)
$$
dU = \mathbf F\cdot d\mathbf r = F\,ds\cos\theta\qquad\Rightarrow\qquad U_{1-2} = \int_{\mathbf r_1}^{\mathbf r_2}\mathbf F\cdot d\mathbf r = \int_{s_1}^{s_2}F\cos\theta\,ds
$$

- Only the component **along the displacement** does work. Its units are the joule (N m).
- Graphically, the work is the **area** under the $F_t$–$s$ curve.
- Constant force at a constant angle on a straight path: $U = F\cos\theta\,(s_2 - s_1)$. Check that both assumptions actually hold first.

![[d_work_area.png|900]]

## 2. Conservative forces and potential energy (L3.1)
A force is **conservative** if its work depends only on the end points, not the path. Equivalently, its work around any closed loop is zero, $\oint\mathbf F\cdot d\mathbf r = 0$. Then a potential $V$ exists with

$$
U_{A-B} = -(V_B - V_A)
$$

- Positive work by the force **decreases** its potential energy.

| Force | Potential energy | Notes |
|---|---|---|
| Weight (constant $g$) | $V_g = mgy$ | datum arbitrary; only changes matter |
| Gravitational attraction | $V_g = -Gm_1m_2/r$ | always negative, $\to0$ as $r\to\infty$ |
| Linear spring | $V_e = \tfrac12k\,\Delta l^2$ | always positive, for stretch **or** compression |
| **Kinetic friction** | none: **non-conservative** | $U = -\mu_kNs$ on every leg, so $-2\mu_kNs$ for there and back |

- Forces that always oppose the motion (friction, drag), or always assist it, are non-conservative.
- **Static friction** usually does no work, because its point of application does not move. The exception is a crate on an accelerating truck: static friction does positive work **on the crate** (Tutorial 3 Q5).

## 3. The work–energy principle (L3.2)
From $\sum F_t = mv\,dv/ds$:

$$
\sum\int_{s_1}^{s_2}F_t\,ds = \tfrac12mv_2^2 - \tfrac12mv_1^2\qquad\Rightarrow\qquad KE_1 + \sum U_{1-2} = KE_2
$$

- Normal forces do no work, because nothing moves in the $n$ direction.
- Split into conservative and non-conservative forces: $KE_1 + V_{g1} + V_{e1} + \sum U^{nc}_{1-2} = KE_2 + V_{g2} + V_{e2}$.
- With **only conservative forces**, $KE + V$ = const (**conservation of energy**). Free fall reproduces $v_2^2 = v_1^2 + 2g\Delta h$.
- **Systems of particles**: sum the scalars. Internal forces cancel in pairs **if** the points they act on move together (true for inextensible cords, as in Tutorial 3 Q4).
- **Friction and heat**: $\mu_kNs$ counts both the mechanical work lost and the heat generated. The surface asperities deform, so the true displacement of the friction force is smaller than $s$.

> [!example] Block down a rough incline (L3): $m = 50$ kg, $v_A = 6$ m/s, $\mu_k = 0.5$
> - Energy balance: $\tfrac12mv_A^2 + mgs\sin\theta - \mu_kmg\cos\theta\,s = 0$.
> - So $s = \dfrac{v_A^2}{2g(\mu_k\cos\theta - \sin\theta)}$ = **5.76 m** at $\theta = 10°$. The answer is independent of $m$.
> - At 30° the formula gives $s = -27.4$ m. The question is ill-posed: $\tan30° > \mu_k$, so the block accelerates at 0.66 m/s² and never stops. The negative answer is where it *would have started from rest* up the slope.
>
> ![[d_incline_stopping_distance.png|720]]

> [!example] Round the loop (L3): $R = 1.5$ m, frictionless, unilateral contact
> - At the top B the track can only push, $N \ge 0$. Setting $N = 0$ gives $mg = mv_B^2/R$, so $v_B = \sqrt{gR} = 3.84$ m/s.
> - Energy from A to B: $\tfrac12mv_A^2 = \tfrac12mv_B^2 + mg(2R)$, so **$v_A = \sqrt{5gR} = 8.58$ m/s**. By conservation, $v_C = v_A$.
> - The **trap**: setting $\tfrac12mv_A^2 = mg(2R)$ gives $\sqrt{4gR} = 7.67$ m/s. With that speed $N$ reaches zero at **131.8° from the bottom** and the block falls off before the top. This answers the lecture's closing question.
>
> ![[d_loop_the_loop.png|920]]

The same $T/mg = v_0^2/gL - 2 + 3\cos\theta$ governs a pendulum given a push (Tutorial 3 Q9):

![[d_t3_q9_pendulum_regimes.png|720]]

## 4. Power and efficiency (L3.3)
$$
P = \frac{dU}{dt} = \mathbf F\cdot\mathbf v = Fv\cos\theta\quad[\text{W} = \text{J/s}],\qquad 1\ \text{hp} = 746\ \text{W}
$$

$$
\eta = \frac{\text{power output}}{\text{power input}} < 1
$$

> [!example] Motor hoisting a 50 kg block (L3), $\eta = 0.8$
> - Cable kinematics: $s_P + 2s_A = l$, so $a_A = -a_P/2 = -3$ m/s² (upwards).
> - Block: $m_Ag - 2T = m_Aa_A$ gives $490.5 - 2T = 50(-3)$, so $T = 320.3$ N.
> - Output power: $P_o = Tv_P = 320.3\times12 = 3844$ W.
> - Input power: $P_i = P_o/\eta$ = **4.8 kW**.

At constant force, power rises with speed. So an accelerating car needs its peak power at the **end** of the manoeuvre (Tutorial 3 Q10):

![[d_t3_q10_car_power.png|700]]

## Year 2 bridge
- **Structural energy methods**: a spring's $\tfrac12k\,\Delta l^2$ generalises to the strain energy $\tfrac12\int\sigma\varepsilon\,dV$ of [[SESA2028 S7 - Strain Energy and Conservation of Energy]] ([[Strain Energy]]). "Work done by loads = strain energy stored" is this chapter's conservation law for a static structure. Virtual work and Castigliano follow ([[SESA2028 S8 - Virtual Work and Castigliano Theorems]]).
- **Minimum potential energy** in finite elements: [[Principle of Minimum Total Potential Energy]] ([[SESA2029 B3 - Principle of Minimum Total Potential Energy]]).
- **Conservative fields in maths**: $\oint\mathbf F\cdot d\mathbf r = 0$ is equivalent to $\mathbf F = -\nabla V$ ([[Conservative Vector Fields]], [[MATH2048 VC3 - Line Integrals and Conservative Fields]]).
- **Orbital energy**: $V_g = -GMm/r$ with $\tfrac12v^2 - \mu/r = -\mu/2a$ is the [[Vis-Viva Equation]] ([[SESA2024 04 - Orbital Energy and the Vis-Viva Equation]]).
- **Power in propulsion**: $P = Fv$ is thrust power, the numerator of propulsive efficiency in [[SESA2023 Propulsion Hub]].

## Links
- Previous: [[FEEG1002 D2 - Curvilinear Motion]] · Next: [[FEEG1002 D4 - Linear Impulse and Momentum]]
- Rigid-body version: [[FEEG1002 D9 - Work and Energy for Rigid Bodies]]
- Worked problems: [[FEEG1002 Dynamics Tutorial 3 - Work, Energy and Power Solutions]]

## Sources
- Dynamics Lecture 3: 3.1 work, conservative forces and potential energy; 3.2 work–energy principle (incline and loop examples); 3.3 power and efficiency (motor hoist example)
