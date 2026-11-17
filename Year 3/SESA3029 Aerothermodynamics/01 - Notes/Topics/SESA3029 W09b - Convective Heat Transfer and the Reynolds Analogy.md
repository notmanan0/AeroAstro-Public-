---
title: "SESA3029 W09b - Convective Heat Transfer and the Reynolds Analogy"
module: "SESA3029 Aerothermodynamics"
type: topic
stream: "Block 5: Heat transfer"
order: 11
tags: [sesa3029, heat-transfer, convection, boundary-layer, thermal-boundary-layer, nusselt, prandtl, stanton, reynolds-analogy]
aliases: ["SESA3029 Lecture 5.3", "SESA3029 W09b", "Convective heat transfer"]
date: 2026-11-17
status: written-ahead
coverage: "Lecture 5.3 (all 15 slides) written ahead from the slides; no transcript yet"
parent: ["[[SESA3029 Aerothermodynamics Hub]]"]
prerequisites: ["[[SESA3029 W09a - Heat Conduction and Thermal Resistance]]", "[[SESA3043 3.1 - Boundary-Layer Concepts and Thickness Measures]]", "[[SESA3043 3.2 - Blasius and Falkner-Skan Similarity Solutions]]", "[[Reynolds Number]]"]
next_topics: ["[[SESA3029 W09c - Critical Thickness of Insulation and Fins]]"]
key_concepts: ["[[Newton's Law of Cooling]]", "[[Thermal Boundary Layer]]", "[[Prandtl Number]]", "[[Nusselt Number]]", "[[Stanton Number]]", "[[Reynolds Analogy]]"]
tutorial_sheets: ["[[SESA3029 Example Sheet 3 - Solutions]]"]
sources: ["02 - Sources/Lectures/Lecture5.3.pdf"]
---

# SESA3029 W09b - Convective Heat Transfer and the Reynolds Analogy

> [!abstract] Summary
> Convection is heat carried between a surface and a moving fluid, and Newton's law of cooling $\dot Q=hA_s(T_s-T_\infty)$ lumps all of its physics into the heat transfer coefficient $h$. A thermal boundary layer grows next to a heated or cooled wall alongside the velocity boundary layer, and the Prandtl number $\mathrm{Pr}=\mu c_p/k$ sets their relative thickness. The dimensionless form of $h$ is the Nusselt number, $\mathrm{Nu}=hL/k=\mathrm{St}\,\mathrm{Re}\,\mathrm{Pr}$, and it is found from correlations of the form $\mathrm{Nu}_x=C\,\mathrm{Re}_x^n\,\mathrm{Pr}^m$. Because heat and momentum diffuse through the boundary layer in the same way, these correlations follow from the skin friction: the laminar flat-plate result $\mathrm{Nu}_x=0.332\,\mathrm{Re}_x^{1/2}\mathrm{Pr}^{1/3}$ is the Blasius $c_f$ rewritten.

