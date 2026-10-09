---
title: "SESA3029 Example Sheet 3 - Solutions"
module: "SESA3029 Aerothermodynamics"
type: tutorial
stream: "Section 5: heat transfer (Weeks 9–12)"
tags: [sesa3029, tutorial-solutions, example-sheet, heat-transfer, conduction, convection, radiation, heat-exchanger]
sheet: "Tutorial 3 (Example Sheet 3)"
theory_notes: []
status: complete
sources: ["03 - Exams & Past Papers/ExampleSheet3(1).pdf"]
---

# SESA3029 Example Sheet 3 - Solutions

> [!abstract] Sheet info
> "Tutorial 3" covers **heat transfer**, the Weeks 9–12 block, which has **not been lectured yet**. Each solution states the model it uses (thermal resistances, Newton cooling, Nusselt correlations, radiation balance, ε–NTU) and derives what is needed. Every number is verified in Python.
>
> Results: Q1 and Q2 reproduce the printed answers exactly. Q4 does too, to rounding. **Q3 and Q6 do not**, and **Q5's answers are printed in swapped order**. Each case is explained below.

![[at_es3_heat_transfer.png|900]]

---

## Q1. Composite wall pierced by steel bolts

Layers: A (3 cm, $k=0.048$), B (10 cm, $k=0.69$) and C (3 cm, $k=0.048$), all in W/m K. The faces are at $150^\circ$C and $10^\circ$C. Steel bolts ($d=1$ cm, $k=40$) run through the whole 16 cm at 10 per m².

**Model.** 1D conduction with two **parallel** paths per unit wall area: the layered insulation, area fraction $1-f$, and the bolts, area fraction $f$. Ignore lateral heat exchange between them.

**Series resistance of the layers** (per unit area, $R''=L/k$):

$$
R''_{wall}=\frac{0.03}{0.048}+\frac{0.10}{0.69}+\frac{0.03}{0.048}=0.625+0.1449+0.625=1.3949\ \text{m}^2\text{K/W}.
$$

**Bolt path:**

$$
R''_{bolt}=\frac{0.16}{40}=0.004\ \text{m}^2\text{K/W}.
$$

Bolt area fraction:

$$
f=10\times\frac{\pi}{4}(0.01)^2=7.854\times10^{-4}.
$$

**Parallel paths add their conductances:**

$$
q''=\Delta T\left[\frac{1-f}{R''_{wall}}+\frac{f}{R''_{bolt}}\right]=140\left[0.71632+0.19635\right]=\boxed{127.8\ \text{W/m}^2}
$$

The sheet gives 127.8 ✓.

> [!tip] A 0.08% area fraction raises the heat flux by 27%
> Without bolts, $q''=140/1.3949=100.4$ W/m². The steel is 830 times more conductive than the insulation, so a tiny area fraction becomes a **thermal short-circuit**. This is why spacecraft and cryogenic tanks use low-conductivity standoffs.

## Q2. Turbine blade: Newton cooling and similarity

Original conditions: $V=160$ m/s, $T_\infty=1150^\circ$C, $L=40$ mm, $T_s=800^\circ$C and $\dot q''=95$ kW/m² at $x^*$.

**Model.** Newton's law, $\dot q''=h\,(T_\infty-T_s)$, with $h$ fixed by the flow and geometry. Property changes with $T_s$ are neglected.

**(a)** First the local heat transfer coefficient:

$$
h=\frac{95\,000}{1150-800}=271.4\ \text{W/m}^2\text{K}.
$$

The flow is unchanged, so $h$ is unchanged:

$$
\dot q''=271.4\times(1150-700)=\boxed{122\ \text{kW/m}^2}.
$$

**(b)** New blade: $L=80$ mm, $V=80$ m/s, same $T_s$ and $T_\infty$. For forced convection $Nu=hL/k=f(Re,Pr)$ at the same dimensionless location $x^*/L$.

$$
Re_{orig}=\frac{160\times0.04}{\nu},
\qquad
Re_{new}=\frac{80\times0.08}{\nu}=Re_{orig}.
$$

$Pr$ is the same (same gas and temperatures), so $Nu$ is the same, and

$$
h_{new}=Nu\,\frac{k}{L_{new}}=h_{orig}\,\frac{L_{orig}}{L_{new}}=\frac{271.4}{2}=135.7,
$$

$$
\dot q''=135.7\times350=\boxed{47.5\ \text{kW/m}^2}.
$$

The sheet gives 122 and 47.5 kW/m² ✓.

> [!note] "Reynolds analogy"
> The sheet's phrase really means **dynamic similarity**: equal $Re$ and $Pr$ give equal $Nu$. Reynolds' analogy proper, $St=C_f/2$, links heat transfer to skin friction and would give the same scaling here.

## Q3. Rocket instrument bay

