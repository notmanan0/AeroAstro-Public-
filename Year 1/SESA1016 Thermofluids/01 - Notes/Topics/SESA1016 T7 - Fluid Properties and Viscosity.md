---
title: "SESA1016 T7 - Fluid Properties and Viscosity"
module: "SESA1016 Thermofluids"
type: topic
stream: "Part B: Similarity and Fluid Fundamentals"
order: 7
tags: [sesa1016, fluid-properties, viscosity, compressibility]
aliases: ["Fluid Properties", "Viscosity"]
date: 2026-09-25
status: lectured
coverage: "Lecture of 3 Mar 2025 (ll. 1–642: what a fluid is, Couette flow and Newton's law of viscosity, Newtonian and non-Newtonian fluids, kinematic viscosity, molecular origin and temperature dependence of viscosity, bulk modulus and speed of sound); Chapter 7 in full"
parent: ["[[SESA1016 Thermofluids Hub]]"]
prerequisites: ["[[SESA1016 T6 - Dimensional Analysis and Similarity]]"]
next_topics: ["[[SESA1016 T8 - Hydrostatics]]"]
key_concepts: ["[[Newtonian Fluid and Viscosity]]", "[[Reynolds Number]]"]
tutorial_sheets: ["[[SESA1016 Problem Sheet 06 - Fluid Properties and Hydrostatics Solutions]]"]
sources: ["02 - Sources/Lectures/Chapter 7.pdf", "02 - Sources/Lectures/SESA1016 Lecture 2025-03-03.txt", "02 - Sources/Tutorial Sheets/Problem Sheet 06 - Fluid Properties and Hydrostatics.pdf"]
---

# SESA1016 T7 - Fluid Properties and Viscosity

