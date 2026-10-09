---
title: "SESA1016 Problem Sheet 06 - Fluid Properties and Hydrostatics Solutions"
module: "SESA1016 Thermofluids"
type: tutorial
stream: "Part B: Fluid Mechanics"
tags: [sesa1016, tutorial-solutions, fluid-properties, hydrostatics]
sheet: "Problem Sheet 06 - Fluid Properties and Hydrostatics"
theory_notes: ["[[SESA1016 T7 - Fluid Properties and Viscosity]]", "[[SESA1016 T8 - Hydrostatics]]"]
key_concepts: ["[[Newtonian Fluid and Viscosity]]", "[[Pressure and Head]]"]
status: complete
sources: ["02 - Sources/Tutorial Sheets/Problem Sheet 06 - Fluid Properties and Hydrostatics.pdf"]
---

# SESA1016 Problem Sheet 06 - Fluid Properties and Hydrostatics Solutions

> [!abstract] Sheet Info
> Nine questions on viscosity, buoyancy, pressure measurement and hydrostatic balance. Draw a pressure path before writing equations; most sign errors disappear immediately.

## Q6.1 Viscosity of air at flight temperatures

Sutherland's law gives

$$
\boxed{\mu(T)=\mu_0\left(\frac{T}{T_0}\right)^{3/2}
\frac{T_0+S}{T+S}}
$$

with $\mu_0=1.716\times10^{-5}\ \mathrm{Pa\,s}$ at $T_0=273.15$ K and $S\approx111$ K for air.

![[tf_sutherland_viscosity.png]]

Dynamic viscosity increases with temperature even though air density usually decreases with altitude. Consequently, kinematic viscosity $\nu=\mu/\rho$ can change much more strongly than $\mu$ alone.

## Q6.2 Melting ice in a glass

A floating ice cube displaces a water volume whose weight equals the ice weight:

$$
\rho_wgV_{disp}=m_{ice}g.
$$

After melting, the ice becomes water of volume

$$V_{melt}=\frac{m_{ice}}{\rho_w}=V_{disp}.$$

Therefore the water level is unchanged:

$$\boxed{\Delta h=0}.$$

This assumes the ice is floating freely, the liquid is water, and losses by evaporation or overflow are negligible.

## Q6.3 Mercury manometer

The open limb is at atmospheric pressure. Moving down $h=0.15$ m through mercury raises pressure:

$$p_{bulb}=p_{atm}+\rho_{Hg}gh.$$

Taking $p_{atm}=101.325$ kPa and $\rho_{Hg}=13\,546\ \mathrm{kg\,m^{-3}}$,

$$
p_{bulb}=101.325+\frac{13\,546(9.81)(0.15)}{1000}
=\boxed{121.3\ \mathrm{kPa\ absolute}}.
$$

The corresponding gauge pressure is $19.9$ kPa.

## Q6.4 Inclined manometer

If the liquid interface moves a distance $\Delta l$ along a tube inclined at $\theta$ to the horizontal, its vertical rise is $\Delta z=\Delta l\sin\theta$. Hence

$$
\Delta p=\rho g\Delta l\sin\theta,
\qquad
\boxed{\Delta l=\frac{\Delta p}{\rho g\sin\theta}}.
$$

A small angle produces a large readable displacement for a small pressure difference: sensitivity increases as $1/\sin\theta$. A variable-angle instrument can therefore use a shallow setting for fine resolution and a steeper setting for a wider measurement range.

## Q6.5 Safe camera depth

The housing was tested at $0.8$ MPa. A safety margin of at least $25\%$ means the working pressure must satisfy

$$1.25p_{work}\le0.8\ \mathrm{MPa},$$

so $p_{work}\le0.64$ MPa gauge. In seawater, taking $\rho=1025\ \mathrm{kg\,m^{-3}}$,

$$
h_{max}=\frac{0.64\times10^6}{1025(9.81)}=63.6\ \mathrm m.
$$

To the nearest conservative $10$ m,

