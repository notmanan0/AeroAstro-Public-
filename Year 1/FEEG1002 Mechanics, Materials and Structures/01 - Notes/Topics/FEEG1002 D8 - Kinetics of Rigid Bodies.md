---
title: "FEEG1002 D8 - Kinetics of Rigid Bodies"
module: "FEEG1002 Mechanics, Materials and Structures"
type: topic
stream: "Part D: Dynamics"
order: 8
tags: [feeg1002, dynamics, rigid-body, kinetics, moment-of-inertia, rolling-with-slip]
aliases: ["Dynamics Lecture 8", "Rigid body kinetics", "Mass moment of inertia", "Radius of gyration", "Rolling with slip"]
date: 2026-09-25
status: complete
parent: ["[[FEEG1002 Mechanics, Materials and Structures Hub]]"]
prerequisites: ["[[FEEG1002 D7 - Kinematics of Rigid Bodies]]", "[[FEEG1002 A4 - Engineer's Bending Theory and Second Moment of Area]]"]
next_topics: ["[[FEEG1002 D9 - Work and Energy for Rigid Bodies]]"]
key_concepts: ["[[Mass Moment of Inertia and Radius of Gyration]]", "[[Planar Rigid-Body Equations of Motion]]", "[[Rolling Without Slip]]", "[[Parallel Axis Theorem]]"]
tutorial_sheets: ["[[FEEG1002 Dynamics Tutorial 8 - Kinetics of Rigid Bodies Solutions]]"]
sources: ["02 - Sources/Dynamics/Lectures/Lecture 08 - Kinetics of Rigid Bodies.pdf"]
---

# FEEG1002 D8 - Kinetics of Rigid Bodies

> [!abstract] Summary
> A rigid body needs three planar equations of motion. Two are for its **centre of mass** G, which moves as if all the mass and force were there; one is for rotation:
>
> $$\sum F_x = ma_{Gx},\qquad \sum F_y = ma_{Gy},\qquad \sum M_G = I_G\alpha\ \ \big(\text{or }\sum M_P = \text{moments of the kinetic diagram about P}\big)$$
>
> The **mass moment of inertia** $I = \int r^2\,dm$ is rotation's "mass". It moves between axes with the parallel axis theorem $I_O = I_G + md^2$, and $I = mk^2$ defines the radius of gyration.
> - For fixed-axis rotation about O: $\sum M_O = I_O\alpha$.
> - For rolling you must **assume** slip or no slip, then **check** it.

## Key Concepts
- [[Mass Moment of Inertia and Radius of Gyration]] · [[Planar Rigid-Body Equations of Motion]] · [[Rolling Without Slip]] · [[Parallel Axis Theorem]] · [[Inertia Matrix]]

---

## 1. Centre of mass (L8.1)

$$
x_G = \frac1m\int x\,dm,\qquad y_G = \frac1m\int y\,dm;\qquad \text{composite: } x_G = \frac{\sum m_ix_{Gi}}{\sum m_i}
$$

