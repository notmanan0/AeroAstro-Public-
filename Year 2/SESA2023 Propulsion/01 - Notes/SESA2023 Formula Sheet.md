---
title: "SESA2023 Formula Sheet"
module: "SESA2023 Propulsion"
type: formula
aliases: ["SESA2023 formulae", "Propulsion formula sheet"]
tags: [sesa2023, formula, exam-prep]
status: complete
coverage: "W01–W11, all eleven topic notes (all lectured)"
sources: ["02 - Sources/Data Book.pdf", "01 - Notes/Topics", "01 - Notes/Concepts", "01 - Notes/Tutorials", "03 - Exams & Past Papers/Solutions"]
---

# SESA2023 Formula Sheet

Coverage: W01–W11, one section per topic note. Items marked ★ are not printed in the Thermofluids Data Book (2022 edition), which is provided in the exam; everything else is in it, sometimes under a different symbol (see the table of symbols below).

> [!info] Contents of the Data Book
> - Perfect gas: $c_p-c_v=R$, $a=\sqrt{\gamma RT}$, $s_2-s_1$ in its three forms, the isentropic relations; Dalton's law and mixture enthalpy and entropy.
> - The SFEE and the steady-flow momentum equation.
> - Compressible flow: stagnation-to-static ratios, $V/\sqrt{c_pT_0}$ and the flow functions $\dot m\sqrt{c_pT_0}/(Ap_0)$ and $\dot m\sqrt{c_pT_0}/(Ap)$, $A/A^*$, the general and choked $\dot m/[\rho_0(2c_pT_0)^{1/2}]$, the normal-shock relations (subscript $s$ for the state behind the shock), Prandtl–Meyer, and the Fanno $4c_fL_{max}/D$ relation, which this course does not use.
> - Combustion: $AFR$, $\phi=AFR_{st}/AFR$ and the steady-flow combustion balance through a reference state.
> - Efficiencies: $\eta_c$, $\eta_t$; for aircraft $\eta_p$, $\eta_f$ (the course's $\eta_{th}$), $\eta_o=\eta_p\eta_f$, sfc $=\dot m_f/T_{net}$ and the Breguet range.
> - Rockets: $I_{sp}$, $c_e$, $C^*$, $C_F$, the mass definitions, $\lambda$, $\delta$, the Tsiolkovsky equation, $(m_{pl})_i=(m_0)_{i+1}$ and $\lambda_o=\prod\lambda_i$.
> - Tables: 1 calorific values; 2 perfect-gas data; 3 molar enthalpies; 4 enthalpies of reaction; 5 $\ln K^\theta$; 19–22 gas-flow tables for $\gamma=1.400$ and 1.333; 24 ISA at selected altitudes in feet; 25 ISA every 1000 m. $g=9.80665$ m/s², $\bar R=8.3145$ kJ kmol⁻¹ K⁻¹.
> - Not in it: the thrust equation, station-by-station engine relations, oblique shocks, the duct friction and heating relations, intake efficiency, turbomachinery and solid motors.

## Symbols and conventions

| Symbol | Meaning and where it applies |
|---|---|
| subscript 0 | stagnation (total) value; no subscript means static. Gas-turbine pressure ratios are stagnation ratios unless stated. Two exceptions: $V_0$ is the flight speed in W01, and $T_0=298$ K is the combustion reference temperature in W05. |
| $V_0$ (W01), $V$ (W06–W07) | flight speed. W03 writes the local flow speed as $U$; W08–W09 use $V$ for absolute velocity, $V_{rel}$ for relative velocity and $U$ for blade speed. |
| $P_A$, $P_j$, $P_e$, $P_c$ (W01, W10–W11) | ambient, jet exit, nozzle exit and chamber pressure; elsewhere written $p_a$, $p_b$ (back pressure). |
| $c_{pa}$, $\gamma_a$ | cold stream (intake, compressor, fan, bypass): 1005 J kg⁻¹ K⁻¹ and 1.4, with $R=287$ J kg⁻¹ K⁻¹. The Data Book lists 1.01 kJ kg⁻¹ K⁻¹; either is accepted if stated. |
| $c_{pp}$, $\gamma_p$ | hot stream (combustion products, after the burner): as given in the question; worked examples use 1100–1200 J kg⁻¹ K⁻¹ and 1.33–1.35. Turbine and core-nozzle pressure ratios use $\gamma_p$. |
| TSFC, sfc | thrust-specific fuel consumption $\dot m_f/F$; the Data Book writes sfc and calls net thrust $T_{net}$. |
| $g_0$ | 9.81 m/s² in the rocket notes and worked examples; the Data Book gives 9.80665. |

Station numbers:

| Engine | Stations |
|---|---|
| Turbojet (W02, W06) | 1 free stream, 2 compressor inlet, 3 burner inlet, 4 turbine inlet, 5 turbine exit, 6 nozzle exit |
| Ramjet (W06) | 1 free stream, 2 diffuser exit, 3 combustor exit, 4 nozzle exit |
| Reheat (W06) | 6 afterburner exit, 8 nozzle throat |
| Two-spool turbofan (W07) | 2 fan face, 13 bypass after the fan, 19 bypass nozzle exit, 23 core after fan root and booster, 3 HPC exit, 4 HPT entry, 45 LPT entry, 5 LPT exit, 9 core nozzle exit |

## W01 Thrust, efficiencies, range and the ISA

Note: [[SESA2023 W01 - Thrust, Efficiency, Range and the ISA]]

★ Thrust, steady flow in the engine frame, control-volume faces where $p=P_A$, uniform jet:

$$
F=\dot m_a\big[(1+f)V_j-V_0\big]+A_j(P_j-P_A)\quad\text{(air-breather)},\qquad F=\dot mV_j+A_j(P_j-P_A)\quad\text{(rocket)}
$$

$F=\dot m_a(V_j-V_0)$ needs both a fully expanded jet ($P_j=P_A$) and $f\ll1$; $-\dot m_aV_0$ is the ram drag.

Efficiencies, general forms (the Data Book's $\eta_p$, $\eta_f$, $\eta_o$):

$$
\eta_P=\frac{FV_0}{\tfrac12\dot m_a\big[(1+f)V_j^2-V_0^2\big]},\qquad \eta_{th}=\frac{\tfrac12\dot m_a\big[(1+f)V_j^2-V_0^2\big]}{\dot m_f\,LCV},\qquad \eta_O=\frac{FV_0}{\dot m_f\,LCV}=\eta_P\,\eta_{th}
$$

★ Simplified forms, valid only with $P_j=P_A$ and $f\ll1$:

$$
\eta_P=\frac{2}{1+V_j/V_0},\qquad \eta_{th}=\frac{V_j^2-V_0^2}{2f\,LCV},\qquad \eta_O=\frac{V_0(V_j-V_0)}{f\,LCV}=\frac{V_0}{\mathrm{TSFC}\cdot LCV}
$$

- $\mathrm{TSFC}=\dot m_f/F=f/(F/\dot m_a)$ in kg s⁻¹ N⁻¹, often quoted in g s⁻¹ kN⁻¹.
- ★ Wake loss (same conditions): $\dot W_{jet}-FV_0=\tfrac12\dot m_a(V_j-V_0)^2$.
- With a burner efficiency, $\eta_bLCV$ goes in the energy balance but the full LCV stays in $\eta_{th}$ and $\eta_O$.

Breguet range, steady level cruise at constant $V_0$, $L/D$ and TSFC, with $W_1$ the weight at the start of cruise and $W_2$ at the end:

$$
s=\frac LD\,\frac{V_0}{g_0\,\mathrm{TSFC}}\ln\frac{W_1}{W_2},\qquad ★\;s=\eta_O\,\frac{LCV}{g_0}\,\frac LD\,\ln\frac{W_1}{W_2}
$$

ISA (Data Book Tables 24 and 25, as $\delta=P/P_{ref}$, $\theta=T/T_{ref}$, $\sigma=\rho/\rho_{ref}$ with 101.325 kPa, 288.15 K and 1.225 kg/m³): $T$ falls by 6.5 K/km up to 11 km and is 216.65 K from 11 to 20 km. Flight speed $V_0=M_0\sqrt{\gamma RT}$ with the static $T$ from the table. The hydrostatic formulae behind the table, $P/P_{ref}=(T/T_{ref})^{5.256}$ in the troposphere and $P/P_{11}=\exp[-g(h-h_{11})/(RT_{11})]$ in the stratosphere, are not lectured; use the table values.

## W02 Thermodynamics, mixtures, SFEE and isentropic efficiency

Note: [[SESA2023 W02 - Thermodynamics, Mixtures, SFEE and Isentropic Efficiency]]

Perfect gas (constant $c_p$, $c_v$): $p=\rho RT$, $R=\bar R/M$, $R=c_p-c_v$, $\gamma=c_p/c_v$, so ★ $c_p=\gamma R/(\gamma-1)$.

SFEE, steady, one stream, $gz$ neglected, heat in and shaft work out positive:

$$
q-w_x=\Big(h+\tfrac12V^2\Big)_{out}-\Big(h+\tfrac12V^2\Big)_{in}=h_{0,out}-h_{0,in}
$$

Entropy change of a perfect gas, and the isentropic relation ($s_2=s_1$):

$$
s_2-s_1=c_p\ln\frac{T_2}{T_1}-R\ln\frac{p_2}{p_1},\qquad \frac{T_2}{T_1}=\left(\frac{p_2}{p_1}\right)^{(\gamma-1)/\gamma}\quad\big((\gamma-1)/\gamma=0.2857\text{ for air}\big)
$$

★ Mixtures of perfect gases, with mole fraction $y_i=n_i/n$, mass fraction $x_i=m_i/m$ and $M$ the molar mass (not the Mach number):

$$
M=\sum y_iM_i,\qquad \frac1M=\sum\frac{x_i}{M_i},\qquad x_i=y_i\frac{M_i}{M},\qquad p_i=y_ip,\qquad c_p=\sum x_ic_{p,i},\qquad R=\frac{\bar R}{M}
$$

Specific properties are mass-weighted; "percent by volume" is a mole fraction. Dalton's law $p=\sum p_i$ is in the Data Book.

Isentropic efficiencies, adiabatic machines, one $c_p$ across the machine (static states 1→2 in W02; the same forms with stagnation states in W06–W09):

$$
\eta_c=\frac{T_{2s}-T_1}{T_2-T_1},\qquad \eta_t=\frac{T_1-T_2}{T_1-T_{2s}},\qquad T_{2s}=T_1\left(\frac{p_2}{p_1}\right)^{(\gamma-1)/\gamma}
$$

The real exit is hotter than the isentropic one in both machines.

★ Turbojet components (stations 1–6, KE neglected inside the engine): diffuser $h_2=h_1+\tfrac12V_1^2$; compressor $w_c=h_3-h_2$; burner $q_{34}=h_4-h_3$; turbine $w_t=h_4-h_5=w_c$; nozzle $\tfrac12V_6^2=h_5-h_6$.

## W03 Compressible flow, normal shocks and nozzles

Note: [[SESA2023 W03 - Compressible Flow, Normal Shocks and Nozzles]]

Perfect gas, steady, quasi-1D, adiabatic; isentropic everywhere except across a shock. $U$ is the flow speed.

$$
a=\sqrt{\gamma RT},\qquad M=\frac Ua,\qquad \frac{T_0}{T}=1+\frac{\gamma-1}2M^2,\qquad \frac{p_0}{p}=\left(\frac{T_0}{T}\right)^{\frac{\gamma}{\gamma-1}},\qquad \frac{\rho_0}{\rho}=\left(\frac{T_0}{T}\right)^{\frac{1}{\gamma-1}}
$$

$T_0$ is constant in any adiabatic flow with no work, shocks and friction included; $p_0$ and $\rho_0$ are constant only if the flow is also isentropic.

★ Critical state ($M=1$): $T^*/T_0=2/(\gamma+1)$, $p^*/p_0=[2/(\gamma+1)]^{\gamma/(\gamma-1)}$, $\rho^*/\rho_0=[2/(\gamma+1)]^{1/(\gamma-1)}$; for $\gamma=1.4$ these are 0.8333, 0.5283 and 0.6339. A converging nozzle fed from a reservoir chokes once $p_b<p^*$.

★ Area–velocity relation, isentropic: $\dfrac1A\dfrac{dA}{dx}=\dfrac1U\dfrac{dU}{dx}\left(M^2-1\right)$, so $M=1$ only at a throat.

Isentropic area ratio and mass flow ($A^*$ is the sonic area; $p$ the local static pressure):

$$
\frac{A}{A^*}=\frac1M\left[\frac{2}{\gamma+1}\left(1+\frac{\gamma-1}{2}M^2\right)\right]^{\frac{\gamma+1}{2(\gamma-1)}},\qquad \frac{\dot m}{\rho_0(2c_pT_0)^{1/2}}=A\left(\frac p{p_0}\right)^{1/\gamma}\left[1-\left(\frac p{p_0}\right)^{\frac{\gamma-1}{\gamma}}\right]^{1/2}
$$

Choked throat, any $\gamma$ (first form in the Data Book, ★ second form):

$$
\dot m=\rho_0(2c_pT_0)^{1/2}A_t\left(\frac{2}{\gamma+1}\right)^{\frac{1}{\gamma-1}}\left(\frac{\gamma-1}{\gamma+1}\right)^{1/2}=\frac{A_tp_0}{\sqrt{T_0}}\sqrt{\frac{\gamma}{R}}\left(\frac{2}{\gamma+1}\right)^{\frac{\gamma+1}{2(\gamma-1)}}
$$

- ★ Air ($\gamma=1.4$, $R=287$): $\dot m=0.0404\,A_tp_0/\sqrt{T_0}$ in SI units, or equivalently $\dot m=\rho^*a^*A_t$. Use the general form for mixtures and rocket gases.
- ★ Nozzle thrust: $F=\dot mU_e+A_e(p_e-p_b)$; the pressure term vanishes only for $p_e=p_b$.

Normal shock, $M_1>1$:

$$
M_2^2=\frac{(\gamma-1)M_1^2+2}{2\gamma M_1^2-(\gamma-1)},\qquad \frac{p_2}{p_1}=1+\frac{2\gamma}{\gamma+1}\left(M_1^2-1\right),\qquad \frac{\rho_2}{\rho_1}=\frac{U_1}{U_2}=\frac{(\gamma+1)M_1^2}{(\gamma-1)M_1^2+2}
$$

- $T_{02}=T_{01}$; ★ $p_{02}/p_{01}=e^{-\Delta s/R}<1$, evaluated as $(p_{02}/p_2)(p_2/p_1)(p_1/p_{01})$ or read from the table.
- ★ Energy across the shock, $\dfrac{\gamma}{\gamma-1}\left(\dfrac{p_2}{\rho_2}-\dfrac{p_1}{\rho_1}\right)=\tfrac12\left(U_1^2-U_2^2\right)$; the Prandtl relation $U_1U_2=a^{*2}$ is in the Data Book.
- As $M_1\to\infty$: $M_2\to\sqrt{(\gamma-1)/(2\gamma)}=0.378$ and $\rho_2/\rho_1\to(\gamma+1)/(\gamma-1)=6$ (for $\gamma=1.4$); $p_2/p_1$ and $T_2/T_1$ grow without limit.
- ★ Shock in a C–D nozzle: $\dot m$ and $T_0$ are unchanged, so the flow behind it is isentropic again from the larger reference area $A_2^*=A_t\,p_{01}/p_{02}$. The eight regimes are in [[Converging-Diverging Nozzle Operating Regimes]].

## W04 Friction, heat addition, oblique shocks and intakes

Note: [[SESA2023 W04 - Friction, Heat Addition, Oblique Shocks and Intakes]]

★ Constant-area duct, perfect gas, steady 1-D. $f$ is the wall friction force divided by $p_1A$; $q$ is the heat added per unit mass divided by $h_1$ ($q<0$ is cooling). Friction alone ($q=0$) is Fanno flow and heating alone ($f=0$) is Rayleigh flow.

$$
p_1\left(1+\gamma M_1^2-f\right)=p_2\left(1+\gamma M_2^2\right),\qquad h_1\left(1+\frac{\gamma-1}2M_1^2+q\right)=h_2\left(1+\frac{\gamma-1}2M_2^2\right)
$$

$$
\mathcal A=\frac{M_1^2\left(1+\frac{\gamma-1}2M_1^2+q\right)}{\left(1+\gamma M_1^2-f\right)^2},\qquad M_2^2=\frac{-(1-2\mathcal A\gamma)\pm\sqrt{1-2\mathcal A(\gamma+1)}}{(\gamma-1)-2\mathcal A\gamma^2}
$$

- With $f=q=0$ the two roots are $M_2=M_1$ and the normal-shock $M_2$. A subsonic inlet takes the subsonic root; a supersonic inlet has two (decelerate but stay supersonic, or shock to subsonic), and the back pressure decides.
- The duct chokes at $\mathcal A=\mathcal A^*=1/[2(\gamma+1)]$ (0.2083 for $\gamma=1.4$), which sets the largest $f$ or $q$ for a given $M_1$.
- Friction and heating drive $M$ towards 1 from either side; cooling drives it away from 1. Friction always lowers $p_0$, and so does heating.
- Then $p_2/p_1$ from the momentum equation and $T_2/T_1=h_2/h_1$ from the energy equation.

★ Oblique shock, wave angle $\sigma$, flow deflection $\delta$, attached weak solution unless told:

$$
M_{n1}=M_1\sin\sigma,\qquad M_{n2}=M_2\sin(\sigma-\delta),\qquad \frac{\rho_2}{\rho_1}=\frac{\tan\sigma}{\tan(\sigma-\delta)},\qquad \tan\delta=2\cot\sigma\,\frac{M_1^2\sin^2\sigma-1}{M_1^2(\gamma+\cos2\sigma)+2}
$$

The normal-shock relations or table at $M_{n1}$ (not $M_1$) give $p_2/p_1$, $T_2/T_1$, $p_{02}/p_{01}$ and $M_{n2}$; then $M_2=M_{n2}/\sin(\sigma-\delta)$. $\delta=0$ at $\sigma=90^\circ$ and at the Mach angle $\sigma=\mu=\sin^{-1}(1/M_1)$; above $\delta_{max}$ the shock detaches.

Intakes, adiabatic ($T_{02}=T_{01}$) with negligible exit KE ($T_2\approx T_{02}$); state 1 is the free stream (static) and $T_{2s}$ is reached isentropically from $p_1$ to $p_{02}$:

$$
★\;\Gamma_d=\frac{p_{02}}{p_{01}},\qquad ★\;\eta_d=\frac{T_{2s}-T_1}{T_2-T_1}=\frac{\Gamma_d^{(\gamma-1)/\gamma}\left(1+\frac{\gamma-1}2M^2\right)-1}{\frac{\gamma-1}2M^2}
$$

Normal-shock (Pitot) intake: its loss is the normal-shock stagnation-pressure ratio at the flight Mach number (Data Book $p_{0s}/p_0$): 0.930 at M 1.5, 0.856 at M 1.7, 0.813 at M 1.8.

## W05 Combustion, stoichiometry and chemical equilibrium

Note: [[SESA2023 W05 - Combustion, Stoichiometry and Chemical Equilibrium]]

- ★ Air is 21 % O₂ and 79 % N₂* by volume (23.2 % and 76.8 % by mass): 3.762 kmol N₂* and 137.9 kg of air per kmol of O₂ ($M_{N_2^*}=28.15$ kg/kmol). N₂* is inert.
- ★ Complete combustion of $\mathrm C_x\mathrm H_y$ to CO₂ and H₂O needs $x+y/4$ kmol O₂ per kmol of fuel.
- $AFR=\dot m_a/\dot m_f$, $f=1/AFR$, and $\phi=AFR_{st}/AFR=f/f_{st}=n_{a,st}/n_a$; $\phi<1$ is lean. Kerosene (C₁₀H₂₁, $M=141$ kg/kmol): $AFR_{st}=14.9$, $f_{st}=0.067$; gas turbines run at $\phi\approx0.3$–0.4.

★ Adiabatic flame temperature: steady, adiabatic, no work, complete combustion, mass-weighted constant $c_{p,r}$ (reactants) and $c_{p,p}$ (products), LCV at the reference temperature $T_0=298$ K (not a stagnation value), reactants entering at $T_1$:

$$
T_2=T_0+\frac{\dfrac{LCV}{AFR+1}-c_{p,r}(T_0-T_1)}{c_{p,p}},\qquad c_{p,r}=\frac{AFR\,c_{p,a}+c_{p,f}}{AFR+1}
$$

This is the general combustion balance of the Data Book. It ignores dissociation, so it overestimates real flame temperatures.

★ Gas-turbine burner (turbojet stations 3→4), per kilogram of air, adiabatic, air $c_{pa}$, products $c_{pp}$, fuel supplied at $T_{ref}=298$ K:

$$
f=\frac{c_{pp}(T_{04}-T_{ref})-c_{pa}(T_{03}-T_{ref})}{LCV-c_{pp}(T_{04}-T_{ref})}
$$

- One $c_p$: $f=(T_{04}-T_{03})/[LCV/c_p-(T_{04}-T_{ref})]$.
- Incomplete combustion (ramjets): replace $LCV$ by $\eta_bLCV$. A heat loss $q_{loss}$ per kilogram of fuel makes the denominator $LCV-q_{loss}-c_{pp}(T_{04}-T_{ref})$.
- With $T_{ref}=0$ (Problem Sheet 4, pre-2020 papers), $(1+f)c_pT_{04}=c_pT_{03}+f\,LCV$, so $f=c_p(T_{04}-T_{03})/(LCV-c_pT_{04})$. The two conventions differ by about 1 %; state which you use.
- For a ramjet, the combustor runs 2→3, so $T_{03}\to T_{02}$ and $T_{04}\to T_{03}$ in the formulae above.

Chemical equilibrium for $a\,\mathrm A+b\,\mathrm B\rightleftharpoons c\,\mathrm C+d\,\mathrm D$, partial pressures in bar, $p^\theta=1$ bar, $K^\theta$ a function of $T$ only (Data Book Table 5 gives $\ln K^\theta$ for the reaction in the direction printed):

$$
K^\theta=\frac{(p_C/p^\theta)^c\,(p_D/p^\theta)^d}{(p_A/p^\theta)^a\,(p_B/p^\theta)^b},\qquad p_i=\frac{n_i}{n}\,p
$$

with $n$ the total moles of products. Atom balances reduce the unknowns to one; keep the root with every $n_i>0$. Higher $T$ favours dissociation of CO₂ and H₂O; higher $p$ suppresses it.

## W06 Brayton cycle, ramjet, turbojet and reheat

Note: [[SESA2023 W06 - Jet Engine Cycle Analysis - Brayton, Ramjet, Turbojet and Reheat]]

★ Ideal cold-air Brayton cycle (cycle states 1–4, constant $c_p$ and $\gamma$, $r_p=p_2/p_1=p_3/p_4$, $x=r_p^{(\gamma-1)/\gamma}$, $\theta=T_3/T_1$):

$$
\eta_{th}=1-\frac{1}{r_p^{(\gamma-1)/\gamma}},\qquad w_{net}=c_pT_1\left[\theta\left(1-\frac1x\right)-(x-1)\right]
$$

Maximum specific work at $x=\sqrt\theta$, i.e. $T_2=T_4$. With $\eta_c,\eta_t<1$ an optimum $r_p$ for efficiency appears, and it rises with $T_{04}/T_{02}$.

★ Ideal ramjet (stations 1–4 above; isentropic diffuser and nozzle, isobaric combustor, fully expanded $p_4=p_a$, one $\gamma$):

$$
M_4=M_1,\qquad \frac{F}{\dot m_a}=(1+f)V_4-V=M_1\sqrt{\gamma RT_a}\left[(1+f)\sqrt{\frac{T_{03}}{T_{02}}}-1\right],\qquad \eta_{th}=1-\frac{T_a}{T_{01}}
$$

with $T_{02}=T_{01}=T_a\left(1+\frac{\gamma-1}2M_1^2\right)$ and $f$ from the W05 balance in ramjet stations.

★ Real ramjet, with $\Gamma_d=p_{02}/p_{01}$, $\Gamma_c=p_{03}/p_{02}$, $\Gamma_n=p_{04}/p_{03}$ and $\eta_b=LCV_{eff}/LCV$; fully expanded, adiabatic nozzle ($T_{04}=T_{03}$):

$$
\frac{p_{04}}{p_a}=\Gamma_d\Gamma_c\Gamma_n\,\frac{p_{01}}{p_a},\qquad V_4=\sqrt{2c_pT_{03}\left[1-\left(\frac{p_a}{p_{04}}\right)^{(\gamma-1)/\gamma}\right]}
$$

so $M_4<M_1$. Gas-turbine questions usually take every $\Gamma$ and $\eta_b$ as 1; ramjet questions give them.

★ Turbojet march (stations 1–6; $c_{pa}$, $\gamma_a$ up to station 3, $c_{pp}$, $\gamma_p$ after; adiabatic components; one spool with no off-take):

1. Intake: $T_{02}=T_{01}=T_1\left(1+\frac{\gamma_a-1}2M^2\right)$, $p_{02}=\Gamma_dp_{01}$ ($\Gamma_d=1$ unless stated).
2. Compressor: $T_{03}=T_{02}\left[1+\left(r_c^{(\gamma_a-1)/\gamma_a}-1\right)/\eta_c\right]$, $w_c=c_{pa}(T_{03}-T_{02})$.
3. Burner: $f$ from W05; $p_{04}=\Gamma_bp_{03}$.
4. Turbine, zero net work on the spool: $c_{pa}(T_{03}-T_{02})=(1+f)c_{pp}(T_{04}-T_{05})$; then $T_{05s}=T_{04}-(T_{04}-T_{05})/\eta_t$ and $p_{05}=p_{04}(T_{05s}/T_{04})^{\gamma_p/(\gamma_p-1)}$.
5. Nozzle, isentropic and fully expanded: $T_6=T_{05}(p_a/p_{05})^{(\gamma_p-1)/\gamma_p}$, $V_j=\sqrt{2c_{pp}(T_{05}-T_6)}$.

★ Performance:

$$
\frac{F_N}{\dot m_a}=(1+f)V_j-V,\qquad \mathrm{sfc}=\frac{f}{F_N/\dot m_a},\qquad \eta_{th}=\frac{(1+f)V_j^2-V^2}{2f\,LCV},\qquad \eta_O=\frac{(F_N/\dot m_a)\,V}{f\,LCV}
$$

★ Reheat: choked nozzle throat with product properties,

$$
\dot m=\frac{A_8\,p_{06}}{\sqrt{T_{06}}}\sqrt{\frac{\gamma}{R}}\left(\frac{2}{\gamma+1}\right)^{\frac{\gamma+1}{2(\gamma-1)}}
$$

To leave the engine upstream unaffected, $\dot m$ and $p_{06}$ are held, so $A_8\propto\sqrt{T_{06}}$ (neglecting the extra fuel and the change in $\gamma$, which add a little more).

## W07 Turbofan architectures and fan pressure ratio

Note: [[SESA2023 W07 - Turbofan Architectures and Fan Pressure Ratio Selection]]

Two-spool turbofan, steady, zero net work on each spool, isentropic intake, separate fully expanded nozzles, cold-air properties unless product values are given. $BPR=\dot m_b/\dot m_c$, $f=\dot m_f/\dot m_c$, $fpr=p_{013}/p_{02}$.

★ Spool balances (work absorbed = work delivered):

$$
\dot m_c\left(h_{03}-h_{023}\right)=(\dot m_c+\dot m_f)\left(h_{04}-h_{045}\right),\qquad BPR=\frac{(1+f)\left(h_{045}-h_{05}\right)-\left(h_{023}-h_{02}\right)}{h_{013}-h_{02}}
$$

★ Fan and jets (fan efficiency $\eta_f$):

$$
T_{013}=T_{02}\left(1+\frac{fpr^{(\gamma-1)/\gamma}-1}{\eta_f}\right),\qquad V_{jb}=\sqrt{2c_pT_{013}\left[1-\left(\frac{p_a}{fpr\,p_{02}}\right)^{(\gamma-1)/\gamma}\right]}
$$

The core jet $V_{jc}$ follows the same way from $T_{05}$ and $p_{05}$. At a given flight condition and $\eta_f$, $V_{jb}$ and so $\eta_P$ depend only on fpr.

★ Thrust, fully expanded separate jets:

$$
\frac{F}{\dot m_c}=(1+f)V_{jc}+BPR\,V_{jb}-(1+BPR)V
$$

- Matched jets ($V_{jc}=V_{jb}=V_j$) give the highest $\eta_P$ for a given thrust and core. With $f\ll1$ the specific thrust per kilogram of total air is $X=F_N/\dot m_{air}=V_j-V$, and $\eta_P=2/(1+V_j/V)$.
- A lower fpr gives a higher bpr for the same core, a higher $\eta_P$ and a lower bare sfc, but a bigger, heavier nacelle with more drag.
- Geared fan: with gear ratio $G$ the LPT turns $G$ times faster, so at fixed loading each LPT stage does about $G^2$ times the work.

★ Installation, with $X=F_N/\dot m_a$ in m/s and $kV\approx9$ m/s:

$$
F_{N,eff}=F_{N,bare}\left(1-\frac{kV}{X}\right)\approx F_{N,bare}\left(1-\frac{9.25}{X}\right),\qquad W_{eng}=12\left(\frac{d}{3\ \mathrm m}\right)^{2.4}\ \mathrm t,\qquad F_{N,corr}=F_{N,eff}-\frac{W_{eng}}{L/D}
$$

## W08 Turbomachinery principles, Euler equation and velocity triangles

Note: [[SESA2023 W08 - Turbomachinery Principles - Euler Equation and Velocity Triangles]]

★ Euler work equation, steady (or time-averaged), adiabatic, so $\Delta h_0$ is the shaft work; $U=r\Omega$:

$$
\dot W=T\Omega=\dot m\left(U_2V_{\theta2}-U_1V_{\theta1}\right),\qquad \Delta h_0=U_2V_{\theta2}-U_1V_{\theta1}
$$

$\Delta h_0>0$ for a compressor and $<0$ for a turbine; torque $=\dot W/\Omega$ and $\Delta T_0=\Delta h_0/c_p$.

★ Velocity triangles, angles from the axial direction, positive in the direction of blade motion:

$$
V_{x,rel}=V_x,\qquad V_{\theta,rel}=V_\theta-U,\qquad \tan\alpha=\frac{V_\theta}{V_x},\qquad \tan\alpha_{rel}=\frac{V_{\theta,rel}}{V_x},\qquad V=\frac{V_x}{\cos\alpha}
$$

★ Mean line at constant radius and constant $V_x$:

$$
\Delta h_0=UV_x\left(\tan\alpha_2-\tan\alpha_1\right)=UV_x\left(\tan\alpha_{2,rel}-\tan\alpha_{1,rel}\right)
$$

- $\alpha$ is the flow angle and $\beta$ the metal angle. Incidence $i=\alpha_{in}-\beta_{in}$; deviation is the difference between the exit flow and metal angles (taken as $\alpha_{out}-\beta_{out}$; quote its magnitude and state the sign). With no deviation the exit flow follows the metal angle.
- Rotor aerodynamics (incidence, relative Mach number) use the relative frame; stators, kinetic energy and absolute Mach number use the absolute frame.
- ★ Mirror blading: $V_{\theta3}=-V_{\theta2,rel}$, $\alpha_3=-\alpha_{2,rel}$. A repeating mirror stage ($\alpha_3=\alpha_1$) has $V_{\theta1}+V_{\theta2}=U$, i.e. 50 % reaction.
- ★ Degree of reaction (a Problem Sheet 8 term, not lectured; a 50 % stage is mirror blading): $R=\dfrac{h_2-h_1}{h_3-h_1}=1-\dfrac\phi2\left(\tan\alpha_1+\tan\alpha_2\right)$ for a repeating stage with constant $V_x$. A 50 % stage has $\tan\alpha_1+\tan\alpha_2=1/\phi$ and $\tan\alpha_2-\tan\alpha_1=\psi/\phi$.

## W09 Turbomachinery characteristics, similarity and maps

Note: [[SESA2023 W09 - Turbomachinery Characteristics - Coefficients, Similarity and Maps]]

★ Flow and stage-loading coefficients, mean line (state the radius, usually mid-span):

$$
\phi=\frac{V_x}{U},\qquad \psi=\frac{|\Delta h_0|}{U^2}=\frac{|\Delta V_\theta|}{U}\ \ (\text{constant }r),\qquad n_{stages}\ge\frac{\Delta h_{0,overall}}{\psi_{max}U^2}
$$

Round the stage count up and recompute the actual $\psi$; equal work per stage. Loading limits: compressor $\psi\le0.65$ (typically 0.35–0.5), turbine $\psi\le2.5$. Per stage, the pressure ratio is limited to about 2 (axial compressor) or 10 (centrifugal); equal stages give $\pi=\pi_{stage}^n$.

Axial velocity from the axial Mach number (Data Book form): $V_x/\sqrt{c_pT_0}=\sqrt{\gamma-1}\,M\left(1+\frac{\gamma-1}2M^2\right)^{-1/2}$.

★ Incompressible machines (pumps, fans, hydraulic turbines), geometrically similar:

$$
\frac{\Delta p}{\rho\Omega^2D^2},\ \eta,\ \frac{\dot W}{\rho\Omega^3D^5}=fn\left(\frac{Q}{\Omega D^3},\ Re=\frac{\rho\Omega D^2}{\mu}\right)
$$

The Reynolds-number effect is weak above $Re\approx2\times10^5$.

★ Compressible machines, same gas in model and full size:

$$
\frac{p_{02}}{p_{01}},\ \frac{T_{02}}{T_{01}},\ \eta,\ \frac{\dot W}{\dot mc_pT_{01}}=fn\left(\frac{\dot m\sqrt{c_pT_{01}}}{D^2p_{01}},\ \frac{ND}{\sqrt{c_pT_{01}}}\right)
$$

For one machine on one gas these reduce to $\dot m\sqrt{T_{01}}/p_{01}$ and $N/\sqrt{T_{01}}$, the map axes.

★ Scale test: match the Mach number (so $V_x/\sqrt{c_pT_{01}}$, equivalently $ND/\sqrt{T_{01}}$), $\phi$ and $\psi$; Reynolds number is not matched. Then

$$
\frac{\dot m_t}{\dot m}=\left(\frac{D_t}{D}\right)^2\frac{p_{01,t}}{p_{01}}\sqrt{\frac{T_{01}}{T_{01,t}}},\qquad \frac{\dot W_t}{\dot W}=\frac{\dot m_t}{\dot m}\left(\frac{U_t}{U}\right)^2
$$

A throttle is adiabatic with no work, so $T_0$ is unchanged through it.

★ Specific speed ($\Omega$ in rad/s, SI units; inlet volume flow and $\Delta h_0$ for compressible machines):

$$
N_s=\frac{\phi^{1/2}}{\psi^{3/4}}=\frac{\Omega\,Q^{1/2}}{(\Delta p/\rho)^{3/4}}
$$

Below about 0.4 centrifugal (radial), 0.4–2 mixed flow, above about 2 axial and propellers.

Maps: a compressor speed line ends at surge (low flow) and turns vertical at choke (high flow); a turbine whose first stator chokes has a fixed $\dot m\sqrt{T_{01}}/p_{01}$ at every speed. A nozzle's flow function rises with pressure ratio until it chokes at $p/p_0=0.528$ (air).

★ Propellers (examined in 2023-24, not lectured in 2025-26): actuator disk $V_{disk}=\tfrac12(V_\infty+V_j)$, $T=\dot m(V_j-V_\infty)=\rho AV_{disk}(V_j-V_\infty)=A\,\Delta p$, $\eta_P=2/(1+V_j/V_\infty)$; advance ratio $J=V_\infty/(nD)$ with $n$ in rev/s. See [[Actuator Disk Theory]].

## W10 Rocket performance, staging and power cycles

Note: [[SESA2023 W10 - Rocket Performance, Staging and Power Cycles]]

Thrust $F=\dot mV_j+A_e(P_e-P_A)$. ★ Ideal jet velocity: adiabatic, isentropic nozzle, fully expanded ($P_e=P_A$), perfect gas of combustion products ($c_p$, $\gamma$ as given):

$$
V_j=\sqrt{2c_pT_{0c}\left[1-\left(\frac{P_e}{P_{0c}}\right)^{\frac{\gamma-1}{\gamma}}\right]},\qquad c_pT=\frac{\gamma}{\gamma-1}\frac{\bar R}{M}T
$$

A light exhaust (low molar mass $M$), a hot chamber and a high pressure ratio raise $V_j$.

Performance parameters:

$$
I_{sp}=\frac{F}{g_0\dot m},\qquad c_e=\frac{F}{\dot m}=g_0I_{sp},\qquad C^*=\frac{p_cA_t}{\dot m},\qquad C_F=\frac{F}{p_cA_t},\qquad c_e=C^*C_F
$$

$C^*$ measures the combustor and $C_F$ the nozzle; the throat is choked, so the throat area comes from the W03 choked-flow formula with the rocket $\gamma$ and $R$.

★ Ideal values (choked throat, isentropic, perfect gas):

$$
C^*=\sqrt{\frac{RT_c}{\gamma}}\left(\frac{\gamma+1}{2}\right)^{\frac{\gamma+1}{2(\gamma-1)}},\qquad C_F=\sqrt{\frac{2\gamma^2}{\gamma-1}\left(\frac{2}{\gamma+1}\right)^{\frac{\gamma+1}{\gamma-1}}\left[1-\left(\frac{P_e}{P_c}\right)^{\frac{\gamma-1}{\gamma}}\right]}+\frac{P_e-P_A}{P_c}\,\frac{A_e}{A_t}
$$

Masses: $m_0=m_{pl}+m_p+m_{dw}$, $m_{bo}=m_{pl}+m_{dw}$, $\lambda=m_{pl}/m_0$, $\delta=m_{dw}/m_0$, $MR=m_0/m_{bo}=1/(\lambda+\delta)$.

Tsiolkovsky equation, constant $c_e$, no gravity or drag (derive it from $m\,dV=-c_e\,dm$):

$$
\Delta V_{ideal}=c_e\ln\frac{m_0}{m_{bo}}=c_e\ln\frac{1}{\lambda+\delta}
$$

★ Staging, worked from the top stage down because only the last stage's payload is known:

$$
\lambda_i=\exp\!\left(-\frac{\Delta V_i}{c_{e,i}}\right)-\delta_i,\qquad (m_0)_i=\frac{(m_{pl})_i}{\lambda_i},\qquad (m_{pl})_i=(m_0)_{i+1},\qquad \lambda_0=\prod_i\lambda_i,\qquad \Delta V_0=\sum_i\Delta V_i
$$

Propellant of stage $i$: $(m_p)_i=(m_0)_i(1-\lambda_i-\delta_i)$.

★ Gravity and drag losses, flight-path angle $\psi$ from the horizontal: $\Delta V=\Delta V_{ideal}-\int_0^tg\sin\psi\,dt-\int_0^t\dfrac Dm\,dt$.

## W11 Solid propellants and rocket nozzle design

Note: [[SESA2023 W11 - Solid Propellants and Rocket Nozzle Design]]

★ Burning rate (Saint-Robert's law) and quasi-steady chamber pressure, with gas generated $\rho_pA_br$ equal to gas discharged through the choked throat $P_cA_t/C^*$:

$$
r=aP_c^{\,n},\qquad P_c=\left(\rho_paC^*\frac{A_b}{A_t}\right)^{\frac{1}{1-n}},\qquad \frac{dP_c}{P_c}=\frac{1}{1-n}\,\frac{d(A_b/A_t)}{A_b/A_t}
$$

- Stable only for $n<1$; in practice $0.2\lesssim n\lesssim0.8$, and sensitivity grows as $n\to1$. $A_b/A_t$ is often written $K_n$.
- Thrust $F=C_FP_cA_t$; a higher grain temperature raises $r$ and the thrust and shortens the burn, with the total impulse roughly unchanged.
- Erosive burning matters when the port-to-throat area ratio $A_p/A_t<4$.

★ Conical nozzle divergence factor (spherical exit wavefront, half-angle $\alpha$), multiplying the momentum thrust:

$$
\lambda=\frac{1+\cos\alpha}{2}
$$

0.989 at 12°, 0.983 at 15°, 0.976 at 18°. This $\lambda$ is not the W10 payload ratio.

## Legacy (2013–19 papers only)

★ Ion thruster, singly charged ions of mass $m_i$ through a net potential $V_b$, beam current $I_b$, divergence half-angle $\theta$: $v=\sqrt{2qV_b/m_i}$, $\dot m=I_bm_i/q$, $F=\dot mv\cos\theta$. Not in the current lecture notes; see [[Electric (Ion) Propulsion]].

## Related

- [[SESA2023 Propulsion Hub]] · [[SESA2023 Past Paper Map]]
