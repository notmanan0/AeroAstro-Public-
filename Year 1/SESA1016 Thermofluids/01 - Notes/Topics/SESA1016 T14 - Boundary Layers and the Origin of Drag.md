---
title: "SESA1016 T14 - Boundary Layers and the Origin of Drag"
module: "SESA1016 Thermofluids"
type: topic
stream: "Part E: Viscous Losses"
order: 14
tags: [sesa1016, boundary-layer, drag, separation, transition]
aliases: ["Origin of Drag", "Boundary Layers"]
date: 2026-09-25
status: lectured
coverage: "Lecture of 1 May 2025 (ll. 13–542: pressure gradients and boundary layers, separation, aerofoil pressure distributions and stall, pressure drag on a cylinder, laminar and turbulent separation, the drag crisis, golf balls); Chapter 14 §§14.1–14.8 and §14.11 from the lecture notes, because the lectures of 28–29 Apr 2025 have no usable audio and §14.11 was left to the tutorial"
parent: ["[[SESA1016 Thermofluids Hub]]"]
prerequisites: ["[[SESA1016 T13 - Conservation of Energy and Propulsion]]", "[[SESA1016 T7 - Fluid Properties and Viscosity]]"]
next_topics: ["[[SESA1016 T15 - Flow in Conduits]]"]
key_concepts: ["[[Boundary-layer Thickness Measures]]", "[[Skin-friction and Pressure Drag]]", "[[Reynolds Number]]"]
tutorial_sheets: ["[[SESA1016 Problem Sheet 10 - Drag and External Flows Solutions]]"]
sources: ["02 - Sources/Lectures/Chapter 14.pdf", "02 - Sources/Lectures/SESA1016 Lecture 2025-05-01.txt", "02 - Sources/Tutorial Sheets/Problem Sheet 10 - Drag and Its Sources - External Flows.pdf"]
---

# SESA1016 T14 - Boundary Layers and the Origin of Drag

> [!abstract] Summary
> No-slip forces the flow to rest at a body's surface, and viscosity spreads that deceleration into a thin boundary layer whose thickness grows as $\delta\approx5\sqrt{\nu x/V_\infty}$ while laminar. Its thickness is measured robustly by the displacement thickness $\delta^*$ (mass-flow deficit) and momentum thickness $\theta$ (momentum deficit, giving a flat plate's drag as $2\rho V_\infty^2\theta$); its wall shear stress gives skin-friction drag. At $Re_x\approx5\times10^5$ it becomes turbulent, with a fuller profile. An adverse pressure gradient slows the near-wall fluid until $\tau_w=0$ and the layer separates, leaving a low-pressure wake and pressure drag; turbulent layers resist separation longer, which causes the drag crisis of cylinders and spheres.

