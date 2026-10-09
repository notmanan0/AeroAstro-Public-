---
title: "SESA1016 Problem Sheet 03 - Heat Engines and Entropy Solutions"
module: "SESA1016 Thermofluids"
type: tutorial
stream: "Part A: Closed-system Thermodynamics"
tags: [sesa1016, tutorial-solutions, heat-engine, entropy]
sheet: "Problem Sheet 03 - Heat Engines and Entropy"
theory_notes: ["[[SESA1016 T3 - Heat Engines and the Second Law]]", "[[SESA1016 T4 - Entropy and Isentropic Relations]]"]
key_concepts: ["[[Thermal Efficiency and COP]]", "[[Entropy Generation]]"]
status: complete
sources: ["02 - Sources/Tutorial Sheets/Problem Sheet 03 - Heat Engines and Entropy.pdf"]
---

# SESA1016 Problem Sheet 03 - Heat Engines and Entropy Solutions

> [!abstract] Sheet Info
> Six questions on cycle state tables, thermal efficiency, second-law limits and entropy generation. All printed answers are reproduced; the repeated $T_2$ in the sheet's Q3.1 answer line is a typographical error.

## Q3.1 Spacecraft air-conditioning cycle

Work per unit mass. State 1 has $p_1=100$ kPa, $T_1=300$ K. The 1->2 isobaric expansion doubles volume:

$$
p_2=p_1=100\ \mathrm{kPa},\qquad T_2=T_1\frac{v_2}{v_1}=\boxed{600\ \mathrm K}.
$$

Process 2->3 is isochoric to $T_3=250$ K:

$$
p_3=p_2\frac{T_3}{T_2}=100\frac{250}{600}=\boxed{41.7\ \mathrm{kPa}}.
$$

Process 3->4 is isobaric and process 4->1 is isochoric, so $v_4=v_1=v_3/2$:

$$
p_4=p_3=\boxed{41.7\ \mathrm{kPa}},\qquad
T_4=T_3\frac{v_4}{v_3}=\boxed{125\ \mathrm K}.
$$

The $p$-$v$ cycle is a rectangle: 1->2 right at 100 kPa, 2->3 down at $2v_1$, 3->4 left at 41.7 kPa, 4->1 up at $v_1$.

Only isobaric legs perform work:

$$
w_{12}=R(T_2-T_1)=0.287(300)=86.1\ \mathrm{kJ/kg}
$$

$$
w_{34}=R(T_4-T_3)=0.287(-125)=-35.9\ \mathrm{kJ/kg}
$$

$$
\boxed{w_{net}=50.2\ \mathrm{kJ/kg}}\;\checkmark
$$

Heat enters on 1->2 and 4->1:

$$
q_{in}=c_p(600-300)+c_v(300-125)
=1.005(300)+0.718(175)=427.2\ \mathrm{kJ/kg}.
$$

$$
\boxed{\eta=\frac{50.2}{427.2}=11.8\%}\;\checkmark
$$

Ideal quasi-static expansion/compression can be internally reversible. Actual heating/cooling through finite temperature differences is irreversible and generates entropy, lowering achievable work.

## Q3.2 Two three-process engines

Both cycles share constant-volume heating 1->2 from 300 to 900 K. Hence

$$
p_2/p_1=T_2/T_1=3,qquad q_{12}=c_v(900-300)=430.8\ \mathrm{kJ/kg}.
$$

### Cycle A: isentropic 2->3A, then isobaric rejection

$p_{3A}=p_1$, so

$$
T_{3A}=T_2\left(\frac{p_{3A}}{p_2}\right)^{(\gamma-1)/\gamma}
=900(1/3)^{0.4/1.4}=657.5\ \mathrm K.
$$

$$
q_{out,A}=c_p(657.5-300)=359.3\ \mathrm{kJ/kg}
$$

$$
\boxed{\eta_A=1-359.3/430.8=16.6\%}\;\checkmark
$$

### Cycle B: isothermal 2->3B, then isobaric rejection

The isothermal leg ends at $p_1$, so $v_3/v_2=p_2/p_1=3$:

$$
q_{23}=w_{23}=RT_2\ln3=0.287(900)\ln3=283.8\ \mathrm{kJ/kg}.
$$

