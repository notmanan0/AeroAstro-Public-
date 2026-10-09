---
title: "SESA2023 Problem Sheet 2 Solutions"
module: "SESA2023 Propulsion"
type: tutorial
stream: "Section 1: Introduction and Fundamentals"
tags:
  - sesa2023
  - tutorial-solutions
  - thermodynamics
  - sfee
  - mixtures
sheet: "Problem Sheet 2: Thermodynamics"
theory_notes: ["[[SESA2023 W02 - Thermodynamics, Mixtures, SFEE and Isentropic Efficiency]]"]
key_concepts: ["[[Entropy Change of a Perfect Gas]]", "[[Gas Mixtures and Dalton's Law]]", "[[Isentropic Efficiency]]", "[[Steady Flow Energy Equation]]", "[[Two-Property Rule and Perfect Gas Model]]"]
status: complete
sources: ["02 - Sources/Tutorial Sheets/Problem Sheet Week 02.pdf"]
---

# SESA2023 Problem Sheet 2 Solutions

> [!abstract] Sheet Info
> Four questions: a three-process heat engine, a Mars compressor (gas mixture), a turbojet via the SFEE, and real vs perfect gas (CoolProp).
>
> All the printed answers are reproduced ✔, with **one typo**: in Q2.2(b) the sheet prints $c_p = 0.872$. It must be **0.827** kJ kg⁻¹ K⁻¹. The check is $c_p-c_v = R = 0.192$, and the sheet's own answer to part (c) (175 kJ/kg) uses 0.827.