Aluminium skin: $k=160$ W/m K, $L=4$ m, $D_o=1$ m, thickness 5 mm. $V=150$ m/s; ambient $T_\infty=280$ K with $k_a=0.026$, $\nu=1.65\times10^{-5}$ and $Pr=0.71$. Inside, $h_i=5$ W/m² K and $\dot Q=400$ W. External correlation $Nu=0.027\,Re^{0.805}Pr^{1/3}$ (turbulent).

**Step 1. External convection**, using the length $L$ as the length scale along the body:

$$
Re_L=\frac{150\times4}{1.65\times10^{-5}}=3.64\times10^7\ \text{(turbulent)},
$$

$$
Nu=0.027(3.64\times10^7)^{0.805}(0.71)^{1/3}=29\,385,
\qquad
h_o=\frac{Nu\,k_a}{L}=191.0\ \text{W/m}^2\text{K}.
$$

**Step 2. Series thermal circuit** for a cylinder, $r_o=0.5$ m and $r_i=0.495$ m:

$$
R_o=\frac{1}{h_o\,\pi D_oL}=4.17\times10^{-4},
\qquad
R_{wall}=\frac{\ln(r_o/r_i)}{2\pi kL}=2.50\times10^{-6},
$$

$$
R_i=\frac{1}{h_i\,2\pi r_iL}=1.608\times10^{-2}\ \text{K/W}.
$$

**Step 3. Steady state.** All 400 W leaves through the circuit:

$$
T_{in}=T_\infty+\dot Q\,(R_o+R_{wall}+R_i)=280+400\times0.016498=\boxed{286.6\ \text{K}}.
$$

> [!warning] Printed answer 286.48 K
> I cannot reproduce 286.48 K exactly. Basing $Re$ and $Nu$ on the diameter, and using the outer area for the inner film, gives 286.49 K, which suggests that is what the answer key did. Either way, **the inner free-convection film is 97% of the resistance**, so the answer is about 286.5 K whichever reasonable choices are made.
>
> A further aerothermodynamic caveat: at 150 m/s the stagnation temperature rise is $V^2/2c_p=11.2$ K. Strictly, the outside of the skin sees a recovery temperature of about 290 K, not 280 K, which would raise $T_{in}$ by about 10 K. The sheet ignores this.

## Q4. Meteor stagnation-point heating

Sphere: $d=0.1$ m, $V=9000$ m/s, altitude 70 km. Air: $T=217$ K, $Pr=0.71$, $\rho=10^{-4}$ kg/m³, $\mu=1.79\times10^{-5}$ N s/m². Surface emissivity $\varepsilon=0.6$. Stagnation correlation $Nu=0.763\,Re_d^{0.5}Pr^{0.4}$.

**(a) Total (stagnation) temperature.** Adiabatic, with $c_p=\gamma R/(\gamma-1)=1004.5$ J/kg K (W01 §4):

$$
T_0=T+\frac{V^2}{2c_p}=217+\frac{9000^2}{2\times1004.5}=\boxed{40\,536\ \text{K}}.
$$

The sheet gives 40 536 K ✓. In reality, dissociation and ionisation would absorb much of this energy; the calorically perfect gas model is a gross idealisation at 9 km/s, but it is what the sheet intends.

**(b) Surface temperature.** Heat balance at the stagnation point, ignoring gas radiation and conduction into the meteor: convective input equals radiative loss,

$$
h\,(T_0-T_s)=\varepsilon\sigma T_s^4.
$$

The conductivity comes from the Prandtl number:

$$
k=\frac{\mu c_p}{Pr}=0.02532\ \text{W/m K},
\qquad
Re_d=\frac{\rho Vd}{\mu}=5028,
$$

$$
Nu=0.763\sqrt{5028}\,(0.71)^{0.4}=47.18,
\qquad
h=\frac{Nu\,k}{d}=11.95\ \text{W/m}^2\text{K}.
$$

The balance is the **quartic**

$$
\varepsilon\sigma T_s^4+hT_s-hT_0=0.
$$

It has one positive real root, one negative real root ($-1966$ K) and a complex pair. Find the positive root with Newton's method:

| $k$ | $T_s$ (K) | $f(T_s)$ | $f'=4\varepsilon\sigma T_s^3+h$ |
|---:|---:|---:|---:|
| 0 | 2000.0 | $8.40\times10^4$ | 1100.7 |
| 1 | 1923.7 | $4.63\times10^3$ | 980.8 |
| 2 | 1919.0 | 16.8 | 973.7 |
| 3 | **1918.97** | 0 | |

$$
\boxed{T_s=1919\ \text{K}}\quad(\text{sheet: }1919\text{ K ✓}).
$$

**(c) Convective heat flux.**

$$
\dot q''=h(T_0-T_s)=11.95\times38\,617=\boxed{461\ \text{kW/m}^2}\quad(\text{sheet: }461\ ✓).
$$

This equals $\varepsilon\sigma T_s^4$, as it must. See [[Blackbody Radiation]] for the Stefan–Boltzmann law.

## Q5. Parallel-flow heat exchanger

