---
title: "FEEG1002 Dynamics Tutorial 8 - Kinetics of Rigid Bodies Solutions"
module: "FEEG1002 Mechanics, Materials and Structures"
type: tutorial
stream: "Part D: Dynamics"
tags: [feeg1002, tutorial-solutions, dynamics, rigid-body, moment-of-inertia, rolling-with-slip]
sheet: "Dynamics Problem sheet 8 (kinetics of rigid bodies)"
theory_notes: ["[[FEEG1002 D8 - Kinetics of Rigid Bodies]]"]
key_concepts: ["[[Mass Moment of Inertia and Radius of Gyration]]", "[[Planar Rigid-Body Equations of Motion]]", "[[Rolling Without Slip]]", "[[Parallel Axis Theorem]]"]
status: complete
sources: ["02 - Sources/Dynamics/Tutorials/Tutorial Sheet 08 - Kinetics of Rigid Bodies.pdf"]
---

# FEEG1002 Dynamics Tutorial 8 - Kinetics of Rigid Bodies Solutions

> [!abstract] Sheet Info
> Five problems:
> - a composite moment of inertia;
> - a cam and platform;
> - toppling bars;
> - hoisting drums;
> - a hoop that may slip on an incline.
>
> Every printed answer is reproduced ✔. Q3(b), which the sheet leaves as "search for...", is solved in closed form.

## Theory Links
- [[FEEG1002 D8 - Kinetics of Rigid Bodies]] · [[Mass Moment of Inertia and Radius of Gyration]] · [[Planar Rigid-Body Equations of Motion]] · [[Parallel Axis Theorem]]

---

## Q1: 4 kg slender bar ($L = 0.8$ m) welded to a 3 kg thin disc ($R = 0.4$ m)
- **Centre of mass**, from the bar's free end: bar G at 0.4 m, disc G at $L + R = 1.2$ m.

$$
l_G = \frac{4(0.4) + 3(1.2)}{7} = \mathbf{0.743}\ \text{m}\ ✔
$$

- **Moment of inertia** (parallel axis theorem for each part):

$$
I_G = \underbrace{\tfrac1{12}(4)(0.8)^2 + 4(0.343)^2}_{\text{bar}:\ 0.684} + \underbrace{\tfrac12(3)(0.4)^2 + 3(0.457)^2}_{\text{disc}:\ 0.867} = \mathbf{1.55}\ \text{kg m}^2\ ✔
$$

## Q2: Uniform cam (4 kg, $r = 0.3$ m) pivoted at O on its rim, lifting a 10 kg platform, torque $T$
- **(a) Kinematics**: G is at height $r\sin\theta$ above O and the platform rests on top of the cam:
  - $y = r\sin\theta + r$;
  - $\dot y = r\dot\theta\cos\theta$;
  - $\ddot y = r\ddot\theta\cos\theta - r\dot\theta^2\sin\theta$ ✔
- **(b) FBDs**:
  - platform: weight and the contact force $N$ (plus friction $\mu_kN$ if present);
  - cam: $T$, weight at G, $N$ and friction from the platform, and pin reactions at O.
- **(c) Frictionless**:
  - platform: $N - m_Pg = m_P\ddot y$;
  - cam, about O: $T - m_Cgr\cos\theta - Nr\cos\theta = I_O\ddot\theta$, with $I_O = \tfrac12m_Cr^2 + m_Cr^2 = 0.54$ kg m².
  - Substitute $\ddot\theta$ from (a):

$$
\ddot y = \frac{T - rg\cos\theta(m_P + m_C) - I_O\dot\theta^2\tan\theta}{I_O/(r\cos\theta) + m_Pr\cos\theta}\ ✔
$$

- **(d)** $T = 50$ N m, $\theta = 0$, $\dot\theta = 0$:

$$
\ddot y = \frac{50 - 0.3(9.81)(14)}{0.54/0.3 + 10(0.3)} = \frac{8.80}{4.80} = \mathbf{1.83}\ \text{m/s}^2\ ✔
$$

