---
title: "SESA2023 Exam 2022-23 Solutions"
module: "SESA2023 Propulsion"
type: exam-solution
year: "2022-23"
tags: [sesa2023, exam-solutions, past-papers, closed-book]
topics: ["[[SESA2023 W03 - Compressible Flow, Normal Shocks and Nozzles]]", "[[SESA2023 W10 - Rocket Performance, Staging and Power Cycles]]", "[[SESA2023 W06 - Jet Engine Cycle Analysis - Brayton, Ramjet, Turbojet and Reheat]]", "[[SESA2023 W08 - Turbomachinery Principles - Euler Equation and Velocity Triangles]]", "[[SESA2023 W09 - Turbomachinery Characteristics - Coefficients, Similarity and Maps]]"]
status: complete
sources: ["03 - Exams & Past Papers/SESA2023-202223-02-SESA2023.pdf"]
---

# SESA2023 Exam 2022-23 Solutions

> [!info] Paper
> Answer all four questions, 25 marks each. The Thermofluids Data Book is provided. Cold air: $R = 287$, $\gamma = 1.4$, $c_p = 1005$ unless stated.

## Q1: Normal shock in a test facility

### (i) Mach numbers either side (3)
A normal shock only forms in **supersonic** flow, and it is a compression. So **$M_1>1$ and $M_2<1$**. The downstream Mach number is a unique function of $M_1$ (and $\gamma$), and $M_2\to\sqrt{(\gamma-1)/2\gamma} = 0.378$ as $M_1\to\infty$.

### (ii) Conserved and non-conserved stagnation properties (4)
- **$T_0$ (equivalently $h_0$) is conserved**: the shock is adiabatic and does no work (SFEE: $h_1+V_1^2/2 = h_2+V_2^2/2$).
- **$p_0$ is not conserved; it falls**: the shock is irreversible and generates entropy, and $p_{02}/p_{01} = e^{-\Delta s/R}<1$.

### (iii)(a) Mach numbers from pressure measurements (4)
$T_1 = 170$ K, $p_1 = 200$ kPa, $p_2 = 800$ kPa. Invert the static pressure ratio:

$$
\frac{p_2}{p_1} = 1+\frac{2\gamma}{\gamma+1}(M_1^2-1) = 4\;\Rightarrow\;M_1^2 = 1+\frac{3(2.4)}{2.8} = 3.571,\qquad \boxed{M_1 = 1.890}
$$

$$
M_2^2 = \frac{1+0.2M_1^2}{1.4M_1^2-0.2} = \frac{1.7143}{4.8}\;\Rightarrow\;\boxed{M_2 = 0.598}
$$

### (iii)(b) Velocities (7)
$$
a_1 = \sqrt{1.4(287)(170)} = 261.4\text{ m/s},\qquad \boxed{U_1 = 1.890(261.4) = 494\text{ m/s}}
$$

$$
\frac{T_2}{T_1} = \frac{p_2/p_1}{\rho_2/\rho_1} = \frac{4}{2.5} = 1.6\;\Rightarrow\;T_2 = 272\text{ K}
$$

$$
\boxed{U_2 = 0.598\sqrt{1.4(287)(272)} = 198\text{ m/s}}
$$

Check with continuity: $U_2 = U_1/(\rho_2/\rho_1) = 494/2.5 = 198$ ✓.

### (iv) Minimum vessel pressure (7)
The vessel is a reservoir at rest, so its pressure is the stagnation pressure of the flow. The **minimum** is when the expansion to state 1 is isentropic (any loss would need more):

$$
p_{vessel,min} = p_{01} = p_1\left(1+0.2M_1^2\right)^{3.5} = 200(1.7143)^{3.5} = \boxed{1.32\text{ MPa}\ (13.2\text{ bar})}
$$

- $T_0 = 170(1.7143) = 291$ K, so the vessel can sit at room temperature. That is a neat check on the design.
- After the shock $p_{02} = 0.772p_{01} = 1.02$ MPa ($\Delta s = 74$ J kg⁻¹ K⁻¹).

See [[Normal Shock Waves]] and [[Stagnation Properties]].

