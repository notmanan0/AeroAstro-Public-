---
title: "SESA2023 Problem Sheet 10 Rockets Solutions"
module: "SESA2023 Propulsion"
type: tutorial
stream: "Section 5: Rockets"
aliases: ["SESA2023 Problem Sheet 6 Solutions", "SESA2023 Problem Sheet 10 Solutions"]
tags:
  - sesa2023
  - tutorial-solutions
  - rockets
  - staging
sheet: "Problem Sheet Week 10: Rockets (identical to Problem Sheet 6)"
theory_notes: ["[[SESA2023 W10 - Rocket Performance, Staging and Power Cycles]]", "[[SESA2023 W11 - Solid Propellants and Rocket Nozzle Design]]"]
key_concepts: ["[[Tsiolkovsky Rocket Equation]]", "[[Rocket Staging]]", "[[Rocket Performance Parameters]]", "[[Critical Conditions and Choked Flow]]"]
status: complete
sources: ["02 - Sources/Tutorial Sheets/Problem Sheet Week 10.pdf", "02 - Sources/Tutorial Sheets/Problem Sheet Week 06.pdf"]
---

# SESA2023 Problem Sheet 10 Rockets Solutions

> [!abstract] Sheet Info
> The sheet has three questions: single stage to orbit, one stage against two for a 14.3 km/s mission, and a rocket nozzle ($A_t$, $C^*$, $c_e$, $C_F$, $I_{sp}$, $F$). All printed answers are reproduced ✔.

> [!info] Problem Sheet 6 is the same sheet
> `Problem Sheet Week 06.pdf` has word-for-word the same questions and answers (numbered 6.1–6.3). Q10.$n$ here is Q6.$n$ there.

> [!warning] Printed answer labels
> In the printed answer key, (d) and (e) are **swapped**: (d) shows $I_{sp} = 258.7$ s and (e) shows $C_F = 1.57$. The question asks for $C_F$ in (d) and $I_{sp}$ in (e). They are labelled by the question below.

## Theory Links
- [[SESA2023 W10 - Rocket Performance, Staging and Power Cycles]]
- [[Tsiolkovsky Rocket Equation]] · [[Rocket Staging]] · [[Rocket Performance Parameters]] · [[Critical Conditions and Choked Flow]]

**Model** (fully expanded, no gravity or drag losses beyond the equivalent $\Delta V$):

$$
\frac{m_{bo}}{m_0} = \lambda+\delta = e^{-\Delta V/c_e}\;\Rightarrow\;\lambda = e^{-\Delta V/c_e}-\delta,\qquad m_0 = \frac{m_{pl}}{\lambda},\qquad m_p = m_0(1-\lambda-\delta)
$$

---

## Q10.1: Single stage to orbit
Data: $\Delta V = 9140$ m/s, $m_{pl} = 2000$ kg, $\delta = 0.03$, $I_{sp} = 400$ s and $t_b = 100$ s. Take $g_0 = 9.80665$ m/s², the data-book value.

$$
c_e = g_0I_{sp} = 3922.7\text{ m/s},\qquad \lambda = e^{-9140/3922.7}-0.03 = 0.09729-0.03 = 0.06729
$$

$$
m_0 = \frac{2000}{0.06729} = \boxed{29{,}722\text{ kg}}\;✔\;(\text{printed }29{,}718)
$$

$$
m_p = 29{,}722(1-0.06729-0.03) = 26{,}830\text{ kg},\qquad \dot m = \frac{m_p}{t_b} = \boxed{268.3\text{ kg/s}}\;✔
$$

- The payload is only **6.7 %** of the lift-off mass, even with an optimistic $I_{sp}$ of 400 s and a 3 % structure. The burn-out mass fraction must be $e^{-2.33} = 9.7\%$.
- With $g_0 = 9.81$ you get $m_0 = 29{,}688$ kg and 268.0 kg/s. The difference is only in the 3rd–4th significant figure, but because $\lambda$ is a small difference of two numbers it amplifies such changes.

## Q10.2: One stage against two ($\Delta V = 14.3$ km/s, $c_e = 4115$ m/s, $\delta = 0.03$, 9 t payload)

### (a) Single stage

$$
\lambda = e^{-14300/4115}-0.03 = 0.030959-0.03 = 0.000959,\qquad m_0 = \frac{9000}{0.000959} = \boxed{9{,}384{,}654\text{ kg}}\;✔
$$