## Q3: Two bars toppling about their bases A ($l = 1.2$ m, 500 kg/m³, $A = 5.76$ cm², so $m_b = 0.346$ kg); one carries a 0.2 kg point mass at the top
- **(a)** With $\theta$ measured from the vertical: $\sum M_A = mgl_G\sin\theta = I_A\alpha = mk_A^2\alpha$, so

$$
\alpha = \frac{l_G}{k_A^2}g\sin\theta\ ✔
$$

  - Uniform bar: $l_G/k_A^2 = (l/2)/(l^2/3) = 3/2l = 1.25$ m⁻¹.
  - With the tip mass: $l_G = 0.820$ m, $k_A^2 = 0.832$ m², so $l_G/k_A^2 = 0.986$ m⁻¹.
  - **The plain bar falls faster.** The tip mass adds more to $I_A$ (it is far away) than to the toppling moment.
- **(b)** Require $(m_bl/2 + md)/(m_bl^2/3 + md^2) = 3/2l$. This reduces to $2ld = 3d^2$, so

$$
d = \frac{2l}3 = \mathbf{0.80}\ \text{m from A}
$$

  - This holds for **any** added mass. $2l/3$ is the length of the simple pendulum equivalent to the bar, i.e. its **centre of percussion** about A. A mass placed there changes neither $l_G/k_A^2$ nor the motion.

![[d_t8_q3_falling_bars.png|700]]

## Q4: Hoisting drums (150 kg, $k_d = 0.45$ m) with $r_e = 0.6$ m and $r_i = 0.3$ m; $P = 1.8$ kN at 45°; 300 kg block
- **(a)** FBDs:
  - drum: $P$ on the outer drum, block rope $T$ on the inner drum, weight, bearing reactions $O_x$ and $O_y$;
  - block: $T$ up, weight down.
- **(b)** With $a = r_i\alpha$:
  - drum: $Pr_e - Tr_i = I_O\alpha$, where $I_O = m_dk_d^2 = 30.4$ kg m²;
  - block: $T - m_bg = m_ba$.

$$
a = \frac{Pr_e - m_bgr_i}{I_O/r_i + m_br_i} = \frac{1080 - 882.9}{101.25 + 90} = \mathbf{1.03}\ \text{m/s}^2\ ✔
$$

- **(c)** $T = m_b(g + a)$ = **3252 N** ✔
- **(d)** The drum's centre of mass is fixed, so $\sum F = 0$:
  - $O_x = P\cos45° = 1273$ N;
  - $O_y = T + m_dg + P\sin45° = 5996$ N;
  - **$R_O = 6130$ N at 78°** to the horizontal ✔

![[d_t8_q4_hoist_fbd.png|840]]

## Q5: Hoop ($r = 150$ mm) released on a 20° incline, $\mu_s = 0.15$, $\mu_k = 0.12$
**Assume no slip** ($I_G = mr^2$, $a = r\alpha$):
- $mg\sin\theta - F = ma$ and $Fr = mr^2\alpha$, so $a = \tfrac12g\sin\theta = 1.68$ m/s² and $F = ma$.
- Friction needed: $F/N = \tfrac12\tan20° = 0.182 > \mu_s = 0.15$. The assumption **fails: the hoop slips**.

**With slip** ($F = \mu_kN$):
- $F = 0.12mg\cos20°$, so $a = g(\sin20° - 0.12\cos20°) = 2.25$ m/s².
- $\alpha = F/(mr)$ = **7.37 rad/s²** ✔, and $a\ne r\alpha = 1.11$ m/s².
- Distance: $3 = \tfrac12(2.25)t^2$, so **$t = 1.633$ s** ✔

A disc or sphere would roll without slip here, needing only $\mu = 0.121$ and $0.104$. The hoop needs the most friction because half its KE is rotational.

![[d_rolling_slip_check.png|880]]

## Sources
- Dynamics Problem sheet 8 (answers printed on the sheet)