- For **uniform** bodies G is the geometric centroid ([[FEEG1002 A4 - Engineer's Bending Theory and Second Moment of Area]] uses the same maths for areas).
- A force through G produces **pure translation**.
- Gravity acts through G when $g$ is uniform, which is why a body pinned at G balances in any orientation.
- G can be found experimentally by hanging the body from two points.

## 2. Mass moment of inertia (L8.1)
For rotation about O, each element $dm$ needs a force $r_O\alpha\,dm$. Taking moments and integrating:

$$
\sum M_O = \alpha\int r_O^2\,dm = I_O\alpha,\qquad I_O = \int r_O^2\,dm\quad[\text{kg m}^2]
$$

$I$ resists changes of **angular** speed, just as $m$ resists changes of linear speed.

> [!warning] Mass vs area moments of inertia
> The polar second moment $J = \int r^2\,dA$ (m⁴) from torsion ([[FEEG1002 A8 - Torsion of Circular Shafts]]) is a geometric property. $I = \int r^2\,dm$ (kg m²) is inertial. For a uniform thin plate, $I_O = \rho_{area}J$.

**Derivations**:
- **Disc**: $I_G = \sigma\int_0^{2\pi}\int_0^Rr^3\,dr\,d\theta = \sigma\pi R^4/2 = \tfrac12mR^2$.
- **Rod**: $I_G = \int_{-L/2}^{L/2}\lambda l^2\,dl = \tfrac1{12}mL^2$.

![[d_mass_moment_of_inertia.png|900]]

| Body | About G (axis ⊥ page unless noted) | Other |
|---|---|---|
| Slender rod, length $L$ | $\tfrac1{12}mL^2$ | about an end: $\tfrac13mL^2$ |
| Thin disc / solid cylinder | $\tfrac12mr^2$ | thin disc about a diameter: $\tfrac14mr^2$ |
| Thin hoop / ring | $mr^2$ | about a diameter: $\tfrac12mr^2$ |
| Solid sphere | $\tfrac25mr^2$ | same about any axis |
| Thin plate $a\times b$ | $\tfrac1{12}m(a^2 + b^2)$ | in-plane axes: $\tfrac1{12}ma^2$, $\tfrac1{12}mb^2$ |

- **Parallel axis theorem**: $I_O = I_G + md^2$, so $I_G$ is the **minimum** over parallel axes.
- **Composite bodies**:
  1. find G;
  2. find each part's $I_{Gi}$;
  3. shift each to G with $m_id_i^2$;
  4. add.
- **Radius of gyration**: $I = mk^2$, i.e. $k = \sqrt{I/m}$, the radius at which all the mass could be concentrated. For a disc $k_G = R/\sqrt2$.
- **3D**: the **inertia tensor** has products of inertia off the diagonal. It is diagonal in principal axes ([[Inertia Matrix]]).

> [!example] Tutorial 8 Q1: 4 kg bar (0.8 m) welded to a 3 kg disc ($R = 0.4$ m)
> - $x_G = (4\times0.4 + 3\times1.2)/7$ = **0.743 m** from the free end.
> - $I_G = \tfrac1{12}(4)(0.8^2) + 4(0.343)^2 + \tfrac12(3)(0.4^2) + 3(0.457)^2$ = **1.55 kg m²**.

## 3. Equations of motion (L8.2)
Establish an inertial frame. External forces equal $m\mathbf a_G$ (from the system-of-particles result in [[FEEG1002 D4 - Linear Impulse and Momentum]]). For moments:

$$
\sum M_G = I_G\alpha\qquad\text{or}\qquad\sum M_P = \bar r\times m\mathbf a_G + I_G\alpha
$$

The second form (moments about **any** point P of the kinetic diagram) is handy for eliminating unknown reactions.

| Motion | Equations |
|---|---|
| Rectilinear translation | $\sum F = ma_G$; $\sum M_G = 0$ (or $\sum M_A = ma_Gd$) |
| Curvilinear translation | $\sum F_n = ma_{Gn}$, $\sum F_t = ma_{Gt}$, $\sum M_G = 0$ |
| Fixed-axis rotation about O | $\sum F_n = mr_G\omega^2$, $\sum F_t = mr_G\alpha$, **$\sum M_O = I_O\alpha$** |
| General plane motion | all three, plus kinematics ($a_G$ vs $\alpha$) |

For fixed-axis rotation, $\sum M_O = I_G\alpha + mr_G(r_G\alpha) = (I_G + mr_G^2)\alpha = I_O\alpha$. That is the parallel axis theorem again, and the pin reactions drop out.

> [!example] Handcart (L8): 200 kg, $P = 50$ N at 60°, frictionless wheels
> - Horizontal: $P\cos60° = ma_G$, so $a_G = 0.125$ m/s².
> - Vertical: $N_A + N_B = mg + P\sin60° = 2005$ N.
> - **Assume no tipping**, $\sum M_G = 0$: $0.3N_A - 0.2N_B = -18.48$ N m.
> - Result: **$N_A = 765$ N, $N_B = 1240$ N**. Load transfers to the rear wheel.
> - $N_A > 0$, so the assumption holds. If it had come out negative, the cart would tip and $\alpha\ne0$.

> [!example] Rod released from rest (L8): 15 kg, 0.9 m, pivot 0.15 m from G
> - Just after release $\omega = 0$, so $R_n = mr_G\omega^2 = 0$.
> - $I_O = \tfrac1{12}(15)(0.9^2) + 15(0.15^2) = 1.35$ kg m².
> - $\sum M_O = I_O\alpha$ gives **$\alpha = mgr_G/I_O = 16.35$ rad/s²**.
> - $\sum F_t = mr_G\alpha$ gives **$R_t = 110.4$ N**, less than the weight of 147 N.
>
> ![[d_pinned_rod_released.png|720]]

The same $\sum M_A = I_A\alpha$ for a bar toppling about its base gives $\alpha = (l_G/k_A^2)g\sin\theta$ (Tutorial 8 Q3). Moving a point mass along the bar changes $l_G/k_A^2$. At $d = 2l/3$, the **centre of percussion**, it matches the plain bar exactly:

![[d_t8_q3_falling_bars.png|720]]

## 4. Rolling with and without slip (L8.3)
A disc under force P has four unknowns ($F_f$, $N$, $\alpha$, $a_G$) but only three equations. The fourth comes from an assumption:

| Case | 4th equation | Friction | Check |
|---|---|---|---|
| **No slip** (try first) | $a_G = r\alpha$ | static, **unknown** | $F_f\le\mu_sN$? |
| **Slip** | $F_f = \mu_kN$, opposing sliding | kinetic, known | $a_G\ne r\alpha$ |

With no slip, the friction can be anywhere up to $\mu_sN$; once slipping, it is $\mu_kN$ regardless of the sliding speed.

> [!example] Lawn roller (L8): $m = 40$ kg, $k_G = 0.1414$ m, $R = 0.2$ m, pushed with 400 N at 45°, $\mu_s = 0.12$, $\mu_k = 0.1$
> - **Assume no slip**: $\alpha = 23.6$ rad/s², $F_A = 94.3$ N, $N_A = 675$ N. But $\mu_sN_A = 81.0$ N < 94.3 N, so the assumption **fails**.
> - **Slip**: $F_A = \mu_kN_A = 67.5$ N, giving **$\alpha = 16.9$ rad/s²** and $a_G = 5.38$ m/s². Note $a_G\ne R\alpha = 3.38$.
>
> ![[d_rolling_slip_check.png|920]]

The left panel above generalises the check. On an incline, rolling without slip needs $\mu_s\ge\tan\theta\,k^2/(k^2 + r^2)$. A hoop is the hardest body to roll without slipping (Tutorial 8 Q5).

## Year 2 bridge
- **Aircraft and spacecraft rotation**: $\sum M = I\alpha$ becomes Euler's equations $\mathbf M = \mathbf I\dot{\boldsymbol\omega} + \boldsymbol\omega\times\mathbf I\boldsymbol\omega$ with the full [[Inertia Matrix]]. These are the pitch equation $M = I_{yy}\dot q$ of [[SESA2027 A1 - Dynamic Systems and Aircraft Equations of Motion]] and the attitude dynamics of [[SESA2024 06 - Attitude Control]].
- **Radius of gyration** reappears in aircraft data: $I_{yy} = mk_y^2$ sets the short-period frequency ([[Short Period Oscillation]]).
- **Structural analogy**: $I = \int r^2\,dm$ and the second moment of area $\int y^2\,dA$ share the parallel axis theorem ([[Parallel Axis Theorem]], [[SESA2028 S1 - Section Properties and Unsymmetrical Bending]]). Products of inertia $I_{xy}$ are the dynamic counterpart of $I_{yz}$ in unsymmetrical bending.
- **Spinning bodies**: centripetal $mr_G\omega^2$ loads on rotating parts lead to [[SESA2028 S11 - Spinning Discs]].

## Links
- Previous: [[FEEG1002 D7 - Kinematics of Rigid Bodies]] · Next: [[FEEG1002 D9 - Work and Energy for Rigid Bodies]]
- Worked problems: [[FEEG1002 Dynamics Tutorial 8 - Kinetics of Rigid Bodies Solutions]]

## Sources
- Dynamics Lecture 8: 8.1 centre of mass, mass moment of inertia and radius of gyration; 8.2 equations of motion (handcart and released-rod examples); 8.3 rolling with slip (lawn roller)
