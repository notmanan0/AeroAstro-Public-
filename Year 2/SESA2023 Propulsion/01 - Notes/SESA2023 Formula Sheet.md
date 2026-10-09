---
title: "SESA2023 Formula Sheet"
module: "SESA2023 Propulsion"
type: formula
aliases: ["SESA2023 formulae", "Propulsion formula sheet"]
tags: [sesa2023, formula, exam-prep]
status: complete
sources: ["02 - Sources/Data Book.pdf", "01 - Notes/Topics"]
---

# SESA2023 Formula Sheet

Everything on one page, organised by lecture week. Items marked ★ are **not** in the Thermofluids Data Book, so memorise them.

> [!info] What the Data Book gives you
> - One-dimensional perfect-gas flow: isentropic relations, the flow functions and $A/A^*$, Fanno (adiabatic constant-area) flow, normal-shock relations, Prandtl–Meyer.
> - Gas tables for $\gamma = 1.4$ and $1.333$.
> - Gas properties (Table 2), calorific values (Table 1), molar enthalpies (Table 3), $\ln K^\theta$ (Table 5), ISA (Tables 24 ft and 25 km).
> - $g = 9.80665$ m/s² and $\bar R = 8.3145$ kJ kmol⁻¹ K⁻¹.

## W1 Thrust, efficiency, range ([[SESA2023 W01 - Thrust, Efficiency, Range and the ISA]])

$$
★\;F = \dot m_a[(1+f)V_j-V]+(p_j-p_a)A_j\qquad\text{rocket: }F = \dot mV_e+(p_e-p_a)A_e
$$

$$
★\;\eta_P = \frac{FV}{\tfrac12\dot m_a[(1+f)V_j^2-V^2]}\approx\frac{2}{1+V_j/V},\qquad ★\;\eta_{th} = \frac{\tfrac12\dot m_a[(1+f)V_j^2-V^2]}{\dot m_fLCV},\qquad ★\;\eta_O = \frac{FV}{\dot m_fLCV} = \eta_P\eta_{th}
$$

$$
★\;\text{TSFC} = \frac{\dot m_f}{F} = \frac{f}{F/\dot m_a} = \frac{V}{\eta_O\,LCV},\qquad ★\;s = \frac LD\frac{\eta_OLCV}{g}\ln\frac{m_{initial}}{m_{final}}
$$

- Turbofan: ★ $\dfrac{F}{\dot m_c} = (1+f)V_{jh}+BPR\,V_{jc}-(1+BPR)V$.
- ISA: sea level is 288.15 K and 101.325 kPa; $-6.5$ K/km to 11 km; then 216.65 K up to 20 km.

## W2 Thermodynamics ([[SESA2023 W02 - Thermodynamics, Mixtures, SFEE and Isentropic Efficiency]])

$$
q-w_x = h_{0,2}-h_{0,1},\qquad s_2-s_1 = c_p\ln\frac{T_2}{T_1}-R\ln\frac{p_2}{p_1},\qquad c_p = \frac{\gamma R}{\gamma-1}
$$

$$
★\;\eta_c = \frac{T_{02s}-T_{01}}{T_{02}-T_{01}},\qquad ★\;\eta_t = \frac{T_{01}-T_{02}}{T_{01}-T_{02s}},\qquad \frac{T_{02s}}{T_{01}} = \left(\frac{p_{02}}{p_{01}}\right)^{(\gamma-1)/\gamma}
$$

★ **Mixtures**: $c_p = \sum x_ic_{p,i}$ (mass fractions), $\mathcal M = (\sum x_i/\mathcal M_i)^{-1}$, $R = \bar R/\mathcal M$, $p_i = y_ip$.

## W3 Compressible flow, shocks, nozzles ([[SESA2023 W03 - Compressible Flow, Normal Shocks and Nozzles]])

$$
a = \sqrt{\gamma RT},\qquad \frac{T_0}{T} = 1+\frac{\gamma-1}2M^2,\qquad \frac{p_0}{p} = \left(\frac{T_0}{T}\right)^{\frac{\gamma}{\gamma-1}},\qquad \frac{A}{A^*} = \frac1M\left[\frac{2}{\gamma+1}\left(1+\frac{\gamma-1}{2}M^2\right)\right]^{\frac{\gamma+1}{2(\gamma-1)}}
$$

