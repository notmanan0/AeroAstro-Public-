---
title: "SESA1016 Problem Sheet 09 - Momentum and Energy Conservation Solutions"
module: "SESA1016 Thermofluids"
type: tutorial
stream: "Part B: Fluid Mechanics"
tags: [sesa1016, tutorial-solutions, momentum, energy, propulsion]
sheet: "Problem Sheet 09 - Momentum and Energy Conservation"
theory_notes: ["[[SESA1016 T12 - Conservation of Momentum]]", "[[SESA1016 T13 - Conservation of Energy and Propulsion]]"]
key_concepts: ["[[Control-volume Analysis Workflow]]", "[[Momentum Flux]]", "[[Steady-flow Energy Equation]]"]
status: complete
sources: ["02 - Sources/Tutorial Sheets/Problem Sheet 09 - Momentum and Energy Conservation.pdf"]
---

# SESA1016 Problem Sheet 09 - Momentum and Energy Conservation Solutions

> [!abstract] Sheet Info
> Eleven control-volume problems. The essential discipline is to draw the control surface, mark outward normals, retain pressure forces, and distinguish forces **on the fluid** from reactions **on the hardware**.

## Q9.1 Wake-survey drag

Per unit tunnel width, continuity between the upstream and downstream planes gives

$$VH=\frac V3d+V_o(H-d).$$

For $V=12\ \mathrm{m\,s^{-1}}$, $H=3$ m and $d=0.14$ m,

$$
\boxed{V_o=V\frac{H-d/3}{H-d}=12.39\ \mathrm{m\,s^{-1}}}.
$$

Along an outer streamline,

$$p_1+\frac12\rho V^2=p_2+\frac12\rho V_o^2,$$

so, with $\rho=1.225\ \mathrm{kg\,m^{-3}}$,

$$\boxed{p_1-p_2=\tfrac12\rho(V_o^2-V^2)=5.85\ \mathrm{Pa}}.$$

The streamwise momentum equation per unit span is

$$
(p_1-p_2)H-D'
=\rho\left[\frac V3\left(\frac V3d\right)+V_o(V_o(H-d))-V(VH)\right].
$$

Solving,

