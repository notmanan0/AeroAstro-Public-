---
title: "SESA1016 Formula Sheet"
module: "SESA1016 Thermofluids"
type: formula
aliases: ["SESA1016 formulae", "Thermofluids formula sheet"]
tags: [sesa1016, formula, exam-prep]
status: complete
sources: ["02 - Sources/Lectures/Chapter 1.pdf", "02 - Sources/Lectures/Chapter 2.pdf", "02 - Sources/Lectures/Chapter 3.pdf", "02 - Sources/Lectures/Chapter 4.pdf", "02 - Sources/Lectures/Chapter 5.pdf", "02 - Sources/Lectures/Chapter 6.pdf", "02 - Sources/Lectures/Chapter 7.pdf", "02 - Sources/Lectures/Chapter 8.pdf", "02 - Sources/Lectures/Chapter 9.pdf", "02 - Sources/Lectures/Chapter 10.pdf", "02 - Sources/Lectures/Chapter 11.pdf", "02 - Sources/Lectures/Chapter 12.pdf", "02 - Sources/Lectures/Chapter 13.pdf", "02 - Sources/Lectures/Chapter 14.pdf", "02 - Sources/Lectures/Chapter 15.pdf"]
---

# SESA1016 Formula Sheet

> [!warning] Begin every calculation with the model
> State whether the analysis uses a **closed system** or **control volume**, then list steady/unsteady, ideal-gas, incompressible, inviscid, adiabatic and one-dimensional assumptions. An equation is only correct inside its assumptions.

## 1. Properties and ideal gases

$$
\rho=\frac{m}{V},\qquad v=\frac{V}{m}=\frac1\rho,\qquad pV=mRT,\qquad pv=RT
$$

$$
R=c_p-c_v,\qquad \gamma=\frac{c_p}{c_v},\qquad c_v=\frac{R}{\gamma-1},\qquad c_p=\frac{\gamma R}{\gamma-1}
$$

For a calorically perfect ideal gas:

$$
\Delta U=mc_v\Delta T,\qquad \Delta H=mc_p\Delta T,\qquad h=u+pv
$$

Temperatures in gas-law, entropy and efficiency relations must be in kelvin.

## 2. Closed-system first law and boundary work

Course sign convention: heat **into** the system is positive; work **done by** the system is positive.

$$
\boxed{\Delta U=Q-W},\qquad W_{1\to2}=\int_{V_1}^{V_2}p\,dV
$$

| Process | Constraint | Work per unit mass | Heat per unit mass |
|---|---|---|---|
| Constant volume | $v_2=v_1$ | $w=0$ | $q=c_v(T_2-T_1)$ |
| Constant pressure | $p_2=p_1$ | $w=p(v_2-v_1)=R\Delta T$ | $q=c_p\Delta T$ |
| Isothermal ideal gas | $T_2=T_1$ | $w=RT\ln(v_2/v_1)$ | $q=w$ |
| Reversible adiabatic | $q=0$ | $w=c_v(T_1-T_2)$ | $0$ |
| Polytropic | $pv^n=C$ | $w=(p_2v_2-p_1v_1)/(1-n)$ | $\Delta u+w$ |

Reversible adiabatic ideal gas:

$$
pv^\gamma=C,\qquad Tv^{\gamma-1}=C,\qquad T^\gamma p^{1-\gamma}=C
$$

$$
\frac{T_2}{T_1}=\left(\frac{v_1}{v_2}\right)^{\gamma-1}
=\left(\frac{p_2}{p_1}\right)^{(\gamma-1)/\gamma}
$$

![[tf_processes_pv.png|720]]

## 3. Heat engines, refrigerators and entropy

Over a cycle, $\Delta U_{cycle}=0$:

$$
W_{net,out}=Q_H-Q_C,\qquad \eta_{th}=\frac{W_{net,out}}{Q_H}=1-\frac{Q_C}{Q_H}
$$

$$
COP_R=\frac{Q_C}{W_{net,in}},\qquad COP_{HP}=\frac{Q_H}{W_{net,in}}=COP_R+1
$$

Carnot limits:

$$
\eta_C=1-\frac{T_C}{T_H},\qquad COP_{R,C}=\frac{T_C}{T_H-T_C},\qquad COP_{HP,C}=\frac{T_H}{T_H-T_C}
$$

