---
title: "SESA1016 T8 - Hydrostatics"
module: "SESA1016 Thermofluids"
type: topic
stream: "Part B: Similarity and Fluid Fundamentals"
order: 8
tags: [sesa1016, hydrostatics, pressure, manometer, atmosphere]
aliases: ["Fluids at Rest", "Stevin's law"]
date: 2026-09-25
status: lectured
coverage: "Lectures of 4 Mar 2025 (ll. 1–628: pressure, Pascal's law, hydraulic jack, Stevin's law, liquids, the hydrostatic paradox, Archimedes) and 6 Mar 2025 (ll. 1–564: Archimedes for general shapes, barometer, manometer, isothermal and lapse-rate atmospheres); Chapter 8 in full"
parent: ["[[SESA1016 Thermofluids Hub]]"]
prerequisites: ["[[SESA1016 T7 - Fluid Properties and Viscosity]]"]
next_topics: ["[[SESA1016 T9 - Describing Flow and the Material Derivative]]"]
key_concepts: ["[[Pressure and Head]]", "[[Ideal-gas Law]]"]
tutorial_sheets: ["[[SESA1016 Problem Sheet 06 - Fluid Properties and Hydrostatics Solutions]]"]
sources: ["02 - Sources/Lectures/Chapter 8.pdf", "02 - Sources/Lectures/SESA1016 Lecture 2025-03-04.txt", "02 - Sources/Lectures/SESA1016 Lecture 2025-03-06.txt", "02 - Sources/Tutorial Sheets/Problem Sheet 06 - Fluid Properties and Hydrostatics.pdf"]
---

# SESA1016 T8 - Hydrostatics