$$\boxed{D'=6.04\ \mathrm{N\,m^{-1}}}.$$

Using chord $c=0.8$ m,

$$
\boxed{C_D=\frac{D'}{\tfrac12\rho V^2c}=0.0856}.
$$

## Q9.2 Model-rocket thrust

Pressure thrust vanishes because the jet pressure is atmospheric. The mass flow is

$$
\dot m=\rho AV
=0.5\frac{\pi(0.01)^2}{4}(450)
=0.01767\ \mathrm{kg\,s^{-1}}.
$$

Thus

$$\boxed{T=\dot mV=7.95\ \mathrm N}.$$

The support experiences an equal and opposite horizontal force.

## Q9.3 Impinging jet with a central orifice

The portion passing through the orifice retains its axial momentum. The remaining flow is turned radially and leaves with zero net axial momentum. Therefore

$$
F=\rho V^2(A_D-A_d)
=\rho V^2\frac\pi4(D^2-d^2).
$$

With $V=90\ \mathrm{m\,s^{-1}}$, $D=0.10$ m and $d=0.035$ m,

$$\boxed{F=55.8\ \mathrm{kN}}.$$

## Q9.4 Clamshell thrust reverser

Normal thrust is

$$
T=\dot m(V_o-V_i)
=68(425-90)
=\boxed{22.8\ \mathrm{kN}}.
$$

When deployed, the exhaust axial component is reversed. Because the vanes are $20^\circ$ from vertical,

$$V_{o,x}=-V_o\sin20^\circ.$$

The braking-force magnitude is

$$
T_r=\dot m(V_i+V_o\sin20^\circ)
=\boxed{16.0\ \mathrm{kN}}.
$$

## Q9.5 Pipe bend and nozzle

Continuity gives the inlet speed

$$
V_1=V_2\left(\frac{D_2}{D_1}\right)^2
=12\left(\frac{0.03}{0.10}\right)^2
=1.08\ \mathrm{m\,s^{-1}}.
$$

Bernoulli to the atmospheric jet gives

$$
p_{1,g}=\frac12\rho(V_2^2-V_1^2)=71.4\ \mathrm{kPa}.
$$

The mass flow is

$$\dot m=\rho A_2V_2=8.48\ \mathrm{kg\,s^{-1}}.$$

Applying vector momentum balance to the fluid and then reversing the fluid-on-bend force gives the bolt reactions required to hold the bend:

$$
\boxed{F_x=570\ \mathrm N\ \text{left}},
\qquad
\boxed{F_y=101.8\ \mathrm N\ \text{down}}.
$$

> [!warning] Pressure convention
> Use gauge pressure when the outlet and the exterior of the bend are both exposed to atmosphere; otherwise atmospheric forces are counted inconsistently.

## Q9.6 Jet impinging on a cone

At inlet,

$$A_i=\frac{\pi(0.25)^2}{4}=0.0491\ \mathrm{m^2},\qquad
\dot m=\rho A_iV_i=1000\times0.0491\times10=490.9\ \mathrm{kg\,s^{-1}}.$$

The water leaves as an axisymmetric sheet along the $45^\circ$ faces of the cone. The whole flow is at atmospheric pressure, so there is no pressure force, and symmetry cancels the transverse momentum. The axial momentum balance on a control volume round the cone and its sheet gives the force on the fluid, and the cone must be held with the opposite force:

$$
F=\dot m\left(V_i-V_o\cos45^\circ\right).
$$

Bernoulli is not to be used for $V_o$ (the impinging flow is viscous), so $V_o$ comes from continuity through the sheet, $V_o=\dot m/(\rho A_o)$, and the answer depends on how the sheet area $A_o$ is taken:

- thin sheet at the cone edge, $A_o=\pi D_{cone}t=\pi\times0.40\times0.04=0.0503$ m²: $V_o=9.77$ m/s and $F=1.52$ kN;
- annular frustum strip of thickness $t$ normal to the $45^\circ$ face, $A_o=\pi(2\times0.20+t\cos45^\circ)t=0.0538$ m²: $V_o=9.12$ m/s and $F=1.74$ kN.

$$\boxed{F\approx1.5\text{--}1.7\ \mathrm{kN}}$$

holding the cone against the jet.

> [!warning] Printed answer not reproduced (re-checked in Python, 2026-11-05)
> The sheet prints 1616.67 N. It lies between the two area conventions above but neither reproduces it, and no other reading of the 4 cm thickness tried (horizontal thickness, outer annulus $\pi(r_2^2-r_1^2)$, unchanged speed $V_o=V_i$, which gives 1.44 kN) gives it exactly. Quote 1.5–1.7 kN with the area assumption stated. The earlier version of this answer gave 1.62 kN by an unstated "annular-area convention".

## Q9.7 Air-water heat exchanger

Water volume flow $2$ L/s corresponds to

$$\dot m_w\approx1000(0.002)=2.0\ \mathrm{kg\,s^{-1}}.$$

The heat released by water cooling through $20$ K is

$$
|\dot Q|=\dot m_wc_w(20)
=2(4200)(20)=168\ \mathrm{kW}.
$$

The air gains this heat while warming from $18^\circ$C to $46^\circ$C:

$$
\dot m_a=\frac{168\,000}{1005(46-18)}
=\boxed{5.97\ \mathrm{kg\,s^{-1}}}.
$$

> [!note] Source correction
> The worked sheet prints $5.97\ \mathrm{m^3\,s^{-1}}$, but the equation calculates a **mass** flow rate; the correct unit is $\mathrm{kg\,s^{-1}}$.

## Q9.8 Heater with pressure rise

Ideal-gas densities and continuity give

$$
\frac{V_1}{V_2}
=\frac{\rho_2A_2}{\rho_1A_1}
=\frac{p_2/T_2}{p_1/T_1}(10)=25.
$$

The SFEE per unit mass, with no shaft work or potential-energy change, is

$$q=c_p(T_2-T_1)+\frac{V_2^2-V_1^2}{2}.$$

Substituting $q=275$ kJ/kg, $c_p\approx1005$ J/(kg K), $T_2-T_1=300$ K and $V_1=25V_2$ yields

$$
\boxed{V_1=229.75\ \mathrm{m\,s^{-1}}},
\qquad
\boxed{V_2=9.19\ \mathrm{m\,s^{-1}}}.
$$

The strong pressure and area change makes the outlet much slower despite heat addition.

> [!note] Sensitivity to $c_p$ (re-checked in Python, 2026-11-05)
> The answer comes from the small difference $q-c_p\Delta T=275\,000-301\,350=-26\,350$ J/kg (the air is slowed down: some enthalpy rise is paid for by kinetic energy). The printed values use $c_p=\gamma R/(\gamma-1)=1004.5$ J/(kg K). With $c_p=1005$ J/(kg K) the difference becomes $-26\,500$ J/kg and $V_2=9.22$ m/s, $V_1=230.4$ m/s.

## Q9.9 Hair dryer

At $p=1$ bar, ideal-gas density gives

$$
\rho_1=\frac{10^5}{287(291.15)}=\boxed{1.197\ \mathrm{kg\,m^{-3}}},
$$

$$
\rho_2=\frac{10^5}{287(323.15)}=\boxed{1.078\ \mathrm{kg\,m^{-3}}}.
$$

The enthalpy rise is

$$\Delta h=c_p(50-18)=\boxed{32\,144\ \mathrm{J\,kg^{-1}}}.$$

Neglecting kinetic energy initially, the $700$ W motor-plus-heater input gives

$$
\dot m=\frac{700}{32\,144}=\boxed{0.0218\ \mathrm{kg\,s^{-1}}}.
$$

With outlet area $A_2=\pi(0.03)^2/4$,

$$\boxed{V_2=\frac{\dot m}{\rho_2A_2}=28.57\ \mathrm{m\,s^{-1}}}.$$

Retaining outlet kinetic energy,

$$
700=\dot m\left[\Delta h+\frac12
\left(\frac{\dot m}{\rho_2A_2}\right)^2\right].
$$

Solving gives $\boxed{\dot m=0.0215\ \mathrm{kg\,s^{-1}}}$. The change is below $2\%$, so the first engineering approximation is reasonable.

## Q9.10 Industrial gas turbine

At compressor exit, $p_2=12.56$ bar, $T_2=668.15$ K:

$$\rho_2=\frac{p_2}{RT_2}=6.55\ \mathrm{kg\,m^{-3}},\qquad
\boxed{V_2=\frac{316}{\rho_2(0.4)}=120.6\ \mathrm{m\,s^{-1}}}.$$

Compressor (adiabatic, inlet KE negligible, exit KE kept). With $\dot W_x$ positive when done **by** the fluid,

$$
\dot W_x=-\dot m\left[c_p(T_2-T_1)+\frac{V_2^2}{2}\right].
$$

Combustor (no work; inlet KE $V_2^2/2=7273$ J/kg kept, exit KE neglected as instructed):

$$
\dot Q_{in}=\dot m\left[c_p(T_3-T_2)-\frac{V_2^2}{2}\right].
$$

Turbine (KE negligible at both ends): $\dot W_t=\dot mc_p(T_3-T_4)$.

The printed answers are reproduced with $c_p=1010$ J/(kg K), a mean value for air over 288–1435 K:

$$
\boxed{\dot W_x=-123.6\ \mathrm{MW}},\qquad
\boxed{\dot Q_{in}=242.5\ \mathrm{MW}},\qquad
\boxed{\dot W_t=204.3\ \mathrm{MW}},
$$

$$
\boxed{\dot W_{electric}=\dot W_t-|\dot W_x|=80.7\ \mathrm{MW}},\qquad
\boxed{\eta=\frac{80.7}{242.5}=33.3\%}.
$$

With $c_p=1005$ J/(kg K) the same method gives $-123.0$, $241.3$, $203.3$ and $80.3$ MW and $33.3\%$. Check on the whole plant: $\dot Q_{in}-\dot W_{electric}=161.8$ MW must equal the exhaust enthalpy excess $\dot mc_p(T_4-T_1)=316\times1010\times507=161.8$ MW.

> [!note] Correction (2026-11-05)
> The earlier version quoted the printed numbers but its formulas, with the module's usual $c_p=1005$ J/(kg K), give the slightly different values above; it also omitted the inlet kinetic energy in the combustor balance. The printed answers use $c_p=1010$ J/(kg K) and keep $V_2^2/2$ at combustor entry, as set out here.

## Q9.11 Isentropic propulsion nozzle

Take air properties $\gamma=1.4$, $R=287\ \mathrm{J\,kg^{-1}K^{-1}}$ and $c_p=1004.5\ \mathrm{J\,kg^{-1}K^{-1}}$. Isentropic expansion from $p_1=1.4$ bar, $T_1=1300$ K to $p_2=1.0$ bar gives

$$
T_2=T_1\left(\frac{p_2}{p_1}\right)^{(\gamma-1)/\gamma}
=1180.8\ \mathrm K.
$$

Use continuity and the adiabatic SFEE together:

$$\rho_1A_1V_1=\rho_2A_2V_2,$$

$$c_pT_1+\frac{V_1^2}{2}=c_pT_2+\frac{V_2^2}{2}.$$

With $D_1=0.8$ m and $D_2=0.2$ m, the simultaneous solution is

$$V_1=24.1\ \mathrm{m\,s^{-1}},\qquad
V_2=489.9\ \mathrm{m\,s^{-1}},$$

$$\boxed{\dot m=\rho_2A_2V_2=4.541\ \mathrm{kg\,s^{-1}}}.$$

Finally,

$$
\boxed{Ma_2=\frac{V_2}{\sqrt{\gamma RT_2}}=0.711}.
$$

## Related

- [[SESA1016 T12 - Conservation of Momentum]]
- [[SESA1016 T13 - Conservation of Energy and Propulsion]]
- [[Control-volume Analysis Workflow]]
- [[Momentum Flux]]
- [[Steady-flow Energy Equation]]

