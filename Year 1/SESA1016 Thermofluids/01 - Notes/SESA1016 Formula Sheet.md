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

Every result below holds only inside its assumptions, so start each calculation by deciding whether the analysis is a closed system or a control volume, and which of steady, ideal gas, incompressible, inviscid, adiabatic and uniform (one-dimensional) apply. Symbols follow the course: $v$ is specific volume in thermodynamics and $v_x$ a velocity component in fluids, $\mathcal V$ is volume and $\dot{\mathcal V}$ volume flow rate, $\bar V$ the area-averaged velocity, $c$ the speed of sound. Temperatures in gas-law, entropy and efficiency formulae are in kelvin and pressures absolute.

## 1. Properties and the ideal gas

From [[SESA1016 T1 - Thermodynamic Systems, Properties and State|T1]] and [[SESA1016 T2 - Work, Heat and the First Law|T2]].

$$
\rho=\frac m{\mathcal V},\qquad v=\frac1\rho,\qquad pV=mRT,\qquad pv=RT,\qquad p=\rho RT,\qquad R=\frac{R_u}M
$$

$R_u=8.3145$ J mol⁻¹ K⁻¹; for air $R=287$ J kg⁻¹ K⁻¹, $\gamma=1.4$, $c_v=718$ and $c_p=1005$ J kg⁻¹ K⁻¹. For a fixed mass, $p_1V_1/T_1=p_2V_2/T_2$.

$$
\Delta u=c_v\Delta T,\qquad \Delta h=c_p\Delta T,\qquad h=u+pv,\qquad c_p-c_v=R,\qquad \gamma=\frac{c_p}{c_v},\qquad c_v=\frac R{\gamma-1}
$$

## 2. First law for a closed system and boundary work