> [!abstract] Summary
> In a fluid at rest, pressure is a normal stress that acts equally in all directions at a point. Without gravity it is the same everywhere (Pascal's law), which is how a hydraulic jack multiplies force. With gravity, a force balance on a thin slab gives Stevin's law, $dp/dz=-\rho g$: pressure depends only on height, falling linearly in a liquid, $p=p_0-\rho gz$. The same balance explains buoyancy (Archimedes, $U=\rho g\mathcal V$), the barometer, the manometer, and, combined with $p=\rho RT$, the exponential and lapse-rate pressure profiles of the atmosphere.

> [!summary]- Exam use: quick path
> - **Use it when:** pressures at different heights in a still liquid or gas are linked (tanks, manometers, barometers, bubble tubes), a body floats or sinks, or the pressure and density at altitude are needed.
> - **Assumptions:** fluid at rest; constant $\rho$ for a liquid; $g$ constant; for the atmosphere, ideal gas with a given $T(z)$.
> - **Method:** 1. Choose the direction of $z$ and mark it. 2. Start at a point of known pressure (a free surface, $p_{atm}$). 3. Move through each fluid in turn, adding $\rho g\,\Delta(\text{depth})$ going down and subtracting going up; moving horizontally within one connected fluid changes nothing. 4. Equate at the target point. 5. Convert between gauge and absolute pressure at the end.
> - **Common mistakes:** the sign of $\Delta z$ (pressure always rises in the direction of $\vec g$); using one density across an interface between two fluids.
> - **Practise:** [[#Worked example - oil and water in a tank]] · [[SESA1016 Problem Sheet 06 - Fluid Properties and Hydrostatics Solutions]] Q6.3, Q6.8

A fluid at rest can only push on a surface. It cannot pull, and with nothing moving there is no shear stress, so the only stress left is pressure, acting perpendicular to every surface it touches. A diver therefore feels the water pressing from every side, not just from above, and a submarine is squeezed all round, not crushed from the top by the weight of the water overhead.

Gravity adds structure. Each layer of fluid has to hold up the weight of everything above it, so pressure grows downwards at a rate given by the force balance on a thin slab. In a liquid the density is constant, so pressure rises linearly with depth, about one atmosphere for every 10 m of water. In the atmosphere the density itself falls as the pressure falls, so the decrease with height is exponential in an isothermal layer and a power law where the temperature falls steadily.

The same balance answers practical questions: why a blimp floats, how Torricelli weighed the atmosphere with a tube of mercury, how a U-tube of coloured water measures the pressure on an aerofoil in a wind tunnel, and how thin the air is at the top of Everest or at airliner cruise altitude.

---

## 1. Describing pressure

### Pressure is a normal stress

In a fluid a force applied at a single point has little meaning; forces act over surfaces, so the useful quantity is a stress. The shear stress $\tau$ of [[SESA1016 T7 - Fluid Properties and Viscosity|T7]] acts tangentially. **Pressure** is the stress that acts normal to a surface, and on an area $A$ it produces a force

$$
F=pA
$$

perpendicular to the surface and always compressive, pushing towards it. Pressure and shear stress are the only two ways a fluid can act on a surface, so every aerodynamic force, lift and drag included, is built from them.

### Absolute and gauge pressure

**Absolute pressure** is the thermodynamic pressure of the ideal-gas law: zero in a perfect vacuum and never negative. **Gauge pressure** is measured relative to a reference, usually the local atmosphere, and can be negative, which just means below the reference. A bicycle tyre at 60 psi (about 4.14 bar) on the pump gauge is 60 psi above atmospheric. See also [[SESA1016 T1 - Thermodynamic Systems, Properties and State#Units, absolute temperature and absolute pressure|T1]].

## 2. Pascal's law

### Pressure is the same everywhere without gravity

Ignore gravity for the moment and push with force $F$ on a piston of area $A$ in the neck of a sealed container of fluid. **Pascal's law** says a pressure $p=F/A$ is set up and is the same at every point in the fluid, and that it acts normal to the walls. On any small element of wall of area $\Delta A$ the force is $\Delta F$, with

$$
\lim_{\Delta A\to0}\frac{\Delta F}{\Delta A}=p
$$

The force must be normal to the wall. The wall pushes on the fluid with a force equal and opposite to the fluid's push on the wall; if that force had a component along the wall, the fluid at rest would be sheared, and a fluid cannot resist shear without moving.

### Pressure does not depend on orientation

A small triangular prism of fluid has two faces of side $L$ at right angles, a hypotenuse face of side $\sqrt2L$, and depth $d$, still ignoring gravity. The pressures on the three faces are $p$ (horizontal face), $p'$ (hypotenuse) and $p''$ (vertical face). The prism stays put, so the forces on it balance. The hypotenuse is at 45°, so the vertical component of its pressure force is $p'\sqrt2Ld\cos45°=p'Ld$. Vertically:

$$
pLd-p'\sqrt2Ld\cos45°=0
$$

$$
pLd-p'Ld=0
$$

$$
p=p'
$$

Horizontally, the same argument with $\sin45°$ gives $p''=p'$, so

$$
p=p'=p''
$$

Pressure at a point is the same on a surface of any orientation. It is a scalar; only the force it produces has a direction, and that direction is set by the surface.

### The hydraulic jack

Connect two cylinders of cross-sections $A_1$ and $A_2$, fill them with oil and fit each with a piston. Push on the first with $F_1$; by Pascal's law the oil pressure is $p=F_1/A_1$ everywhere, so holding the second piston still needs

$$
F_2=pA_2
$$

$$
\boxed{F_2=F_1\frac{A_2}{A_1}}
$$

If $A_2$ is 100 times $A_1$, the force is multiplied by 100: a hydraulic lever. Aircraft use this to move control surfaces, deploy high-lift devices and raise the landing gear with a small pump.

Energy is still conserved. Push the first piston down by $d_1$. The oil is incompressible, so the volume $A_1d_1$ leaving the first cylinder enters the second:

$$
A_1d_1=A_2d_2
$$

$$
d_2=d_1\frac{A_1}{A_2}
$$

The work done on the second piston is then

$$
F_2d_2=F_1\frac{A_2}{A_1}\cdot d_1\frac{A_1}{A_2}=F_1d_1
$$

the work put in at the first. The large force moves a proportionally small distance.

## 3. Stevin's law

### The force balance on a slab

Now include gravity. Take $z$ upwards, opposite to $\vec g$, and consider a thin horizontal slab of fluid with top and bottom area $A$ and height $\Delta z$ at height $z$. The density may vary with height, so call it $\rho(z)$. Three vertical forces act:

- its weight, $\rho(z)A\,\Delta z\,g$, downwards;
- the pressure force on the bottom face, $p(z)A$, upwards (pressure pushes towards the slab);
- the pressure force on the top face, $(p+\Delta p)A$, downwards, where $\Delta p$ is the as yet unknown change in pressure over $\Delta z$.

Pressure forces on the side faces cancel in pairs. The fluid is at rest, so with upwards positive

$$
pA-(p+\Delta p)A-\rho(z)A\,\Delta z\,g=0
$$

The area cancels, and so do the $pA$ terms:

$$
-\Delta p\,A-\rho(z)A\,\Delta z\,g=0
$$

$$
\Delta p=-\rho(z)g\,\Delta z
$$

Let $\Delta z\to0$ and divide by $dz$:

$$
\boxed{\frac{dp}{dz}=-\rho(z)g}
$$

This is **Stevin's law**. The left-hand side is the **pressure gradient**, the rate at which pressure changes with height. It is larger in a denser fluid (pressure changes faster in mercury than in water, and very slowly in a gas) and larger where gravity is stronger: on Mars, with $g$ about 0.38 of Earth's, it is weaker. The minus sign says pressure falls going up. Physically, the pressure difference across each slab supports the slab's weight.

![[tf_stevin_element.png|900]]

### Height or depth

The sign depends only on which way $z$ points. Measuring height $z$ up from the bottom of a lake gives $dp/dz=-\rho g$; measuring depth down from the surface, as a ship designer might, gives $dp/dz=+\rho g$. The pressure in the lake is the same either way, rising from $p_{atm}$ at the surface to a maximum at the bottom. The rule to remember is that **pressure increases in the direction of $\vec g$**; choose the coordinate first and let the sign follow.

## 4. Liquids

### Integrating Stevin's law

Stevin's law holds at each point, with the local density. To get the pressure difference between heights $z_0$ and $z_1$, add up the small changes, which means integrating:

$$
dp=-\rho(z)g\,dz
$$

$$
\int_{p_0}^{p_1}dp=-g\int_{z_0}^{z_1}\rho(z)\,dz
$$

with $g$ taken outside as a constant. For a liquid the density is constant to a very good approximation, so it comes outside too:

$$
p_1-p_0=-\rho g(z_1-z_0)
$$

$$
\boxed{\Delta p=-\rho g\,\Delta z}
$$

which holds for any finite $\Delta z$, not just small ones. Taking $z_0=0$ as the reference with pressure $p_0$, and a general height $z$:

$$
\boxed{p(z)=p_0-\rho gz}
$$

The pressure varies linearly with height because the pressure gradient is constant. Measured as depth $h$ below a free surface at $p_{atm}$, the same result reads $p=p_{atm}+\rho gh$.

![[tf_hydrostatics.png|900]]

### The hydrostatic paradox

Two open containers stand side by side, filled with the same liquid to the same level. One is a narrow tank, the other a wide L-shaped vessel holding five times as much liquid. The pressures at the two bottoms are equal: both bottoms are the same distance $\Delta z$ below a free surface at $p_{atm}$, so $\Delta p=\rho g\Delta z$ is the same, even though the weights of liquid are very different. This is the **hydrostatic paradox**.

To see that it must be so, join the bottoms of the two containers with a thin tube. If the pressures differed, liquid would flow from the higher-pressure container to the other and the levels would change, which does not happen. The same holds at every height, not just the bottom: in a connected body of fluid at rest, **the pressure depends only on $z$**, whatever the shape of the container. Pascal's law, in the presence of gravity, becomes the statement that pressure is constant along any horizontal level within one continuous fluid. That is what makes complicated hydrostatic systems easy: only the heights matter.

## 5. Archimedes' law

A body submerged in a fluid feels an upward **buoyant force** (upthrust) equal to the weight of fluid it displaces:

$$
\boxed{U=\rho g\mathcal V}
$$

where $\rho$ is the density of the fluid and $\mathcal V$ the volume of the body.

The derivation follows from Stevin's law. A cube of side $L$ (a cubic blimp) is fully submerged in fluid of density $\rho$, assumed not to vary noticeably over the height $L$. The side forces cancel. On the bottom face the fluid pushes up with $pL^2$; on the top face it pushes down with $(p+\Delta p)L^2$, where Stevin's law for the surrounding fluid gives $\Delta p=-\rho gL$. The net upward pressure force is

$$
U=pL^2-(p+\Delta p)L^2
$$

$$
U=-\Delta p\,L^2
$$

$$
U=\rho gL\cdot L^2=\rho gL^3=\rho g\mathcal V
$$

The upthrust contains the density of the fluid, not of the body. It exists only because the pressure on the bottom of the body is higher than on its top, which in turn exists only because of gravity: there are no blimps on the Moon, where there is no atmosphere to provide the pressure difference.

For a body of general shape the pressure varies all round the surface and the force has to be found by integrating it over the surface, but the result is the same, $U=\rho g\mathcal V$. A neater argument: replace the body by fluid of the same shape. That fluid is in equilibrium, so the surrounding pressure must support exactly its weight, $\rho g\mathcal V$; the pressure on the surface does not know what is inside it.

The net vertical force on a body of average density $\rho_m$ is upthrust minus weight:

$$
U-W=\rho g\mathcal V-\rho_mg\mathcal V
$$

$$
U-W=(\rho-\rho_m)g\mathcal V
$$

If the body is less dense than the fluid it rises; if denser, it sinks. A blimp floats because its average density, envelope, frame and helium included, is below that of air.

## 6. The barometer

The pressure of the atmosphere was first measured by Torricelli, a student of Galileo, who filled a glass tube closed at one end with liquid, inverted it with the open end under the surface of a dish of the same liquid, and raised it. The liquid stays in the tube until the closed end is raised past a critical height $h$; above that, the column stops rising and a pocket of near-vacuum forms at the top, whose pressure is only the small vapour pressure of the liquid.

Apply Stevin's law between the free surface in the dish, which is at $p_{atm}$ (by Pascal's law, the same as the liquid in the tube at that level), and the top of the column, where $p\approx0$:

$$
p_1-p_0=-\rho g(z_1-z_0)
$$

$$
0-p_{atm}=-\rho gh
$$

$$
\boxed{p_{atm}=\rho gh}
$$

With mercury ($\rho=13\,600$ kg/m³) Torricelli found $h\approx760$ mm, varying by a few centimetres with the weather: lower when a storm approaches. One standard atmosphere is defined as 760 mm of mercury, $101\,325$ Pa, and 1/760 of it is the torr, 133.3 Pa. Mercury was used because it is dense: water is 13.6 times lighter, so a water barometer needs a column 13.6 times taller, 10.3 m.

> [!tip] Ten metres of water is one atmosphere
> $p_{atm}/(\rho_{water}g)=101\,325/(1000\times9.81)=10.3$ m. A suction pump cannot lift water more than about 10 m, because it can at best reduce the pressure above the water to zero; but a pump at the bottom can push water to any height if it supplies enough pressure. Pumping water to the top of a 100 m building needs about 10 bar, so very tall buildings use stages of pumps.

## 7. The manometer

The gauge pressure the lungs can produce is measured with a U-tube partly filled with a coloured liquid, both ends open to the atmosphere so the levels start equal. With the pressure $p_{lungs}$ applied to the left branch, the liquid falls on that side and rises on the other, until the difference in level is $h=z_1-z_0$.

Points 0 and 0′, at the same height $z_0$ in the same connected liquid, are at the same pressure, and the pressure at 0 is $p_{lungs}$. Point 1, at the top of the right-hand column, is at $p_{atm}$. Stevin's law up the right-hand column:

$$
p_1-p_0=-\rho g(z_1-z_0)
$$

$$
p_{atm}-p_{lungs}=-\rho gh
$$

$$
\boxed{p_{lungs}-p_{atm}=\rho gh}
$$

The level difference measures the gauge pressure directly. This is a **liquid-column manometer**. A scale beside the tube makes the reading precise, tilting the reading tube at a small angle makes the liquid move further along it for the same pressure and so increases the sensitivity (Problem Sheet 6, Q6.4), and many tubes side by side give the pressures at many points at once. The multi-tube manometer in the second-year aerofoil lab works this way, connecting each tube to a pressure tap on the aerofoil surface.

## 8. Stratification of the atmosphere

### The column of air above the surface

Sea-level pressure is about $10^5$ Pa, and it supports the weight of the air above. A column of air 1 cm² in cross-section, from sea level to the top of the atmosphere, therefore has mass

$$
m=\frac{pA}{g}=\frac{101\,325\times10^{-4}}{9.81}=1.03\ \mathrm{kg}
$$

about a kilogram per square centimetre.

### Three equations for the atmosphere

Air is compressible, so its density cannot be taken as constant; it changes with height along with the pressure. To find $p(z)$ and $\rho(z)$ three relations are combined:

- the ideal-gas law at every height, $p(z)=\rho(z)RT(z)$, with $R=287$ J kg⁻¹ K⁻¹ for dry air;
- Stevin's law, $dp/dz=-\rho(z)g$, treating the atmosphere as at rest;
- a temperature profile $T(z)$, known from measurement and described by the **lapse rate** $\Gamma=-dT/dz$, positive when temperature falls with height.

### Isothermal atmosphere

With $\Gamma=0$, $T=T_0$ throughout. The gas law gives the density in terms of the pressure:

$$
\rho=\frac{p}{RT_0}
$$

Substitute into Stevin's law:

$$
\frac{dp}{dz}=-\frac{pg}{RT_0}
$$

Separate the variables:

$$
\frac{dp}{p}=-\frac{g}{RT_0}\,dz
$$

Integrate from $(z_0,p_0)$ to $(z_1,p_1)$:

$$
\int_{p_0}^{p_1}\frac{dp}{p}=-\frac{g}{RT_0}\int_{z_0}^{z_1}dz
$$

$$
\ln p_1-\ln p_0=-\frac{g}{RT_0}(z_1-z_0)
$$

Exponentiate, and take $z_0=0$ and a general $z_1=z$:

$$
\boxed{\frac{p(z)}{p_0}=\exp\left(-\frac{gz}{RT_0}\right)}
$$

The pressure decays exponentially, falling by a factor $e$ every $RT_0/g$ (8.4 km at 288 K). The density follows the same law, $\rho=\rho_0\exp(-gz/RT_0)$ with $\rho_0=p_0/RT_0$. This is the model for the lower stratosphere, where the temperature is constant.

### Troposphere with a constant lapse rate

In the troposphere, from sea level to about 11 km, the temperature falls linearly:

$$
T(z)=T_0-\Gamma_ez
$$

with the **environmental lapse rate** $\Gamma_e=6.5$ K/km on average. At sea level the ISA has $T_0=288.15$ K, $p_0=101\,325$ Pa and $\rho_0=1.225$ kg/m³. Fly 10 km up and it is about 65 K colder, around −50 °C.

Now $\rho=p/(R(T_0-\Gamma_ez))$, and Stevin's law gives

$$
\frac{dp}{p}=-\frac{g}{R}\frac{dz}{T_0-\Gamma_ez}
$$

This integral can be done by hand or with Wolfram Alpha. The right-hand integral is

$$
\int_0^z\frac{dz'}{T_0-\Gamma_ez'}=-\frac{1}{\Gamma_e}\Big[\ln(T_0-\Gamma_ez')\Big]_0^z=-\frac{1}{\Gamma_e}\ln\frac{T_0-\Gamma_ez}{T_0}
$$

so

$$
\ln\frac{p}{p_0}=-\frac{g}{R}\left(-\frac{1}{\Gamma_e}\ln\frac{T_0-\Gamma_ez}{T_0}\right)
$$

$$
\ln\frac{p}{p_0}=\frac{g}{\Gamma_eR}\ln\frac{T_0-\Gamma_ez}{T_0}
$$

$$
\boxed{\frac{p(z)}{p_0}=\left(\frac{T_0-\Gamma_ez}{T_0}\right)^{g/(\Gamma_eR)}}
$$

a power law, with exponent $g/(\Gamma_eR)=9.81/(0.0065\times287)=5.26$. The density then follows from the gas law, $\rho=p/(RT)$.

> [!check] Limiting case
> As $\Gamma_e\to0$, write $(1-\Gamma_ez/T_0)^{g/(\Gamma_eR)}$. Using $(1-x)^{1/x}\to e^{-1}$ as $x\to0$ with $x=\Gamma_ez/T_0$, the power becomes $[(1-x)^{1/x}]^{gz/(RT_0)}\to e^{-gz/(RT_0)}$, the isothermal result.

### Comparing the three models

![[tf_atmosphere_models.png|900]]

Assuming constant density (the isochoric model) makes the pressure fall linearly, $p=p_0-\rho_0gz$, reaching zero at $p_0/(\rho_0g)=8.4$ km and going negative above; the temperature $p/(\rho_0R)$ then falls below absolute zero. It is unphysical above a couple of kilometres, though not bad for the first kilometre. The isothermal model is reasonable for pressure and density over the first few kilometres. The lapse-rate model is the ISA troposphere.

---

## Worked examples

### Worked example - air on top of Everest

Find the pressure and density at the summit of Everest, 8848 m, and at the 11 km tropopause, using the ISA troposphere.

At 8848 m:

$$
T=288.15-0.0065\times8848=230.6\ \mathrm K
$$

$$
p=101\,325\times\left(\frac{230.6}{288.15}\right)^{5.26}=31.4\ \mathrm{kPa}
$$

$$
\rho=\frac{p}{RT}=\frac{31\,420}{287\times230.6}=0.475\ \mathrm{kg/m^3}
$$

about 39 % of sea-level density: each breath holds well under half the oxygen. At 11 km, $T=216.65$ K, $p=22.6$ kPa and $\rho=0.364$ kg/m³. The isothermal model gives 35.5 kPa and 0.429 kg/m³ at 8848 m, and the constant-density model a negative pressure.

### Worked example - oil and water in a tank

A cylindrical tank of diameter 0.7 m holds 100 L of water and 300 L of oil of density 800 kg/m³. Find the gauge pressure at the bottom (Problem Sheet 6, Q6.6, the sheet's worked solution).

![[tf_two_layer_tank.png|900]]

The cross-section is $A=\pi\times0.7^2/4=0.3848$ m², so the layer depths are

$$
h_w=\frac{0.1}{0.3848}=0.260\ \mathrm m,\qquad h_o=\frac{0.3}{0.3848}=0.780\ \mathrm m
$$

The oil floats on the water. Measure depth from the free surface, so pressure increases with depth. Through the oil, from the surface to the interface:

$$
p_1-p_0=\rho_ogh_o
$$

and through the water, from the interface to the bottom:

$$
p_2-p_1=\rho_wgh_w
$$

Adding, the gauge pressure at the bottom is

$$
p_2-p_0=g(\rho_oh_o+\rho_wh_w)=9.81\times(800\times0.780+1000\times0.260)=8.67\ \mathrm{kPa}
$$

The pressure profile has two straight segments with different slopes, steeper in the denser water.

> [!check] Force balance on the whole contents
> Vertical equilibrium of all the liquid: $p_2A=p_0A+(\text{weight of oil}+\text{weight of water})$. The weights are $300\times0.8\times9.81=2354$ N and $100\times9.81=981$ N, so $p_2-p_0=3335/0.3848=8.67$ kPa. Stevin's law is a force balance, nothing more.

### Worked example - bubble-tube level gauge

Air is bled slowly through a tube whose open end is 1 m above the bottom of a tank of liquid with specific gravity 0.85. The gauge on the air line reads 15 kPa. How deep is the liquid? (Problem Sheet 6, Q6.8, the tutorial problem.)

Air bubbles out only when its pressure just exceeds the liquid pressure at the tube outlet, so the gauge reading is the gauge pressure of the liquid at that depth. The air in the tube has negligible density, so its pressure is the same at the gauge and at the outlet. The outlet is $d-1$ below the surface:

$$
p_g=\rho g(d-1)
$$

$$
d=1+\frac{15\,000}{850\times9.81}=2.80\ \mathrm m
$$

### Worked example - mercury manometer on a gas bulb

A mercury U-tube connects bulb A to the atmosphere at standard sea-level conditions; the mercury stands 15 cm higher in the open limb. Find the absolute pressure in A (Problem Sheet 6, Q6.3).

Start at the open surface, at $p_{atm}=101\,325$ Pa, and move down 0.15 m through mercury to the level of the mercury surface on the bulb side; that level has the bulb pressure (the gas above it is too light to matter). With $\rho_{Hg}=13\,546$ kg/m³:

$$
p_A=p_{atm}+\rho_{Hg}gh=101\,325+13\,546\times9.81\times0.15=121.3\ \mathrm{kPa}
$$

that is, 19.9 kPa gauge.

### Worked example - inclined-tube manometer

A manometer has a large reservoir connected to the reference pressure and a reading tube inclined at $\theta$ to the horizontal connected to a pressure tap. Find the movement $\Delta l$ of the liquid along the tube for a pressure difference $\Delta p=p_{tap}-p_{atm}$ (Problem Sheet 6, Q6.4).

The reservoir is so large that its level hardly moves, so the liquid in the tube rises a vertical height $\Delta z=\Delta l\sin\theta$ above it, and Stevin's law gives $|\Delta p|=\rho g\Delta z$:

$$
\Delta l=\frac{|\Delta p|}{\rho g\sin\theta}
$$

The sensitivity grows as $1/\sin\theta$. For $\Delta p=100$ Pa in water, a vertical tube moves 10.2 mm but a tube at 10° moves 58.7 mm, much easier to read. A variable-angle manometer can use a shallow angle for small pressures and a steeper one for a larger range.

### Worked example - a melting ice cube

An ice cube floats in a glass of water. When it melts, does the level rise, fall or stay the same? (Problem Sheet 6, Q6.2.)

A floating body is in equilibrium, so its weight equals the upthrust, which is the weight of water displaced:

$$
m_{ice}g=\rho_wg\mathcal V_{disp}
$$

$$
\mathcal V_{disp}=\frac{m_{ice}}{\rho_w}
$$

When the ice melts, its mass is unchanged and it becomes water of volume $m_{ice}/\rho_w$, exactly the volume it was already displacing. The level does not change. (Ice is about 917 kg/m³, so 91.7 % of a floating cube is below the surface; the 8.3 % above is exactly what the extra volume of the solid accounts for.)

---

## Links

- Parent: [[SESA1016 Thermofluids Hub]] · Previous: [[SESA1016 T7 - Fluid Properties and Viscosity]] · Next: [[SESA1016 T9 - Describing Flow and the Material Derivative]]
- Concepts: [[Pressure and Head]] · [[Ideal-gas Law]]
- Worked sheet: [[SESA1016 Problem Sheet 06 - Fluid Properties and Hydrostatics Solutions]] (Q6.2–Q6.9) · Formula list: [[SESA1016 Formula Sheet]]
- Used again in: [[SESA1016 T10 - Euler and Bernoulli Equations|T10]] (Bernoulli reduces to Stevin's law at rest; Pitot and static pressures read on manometers) · [[SESA2023 W01 - Thrust, Efficiency, Range and the ISA]] (the ISA in Propulsion)

## Sources

- `Chapter 8.pdf`: lecture notes Chapter 8, Fluids at rest, §§8.1–8.8, Derivations 8.1–8.3, Figs 8.1–8.11.
- `SESA1016 Lecture 2025-03-04.txt` (4 Mar 2025): pressure as a normal stress (ll. 48–64), Pascal's law (ll. 65–94), hydraulic jack (ll. 95–171), Stevin's law (ll. 172–322), liquids (ll. 323–402), the hydrostatic paradox (ll. 403–472), Archimedes and the cubic blimp (ll. 475–620).
- `SESA1016 Lecture 2025-03-06.txt` (6 Mar 2025): Archimedes for general shapes (ll. 41–80), barometer (ll. 81–200), manometer (ll. 202–285), atmosphere models and Everest (ll. 286–554).
- `Problem Sheet 06 - Fluid Properties and Hydrostatics.pdf`: Q6.2–Q6.9, printed answers and worked solutions to Q6.6 and Q6.9.

## Self-study tasks

### Core

- [ ] Do the lapse-rate integral by hand (left to you, 6 Mar, ll. 472–479). → [[#Troposphere with a constant lapse rate]]
- [ ] Q6.2, melting ice cube. Answer: level unchanged. → [[#Worked example - a melting ice cube]]
- [ ] Q6.3, mercury manometer on a gas bulb. Target 121.3 kPa. → [[#Worked example - mercury manometer on a gas bulb]]
- [ ] Q6.4, inclined-tube manometer sensitivity. → [[#Worked example - inclined-tube manometer]]
- [ ] Q6.5, safe depth for an underwater camera tested at 0.8 MPa with a 25 % margin. Target 60 m. → [[SESA1016 Problem Sheet 06 - Fluid Properties and Hydrostatics Solutions]]
- [ ] Q6.6, oil and water in a tank (worked solution). Target 8.67 kPa. → [[#Worked example - oil and water in a tank]]
- [ ] Q6.7, loaded piston on an oil reservoir with a thin tube. Targets 55.26 cm and 42.96 mm. → [[#The hydrostatic paradox]] · [[SESA1016 Problem Sheet 06 - Fluid Properties and Hydrostatics Solutions]]
- [ ] Q6.8, bubble-tube level gauge (the tutorial problem). Target 2.80 m. → [[#Worked example - bubble-tube level gauge]]
- [ ] Q6.9, trapped air in a side tube (worked solution). Target 0.082 m for $H=1$ m. → [[SESA1016 Problem Sheet 06 - Fluid Properties and Hydrostatics Solutions]]

### Further practice

- [ ] Derive Stevin's law from a force balance on a slab, then Archimedes' law for a cube. → [[#The force balance on a slab]] · [[#5. Archimedes' law]]
- [ ] Show that $F_1d_1=F_2d_2$ for a hydraulic jack (left to the notes, 4 Mar, ll. 162–166). → [[#The hydraulic jack]]
- [ ] Build a manometer from a plastic tube and measure the gauge pressure your lungs can produce (suggested at 6 Mar, ll. 258–263); 1 m of water is about 10 kPa. → [[#7. The manometer]]

## Transcript and slide slips

> [!warning] Transcript slips (4 Mar, ll. 253 and 266)
> Where: [[#The force balance on a slab]].
>
> Stevin's law is first read out as "dp dz equals rho times g" without the minus sign, which is restored straight afterwards (ll. 270–272). Gravity on Mars is said to be "about one-sixth" of Earth's; that is the Moon. Mars has about 0.38 g.

> [!warning] Transcript slips (6 Mar, ll. 299, 304 and 464)
> Where: [[#Worked example - air on top of Everest]] · [[#Troposphere with a constant lapse rate]].
>
> Everest is given as "848 meters" (8848 m), sea-level density as "1,225" (1.225 kg/m³) and the lapse-rate slope as "negative 5.6" (−6.5 K/km).

> [!warning] Lecture-notes slips (Chapter 8)
> Where: [[#The hydraulic jack]] · [[#5. Archimedes' law]] · [[#Three equations for the atmosphere]].
>
> After eq. 8.5, "if $A_2$ is 100 times $A_2$" should read "100 times $A_1$". Before eq. 8.18 the weight of the body is written $W=\rho g\mathcal V$; it is $\rho_mg\mathcal V$, as eq. 8.18 itself uses. Eq. 8.23, $p=\rho RT$ with $R=287$ J kg⁻¹ K⁻¹, is called the ideal-gas law "in molar form"; it is the specific (per-mass) form. In §8.8, 1 bar is "1 kilogram per square centimetre"; it is the weight of about 1.02 kg per cm².