---

## Q2: Rocket engine ($I_{sp} = 306$ s, 50 bar, 5000 K, $A_t = 0.05$ m², cold air)

### (i) Does altitude affect $\dot m$? (3)
**No**, provided the nozzle is choked (always true for a rocket, since $p_c/p_a\gg1.89$). The throat is sonic, so $\dot m = A_tp_c\sqrt{\gamma/RT_c}(\ldots)$ depends only on the chamber state and the throat area. Changes in back pressure cannot propagate upstream through the sonic throat.

### (ii) Mass flow in vacuum (8)
$$
\dot m = A_tp_c\sqrt{\frac{\gamma}{RT_c}}\left(\frac{2}{\gamma+1}\right)^{\frac{\gamma+1}{2(\gamma-1)}} = 0.05(50\times10^5)\sqrt{\frac{1.4}{287(5000)}}(0.5787) = \boxed{142.9\text{ kg/s}}
$$

This is the same at any altitude, from (i).

### (iii) $C^*$, $C_F$ and thrust (5)
Take $g_0 = 9.81$:

$$
C^* = \frac{p_cA_t}{\dot m} = \boxed{1749\text{ m/s}},\qquad c_e = g_0I_{sp} = 3002\text{ m/s},\qquad C_F = \frac{c_e}{C^*} = \boxed{1.716},\qquad F = \dot mc_e = \boxed{429\text{ kN}}
$$

### (iv) Exit pressure and area (9)
Pressure thrust is ignored, so $c_e = V_e$, and the SFEE and isentropic nozzle give:

$$
V_e^2 = 2c_pT_c\left[1-\left(\frac{p_e}{p_c}\right)^{0.2857}\right]\;\Rightarrow\;\frac{p_e}{p_c} = \left(1-\frac{3002^2}{2(1005)(5000)}\right)^{3.5} = (0.10336)^{3.5} = 3.55\times10^{-4}
$$

$$
\boxed{p_e = 1.78\text{ kPa}}
$$

$M_e$ from $p_c/p_e = 2816$ is 6.59. The area–Mach relation then gives $A_e/A_t = 79.6$:

$$
\boxed{A_e = 3.98\text{ m}^2}
$$

(Check with continuity, $A_e = \dot m/(\rho_eV_e)$: 3.98 m² ✓.) This is a vacuum-type nozzle (diameter 2.25 m). At sea level it would be grossly over-expanded. See [[Rocket Performance Parameters]] and [[Rocket Nozzle Geometry]].

---

## Q3: Power-generation gas turbine

### (i) Raising TET: pros and cons (5)
- **Advantages**:
  - higher **specific work** (smaller, lighter engine per MW);
  - higher **thermal efficiency** (the optimum pressure ratio also rises);
  - better part-load flexibility and higher exhaust temperature for combined-cycle heat recovery.
- **Disadvantages**:
  - blade creep, oxidation and thermal fatigue, so shorter life;
  - needs expensive single-crystal alloys, TBCs and **cooling air** (15–25 % of the flow), which itself costs efficiency;
  - higher **NOₓ** (thermal NOₓ grows exponentially with flame temperature);
  - higher cost and maintenance.

See [[Turbine Entry Temperature and Blade Cooling]].

### (ii) Compressor pressure ratio (6)
Turbine: products with $\gamma = 1.33$, $\eta_t = 0.9$ and $p_{03}/p_{04} = p_{02}/p_{01} = r_p$ (no combustor loss; $p_{01} = p_{04}$).

$$
T_{04s} = T_{03}-\frac{T_{03}-T_{04}}{\eta_t} = 1650-\frac{750}{0.9} = 816.7\text{ K}
$$

$$
r_p = \left(\frac{T_{03}}{T_{04s}}\right)^{\gamma/(\gamma-1)} = (2.0204)^{4.030} = \boxed{17.0}
$$

### (iii) $T_{02}$ (4)
$T_{01} = T_1 = 288$ K (stationary intake):

$$
T_{02s} = 288(17.02)^{0.2857} = 647.3\text{ K},\qquad T_{02} = 288+\frac{359.3}{0.9} = \boxed{687.2\text{ K}}
$$

