---
title: "SESA2023 Problem Sheet 1 Solutions"
module: "SESA2023 Propulsion"
type: tutorial
stream: "Section 1: Introduction and Fundamentals"
tags:
  - sesa2023
  - tutorial-solutions
  - thrust
  - efficiency
  - breguet-range
sheet: "Problem Sheet 1: Introduction"
theory_notes: ["[[SESA2023 W01 - Thrust, Efficiency, Range and the ISA]]"]
key_concepts: ["[[Thrust Equation]]", "[[Propulsive Efficiency]]", "[[Thermal and Overall Efficiency]]", "[[Thrust Specific Fuel Consumption]]", "[[Breguet Range Equation]]"]
status: complete
sources: ["02 - Sources/Tutorial Sheets/Problem Sheet Week 01.pdf"]
---

# SESA2023 Problem Sheet 1 Solutions

> [!abstract] Sheet Info
> Four questions on the momentum thrust equation, efficiencies and range. All the printed answers are reproduced ✔.
>
> One qualification: in Q1.4 the $f\ll1$ error at the actual $f$ is **0.15 percentage points**, slightly more than the sheet's "less than 0.1". The conclusion (the approximation is fine) stands.

## Theory Links
- [[SESA2023 W01 - Thrust, Efficiency, Range and the ISA]]
- [[Thrust Equation]] · [[Propulsive Efficiency]] · [[Thermal and Overall Efficiency]] · [[Thrust Specific Fuel Consumption]] · [[Breguet Range Equation]]

---

## Q1.1: LH₂/LOX rocket, 2000 kN, $V_j = 4000$ m/s, O/F = 7.94, $\rho_e = 39.8$ g/m³

### (a) Propellant for 1 minute (fully expanded, so $F = \dot mV_j$)

$$
\dot m = \frac{F}{V_j} = \frac{2\times10^6}{4000} = 500\text{ kg/s}\;\Rightarrow\;m = 30{,}000\text{ kg in 60 s}
$$

The mass fraction of H₂ is $1/(1+7.94) = 0.1119$, so

$$
m_{H_2} = \boxed{3356\text{ kg}},\qquad m_{O_2} = \boxed{26{,}644\text{ kg}}\;✔
$$

### (b) Thrust in vacuum (same exit state)
The exit area follows from continuity: $A_e = \dot m/(\rho_eV_j) = 500/(0.0398\times4000) = 3.141$ m². In (a) the exit pressure equalled sea-level atmospheric, $P_e = 101.325$ kPa. In vacuum $P_A = 0$, so

$$
F_{vac} = \dot mV_j+A_eP_e = 2000+3.141(101.325) = \boxed{2318\text{ kN}}\;✔
$$

The nozzle is choked and unchanged, so $\dot m$ and $V_j$ are unchanged. Only the pressure term appears.

## Q1.2: Jet engine at 200 m/s, $\rho = 0.74$ kg/m³, $A_1 = 4.5$ m², $F = 140$ kN, TSFC = 17 mg N⁻¹ s⁻¹, LCV 40 MJ/kg

### (a) Fuel flow and fuel–air ratio

$$
\dot m_f = \text{TSFC}\times F = 17\times10^{-6}\times140\times10^3 = \boxed{2.38\text{ kg/s}}
$$

$$
\dot m_a = \rho A_1V_0 = 0.74(4.5)(200) = 666\text{ kg/s},\qquad f = \frac{2.38}{666} = \boxed{0.00357}\ (≈0.004)\;✔
$$

### (b) Jet velocity (fully expanded)

$$
F = \dot m_a[(1+f)V_j-V_0]\;\Rightarrow\;V_j = \frac{F/\dot m_a+V_0}{1+f} = \frac{210.2+200}{1.00357} = \boxed{408.7\text{ m/s}}\;✔
$$

### (c) Efficiencies
- Jet power: $\dot W_{jet} = \tfrac12(666)[(1.00357)(408.7)^2-200^2] = 42.52$ MW.
- Fuel power: $\dot m_fLCV = 95.2$ MW.
- Aircraft power: $FV_0 = 28.0$ MW.

$$
\eta_{th} = \frac{42.52}{95.2} = \boxed{44.7\%},\qquad\eta_P = \frac{28.0}{42.52} = \boxed{65.9\%},\qquad\eta_O = \frac{28.0}{95.2} = \boxed{29.4\%}\;✔
$$

Check: $0.447\times0.659 = 0.294$ ✔.

## Q1.3: Aircraft with two such engines, 100 t of fuel

### (a) Range at constant thrust and fuel flow
The total fuel flow is $2(2.38) = 4.76$ kg/s, which gives an endurance of $100{,}000/4.76 = 21{,}008$ s. Then

$$
s = V_0t = 200(21{,}008) = \boxed{4202\text{ km}}\;✔
$$

### (b) Mass without fuel, if $L/D = 10$
Breguet with range 4202 km:

$$
\ln\frac{W_1}{W_2} = \frac{s\,g_0\,\text{TSFC}}{V_0(L/D)} = \frac{4.202\times10^6(9.81)(17\times10^{-6})}{200(10)} = 0.3504\;\Rightarrow\;\frac{W_1}{W_2} = 1.4196
$$

$$
W_1-W_2 = 100\text{ t}\;\Rightarrow\;m_2 = \frac{100}{0.4196} = \boxed{238\text{ t}}\;✔
$$

Part (a) held the thrust constant while the weight fell, which isn't strictly consistent with $F = D = W/(L/D)$. Part (b) uses Breguet (constant $L/D$) to back out the mass that gives this range.

## Q1.4: Error of the $f\ll1$ approximation in $\eta_P$
Use $V_0 = 200$ m/s and $V_j = 408.7$ m/s. The exact form is $\eta_P = \dfrac{V_0[(1+f)V_j-V_0]}{\tfrac12[(1+f)V_j^2-V_0^2]}$, and the approximate form is $2/(1+V_j/V_0) = 0.6571$.

| $f$ | $\eta_P$ exact | error (percentage points) |
|---|---|---|
| 0 | 0.6571 | 0.00 |
| 0.00357 (actual) | 0.6586 | 0.15 |
| 0.02 | 0.6653 | 0.82 |
| 0.05 | 0.6769 | 1.98 |
| 0.10 | 0.6944 | 3.74 |

The error grows almost linearly, by about 0.37 points per 0.01 of $f$. For Q1.2 ($f = 0.0036$) the approximation is **appropriate**: 65.7 % against 65.9 %.

## Sources
- `02 - Sources/Tutorial Sheets/Problem Sheet Week 01.pdf`. All values checked in Python.
