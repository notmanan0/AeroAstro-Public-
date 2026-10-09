---
title: "SESA1016 Problem Sheet 02 - Work and Heat Solutions"
module: "SESA1016 Thermofluids"
type: tutorial
stream: "Part A: Closed-system Thermodynamics"
tags: [sesa1016, tutorial-solutions, first-law, work, heat]
sheet: "Problem Sheet 02 - Work and Heat"
theory_notes: ["[[SESA1016 T2 - Work, Heat and the First Law]]"]
key_concepts: ["[[Boundary Work]]", "[[Internal Energy and Enthalpy]]"]
status: complete
sources: ["02 - Sources/Tutorial Sheets/Problem Sheet 02 - Work and Heat.pdf"]
---

# SESA1016 Problem Sheet 02 - Work and Heat Solutions

> [!abstract] Sheet Info
> Five questions on moving pistons, path-dependent work, isothermal/isochoric processes and reversible adiabatic compression. All printed answers are reproduced.

## Theory Links

- [[SESA1016 T2 - Work, Heat and the First Law]]
- [[Boundary Work]] · [[Internal Energy and Enthalpy]]

---

## Q2.1 Heavy piston

**Data**: $A=0.1\ \mathrm{m^2}$, $m_p=203.9$ kg, $V_1=0.05\ \mathrm{m^3}$, $p_1=p_{atm}=100$ kPa, $T_1=300$ K, $R=0.290$ and $c_v=0.725\ \mathrm{kJ\,kg^{-1}K^{-1}}$.

### (a-b) States and path

- 1->2: piston remains on its support, so $V=$ constant while $p$ rises.
- At state 2, gas force balances atmospheric and piston loads.
- 2->3: piston rises quasi-statically at constant load, so $p=$ constant and volume increases.

The $p$-$V$ path is vertical 1->2, then horizontal 2->3.

### (c) Gas mass

$$
m=\frac{p_1V_1}{RT_1}
=\frac{100(0.05)}{0.290(300)}
=\boxed{0.0575\ \mathrm{kg}}\;\checkmark
$$

### (d) Lift pressure

$$
p_2A=p_{atm}A+m_pg
$$

$$
p_2=p_{atm}+\frac{m_pg}{A}
=100+\frac{203.9(9.81)}{0.1}\frac1{1000}
\approx\boxed{120\ \mathrm{kPa}}.
$$

The same constant load acts during motion, so $p_3=p_2=1.2$ bar. The state-2 temperature is

$$
T_2=T_1\frac{p_2}{p_1}=360\ \mathrm K.
$$

### (e) Heat 1->2

$W_{12}=0$ because the piston has not moved:

$$
Q_{12}=\Delta U_{12}=mc_v(T_2-T_1)
=(0.05747)(0.725)(60)
=\boxed{2.50\ \mathrm{kJ}}\;\checkmark
$$

### (f) Heat and work 2->3

The piston rises $0.2$ m, so

$$
V_3=V_2+A\Delta x=0.05+0.1(0.2)=0.07\ \mathrm{m^3}.
$$

At constant pressure, $T_3/T_2=V_3/V_2=1.4$, hence $T_3=504$ K.

$$
W_{23}=p(V_3-V_2)=120(0.02)=\boxed{2.40\ \mathrm{kJ}}
$$

$$
\Delta U_{23}=mc_v(504-360)=6.00\ \mathrm{kJ}
$$

$$
Q_{23}=\Delta U_{23}+W_{23}=\boxed{8.40\ \mathrm{kJ}}\;\checkmark
$$

## Q2.2 Adiabatic compression followed by constant-pressure expansion

Let $r=V_1/V_2$, $V_3=V_1$, and $pV^\gamma=$ constant during 1->2.

$$
W_{12}=\int_{V_1}^{V_2}p_1V_1^\gamma V^{-\gamma}dV
=\frac{p_1V_1}{1-\gamma}(r^{\gamma-1}-1).
$$