$$
q_{in,B}=430.8+283.8=714.6\ \mathrm{kJ/kg},\qquad
q_{out,B}=c_p(900-300)=603.0\ \mathrm{kJ/kg}
$$

$$
\boxed{\eta_B=1-603.0/714.6=15.6\%}\;\checkmark
$$

Engineer A is right that A takes and rejects less heat; Engineer B is right that B produces more net work. Neither observation alone determines efficiency. Cycle A is slightly more efficient because its smaller work is produced from disproportionately smaller heat input.

## Q3.3 Why not 100% efficiency?

**Answer: (c).** Even a perfectly reversible cyclic heat engine must reject heat to a lower-temperature reservoir. Otherwise it would convert heat from a single reservoir entirely into work, violating the Kelvin-Planck statement.

## Q3.4 Triangle engine

State 1: $p_1=100$ kPa, $V_1=0.001\ \mathrm{m^3}$, $T_1=300$ K. State 2: $p_2=1000$ kPa, $V_2=0.010\ \mathrm{m^3}$.

The gas mass is

$$
m=\frac{p_1V_1}{RT_1}=\frac{100(0.001)}{0.287(300)}=1.161\times10^{-3}\ \mathrm{kg}.
$$

From the ideal-gas ratio:

$$
T_2=T_1\frac{p_2V_2}{p_1V_1}=300(100)=30000\ \mathrm K.
$$

The straight 1->2 path has trapezoidal area:

$$
W_{12}=\frac{p_1+p_2}{2}(V_2-V_1)
=\frac{100+1000}{2}(0.009)=\boxed{4.95\ \mathrm{kJ}}.
$$

$$
\Delta U_{12}=mc_v(T_2-T_1)=24.75\ \mathrm{kJ}
$$

$$
\boxed{Q_{12}=\Delta U_{12}+W_{12}=29.7\ \mathrm{kJ}}\;\checkmark
$$

The net cycle work is the triangle area:

$$
\boxed{W_{net}=\tfrac12(1000-100)(0.010-0.001)=4.05\ \mathrm{kJ}}.
$$

Only 1->2 supplies heat, so

$$
\boxed{\eta=4.05/29.7=13.6\%}\;\checkmark
$$

> [!warning] A geometrically neat but terrible engine
> The implied maximum temperature is about 30,000 K. Constant specific heats, ideal-gas chemistry and material survival all fail. The low efficiency adds no redeeming benefit.

## Q3.5 Entropy generation in two heat transfers

For heat $Q=200$ kJ from $800$ K to a sink:

$$
S_{gen}=Q\left(\frac1{T_C}-\frac1{T_H}\right).
$$

Process A, $T_C=500$ K:

$$
S_{gen,A}=200000(1/500-1/800)=\boxed{150\ \mathrm{J/K}}.
$$

Process B, $T_C=750$ K:

$$
S_{gen,B}=200000(1/750-1/800)=\boxed{16.7\ \mathrm{J/K}}.
$$

Process A is more irreversible because its temperature difference is larger. $\checkmark$

## Q3.6 Constant-pressure and constant-volume heating

$T_1=293.15$ K and, for the first experiment, $T_2=373.15$ K.

### Fixed temperature rise

Isobaric:

$$
\Delta s=c_p\ln(T_2/T_1)=1005\ln(373.15/293.15)
=\boxed{243\ \mathrm{J\,kg^{-1}K^{-1}}}.
$$

Isochoric:

$$
\Delta s=c_v\ln(T_2/T_1)=718\ln(373.15/293.15)
=\boxed{173\ \mathrm{J\,kg^{-1}K^{-1}}}.
$$

### Fixed heat input $q=100$ kJ/kg

Isobaric: $T_2=T_1+q/c_p=392.65$ K,

$$
\Delta s_p=c_p\ln(392.65/293.15)=\boxed{294\ \mathrm{J\,kg^{-1}K^{-1}}}.
$$

Isochoric: $T_2=T_1+q/c_v=432.43$ K,

$$
\Delta s_v=c_v\ln(432.43/293.15)=\boxed{279\ \mathrm{J\,kg^{-1}K^{-1}}}\;\checkmark
$$

## Related

- [[SESA1016 T3 - Heat Engines and the Second Law]] · [[SESA1016 T4 - Entropy and Isentropic Relations]]

