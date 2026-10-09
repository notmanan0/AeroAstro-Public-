---
title: "SESA2023 Problem Sheet 9 Solutions"
module: "SESA2023 Propulsion"
type: tutorial
stream: "Section 4: Turbomachinery and Propellers"
tags:
  - sesa2023
  - tutorial-solutions
  - turbomachinery
  - dimensional-analysis
sheet: "Exercises Week 9 (turbomachinery characteristics)"
theory_notes: ["[[SESA2023 W09 - Turbomachinery Characteristics - Coefficients, Similarity and Maps]]", "[[SESA2023 W08 - Turbomachinery Principles - Euler Equation and Velocity Triangles]]"]
key_concepts: ["[[Flow and Work Coefficients]]", "[[Dimensional Analysis of Turbomachines]]", "[[Compressor and Turbine Characteristics]]", "[[Critical Conditions and Choked Flow]]"]
status: complete
sources: ["02 - Sources/Tutorial Sheets/Problem Sheet Week 09.pdf"]
---

# SESA2023 Problem Sheet 9 Solutions

> [!abstract] Sheet Info
> The sheet has five questions:
> - HPC exit annulus sizing and stage count from a stage-loading limit;
> - dimensional analysis of streamline patterns;
> - scaling a hydraulic turbine;
> - testing a compressor at reduced inlet pressure;
> - why throttling a choked steam turbine keeps its volume flow constant.
>
> All printed answers are reproduced ✔. One small difference is flagged in 9.1(a). Cold air throughout: $c_p = 1005$, $R = 287$, $\gamma = 1.4$.

## Theory Links
- [[SESA2023 W09 - Turbomachinery Characteristics - Coefficients, Similarity and Maps]]
- [[Flow and Work Coefficients]] · [[Dimensional Analysis of Turbomachines]] · [[Compressor and Turbine Characteristics]] · [[Critical Conditions and Choked Flow]]

---

## Q9.1: HP compressor exit annulus and stage count

### (a) Exit state, area and blade height
Data: $T_{023} = 327$ K, $p_{023} = 89.1$ kPa, $\dot m = 32.1$ kg/s, $r_p = 18$, $\eta_c = 0.90$, $V_x = 171$ m/s (purely axial at exit), $r_m = 0.267$ m.

**Compressor exit stagnation state**:

$$
T_{03} = T_{023}\left[1+\frac{r_p^{(\gamma-1)/\gamma}-1}{\eta_c}\right] = 327\left[1+\frac{18^{0.2857}-1}{0.9}\right] = 327(2.4264) = 793.4\text{ K},\qquad p_{03} = 18(89.1) = 1603.8\text{ kPa}
$$

**Static state**: the exit flow is purely axial, so $V = V_x$.

$$
T_3 = T_{03}-\frac{V_x^2}{2c_p} = 793.4-\frac{171^2}{2010} = \boxed{778.9\text{ K}}\;✔
$$

$$
p_3 = p_{03}\left(\frac{T_3}{T_{03}}\right)^{3.5} = \boxed{1.503\times10^3\text{ kPa}}\;✔,\qquad \rho_3 = \frac{p_3}{RT_3} = \boxed{6.72\text{ kg/m}^3}\;✔
$$

**Annulus area and blade height**, using $A = 2\pi r_mh$:

$$
A = \frac{\dot m}{\rho_3V_x} = \frac{32.1}{6.72(171)} = \boxed{0.0279\text{ m}^2}\;✔,\qquad h = \frac{A}{2\pi r_m} = \frac{0.0279}{2\pi(0.267)} = \boxed{16.6\text{ mm}}
$$

> [!note] Blade height against the printed answer
> The printed answer is $h = 16.70$ mm. Unrounded working gives $A = 0.027915$ m² and $h = 16.64$ mm. The 0.4 % difference is intermediate rounding in the official solution; either value earns the marks. A 17 mm last-stage blade is very short, which is why HPC tip-clearance losses matter so much in high-OPR engines.

### (b) Minimum number of stages for $\psi\le0.45$
Blade speed at the mean radius:

$$
U = 2\pi r_mN = 2\pi(0.267)(185.6) = 311.4\text{ m/s}
$$

The total work is $\Delta h_0 = c_p(T_{03}-T_{023}) = 1005(793.4-327) = 468.8$ kJ/kg, shared between $n$ equal stages, each with $\Delta h_{0,stage} = \psi U^2$:

$$
n\ge\frac{\Delta h_0}{\psi_{max}U^2} = \frac{468\,763}{0.45(311.4)^2} = 10.74\;\Rightarrow\;\boxed{n = 11\text{ stages}}\;✔
$$

$$
\psi = \frac{468\,763}{11(311.4)^2} = \boxed{0.439}\;✔
$$

The number of stages must be rounded **up**, so the stages actually run a little below the loading limit. This is a direct use of [[Flow and Work Coefficients]].

## Q9.2: Variables that fix the streamline pattern (inviscid, incompressible)

In inviscid incompressible flow there is no Reynolds number (no $\mu$) and no Mach number (no $a$). Only **geometry** and the **direction** of the flow relative to the geometry are left.