The burn-out fraction 0.031 is barely above the 3 % structure, so the payload fraction collapses to 0.1 %. **About 9400 t to lift 9 t** is plainly impractical.

### (b) Two identical stages, 7150 m/s each

$$
\lambda_i = e^{-7150/4115}-0.03 = 0.17595-0.03 = 0.14595
$$

Work down from the payload (see [[Rocket Staging]]):

$$
m_{02} = \frac{9000}{0.14595} = 61{,}665\text{ kg},\qquad m_{01} = \frac{m_{02}}{0.14595} = \boxed{422{,}497\text{ kg}}\;✔
$$

| | Single stage | Two stages |
|---|---|---|
| Lift-off mass | 9385 t | **422.5 t** |
| Overall payload fraction $\lambda_0$ | 0.00096 | $\lambda_1\lambda_2 = 0.0213$ |
| Propellant | 9094 t | 348.2 + 50.8 = **399.0 t** |

Staging cuts the lift-off mass by a factor of **22**. When $\Delta V/c_e$ is large (3.5 here), each stage only needs to reach half the velocity, so its mass ratio is the **square root** of the single-stage one ($e^{1.74}$ rather than $e^{3.48}$). Meanwhile, the dead weight of the first stage is dropped before it has to be accelerated to full speed.

> [!tip] Contrast with 2024-25 Q2
> At a modest $\Delta V/c_e\approx1.1$, the same $\delta$-model gives almost no benefit from staging. See [[SESA2023 Exam 2024-25 Solutions]] Q2(iii). Staging pays off when the mission $\Delta V$ is large compared with $c_e$.

## Q10.3: Rocket nozzle (60 bar, 2800 K, $R = 397$, $\gamma = 1.22$, 50 kg/s, fully expanded to 1 bar)

$$
c_p = \frac{\gamma R}{\gamma-1} = \frac{1.22(397)}{0.22} = 2201.5\text{ J kg}^{-1}\text{ K}^{-1}
$$

### (a) Throat area (choked)

$$
\dot m = A_tp_0\sqrt{\frac{\gamma}{RT_0}}\left(\frac{2}{\gamma+1}\right)^{\frac{\gamma+1}{2(\gamma-1)}} = A_t(60\times10^5)(1.0476\times10^{-3})(0.59064)
$$

$$
A_t = \frac{50}{3712.6} = \boxed{0.0135\text{ m}^2}\;✔\quad(d_t = 131\text{ mm})
$$

### (b) Characteristic velocity

$$
C^* = \frac{p_0A_t}{\dot m} = \frac{60\times10^5(0.013468)}{50} = \boxed{1616\text{ m/s}}\;✔
$$

$C^*$ depends only on the chamber gas ($\gamma$, $R$, $T_0$), not on the nozzle.

### (c) Effective exhaust velocity
For a fully expanded jet there is no pressure thrust, so $c_e = V_j$:

$$
c_e = \sqrt{2c_pT_0\left[1-\left(\frac{p_e}{p_0}\right)^{(\gamma-1)/\gamma}\right]} = \sqrt{2(2201.5)(2800)\left[1-\left(\tfrac1{60}\right)^{0.1803}\right]} = \sqrt{2(2201.5)(2800)(0.5221)} = \boxed{2537\text{ m/s}}\;✔
$$

### (d) Nozzle thrust coefficient

$$
C_F = \frac{c_e}{C^*} = \frac{2537}{1616} = \boxed{1.570}\;✔
$$

### (e) Specific impulse

$$
I_{sp} = \frac{c_e}{g_0} = \frac{2537}{9.80665} = \boxed{258.7\text{ s}}\;✔\quad(258.6\text{ s with }g_0 = 9.81)
$$

### (f) Thrust

$$
F = \dot mc_e = 50(2537) = \boxed{126.9\text{ kN}}\;✔
$$

The split $c_e = C^*C_F$ separates the **chamber** ($C^*$) from the **nozzle** ($C_F$). Only 52 % of the available enthalpy $c_pT_0$ is converted, because the expansion stops at 1 bar. A vacuum nozzle expanding further would raise $C_F$, and so $I_{sp}$, with $C^*$ unchanged.

## Sources
- `02 - Sources/Tutorial Sheets/Problem Sheet Week 10.pdf` (and the identical `Problem Sheet Week 06.pdf`). All numbers are reproduced in `04 - Scripts/verify_tutorials.py`.