> [!abstract] Summary
> A fluid is a substance that keeps deforming for as long as a shear stress acts on it; a solid deforms by a fixed amount and stops. For a Newtonian fluid the shear stress is proportional to the rate of shear strain, $\tau=\mu\,dv/dy$, with the dynamic viscosity $\mu$ as the constant; between a moving and a fixed plate this gives the linear Couette profile. Density, the bulk modulus (which fixes the speed of sound, $c^2=E_v/\rho$) and the kinematic viscosity $\nu=\mu/\rho$ complete the properties used in the rest of the module. Gas viscosity rises with temperature (Sutherland's law) while liquid viscosity falls.

> [!summary]- Exam use: quick path
> - **Use it when:** a plate, shaft or block slides on a thin fluid film; you need a viscous force or stress; you compare how compressible or viscous two fluids are; or you need $\mu(T)$ for air.
> - **Assumptions:** Newtonian fluid, no-slip at every wall, thin gap with a linear (Couette) profile and no pressure gradient, steady motion.
> - **Method:** 1. Sketch the velocity profile with no-slip at each surface. 2. Velocity gradient $dv/dy=V/h$ for a thin film. 3. $\tau=\mu\,dv/dy$. 4. Force $F=\tau A$ (torque $=$ force × radius for a rotating shaft). 5. Check units: Pa s × s⁻¹ = Pa.
> - **Common mistakes:** confusing $\mu$ (Pa s) with $\nu$ (m²/s); taking the fluid speed at a moving wall as zero instead of the wall speed.
> - **Practise:** [[#Worked example - plate sliding on a fluid film]] · [[SESA1016 Problem Sheet 06 - Fluid Properties and Hydrostatics Solutions]] Q6.1

The difference between a solid, a liquid and a gas is the strength of the bonds between molecules. In a gas the molecules are far apart and interact only by colliding, so a gas fills whatever space it is given and has a low density. In a liquid they are close together with significant bonds between them, so a liquid has a much higher density and its volume hardly changes, but the molecules can still move past each other. In a solid they are packed into a fixed structure by strong bonds.

Gases and liquids together are fluids, and what they share is that they flow. Push sideways on the top of a block of rubber and it leans over by a fixed amount and stops; push on the top of a layer of oil and the top keeps moving for as long as you push. A solid resists being deformed; a fluid resists only the rate at which it is deformed, and the property that measures that resistance is the viscosity.

Viscosity is small in air, but it acts over the whole surface of a fuselage and wings, and it is the origin of skin-friction drag, a substantial part of the fuel bill of every airliner (3 Mar, ll. 171–176). Its microscopic origin, molecules carrying momentum between layers moving at different speeds, also explains why air becomes more viscous when heated while oil becomes less.

---

## 1. What is a fluid

### Solid and fluid between two plates

A layer of material of thickness $h$ lies between two parallel plates. The bottom plate is held still and a force $F$ is applied to the top plate; two points that start one above the other on the two plates mark the deformation (3 Mar, ll. 62–113).

If the material is a solid, the top plate moves a distance $l$ and stops when the internal stresses balance $F$. The ratio $l/h$ is the **shear strain**, and for an elastic solid it is proportional to the applied force:

$$
\frac{l}{h}\propto F
$$

If the material is a fluid, the top plate keeps moving as long as the force acts: at time $t_1$ it has moved $l_1$, at a later $t_2$ it has moved $l_2>l_1$, and so on. The strain grows without limit, so the useful quantity is how fast it grows. The plate speed is

$$
V=\frac{dl}{dt}
$$

and since $h$ is constant the **rate of shear strain** is

$$
\frac{d(l/h)}{dt}=\frac{1}{h}\frac{dl}{dt}=\frac{V}{h}
$$

For a fluid it is this rate that is proportional to the force:

$$
\frac{dl}{dt}\propto F
$$

A fluid can take up any shape at rest without internal stress, but it cannot resist a shear stress without moving. Fluids also transfer heat more effectively than solids, because density differences set up convective motion that carries thermal energy bodily, while a solid can conduct heat only at the molecular level.

## 2. Density and specific gravity

The **density** is mass per unit volume,

$$
\rho=\frac{m}{V}\doteq[M][L]^{-3}
$$

in kg/m³. Air at room temperature has $\rho\approx1.2$ kg/m³ and water about 1000 kg/m³. The density of a gas changes strongly with temperature and pressure ($\rho=p/RT$); that of a liquid changes only weakly with temperature and hardly at all with pressure.

For liquids the **specific gravity** is often quoted:

$$
S=\frac{\rho}{\rho_{water}}
$$

with $\rho_{water}=1000$ kg/m³ (water at 4 °C). A liquid with $S<1$, such as an oil with $S=0.8$–0.9, is lighter than water and floats on it.

## 3. Compressibility: the bulk modulus

### Definition

All fluids are compressible, but liquids much less than gases because their molecules are already close together. Let a fluid of volume $V$ sit in a cylinder closed by a piston of area $A$. A force $F$ on the piston raises the pressure by $\Delta p=F/A$ and moves the piston by $\Delta h<0$, so the volume changes by $\Delta V=A\,\Delta h<0$. The **bulk modulus of elasticity** is the pressure rise divided by the fractional volume change it causes:

$$
\boxed{E_v=-\frac{\Delta p}{\Delta V/V}=-\frac{\Delta p}{\Delta v/v}}
$$

The minus sign makes $E_v$ positive, since compression reduces the volume. $E_v$ has the dimensions of pressure. It plays the same role as Young's modulus in solid mechanics: stress over strain, with $\Delta p$ as the stress and $\Delta V/V$ as the strain. The same definition holds per unit mass, because $V/m=v$ and the mass cancels in $\Delta V/V$.

For water, $E_v\approx2.2$ GPa. Doubling the pressure of water from atmospheric, $\Delta p=10^5$ Pa:

$$
\frac{\Delta V}{V}=-\frac{\Delta p}{E_v}=-\frac{10^5}{2.2\times10^9}=-4.5\times10^{-5}
$$

a change of 0.0045 %. That is why liquids are usually treated as **incompressible**: their density is effectively constant, and it depends more on temperature than on pressure (3 Mar, ll. 589–607).

### Speed of sound

Small pressure disturbances travel through a fluid at the speed of sound $c$, given by

$$
\boxed{c^2=\frac{E_v}{\rho}}
$$

a result from continuum mechanics, quoted here without proof. A stiffer fluid (larger $E_v$) or a lighter one carries sound faster. For water,

$$
c=\sqrt{\frac{2.2\times10^9}{997}}=1485\ \mathrm{m/s}
$$

For a gas the bulk modulus follows from the process the gas goes through as the wave passes. Sound waves are fast enough to be adiabatic and gentle enough to be reversible, so $pv^\gamma=$ const. Differentiate:

$$
v^\gamma\,dp+\gamma pv^{\gamma-1}\,dv=0
$$

Divide by $v^\gamma$:

$$
dp=-\gamma p\frac{dv}{v}
$$

so

$$
E_v=-\frac{dp}{dv/v}=\gamma p
$$

Then $c^2=\gamma p/\rho=\gamma RT$. For air at 20 °C,

$$
c=\sqrt{1.4\times287\times293.15}=343\ \mathrm{m/s}
$$

the familiar 340 m/s (3 Mar, l. 627). Air's bulk modulus at atmospheric pressure is only $1.4\times101\,325=1.4\times10^5$ Pa, about 15 000 times smaller than water's, which is why gases are compressible and liquids nearly not. The compressibility of gases becomes important in shock waves.

> [!check] Why not the isothermal value
> If the gas were compressed isothermally, $pv=$ const would give $E_v=p$ and $c=\sqrt{RT}=290$ m/s, 15 % below the measured speed of sound. The measured value supports the isentropic model.

## 4. Viscosity

### Couette flow and the no-slip condition

Fluid between two plates a distance $h$ apart, with the bottom plate fixed and the top plate moving at $V$, is in **Couette flow**, named after Maurice Couette, one of the founders of rheology, the measurement of how fluids deform (3 Mar, ll. 114–127). $y$ is measured upwards from the bottom plate.

The layer of fluid touching each plate moves with that plate. Close up, the plate surface is a lattice of molecules, and fluid molecules near it interact strongly enough with them to be held at the plate's velocity. This is the **no-slip condition**: the velocity of the fluid relative to a solid surface in contact with it is zero (3 Mar, ll. 205–222). The emphasis is on relative velocity. At the fixed bottom plate the fluid is at rest; at the moving top plate it moves at $V$:

$$
v(0)=0,\qquad v(h)=V
$$

### The linear velocity profile

Between the plates the velocity varies from 0 to $V$. It varies linearly, as a force balance shows. Consider a thin layer of fluid between heights $y$ and $y+dy$ in steady flow, with no pressure difference along the plates. The fluid above drags the layer forward with a shear stress $\tau(y+dy)$ on its top face, and the slower fluid below holds it back with $\tau(y)$ on its bottom face. The layer is not accelerating, so per unit area

$$
\tau(y+dy)-\tau(y)=0
$$

$$
\frac{d\tau}{dy}=0
$$

and the shear stress is the same at every height. With Newton's law of viscosity (below), $\tau=\mu\,dv/dy$, a constant $\tau$ means a constant velocity gradient, so the profile is a straight line, $v=ay+b$. The no-slip conditions fix the constants: $v(0)=0$ gives $b=0$ and $v(h)=V$ gives $a=V/h$. So

$$
\boxed{v(y)=V\frac{y}{h}}
$$

![[tf_couette_flow.png|900]]

The velocity gradient is

$$
\frac{dv}{dy}=\frac{V}{h}
$$

which equals the rate of shear strain $d(l/h)/dt$ found in §1. The velocity gradient is the general measure of how fast neighbouring layers of fluid are being deformed, and in Couette flow every layer is sheared at the same rate (3 Mar, ll. 230–237).

### Newton's law of viscosity

Couette's experiments showed that the force needed to drive the top plate is proportional to its area $A$ and to its speed, and inversely proportional to the gap:

$$
\boxed{F=\mu\frac{AV}{h}}
$$

A larger plate drags more fluid; a thicker layer is easier to shear. The constant $\mu$ depends only on the fluid and is the **dynamic viscosity**. Divide by $A$ and write the general velocity gradient in place of $V/h$:

$$
\boxed{\tau=\mu\frac{dv}{dy}}
$$

This is **Newton's law of viscosity**. $\tau=F/A$ is a **shear stress**, a force per unit area acting tangentially, produced by shearing the fluid. It acts on the top plate (the fluid holds it back, so the force $F$ is needed to keep it moving) and equally on the bottom plate (the fluid drags it forward).

The units of $\mu$ follow from $\mu=\tau/(dv/dy)$: Pa divided by s⁻¹, so Pa s, with dimensions $[M][L]^{-1}[T]^{-1}$. The name "dynamic" comes from the Greek for force and is a reminder that the units contain a newton, or a kilogram. Typical values at room temperature are $\mu=1.8\times10^{-5}$ Pa s for air and $8.9\times10^{-4}$ Pa s for water, about 50 times larger. Gases are much less viscous than liquids, but they are viscous.

### Newtonian and non-Newtonian fluids

Newton's law says shear stress is proportional to shear rate. To measure $\mu$, shear the fluid at several known rates, measure the stress needed, and plot one against the other: the points lie on a straight line through the origin whose slope is $\mu$, steeper for honey than for water (3 Mar, ll. 262–277). Fluids that behave this way are **Newtonian**: air, water and oils.

![[tf_rheology_curves.png|900]]

Many fluids are not. In a **shear-thickening** (dilatant) fluid the stress rises faster than linearly with shear rate. A mixture of corn starch and water can be stirred slowly with a stick, but resists strongly if stirred fast; quicksand behaves similarly. In a **shear-thinning** (pseudo-plastic) fluid the stress rises more slowly than linearly, so the fluid becomes easier to move once it is moving fast; ketchup is the standard example. Air and water are Newtonian, and every fluid in this module is treated as Newtonian.

### Kinematic viscosity

The **kinematic viscosity** is the dynamic viscosity divided by the density:

$$
\boxed{\nu=\frac{\mu}{\rho}}
$$

Its units are (Pa s)/(kg m⁻³) = m²/s, with no mass in them, hence "kinematic". It looks like the units of acceleration with the square moved to the numerator.

| Fluid | $\mu$ (Pa s) | $\nu$ (m²/s) | $\rho$ (kg/m³) |
|---|---|---|---|
| Air | $1.8\times10^{-5}$ | $1.5\times10^{-5}$ | 1.20 |
| Water | $8.9\times10^{-4}$ | $8.9\times10^{-7}$ | 997 |

Water is about 50 times more viscous than air, but because it is about 830 times denser its kinematic viscosity is about 17 times smaller.

The meaning of $\nu$ is clearest from an experiment (3 Mar, ll. 322–407). Two identical round tanks, one of water and one of air (with smoke to make it visible), are stirred until the swirling motion has the same speed $V_0$. Friction against the fixed walls then slows each one down. Water has the larger viscous force, since that is proportional to $\mu$, but it also has a much larger mass to decelerate, proportional to $\rho$. By Newton's second law the deceleration goes as force over mass, so as $\mu/\rho=\nu$. Air, with the larger $\nu$, slows down faster, and the swirl in the water persists much longer.

Under suitable conditions the velocity decays exponentially,

$$
V(t)=V_0\,e^{-\nu t/R^2}
$$

where $R$ is the radius of the tank. The time for the motion to halve is $t_{1/2}=R^2\ln2/\nu$: proportional to $1/\nu$, and longer in a larger tank. Eddies and vortices therefore survive much longer in water than in air.

![[tf_viscous_decay.png|900]]

### Molecular origin of viscosity

The mechanism is different in gases and liquids, because their molecules are arranged differently (3 Mar, ll. 412–489).

In a gas, take two adjacent layers moving at $V'$ and $V$, with $V'>V$. On top of their bulk motion the molecules move randomly in all directions. Some molecules from the fast layer wander into the slow layer, carrying on average more forward momentum than the molecules there; their collisions speed the slow layer up. Molecules from the slow layer wander into the fast one and slow it down. The net effect is a transfer of momentum from fast fluid to slow, called **molecular diffusion of momentum**, which smooths out the velocity difference over time. Viscosity is the macroscopic name for this. The molecular motions happen over the mean free path, far smaller than the scale of any velocity difference of interest, so the fluid can still be treated as a continuum with $\mu$ as a property. The same process at a wall, where fluid molecules lose momentum in collisions with the atoms of the surface, appears macroscopically as the wall shear stress.

In a liquid the molecules are packed closely and held by intermolecular forces (hydrogen bonds, van der Waals forces). When one layer moves, the bonds pull its neighbours along with it, and this resistance is the liquid's viscosity. Stronger bonds mean higher viscosity.

### Effect of temperature

The two mechanisms respond to temperature in opposite ways.

Heating a gas makes its molecules move faster, so they travel further and more often between layers, and momentum is exchanged more effectively: the viscosity of a gas **rises** with temperature. It is well described by **Sutherland's law**,

$$
\boxed{\mu=\mu_0\left(\frac{T}{T_0}\right)^{3/2}\frac{T_0+S}{T+S}}
$$

where $\mu_0$ is the viscosity at a reference temperature $T_0$ and $S$ is a constant for the gas. For air, $S=111$ K and $\mu_0=1.825\times10^{-5}$ Pa s at $T_0=293.15$ K (20 °C). In the ideal-gas picture pressure does not change the molecular agitation, so viscosity depends only weakly on pressure.

Heating a liquid makes its molecules vibrate more strongly, which weakens the bonds relative to the thermal motion, so the viscosity of a liquid **falls** with temperature. Oil spreading more easily in a hot pan is this effect. A common model is

$$
\mu=a\,e^{b/T}
$$

with $a$ and $b$ fitted to measurements for each liquid.

![[tf_sutherland_viscosity.png|900]]

> [!check] Air across an airliner's temperature range
> From Sutherland's law with the course constants: $\mu=1.43\times10^{-5}$ Pa s at the ISA tropopause (216.65 K), $1.80\times10^{-5}$ at ISA sea level (288.15 K) and $1.92\times10^{-5}$ on a 40 °C runway. The viscosity changes by about 35 % over that range, but the kinematic viscosity changes much more, because the density at 11 km is less than a third of sea level: $\nu=3.9\times10^{-5}$ m²/s at cruise against $1.5\times10^{-5}$ at sea level.

---

## Worked examples

### Worked example - plate sliding on a fluid film

A plate of area 0.5 m² slides at 1 m/s over a fixed surface, separated by a 1 mm film. Find the shear stress and the force needed for a film of water and for a film of air (suggested example on §7.5).

With no-slip at both surfaces and a thin film, the profile is linear and $dv/dy=V/h=1/0.001=1000$ s⁻¹. For water:

$$
\tau=\mu\frac{dv}{dy}=8.9\times10^{-4}\times1000=0.89\ \mathrm{Pa}
$$

$$
F=\tau A=0.89\times0.5=0.45\ \mathrm N
$$

For air, $\tau=1.8\times10^{-5}\times1000=0.018$ Pa and $F=0.009$ N, 50 times less. Halving the gap would double both forces.

### Worked example - compressing water

Water at atmospheric pressure is pressurised by an extra 1 bar. Find the fractional volume change and the speed of sound (3 Mar, ll. 589–625).

$$
\frac{\Delta V}{V}=-\frac{10^5}{2.2\times10^9}=-4.5\times10^{-5}\quad(0.0045\ \%)
$$

$$
c=\sqrt{\frac{E_v}{\rho}}=\sqrt{\frac{2.2\times10^9}{997}}=1.49\ \mathrm{km/s}
$$

about 4.3 times the speed of sound in air.

### Worked example - viscosity of air for an airliner

Plot the dynamic viscosity of air over the temperatures an airliner meets anywhere on Earth, from take-off to cruise (Problem Sheet 6, Q6.1).

A sensible range is from about 200 K (cold upper atmosphere) to about 330 K (a hot desert runway). Evaluating Sutherland's law with $\mu_0=1.825\times10^{-5}$ Pa s, $T_0=293.15$ K and $S=111$ K across that range gives the curve in the figure in §4, rising from about $1.3\times10^{-5}$ to $2.0\times10^{-5}$ Pa s. The equivalent reference $\mu_0=1.716\times10^{-5}$ Pa s at 273.15 K (used in the solution note) agrees to within 0.7 %.

---

## Links

- Parent: [[SESA1016 Thermofluids Hub]] · Previous: [[SESA1016 T6 - Dimensional Analysis and Similarity]] · Next: [[SESA1016 T8 - Hydrostatics]]
- Concepts: [[Newtonian Fluid and Viscosity]] · [[Reynolds Number]] · [[Ideal-gas Law]]
- Worked sheet: [[SESA1016 Problem Sheet 06 - Fluid Properties and Hydrostatics Solutions]] (Q6.1) · Formula list: [[SESA1016 Formula Sheet]]
- Used again in: [[SESA1016 T9 - Describing Flow and the Material Derivative|T9]] (shear between plates) · [[SESA1016 T14 - Boundary Layers and the Origin of Drag|T14]] (wall shear stress and skin friction) · [[SESA1016 T15 - Flow in Conduits|T15]] (laminar pipe flow)

## Sources

- `Chapter 7.pdf`: lecture notes Chapter 7, Properties of fluids, §§7.1–7.5, Table 7.1, Figs 7.1–7.8.
- `SESA1016 Lecture 2025-03-03.txt` (3 Mar 2025): states of matter (ll. 33–60), solid and fluid between plates (ll. 61–113), Couette flow and Newton's law (ll. 114–256), non-Newtonian fluids (ll. 257–304), kinematic viscosity and the two tanks (ll. 305–407), molecular origin (ll. 408–489), temperature dependence (ll. 490–549), bulk modulus and speed of sound (ll. 550–640).
- `Problem Sheet 06 - Fluid Properties and Hydrostatics.pdf`: Q6.1 (the rest of the sheet belongs to [[SESA1016 T8 - Hydrostatics|T8]]).

## Self-study tasks

### Core

- [ ] Q6.1, plot $\mu(T)$ for air with Sutherland's law over an airliner's temperature range (Problem Sheet 6; also set at 3 Mar, ll. 523–527). → [[#Worked example - viscosity of air for an airliner]] · [[SESA1016 Problem Sheet 06 - Fluid Properties and Hydrostatics Solutions]]
- [ ] Work out the force needed to double atmospheric pressure in a water-filled cylinder and the resulting volume change (left to you at 3 Mar, ll. 591–598). → [[#Worked example - compressing water]]
- [ ] Use $c^2=E_v/\rho$ to estimate the speed of sound in water (3 Mar, ll. 624–625). Target about 1.5 km/s. → [[#Speed of sound]]

### Further practice

- [ ] Derive the linear Couette profile from a force balance on a fluid layer (the lecture states the result without proof, 3 Mar, ll. 224–227). → [[#The linear velocity profile]]
- [ ] Explain, using Newton's second law, why a swirl in water outlasts the same swirl in air although water is 50 times more viscous. → [[#Kinematic viscosity]]
- [ ] Explain from the molecular picture why gas viscosity rises and liquid viscosity falls with temperature. → [[#Effect of temperature]]

## Transcript and slide slips

> [!warning] Transcript slips on units (3 Mar, ll. 140 and 317)
> Where: [[#Newton's law of viscosity]] · [[#Kinematic viscosity]].
>
> The unit of $\mu$ is read as "Pascal per second"; it is pascal second, Pa s (pressure times time, as l. 141 says). The unit of $\nu$ is read as "meter second squared"; it is m²/s.

> [!warning] Transcript slip (3 Mar, ll. 401–402)
> Where: [[#Kinematic viscosity]].
>
> "$\nu$ for water is about 1/7th of $\nu$ for air." From Table 7.1 the ratio is $8.9\times10^{-7}/1.5\times10^{-5}=1/17$.

> [!warning] Transcript slip (3 Mar, ll. 624–625)
> Where: [[#Speed of sound]].
>
> The speed of sound in water is given as "about three or four or five kilometres per second". With $E_v=2.2$ GPa and $\rho=997$ kg/m³, $c=1.49$ km/s.

> [!warning] Lecture-notes slip (Chapter 7, §7.5.2 and Table 7.1)
> Where: [[#Kinematic viscosity]].
>
> The text after Table 7.1 says "air is definitely more viscous". It is water that has the higher dynamic viscosity (50 times air's); air has the higher kinematic viscosity. The surrounding sentences make clear that this is what was meant.

> [!warning] Lecture-notes slip (Chapter 7, eq. 7.12)
> Where: [[#Kinematic viscosity]].
>
> $V(t)=V_0e^{-\nu t}$ is not dimensionally homogeneous: $\nu t$ has units of m², so the exponent is not dimensionless. A length scale of the tank is missing, $V=V_0e^{-\nu t/R^2}$ with $R$ the tank radius. The conclusion that the decay time scales with $1/\nu$ is unchanged.

> [!warning] Lecture-notes slip (Chapter 7, captions of Figs 7.4 and 7.7)
> Where: [[#Couette flow and the no-slip condition]].
>
> The caption of Fig. 7.4 (Couette flow) is copied from the continuum figure in Chapter 1 ("container filled with a gas … mass density as a function of the sample volume"), and Fig. 7.7(b) is described as the effect of temperature on viscosity when it shows the smoothing of a velocity jump. The text describes both figures correctly.
