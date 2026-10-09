---
title: "SESA2023 Problem Sheet 4 Solutions"
module: "SESA2023 Propulsion"
type: tutorial
stream: "Section 3: Ramjets, Gas Turbines, Turbojets and Turbofans"
tags:
  - sesa2023
  - tutorial-solutions
  - ramjet
sheet: "Problem Sheet 4: Ramjets"
theory_notes: ["[[SESA2023 W06 - Jet Engine Cycle Analysis - Brayton, Ramjet, Turbojet and Reheat]]", "[[SESA2023 W04 - Friction, Heat Addition, Oblique Shocks and Intakes]]"]
key_concepts: ["[[Ramjet]]", "[[Component Stagnation Pressure Ratios]]", "[[Intake Pressure Recovery]]", "[[Normal Shock Waves]]"]
status: complete
sources: ["02 - Sources/Tutorial Sheets/Problem Sheet Week 04.pdf"]
---

# SESA2023 Problem Sheet 4 Solutions

> [!abstract] Sheet Info
> Four ramjet questions: ideal (flight speed from $f$ and $T_{max}$), real (with $\Gamma$ values and combustion efficiency), a normal-shock inlet, and perfect vs real gas.
>
> All the printed answers are reproduced ✔, using the energy balance
>
> $$(1+f)c_pT_{03} = c_pT_{02}+f\,LCV\qquad(\text{fuel enthalpy referenced to 0 K})$$
>
> With the lecture's $T_{ref} = 298$ K form the answers change by about 1 %. Q4.2(a) asks for the "air–fuel ratio" but the answer given (0.0521) is the **fuel–air** ratio.

## Theory Links
- [[SESA2023 W06 - Jet Engine Cycle Analysis - Brayton, Ramjet, Turbojet and Reheat]] · [[SESA2023 W04 - Friction, Heat Addition, Oblique Shocks and Intakes]]
- [[Ramjet]] · [[Component Stagnation Pressure Ratios]] · [[Intake Pressure Recovery]]

---

## Q4.1: Ideal ramjet at 10 km, $f = 0.04$, $T_{max} = 2400$ K, LCV 41 MJ/kg
The ISA at 10 km gives $T_a = 223.26$ K and $a = 299.5$ m/s.

### (a) Flight speed
The energy balance gives the combustor-inlet temperature:

$$
T_{02} = (1+f)T_{03}-\frac{f\,LCV}{c_p} = 1.04(2400)-\frac{0.04(41\times10^6)}{1005} = 864.2\text{ K}
$$

$$
M_0 = \sqrt{\frac{T_{02}/T_a-1}{0.2}} = \boxed{3.79},\qquad V_0 = 3.79(299.5) = \boxed{1135\text{ m/s}}\;✔
$$

### (b) Exhaust
Ideal ($p_{04} = p_{01}$, fully expanded), so $M_e = M_0 = \boxed{3.79}$.

$$
T_e = \frac{2400}{3.871} = 620\text{ K},\qquad V_e = 3.79\sqrt{1.4(287)(620)} = \boxed{1891\text{ m/s}}\;✔
$$

### (c) Specific thrust

$$
\frac{F}{\dot m_a} = (1+f)V_e-V_0 = 1.04(1891)-1135 = \boxed{832\text{ m/s}}\;✔
$$

## Q4.2: Real ramjet, M 3.5, 240 K, 12 kPa, $T_{03} = 2650$ K, $F = 49$ kN, LCV 42 MJ/kg, $\Gamma_d = 0.75$, $\Gamma_c = 0.90$, $\Gamma_n = 0.80$, $\eta_b = 0.90$

1. $T_{02} = 240(1+0.2\times3.5^2) = 828$ K and $V_0 = 3.5(310.5) = 1086.9$ m/s.
2. **(a)** $f = \dfrac{c_p(T_{03}-T_{02})}{\eta_bLCV-c_pT_{03}} = \dfrac{1005(1822)}{3.78\times10^7-2.663\times10^6} = \boxed{0.0521}$ ✔
3. Nozzle pressure ratio: $p_{04}/p_a = (3.45)^{3.5}(0.75)(0.90)(0.80) = 76.27(0.54) = 41.19$. The ideal value would be 76.3.
4. $T_4 = 2650/41.19^{0.2857} = 916.0$ K, so $V_e = \sqrt{2(1005)(2650-916)} = 1866.9$ m/s.
5. **(c)** $F/\dot m_a = 1.0521(1866.9)-1086.9 = \boxed{877\text{ m/s}}$ ✔ (sheet: 876.8)
6. **(b)** $\dot m_a = 49\,000/877.3 = \boxed{55.9\text{ kg/s}}$ ✔
7. **(d)** $\eta_O = \dfrac{FV_0}{\dot m_fLCV} = \dfrac{49\,000(1086.9)}{0.0521(55.9)(4.2\times10^7)} = \boxed{43.5\%}$ ✔. The *full* LCV is used here.

## Q4.3: Normal shock at the diffuser inlet, otherwise ideal; $T_{max} = 2000$ K, 250 K, 20 kPa, $f = 0.03$, LCV 41 MJ/kg
### (a) Maximum Mach number
The shock does not change $T_0$, so the energy balance fixes $T_{02}$:

$$
T_{02} = 1.03(2000)-\frac{0.03(41\times10^6)}{1005} = 836.1\text{ K}\;\Rightarrow\;M = \sqrt{\frac{836.1/250-1}{0.2}} = \boxed{3.42}\;✔
$$

### (b) Free-stream stagnation pressure

$$
p_{01} = 20\left(\frac{836.1}{250}\right)^{3.5} = 1368\text{ kPa} = \boxed{13.7\text{ bar}}\;✔
$$

### (c) After the diffuser
The normal shock at M 3.42 gives $p_{02}/p_{01} = 0.2275$, so $p_{02} = \boxed{3.1\text{ bar}}$ ✔. **77 % of the stagnation pressure is lost.** This is why Pitot intakes are only used below about M 1.8.

## Q4.4: Ideal ramjet at M 2.7, 250 K, 10 kPa, $T_{03} = 2400$ K, perfect vs real gas

| | Perfect gas (γ = 1.4) | Real gas (sheet, CoolProp) |
|---|---|---|
| (a) $a_\infty$ | $\sqrt{1.4(287)(250)} = 316.9$ m/s | 317.1 m/s |
| (b) $T_{02} = T_a(1+0.2M^2)$ | 614.5 K | 608.9 K |
| (c) $V_j = M\sqrt{\gamma RT_{03}/2.458}$ | 1691 m/s | 1757 m/s |
| (d) $M_j$ | 2.70 (equal to $M_0$) | 2.66 |

The real gas has a higher $c_p$ at high temperature, so the same $T_{03}$ holds more enthalpy, and more is released through the same pressure ratio. That gives a higher $V_j$ (+4 %). A larger $c_p$ also means a smaller temperature drop per unit enthalpy drop. The exit static temperature therefore stays higher, the exit speed of sound is higher, and $M_j$ comes out slightly *lower* (2.66). The perfect-gas model under-predicts the jet velocity by about 4 %.

## Sources
- `02 - Sources/Tutorial Sheets/Problem Sheet Week 04.pdf`. All values checked in Python.