$$
\dot m_{choked} = \frac{A_tp_0}{\sqrt{RT_0}}\sqrt\gamma\left(\frac{2}{\gamma+1}\right)^{\frac{\gamma+1}{2(\gamma-1)}},\qquad \frac{T^*}{T_0} = \frac{2}{\gamma+1},\qquad \frac{p^*}{p_0} = \left(\frac{2}{\gamma+1}\right)^{\frac{\gamma}{\gamma-1}}\ (0.528\text{ for air})
$$

$$
V_j = \sqrt{2c_pT_0\left[1-\left(\frac{p}{p_0}\right)^{(\gamma-1)/\gamma}\right]}\qquad(\text{isentropic nozzle; the SFEE plus the isentropic relation})
$$

**Normal shock**:

$$
M_2^2 = \frac{1+\frac{\gamma-1}2M_1^2}{\gamma M_1^2-\frac{\gamma-1}2},\qquad \frac{p_2}{p_1} = 1+\frac{2\gamma}{\gamma+1}(M_1^2-1),\qquad \frac{\rho_2}{\rho_1} = \frac{V_1}{V_2} = \frac{(\gamma+1)M_1^2}{(\gamma-1)M_1^2+2}
$$

$T_0$ is constant across the shock and $p_0$ falls. See [[Converging-Diverging Nozzle Operating Regimes]] for the eight C–D regimes.

## W4 Friction, heating, oblique shocks, intakes ([[SESA2023 W04 - Friction, Heat Addition, Oblique Shocks and Intakes]])
- ★ Friction (Fanno) and heating (Rayleigh) both drive $M\to1$. Heating always lowers $p_0$ (the Rayleigh loss).
- ★ Oblique shock: $M_{n1} = M_1\sin\sigma$, and $\tan\delta = 2\cot\sigma\dfrac{M_1^2\sin^2\sigma-1}{M_1^2(\gamma+\cos2\sigma)+2}$.
- ★ Component losses: $\Gamma_d = p_{02}/p_{01}$, $\Gamma_c = p_{03}/p_{02}$, $\Gamma_n = p_{04}/p_{03}$, so $p_{04}/p_a = \Gamma_d\Gamma_c\Gamma_n\,p_{01}/p_a$.
- ★ Intake efficiency: $\eta_d = (T_{02s}-T_a)/(T_{01}-T_a)$.

## W5 Combustion ([[SESA2023 W05 - Combustion, Stoichiometry and Chemical Equilibrium]])
- ★ Air is $\mathrm{O_2+3.762\,N_2^*}$, i.e. 137.9 kg per kmol O₂.
- ★ $\mathrm{C_xH_y}$ needs $x+y/4$ kmol O₂ per kmol of fuel.
- ★ $\phi = f/f_{st}$.

★ **Burner** (fuel at $T_{ref} = 298$ K):

$$
f = \frac{c_{p,g}(T_{03}-T_{ref})-c_{p,a}(T_{02}-T_{ref})}{\eta_bLCV-q_{loss}-c_{p,g}(T_{03}-T_{ref})}\qquad\left(\text{pre-2020 papers: }f = \frac{c_p(T_{03}-T_{02})}{LCV-c_pT_{03}}\right)
$$

**Equilibrium**: $K^\theta = \prod(p_i/p^\theta)^{\nu_i}$ (products over reactants), $p_i = (n_i/n)p$. Close the system with atom balances.

## W6 Cycles ([[SESA2023 W06 - Jet Engine Cycle Analysis - Brayton, Ramjet, Turbojet and Reheat]])
- ★ Ideal Brayton: $\eta = 1-r_p^{-(\gamma-1)/\gamma}$.
- ★ Turbojet work balance: $c_{p,a}(T_{03}-T_{02}) = (1+f)c_{p,g}(T_{04}-T_{05})$.
- ★ Ideal ramjet ($M_e = M$):

$$
★\;\frac{F}{\dot m_a} = M\sqrt{\gamma RT_a}\left[(1+f)\sqrt{\frac{T_{03}}{T_{02}}}-1\right],\qquad \eta_{th} = 1-\frac{T_a}{T_{02}}
$$

★ **Reheat**: the choked throat needs $A_8\propto(1+f_{tot})\sqrt{T_{0,nozzle}}/p_{0,nozzle}$.

## W7 Turbofans ([[SESA2023 W07 - Turbofan Architectures and Fan Pressure Ratio Selection]])
★ **LP-spool balance**:

$$
c_p(T_{045}-T_{05}) = (1+BPR)c_p(T_{013}-T_{02})\ (+\text{LPC work})
$$

