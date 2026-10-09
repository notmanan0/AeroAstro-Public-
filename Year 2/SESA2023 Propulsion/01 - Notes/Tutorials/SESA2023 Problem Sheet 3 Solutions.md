---
title: "SESA2023 Problem Sheet 3 Solutions"
module: "SESA2023 Propulsion"
type: tutorial
stream: "Section 1: Introduction and Fundamentals"
tags:
  - sesa2023
  - tutorial-solutions
  - compressible-flow
  - nozzles
sheet: "Problem Sheet 3: Gas dynamics"
theory_notes: ["[[SESA2023 W03 - Compressible Flow, Normal Shocks and Nozzles]]"]
key_concepts: ["[[Stagnation Properties]]", "[[Isentropic Nozzle Flow]]", "[[Critical Conditions and Choked Flow]]", "[[Normal Shock Waves]]"]
status: complete
sources: ["02 - Sources/Tutorial Sheets/Problem Sheet Week 03.pdf"]
---

# SESA2023 Problem Sheet 3 Solutions

> [!abstract] Sheet Info
> Four questions on isentropic nozzle states, a supersonic Pitot reading, rocket nozzle sizing, and the two branches of $A/A^*$. All the printed answers are reproduced ✔. Air throughout: $\gamma = 1.4$, $R = 287$, $c_p = 1005$.

## Theory Links
- [[SESA2023 W03 - Compressible Flow, Normal Shocks and Nozzles]]
- [[Stagnation Properties]] · [[Isentropic Nozzle Flow]] · [[Critical Conditions and Choked Flow]] · [[Normal Shock Waves]]

---

## Q3.1: Nozzle fed from a pipe, $A_1 = 10$ cm², 10 bar, 400 K, 1 kg/s
### (a) Stagnation state

$$
\rho_1 = \frac{10^6}{287(400)} = 8.711\text{ kg/m}^3,\quad U_1 = \frac{1}{8.711(0.001)} = 114.8\text{ m/s}
$$

$$
T_0 = 400+\frac{114.8^2}{2010} = \boxed{406.6\text{ K}},\qquad p_0 = 10\Big(\frac{406.6}{400}\Big)^{3.5} = \boxed{1058.6\text{ kPa}}\;✔
$$

### (b) States from the measured pressures
Isentropic: $M = \sqrt{5[(p_0/p)^{0.2857}-1]}$, $T = T_0/(1+0.2M^2)$, $U = M\sqrt{\gamma RT}$, $A = \dot m/(\rho U)$.

| Point | $p$ (kPa) | $M$ | $T$ (K) | $U$ (m/s) | $A$ (cm²) |
|---|---|---|---|---|---|
| 2 | 800 | **0.65** | **375** | **251** | **5.37** |
| 3 | 559 | **1.00** | **339** | **369** | **4.71** (throat, $A^*$) |
| 4 | 135 | **2.00** | **226** | **603** | **7.96** |

All match the sheet ✔. Point 3 is sonic, so it is the throat: $A^* = \dot m\sqrt{T_0}/(0.0404\,p_0) = 4.71$ cm².

## Q3.2: Sphere in a 500 m/s, 300 K, 1 bar tunnel
$a = \sqrt{1.4(287)(300)} = 347.2$ m/s, so $M = 1.44$ and the flow is **supersonic**. A bow shock stands ahead of the sphere, and the stagnation point sits behind its normal part.

- Isentropic $p_0 = 1\times(1+0.2\times1.44^2)^{3.5} = 3.37$ bar. This would be wrong here.
- Normal shock at $M = 1.44$: $p_{02}/p_{01} = 0.948$.

$$
p_{tip} = p_{02} = 3.37(0.948) = \boxed{319\text{ kPa}}\;✔
$$

## Q3.3: Rocket nozzle, 185 kN at 100 kg/s, $T_0 = 2000$ K, $p_0 = 10$ bar, air properties
### (a) Exit Mach and throat diameter
- Ignoring the pressure term, $V_e = F/\dot m = 1850$ m/s.
- $T_e = 2000-1850^2/2010 = 297.3$ K, so $M_e = 1850/\sqrt{1.4(287)(297.3)} = \boxed{5.35}$.
- The nozzle is choked: $A_t = \dfrac{\dot m\sqrt{T_0}}{0.0404\,p_0} = 0.1106$ m², so $d_t = \boxed{0.375\text{ m}}$ ✔.

### (b) Exit diameter and pressure
- $A_e/A^* = 32.97$ at M 5.35, so $A_e = 3.648$ m² and $d_e = \boxed{2.155\text{ m}}$.
- $p_e = p_0/(1+0.2M_e^2)^{3.5} = \boxed{1264\text{ Pa}}$ ✔.

### (c) Best altitude
Best performance comes when fully expanded, $p_a = p_e = 1.26$ kPa. ISA Table 25 gives 1.39 kPa at 29 km and 1.20 kPa at 30 km, so the best altitude is **≈ 30 km** ✔.

## Q3.4: Area 6 cm² in the Q3.1 nozzle
$A^* = 4.712$ cm², so $A/A^* = 1.273$. Solve $A/A^* = \dfrac1M\Big[\dfrac{2}{\gamma+1}\big(1+\tfrac{\gamma-1}{2}M^2\big)\Big]^{3}$ numerically.

| Branch | $M$ | $p = p_0/(1+0.2M^2)^{3.5}$ |
|---|---|---|
| (a) subsonic (upstream of the throat) | **0.54** | **869 kPa** |
| (b) supersonic (downstream) | **1.63** | **239 kPa** |

Both match ✔. See `prop_area_mach.png` in [[SESA2023 W03 - Compressible Flow, Normal Shocks and Nozzles]].

## Sources
- `02 - Sources/Tutorial Sheets/Problem Sheet Week 03.pdf`. Solved numerically with a bisection search (`brentq`).