Entropy balance for a closed system:

$$
\Delta S=\int\frac{\delta Q}{T_b}+S_{gen},\qquad S_{gen}\ge0
$$

Ideal-gas entropy change:

$$
s_2-s_1=c_v\ln\frac{T_2}{T_1}+R\ln\frac{v_2}{v_1}
=c_p\ln\frac{T_2}{T_1}-R\ln\frac{p_2}{p_1}
$$

## 4. Ideal cycles

Let $r=v_1/v_2$ be compression ratio, $r_c=v_3/v_2$ Diesel cut-off ratio and $r_p=p_2/p_1$ Brayton pressure ratio:

$$
\eta_{Otto}=1-\frac1{r^{\gamma-1}}
$$

$$
\eta_{Diesel}=1-\frac1{r^{\gamma-1}}\frac{r_c^\gamma-1}{\gamma(r_c-1)}
$$

$$
\eta_{Brayton}=1-\frac1{r_p^{(\gamma-1)/\gamma}}
$$

![[tf_ideal_cycles_pv.png|720]]

## 5. Dimensional analysis

If a phenomenon depends on $n$ dimensional variables built from $k$ independent base dimensions, Buckingham gives $n-k$ independent dimensionless groups:

$$
\Pi_1=F(\Pi_2,\ldots,\Pi_{n-k})
$$

Common groups:

$$
Re=\frac{\rho VL}{\mu}=\frac{VL}{\nu},\qquad Ma=\frac{V}{a},\qquad Fr=\frac{V}{\sqrt{gL}},\qquad St=\frac{fL}{V}
$$

$$
C_D=\frac{D}{\tfrac12\rho V^2A},\qquad C_L=\frac{L}{\tfrac12\rho V^2A},\qquad C_p=\frac{p-p_\infty}{\tfrac12\rho V_\infty^2}
$$

Model and prototype must match every dynamically important $\Pi$ group; geometric similarity alone is insufficient.

## 6. Fluid properties and hydrostatics

Newtonian fluid:

$$
\tau=\mu\frac{du}{dy},\qquad \nu=\frac\mu\rho,\qquad K=-V\frac{dp}{dV}=\rho\frac{dp}{d\rho}
$$

Hydrostatic balance, with $z$ positive upward:

$$
\frac{dp}{dz}=-\rho g,\qquad p_2-p_1=\rho g(z_1-z_2)
$$

$$
F_B=\rho_f gV_{disp},\qquad p_{abs}=p_{gauge}+p_{atm}
$$

Across a manometer: move **down** by $h$ and add $\rho gh$; move **up** and subtract it.

## 7. Flow description and acceleration

$$
\frac{D\phi}{Dt}=\frac{\partial\phi}{\partial t}+\mathbf V\cdot\nabla\phi
$$

$$
\mathbf a=\frac{D\mathbf V}{Dt}=\frac{\partial\mathbf V}{\partial t}+(\mathbf V\cdot\nabla)\mathbf V
$$

For steady one-dimensional flow along $s$: $a_s=V\,dV/ds$.

Speed of sound for an ideal gas:

$$
a=\sqrt{\gamma RT},\qquad Ma=\frac Va
$$

## 8. Euler and Bernoulli

Euler equation along a streamline:

$$
\rho V\,dV=-dp-\rho g\,dz
$$

For steady, incompressible, inviscid flow with no shaft work or losses:

$$
\boxed{p+\frac12\rho V^2+\rho gz=\mathrm{constant\ along\ a\ streamline}}
$$

Head form:

$$
\frac p{\rho g}+\frac{V^2}{2g}+z=H
$$

At a stagnation point at the same elevation:

$$
p_0=p+\frac12\rho V^2,\qquad V=\sqrt{\frac{2(p_0-p)}\rho}
$$

## 9. Mass conservation

$$
\dot V=\int_A\mathbf V\cdot\mathbf n\,dA=\bar V A,qquad
\dot m=\int_A\rho\mathbf V\cdot\mathbf n\,dA=\rho\bar V A
$$

General control-volume mass balance:

$$
\frac{d}{dt}\int_{CV}\rho\,dV+\int_{CS}\rho\mathbf V\cdot\mathbf n\,dA=0
$$