### (a) Geometrically similar aerofoils in a wind tunnel
- **Variables**: the size $c$ (with the shape fixed by geometric similarity), the free-stream speed $V$, the density $\rho$ and the angle of attack $\alpha$.
- **Dimensionless groups**: $V$, $\rho$ and $c$ cannot be combined into any dimensionless group, so they only scale the pattern. The single controlling group is $\alpha$, which is already dimensionless (plus the fixed shape ratios such as $t/c$).
- **Conclusion**: the streamline pattern is a function of $\alpha$ only. The dependent groups $C_L$, $C_D$, $C_M$ and $C_p(x/c)$ are unique functions of $\alpha$.

### (b) Geometrically similar turbomachines
- **Variables**: the size $D$, the rotational speed $N$, the volume flow rate $Q$ and the density $\rho$.
- **Dimensionless groups**: the angle between the approaching flow and the blades depends on the ratio of through-flow velocity to blade speed. That ratio is the one group:

$$
\phi\propto\frac{Q}{ND^3}\quad(\text{equivalently }V_x/U)
$$

- **Conclusion**: fixing $\phi$ fixes all the velocity-triangle angles, so every other group is a unique function of it: $\dfrac{gH}{N^2D^2}$ (ψ), $\dfrac{P}{\rho N^3D^5}$ and $\eta$.

Real machines add $Re = \rho ND^2/\mu$ (a weak effect at high $Re$) and, for compressible flow, a Mach-number group $ND/\sqrt{\gamma RT_{01}}$. See [[Dimensional Analysis of Turbomachines]].

## Q9.3: Hydraulic turbine scaled from a 1/10 model
The model has $H_m = 10$ m, $N_m = 3000$ rpm, $Q_m = 1.1$ m³/s and $\eta = 0.91$ at its best-efficiency point. The prototype has $D_p = 10D_m$ and $H_p = 100$ m.

Equal efficiency means the same operating point, so all the groups match (ignoring viscosity and cavitation):

$$
\frac{gH}{N^2D^2}\text{ equal:}\quad N_p = N_m\frac{D_m}{D_p}\sqrt{\frac{H_p}{H_m}} = 3000\left(\frac1{10}\right)\sqrt{10} = \boxed{948.7\text{ rpm}}\;✔
$$

$$
\frac{Q}{ND^3}\text{ equal:}\quad Q_p = Q_m\frac{N_p}{N_m}\left(\frac{D_p}{D_m}\right)^3 = 1.1(0.3162)(1000) = \boxed{347.8\text{ m}^3/\text{s}}\;✔
$$

$$
P_p = \eta\rho gQ_pH_p = 0.91(1000)(9.81)(347.8)(100) = \boxed{310.5\text{ MW}}\;✔
$$

## Q9.4: Compressor tested with a throttled inlet
The design point is $p_{01} = 1$ bar, $T_{01} = 300$ K, 4000 rpm and a pressure ratio of 10. On test, the exhaust goes to atmosphere (1 bar), so at the same pressure ratio of 10 the inlet is throttled to $p_{01} = 0.1$ bar. The test inlet temperature is $T_{01} = 280$ K.

**Same non-dimensional speed** $N/\sqrt{T_{01}}$:

$$
N_{test} = 4000\sqrt{\frac{280}{300}} = \boxed{3864\text{ rpm}}\;✔
$$

**Same non-dimensional flow** $\dot m\sqrt{T_{01}}/p_{01}$:

$$
\dot m_{des} = \dot m_{test}\frac{p_{01,des}}{p_{01,test}}\sqrt{\frac{T_{01,test}}{T_{01,des}}} = 5(10)\sqrt{\frac{280}{300}} = \boxed{48.3\text{ kg/s}}\;✔
$$

**Same non-dimensional power** $\dot W/(\dot mc_pT_{01})$, which is the same as the same $\Delta T_0/T_{01}$:

$$
\dot W_{des} = 1.5\text{ MW}\times\frac{48.3}{5}\times\frac{300}{280} = \boxed{15.5\text{ MW}}\;✔
$$

Throttling the inlet cuts the test power by about 10×. That is the whole point of the arrangement: the aerodynamics are identical, but the rig needs only about 1.5 MW.

## Q9.5: Throttle control of a choked steam turbine
**Mass flow proportional to throttle pressure.** A turbine with a very high pressure ratio sits on the vertical (choked) part of its characteristic. There, the non-dimensional mass flow is fixed at the choking value:

$$
\frac{\dot m\sqrt{c_pT_{0}}}{Ap_0} = \text{const}\quad\text{(the choked flow function, see [[Critical Conditions and Choked Flow]])}
$$

An adiabatic throttle does no work and transfers no heat, so the SFEE gives $h_0$ = const. For a perfect gas that means **$T_0$ = const** across the throttle; only $p_0$ falls. With $A$ and $T_0$ fixed:

$$
\boxed{\dot m\propto p_0}\quad\text{(the pressure after the throttle)}
$$

**Volume flow constant.** The inlet volume flow rate, based on stagnation density $\rho_0 = p_0/RT_0$, is:

$$
Q = \frac{\dot m}{\rho_0} = \frac{\dot m RT_0}{p_0}\propto\frac{p_0}{p_0}T_0 = \text{const}
$$

So the volume flow stays constant however far the valve is closed. The velocity triangles at turbine entry are therefore unchanged, and the turbine keeps its design incidence even at part load. (The cost is the entropy produced in the throttle, which is why sliding-pressure control is often preferred.)

## Sources
- `02 - Sources/Tutorial Sheets/Problem Sheet Week 09.pdf`. All numbers are reproduced in `04 - Scripts/verify_tutorials.py`.