Heat into the system and work done by the system are positive ([[SESA1016 T2 - Work, Heat and the First Law#1. The first law for a closed system|T2 §1]]).

$$
\boxed{\Delta U=Q-W},\qquad W=\int_{V_1}^{V_2}p\,dV
$$

| Process (ideal gas) | Work $W$ | Heat $Q$ |
|---|---|---|
| Constant volume | $0$ | $mc_v\Delta T$ |
| Constant pressure | $p(V_2-V_1)=mR\Delta T$ | $mc_p\Delta T$ |
| Isothermal | $mRT\ln(V_2/V_1)$ | $=W$ |
| Reversible adiabatic | $(p_1V_1-p_2V_2)/(\gamma-1)=mc_v(T_1-T_2)$ | $0$ |

![[tf_processes_pv.png|720]]

## 3. Cycles, the second law and entropy

From [[SESA1016 T3 - Heat Engines and the Second Law|T3]] and [[SESA1016 T4 - Entropy and Isentropic Relations|T4]]. Over a cycle $\Delta U=0$:

$$
W_{net}=Q_{in}-Q_{out},\qquad \eta_{th}=\frac{W_{net}}{Q_{in}}=1-\frac{Q_{out}}{Q_{in}},\qquad COP_{HP}=\frac{Q_H}{W_{in}}=COP_R+1
$$

$$
dS=\frac{dQ}T+dS_{gen},\quad dS_{gen}\ge0,\qquad S_{gen}=Q\left(\frac1{T_C}-\frac1{T_H}\right)\ \text{(heat $Q$ from $T_H$ to $T_C$)}
$$

$$
T\,ds=du+p\,dv=dh-v\,dp
$$

$$
s_2-s_1=c_v\ln\frac{T_2}{T_1}+R\ln\frac{v_2}{v_1}=c_p\ln\frac{T_2}{T_1}-R\ln\frac{p_2}{p_1}
$$

Isentropic (reversible adiabatic) ideal gas, constant $\gamma$:

$$
\frac{T_2}{T_1}=\left(\frac{v_1}{v_2}\right)^{\gamma-1}=\left(\frac{p_2}{p_1}\right)^{(\gamma-1)/\gamma},\qquad \frac{p_2}{p_1}=\left(\frac{v_1}{v_2}\right)^\gamma
$$

## 4. Ideal cycles

From [[SESA1016 T5 - Ideal Heat Engine Models|T5]], with compression ratio $r=v_1/v_2$, cut-off ratio $r_c=v_3/v_2$ and pressure ratio $r_p=p_2/p_1$:

$$
\eta_{Carnot}=1-\frac{T_C}{T_H},\qquad \eta_{Otto}=1-\frac1{r^{\gamma-1}},\qquad \eta_{Diesel}=1-\frac1{r^{\gamma-1}}\left[\frac{r_c^\gamma-1}{\gamma(r_c-1)}\right],\qquad \eta_{Brayton}=1-\frac1{r_p^{(\gamma-1)/\gamma}}
$$

Brayton pressure ratio for maximum net work per kilogram, with $T_1$ the compressor inlet and $T_3$ the turbine inlet temperature:

$$
r_{p,opt}=\left(\frac{T_3}{T_1}\right)^{\gamma/(2(\gamma-1))}
$$

![[tf_ideal_cycles_pv.png|720]]

## 5. Dimensional analysis

From [[SESA1016 T6 - Dimensional Analysis and Similarity|T6]]: $n$ variables with $k$ independent dimensions form $n-k$ independent groups, $\Pi_1=F(\Pi_2,\ldots,\Pi_{n-k})$.

$$
Re=\frac{\rho Vd}\mu=\frac{Vd}\nu,\quad Fr=\frac V{\sqrt{gd}},\quad Ma=\frac Vc,\quad We=\frac{\rho V^2d}\sigma,\quad St=\frac{fd}V,\quad C_D=\frac D{\tfrac12\rho V^2A},\quad C_L=\frac L{\tfrac12\rho V^2A}
$$

Similarity between model and full scale needs every relevant group matched, not only the geometry. Creeping flow round a sphere: $C_D=24/Re$.

## 6. Fluid properties

From [[SESA1016 T7 - Fluid Properties and Viscosity|T7]].

$$
\tau=\mu\frac{dv}{dy},\qquad F=\mu\frac{AV}h\ \text{(Couette)},\qquad \nu=\frac\mu\rho,\qquad E_v=-\frac{\Delta p}{\Delta\mathcal V/\mathcal V},\qquad c=\sqrt{\frac{E_v}\rho},\qquad c=\sqrt{\gamma RT}\ \text{(ideal gas)}
$$

Sutherland's law for air ($S=111$ K, $\mu_0=1.825\times10^{-5}$ Pa s at $T_0=293.15$ K):

$$
\mu=\mu_0\left(\frac T{T_0}\right)^{3/2}\frac{T_0+S}{T+S}
$$

## 7. Hydrostatics and the atmosphere

From [[SESA1016 T8 - Hydrostatics|T8]], $z$ positive upwards:

$$
\frac{dp}{dz}=-\rho g,\qquad p=p_0-\rho gz\ \text{(liquid)},\qquad p_{abs}=p_{gauge}+p_{atm},\qquad F_2=F_1\frac{A_2}{A_1}\ \text{(jack)},\qquad U=\rho g\mathcal V\ \text{(upthrust)}
$$

Through a manometer, going down by $h$ in a fluid adds $\rho gh$ and going up subtracts it.

$$
\frac p{p_0}=\exp\left(-\frac{gz}{RT_0}\right)\ \text{(isothermal)},\qquad \frac p{p_0}=\left(\frac{T_0-\Gamma_ez}{T_0}\right)^{g/(\Gamma_eR)}\ \text{(constant lapse rate, ISA }\Gamma_e=6.5\text{ K/km)}
$$

## 8. Flow kinematics, Euler and Bernoulli

From [[SESA1016 T9 - Describing Flow and the Material Derivative|T9]] and [[SESA1016 T10 - Euler and Bernoulli Equations|T10]].

$$
\frac{DT}{Dt}=\frac{\partial T}{\partial t}+v_x\frac{\partial T}{\partial x}+v_y\frac{\partial T}{\partial y}+v_z\frac{\partial T}{\partial z},\qquad \frac{dy}{dx}=\frac{v_y}{v_x}\ \text{(streamline)}
$$

$$
\vec a=\left(V\frac{\partial V}{\partial s}+\frac{\partial V}{\partial t}\right)\vec u_t+\frac{V^2}r\vec u_n,\qquad \rho a_l=-\frac{\partial p}{\partial l}\ \text{(Euler, no gravity, any direction }l)
$$

Steady, incompressible, inviscid, along a streamline (constant everywhere if the upstream flow is uniform):

$$
\boxed{p+\tfrac12\rho V^2+\rho gz=\text{const}},\qquad \frac p{\rho g}+\frac{V^2}{2g}+z=H
$$

$$
p_0=p+\tfrac12\rho V^2,\qquad V=\sqrt{\frac{2(p_0-p)}\rho},\qquad C_p=\frac{p-p_\infty}{\tfrac12\rho V_\infty^2}=1-\left(\frac V{V_\infty}\right)^2,\qquad C_{p,cylinder}=1-4\sin^2\beta
$$

## 9. Conservation of mass

From [[SESA1016 T11 - Conservation of Mass|T11]].

$$
\dot{\mathcal V}=\int_A\vec V\cdot\vec n\,dA=\bar VA,\qquad \dot m=\int_A\rho\,\vec V\cdot\vec n\,dA=\rho\bar VA\ \text{(constant }\rho)
$$

$$
0=\frac d{dt}\int_{CV}\rho\,d\mathcal V+\int_{CS}\rho\,\vec V\cdot\vec n\,dA,\qquad \text{steady: }\sum\dot m_{out}=\sum\dot m_{in},\qquad \rho_1V_1A_1=\rho_2V_2A_2
$$

## 10. Conservation of momentum

From [[SESA1016 T12 - Conservation of Momentum|T12]]; forces are those on the fluid in the control volume (pressure, walls and supports, weight), and the force on the hardware is the reaction.

$$
\dot{\vec M}=\int_A\rho\vec V(\vec V\cdot\vec n)\,dA,\qquad \sum\vec F=\frac d{dt}\int_{CV}\rho\vec V\,d\mathcal V+\int_{CS}\rho\vec V(\vec V\cdot\vec n)\,dA
$$

$$
\boxed{\sum\vec F=\dot m\left(\vec V_{out}-\vec V_{in}\right)}\ \text{(steady, one inlet, one outlet, uniform)}
$$

## 11. Conservation of energy and propulsion

From [[SESA1016 T13 - Conservation of Energy and Propulsion|T13]]; $\dot Q$ into the fluid and shaft work $\dot W_x$ done by the fluid are positive.

$$
h_{tot}=h+\tfrac12V^2+gz,\qquad \boxed{\dot Q-\dot W_x=\dot m\left(h_{tot,out}-h_{tot,in}\right)}
$$

Adiabatic nozzle: $h_1+\tfrac12V_1^2=h_2+\tfrac12V_2^2$. Adiabatic turbine or compressor with small $\Delta V$: $\dot W_x=\dot mc_p(T_{in}-T_{out})$.

$$
T=\dot m_{air}(V_j-V_\infty),\qquad \eta_p=\frac{TV_\infty}{\dot Q}=\frac{(V_j-V_\infty)V_\infty}{c_p(T_j-T_\infty)+\tfrac12\left(V_j^2-V_\infty^2\right)}
$$

## 12. Boundary layers and drag

From [[SESA1016 T14 - Boundary Layers and the Origin of Drag|T14]].

$$
\delta^*=\int_0^\infty\left(1-\frac{v_x}{V_\infty}\right)dy,\qquad \theta=\int_0^\infty\frac{v_x}{V_\infty}\left(1-\frac{v_x}{V_\infty}\right)dy,\qquad H=\frac{\delta^*}\theta
$$

$$
\tau_w=\mu\left.\frac{\partial v_x}{\partial y}\right|_{y=0},\qquad c_f=\frac{\tau_w}{\tfrac12\rho V_\infty^2},\qquad D=2\rho V_\infty^2\theta\ \text{(plate, both sides, per unit width)}
$$

$$
Re_x=\frac{V_\infty x}\nu,\qquad \delta=5\sqrt{\frac{\nu x}{V_\infty}}=\frac{5x}{\sqrt{Re_x}}\ \text{(laminar)},\qquad Re_{x,tr}\approx5\times10^5
$$

$$
D=\int_A\left(-p\sin\theta+\tau\cos\theta\right)dA=D_p+D_v
$$

## 13. Flow in conduits

From [[SESA1016 T15 - Flow in Conduits|T15]]; laminar below $Re_D=2000$, turbulent above about 3000.

$$
Re_D=\frac{\bar VD}\nu,\qquad \frac{\partial p}{\partial x}=-\frac2R\tau_w,\qquad v_x(r)=V_{max}\left(1-\frac{r^2}{R^2}\right),\qquad \bar V=\tfrac12V_{max},\qquad \dot{\mathcal V}=\frac{\pi D^4}{128\mu}\frac{\Delta p}L
$$

$$
\Delta p=f\frac LD\tfrac12\rho\bar V^2,\qquad f=\frac{64}{Re_D}\ \text{(laminar)},\qquad \frac1{\sqrt f}+2\log_{10}\left(\frac\epsilon{3.7D}+\frac{2.51}{\sqrt f\,Re_D}\right)=0\ \text{(Colebrook)}
$$

$$
K=\frac{\Delta p}{\tfrac12\rho\bar V^2},\qquad \Delta p=\sum_{pipes}f\frac LD\tfrac12\rho\bar V^2+\sum_{components}K\tfrac12\rho\bar V^2,\qquad \dot W_p=\frac{\dot{\mathcal V}\Delta p}{\eta_p}
$$

In head form, between points 1 and 2 with a pump adding head $h_p$ and losses $h_L$: $\dfrac{p_1}{\rho g}+\dfrac{\bar V_1^2}{2g}+z_1+h_p=\dfrac{p_2}{\rho g}+\dfrac{\bar V_2^2}{2g}+z_2+h_L$.

![[tf_moody_chart.png|700]]

## Related

- [[SESA1016 Thermofluids Hub]] · [[SESA1016 Online Exam Question Map]]