Hot water: $\dot m=0.3$ kg/s, $c_p=4200$ J/kg K, in at $90^\circ$C, so $C_h=1260$ W/K. Cold water: $\dot m=0.4$ kg/s, $c_p=4180$, in at $10^\circ$C, so $C_c=1672$ W/K. $h_h=40$, $h_c=800$ W/m² K, $A=8.5$ m², wall resistance neglected.

**Overall coefficient** (two films in series):

$$
U=\left(\frac{1}{40}+\frac{1}{800}\right)^{-1}=38.10\ \text{W/m}^2\text{K},
\qquad
UA=323.8\ \text{W/K}.
$$

**Derivation of the parallel-flow solution.** Over an element $\mathrm dA$, $\delta\dot Q=U(T_h-T_c)\,\mathrm dA$, with $\mathrm dT_h=-\delta\dot Q/C_h$ and $\mathrm dT_c=+\delta\dot Q/C_c$. Subtracting:

$$
\frac{\mathrm d(T_h-T_c)}{\mathrm dA}=-U\left(\frac{1}{C_h}+\frac{1}{C_c}\right)(T_h-T_c)
$$

$$
\Rightarrow\
\Delta T_{out}=\Delta T_{in}\exp\!\left[-UA\left(\frac{1}{C_h}+\frac{1}{C_c}\right)\right]=80\,e^{-0.4507}=50.98\ \text{K}.
$$

The total heat follows from the change in the difference:

$$
\dot Q=\frac{\Delta T_{in}-\Delta T_{out}}{1/C_h+1/C_c}=20.85\ \text{kW}.
$$

This is the same as ε–NTU with $NTU=UA/C_{min}=0.257$, $C_r=0.754$ and $\varepsilon=\dfrac{1-e^{-NTU(1+C_r)}}{1+C_r}=0.2069$.

$$
T_{h,out}=90-\frac{20\,854}{1260}=\boxed{73.5^\circ\text{C}},
\qquad
T_{c,out}=10+\frac{20\,854}{1672}=\boxed{22.5^\circ\text{C}}.
$$

LMTD check: $(80-50.98)/\ln(80/50.98)=64.40$ K, and $UA\times\text{LMTD}=20.85$ kW ✓.

> [!warning] Order of the printed answers
> The question asks for "the cold and hot sides" but prints $[73.5, 22.5]$. 73.5°C is the **hot** outlet and 22.5°C the **cold** outlet. The cold stream cannot exceed the hot outlet in parallel flow anyway.

## Q6. Minimum condenser-pipe length

$D=20$ mm, $\dot m=0.1$ kg/s, inside properties $k=0.686$ W/m K, $c_p=4239$ J/kg K, $\mu=2.37\times10^{-4}$ N s/m², $Pr=1.47$. Outside: air at $20^\circ$C with $h_c=12\,000$ W/m² K. The fluid enters at 140°C and must reach 60°C. Wall conduction is neglected.

**Model.** Sensible cooling of the internal flow to $60^\circ$C, with no latent heat (as the data imply), and a constant outside temperature.

**Step 1. Internal convection.**

$$
Re=\frac{4\dot m}{\pi D\mu}=\frac{4\times0.1}{\pi\times0.02\times2.37\times10^{-4}}=26\,860\ \text{(turbulent)}.
$$

Dittus–Boelter for a fluid being **cooled**, $Nu=0.023\,Re^{0.8}Pr^{0.3}$:

$$
Nu=90.2,
\qquad
h_i=\frac{Nu\,k}{D}=3094\ \text{W/m}^2\text{K}.
$$

**Step 2. Overall coefficient**, thin wall, same area each side:

$$
U=(1/3094+1/12\,000)^{-1}=2460\ \text{W/m}^2\text{K}.
$$

**Step 3. Length.** Energy balance on a slice of length $\mathrm dx$: $\dot mc_p\,\mathrm dT_m=-U\pi D\,(T_m-T_\infty)\,\mathrm dx$. Integrating from inlet to outlet:

$$
L=\frac{\dot mc_p}{U\pi D}\ln\frac{T_{in}-T_\infty}{T_{out}-T_\infty}=\frac{0.1\times4239}{2460\times\pi\times0.02}\ln\frac{120}{40}=2.743\times1.0986=\boxed{3.01\ \text{m}}.
$$

With $Pr^{0.4}$ (the heating form): $L=2.92$ m.

> [!warning] Printed answer 30.2 m
> 30.2 m is ten times this result. The key would need $U\approx245$ W/m² K, which none of the stated data give. It looks like a decimal slip in the key. **3.0 m** follows from the data as given. Raise this in the tutorial.

## Links

- Previous sheet: [[SESA3029 Example Sheet 2 - Solutions]]
- Related earlier notes: [[Blackbody Radiation]] · [[Reynolds Number]] · [[Spacecraft Thermal Balance Equation]] · [[Turbine Entry Temperature and Blade Cooling]]
- Hub: [[SESA3029 Aerothermodynamics Hub]] (heat-transfer block, Weeks 9–12)