### (iv) Fuel-air ratio with combustor heat loss (10)
SFEE on the combustor, with 298 K reference, gaseous fuel at 298 K, and a heat loss of 2 MJ per kg of fuel:

$$
\dot m_ac_{p,a}(T_{02}-298)+\dot m_f\,LCV-\dot m_fq_{loss} = (\dot m_a+\dot m_f)c_{p,g}(T_{03}-298)
$$

$$
f = \frac{c_{p,g}(T_{03}-298)-c_{p,a}(T_{02}-298)}{LCV-q_{loss}-c_{p,g}(T_{03}-298)} = \frac{1100(1352)-1005(389.2)}{26\times10^6-2\times10^6-1100(1352)} = \frac{1.0960\times10^6}{22.513\times10^6} = \boxed{0.0487}
$$

Without the heat loss it would be 0.0447, so the loss needs about 9 % more fuel. The fuel is low-grade (26 MJ/kg, like a syngas or biogas), hence the large $f$. See [[Adiabatic Flame Temperature]] and [[Steady Flow Energy Equation]].

---

## Q4: Axial turbine stage

### (i) Flow and stage-loading coefficients (4)
$$
\phi = \frac{V_x}{U},\qquad \psi = \frac{\Delta h_0}{U^2} = \frac{\Delta V_\theta}{U}\ (\text{by Euler})
$$

- $V_x$: axial velocity.
- $U = \Omega r$: blade speed at the mean radius.
- $\Delta h_0$: specific stagnation-enthalpy drop across the stage.
- $\Delta V_\theta$: change in absolute swirl velocity across the rotor.

See [[Flow and Work Coefficients]].

### (ii) Raising $\psi$: one advantage, one disadvantage (4)
- **Advantage**: more work per stage, so **fewer stages** for a given duty. The turbine is shorter, lighter and cheaper, with fewer aerofoils to cool.
- **Disadvantage**: larger flow turning and higher exit Mach numbers (and larger exit swirl) mean **lower efficiency** (profile, secondary and shock losses). See the Smith chart; the practical limit is $\psi\lesssim2.5$.

### (iii) Stator exit static state (6)
$c_p = 1050$, $\gamma = 1.37$ ($\gamma/(\gamma-1) = 3.703$). The stator does no work and is isentropic, so $T_0 = 1000$ K and $p_0 = 10$ bar are unchanged.

$$
V_2 = \frac{V_x}{\cos60^\circ} = 400\text{ m/s},\qquad T_2 = 1000-\frac{400^2}{2(1050)} = \boxed{923.8\text{ K}}
$$

$$
p_2 = 10\left(\frac{923.8}{1000}\right)^{3.703} = \boxed{7.46\text{ bar}}\quad(M_2 = 0.668)
$$

### (iv) Rotor blade angles (11)
$U = 350$ m/s and $w = 100$ kJ/kg. Euler: $w = U(V_{\theta2}-V_{\theta3})$, so $\Delta V_\theta = 285.7$ m/s.

![[prop_e2223_q4_turbine_triangles.png|720]]

| | $V_\theta$ | $\alpha$ | $W_\theta = V_\theta-U$ | $\beta$ (relative, from axial) | $W$ |
|---|---|---|---|---|---|
| Rotor inlet (2) | 346.4 | 60.0° | −3.6 | **−1.0°** | 200.0 |
| Rotor exit (3) | 60.7 | 16.9° | −289.3 | **−55.3°** | 351.7 |

With zero incidence and zero deviation, the **blade metal angles equal the relative flow angles**: inlet −1.0° (practically axial) and exit −55.3°. Also $\phi = 0.571$ and $\psi = 0.816$. The relative flow accelerates from 200 to 352 m/s, so the rotor is a reaction design. The exit keeps 16.9° of residual swirl (a small leaving loss).

## Related
- [[SESA2023 Past Paper Map]] · [[SESA2023 Propulsion Hub]] · [[SESA2023 Formula Sheet]]
- Script: `04 - Scripts/verify_past_papers.py` (section "2022-23")