The best $\eta_P$ for given core power comes when the jets are matched ($V_{jc}\approx V_{jh}$). A higher BPR means a lower fpr, a higher $\eta_P$ and a lower TSFC.

## W8 Turbomachinery principles ([[SESA2023 W08 - Turbomachinery Principles - Euler Equation and Velocity Triangles]])

$$
★\;\Delta h_0 = U_2V_{\theta2}-U_1V_{\theta1},\qquad ★\;W_\theta = V_\theta-U,\qquad \tan\alpha = \frac{V_\theta}{V_x},\qquad \tan\beta = \frac{V_\theta-U}{V_x}
$$

$$
★\;R = \frac{h_2-h_1}{h_3-h_1} = 1-\frac\phi2(\tan\alpha_1+\tan\alpha_2)\ (\text{repeating stage}),\qquad ★\;\text{de Haller: }W_2/W_1\gtrsim0.72
$$

## W9 Characteristics and similarity ([[SESA2023 W09 - Turbomachinery Characteristics - Coefficients, Similarity and Maps]])

$$
★\;\phi = \frac{V_x}U,\qquad ★\;\psi = \frac{\Delta h_0}{U^2},\qquad ★\;n_{stages}\ge\frac{\Delta h_{0,total}}{\psi_{max}U^2}\ (\text{round up; compressor }\psi\lesssim0.45\text{–}0.65,\text{ turbine }\psi\lesssim2.5)
$$

★ **Similarity**: keep $\dfrac{\dot m\sqrt{T_{01}}}{D^2p_{01}}$ and $\dfrac{ND}{\sqrt{T_{01}}}$ equal. Then $\dfrac{p_{02}}{p_{01}}$, $\eta$ and $\dfrac{\dot W}{\dot mc_pT_{01}}$ are equal too.

★ **Hydraulic**: $\dfrac{gH}{N^2D^2}$, $\dfrac{Q}{ND^3}$, $\dfrac{P}{\rho N^3D^5}$, with specific speed $N_s = \dfrac{\Omega Q^{1/2}}{(gH)^{3/4}}$.

★ **Actuator disk**: $V_{disk} = \tfrac12(V_\infty+V_j)$, $T = \rho AV_{disk}(V_j-V_\infty)$, advance ratio $J = V/(nD)$.

## W10–11 Rockets ([[SESA2023 W10 - Rocket Performance, Staging and Power Cycles]], [[SESA2023 W11 - Solid Propellants and Rocket Nozzle Design]])

$$
★\;I_{sp} = \frac{F}{\dot mg_0},\qquad ★\;c = \frac{F}{\dot m} = g_0I_{sp} = C^*C_F,\qquad ★\;C^* = \frac{p_cA_t}{\dot m},\qquad ★\;C_F = \frac{F}{p_cA_t}
$$

$$
★\;\Delta V = c\ln\frac{m_0}{m_{bo}},\qquad ★\;\lambda = e^{-\Delta V/c}-\delta,\qquad m_0 = \frac{m_{pl}}{\lambda},\qquad m_p = m_0(1-\lambda-\delta)
$$

For staging, stage $i$'s payload is $m_{0,i+1}$.
- ★ Ideal $C^* = \dfrac{\sqrt{\gamma RT_c}}{\gamma}\left(\dfrac{\gamma+1}{2}\right)^{\frac{\gamma+1}{2(\gamma-1)}}$.
- ★ $C_F = \sqrt{\dfrac{2\gamma^2}{\gamma-1}\left(\dfrac{2}{\gamma+1}\right)^{\frac{\gamma+1}{\gamma-1}}\left[1-\left(\dfrac{p_e}{p_c}\right)^{\frac{\gamma-1}{\gamma}}\right]}+\dfrac{(p_e-p_a)A_e}{p_cA_t}$.
- ★ Solid burning rate $r = ap_c^n$. Steady chamber pressure $p_c = (a\rho_pC^*A_b/A_t)^{1/(1-n)}$, which is stable only if $n<1$.
- ★ Ion thruster: $v = \sqrt{2qV_b/m_i}$, $\dot m = Im_i/q$, $F = \dot mv\cos\theta$.
- ★ Orbit: $V_{orb} = \sqrt{\mu/r}$, with $\mu_E = 3.986\times10^{14}$ m³ s⁻².

## Related
- [[SESA2023 Propulsion Hub]] · [[SESA2023 Past Paper Map]]
