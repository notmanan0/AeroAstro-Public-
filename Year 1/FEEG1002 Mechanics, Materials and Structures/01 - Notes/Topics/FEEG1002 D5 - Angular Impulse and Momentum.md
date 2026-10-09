---
title: "FEEG1002 D5 - Angular Impulse and Momentum"
module: "FEEG1002 Mechanics, Materials and Structures"
type: topic
stream: "Part D: Dynamics"
order: 5
tags: [feeg1002, dynamics, angular-momentum, central-force, orbits]
aliases: ["Dynamics Lecture 5", "Angular momentum", "Conservation of angular momentum", "Central force motion"]
date: 2026-09-25
status: complete
parent: ["[[FEEG1002 Mechanics, Materials and Structures Hub]]"]
prerequisites: ["[[FEEG1002 D4 - Linear Impulse and Momentum]]"]
next_topics: ["[[FEEG1002 D6 - Single Degree of Freedom Vibration]]"]
key_concepts: ["[[Principle of Angular Impulse and Momentum]]", "[[Orbital Angular Momentum]]"]
tutorial_sheets: ["[[FEEG1002 Dynamics Tutorial 5 - Angular Impulse and Momentum Solutions]]"]
sources: ["02 - Sources/Dynamics/Lectures/Lecture 05 - Angular Impulse and Momentum.pdf"]
---

# FEEG1002 D5 - Angular Impulse and Momentum

> [!abstract] Summary
> The **angular momentum** of a particle about a point O is the moment of its linear momentum, $\mathbf H_O = \mathbf r\times m\mathbf v$. Crossing $\sum\mathbf F = \dot{\mathbf L}$ with $\mathbf r$ gives $\sum\mathbf M_O = \dot{\mathbf H}_O$. Integrating over time:
> $$(\mathbf H_O)_1 + \sum\int_{t_1}^{t_2}\mathbf M_O\,dt = (\mathbf H_O)_2$$
> If every force passes through O (a **central force**), the angular impulse is zero and $H_O = rmv_\perp$ is **conserved**. Pull a whirling mass inwards and it speeds up. A satellite moves faster at perigee than apogee.