Steady, one-dimensional ports:

$$
\sum\dot m_{in}=\sum\dot m_{out}
$$

## 10. Momentum conservation

General inertial control-volume form:

$$
\sum\mathbf F=\frac{d}{dt}\int_{CV}\rho\mathbf V\,dV+
\int_{CS}\rho\mathbf V(\mathbf V\cdot\mathbf n)\,dA
$$

Steady, uniform ports:

$$
\boxed{\sum\mathbf F=\sum_{out}\dot m\mathbf V-\sum_{in}\dot m\mathbf V}
$$

Include pressure forces, weight and support/wall reactions. The force **on the hardware** is the negative of the force exerted by the hardware on the fluid.

Jet thrust with a single exit:

$$
F=\dot m(V_e-V_i)+(p_e-p_a)A_e
$$

## 11. Steady-flow energy equation

Define $e_t=h+V^2/2+gz$. For steady, one-dimensional ports:

$$
\boxed{\dot Q-\dot W_s=
\sum_{out}\dot m\left(h+\frac{V^2}{2}+gz\right)
-\sum_{in}\dot m\left(h+\frac{V^2}{2}+gz\right)}
$$

Single inlet and outlet per unit mass:

$$
q-w_s=(h_2-h_1)+\frac{V_2^2-V_1^2}{2}+g(z_2-z_1)
$$

Nozzle/diffuser, adiabatic and no shaft work:

$$
h_1+\frac{V_1^2}{2}=h_2+\frac{V_2^2}{2}
$$

## 12. Boundary layers and drag

$$
\delta^*=\int_0^\infty\left(1-\frac u{U_e}\right)dy,qquad
\theta=\int_0^\infty\frac u{U_e}\left(1-\frac u{U_e}\right)dy,qquad H=\frac{\delta^*}{\theta}
$$

$$
\tau_w=\mu\left.\frac{\partial u}{\partial y}\right|_0,qquad c_f=\frac{\tau_w}{\tfrac12\rho U_e^2}
$$

Zero-pressure-gradient momentum integral equation:

$$
c_f=2\frac{d\theta}{dx}
$$

Flat-plate estimates:

| Quantity | Laminar | Turbulent |
|---|---|---|
| $\delta/x$ | $4.91Re_x^{-1/2}$ | $0.38Re_x^{-1/5}$ |
| $\theta/x$ | $0.664Re_x^{-1/2}$ | $0.037Re_x^{-1/5}$ |
| local $c_f$ | $0.664Re_x^{-1/2}$ | $0.059Re_x^{-1/5}$ |
| mean $C_F$ | $1.328Re_L^{-1/2}$ | $0.074Re_L^{-1/5}$ |

$$
D=\frac12\rho V^2AC_D
$$

## 13. Flow in conduits

$$
Re_D=\frac{\rho\bar VD}{\mu},\qquad f=\frac{64}{Re_D}\quad\text{(fully developed laminar pipe flow)}
$$

Laminar circular-pipe profile:

$$
u(r)=2\bar V\left(1-\frac{r^2}{R^2}\right),\qquad u_{max}=2\bar V
$$

Darcy-Weisbach and minor losses:

$$
h_f=f\frac LD\frac{\bar V^2}{2g},\qquad h_m=K\frac{\bar V^2}{2g},\qquad
h_L=\left(f\frac LD+\sum K\right)\frac{\bar V^2}{2g}
$$

Colebrook relation for turbulent flow:

$$
\frac1{\sqrt f}=-2\log_{10}\left(\frac{\varepsilon/D}{3.7}+\frac{2.51}{Re_D\sqrt f}\right)
$$

Extended Bernoulli:

$$
\frac{p_1}{\rho g}+\frac{V_1^2}{2g}+z_1+h_p-h_t-h_L
=\frac{p_2}{\rho g}+\frac{V_2^2}{2g}+z_2
$$

$$
P_{fluid}=\rho g\dot Vh_p,\qquad P_{shaft}=\frac{P_{fluid}}{\eta_p}
$$

![[tf_moody_chart.png|700]]

## Related

- [[SESA1016 Thermofluids Hub]] · [[SESA1016 Online Exam Question Map]]