## Theory Links
- [[SESA2023 W02 - Thermodynamics, Mixtures, SFEE and Isentropic Efficiency]]
- [[Entropy Change of a Perfect Gas]] · [[Gas Mixtures and Dalton's Law]] · [[Isentropic Efficiency]] · [[Steady Flow Energy Equation]]

---

## Q2.1: Heat engine on air starting at 1 bar and 300 K
The cycle is: 1→2 isothermal heat rejection of 100 kJ/kg, 2→3 isobaric, 3→1 isochoric. On a $p$–$v$ diagram, the path 1→2 goes up and left along the isotherm to higher $p$. Then 2→3 runs right at constant $p_2$ back to $v_1$, and 3→1 drops vertically to state 1. The cycle is traversed clockwise, so it produces net work.

- **(a)** $\Delta s_{12} = q/T = -100/300 = \boxed{-0.333\text{ kJ kg}^{-1}\text{K}^{-1}}$ ✔
- **(b)** Isothermal ideal gas, so $\Delta u = 0$ and $w_{12} = q_{12} = \boxed{-100\text{ kJ/kg}}$ (work done *on* the gas) ✔
- **(c)** $\Delta s = -R\ln(p_2/p_1)$, so $p_2 = 1\times e^{0.3333/0.287} = \boxed{3.19\text{ bar}}$ ✔
- **(d)** $v_3 = v_1 = RT_1/p_1 = 0.861$ m³/kg, so $w_{23} = p_2(v_1-v_2) = p_2v_1-RT_1 = 275.0-86.1 = \boxed{188.9\text{ kJ/kg}}$ ✔
- **(e)** $w_{31} = 0$, so $w_{net} = -100+188.9 = \boxed{88.9\text{ kJ/kg}}$ ✔
- **(f)** Heat is only added in 2→3. $T_3 = p_2v_1/R = 958.4$ K, so $q_{23} = c_p(T_3-T_2) = 1.005(658.4) = 661.7$ kJ/kg. Then $\eta = 88.9/661.7 = \boxed{13.4\%}$ ✔. Process 3→1 rejects heat at constant volume.

## Q2.2: Mars compressor, $\pi = 15$, $\eta_c = 0.9$, inlet 215 K
### (a) On Earth (standard air at 300 K)

$$
w = \frac{c_pT_1(\pi^{0.2857}-1)}{\eta_c} = \frac{1.005(300)(2.1678-1)}{0.9} = \boxed{391\text{ kJ/kg}}\;✔
$$

### (b) Mars atmosphere: 95 % CO₂ + 5 % N₂ **by volume**
- Mean molar mass: $M = 0.95(44)+0.05(28) = 43.2$ kg/kmol.
- Mass fractions: $x_{CO_2} = 0.95(44)/43.2 = 0.968$ and $x_{N_2} = 0.032$.
- $c_p = 0.968(0.82)+0.032(1.04) = \boxed{0.827}$ and $c_v = 0.968(0.63)+0.032(0.74) = \boxed{0.634}$ kJ kg⁻¹ K⁻¹.
- $\gamma = 0.827/0.634 = \boxed{1.31}$ (1.305).

Check: $R = 8.3145/43.2 = 0.1925\approx c_p-c_v = 0.1936$ ✔.

> [!warning] Typo on the sheet
> The sheet prints $c_p = 0.872$. That value would give $c_p-c_v = 0.238\neq R$ and $\gamma = 1.375$. The digits are transposed.

### (c) On Mars (215 K)

$$
w = \frac{0.827(215)(15^{0.2340}-1)}{0.9} = \boxed{175\text{ kJ/kg}}\;✔\quad(177\text{ with }\gamma = 1.31\text{ exactly})
$$

The work is less than half the Earth value. The colder inlet and the lower $c_p$ and $(\gamma-1)/\gamma$ of CO₂ both reduce it.

## Q2.3: Turbojet at 2 km, 150 m/s, 200 kg/s, $\pi_c = 20$, $q = 500$ kJ/kg, isentropic components, $f\ll1$
The ISA at 2 km gives $T_1 = 275.15$ K and $p_1 = 79.50$ kPa.

| Station | Result |
|---|---|
| Intake | $T_{02} = 275.15+150^2/2010 = 286.3$ K; $p_{02} = 79.50(286.3/275.15)^{3.5} = 91.4$ kPa |
| Compressor | $T_{03} = 286.3(20)^{0.2857} = 673.9$ K |
| Burner | $T_{04} = 673.9+500/1.005 = 1171.4$ K |
| Turbine ($w_t = w_c$) | $T_{05} = 1171.4-(673.9-286.3) = 783.9$ K; $p_{05} = 20(91.4)(783.9/1171.4)^{3.5} = 448.0$ kPa |
| Nozzle (to $p_1$) | $T_6 = 783.9(79.5/448.0)^{0.2857} = \boxed{478\text{ K}}$; $V_j = \sqrt{2(1005)(783.9-478.3)} = \boxed{784\text{ m/s}}$ ✔ |

- **(b)** $F = \dot m(V_j-V_0) = 200(784-150) = \boxed{127\text{ kN}}$ ✔
- **(c)** $\eta_P = 2/(1+784/150) = \boxed{32\%}$, $\eta_{th} = (784^2-150^2)/(2\times500\,000) = \boxed{59\%}$, $\eta_O = \boxed{19\%}$ ✔

## Q2.4: Perfect vs real gas (CoolProp)
The perfect-gas results use $c_p = 1.005$ and $\gamma = 1.4$.

| Case | Perfect gas | Real gas (sheet, CoolProp) |
|---|---|---|
| (a) Compressor 1→10 bar from 300 K | $T_2 = 300(10)^{0.2857} = 579.2$ K, $w = 280.6$ kJ/kg | 574.45 K, 280.15 kJ/kg |
| (b) Burner at 600 K, +500 kJ/kg | $T = 600+500/1.005 = 1097.5$ K | 1052.6 K |

**(c)** For compression near ambient temperature the perfect-gas model is excellent: 0.2 % error in work and 5 K in temperature. For large heat addition it **overestimates** the temperature by about 45 K, because the real $c_p$ rises with temperature (about 1.1 kJ kg⁻¹ K⁻¹ near 1000 K). That is why a larger product $c_p$ is used downstream of the combustor.

(CoolProp isn't installed in this vault's Python environment, so the real-gas column quotes the sheet.)

## Sources
- `02 - Sources/Tutorial Sheets/Problem Sheet Week 02.pdf`. All values checked in Python.