Since $p_2=p_1r^\gamma$,

$$
W_{23}=p_2(V_3-V_2)=p_1r^\gamma V_1\left(1-\frac1r\right).
$$

Thus

$$
\boxed{\frac{W_{12}}{W_{23}}=
\frac{r^{\gamma-1}-1}{(1-\gamma)r^\gamma(1-1/r)}}.
$$

For $\gamma=1.4$, $r=6$:

$$
\boxed{W_{12}/W_{23}=-0.256}\;\checkmark
$$

The negative sign is correct: compression work is work done **on** the gas, while expansion work is done by it.

## Q2.3 Two paths between the same states

For process A:

$$
\Delta U=Q-W=16-20=\boxed{-4\ \mathrm{kJ}}.
$$

$\Delta U$ is a state change, so it is also $-4$ kJ for process B. With $Q_B=9$ kJ:

$$
W_B=Q_B-\Delta U=9-(-4)=\boxed{13\ \mathrm{kJ}}\;\checkmark
$$

Heat and work change with path; internal-energy change does not.

## Q2.4 Isothermal expansion then rigid heating

**Data**: $m=10$ kg, $R=0.287$, $c_v=0.718\ \mathrm{kJ\,kg^{-1}K^{-1}}$, $T_1=300$ K, $p_1/p_2=5$.

### Isothermal expansion

$$
W_{12}=mRT\ln\frac{V_2}{V_1}=mRT\ln\frac{p_1}{p_2}
=10(0.287)(300)\ln5
=\boxed{1386\ \mathrm{kJ}}.
$$

For an ideal gas at constant temperature:

$$
\boxed{\Delta U_{12}=0},\qquad \boxed{Q_{12}=W_{12}=1386\ \mathrm{kJ}}\;\checkmark
$$

### Locked piston, pressure raised from 1 to 5 bar

At fixed volume, $T_3/T_2=p_3/p_2=5$, so $T_3=1500$ K. Hence

$$
\boxed{W_{23}=0}
$$

$$
\Delta U_{23}=mc_v(1500-300)=10(0.718)(1200)
=\boxed{8616\ \mathrm{kJ}}
$$

$$
\boxed{Q_{23}=8616\ \mathrm{kJ}}\;\checkmark
$$

## Q2.5 Isothermal expansion and adiabatic compression

**Data**: $m=0.5$ kg, $T_1=300$ K, $p_1=100$ kPa, $V_2=2V_1$, $\gamma=1.4$, $R=0.287\ \mathrm{kJ\,kg^{-1}K^{-1}}$.

### (a-b) Isothermal expansion

$$
T_2=300\ \mathrm K,\qquad p_2=p_1\frac{V_1}{V_2}=\boxed{50\ \mathrm{kPa}}.
$$

$$
W_{12}=mRT\ln2=(0.5)(0.287)(300)\ln2
=\boxed{29.84\ \mathrm{kJ}}.
$$

$\Delta U_{12}=0$, so $\boxed{Q_{12}=29.84\ \mathrm{kJ}}$.

### (c-d) Reversible adiabatic compression to $V_3=V_1$

$$
T_3=T_2\left(\frac{V_2}{V_3}\right)^{\gamma-1}
=300(2)^{0.4}=\boxed{395.9\ \mathrm K}
$$

$$
p_3=p_2\left(\frac{V_2}{V_3}\right)^\gamma
=50(2)^{1.4}=\boxed{132.0\ \mathrm{kPa}}.
$$

$c_v=R/(\gamma-1)=0.7175\ \mathrm{kJ\,kg^{-1}K^{-1}}$ and $Q_{23}=0$:

$$
W_{23}=-\Delta U_{23}=mc_v(T_2-T_3)
=\boxed{-34.4\ \mathrm{kJ}}\;\checkmark
$$

Compression is negative work under the course convention.

## Related

- [[SESA1016 Thermofluids Hub]] · [[SESA1016 Formula Sheet]]

