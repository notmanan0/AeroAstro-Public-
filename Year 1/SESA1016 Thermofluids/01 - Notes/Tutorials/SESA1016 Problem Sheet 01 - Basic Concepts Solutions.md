---
title: "SESA1016 Problem Sheet 01 - Basic Concepts Solutions"
module: "SESA1016 Thermofluids"
type: tutorial
stream: "Part A: Closed-system Thermodynamics"
tags: [sesa1016, tutorial-solutions, ideal-gas]
sheet: "Problem Sheet 01 - Basic Concepts"
theory_notes: ["[[SESA1016 T1 - Thermodynamic Systems, Properties and State]]"]
key_concepts: ["[[Ideal-gas Law]]", "[[Thermodynamic State and Process]]"]
status: complete
sources: ["02 - Sources/Tutorial Sheets/Problem Sheet 01 - Basic Concepts.pdf"]
---

# SESA1016 Problem Sheet 01 - Basic Concepts Solutions

> [!abstract] Sheet Info
> Five questions on ideal-gas state relations, mass conservation and frictionless-piston equilibrium. All printed answers are reproduced.

## Theory Links

- [[SESA1016 T1 - Thermodynamic Systems, Properties and State]]
- [[Ideal-gas Law]] · [[Thermodynamic State and Process]]

---

## Q1.1 Unknown tank volume

Both tanks return to the same temperature, and the total mass is unchanged. For an ideal gas, $m=pV/(RT)$, so the common $RT$ cancels:

$$
p_A V_A+p_BV_B=p_f(V_A+V_B).
$$

With $V_A=5$ L, $p_A=1.5$ bar, $p_B=1.0$ bar and $p_f=1.2$ bar:

$$
1.5(5)+1.0V_B=1.2(5+V_B)
$$

$$
7.5+V_B=6+1.2V_B\quad\Rightarrow\quad
\boxed{V_B=7.5\ \mathrm{L}}\;\checkmark
$$

The tube volume is neglected. Absolute pressure is used throughout.

## Q1.2 Rigid CO$_2$ container

**Data**: $V=2.5\times10^{-3}\ \mathrm{m^3}$, $m_1=4.4\times10^{-3}$ kg, $R_{CO_2}=188.9\ \mathrm{J\,kg^{-1}K^{-1}}$.

### (a) Initial pressure at 300 K

$$
p_1=\frac{m_1RT_1}{V}
=\frac{(4.4\times10^{-3})(188.9)(300)}{2.5\times10^{-3}}
=\boxed{99.75\ \mathrm{kPa}}\;\checkmark
$$

### (b) Pressure after heating to 450 K

At fixed mass and volume, $p/T=$ constant:

$$
p_2=p_1\frac{T_2}{T_1}=99.75\frac{450}{300}
=\boxed{149.6\ \mathrm{kPa}}\;\checkmark
$$

### (c) Add 2.2 g at 450 K

$m_3=6.6\times10^{-3}$ kg, so

$$
p_3=\frac{m_3RT_3}{V}
=\boxed{224.4\ \mathrm{kPa}}\;\checkmark
$$

The mass rises by 50%, so the fixed-$T$, fixed-$V$ pressure also rises by 50% from part (b), a useful check.

## Q1.3 Atmospheric air

Use $R_{air}=287\ \mathrm{J\,kg^{-1}K^{-1}}$.

### (a) Sea-level density

$$
\rho_1=\frac{p_1}{RT_1}
=\frac{101300}{287(288.15)}
=\boxed{1.225\ \mathrm{kg/m^3}}\;\checkmark
$$

### (b) Density at 5000 m

$T_2=-17^\circ$C $=256.15$ K:

$$
\rho_2=\frac{54000}{287(256.15)}
=\boxed{0.735\ \mathrm{kg/m^3}}\;\checkmark
$$

### (c) Balloon volume

The balloon retains the same mass:

$$
\frac{p_1V_1}{T_1}=\frac{p_2V_2}{T_2}
$$

$$
V_2=V_1\frac{p_1}{p_2}\frac{T_2}{T_1}
=1(101.3/54)(256.15/288.15)
=\boxed{1.67\ \mathrm{m^3}}\;\checkmark
$$

Lower ambient pressure dominates the modest temperature reduction, so the balloon expands.

## Q1.4 Piston expanding into vacuum

Initial gas temperature is $T_i=900^\circ$C $=1173.15$ K. The gas initially occupies $V_2$ and ultimately occupies the whole tank $V_1+V_2=3V_2$. The final heating ends when $p_f=p_i$.

For the same mass:

$$
\frac{p_iV_2}{T_i}=\frac{p_f(3V_2)}{T_f}.
$$

Since $p_f=p_i$:

$$
T_f=3T_i=3(1173.15)=\boxed{3519\ \mathrm K}\;\checkmark
$$

### Was the piston motion quasi-equilibrium?

**No.** Initially the gas pressure is opposed by vacuum, a finite unbalanced pressure difference. The piston accelerates and the gas passes through nonequilibrium states; a single uniform boundary pressure cannot describe the path.

## Q1.5 Two gases separated by a piston

Both sides remain isothermal at $T_0$. Each side contains a fixed mass, so $pV=mRT_0$ is constant separately:

$$
p_fV_{1f}=p_{1i}V_{1i}=2(0.002)=0.004\ \mathrm{bar\,m^3}
$$

$$
p_fV_{2f}=p_{2i}V_{2i}=1(0.001)=0.001\ \mathrm{bar\,m^3}.
$$

The total volume is rigid:

$$
V_{1f}+V_{2f}=0.003\ \mathrm{m^3}.
$$

Therefore

$$
\frac{0.004}{p_f}+\frac{0.001}{p_f}=0.003
\quad\Rightarrow\quad
p_f=\boxed{1.67\ \mathrm{bar}}.
$$

$$
V_{1f}=\frac{0.004}{1.6667}=\boxed{0.0024\ \mathrm{m^3}},\qquad
V_{2f}=\frac{0.001}{1.6667}=\boxed{0.0006\ \mathrm{m^3}}\;\checkmark
$$

The common final pressure lies between the two initial pressures, as required.

## Related

- [[SESA1016 Thermofluids Hub]] · [[SESA1016 Formula Sheet]]