## Key Concepts
- [[Principle of Angular Impulse and Momentum]] · [[Orbital Angular Momentum]] · [[Kepler's Laws]]

---

## 1. Moments of vectors (L5.1)
- **Moment of a force**: $\mathbf M_O = \mathbf r\times\mathbf F$, evaluated with the determinant of $\mathbf i, \mathbf j, \mathbf k$.
- **In 2D** it has only a $\mathbf k$ component:

$$
\mathbf M_O = (r_xF_y - r_yF_x)\mathbf k = rF\sin\theta\,\mathbf k
$$

- Two equivalent ways to compute $rF\sin\theta$:
  - the force component **perpendicular** to $\mathbf r$, times $r$;
  - $F$ times the **perpendicular distance** $d = r\sin\theta$ from O to the line of action.
- It is zero when the force passes through O ($\theta = 0°$ or $180°$).
- **Moment of momentum** works the same way: $\mathbf H_O = \mathbf r\times m\mathbf v$, so $H_O = mv\,d = r\,mv_\perp$ in 2D.
- Directions follow the right-hand rule.

## 2. The principle (L5.1)
$$
\sum\mathbf r\times\mathbf F = \mathbf r\times m\dot{\mathbf v}\qquad\text{and}\qquad \dot{\mathbf H}_O = \underbrace{\dot{\mathbf r}\times m\mathbf v}_{\mathbf v\times m\mathbf v = 0} + \mathbf r\times m\dot{\mathbf v}\quad\Rightarrow\quad\sum\mathbf M_O = \dot{\mathbf H}_O
$$

- O must be fixed in an inertial frame.
- **Conservation**: $(\mathbf H_O)_1 = (\mathbf H_O)_2$ whenever the net angular impulse about O is zero.
- **Central-force examples**:
  - a car on a curve with $F_t = 0$;
  - a cord pulled towards the centre;
  - a spring pinned at one end;
  - gravity on planets and satellites.

## 3. Solved problem: pulling in the cable (L5.2)
A 120 kg ride car moves at $v_1 = 1.2$ m/s at $r_1 = 3.6$ m. The cable is then pulled in at $\dot r = 0.15$ m/s.

After 3 s, $r_2 = 3.6 - 0.45 = 3.15$ m. The cable force points at O, so $H_O$ is conserved:

$$
r_1mv_1 = r_2mv_2'\quad\Rightarrow\quad v_2' = \frac{3.6(1.2)}{3.15} = 1.371\ \text{m/s},\qquad v_2 = \sqrt{1.371^2 + 0.15^2} = \mathbf{1.38}\ \text{m/s}
$$

The **work done by the cable** equals the gain in kinetic energy: $U = \tfrac12m(v_2^2 - v_1^2)$ = **27.9 J**.
- Angular momentum is conserved but KE is **not**. The cable force has a component along the (spiral) path and does work.
- The cable force is not constant, so $\int\mathbf F\cdot d\mathbf s$ would be awkward; energy gets the answer directly.

![[d_central_force_ride.png|900]]

This is the figure-skater effect: reduce $r$ and the transverse speed $v' = r_1v_1/r$ rises.

## 4. Solved problem: elliptical orbit (L5.3)
A satellite has $v_A = 8333.3$ m/s at perigee $r_A = 6.976\times10^6$ m, with $GM_e = 3.988\times10^{14}$ m³/s². Two conservation laws hold:
- **energy** (gravity is conservative): $\tfrac12v_A^2 - GM/r_A = \tfrac12v_B^2 - GM/r_B$;
- **angular momentum** (gravity is central): $v_Ar_A = v_Br_B$. At perigee and apogee the velocity is perpendicular to $\mathbf r$.

Eliminate $r_B$ to get a quadratic in $v_B$. One root is $v_A$ itself (perigee); the other is apogee:

$$
v_B = \mathbf{5382}\ \text{m/s},\qquad r_B = \frac{v_Ar_A}{v_B} = \mathbf{10.80\times10^6}\ \text{m}
$$

![[d_elliptical_orbit_example.png|780]]

> [!tip] Where the tutorial goes further
> - **Tutorial 5 Q4**: the velocity is **not** perpendicular to $\mathbf r$ at A ($\phi_A = 70°$). Use $H = r_Av_A\sin\phi_A$.
> - **Tutorial 5 Q2**: tangential forces supply an angular impulse, $\int(F_2\cos\theta - \mu_kmg)R\,dt = mR\Delta v$. The cord tension follows from $\sum F_n = mv^2/R$.
>
> ![[d_t5_q2_cord_tension.png|700]]

## Year 2 bridge
- **Orbits**: angular momentum per unit mass $h = rv_\perp$ being constant is Kepler's second law (equal areas in equal times). With energy it gives the whole orbit: [[Orbital Angular Momentum]], [[Kepler's Laws]], [[Orbit Equation and Conic Sections]] ([[SESA2024 02 - Kepler's Laws and the Orbit Equation]]). The lecture's perigee/apogee calculation is a special case of the [[Vis-Viva Equation]] ([[SESA2024 04 - Orbital Energy and the Vis-Viva Equation]]).
- **Spacecraft attitude**: for a rigid body $\mathbf H = \mathbf I\boldsymbol\omega$ with the [[Inertia Matrix]]. Momentum wheels store and exchange $\mathbf H$ ([[Reaction Wheels and Momentum Dumping]], [[Momentum Bias and Gyroscopic Rigidity]], [[SESA2024 06 - Attitude Control]]). External torques (gravity gradient, solar pressure) are the "angular impulse" that eventually saturates the wheels.
- **Rigid bodies**: $\sum M_G = I_G\alpha$ in [[FEEG1002 D8 - Kinetics of Rigid Bodies]] is the rate form of this principle for a body.

## Links
- Previous: [[FEEG1002 D4 - Linear Impulse and Momentum]] · Next: [[FEEG1002 D6 - Single Degree of Freedom Vibration]]
- Worked problems: [[FEEG1002 Dynamics Tutorial 5 - Angular Impulse and Momentum Solutions]]

## Sources
- Dynamics Lecture 5: 5.1 principle of angular impulse and momentum; 5.2 central force (amusement ride); 5.3 elliptical orbit