> [!summary]- Exam use: quick path
> - **Use it when:** a fluid flows past a surface at a different temperature and the question asks for $h$, a heat flux or a heat rate, given a Nusselt correlation.
> - **Assumptions:** steady, forced convection, constant fluid properties, low speed (no frictional heating), the correlation's own range of Re and wall condition (uniform wall temperature or uniform heat flux); for a flat plate, zero pressure gradient.
> - **Method:** 1. Compute $\mathrm{Re}=\rho VL/\mu=VL/\nu$ with the length the correlation uses ($x$ along a plate, $D$ for a pipe). 2. Decide laminar or turbulent from Re (plate laminar below $3\times10^5$). 3. $\mathrm{Nu}$ from the correlation. 4. $h=\mathrm{Nu}\,k/L$. 5. $\dot Q=hA_s(T_s-T_\infty)$, using $\bar h$ if $h$ varies along the surface.
> - **Common mistakes:** using a local correlation $\mathrm{Nu}_x$ as if it were the average (on a laminar plate $\bar h=2h(L)$, so this halves the heat rate); taking $k$ of the solid instead of the fluid in $\mathrm{Nu}=hL/k$.
> - **Practise:** [[#Example 2 - boundary-layer cooling of two parallel plates|the parallel-plates example]] · [[SESA3029 Example Sheet 3 - Solutions#Q2. Turbine blade: Newton cooling and similarity|ES3 Q2]]

Conduction ([[SESA3029 W09a - Heat Conduction and Thermal Resistance|W09a]]) moves heat through a solid or a stationary fluid by molecular contact alone. When the fluid moves, heat is still conducted into the first layer of fluid at the wall, but the flow then sweeps that heated fluid away and brings fresh fluid in its place. The steeper the temperature gradient this maintains at the wall, the more heat leaves the surface. Convection is therefore conduction at the wall combined with transport by the bulk motion, and anything that changes the flow near the wall (speed, viscosity, laminar or turbulent motion, distance from the leading edge) changes the heat transfer.

Newton's law of cooling ([[SESA3029 W09a - Heat Conduction and Thermal Resistance#9. Convection heat transfer|W09a §9]], which also covers forced and free convection) hides all of this inside one number:

$$
\dot Q=hA_s(T_s-T_\infty),
$$

with $T_s$ the surface temperature, $T_\infty$ the fluid temperature far from the surface, $A_s$ the wetted surface area and $h$ the **heat transfer coefficient** in W m⁻² K⁻¹. The law is a definition of $h$ rather than a physical law; the physics is in how $h$ depends on the flow, which is set by the velocity and thermal boundary layers and expressed through four dimensionless groups (Re, Pr, Nu and St). Typical values run from about 2–25 W m⁻² K⁻¹ for free convection in a gas to 25–250 for forced convection in air and thousands for liquids, which is why a fan or a water jacket cools so much better than still air.

## 1. The velocity boundary layer

Fluid in contact with a solid surface takes the surface's velocity: on a stationary plate, $u=0$ at $y=0$. This is the **no-slip condition**. The motionless layer slows the layer above it through viscous shear, that layer slows the next, and so on, so the presence of the plate is felt up to a distance $\delta$ from it, the **boundary layer thickness**, defined as the height at which $u=0.99V$. Above $\delta$ the fluid moves at the free-stream velocity $V$. The boundary conditions are

$$
u=0\ \text{ at }\ y=0,\qquad u=V\ \text{ at }\ y=\delta .
$$

Along a flat plate the layer starts laminar, with smooth, ordered streamlines and a nearly parabolic velocity profile. Downstream it passes through a **transition region**, where the flow fluctuates between laminar and turbulent, and becomes a **turbulent boundary layer** with irregular, three-dimensional eddies. The turbulent profile is much fuller (it flattens out across most of the layer) and drops steeply to zero in a thin viscous sublayer at the wall, with a buffer layer between the two. The distance from the leading edge to the start of transition is $x_{cr}$.

The state of the layer is governed by the **Reynolds number**, the ratio of inertial to viscous forces,

$$
\mathrm{Re}=\frac{\rho VL}{\mu}=\frac{VL}{\nu},
$$

with $\rho$ the density (kg m⁻³), $V$ the velocity (m s⁻¹), $L$ a characteristic length (m), $\mu$ the dynamic viscosity (kg m⁻¹ s⁻¹) and $\nu=\mu/\rho$ the kinematic viscosity. Low Re gives a laminar layer and high Re a turbulent one. A flat-plate boundary layer is taken as laminar for $\mathrm{Re}_x=\rho Vx/\mu<3\times10^5$; many textbooks quote $5\times10^5$, and the real value depends on the free-stream turbulence and surface roughness. Flow inside a pipe is taken as laminar for $\mathrm{Re}_D<2000$.

The velocity boundary layer itself, its thickness measures and the Blasius solution are covered in [[SESA3043 3.1 - Boundary-Layer Concepts and Thickness Measures|SESA3043 3.1]] and [[SESA3043 3.2 - Blasius and Falkner-Skan Similarity Solutions|SESA3043 3.2]]. Two results from there are used below: on a laminar flat plate $\delta_{99}=4.91x/\sqrt{\mathrm{Re}_x}$ and the local skin friction coefficient is

$$
c_{f,x}=\frac{\tau_w}{\tfrac12\rho V^2}=\frac{0.664}{\sqrt{\mathrm{Re}_x}} .
$$

## 2. The thermal boundary layer

When fluid at $T_\infty$ flows over a surface at a different temperature $T_s$, the same layer-by-layer process happens with energy in place of momentum. The fluid touching the wall reaches $T_s$, it exchanges energy with the next layer, and so on, so a **thermal boundary layer** grows from the leading edge. Its thickness $\delta_t$ is the distance from the surface at which

$$
T-T_s=0.99\,(T_\infty-T_s).
$$

Like $\delta$, it thickens in the flow direction, so the effect of the heat transfer is felt further from the plate downstream. On a heated or cooled surface in a moving fluid both layers develop at the same time, and how the velocity layer grows relative to the thermal layer controls the convection.

**The heat transfer coefficient from the wall gradient.** At the wall the fluid is at rest (no slip), so heat crosses the first layer of fluid by conduction alone. Fourier's law in the fluid, with $y$ measured from the wall into the fluid and $k$ the fluid's conductivity, gives the surface heat flux

$$
\dot q_s=-k\left.\frac{\partial T}{\partial y}\right|_{y=0}.
$$

The same flux, written with Newton's law of cooling, is

$$
\dot q_s=h\,(T_s-T_\infty).
$$

Equate the two:

$$
h\,(T_s-T_\infty)=-k\left.\frac{\partial T}{\partial y}\right|_{y=0}
$$

$$
\Rightarrow\quad h=\frac{-k\,(\partial T/\partial y)_{y=0}}{T_s-T_\infty}.
$$

The wall gradient scales roughly as $(T_\infty-T_s)/\delta_t$, so $h\sim k/\delta_t$: a thin thermal boundary layer means a steep gradient and a high $h$. This is why $h$ is largest at the leading edge, where $\delta_t\to0$, and falls downstream as the layer thickens (§5).

![[at_w09b_boundary_layers.png|900]]

Panel (a) draws both layers to scale on the two plates of the example in §6: at the trailing edge $\delta=1.82$ mm and $\delta_t=2.07$ mm, both well short of the 5 mm half-gap. Panel (b) plots the profiles against the similarity variable $\eta=y\sqrt{V/\nu x}$, computed from the Blasius and thermal similarity equations for a plate at uniform $T_s$.

## 3. The Prandtl number

Momentum spreads through a fluid by viscosity, at a rate set by the **momentum diffusivity** $\nu=\mu/\rho$. Heat spreads by conduction, at a rate set by the **thermal diffusivity** $\alpha=k/(\rho c_p)$. Both have units of m² s⁻¹. Their ratio is the **Prandtl number**:

$$
\mathrm{Pr}=\frac{\nu}{\alpha}=\frac{\mu/\rho}{k/(\rho c_p)} .
$$

The densities cancel:

$$
\boxed{\mathrm{Pr}=\frac{\mu c_p}{k}}
$$

with $\mu$ in kg m⁻¹ s⁻¹, $c_p$ the specific heat capacity in J kg⁻¹ K⁻¹ and $k$ the thermal conductivity in W m⁻¹ K⁻¹. Pr is a property of the fluid alone: about 0.7 for air and most gases, about 7 for water at room temperature, 0.01–0.03 for liquid metals and hundreds or more for oils.

Pr measures the relative thickness of the velocity and thermal boundary layers:

- $\mathrm{Pr}<1$: momentum diffuses more slowly than heat, so the thermal boundary layer is thicker than the velocity one (air, liquid metals);
- $\mathrm{Pr}>1$: momentum diffuses faster, so the velocity boundary layer is thicker (water, oils);
- $\mathrm{Pr}\approx1$: the two diffuse at similar rates and the layers have similar thickness.

For a laminar flat plate at uniform wall temperature with Pr between about 0.6 and 50, the similarity solution gives $\delta_t/\delta\approx\mathrm{Pr}^{-1/3}$. For air at $\mathrm{Pr}=0.72$ this is 1.12 (the computed ratio in panel (a) above is $2.07/1.82=1.14$), and for water at $\mathrm{Pr}=7$ it is 0.52, which is the much thinner orange profile in panel (b). At $\mathrm{Pr}=1$ the temperature profile and the velocity profile are the same curve, a fact that §7 turns into the Reynolds analogy.

## 4. Nusselt and Stanton numbers

The **Nusselt number** is the dimensionless heat transfer coefficient:

$$
\mathrm{Nu}=\frac{hL}{k},
$$

with $k$ the conductivity of the fluid ([[SESA3029 W09a - Heat Conduction and Thermal Resistance#11. The Nusselt number|W09a §11]] introduces it). It compares the heat transfer by convection with the heat that pure conduction would carry across a fluid layer of thickness $L$ with the same temperature difference. Per unit area, convection gives $h\,\Delta T$ and conduction across the layer gives $k\,\Delta T/L$, so their ratio is

$$
\frac{h\,\Delta T}{k\,\Delta T/L}=\frac{hL}{k}=\mathrm{Nu}.
$$

$\mathrm{Nu}=1$ would mean the fluid might as well be stationary; large Nu means the motion multiplies the heat transfer many times over. When $L$ is the distance $x$ from the leading edge, the result is the local Nusselt number $\mathrm{Nu}_x=hx/k$.

The **Stanton number** compares the heat transferred to the fluid with the heat capacity of the fluid stream passing the surface:

$$
\mathrm{St}=\frac{h}{\rho Vc_p}.
$$

Multiply top and bottom by $\Delta T$: the numerator $h\,\Delta T$ is the wall heat flux, and the denominator $\rho Vc_p\,\Delta T$ is the flux of enthalpy that a stream of speed $V$ would carry if its whole temperature changed by $\Delta T$.

**Relation between the numbers.** The four groups share terms. Write out the product of St, Re and Pr:

$$
\mathrm{St}\times\mathrm{Re}\times\mathrm{Pr}=\frac{h}{\rho Vc_p}\times\frac{\rho VL}{\mu}\times\frac{c_p\mu}{k}.
$$

Cancel $\rho V$ between the first two factors:

$$
=\frac{h}{c_p}\times\frac{L}{\mu}\times\frac{c_p\mu}{k}.
$$

Cancel $c_p$ and $\mu$:

$$
=\frac{hL}{k}=\mathrm{Nu}.
$$

$$
\boxed{\mathrm{Nu}=\mathrm{St}\times\mathrm{Re}\times\mathrm{Pr}}
$$

So $\mathrm{St}=\mathrm{Nu}/(\mathrm{Re}\,\mathrm{Pr})$; this is the step that connects heat transfer to skin friction in §7.

## 5. Correlations for the Nusselt number

Finding $h$ means finding Nu, and for most flows Nu comes from correlations built up from experiment and analysis for particular geometries, flow regimes and wall conditions. The standard set is:

| Flow | Range | Uniform wall heat flux | Uniform wall temperature |
|---|---|---|---|
| Laminar pipe flow (fully developed) | $\mathrm{Re}<2000$ | $\mathrm{Nu}=4.364$ | $\mathrm{Nu}=3.658$ |
| Laminar boundary layer (flat plate) | $\mathrm{Re}<3\times10^5$ | $\mathrm{Nu}_x=0.453\,\mathrm{Re}_x^{1/2}\mathrm{Pr}^{1/3}$ | $\mathrm{Nu}_x=0.332\,\mathrm{Re}_x^{1/2}\mathrm{Pr}^{1/3}$ |
| Turbulent pipe flow | $2000<\mathrm{Re}<50\,000$ | $\mathrm{Nu}=0.023\,\mathrm{Re}^{4/5}\mathrm{Pr}^n$ | (same) |
| Turbulent boundary layer (flat plate) | $\mathrm{Re}>3\times10^5$ | $\mathrm{Nu}_x=0.0308\,\mathrm{Re}_x^{4/5}\mathrm{Pr}^{1/3}$ | $\mathrm{Nu}_x=0.0296\,\mathrm{Re}_x^{4/5}\mathrm{Pr}^{1/3}$ |

In the turbulent pipe correlation $n=0.3$ when the fluid is being cooled and $n=0.4$ when it is being heated. For the boundary-layer correlations the length is $x$, the distance from the leading edge; for pipe flow it is the pipe diameter $D$, with Re based on the mean velocity. A uniform heat flux gives a higher Nu than a uniform wall temperature (0.453 against 0.332 laminar, 36 % more), because with a fixed flux the wall temperature rises downstream and keeps the gradient at the wall steeper there.

All of the boundary-layer correlations have the general form

$$
\mathrm{Nu}_x=C\,\mathrm{Re}_x^n\,\mathrm{Pr}^m ,
$$

known in this module as the **Reynolds analogy**; the form and the constants follow from the skin friction (§7).

**Local and average values.** The flat-plate correlations give the local $\mathrm{Nu}_x$, so $h$ varies along the plate. For the laminar, uniform-wall-temperature case, write the local coefficient out:

$$
h(x)=\frac{k}{x}\mathrm{Nu}_x=\frac{k}{x}\,0.332\left(\frac{\rho Vx}{\mu}\right)^{1/2}\mathrm{Pr}^{1/3} .
$$

Collect the powers of $x$:

$$
h(x)=0.332\left(\frac{\rho V}{\mu}\right)^{1/2}\mathrm{Pr}^{1/3}\,k\,x^{-1/2} .
$$

So $h\propto x^{-1/2}$, infinite at the leading edge and falling downstream. The heat rate through a strip of width $w$ is $\mathrm{d}\dot Q=h(x)\,(w\,\mathrm dx)\,\Delta T$, with $\Delta T=T_s-T_\infty$, so over a plate of length $L$

$$
\dot Q=\left(\int_0^Lh(x)\,\mathrm dx\right)w\,\Delta T .
$$

Define the average coefficient $\bar h$ as the constant value that gives the same heat rate, $\dot Q=\bar hLw\,\Delta T=\bar hA\,\Delta T$:

$$
\bar h=\frac1L\int_0^Lh(x)\,\mathrm dx .
$$

Substitute $h(x)$ and take the constants outside:

$$
\bar h=\frac{0.332\,(\rho V/\mu)^{1/2}\,\mathrm{Pr}^{1/3}\,k}{L}\int_0^Lx^{-1/2}\,\mathrm dx .
$$

The integral is $\left[2x^{1/2}\right]_0^L=2L^{1/2}$:

$$
\bar h=0.664\left(\frac{\rho V}{\mu}\right)^{1/2}\mathrm{Pr}^{1/3}\,k\,L^{-1/2}.
$$

Comparing with $h(x)$ at $x=L$,

$$
\boxed{\bar h=2\,h(L)}\qquad\Rightarrow\qquad \overline{\mathrm{Nu}}_L=\frac{\bar hL}{k}=0.664\,\mathrm{Re}_L^{1/2}\mathrm{Pr}^{1/3}\quad(\text{laminar, uniform }T_s).
$$

The same steps with $h\propto x^{-1/5}$ give $\int_0^Lx^{-1/5}\,\mathrm dx=\tfrac54L^{4/5}$, so for a plate turbulent from the leading edge $\bar h=\tfrac54h(L)$ and $\overline{\mathrm{Nu}}_L=0.037\,\mathrm{Re}_L^{4/5}\mathrm{Pr}^{1/3}$.

![[at_w09b_local_h.png|900]]

Panel (a) shows $h(x)$ on the plate of §6 and its average $\bar h=2h(L)$. Panel (b) shows the jump at transition: at $\mathrm{Re}_x=3\times10^5$ the turbulent $\mathrm{Nu}_x$ is about 3.9 times the laminar value, because turbulent mixing thins the near-wall layer that the heat has to cross by conduction.

## 6. Worked examples

### Example 1 - pipe cooling

*Air at $T_\infty=10^\circ$C flows at $V=8$ m s⁻¹ across a pipe of diameter $D=10$ cm whose surface is at $T_s=110^\circ$C. Take $k=0.02808$ W m⁻¹ K⁻¹, $\nu=1.896\times10^{-5}$ m² s⁻¹, $\mathrm{Pr}=0.72$ and $\overline{\mathrm{Nu}}=0.027\,\mathrm{Re}^{0.805}\mathrm{Pr}^{1/3}$. Determine the rate of heat loss from the pipe per unit length.*

The flow is across the outside of the pipe, so the length scale is the diameter and the correlation is an average over the circumference. It is the standard correlation for a cylinder in cross-flow, valid for $\mathrm{Re}_D$ from about $4\times10^4$ to $4\times10^5$. The pipe-flow correlations of §5 are for flow inside a pipe and do not apply here.

$$
\mathrm{Re}=\frac{VD}{\nu}=\frac{8\times0.1}{1.896\times10^{-5}}=4.219\times10^4 ,
$$

inside the correlation's range.

$$
\mathrm{Nu}=0.027\times(4.219\times10^4)^{0.805}\times0.72^{1/3}=127.97\approx128 .
$$

From $\mathrm{Nu}=hD/k$,

$$
h=\mathrm{Nu}\frac kD=128\times\frac{0.02808}{0.1}=35.94\ \text{W m}^{-2}\text{K}^{-1}.
$$

Per unit length ($L=1$ m) the surface area is

$$
A_s=\pi DL=\pi\times0.1\times1=0.314\ \text{m}^2 ,
$$

and the heat loss is

$$
\dot Q=hA_s(T_s-T_\infty)=35.94\times0.314\times(110-10)=\boxed{1128.5\ \text{W per metre}}.
$$

A temperature difference in K equals the same difference in °C, so the Celsius values can be used directly. With $A_s=\pi\times0.1=0.31416$ m² unrounded the answer is 1129 W.

### Example 2 - boundary-layer cooling of two parallel plates

*Air at 2 bar and 15 °C flows at 8 m s⁻¹ between two parallel plates 1 cm apart, each $L=15$ cm long in the flow direction and $W=10$ cm wide, held at 40 °C. Take $\mu=1.78\times10^{-5}$ N s m⁻², $k=0.0248$ W m⁻¹ K⁻¹, $\mathrm{Pr}=0.72$. (a) Check whether the flow is laminar or turbulent. (b) Find the heat transfer rate through each plate.*

**(a)** The density follows from the ideal-gas law with $R=287$ J kg⁻¹ K⁻¹ and $T=15+273=288$ K:

$$
\rho=\frac{p}{RT}=\frac{2\times10^5}{287\times288}=2.42\ \text{kg m}^{-3}.
$$

The highest Reynolds number on the plate is at the trailing edge:

$$
\mathrm{Re}_L=\frac{\rho VL}{\mu}=\frac{2.42\times8\times0.15}{1.78\times10^{-5}}=1.631\times10^5 .
$$

$\mathrm{Re}_L<3\times10^5$, so the boundary layer is laminar along the whole plate. The plates are treated as two separate flat plates, each with its own boundary layer from its leading edge. This is valid because the layers stay thin compared with the gap: at the trailing edge $\delta=4.91L/\sqrt{\mathrm{Re}_L}=1.8$ mm and $\delta_t\approx2.1$ mm, well inside the 5 mm half-gap (figure in §2), so they do not merge and the core flow stays at 15 °C.

**(b)** The heat transfer coefficient varies with $x$, so the local correlation for a laminar layer at uniform wall temperature is averaged as in §5:

$$
\bar h=0.664\left(\frac{\rho V}{\mu}\right)^{1/2}\mathrm{Pr}^{1/3}\,k\,L^{-1/2}
=0.664\left(\frac{2.42\times8}{1.78\times10^{-5}}\right)^{1/2}\times0.72^{1/3}\times0.0248\times0.15^{-1/2}.
$$

$$
\bar h=39.74\ \text{W m}^{-2}\text{K}^{-1}.
$$

Each plate has one face in contact with the flow, of area $A_s=WL=0.1\times0.15=0.015$ m², so

$$
\dot Q=\bar hA_s\,\Delta T=39.74\times0.015\times(40-15)=\boxed{14.9\ \text{W per plate}},
$$

from each plate into the air.

> [!check] Local values on the same plate
> $h(x)=0.332\,(\rho V/\mu)^{1/2}\mathrm{Pr}^{1/3}k\,x^{-1/2}$ gives 77.0 W m⁻² K⁻¹ at $x=1$ cm, 34.4 at 5 cm and 19.87 at the trailing edge, and $2\times19.87=39.74=\bar h$ ✓. Using $h(L)$ in place of $\bar h$ would give 7.45 W, half the right answer.

## 7. The Reynolds analogy

The velocity boundary layer and the thermal boundary layer are built by the same process: something (momentum or heat) diffuses away from the wall while the flow carries it downstream. On a flat plate the two are governed by equations of identical form, so the heat transfer can be predicted from the skin friction.

### The two boundary-layer equations

For steady, two-dimensional, incompressible flow over a flat plate with zero pressure gradient and constant properties, the $x$-momentum boundary-layer equation ([[Prandtl Boundary-Layer Equations]]) is

$$
u\frac{\partial u}{\partial x}+v\frac{\partial u}{\partial y}=\nu\frac{\partial^2u}{\partial y^2}.
$$

The left side is the momentum carried in by the flow; the right side is viscous diffusion across the layer. The energy balance on the same fluid element, at low speed so that frictional heating is negligible, has the same structure: enthalpy carried in by the flow balanced by conduction across the layer. Conduction along the layer is dropped for the same thin-layer reason that viscous diffusion along it is dropped. Dividing through by $\rho c_p$,

$$
u\frac{\partial T}{\partial x}+v\frac{\partial T}{\partial y}=\alpha\frac{\partial^2T}{\partial y^2},\qquad \alpha=\frac{k}{\rho c_p}.
$$

### Dimensionless form

Define

$$
u^*=\frac uV,\qquad T^*=\frac{T-T_s}{T_\infty-T_s}.
$$

$V$ and $T_\infty-T_s$ are constants, so dividing the momentum equation by $V$ and the energy equation by $T_\infty-T_s$ gives

$$
u\frac{\partial u^*}{\partial x}+v\frac{\partial u^*}{\partial y}=\nu\frac{\partial^2u^*}{\partial y^2},\qquad
u\frac{\partial T^*}{\partial x}+v\frac{\partial T^*}{\partial y}=\alpha\frac{\partial^2T^*}{\partial y^2}.
$$

The boundary conditions are the same too: $u^*=0$ and $T^*=0$ at the wall, and $u^*\to1$ and $T^*\to1$ at the edge of the layer and at the leading edge.

### Prandtl number of one

If $\nu=\alpha$, which is $\mathrm{Pr}=1$, the two equations and their boundary conditions are identical, so their solutions are identical:

$$
T^*(x,y)=u^*(x,y),\qquad\left.\frac{\partial T^*}{\partial y}\right|_{y=0}=\left.\frac{\partial u^*}{\partial y}\right|_{y=0}.
$$

This is the coincidence of the dotted and red curves in panel (b) of the §2 figure.

### Skin friction in terms of the profile

The wall shear stress and the skin friction coefficient are

$$
\tau_w=\mu\left.\frac{\partial u}{\partial y}\right|_0=\mu V\left.\frac{\partial u^*}{\partial y}\right|_0,
$$

$$
c_f=\frac{\tau_w}{\tfrac12\rho V^2}=\frac{2\mu}{\rho V}\left.\frac{\partial u^*}{\partial y}\right|_0 .
$$

Halve it:

$$
\frac{c_f}{2}=\frac{\mu}{\rho V}\left.\frac{\partial u^*}{\partial y}\right|_0 .
$$

### Heat transfer in terms of the profile

From §2, $h=-k\,(\partial T/\partial y)_0/(T_s-T_\infty)$. Since $T-T_s=(T_\infty-T_s)T^*$,

$$
\left.\frac{\partial T}{\partial y}\right|_0=(T_\infty-T_s)\left.\frac{\partial T^*}{\partial y}\right|_0=-(T_s-T_\infty)\left.\frac{\partial T^*}{\partial y}\right|_0 ,
$$

$$
h=k\left.\frac{\partial T^*}{\partial y}\right|_0 .
$$

Divide by $\rho Vc_p$ to form the Stanton number:

$$
\mathrm{St}=\frac{h}{\rho Vc_p}=\frac{k}{\rho Vc_p}\left.\frac{\partial T^*}{\partial y}\right|_0 .
$$

### The ratio of Stanton number to skin friction

Divide St by $c_f/2$. The wall gradients are equal at $\mathrm{Pr}=1$ and cancel:

$$
\frac{\mathrm{St}}{c_f/2}=\frac{k/(\rho Vc_p)}{\mu/(\rho V)}=\frac{k}{\mu c_p}=\frac{1}{\mathrm{Pr}}=1 .
$$

$$
\boxed{\mathrm{St}=\frac{c_f}{2}}\qquad(\mathrm{Pr}=1,\ \text{flat plate, zero pressure gradient})
$$

This is Reynolds' analogy in its original form: the Stanton number equals half the skin friction coefficient, so a measurement of drag gives the heat transfer. It applies to the local values and, by integration, to the averages.

### Other Prandtl numbers

For other Prandtl numbers the thermal layer is thicker or thinner than the velocity layer by about $\mathrm{Pr}^{-1/3}$ (§3), which steepens or flattens the wall gradient. The Chilton–Colburn form of the analogy corrects for this:

$$
\mathrm{St}\,\mathrm{Pr}^{2/3}=\frac{c_f}{2}\qquad(0.6<\mathrm{Pr}<60).
$$

### The laminar correlation from the Blasius skin friction

Substitute $c_{f,x}=0.664\,\mathrm{Re}_x^{-1/2}$:

$$
\mathrm{St}_x\,\mathrm{Pr}^{2/3}=\frac{0.664}{2}\mathrm{Re}_x^{-1/2}=0.332\,\mathrm{Re}_x^{-1/2}.
$$

Divide by $\mathrm{Pr}^{2/3}$:

$$
\mathrm{St}_x=0.332\,\mathrm{Re}_x^{-1/2}\,\mathrm{Pr}^{-2/3}.
$$

Multiply by $\mathrm{Re}_x\,\mathrm{Pr}$ (§4):

$$
\mathrm{Nu}_x=\mathrm{St}_x\,\mathrm{Re}_x\,\mathrm{Pr}=0.332\,\mathrm{Re}_x^{1/2}\,\mathrm{Pr}^{1/3}.
$$

It is the laminar boundary-layer correlation of §5 for a uniform wall temperature. The turbulent case works the same way: the turbulent flat-plate skin friction $c_{f,x}=0.0592\,\mathrm{Re}_x^{-1/5}$ gives $\mathrm{Nu}_x=0.0296\,\mathrm{Re}_x^{4/5}\mathrm{Pr}^{1/3}$, the turbulent correlation of §5. So the exponent of Re in $\mathrm{Nu}_x=C\,\mathrm{Re}_x^n\mathrm{Pr}^m$ is set by the friction law ($n=1/2$ laminar, $4/5$ turbulent), the constant is $c_f\sqrt{\mathrm{Re}_x}/2$ or its turbulent equivalent, and $m=1/3$ comes from the Pr correction. This is the sense in which the general form is called the Reynolds analogy.

![[at_w09b_reynolds_analogy.png|900]]

The figure checks this against the exact solution of the thermal boundary-layer equation. $0.332\,\mathrm{Pr}^{1/3}$ is within about 2 % of the exact value for $0.6<\mathrm{Pr}<100$ (0.2976 against 0.2956 for air, 0.635 against 0.646 for water). The original $\mathrm{St}=c_f/2$, which gives $0.332\,\mathrm{Pr}$, is exact only at $\mathrm{Pr}=1$; for air it is 19 % low and for water about 3.6 times too high.

> [!warning] Where the analogy fails
> The derivation needed zero pressure gradient. With a pressure gradient the momentum equation gains a $-\frac1\rho\frac{\mathrm dp}{\mathrm dx}$ term that the energy equation has no counterpart for, so friction and heat transfer separate: near separation $c_f\to0$ while the heat transfer stays finite. Form drag (pressure drag on a bluff body) has no heat-transfer counterpart at all. At high Mach number frictional heating adds a source term to the energy equation and $T_\infty$ has to be replaced by the recovery temperature.

## Problem-solving workflow

1. List the fluid properties ($\rho$ or $\nu$, $\mu$, $k$, Pr) at the stated conditions; get $\rho$ from $p=\rho RT$ for a gas if it is not given.
2. Choose the correlation that matches the geometry (plate, flow across a cylinder, flow inside a pipe), the regime and the wall condition, and use its length scale.
3. Compute Re and check it against the correlation's range (laminar plate below $3\times10^5$).
4. Get Nu, then $h=\mathrm{Nu}\,k/L$. If the correlation is local ($\mathrm{Nu}_x$), integrate for $\bar h$: $\bar h=2h(L)$ laminar, $\tfrac54h(L)$ turbulent.
5. $\dot Q=\bar hA_s(T_s-T_\infty)$, with $A_s$ the wetted area only.

## Terminology and alternative names

| Course term | Also called | Where the course uses it | Note |
|---|---|---|---|
| heat transfer coefficient $h$ | convection coefficient; film coefficient; surface conductance | L5.3 slide 7; L5.4 slide 6 | |
| dimensionless heat transfer coefficient Nu | Nusselt number | L5.3 slide 7 | |
| Reynolds analogy ($\mathrm{Nu}_x=C\,\mathrm{Re}_x^n\mathrm{Pr}^m$) | power-law Nusselt correlation; Chilton–Colburn analogy (for $\mathrm{St}\,\mathrm{Pr}^{2/3}=c_f/2$) | L5.3 slides 7–8 | Most textbooks reserve "Reynolds analogy" for $\mathrm{St}=c_f/2$ |
| momentum diffusivity | kinematic viscosity $\nu$ | L5.3 slides 5–6 | |
| thermal boundary layer $\delta_t$ | temperature boundary layer (also on slide 4) | L5.3 slide 4 | |
| uniform wall temperature / uniform wall heat flux | isothermal wall / constant heat flux | L5.3 slides 7–8 | |

## Links

- Parent: [[SESA3029 Aerothermodynamics Hub]]
- Previous: [[SESA3029 W09a - Heat Conduction and Thermal Resistance]] (Fourier's law and thermal resistance, used for $h$ at the wall and in W09c) · Next: [[SESA3029 W09c - Critical Thickness of Insulation and Fins]]
- New concepts: [[Newton's Law of Cooling]] · [[Thermal Boundary Layer]] · [[Prandtl Number]] · [[Nusselt Number]] · [[Stanton Number]] · [[Reynolds Analogy]]
- Velocity boundary layer: [[SESA3043 3.1 - Boundary-Layer Concepts and Thickness Measures]] · [[SESA3043 3.2 - Blasius and Falkner-Skan Similarity Solutions#Skin friction|SESA3043 3.2, Blasius skin friction]] · [[Blasius and Falkner-Skan Similarity Solutions]] · [[Prandtl Boundary-Layer Equations]] · [[Reynolds Number]] · [[Boundary-layer Thickness Measures]]
- Worked sheet: [[SESA3029 Example Sheet 3 - Solutions#Q2. Turbine blade: Newton cooling and similarity|ES3 Q2]] · [[SESA3029 Example Sheet 3 - Solutions#Q3. Rocket instrument bay|ES3 Q3]] · [[SESA3029 Example Sheet 3 - Solutions#Q4. Meteor stagnation-point heating|ES3 Q4]]
- Formulae: [[SESA3029 Formula Sheet]]

## Sources

- `Lecture5.3.pdf`: Lecture 5.3, convective heat transfer (boundary layer, other dimensionless numbers, Reynolds analogy, example problems), 15 slides; slide 9 repeats slide 10. No lecturer is named on the deck. Slides 2–4 the velocity and thermal boundary layers (figures after Çengel); slide 5 the Prandtl number; slide 6 Re, Pr, Nu, St and $\mathrm{Nu}=\mathrm{St}\,\mathrm{Re}\,\mathrm{Pr}$; slides 7–8 the correlations and the general form; slides 10–11 the pipe-cooling example; slides 12–15 the parallel-plates example.
- This note is written ahead from the slides. No transcript exists yet; it will be reconciled with the transcript once the lecture has been given. Lectures for the heat-transfer block are expected from Thu 19 Nov 2026.
- Additions not on the slides, each derived here: $h$ from the wall gradient (§2), the average $\bar h=2h(L)$ in closed form and the turbulent $\tfrac54$ (§5, slide 15 does the laminar integral numerically), and the derivation of $\mathrm{St}=c_f/2$ and the Chilton–Colburn form, with the 0.332 and 0.0296 constants recovered from the skin friction (§7).
- Figures: `generate_aerothermo_w09bc_figures.py` (`at_w09b_boundary_layers.png`, `at_w09b_local_h.png`, `at_w09b_reynolds_analogy.png`). The profiles and the exact $\mathrm{Nu}_x/\sqrt{\mathrm{Re}_x}$ come from numerical solutions of the Blasius equation and the thermal similarity equation ($f''(0)=0.33206$ in the $\eta=y\sqrt{V/\nu x}$ scaling).
- Textbooks cited on the slides: Holman, *Heat Transfer*, 10th ed.; Çengel, *Heat Transfer: A Practical Approach*, 2nd ed. (external forced convection and the Chilton–Colburn analogy).

## Self-study tasks

There is no transcript yet, so no homework has been set aloud. The slide references below are where each task or example appears.

### Core

- [ ] **(L5.3 slides 12–15)** Parallel plates: check laminar or turbulent, then find $\bar h$ and the heat rate per plate. Answers $\mathrm{Re}_L=1.63\times10^5$ (laminar), $\bar h=39.74$ W m⁻² K⁻¹, 14.9 W. → [[#Example 2 - boundary-layer cooling of two parallel plates|§6, Example 2]]
- [ ] **(L5.3 slides 10–11)** Pipe in cross-flow: heat loss per metre. Answer 1128.5 W (1129 W with $A_s$ unrounded). → [[#Example 1 - pipe cooling|§6, Example 1]]
- [ ] **(L5.3 slide 15)** Derive $\bar h=2h(L)$ for the laminar flat plate, and $\overline{\mathrm{Nu}}_L=0.664\,\mathrm{Re}_L^{1/2}\mathrm{Pr}^{1/3}$. → [[#5. Correlations for the Nusselt number|§5]]
- [ ] **(L5.3 slide 6)** Show that $\mathrm{Nu}=\mathrm{St}\,\mathrm{Re}\,\mathrm{Pr}$ and interpret each group as a ratio. → [[#4. Nusselt and Stanton numbers|§4]]
- [ ] [[SESA3029 Example Sheet 3 - Solutions#Q2. Turbine blade: Newton cooling and similarity|ES3 Q2]]: Newton cooling and similarity on a turbine blade. Answers 122 and 47.5 kW m⁻².

### Further practice

- [ ] **(L5.3 slides 7–8)** Derive the Reynolds analogy $\mathrm{St}=c_f/2$ for $\mathrm{Pr}=1$, then recover $\mathrm{Nu}_x=0.332\,\mathrm{Re}_x^{1/2}\mathrm{Pr}^{1/3}$ from $c_{f,x}=0.664\,\mathrm{Re}_x^{-1/2}$ (suggested, not lecturer-set). → [[#7. The Reynolds analogy|§7]]
- [ ] **(L5.3 slide 5)** Show $\mathrm{Pr}=\nu/\alpha=\mu c_p/k$ and estimate $\delta_t/\delta$ for air and water. Answers 1.12 and 0.52. → [[#3. The Prandtl number|§3]]
- [ ] [[SESA3029 Example Sheet 3 - Solutions#Q3. Rocket instrument bay|ES3 Q3]]: the cross-flow correlation of slide 10 on a rocket skin, in series with conduction and an internal film.
- [ ] [[SESA3029 Example Sheet 3 - Solutions#Q4. Meteor stagnation-point heating|ES3 Q4]]: a stagnation-point correlation of the form $C\,\mathrm{Re}^n\mathrm{Pr}^m$, with $k$ found from $\mathrm{Pr}=\mu c_p/k$.
- [ ] (suggested, not lecturer-set) Show that a plate turbulent from its leading edge has $\bar h=\tfrac54h(L)$ and $\overline{\mathrm{Nu}}_L=0.037\,\mathrm{Re}_L^{4/5}\mathrm{Pr}^{1/3}$. → [[#5. Correlations for the Nusselt number|§5]]

## Transcript and slide slips

> [!warning] Slips on L5.3 slides 4, 7 and 8
> Where: [[#5. Correlations for the Nusselt number]].
>
> | Where | Printed | Correct |
> |---|---|---|
> | slide 4 | "thermal boundary later $\delta_t$" | thermal boundary layer |
> | slides 7–8 | $\mathrm{Nu}_x=C\,\mathrm{Re}_x^n\,\mathrm{Pr}_x^m$ | $\mathrm{Pr}^m$: Pr is a fluid property and does not vary with $x$ |
> | slide 8 | turbulent pipe flow written $\mathrm{Nu}_x=0.023\,\mathrm{Re}_x^{4/5}\mathrm{Pr}^n$ | fully developed pipe flow uses the diameter: $\mathrm{Nu}_D=0.023\,\mathrm{Re}_D^{4/5}\mathrm{Pr}^n$. The $n$ here (0.3 or 0.4) is not the Re exponent $n$ of the general form |
> | slide 8 | turbulent pipe flow for $2000<\mathrm{Re}<50\,000$ | this correlation (Dittus–Boelter) is normally quoted for $\mathrm{Re}_D\gtrsim10^4$; between 2000 and about $10^4$ the flow is transitional |

> [!warning] Arithmetic on L5.3 slides 11, 13 and 15
> Where: [[#6. Worked examples]].
>
> | Where | Printed | Recomputed |
> |---|---|---|
> | slide 11 | $\dot Q=1128.5$ W | correct with $A_s$ rounded to 0.314 m²; 1129 W with $\pi\times0.1$ |
> | slide 13 | $\mathrm{Re}=163\,261$ | 163 146 with $\rho=2.42$ (163 124 with $\rho$ unrounded); laminar either way |
> | slide 15 | $k$ in "W m⁻¹ K" | W m⁻¹ K⁻¹ |
> | slide 15 | $\bar h=39.76$ W m⁻² K⁻¹, $\dot Q=14.91$ W | 39.74 and 14.90 W |