> [!summary]- Exam use: quick path
> - **Use it when:** a boundary-layer thickness, displacement or momentum thickness, wall shear stress or friction coefficient is wanted; or drag must be found from a measured velocity profile or surface pressures; or you must explain separation, stall or the drag crisis.
> - **Assumptions:** flat plate at zero incidence (zero pressure gradient) unless stated; laminar for $Re_x<5\times10^5$; incompressible; 2D, unit width.
> - **Method:** 1. Compute $Re_x=V_\infty x/\nu$ and decide laminar or turbulent. 2. $\delta=5x/\sqrt{Re_x}$ for laminar. 3. For a measured profile, integrate $\delta^*=\int(1-u/V_\infty)dy$ and $\theta=\int(u/V_\infty)(1-u/V_\infty)dy$ by the trapezoidal rule. 4. Plate drag per unit width $D=2\rho V_\infty^2\theta$ (both sides) or $2\int\tau_w\,dx$. 5. For pressure drag, resolve $p\,dA$ on each face in the flow direction and sum.
> - **Common mistakes:** using $\delta_{99}$ when an integral thickness is asked for; forgetting the factor 2 for both sides of a plate.
> - **Practise:** [[#Worked example - momentum thickness and riblets]] · [[SESA1016 Problem Sheet 10 - Drag and External Flows Solutions]] Q10.1–Q10.3

Air is not very viscous, and treating it as inviscid explains lift ([[SESA1016 T10 - Euler and Bernoulli Equations|T10]]). But it cannot be inviscid right at a surface: the no-slip condition of [[SESA1016 T7 - Fluid Properties and Viscosity|T7]] holds the fluid touching the surface at rest, while a little way out the fluid moves at the free-stream speed. Between the two lies a thin layer where the velocity changes rapidly and viscous shear is large. That is the **boundary layer**, an idea introduced by Prandtl in 1904. Outside it the flow behaves as if inviscid; inside it viscosity rules.

The boundary layer is where drag comes from, in two ways. The shear stress it exerts on the surface, summed over the whole wetted area, is skin-friction drag; on a wing at small incidence that is most of the drag. And when the pressure rises along the surface, the slow fluid near the wall may not have the momentum to push into it: the layer stops, reverses and separates, leaving behind a wide wake of low pressure. The pressure difference between the front and the back of the body is pressure drag, and on a bluff body such as a cylinder it dominates.

A cylinder and an aerofoil 167 times longer can have the same drag at the same speed, the first almost all pressure drag and the second almost all skin friction. The aim of streamlining is to keep the boundary layer attached.

---

## 1. Flow past a flat plate

The standard geometry is a thin flat plate of length $L$ and unit width, at zero incidence to a stream of speed $V_\infty$ and kinematic viscosity $\nu$, with $x$ along the plate from the leading edge and $y$ normal to it, in the plate's frame. The **plate Reynolds number** is

$$
Re=\frac{V_\infty L}{\nu}
$$

A line of tracer (a timeline) released upstream shows the layer forming as it passes the plate. Far from the plate it moves on undisturbed. Near the plate it is held back: the fluid touching the plate sticks to it, and each layer above is slowed by the shear of the slower layer below. The deceleration spreads outwards from the plate as the fluid travels along it, so the slowed region, the boundary layer, thickens downstream, above and below the plate. Its edge is not a streamline; the streamlines are nearly horizontal. At the trailing edge the two layers merge into a **wake**, where viscosity still matters.

## 2. The velocity profile and its thickness

### The boundary-layer profile

At a station $x$, the streamwise velocity $v_x(y)$ rises from zero at the wall to $V_\infty$ far away:

$$
v_x(0)=0,\qquad v_x(\infty)=V_\infty
$$

where "$\infty$" means far enough from the wall, in practice a few millimetres. The second condition also implies $\partial v_x/\partial y=0$ outside the layer. The profile can be measured by traversing a probe (a stagnation tube, say) away from the wall.

### The 99 % thickness

The simplest thickness is where the velocity reaches a set fraction of the free stream, usually 99 %: $\delta_{99}$ is the $y$ at which $v_x=0.99V_\infty$ ($\delta_{95}$ and $\delta_{90}$ are also used). It depends on the profile at one point only, so two very different profiles can have the same $\delta_{99}$, one looking much thicker than the other. Integral measures, which use the whole profile, are more robust.

### Displacement thickness

Because the fluid in the boundary layer is slower than $V_\infty$, less mass flows past a station than would without the layer. The flow outside behaves as if the body were slightly fatter: the streamlines are displaced outwards. The mass-flow deficit per unit width is

$$
\int_0^\infty\rho\left[V_\infty-v_x(y)\right]dy
$$

Compare an inviscid flow at uniform $V_\infty$ right down to an apparent wall moved out by a distance $\delta^*$. Its deficit compared with uniform flow down to the real wall is a rectangle, $\rho V_\infty\delta^*$. Define $\delta^*$ by making the two deficits equal:

$$
\int_0^\infty\rho\left[V_\infty-v_x\right]dy=\rho V_\infty\delta^*
$$

With constant density, dividing by $\rho V_\infty$:

$$
\boxed{\delta^*=\int_0^\infty\left(1-\frac{v_x}{V_\infty}\right)dy}
$$

the **displacement thickness**: the distance the wall would have to move out so that a uniform inviscid flow carries the same mass flow as the real one. It is a length, smaller than $\delta_{99}$. The upper limit does not matter in practice, because the integrand vanishes outside the layer.

### Momentum thickness and drag

The momentum thickness comes from a control volume, and it directly gives the drag (Chapter 14, §14.3.2). Take the upper surface of the plate, unit width, and a control volume from upstream of the leading edge (inlet, height $h_1$, uniform $V_\infty$) to the trailing edge (outlet, height $h_2$, where the profile is $v_x(y)$), bounded above by a streamline well outside the layer. The streamline is deflected upwards slightly by the layer's blockage, so $h_2>h_1$.

![[tf_momentum_thickness_cv.png|900]]

No fluid crosses a streamline, so mass enters only at the inlet and leaves only at the outlet:

$$
\rho V_\infty h_1=\int_0^{h_2}\rho v_x\,dy
$$

The whole flow is at the ambient pressure, so the only force on the fluid is the shear from the plate, which acts upstream with magnitude $D_u$, the drag of the upper surface. Streamwise momentum:

$$
-D_u=\int_0^{h_2}\rho v_x\,v_x\,dy-\rho V_\infty V_\infty h_1
$$

Eliminate the unknown $h_1$ using the mass balance, $\rho V_\infty^2h_1=V_\infty\int_0^{h_2}\rho v_x\,dy$:

$$
-D_u=\int_0^{h_2}\rho v_x^2\,dy-V_\infty\int_0^{h_2}\rho v_x\,dy
$$

Change signs and combine:

$$
D_u=\int_0^{h_2}\rho v_x\left(V_\infty-v_x\right)dy
$$

the deficit of momentum flow caused by the viscous forces. As before, define a thickness: the **momentum thickness** $\theta$ is the thickness of a layer of fluid at $V_\infty$ whose momentum flow, $\rho V_\infty^2\theta$, equals this deficit:

$$
\boxed{\theta=\int_0^\infty\frac{v_x}{V_\infty}\left(1-\frac{v_x}{V_\infty}\right)dy}
$$

Then $D_u=\rho V_\infty^2\theta$ and, counting both sides of the plate,

$$
\boxed{D=2\rho V_\infty^2\theta}
$$

per unit width, with $\theta$ evaluated at the trailing edge. The whole history of the flow over the plate, its acceleration, deceleration and dissipation, ends up stored in the trailing-edge profile, which fixes the drag.

The **shape factor** compares the two thicknesses:

$$
H=\frac{\delta^*}{\theta}
$$

about 2.59 for a laminar flat-plate layer and 1.3–1.6 for a turbulent one; pressure gradients change it. In practice $\delta^*$ and $\theta$ are found by integrating measured profiles numerically, as in Problem Sheet 10.

## 3. Wall shear stress and skin friction

The velocity gradient $\partial v_x/\partial y$, the rate of shear strain, is largest at the wall and falls to zero at the edge of the layer. By Newton's law of viscosity the fluid exerts on the wall the shear stress

$$
\boxed{\tau_w=\mu\left.\frac{\partial v_x}{\partial y}\right|_{y=0}}
$$

tangential to the plate and in the direction of the stream. Divided by the free-stream dynamic pressure it gives the **local friction coefficient**

$$
c_f=\frac{\tau_w}{\tfrac12\rho V_\infty^2}
$$

Near the leading edge the layer is thin, so the velocity rises from zero to $V_\infty$ over a short distance: the gradient, and $\tau_w$, are large. Further downstream the layer is thicker and the gradient gentler, so $\tau_w$ falls along the plate. On an element of plate $dx$ (unit width) the shear force is $\tau_w\,dx$, and over both sides

$$
\boxed{D_v=2\int_0^L\tau_w(x)\,dx}
$$

Because $\tau_w$ is largest at the front, the front half of the plate produces more than half of the friction drag.

> [!check] How much more than half
> For a laminar layer $\delta\propto\sqrt x$, and with a fixed profile shape $\tau_w\approx\mu V_\infty f'(0)/\delta\propto x^{-1/2}$. Then $\int_0^{L/2}x^{-1/2}dx\big/\int_0^Lx^{-1/2}dx=\sqrt{1/2}=0.71$: the front half carries 71 % of the friction drag.

## 4. Laminar, turbulent and transition

### Laminar and turbulent boundary layers

In a **laminar** boundary layer the fluid moves in smooth layers, like the pages of a bent book, essentially only in the streamwise direction, with a small outward component as the layer thickens. It is steady and two-dimensional. Small disturbances, from surface roughness or eddies in the oncoming stream, are always present, but at low enough Reynolds number viscosity damps them.

In a **turbulent** boundary layer the motion is disordered, three-dimensional and unsteady, with significant vertical and spanwise velocities. The profile at a point changes from moment to moment, so engineers use the time-averaged (mean) profile for thicknesses and wall shear. Its striking feature is that it is **fuller**: for the same $\delta_{99}$ the velocity near the wall is much higher than in a laminar layer, because turbulent eddies carry fast fluid from the outer edge down towards the wall, far more effectively than viscosity alone. The steeper gradient at the wall gives higher skin friction.

![[tf_boundary_layers.png|900]]

### Transition

Define the **local Reynolds number**, a dimensionless distance from the leading edge,

$$
Re_x=\frac{V_\infty x}{\nu}
$$

which equals the plate Reynolds number at the trailing edge, $x=L$. Near the leading edge $Re_x$ is small and the layer is laminar. Further downstream, at a critical value

$$
Re_{x,cr}\approx5\times10^5
$$

viscosity can no longer damp small disturbances: the layer becomes unstable, the disturbances grow, and after a transitional region it becomes turbulent. The critical value is not exact. A rough surface or a gusty, turbulent oncoming stream brings transition forward.

## 5. Growth of the boundary layer

### Momentum diffusion

The growth of the layer follows from Stokes's first problem. A very long plate in still fluid is set moving along its length at speed $V$ at $t=t_0$. The fluid at the wall moves with the plate at once, by no-slip. Each layer then drags the layer above it through the shear stress $\tau=\mu\,\partial v_x/\partial y$, so the motion spreads outwards with time while the fluid far away stays still. The depth to which it has penetrated grows as

$$
\delta\sim\sqrt{\nu t}
$$

the square-root law of diffusion processes such as heat conduction. The controlling property is the kinematic viscosity $\nu=\mu/\rho$, not $\mu$: the shear stress scales with $\mu$, but the acceleration it produces scales with $1/\rho$. $\nu$ is the diffusivity of momentum.

### Laminar thickness on a fixed plate

On the fixed plate, fluid just outside the layer travels at $V_\infty$ and reaches a distance $x$ from the leading edge after a time $t=x/V_\infty$. In that time the deceleration has diffused out a distance of order $\sqrt{\nu t}=\sqrt{\nu x/V_\infty}$. A full analysis (Blasius's solution) fixes the constant:

$$
\boxed{\delta(x)=5\sqrt{\frac{\nu x}{V_\infty}}}
$$

Divide by $L$ and rearrange:

$$
\frac{\delta}{L}=5\sqrt{\frac{\nu}{V_\infty L}}\sqrt{\frac{x}{L}}=\frac{5}{\sqrt{Re}}\sqrt{\frac xL}
$$

and equivalently, $\delta=5x/\sqrt{Re_x}$. The layer is thinner at higher Reynolds number, because momentum diffuses slowly compared with how fast it is carried downstream; at aerospace Reynolds numbers the layer is a small fraction of the body's size, which is why inviscid methods work for lift. And the laminar layer grows as $\sqrt x$: quickly at first, then ever more slowly.

### Boundary layers on aerodynamic bodies

On an aerofoil at high Reynolds number, $Re=V_\infty c/\nu$, the flow divides into two regions. In the thin boundary layer, thickening from the leading edge, viscous forces dominate and the fluid is **rotational**: particles spin as well as translate, under shear. Bernoulli does not apply there. The boundary layers from the two surfaces merge at the trailing edge into the wake, also viscous. Outside them the fluid is still viscous but the motion is **irrotational**: particles stretch but do not rotate, so the net viscous force on a particle vanishes and only pressure forces act, and Bernoulli relates pressure and velocity. That outer region is where the inviscid theory of [[SESA1016 T10 - Euler and Bernoulli Equations|T10]] and second-year aerodynamics applies.

## 6. Pressure gradients and separation

### Zero, favourable and adverse pressure gradients

On a flat plate at zero incidence the pressure is everywhere $p_\infty$:

$$
\frac{\partial p}{\partial x}=0\qquad\text{(zero pressure gradient)}
$$

A fluid particle in the boundary layer feels equal pressure on its front and back, so only the viscous force acts on it, slowing it. On a body of finite thickness the pressure varies along the surface, imposed by the outer flow. The layer is so thin that it does not alter that pressure; locally it sees a flat wall with a pressure that rises or falls along it.

A pressure gradient is a force per unit volume: Pa/m = N/m³. So it pushes or holds back every particle in the layer.

The two cases arise for a flat plate in a wind tunnel whose walls converge or diverge. With **converging** walls the area falls, so by continuity the outer flow speeds up and by Bernoulli its pressure falls along the plate:

$$
\frac{\partial p}{\partial x}<0\qquad\text{(favourable pressure gradient)}
$$

The edge velocity $V_e$ rises. The pressure force pushes the near-wall fluid forwards, counteracting the viscous deceleration, so the profile becomes fuller near the wall, the wall gradient steeper, and $\tau_w$ rises. A favourable gradient is good for the layer.

With **diverging** walls the outer flow slows and the pressure rises:

$$
\frac{\partial p}{\partial x}>0\qquad\text{(adverse pressure gradient)}
$$

Fluid outside the layer can trade kinetic energy for pressure, but the slow fluid near the wall has little kinetic energy to trade, and now the pressure force acts against it as well as the viscous force. It slows further. The profile develops an inflection point (convex near the wall, concave above), the wall gradient falls and $\tau_w$ falls. A mild adverse gradient is survivable: the near-wall fluid is dragged along by the faster fluid above.

![[tf_pressure_gradient_bl.png|900]]

### Separation

If the adverse gradient is too strong, the near-wall fluid is brought to rest. At the point where

$$
\tau_w=0,\qquad\left.\frac{\partial v_x}{\partial y}\right|_{y=0}=0
$$

the profile leaves the wall vertically: this is the **separation point**. Beyond it the boundary layer lifts off the surface, and underneath it the higher pressure downstream drives a reversed flow back towards the separation point, a region of recirculation. Separated flow past ellipses, aerofoils and blunt shapes shows this (Album of Fluid Motion).

### Separation on aerofoils

The pressure distribution on an aerofoil is plotted as $C_p$ against $x/c$ with the $C_p$ axis reversed, suction upwards, as in XFOIL. $C_p=1$ at the stagnation point near the leading edge is the maximum possible. Over the front of the upper surface the flow accelerates and the pressure falls to a suction peak: a favourable gradient. Over the rear the pressure recovers towards the free-stream value: an adverse gradient. Separation, if it happens, happens there.

As the angle of attack rises, the suction peak grows and the adverse gradient behind it gets steeper. At some angle the layer separates near the trailing edge; at higher angles the separation point moves forward until the flow separates near the leading edge, and the aerofoil **stalls**: the lift drops. Separation also makes the flow unsteady, loading structures unsteadily, and generates noise.

## 7. Pressure drag

### The circular cylinder

A circular cylinder (a model for tall buildings, marine risers and other bluff, slender objects) shows pressure drag clearly. Measure the angle $\beta$ from the front. At $\beta=0$ there is a stagnation point and $C_p=1$. The flow accelerates round the sides and the pressure falls, to about $C_p=-3$ at $\beta=90°$ in inviscid theory ([[SESA1016 T10 - Euler and Bernoulli Equations#Worked example - flow round a cylinder|T10]]): a favourable gradient. In inviscid flow the pressure would recover symmetrically to $C_p=1$ at the back, and the net force would be zero.

In real flow, past about 90° the pressure rises, the adverse gradient separates the boundary layer from both sides, and a wide wake of recirculating flow at slightly below free-stream pressure forms behind. The front sees high pressure, the back low pressure: integrated over the surface, the net streamwise pressure force is the **pressure drag** $D_p$, and for a cylinder it is almost all of the drag.

![[tf_drag_separation.png|900]]

### Laminar and turbulent separation, and the drag crisis

A turbulent layer, with its fuller profile, has more momentum near the wall, so it can push further into an adverse pressure gradient before separating. If the boundary layer on the front of a cylinder stays laminar, it separates just after 90° and leaves a wide wake. If it becomes turbulent first, separation moves well back, the wake narrows, the low-pressure area on the back shrinks, and the pressure drag falls.

Which happens depends on the Reynolds number $Re=V_\infty d/\nu$. For a smooth cylinder or sphere there is a critical value, about $3$–$5\times10^5$, at which the layer turns turbulent before separating and $C_D$ drops by a factor of 4 or 5: the **drag crisis**. For a sphere, $C_D$ falls from about 0.45 to about 0.1.

Dimples on a golf ball disturb the laminar layer and trigger transition at a lower Reynolds number, so the drag crisis comes at a lower speed, within the range of a struck ball, and the ball flies further with lower drag. Early golf balls were smooth; players noticed that scuffed ones went further. For streamlined aerospace bodies the opposite applies: roughness brings forward transition, and with no large separation to suppress, the turbulent layer's higher skin friction and the drag of the roughness elements themselves only add drag. Hence flush rivets and smooth skins.

## 8. Calculating drag from surface data

### Pressure and shear on a surface element

Every aerodynamic force on a body comes from the pressure and shear stress over its wetted surface. Take a surface element $dA=ds\cdot1$ (unit span) inclined at angle $\theta$ to the free stream. The pressure force $p\,dA$ acts normal to it and the shear force $\tau\,dA$ along it. Resolving into the drag direction (along $V_\infty$) and the lift direction (normal to it):

$$
dD=-p\sin\theta\,dA+\tau\cos\theta\,dA
$$

$$
dL=-p\cos\theta\,dA-\tau\sin\theta\,dA
$$

and integrating over the whole surface,

$$
\boxed{D=\int_A\left(-p\sin\theta+\tau\cos\theta\right)dA=D_p+D_v}
$$

$$
L=\int_A\left(-p\cos\theta-\tau\sin\theta\right)dA=L_p+L_v
$$

with the pressure and viscous parts separated. For a streamlined aerofoil at low incidence, lift is almost all pressure ($L_v$ negligible) and drag mostly viscous ($D_v$ dominant). For bluff bodies, which separate early, as in most motorsport flows, pressure dominates both lift and drag. Only the pressure **difference** across the body matters, so gauge pressures can be used.

### Numerical integration

Measured or computed $p$ and $\tau$ are known only at discrete points, so the integrals are replaced by sums. With the rectangle rule, each point $i$ represents an element of area $\Delta A_i$ at angle $\theta_i$:

$$
D\approx\sum_{i=1}^N\left(-p_i\sin\theta_i+\tau_i\cos\theta_i\right)\Delta A_i
$$

---

## Worked examples

### Worked example - boundary layer at the end of a plate

A 1 m flat plate is in air at 10 m/s, $\nu=1.5\times10^{-5}$ m²/s. Estimate the boundary-layer thickness at the trailing edge, assuming laminar flow throughout (Chapter 14, Example 14.1).

$$
Re=\frac{V_\infty L}{\nu}=\frac{10\times1}{1.5\times10^{-5}}=6.67\times10^5
$$

$$
\delta_{99}(L)=\frac{5L}{\sqrt{Re}}=\frac{5}{816}=6.1\ \mathrm{mm}
$$

0.6 % of the plate length. ($Re$ slightly exceeds $5\times10^5$, so in practice transition would begin near the trailing edge.)

### Worked example - towed plate in water

A smooth plate 2 m long and 1 m wide is towed through water at 1.5 m/s. Find where $Re_x=5\times10^5$ and the laminar thickness there; what would roughening the surface do? (Problem Sheet 10, Q10.1, the tutorial problem.) Take $\nu=1.14\times10^{-6}$ m²/s for water at about 15 °C.

$$
x=\frac{Re_x\nu}{V_\infty}=\frac{5\times10^5\times1.14\times10^{-6}}{1.5}=0.38\ \mathrm m
$$

$$
\delta=\frac{5x}{\sqrt{Re_x}}=\frac{5\times0.38}{707}=2.69\ \mathrm{mm}
$$

Etching the surface would trigger transition earlier, giving a longer and thicker turbulent layer and more skin friction. The answer depends on $\nu$: with $10^{-6}$ m²/s (20 °C) it would be 0.33 m and 2.36 mm.

### Worked example - polynomial profile

A laminar profile is modelled as $u/U_\infty=2\eta+A\eta^3+B\eta^4+C$ with $\eta=y/\delta$. Find $A$, $B$, $C$, then $\delta^*/\delta$, $\theta/\delta$, and the wall shear for air at 20 °C, $U_\infty=30$ m/s, $\delta=1$ cm (Problem Sheet 10, Q10.2).

No-slip, $u(0)=0$, gives $C=0$. At the edge the velocity matches the free stream and the shear vanishes:

$$
f(1)=2+A+B=1,\qquad f'(1)=2+3A+4B=0
$$

so $A+B=-1$ and $3A+4B=-2$, giving $A=-2$, $B=1$:

$$
\frac{u}{U_\infty}=2\eta-2\eta^3+\eta^4
$$

Displacement thickness:

$$
\frac{\delta^*}{\delta}=\int_0^1\left(1-2\eta+2\eta^3-\eta^4\right)d\eta=1-1+\tfrac12-\tfrac15=\frac{3}{10}
$$

Momentum thickness, expanding $f(1-f)$ and integrating term by term:

$$
\frac{\theta}{\delta}=\int_0^1f(1-f)\,d\eta=\frac{37}{315}=0.117
$$

Wall shear, with $f'(0)=2$ and $\mu=1.81\times10^{-5}$ Pa s:

$$
\tau_w=\frac{\mu U_\infty}{\delta}f'(0)=\frac{2\times1.81\times10^{-5}\times30}{0.01}=0.109\ \mathrm{Pa}
$$

The shape factor is $H=0.3/0.117=2.55$, close to the exact laminar 2.59.

![[tf_q10_2_boundary_profile.png|900]]

### Worked example - displacement thickness from measurements

Velocities measured at the trailing edge of a plate in a 9.8 m/s stream are given below. Find $\delta^*$ (Problem Sheet 10, Q10.3, the sheet's worked solution).

| $y$ (mm) | 0 | 0.7 | 1.4 | 2.1 | 2.8 | 3.5 | 4.2 | 4.9 | 5.6 | 6.3 | 7.0 |
|---|---|---|---|---|---|---|---|---|---|---|---|
| $v_x$ (m/s) | 0 | 2.1 | 3.4 | 4.8 | 5.8 | 6.7 | 7.8 | 8.9 | 9.6 | 9.8 | 9.8 |

The integrand $1-v_x/V_\infty$ is zero for the last two points, so integrating to 7 mm is enough. The trapezoidal rule (`numpy.trapezoid(1 - vx/9.8, y)`) gives

$$
\delta^*=2.44\ \mathrm{mm}
$$

and the same data give $\theta=0.958$ mm and $H=2.55$, a laminar-like value. $\delta_{99}$ is about 5.5–6 mm, so $\delta^*<\delta_{99}$ as expected.

![[tf_bl_thickness_measures.png|900]]

### Worked example - momentum thickness and riblets

A flat plate is tested smooth and then covered with a riblet film, at the same speed. A stagnation tube traversed at the trailing edge feeds a water manometer; the readings $h$ are given below, with 9.8 mm in the free stream for both. Find the drag reduction (Problem Sheet 10, Q10.4).

| $y$ (mm) | 0 | 0.7 | 1.4 | 2.1 | 2.8 | 3.5 | 4.2 | 4.9 | 5.6 | 6.3 | 7.0 |
|---|---|---|---|---|---|---|---|---|---|---|---|
| $h_{base}$ (mm) | 0 | 1.1 | 2.4 | 4.3 | 5.7 | 6.7 | 7.8 | 8.9 | 9.6 | 9.8 | 9.8 |
| $h_{texture}$ (mm) | 0 | 1.2 | 2.6 | 4.8 | 5.9 | 6.9 | 8.2 | 9.2 | 9.8 | 9.8 | 9.8 |

The test section is at atmospheric pressure, so the probe reads the dynamic pressure $\tfrac12\rho_av_x^2=\rho_wgh$. Hence $v_x\propto\sqrt h$, and

$$
\frac{v_x}{V_\infty}=\sqrt{\frac{h}{h_\infty}}
$$

No densities are needed. The drag of a flat plate is $2\rho V_\infty^2\theta$, and $\rho$ and $V_\infty$ are the same in both runs, so the drag ratio is the ratio of momentum thicknesses. Trapezoidal integration gives $\theta_{base}=0.820$ mm and $\theta_{texture}=0.773$ mm:

$$
\text{drag reduction}=\frac{0.820-0.773}{0.820}=5.8\ \%
$$

> [!check] Free-stream speed
> On the day, $\rho_a=99\,355/(287\times291.15)=1.189$ kg/m³, and $h_\infty=9.8$ mm of water gives $V_\infty=\sqrt{2\rho_wgh_\infty/\rho_a}=12.7$ m/s, a plausible tunnel speed. It cancels from the answer.

### Worked example - pressure drag on a rectangular cylinder

A rectangular cylinder of thickness $H=0.32$ m faces the stream. The front face has 110 kPa at its centre (stagnation) falling linearly to 102 kPa at its edges; the back face is uniformly at 98 kPa. Find the drag per unit width (Problem Sheet 10, Q10.5, the sheet's worked solution).

The top and bottom faces are parallel to the stream and give no drag. On the front face the pressure is symmetric about the centreline, and on each half the force is the area of a trapezium:

$$
F_{front}=2\times\frac{p_{side}+p_{stag}}{2}\times\frac H2=2\times\frac{102\,000+110\,000}{2}\times0.16=33\,920\ \mathrm{N/m}
$$

$$
F_{back}=p_{back}H=98\,000\times0.32=31\,360\ \mathrm{N/m}
$$

$$
D_p=F_{front}-F_{back}=2560\ \mathrm{N/m}
$$

Using gauge pressures would give the same difference, since the atmospheric part cancels.

### Worked example - pressure drag on a diamond aerofoil

A diamond aerofoil of chord 0.12 m with a 27° angle at the leading and trailing edges is in a supersonic stream at 402.5 m/s, $\rho=1.34$ kg/m³, at zero incidence. Three taps per face each cover 0.02 m of chord; the mean gauge pressures on the upper surface are $-9250$, $-8900$, $-4500$ Pa on the rear face (taps 1–3) and 35 670, 49 010, 51 372 Pa on the front face (taps 4–6), with the lower surface symmetric. Find the pressure drag per unit width and $C_{dp}=D_p/(\tfrac12\rho V_\infty^2c)$ (Problem Sheet 10, Q10.6, the tutorial problem).

Each face is inclined at the half-angle $\varepsilon$ to the chord. A tap covering a chordwise length $\Delta x$ covers a face length $\Delta x/\cos\varepsilon$; the pressure acts normal to the face, and its streamwise component is

$$
p\,\frac{\Delta x}{\cos\varepsilon}\sin\varepsilon=p\,\Delta x\tan\varepsilon
$$

On the front face this points downstream (drag); on the rear face it points upstream, so suction there also adds drag. With both surfaces:

$$
D_p=2\tan\varepsilon\,\Delta x\left(\sum p_{front}-\sum p_{rear}\right)=2\tan\varepsilon\times0.02\times\left(136\,052+22\,650\right)
$$

The figure shows 27° as the angle between the upper and lower faces at the leading edge, so $\varepsilon=13.5°$:

$$
D_p=2\times0.2401\times0.02\times158\,702=1.52\ \mathrm{kN/m},\qquad C_{dp}=\frac{1524}{\tfrac12\times1.34\times402.5^2\times0.12}=0.117
$$

If 27° were instead the angle of each face to the chord, $\tan\varepsilon$ would be 0.510 and $D_p=3.23$ kN/m, $C_{dp}=0.248$ (the value in the solution note), but that would make the aerofoil 51 % thick.

### Worked example - horizontal buoyancy in a wind tunnel

A NACA 0015 wing of chord 0.6 m spans the 1.2 m height of a test section. Boundary layers on the tunnel walls make the core flow accelerate and its pressure fall along the tunnel. A Pitot tube on the empty tunnel's axis at 30 m/s gives water-manometer readings $h=54.9$, 55.6, 56.2, 57.0, 57.9, 58.5 mm at $x=-1$ to 1.5 m in steps of 0.5 m. Estimate the streamwise buoyancy force on the wing (Problem Sheet 10, Q10.7).

The Pitot tube reads the dynamic pressure, $q=\tfrac12\rho V^2=(\rho_w-\rho_a)gh$. In the inviscid core, Bernoulli keeps $p+q$ constant, so $p=\text{const}-q$. A least-squares straight line (`numpy.polyfit`) through $p(x)$ gives

$$
\frac{dp}{dx}=-14.4\ \mathrm{Pa/m}
$$

The wing's volume is its section area, about $0.103c^2$, times the span: $\mathcal V=0.103\times0.6^2\times1.2=0.0445$ m³. As in Archimedes' law ([[SESA1016 T8 - Hydrostatics#5. Archimedes' law|T8]]), a pressure gradient pushes on a body of volume $\mathcal V$ with force $-\mathcal V\,dp/dx$:

$$
F_b=-\frac{dp}{dx}\mathcal V=14.4\times0.0445=0.64\ \mathrm N
$$

acting downstream, to be subtracted from the balance reading. Diverging the tunnel walls slightly to allow for the growth of their boundary layers would remove the gradient.

---

## Links

- Parent: [[SESA1016 Thermofluids Hub]] · Previous: [[SESA1016 T13 - Conservation of Energy and Propulsion]] · Next: [[SESA1016 T15 - Flow in Conduits]]
- Concepts: [[Boundary-layer Thickness Measures]] · [[Skin-friction and Pressure Drag]] · [[Reynolds Number]] · [[Pressure Coefficient]] · [[Newtonian Fluid and Viscosity]]
- Worked sheet: [[SESA1016 Problem Sheet 10 - Drag and External Flows Solutions]] · Formula list: [[SESA1016 Formula Sheet]]
- Continues in: [[SESA2022 T2 - Boundary Layers]] (Blasius, momentum integral, transition) · [[SESA2029 A8 - Turbulence, RANS and Turbulence Models]]

## Sources

- `Chapter 14.pdf`: lecture notes Chapter 14, The origin of drag, §§14.1–14.11, Example 14.1, Figs 14.1–14.23.
- `SESA1016 Lecture 2025-05-01.txt` (1 May 2025): zero, favourable and adverse pressure gradients (ll. 13–187), separation (ll. 188–231), aerofoil pressure distributions and stall (ll. 232–302), cylinder pressure drag (ll. 303–394), laminar and turbulent separation and the drag crisis (ll. 395–475), cylinder against aerofoil (ll. 476–495), golf balls (ll. 496–516). §14.11 was left to the tutorial (ll. 518–530).
- The boundary-layer lectures of 28 and 29 Apr 2025 were recorded without usable audio (see the transcript index), so §§1–5 are written from the lecture notes.
- `Problem Sheet 10 - Drag and Its Sources - External Flows.pdf`: Q10.1–Q10.7, printed answers and worked solutions to Q10.3 and Q10.5.

## Self-study tasks

### Core

- [ ] Read §14.11 on calculating drag from surface pressure and shear (left to the tutorial, 1 May, ll. 518–530). → [[#8. Calculating drag from surface data]]
- [ ] Q10.1, towed plate in water (tutorial problem). Targets 2.69 mm, 0.38 m. → [[#Worked example - towed plate in water]]
- [ ] Q10.2, polynomial profile. Targets $A=-2$, $B=1$, $C=0$, $\delta^*/\delta=3/10$, $\theta/\delta\approx0.12$, 0.109 Pa. → [[#Worked example - polynomial profile]]
- [ ] Q10.3, displacement thickness from data (worked solution). Target 2.443 mm. → [[#Worked example - displacement thickness from measurements]]
- [ ] Q10.4, riblet drag reduction. Target 5.8 %. → [[#Worked example - momentum thickness and riblets]]
- [ ] Q10.5, rectangular cylinder (worked solution). Target 2560 N/m. → [[#Worked example - pressure drag on a rectangular cylinder]]
- [ ] Q10.6, diamond aerofoil (tutorial problem). → [[#Worked example - pressure drag on a diamond aerofoil]]
- [ ] Q10.7, horizontal buoyancy in a wind tunnel. Target 0.64 N. → [[#Worked example - horizontal buoyancy in a wind tunnel]]

### Further practice

- [ ] Derive $\delta^*$ and $\theta$ from mass and momentum deficits, and $D=2\rho V_\infty^2\theta$ from a control volume over the plate (Chapter 14, §14.3). → [[#Displacement thickness]] · [[#Momentum thickness and drag]]
- [ ] Explain, with sketches of the profile and $\tau_w(x)$, how favourable and adverse pressure gradients act on a boundary layer and why separation occurs where $\tau_w=0$ (1 May, ll. 69–218). → [[#Zero, favourable and adverse pressure gradients]] · [[#Separation]]
- [ ] Explain the drag crisis and why golf balls have dimples (1 May, ll. 395–516). → [[#Laminar and turbulent separation, and the drag crisis]]

## Transcript and slide slips

> [!warning] Lecture-notes slips (Chapter 14, §§14.3.2 and 14.6)
> Where: [[#Momentum thickness and drag]] · [[#Transition]].
>
> Before eq. 14.5, "mass conservation implies that the net outflow of momentum is zero" should read net outflow of mass, as eq. 14.5 shows. After eq. 14.18, "at the leading edge, $x=L$" should be the trailing edge.

> [!warning] Lecture-notes slip (Chapter 14, eq. 14.26)
> Where: [[#Laminar and turbulent separation, and the drag crisis]].
>
> The sphere drag coefficient is written $C_D=D/(\tfrac12\rho V_\infty^2d^2)$. Chapter 6 (eq. 6.57) and standard sphere data use the frontal area, $C_D=D/(\tfrac12\rho V_\infty^2\,\pi d^2/4)$; with $d^2$ the values would be smaller by $\pi/4$. The drag-crisis factor of about 5 is unaffected.

> [!warning] Problem-sheet ambiguity (Problem Sheet 10, Q10.6)
> Where: [[#Worked example - pressure drag on a diamond aerofoil]].
>
> "The angle $\theta$ at the leading and trailing edge is 27°" can be read as the included angle or as each face's angle to the chord. The figure marks $\theta$ between the upper and lower faces, the included angle, giving 1.52 kN/m and $C_{dp}=0.117$; no answer is printed to settle it.