$$\boxed{h_{safe}=60\ \mathrm m}.$$

## Q6.6 Water and oil in a cylindrical tank

For diameter $D=0.70$ m,

$$A=\frac{\pi D^2}{4}=0.3848\ \mathrm{m^2}.$$

The water and oil depths are

$$
h_w=\frac{0.10}{A}=0.2599\ \mathrm m,
\qquad
h_o=\frac{0.30}{A}=0.7797\ \mathrm m.
$$

The base gauge pressure is the sum of the two hydrostatic contributions:

$$
p_g=\rho_wgh_w+\rho_ogh_o
$$

$$
=9.81[1000(0.2599)+800(0.7797)]
=\boxed{8.67\ \mathrm{kPa}}.
$$

## Q6.7 Loaded reservoir and capillary tube

The reservoir piston diameter is $D_1=0.12$ m, so

$$A_1=\frac{\pi D_1^2}{4}=0.01131\ \mathrm{m^2}.$$

Oil has $\rho=0.8(1000)=800\ \mathrm{kg\,m^{-3}}$. A $5$ kg load creates a pressure $mg/A_1$, equivalent to the oil head

$$
\Delta h=\frac{mg/A_1}{\rho g}=\frac{m}{\rho A_1}
=\boxed{0.5526\ \mathrm m=55.26\ \mathrm{cm}}.
$$

This is the difference between the two free-surface levels. Since the reservoir initially contains $h_1=0.042$ m of oil, the tube surface is $0.5946$ m above the base.

When the mass is removed, both surfaces settle to a common height $h_f$. With tube diameter $D_2=5$ mm,

$$A_2=\frac{\pi D_2^2}{4}=1.963\times10^{-5}\ \mathrm{m^2}.$$

Volume conservation gives

$$
A_1h_1+A_2(h_1+\Delta h)=(A_1+A_2)h_f,
$$

$$
\boxed{h_f=0.04296\ \mathrm m=42.96\ \mathrm{mm}}.
$$

> [!note] Diagram convention
> The sheet's first answer, $55.26$ cm, is the level difference caused by the load, not the tube surface's absolute height above the base.

## Q6.8 Bubble-tube level measurement

At the point where bubbles just emerge, the air gauge pressure balances the hydrostatic pressure above the outlet:

$$p_g=\rho g(d-1.0).$$

For $p_g=15$ kPa and oil density $\rho=850\ \mathrm{kg\,m^{-3}}$,

$$
d=1.0+\frac{15\,000}{850(9.81)}
=\boxed{2.80\ \mathrm m}.
$$

## Q6.9 Trapped-air well manometer

Initially the trapped air has volume $V_i=AH$ and pressure $p_i=p_{atm}$. After the tank level reaches the valve, the side-tube interface has risen by $\Delta l$, so

$$
V_f=A(H-\Delta l),
\qquad
p_f=p_{atm}+\rho g(H-\Delta l).
$$

The compression is isothermal, hence $p_iV_i=p_fV_f$:

$$
p_{atm}AH=
[p_{atm}+\rho g(H-\Delta l)]A(H-\Delta l).
$$

Expanding and collecting powers of $\Delta l$ gives

$$
\boxed{\rho g\Delta l^2-(p_{atm}+2\rho gH)\Delta l+\rho gH^2=0}.
$$

The physical solution is the smaller root, because it must satisfy $0<\Delta l<H$:

$$
\boxed{\Delta l=
\frac{p_{atm}+2\rho gH-
\sqrt{(p_{atm}+2\rho gH)^2-4(\rho g)^2H^2}}
{2\rho g}}.
$$

> [!warning] Root selection
> The second algebraic root violates the apparatus geometry. Always test roots against the permitted displacement before accepting them.

## Related

- [[SESA1016 T7 - Fluid Properties and Viscosity]]
- [[SESA1016 T8 - Hydrostatics]]
- [[Pressure and Head]]
- [[Newtonian Fluid and Viscosity]]
- [[SESA1016 Formula Sheet]]
