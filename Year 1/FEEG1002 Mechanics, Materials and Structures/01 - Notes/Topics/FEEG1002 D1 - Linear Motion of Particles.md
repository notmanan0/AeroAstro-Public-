---
title: "FEEG1002 D1 - Linear Motion of Particles"
module: "FEEG1002 Mechanics, Materials and Structures"
type: topic
stream: "Part D: Dynamics"
order: 1
tags: [feeg1002, dynamics, kinematics, newtons-laws, friction, pulleys, particles]
aliases: ["Dynamics Lecture 1", "Rectilinear motion", "Linear motion", "Dependent motion"]
date: 2026-09-25
status: complete
parent: ["[[FEEG1002 Mechanics, Materials and Structures Hub]]"]
prerequisites: ["[[FEEG1002 A1 - Forces, Equilibrium, Stress and Strain]]"]
next_topics: ["[[FEEG1002 D2 - Curvilinear Motion]]"]
key_concepts: ["[[Kinematic Relations for Rectilinear Motion]]", "[[Newton's Laws of Motion]]", "[[Coulomb Friction]]", "[[Dependent Motion and Pulley Constraints]]"]
tutorial_sheets: ["[[FEEG1002 Dynamics Tutorial 1 - Linear Motion Solutions]]"]
sources: ["02 - Sources/Dynamics/Lectures/Lecture 01 - Linear Motion.pdf"]
---

# FEEG1002 D1 - Linear Motion of Particles

> [!abstract] Summary
> A **particle** has mass but negligible size, so only the motion of its centre of mass matters and rotation is ignored. Along a straight line, three kinematic quantities are linked by calculus:
> $$v = \frac{ds}{dt},\qquad a = \frac{dv}{dt} = \frac{d^2s}{dt^2},\qquad a = v\frac{dv}{ds}$$
> **Kinetics** then links $a$ to forces through $\sum F = ma$, measured in an inertial (non-accelerating) frame. The chapter's toolkit has three parts:
> - **pick the integral** that matches how the force is given: as a function of $t$, $s$ or $v$;
> - **model the force**: gravity, friction, springs, ropes, drag, buoyancy;
> - **use cord-length constraints** to link blocks connected by pulleys.

## Key Concepts
- [[Kinematic Relations for Rectilinear Motion]] · [[Newton's Laws of Motion]] · [[Coulomb Friction]] · [[Dependent Motion and Pulley Constraints]] · [[Free Body Diagram and Equilibrium]]

---

## 1. Kinematics (L1.1)
- **Position** $s$ is measured from a fixed origin. Displacement is the change in position, $\Delta s = s' - s$.
- **Velocity**: $v = ds/dt$. It is a vector; its magnitude is the **speed**.
- **Acceleration**: $a = dv/dt$. A negative $a$ means the speed is decreasing *if* $v > 0$.
- The chain rule gives the form you need when $a$ depends on **position**:

$$
a = \frac{dv}{dt} = \frac{dv}{ds}\frac{ds}{dt} = v\frac{dv}{ds}
$$

**Which integral to use** (the lecture's summary table):

| You know... | Integrate | Result |
|---|---|---|
| $a(t)$ | $\int_{v_0}^v dv = \int_0^t a\,dt$ | $v(t)$ |
| $a(s)$ (springs, buoyancy, gravity with altitude) | $\int_{v_0}^v v\,dv = \int_{s_0}^s a\,ds$ | $v(s)$ |
| $a(v)$ (drag) | $\int_{s_0}^s ds = \int_{v_0}^v \frac{v}{a(v)}dv$ or $\int dt = \int \frac{dv}{a(v)}$ | $s(v)$, $t(v)$ |
| $v(t)$ | $\int ds = \int v\,dt$ | $s(t)$ |

**Constant acceleration** (the "SUVAT" equations; valid **only** if $a$ is constant):

$$
v = v_0 + a_ct,\qquad s = s_0 + v_0t + \tfrac12a_ct^2,\qquad v^2 = v_0^2 + 2a_c(s - s_0)
$$

![[d_t1_q1_boat_kinematics.png|700]]

> [!example] Tutorial 1 Q1: boat, $s = 4t + 1.6t^2 - 0.08t^3$
> - Differentiate: $v = 4 + 3.2t - 0.24t^2$ and $a = 3.2 - 0.48t$.
> - At $t = 4$ s: $v = 12.96$ m/s and $a = 1.28$ m/s².
> - Maximum $v$ where $a = 0$: $t = 6.67$ s, $v_{max} = 14.7$ m/s. Check the ends of the interval too: 9.44 m/s at 2 s and 12.0 m/s at 10 s.

## 2. Newton's laws and inertial frames (L1.2)
1. **Inertia**: with no resultant force, a particle stays at rest or moves at constant velocity.
2. $\sum\mathbf F = m\mathbf a$. **Mass** measures resistance to changes of velocity (kg).
3. **Action and reaction**: forces between two particles are equal, opposite and collinear.

**Procedure**, used identically in every later chapter:
1. Choose positive directions.
2. Draw the **free-body diagram (FBD)**, exactly as in [[FEEG1002 A1 - Forces, Equilibrium, Stress and Strain]].
3. Draw the **kinetic diagram** with $m\mathbf a$ pointing in the positive direction.
4. Equate the two: $\sum F_x = ma_x$.

$\sum F = ma$ holds only in an **inertial frame**, one that does not accelerate. Near the Earth's surface we treat the Earth as inertial and ignore its rotation. For satellites and rockets the frame is "fixed to the stars". Lecture 1's film clip shows the idea: a ball dropped in a cart moving at constant speed lands at the foot of the mast, but in an accelerating cart it does not.

## 3. Typical forces (L1.3)

| Force | Model | Makes $a$ a function of... |
|---|---|---|
| Gravitational attraction | $F_g = Gm_1m_2/r^2$, $G = 6.674\times10^{-11}$ m³ kg⁻¹ s⁻² | $s$ (radius) |
| Weight near the surface | $W = mg$, $g_0 = GM_e/R_e^2 \approx 9.81$ m/s² | constant |
| Static friction | $F_s \le \mu_sN$ (an upper limit only) | from equilibrium |
| Kinetic friction | $F_k = \mu_kN$, opposing sliding, $\mu_k < \mu_s$ | constant |
| Spring | $F_e = k\,\Delta l = k(l - l_0)$ | $s$ |
| Rope tension | $T \ge 0$, massless and inextensible | coupled to $a$ |
| Drag | $F_D = \tfrac12\rho_fSC_Dv^2 = Cv^2$ (or $cv$ at low speed) | $v$ |
| Buoyancy (Archimedes) | $F_B = \rho_fV_sg$ | $s$ (submerged volume) |

- **Mass and weight**: mass is absolute; weight depends on the local field.
- **Gravity with altitude**: $g(y) = g_0R_e^2/(R_e + y)^2$. At the ISS, $g$ is still 88.5% of $g_0$. Astronauts are "weightless" because they are in free fall, not because gravity has vanished.

![[d_gravity_vs_altitude.png|680]]

- **Friction** ([[Coulomb Friction]]): $F_s \le \mu_sN$ **cannot be used to calculate** $F_s$. Find $F_s$ from equilibrium, then check it against $\mu_sN$. Once sliding starts, $F_k = \mu_kN$ *is* the force. The model assumes dry, unlubricated surfaces, with friction independent of contact area and speed.

![[d_coulomb_friction.png|900]]

- **Rope tension depends on the motion**: a mass hanging on a rope has $T = mg$ in equilibrium but $T = m(g + a)$ when accelerating upwards.
- **Terminal velocity**: with drag $mg - cv^2 = ma$, the speed approaches $v_t = \sqrt{mg/c}$, where drag balances weight.

![[d_drag_terminal_velocity.png|900]]

> [!example] Tutorial 1 Q5: bungee, $m = 85$ kg, 50 m drop, cord engages after 20 m
> - Free fall to 20 m: $v = \sqrt{2g(20)} = 19.8$ m/s.
> - Just reaching the water, energy gives $mg(50) = \tfrac12k(30)^2$, so $k_{min} = 92.7$ N/m.
> - $a = 0$ where $k(x - 20) = mg$, at $x = 29.0$ m. This is where the speed peaks: $v_{max} = 21.9$ m/s, **not** at the moment the cord engages.
> - The largest deceleration, 22.9 m/s² ($2.3g$), occurs at the lowest point.
>
> ![[d_t1_q5_bungee.png|900]]

## 4. Dependent motion: pulleys (L1.4)
Blocks joined by an **inextensible** cord over **massless, frictionless** pulleys have linked motions.

**Kinematics recipe** ([[Dependent Motion and Pulley Constraints]]):
1. Measure each position coordinate from a **fixed datum**, positive in that block's direction of motion.
2. Write total cord length = sum of the variable segments + constant segments. The constant segments (arcs over pulleys, fixed lengths) drop out.
3. With several cords, write **one equation per cord** and eliminate the intermediate coordinates.
4. Differentiate for velocities and accelerations, keeping signs consistent.

**Kinetics**: a massless, frictionless pulley means **one tension throughout each cord**. A pulley carrying $n$ strands transmits $nT$. That gives a **mechanical advantage**: more lifting force, but proportionally less acceleration and speed. The anchor forces also grow, so check the anchor points.

![[d_pulley_constraints.png|940]]

| Arrangement | Constraint | Kinematics | Force on B |
|---|---|---|---|
| (a) one cord, movable pulley on B | $2s_B + s_A$ = const | $2v_B = -v_A$ | $2T$ |
| (b) two cords (lecture example) | $s_A + 4s_B$ = const | $v_A = -4v_B$ | $4T$ |

Pulling A down at 2 m/s in (b) lifts B at 0.5 m/s.

> [!example] Tutorial 1 Q11: concrete block A (150 kg) drags log D (250 kg, $\mu_k = 0.5$) up a 30° ramp
> - The cord from A passes over B, around pulley C on the log, and back to B. So $s_A + 2s_C$ = const and $a_A = 2a_D$.
> - A: $m_Ag - T = m_A(2a_D)$.
> - D: $2T - m_Dg(\sin30° + \mu_k\cos30°) = m_Da_D$.
> - Result: $a_D = 0.770$ m/s², $a_A = 1.54$ m/s², $T = 1240$ N. A hits the ground after 6 m at 4.30 m/s.
> - Pulley B carries three strands: $R_B = 3282$ N.
>
> ![[d_t1_q11_log_and_block_fbds.png|920]]

## Year 2 bridge
- **Everything in SESA2027 starts here**: [[SESA2027 A1 - Dynamic Systems and Aircraft Equations of Motion]] writes $\sum F = m\dot{\mathbf v}$ for a rigid aircraft. It uses a **body-fixed (non-inertial)** frame, which is why extra $\boldsymbol\omega\times\mathbf v$ terms appear. The inertial-frame warning in §2 is exactly why.
- **Integrating $a(s)$ and $a(v)$** is the separable-ODE toolkit. Linear versions with springs and dampers become the second-order ODEs of [[MATH2048 ODE1 - Second-Order Linear ODEs with Constant Coefficients]] and [[FEEG1002 D6 - Single Degree of Freedom Vibration]].
- **Gravity with altitude** leads to orbital mechanics: [[SESA2024 02 - Kepler's Laws and the Orbit Equation]], [[Vis-Viva Equation]].
- **Drag** $\tfrac12\rho SC_Dv^2$ is the same drag equation used throughout [[SESA2022 Aerodynamics Hub]].
- **Springs as structures**: the spring stiffness $k$ of a real structure comes from beam theory ($k = 3EI/L^3$ for a cantilever, [[SESA2028 S2 - Beam Deflection and Bending Design]]).

## Links
- Previous: [[FEEG1002 A1 - Forces, Equilibrium, Stress and Strain]] (FBDs) · Next: [[FEEG1002 D2 - Curvilinear Motion]]
- Worked problems: [[FEEG1002 Dynamics Tutorial 1 - Linear Motion Solutions]]

## Sources
- Dynamics Lecture 1 (G. Squicciarini): 1.1 kinematics, 1.2 Newton's laws, 1.3 typical forces, 1.4 dependent motion
