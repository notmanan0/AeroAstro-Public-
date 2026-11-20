---
title: "SESA3029 W09a - Heat Conduction and Thermal Resistance"
module: "SESA3029 Aerothermodynamics"
type: topic
stream: "Block 5: Heat transfer"
order: 10
tags: [sesa3029, heat-transfer, conduction, fourier-law, thermal-resistance, electrical-analogy, convection, nusselt-number]
aliases: ["SESA3029 Lecture 5.1", "SESA3029 Lecture 5.2", "SESA3029 W09a"]
date: 2026-11-17
status: lectured
coverage: "Lecture 5.1 (§§1–5, Thu 19 Nov; not recorded this year, so checked against last year's 2025–26 recording) and Lecture 5.2 (§§6–11, Fri 20 Nov, transcript L5-2: slides 1–18, radial conduction, convection, Newton's law of cooling, the plane wall with convection on both sides, the Nusselt number); slide 19 (conduction or convection, double glazing) not reached and written from the slide"
parent: ["[[SESA3029 Aerothermodynamics Hub]]"]
prerequisites: ["[[SESA1016 T2 - Work, Heat and the First Law]]", "[[Heat Equation]]", "[[SESA3029 W07c - Ackeret Theory and Optimum Supersonic Aerofoils]]"]
next_topics: ["[[SESA3029 W09b - Convective Heat Transfer and the Reynolds Analogy]]"]
key_concepts: ["[[Modes of Heat Transfer]]", "[[Fourier's Law of Heat Conduction]]", "[[Thermal Conductivity]]", "[[Thermal Resistance]]", "[[Radial Conduction in Cylinders and Spheres]]"]
tutorial_sheets: ["[[SESA3029 Example Sheet 3 - Solutions]]"]
sources: ["02 - Sources/Lectures/Lecture5.1.pdf", "02 - Sources/Lectures/Lecture 5-1 (2025-26 version).txt", "02 - Sources/Lectures/Lecture5.2.pdf", "02 - Sources/Lectures/20 November 2026 at 16_48_17.txt", "03 - Exams & Past Papers/ExampleSheet3(1).pdf"]
---

# SESA3029 W09a - Heat Conduction and Thermal Resistance

> [!abstract] Summary
> Heat moves by conduction, convection and radiation, and the net transfer is always from the hotter body to the colder one. Conduction obeys Fourier's law, $\dot Q=-kA\,\mathrm dT/\mathrm dx$, and in steady one-dimensional conduction without heat generation the rate through a layer is a temperature difference divided by a thermal resistance: $L/kA$ for a plane wall, $\ln(r_o/r_i)/2\pi kL$ for a long hollow cylinder and $\frac{1}{4\pi k}\left(\frac1{r_i}-\frac1{r_o}\right)$ for a spherical shell. A convecting surface adds $1/hA_s$ from Newton's law of cooling. Resistances add in series and their reciprocals add in parallel, exactly as in an electrical circuit, which turns layered walls, insulated pipes and tanks into one-line calculations.

> [!summary]- Exam use: quick path
> - **Use it when:** a wall, tube or spherical tank (possibly layered, possibly with a fluid on either side) sits between two known temperatures and the question asks for the heat rate, the heat flux or an interface temperature.
> - **Assumptions:** steady; one-dimensional (plane: $T=T(x)$; cylinder and sphere: $T=T(r)$, so the cylinder is long and its end faces carry no heat); constant $k$ in each layer; no heat generated inside; perfect contact between layers; fluid temperatures $T_\infty$ taken far from the surface.
> - **Method:** 1. Draw the resistance network from the hot fluid to the cold one. 2. Write each resistance with **its own area**: $L/kA$, $\ln(r_o/r_i)/2\pi kL$, $\frac1{4\pi k}(1/r_i-1/r_o)$, $1/hA_s$. 3. Add series resistances; add reciprocals of parallel ones. 4. $\dot Q=\Delta T_\text{overall}/R_\text{total}$. 5. March through the network: each $\Delta T_j=\dot Q R_j$ gives the next interface temperature.
> - **Common mistakes:** using one area for both convection resistances of a tube (the inner surface is $2\pi r_1L$, the outer $2\pi r_3L$); forgetting the factor that turns cm into m in $L/k$, or mixing the per-area resistance $R''=L/k$ (m²K/W) with $R=L/kA$ (K/W).
> - **Practise:** [[#Worked example - the insulated plane block|the insulated plane block]] · [[SESA3029 Example Sheet 3 - Solutions#Q1. Composite wall pierced by steel bolts|ES3 Q1, the same block pierced by steel bolts]]

Estimating a rate of heat transfer is a practical problem with a wide range of uses: clothing that sets how fast a body rejects heat, pans and ovens, refrigerators that keep their contents cold by rejecting heat, vehicle brakes that must dissipate friction heat, house radiators acting as heat exchangers, and quantum processors held near absolute zero, where the thermal vibration of atoms and electrons is small enough not to disturb the qubits. The aerospace cases are more severe. A gas turbine runs at around 1500 °C while its blade alloys melt at around 1250 °C, so the blades survive only because cooling air carries the heat away. A lunar-return capsule entering the atmosphere at $M\approx20$ has an average surface temperature of about 1600 °C and a peak near 3000 °C, above the melting point of most metals and alloys, so its heat shield has to limit how much of that heat reaches the inside.

The same capsule shows all three modes of heat transfer. Heat passes **through** the shield wall by conduction. It reaches the wall **from** the hot shock-layer gas by convection, which is conduction combined with the motion of the fluid in the boundary layer. The hot surface and the glowing gas also exchange energy by radiation, which needs no medium at all. Conduction is treated in full below, with convection entering as a boundary condition on a wall; the convective heat transfer coefficient itself, the Reynolds analogy and radiation are in [[SESA3029 W09b - Convective Heat Transfer and the Reynolds Analogy|W09b]] and [[SESA3029 W09d - Thermal Radiation|W09d]].

Everything here is steady and one-dimensional. Under those two conditions the heat rate is the same through every layer of a wall, and a wall behaves like a chain of electrical resistors with temperature playing the part of voltage. That analogy is the working tool of the block, and it carries straight over to the fins and insulation of [[SESA3029 W09c - Critical Thickness of Insulation and Fins|W09c]] and the overall heat transfer coefficient of the heat exchangers in [[SESA3029 W09f - Heat Exchangers|W09f]].

## 1. Modes of heat transfer

**Conduction** is the transfer of heat from the more energetic particles of a substance to the adjacent, less energetic ones as a result of interactions between the particles: warmer particles vibrate more vigorously and pass energy to their neighbours. It needs a medium but no motion of the medium: a pan heating on a hot plate, or heat crossing the wall of a capsule from the hot outside to the cooler inside.

**Convection** is the mode of energy transfer between a solid surface and an adjacent fluid that is in motion. It is conduction combined with fluid motion: right at the wall the fluid is at rest relative to the surface and heat crosses into it by conduction, and the moving fluid then carries that heat away. A cup of tea cooling down is convection, whether it is left to stand or put in front of a fan to cool faster. In the absence of bulk fluid motion the same fluid transfers heat by conduction only (§11).

**Radiation** is energy emitted in the form of electromagnetic waves by any body at a temperature above absolute zero (0 K). Unlike conduction and convection, no intervening medium is necessary, so radiation crosses a vacuum, which is how the Sun's heat reaches the Earth. Radiation is the subject of [[SESA3029 W09d - Thermal Radiation|W09d]]; the black-body background is in [[Blackbody Radiation]] (SESA2024).

![[at_w09a_modes.png|900]]

### Direction and rate

Take two blocks joined by a solid rod, block 1 at 100 °C and block 2 at 30 °C. Heat flows along the rod from block 1 to block 2: the transfer of energy as heat is from the higher-temperature body to the lower-temperature one, which is the second law of thermodynamics ([[SESA1016 T2 - Work, Heat and the First Law|SESA1016 T2]] for the sign conventions of heat). If both blocks are at 70 °C, nothing flows: heat transfer stops when the two bodies reach the same temperature, and that is thermal equilibrium.

The **heat transfer rate** $\dot Q$ is the energy crossing a surface per unit time, in watts (W = J/s). Dividing by the area it crosses gives the **heat flux**,

$$
\dot q=\frac{\dot Q}{A}\qquad(\text{W/m}^2).
$$

Heat transfer is driven by temperature, which is a scalar, and a larger temperature difference gives a larger rate. The heat flow itself has a magnitude and a direction, so the heat flux is a vector (§2, the 3D form of Fourier's law).

## 2. Fourier's law of heat conduction

Let the rod between the two blocks have length $L$ and cross-sectional area $A$, with block 1 at $T_1$ and block 2 at $T_2$. Three observations fix the form of the law. The rate is zero when $T_1=T_2$, so a reasonable model is that $\dot Q$ is proportional to the temperature difference. A longer rod passes less heat, and a thicker rod (larger $A$) passes more. Together,

$$
\dot Q\propto\frac{A}{L}\left(T_1-T_2\right).
$$

Removing the proportionality with a constant $k$,

$$
\dot Q=k\frac{A}{L}\left(T_1-T_2\right).
$$

This holds for the whole rod. To get a local law, apply it to a short piece of rod between $x$ and $x+\Delta x$, with $x$ measured in the direction of heat transfer:

$$
\dot Q=kA\,\frac{T(x)-T(x+\Delta x)}{\Delta x}.
$$

Pull out a minus sign:

$$
\dot Q=-kA\,\frac{T(x+\Delta x)-T(x)}{\Delta x}.
$$

Let $\Delta x\to0$. The fraction becomes the derivative:

$$
\boxed{\dot Q=-kA\frac{\mathrm dT}{\mathrm dx}}\qquad\text{(Fourier's law of heat conduction, 1-D)}
$$

For the whole rod with a linear temperature fall the derivative is $\mathrm dT/\mathrm dx=(T_2-T_1)/L$, and the boxed law gives back $\dot Q=kA(T_1-T_2)/L$.

The minus sign is there because heat flows down the temperature gradient. With $T$ falling along $+x$, $\mathrm dT/\mathrm dx<0$ and $\dot Q>0$: the heat flows along $+x$. If the temperature rises along $x$, $\dot Q$ comes out negative, meaning the heat flows towards $-x$. The sign of $\dot Q$ is a direction, not an error.

![[at_w09a_fourier_sign.png|900]]

In three dimensions the heat flux is a vector that points down the steepest temperature descent:

$$
\dot{\mathbf q}=-k\nabla T,\qquad \dot q_i=-k\frac{\partial T}{\partial x_i}\quad(i=1,2,3).
$$

This form assumes an isotropic material, one whose $k$ is the same in every direction. In a fibre composite or a laminated heat shield $k$ differs along and across the plies and becomes a tensor, $\dot q_i=-k_{ij}\,\partial T/\partial x_j$. Combining $\dot{\mathbf q}=-k\nabla T$ with an energy balance on a small volume gives the heat-conduction partial differential equation that Fourier set up and solved with Fourier series ([[Heat Equation]], MATH2048; its finite-difference solution is [[SESA3029 W09e - Numerical Methods in Conduction|W09e]]).

## 3. Thermal conductivity

Rearranging Fourier's law defines the constant of proportionality,

$$
k=\frac{-\dot Q}{A\,\mathrm dT/\mathrm dx}.
$$

Check the units: $\dot Q$ in W, $A$ in m² and $\mathrm dT/\mathrm dx$ in K/m give $k$ in $\text{W}/(\text{m}^2\cdot\text{K/m})=\text{W/(m K)}$. This is the **thermal conductivity**: the rate of heat transfer through a unit thickness of the material, per unit area, per unit temperature difference. It measures a material's ability to conduct heat.

Water has $k=0.607$ W/(m K) and iron $k=80.2$ W/(m K), so iron conducts heat $80.2/0.607=132$ times faster than water. Denser packing means more frequent particle interactions, which is part of why solids generally conduct better than liquids and liquids better than gases. Most of iron's advantage over water comes from its free electrons, which carry energy as well as charge; that is why good electrical conductors such as copper and iron are also good thermal conductors. The insulation layers of the next sections have $k\approx0.05$ W/(m K), and still air about $0.026$ W/(m K).

## 4. Conduction through a plane wall

A plane wall has thickness $L$ and face area $A$, with its faces held at $T_1$ ($x=0$) and $T_2$ ($x=L$). Assume steady conditions, conduction in $x$ only, constant $k$ and no heat generated inside the wall.

Apply an energy balance to a thin slice between $x$ and $x+\mathrm dx$. In steady state nothing accumulates and nothing is generated, so the heat entering equals the heat leaving:

$$
\dot Q(x)-\dot Q(x+\mathrm dx)=0
\quad\Rightarrow\quad
\frac{\mathrm d\dot Q}{\mathrm dx}=0 .
$$

So $\dot Q$ is the same at every $x$. Substitute Fourier's law:

$$
\frac{\mathrm d}{\mathrm dx}\left(-kA\frac{\mathrm dT}{\mathrm dx}\right)=0 .
$$

With $k$ and $A$ constant,

$$
\frac{\mathrm d^2T}{\mathrm dx^2}=0 .
$$

Integrate twice:

$$
T(x)=C_1x+C_2 .
$$

The boundary condition $T(0)=T_1$ gives $C_2=T_1$, and $T(L)=T_2$ gives $C_1=(T_2-T_1)/L$:

$$
T(x)=T_1-\left(T_1-T_2\right)\frac{x}{L}.
$$

The profile is a straight line, and its slope is $\mathrm dT/\mathrm dx=-(T_1-T_2)/L$. Fourier's law then gives

$$
\dot Q=-kA\left(-\frac{T_1-T_2}{L}\right)=\frac{kA}{L}\left(T_1-T_2\right).
$$

This is the steady one-dimensional case of the [[Heat Equation]] ($\partial T/\partial t=\alpha\,\partial^2T/\partial x^2$ with the time derivative set to zero). The straight line depends on $k$ being constant: if $k$ varies with temperature, $\dot Q$ is still uniform but $\mathrm dT/\mathrm dx=-\dot Q/(kA)$ is steepest where $k$ is smallest, and the profile curves.

## 5. The electrical analogy and thermal resistance

Compare the plane-wall result with Ohm's law:

$$
\dot Q=\frac{T_1-T_2}{L/(kA)}
\qquad\longleftrightarrow\qquad
I=\frac{V}{R}.
$$

Temperature difference plays the part of voltage and the heat transfer rate the part of current. The quantity in the denominator is the **thermal resistance** of the wall:

$$
\boxed{R_\text{th}=\frac{L}{kA}}\qquad(\text{K/W; plane wall, steady, 1-D, constant }k),\qquad \dot Q=\frac{\Delta T}{R_\text{th}} .
$$

A thick wall of poor conductor has a large resistance and passes little heat for a given temperature difference. Thermal resistances combine like electrical ones, depending on whether the components conducting heat are in series or in parallel.

![[at_w09a_series_parallel.png|900]]

### Layers in series

In a wall made of layers 1 and 2 stacked along the heat path (left panel), the same $\dot Q$ passes through each layer in steady state, because no heat is stored at the interface. The temperature drop across each layer is

$$
T_1-T_\text{int}=\dot QR_1,\qquad T_\text{int}-T_2=\dot QR_2 .
$$

Add the two; the interface temperature cancels:

$$
T_1-T_2=\dot Q\left(R_1+R_2\right)
\quad\Rightarrow\quad
\dot Q=\frac{T_1-T_2}{R_1+R_2}.
$$

So series resistances add:

$$
R_\text{total}=R_1+R_2 .
$$

### Paths in parallel

When layers 1 and 2 sit side by side, each spanning the whole thickness between the same two faces (right panel), they share the same temperature difference and the heat divides between them:

$$
\dot Q_1=\frac{T_1-T_2}{R_1},\qquad \dot Q_2=\frac{T_1-T_2}{R_2}.
$$

The total is the sum:

$$
\dot Q=\dot Q_1+\dot Q_2=\left(T_1-T_2\right)\left(\frac1{R_1}+\frac1{R_2}\right)
\quad\Rightarrow\quad
\frac1{R_\text{total}}=\frac1{R_1}+\frac1{R_2}.
$$

The parallel rule assumes the two paths do not exchange heat sideways, so that each stays one-dimensional. When the paths have very different conductivities, the temperature at a given $x$ differs between them, some heat crosses between them, and the parallel model is an approximation.

### Resistance per unit area

For plane layers that all share the same area $A$, it is often neater to work per unit area. Multiplying $R$ by $A$ gives the **area-specific resistance** $R''=RA=L/k$, in m² K/W, and the heat flux is

$$
\dot q=\frac{\dot Q}{A}=\frac{\Delta T}{RA}=\frac{\Delta T}{R''}.
$$

Written as $RA$, this product reads like the resistance $R_A$ of layer A; keep the two apart.

### Worked example - the insulated plane block

*An insulated plane block has three layers: insulation A (3 cm, $k_A=0.048$ W m⁻¹ K⁻¹), block B (10 cm, $k_B=0.69$ W m⁻¹ K⁻¹) and insulation C (3 cm, $k_C=0.048$ W m⁻¹ K⁻¹), all with the same cross-sectional area. The outer faces are at $T_1=150$ °C and $T_4=10$ °C. Find $\dot q=\dot Q/A$, $T_2$ and $T_3$, and compare with the heat transfer rate for block B alone, without the insulation layers.*

The three layers are in series, all in SI units:

$$
R_\text{total}=R_A+R_B+R_C=\frac1A\left(\frac{L_A}{k_A}+\frac{L_B}{k_B}+\frac{L_C}{k_C}\right).
$$

Since $L_A=L_C$ and $k_A=k_C$, the two insulation terms are equal:

$$
R_\text{total}A=\frac{2\times0.03}{0.048}+\frac{0.1}{0.69}=1.2500+0.1449=1.3949\ \text{m}^2\,\text{K/W}.
$$

The heat flux is

$$
\dot q=\frac{T_1-T_4}{R_\text{total}A}=\frac{150-10}{1.3949}=100.36\ \text{W/m}^2 .
$$

A temperature difference has the same value in K and °C, though not in °F.

Every layer carries the same $\dot q$, so Fourier's law across layer A gives its temperature drop:

$$
\dot q_A=\frac{k_A}{L_A}\left(T_1-T_2\right)=\dot q
\quad\Rightarrow\quad
\Delta T_A=\frac{\dot qL_A}{k_A}=\frac{100.36\times0.03}{0.048}=62.73\ \text{K}.
$$

$$
T_2=T_1-\Delta T_A=150-62.73=87.27\ ^\circ\text{C}.
$$

Across block B,

$$
\Delta T_B=\frac{\dot qL_B}{k_B}=\frac{100.36\times0.1}{0.69}=14.55\ \text{K},
\qquad
T_3=T_2-\Delta T_B=87.27-14.55=72.73\ ^\circ\text{C}
$$

(72.73 with unrounded values carried through; the rounded figures shown give 72.72).

As a check, layer C has the same properties and geometry as A, so $\Delta T_C=\Delta T_A=62.73$ K, and $T_3-\Delta T_C=72.73-62.73=10.00$ °C, which is $T_4$ ✓.

Block B alone, with its faces at 150 °C and 10 °C:

$$
\dot q_B=\frac{k_B}{L_B}\Delta T=\frac{0.69}{0.1}\times140=966\ \text{W/m}^2 ,
$$

which is $966/100.36=9.6$ times the flux with the insulation in place. With block B as the wall of a house, two 3 cm layers of insulation cut the heat loss by almost a factor of ten, because they hold $2\times62.73=125.5$ K of the 140 K difference, 90 % of it.

![[at_w09a_insulated_block.png|900]]

> [!check] Steel bolts through the same block (ES3 Q1)
> Pierce the block with steel bolts ($d=1$ cm, $k=40$ W/(m K)) at 10 per m². Each bolt is a parallel path through all 16 cm with $R''=0.16/40=0.004$ m² K/W, against 1.3949 for the layers. The bolts occupy an area fraction $f=10\times\tfrac\pi4(0.01)^2=7.85\times10^{-4}$, and the parallel rule per unit area gives $\dot q=140\left[(1-f)/1.3949+f/0.004\right]=100.28+27.49=127.8$ W/m², the printed answer. Under 0.1 % of the area raises the flux by 27 %: a high-conductivity path in parallel with insulation acts as a thermal short circuit. Worked in full in [[SESA3029 Example Sheet 3 - Solutions#Q1. Composite wall pierced by steel bolts|ES3 Q1]].

## 6. Radial conduction in a long hollow cylinder

Not everything is a plane wall. Engineering often puts the resistance in the form of a cylinder or a hollow cylinder: the covering of an electrical wire is the obvious case, which insulates thermally as well as electrically and matters when a large current heats the wire, and lagging round a pipe is another. A long hollow cylinder has inside radius $r_i$, outside radius $r_o$ and length $L$, with its inner surface at $T_i$ and its outer surface at $T_o$. If the cylinder is long and the surface temperatures do not vary around it or along it, the temperature depends on $r$ alone and heat flows mainly in the radial direction. Here $L$ is the length of the cylinder along its axis, not a thickness.

![[at_w09a_radial_setup.png|900]]

The step that needs care is the area. In Fourier's law $A$ is always the surface **through** which the heat is conducted, and here that surface is not fixed. At any radius $r$ between $r_i$ and $r_o$ the heat crosses a cylinder whose cross-section is a circle of perimeter $2\pi r$; multiplying by the length gives the area, which grows with radius:

$$
A_r=2\pi rL .
$$

Fourier's law (1-D, in the radial direction) becomes

$$
\dot Q_r=-kA_r\frac{\mathrm dT}{\mathrm dr}=-2\pi krL\frac{\mathrm dT}{\mathrm dr}.
$$

An energy balance on the thin shell between $r$ and $r+\mathrm dr$ (steady, no generation) gives, exactly as for the plane wall, $\mathrm d\dot Q_r/\mathrm dr=0$: the same total heat rate crosses every cylindrical surface. The flux $\dot Q_r/A_r$ falls as $1/r$ because the same heat spreads over more area. Multiply both sides of Fourier's law by $\mathrm dr/r$, which removes $r$ and $\mathrm dr$ from the right-hand side and separates the variables, with $\dot Q_r$ a constant:

$$
\dot Q_r\frac{\mathrm dr}{r}=-2\pi kL\,\mathrm dT .
$$

Integrate from the inner surface to the outer one, applying the boundary conditions $T=T_i$ at $r=r_i$ and $T=T_o$ at $r=r_o$:

$$
\dot Q_r\int_{r_i}^{r_o}\frac{\mathrm dr}{r}=-2\pi kL\int_{T_i}^{T_o}\mathrm dT .
$$

The left integral is $\ln r$ between the limits and the right one is $T$:

$$
\dot Q_r\left(\ln r_o-\ln r_i\right)=-2\pi kL\left(T_o-T_i\right).
$$

Combine the logarithms and flip the sign on the right:

$$
\dot Q_r\ln\frac{r_o}{r_i}=2\pi kL\left(T_i-T_o\right)
\quad\Rightarrow\quad
\boxed{\dot Q_r=\frac{2\pi kL\left(T_i-T_o\right)}{\ln(r_o/r_i)}}
$$

In the form $\dot Q=\Delta T/R_\text{th}$, the thermal resistance of the cylindrical layer is

$$
\boxed{R_\text{th}=\frac{\ln(r_o/r_i)}{2\pi kL}}\qquad(\text{long cylinder, steady, radial, constant }k).
$$

The temperature profile follows from integrating only as far as a general radius $r$:

$$
\dot Q_r\ln\frac{r}{r_i}=2\pi kL\left(T_i-T\right).
$$

Substitute $\dot Q_r$ from the boxed result and solve for $T$:

$$
T(r)=T_i-\left(T_i-T_o\right)\frac{\ln(r/r_i)}{\ln(r_o/r_i)} .
$$

The profile is logarithmic, not linear: the temperature falls fastest near the inner surface, where the area is smallest and the flux largest.

### When a tube can be treated as a plane wall

For a thin wall, $r_o=r_i+t$ with $t\ll r_i$. The logarithm expands as

$$
\ln\frac{r_o}{r_i}=\ln\left(1+\frac{t}{r_i}\right)=\frac{t}{r_i}-\frac12\left(\frac{t}{r_i}\right)^2+\dots
$$

Keeping the first term,

$$
R_\text{th}\simeq\frac{t/r_i}{2\pi kL}=\frac{t}{k\,(2\pi r_iL)}=\frac{t}{kA_i},
$$

the plane-wall resistance with the inner area. Using the inner area overestimates the resistance, by 10 % when $r_o/r_i=1.2$ and 44 % when $r_o/r_i=2$. Using the area at the mean radius $\bar r=(r_i+r_o)/2$ is far better: 0.3 % low at $r_o/r_i=1.2$ and 3.8 % low at 2.

![[at_w09a_radial_profiles.png|900]]

## 7. Multiple cylindrical layers

Layers of different materials wrapped round each other form cylindrical sections in series, exactly like the plane layers of §5. For three layers A, B and C between radii $r_1$, $r_2$, $r_3$ and $r_4$, with temperatures $T_1$ to $T_4$ at those radii and all of length $L$,

$$
R_\text{total}=\frac{\ln(r_2/r_1)}{2\pi k_AL}+\frac{\ln(r_3/r_2)}{2\pi k_BL}+\frac{\ln(r_4/r_3)}{2\pi k_CL},\qquad
\dot Q=\frac{T_1-T_4}{R_\text{total}} .
$$

The plane-wall equivalent from 5.1 is $R_\text{total}=L_1/k_AA+L_2/k_BA+L_3/k_CA$, with $L_1$, $L_2$, $L_3$ the layer thicknesses. In the cylindrical sum each layer's resistance depends on the ratio of its radii, so the same thickness of insulation is worth more near the axis than far from it. Solid rocket motors are built this way: insulation and casing wrapped round the propellant form a multi-layer cylinder in which heat conducts mainly radially.

## 8. Conduction in a spherical shell

A spherical shell of inner radius $r_i$ at $T_i$ and outer radius $r_o$ at $T_o$ is also one-dimensional when the temperature depends on radius alone. The area for heat flow is now

$$
A_r=4\pi r^2 ,
$$

and Fourier's law is

$$
\dot Q_r=-kA_r\frac{\mathrm dT}{\mathrm dr}=-4\pi kr^2\frac{\mathrm dT}{\mathrm dr}.
$$

The shell balance again makes $\dot Q_r$ the same at every radius. Separate the variables:

$$
\dot Q_r\frac{\mathrm dr}{r^2}=-4\pi k\,\mathrm dT .
$$

Integrate between the two surfaces:

$$
\dot Q_r\int_{r_i}^{r_o}\frac{\mathrm dr}{r^2}=-4\pi k\int_{T_i}^{T_o}\mathrm dT .
$$

The integral of $r^{-2}$ is $-1/r$:

$$
\dot Q_r\left[-\frac1r\right]_{r_i}^{r_o}=\dot Q_r\left(\frac1{r_i}-\frac1{r_o}\right)=-4\pi k\left(T_o-T_i\right).
$$

So

$$
\boxed{\dot Q_r=\frac{4\pi k\left(T_i-T_o\right)}{1/r_i-1/r_o}},\qquad
\boxed{R_\text{th}=\frac{1}{4\pi k}\left(\frac1{r_i}-\frac1{r_o}\right)=\frac{r_o-r_i}{4\pi k\,r_ir_o}}
$$

The second form of $R_\text{th}$ comes from putting the bracket over a common denominator. For a thin shell, $r_ir_o\simeq r_i^2$ and $R_\text{th}\simeq t/(k\,4\pi r_i^2)$, the plane-wall value with the inner area. Integrating only to a general radius gives the profile

$$
T(r)=T_i-\left(T_i-T_o\right)\frac{1/r_i-1/r}{1/r_i-1/r_o},
$$

which curves more sharply than the cylinder's, since the area grows as $r^2$ rather than $r$ (figure in §6).

Cryogenic propellant tanks for liquid rocket engines are nearly spherical and are wrapped in multi-layer insulation, which is what keeps the propellant from boiling off.

### Worked example - boil-off from a spherical oxygen tank (suggested, not lecturer-set)

*A spherical liquid-oxygen tank has an inner radius of 1.50 m and is wrapped in 5 cm of insulation with $k=0.02$ W/(m K). The inner surface of the insulation is at the LOX temperature, 90 K, and the outer surface at 290 K. Find the heat leak and the boil-off rate, taking the latent heat of vaporisation of oxygen as $h_{fg}=213$ kJ/kg.*

With $r_i=1.50$ m and $r_o=1.55$ m,

$$
R_\text{th}=\frac{1}{4\pi(0.02)}\left(\frac1{1.50}-\frac1{1.55}\right)=\frac{0.021505}{0.25133}=0.08557\ \text{K/W}.
$$

$$
\dot Q=\frac{290-90}{0.08557}=2337\ \text{W}.
$$

All of this heat goes into vaporising liquid at its saturation temperature, so

$$
\dot m=\frac{\dot Q}{h_{fg}}=\frac{2337}{213\times10^3}=0.01097\ \text{kg/s}=948\ \text{kg/day}.
$$

The tank holds $\tfrac43\pi(1.50)^3\times1141=16.1$ t of LOX, so it loses 5.9 % a day, which is why tanks are topped up until launch. The plane-wall estimate $t/(k\,4\pi r_i^2)$ gives 0.0884 K/W, 3.3 % high. If the outer surface is instead exposed to air at 290 K with $h=5$ W/(m² K), a convection resistance $1/(h\,4\pi r_o^2)=0.0066$ K/W joins in series and the leak falls to 2169 W.

## 9. Convection heat transfer

Convection is heat transfer through bulk fluid motion: a bulk of fluid flowing over a surface, which may be a solid or a liquid surface. When the fluid moves, heat is transferred by convection; in the absence of bulk fluid motion it is transferred by conduction alone. Like conduction, convection requires a material medium.

The gas-turbine blade is the standard aerospace case. Combustion in an aero engine produces gas at around 1800–2000 °C, and that temperature is what the fuel pays for, but no turbine blade survives it: blade alloys melt at around 1250 °C, and well before that an overheated blade creeps, growing in length under the centrifugal load, which a turbine with tight tip clearances cannot tolerate. Cold air taken from the engine casing is mixed into the combustion products just downstream of the combustor, so the gas reaching the turbine is cooler, around 1500 °C, though still above the melting point. The blades are then cooled. Air from the casing is fed through the blade and out of rows of small cooling holes as microjets, which cover the surface in a blanket of cool air (film cooling), so the hot gas, particularly at the first turbine row, never touches the metal; a ceramic coating on the blade helps but is not enough on its own. Turbine entry temperature is a key selling point of an engine, because a higher one gives more performance and a small gain in blade life saves an airline a great deal over the engine's life.

There are two types of convective heat transfer:

- **Forced convection**, where the fluid is forced over the hot object by external means, a fan or a pump: a hot plate cooled by a fan, or blowing over a hot cup of coffee.
- **Free convection** (natural convection), where there is no external forcing and the fluid motion is generated by density gradients. A hot surface in initially still air heats the air next to it by conduction; the heated air becomes less dense and buoyancy pushes it up; continuity means it cannot leave a void, so colder air from the surroundings takes its place, is heated in turn, and a steady buoyancy-driven current carries the heat away. Letting a cup of coffee cool by itself is free convection. Buoyancy needs gravity, so in orbit, with little or no effective gravity, free convection almost disappears.

The rate of convective heat transfer is governed by how fast the fluid moves, in the same way that conduction is governed by how readily the particles pass on their vibration: a faster flow washes away more heat. A gentle forced flow is possible, but a fan easily gives 5–6 m/s, while the free-convection current round a cup of coffee at 100 °C moves at the order of centimetres per second. So forced convection is generally the stronger of the two. Free convection is still far from insignificant: the motions of the atmosphere and the oceans are dominated by it, which makes it the most important heat transfer mechanism in natural systems.

### Newton's law of cooling

Both types are described by **Newton's law of cooling**,

$$
\dot Q=hA_s\left(T_s-T_\infty\right),
$$

where $h$ is the heat transfer coefficient in W/(m² K), $A_s$ the heat transfer surface area in m², $T_s$ the temperature of the surface and $T_\infty$ the temperature of the fluid far from the surface. The area is the surface **over** which heat is convected, not the one through which it is conducted: the fluid flowing over the plate takes heat from the face it touches. In both modes the heat flows normal to the surface. For the sign: with $T_s>T_\infty$, $\dot Q$ is the heat leaving the surface.

The law is purely algebraic, simpler in form than Fourier's law, and all the difficulty of convection is hidden in $h$. The thermal conductivity $k$ is a material property: given the material and its temperature, it can be read from a table and nothing else changes it. The heat transfer coefficient $h$ depends on the fluid, as $k$ does, but also on the fluid dynamics of the whole system: laminar or turbulent flow, a jet or a wake, an internal or an external flow, and hundreds of other configurations change it substantially. So no table of $h$ exists. Finding it exactly needs CFD or accurate measurement; engineering estimates come from correlations, the subject of [[SESA3029 W09b - Convective Heat Transfer and the Reynolds Analogy|W09b]].

### Convection as a thermal resistance

Written as $\dot Q=\Delta T/R$, Newton's law gives the **convection resistance**

$$
\boxed{R_\text{th}=\frac{1}{hA_s}}\qquad(\text{K/W}),
$$

so the electrical analogy holds for convection too, and a fluid on either side of a wall adds a resistor at each end of the network.

## 10. Walls and tubes with convection on both sides

In the insulated block of 5.1 the face temperatures were given. More often the temperatures known are those of the fluids on either side, and the boundary conditions of the wall come from convection. A house wall is the usual case. Inside there is free convection, driven by the occupants and the heating; outside, the wind drives forced convection. Each has its own heat transfer coefficient, and each adds a thermal resistance to the conduction resistances of the layers. The fluid temperatures $T_1$ and $T_5$ are taken far enough from the wall that the fluid temperature no longer varies; close to the wall it does, across the thermal boundary layer of [[SESA3029 W09b - Convective Heat Transfer and the Reynolds Analogy|W09b]], which also sets how far is far enough. In this plane case the convection area is the same as the conduction area $A$.

For a plane wall of two layers A and B, area $A$, between a hot fluid at $T_1$ (coefficient $h_1$) and a cold fluid at $T_5$ (coefficient $h_2$), the heat passes through four resistances in series, convection 1, conduction through A, conduction through B and convection 2:

$$
R_\text{total}=\frac1{h_1A}+\frac{L_A}{k_AA}+\frac{L_B}{k_BA}+\frac1{h_2A},\qquad
\dot Q=\frac{T_1-T_5}{R_\text{total}} .
$$

Once $\dot Q$ is known the interface temperatures follow from $\Delta T_j=\dot QR_j$, step by step from either end, as in §5. The temperature profile is curved in each fluid, where the boundary layer carries the drop, and straight in each solid layer, steeper in the layer with the smaller $k$.

### Worked example - the 5.1 block between two fluids (suggested, not lecturer-set)

*Put the insulated block of §5 between air at 150 °C with $h_1=10$ W/(m² K) and air at 10 °C with $h_2=25$ W/(m² K). Find the heat flux and the two surface temperatures.*

Per unit area,

$$
R''_\text{total}=\frac1{h_1}+1.3949+\frac1{h_2}=0.100+1.3949+0.040=1.5349\ \text{m}^2\,\text{K/W},
$$

$$
\dot q=\frac{150-10}{1.5349}=91.21\ \text{W/m}^2 .
$$

The surface temperatures come from Newton's law on each side:

$$
T_{s1}=150-\frac{\dot q}{h_1}=150-9.12=140.88\ ^\circ\text{C},\qquad
T_{s2}=10+\frac{\dot q}{h_2}=10+3.65=13.65\ ^\circ\text{C}.
$$

Through the layers, $T_2=140.88-91.21\times0.625=83.87$ °C and $T_3=83.87-91.21\times0.1449=70.65$ °C, and $70.65-91.21\times0.625=13.65$ °C closes the chain ✓. The two convection resistances are only 9 % of the total, so they lower the flux by 9 %. Without the insulation, the same two fluids drive $140/(0.100+0.145+0.040)=491$ W/m² through block B alone: half the 966 W/m² of §5, because the convection resistances are now comparable with the wall's.

![[at_w09a_convection_wall.png|900]]

### Composite tubes

The same electrical analogy applies to composite cylindrical tubes. A hollow stainless-steel tube carries hot water and is surrounded by an insulation layer whose outer surface is exposed to air, like a water line in a house. With the water at $T_1$ inside radius $r_1$, steel from $r_1$ to $r_2$, insulation from $r_2$ to $r_3$ and air at $T_5$ outside, for a tube of length $L$,

$$
R_\text{total}=\frac{1}{h_1\,2\pi r_1L}+\frac{\ln(r_2/r_1)}{2\pi k_AL}+\frac{\ln(r_3/r_2)}{2\pi k_BL}+\frac{1}{h_2\,2\pi r_3L},\qquad
\dot Q=\frac{T_1-T_5}{R_\text{total}} .
$$

Each convection resistance uses the area of the surface it acts on: the inner surface $2\pi r_1L$ for the water and the outer surface $2\pi r_3L$ for the air.

### Worked example - an insulated hot-water pipe (suggested, not lecturer-set)

*Water at 80 °C flows in a stainless-steel tube ($r_1=10$ mm, $r_2=12$ mm, $k_A=15$ W/(m K)) covered by insulation out to $r_3=30$ mm ($k_B=0.04$ W/(m K)). The water-side coefficient is $h_1=1000$ W/(m² K) and the air outside is at 20 °C with $h_2=10$ W/(m² K). Find the heat loss per metre and the outer surface temperature.*

Per metre of tube ($L=1$ m):

$$
R_1=\frac{1}{1000\times2\pi(0.010)}=0.01592,\qquad
R_A=\frac{\ln(12/10)}{2\pi(15)}=0.00193,
$$

$$
R_B=\frac{\ln(30/12)}{2\pi(0.04)}=3.6458,\qquad
R_2=\frac{1}{10\times2\pi(0.030)}=0.5305\quad(\text{all K/W}).
$$

$$
R_\text{total}=4.1942\ \text{K/W},\qquad \dot Q=\frac{80-20}{4.1942}=14.31\ \text{W per metre}.
$$

Marching through the network, the inner surface is at $80-14.31\times0.01592=79.77$ °C, the steel–insulation interface at $79.74$ °C and the outer surface at $T_3=79.74-14.31\times3.6458=27.59$ °C. The steel and the water film together take less than 0.3 K: almost all the drop is across the insulation, with most of the rest in the outer air film. Using the inner area for the outer coefficient as well would give $R_2=1.59$ K/W and $\dot Q=11.4$ W/m, 20 % low. The bare tube, with air directly on the steel at $r_2$, loses 44.6 W/m. The insulation also enlarges the outer surface, which lowers $R_2$; for a thin pipe that effect can win, which is the critical thickness of insulation in [[SESA3029 W09c - Critical Thickness of Insulation and Fins|W09c]].

![[at_w09a_composite_tube.png|900]]

## 11. The Nusselt number

Dimensionless numbers simplify fluid-flow problems by reducing the number of variables, and they also carry a physical meaning: the Reynolds number is the ratio of inertia forces to viscous forces. Convective heat transfer has its own, and the most widely used is the **Nusselt number**, the dimensionless form of the heat transfer coefficient,

$$
\text{Nu}=\frac{hL}{k},
$$

where $L$ is a characteristic length of the problem and $k$ the thermal conductivity **of the fluid**. The length is the same one the Reynolds number of the flow uses: the diameter for flow in a pipe, the distance from the leading edge for flow over a flat surface. The units confirm that Nu is dimensionless: $h$ is in W/(m² K), so $hL$ is in W/(m K), the units of $k$. The fluid's conductivity appears because, right at the wall, the fluid is at rest relative to the surface and the heat enters it by conduction; $h$ measures how much the fluid motion enhances that. Correlations for convective heat transfer are written for Nu in the same way that a flow is characterised by its Reynolds number ([[SESA3029 W09b - Convective Heat Transfer and the Reynolds Analogy|W09b]]).

The physical meaning of Nu comes from a fluid layer of thickness $L$ with a temperature difference $\Delta T=T_2-T_1$ across it. With bulk fluid motion the heat crosses by convection,

$$
\dot Q_\text{conv}=hA\Delta T .
$$

If the layer is motionless, the heat crosses by conduction only (particle collisions), as through a plane wall:

$$
\dot Q_\text{cond}=kA\frac{\Delta T}{L}.
$$

The ratio is

$$
\frac{\dot Q_\text{conv}}{\dot Q_\text{cond}}=\frac{hA\Delta T}{kA\Delta T/L}=\frac{hL}{k}=\text{Nu}.
$$

So the Nusselt number is the enhancement of heat transfer through a fluid layer by convection, relative to conduction through the same layer at rest: $\text{Nu}=10$ means convection transfers ten times as much heat as conduction would in the same problem. A larger Nu means more effective convection; $\text{Nu}>1$ means convection contributes more; $\text{Nu}=1$ is pure conduction with no bulk fluid motion. That makes Nu a direct, quantitative measure of how much heat transfer is gained by engineering the flow round or inside an object. This reading of $\text{Nu}=1$ holds when $L$ is the layer thickness across which $\Delta T$ acts. With another choice of $L$, such as the length of a plate along the flow (W09b), Nu is still $hL/k$ but its value is no longer measured against 1.

As a guide to magnitudes:

| Flow | Typical Nu |
|---|---|
| laminar flow, and most free convection (laminar or slightly turbulent) | order 1, roughly 1–10 |
| turbulent flow | order 10–100 |
| flows with phase change, such as boiling on a hot surface | above 1000 |

These are order-of-magnitude guides for a Nusselt number based on a thickness comparable with the fluid layer across which the heat crosses. A correlation that uses a length along the flow gives far larger values for the same physics: a laminar flat plate in air ($\mathrm{Pr}=0.7$) at $\mathrm{Re}_x=3\times10^5$ already has $\mathrm{Nu}_x=0.332\,\mathrm{Re}_x^{1/2}\mathrm{Pr}^{1/3}=161$ (W09b). So the table compares regimes; it is not a check on a correlation's answer.

Which mode dominates depends on whether the fluid can move. In water boiling in a pot, warm air circulated round a room by a radiator, and a processor cooled by a fan, the fluid moves and convection dominates. In a double- or triple-glazed window the 6–10 mm gap is kept narrow so that the air barely circulates; it then behaves as a still layer, Nu stays close to 1, and the gap acts as a conduction resistance with the low $k$ of air.

> [!check] Double glazing as a conduction resistance (suggested, not lecturer-set)
> With still air ($k=0.026$ W/(m K)) in an 8 mm gap, $\text{Nu}=1$ gives $h=k/L=3.25$ W/(m² K), i.e. $R''=L/k=0.308$ m² K/W. A single 4 mm pane ($k=0.96$) has $R''=0.0042$. With $h=8$ inside, $h=20$ outside and a 20 K difference, the single pane passes $20/(0.125+0.0042+0.050)=112$ W/m² and the 4–8–4 double unit $20/(0.125+0.316+0.050)=40.7$ W/m². The glass contributes almost nothing in either case; the still air does the work.

## Problem-solving workflow

1. Identify the geometry (plane, long cylinder, sphere) and check that steady, one-dimensional conduction without heat generation is a fair model.
2. List every resistance between the two known temperatures, in order: convection $1/hA_s$ at each fluid boundary, then each solid layer with its own formula. Decide which are in series and which in parallel.
3. Convert all lengths to metres, and keep either $R$ (K/W) or $R''=RA$ (m² K/W) throughout, not a mixture. For cylinders and spheres use $R$, since the area changes with radius.
4. $\dot Q=\Delta T_\text{overall}/R_\text{total}$; for a wall per unit area, $\dot q=\Delta T/R''_\text{total}$.
5. For an interface temperature, subtract $\dot QR_j$ layer by layer from the hot end, and check that the last step lands on the cold-end temperature.
6. For a sanity check, the largest temperature drop sits across the largest resistance.

## Terminology and alternative names

| Course term | Also called | Where the course uses it | Note |
|---|---|---|---|
| modes of heat transfer | heat transfer mechanisms | L5.1 slides 3–7; L5.2 slide 1 | Slide 7 is titled "Heat transfer mechanisms" |
| Fourier's law of heat conduction | Fourier's law; the conduction rate equation | L5.1 slide 11; L5.2 slides 3, 7 | |
| electrical (resistance) analogy | thermal circuit | L5.1 slides 13–14; L5.2 slides 5, 14–16 | |
| thermal resistance $R_\text{th}$ | conduction or convection resistance; $R$ | L5.1 slides 13–17; L5.2 slides 4–7, 14 | |
| $RA$ (L5.1 slide 17) | area-specific (unit-area) thermal resistance $R''$; R-value (building industry) | L5.1 slide 17 | Not $R_A$, the resistance of layer A |
| heat transfer coefficient $h$ | convection coefficient; convective heat transfer coefficient; film coefficient | L5.2 slides 13, 17; "convection coefficient" spoken, L5-2 ll. 365, 375 | |
| free convection | natural convection; buoyancy-driven flow | L5.2 slides 11–12; L5-2 ll. 297, 332 | the lecture uses "free" and "natural" interchangeably |
| cooling air from the engine casing | compressor bleed air; secondary air; dilution air (mixed in before the turbine) | L5-2 ll. 206–209, 242 | slide 10 calls it "bypass air" (see the slips) |

## Links

- Parent: [[SESA3029 Aerothermodynamics Hub]]
- Previous: [[SESA3029 W07c - Ackeret Theory and Optimum Supersonic Aerofoils]] (end of the compressible-flow block)
- Next: [[SESA3029 W09b - Convective Heat Transfer and the Reynolds Analogy]] (finding $h$; Reynolds analogy), then [[SESA3029 W09c - Critical Thickness of Insulation and Fins|W09c]], [[SESA3029 W09d - Thermal Radiation|W09d]], [[SESA3029 W09e - Numerical Methods in Conduction|W09e]], [[SESA3029 W09f - Heat Exchangers|W09f]]
- New concepts: [[Modes of Heat Transfer]] · [[Fourier's Law of Heat Conduction]] · [[Thermal Conductivity]] · [[Thermal Resistance]] · [[Radial Conduction in Cylinders and Spheres]]
- Convection concepts first met in §§9–11 and developed in W09b: [[Newton's Law of Cooling]] · [[Nusselt Number]]
- Earlier years: [[SESA1016 T2 - Work, Heat and the First Law]] (heat and its sign) · [[Heat Equation]] and [[MATH2048 PDE3 - The Heat Equation]] (the transient equation; this note is its steady 1-D limit) · [[SESA2029 A3 - Iterative Solution of the Steady Heat Equation]] (numerical solution) · [[Blackbody Radiation]] (SESA2024)
- Practice: [[SESA3029 Example Sheet 3 - Solutions#Q1. Composite wall pierced by steel bolts|ES3 Q1]] · [[SESA3029 Past Papers - Question Map]] (heat-transfer questions, Weeks 9–12)
- Formulae: [[SESA3029 Formula Sheet]] (the exam sheet gives the four resistances; Nusselt correlations come with the question)

## Sources

- `Lecture5.1.pdf` (L5.1, 20 slides) and `Lecture 5-1 (2025-26 version).txt` (L5-1, 470 lines; filed Thu 19 Nov; last year's recording of the same deck, not of this year's lecture, covering all 20 slides; the file starts mid-sentence, so the opening of the recording is missing): why heat transfer matters (slide 2; ll. 9–48), modes of heat transfer on a re-entry capsule (slides 3–6; ll. 49–108), direction of heat transfer and thermal equilibrium (slide 7; ll. 109–134), heat transfer rate and flux (slide 8; ll. 135–148), conduction, Fourier's law and thermal conductivity (slides 9–12; ll. 149–251), the electrical resistance analogy and plane walls in series and parallel (slides 13–14; ll. 252–302), the insulated plane block example (slides 15–20; ll. 303–469).
- `Lecture5.2.pdf` (L5.2): Lecture 5.2, 19 slides. Recap of 5.1 (slide 1), conduction in cylinders, multiple cylindrical layers and spheres with the solid-rocket and cryogenic-tank examples (3–8), convection heat transfer, Newton's law of cooling and the convection resistance (9–14), the plane wall and composite tube with convection boundaries (15–16), the Nusselt number (17–18) and conduction against convection (19).
- `20 November 2026 at 16_48_17.txt` (**L5-2**, Fri 20 Nov 2026, Dr Nader Karimi, 531 lines; this year's Lecture 5.2):
  - recap skipped; Lecture 5.1 (Thu 19 Nov) was not recorded, and last year's recording stands in for it (ll. 8–19);
  - the electrical analogy recalled (ll. 20–32); conduction through a hollow cylinder, the area $2\pi rL$ and the integration to $R_\text{th}=\ln(r_o/r_i)/2\pi kL$, slides 3–4 (ll. 33–108);
  - multiple cylindrical layers and the solid rocket motor, slides 5–6 (ll. 109–139); the spherical shell and cryogenic tanks, slides 7–8 (ll. 140–185);
  - convection: turbine-blade cooling, dilution air and film cooling, slide 10 (ll. 186–253); forced and free convection, buoyancy, and which is stronger, slides 11–12 (ll. 254–359);
  - Newton's law of cooling, why $h$ is hard to find, and the convection resistance, slides 13–14 (ll. 360–415);
  - the plane wall with convection on both sides, the example held over from Lecture 5.1, slide 15, and the radial version, slide 16 (ll. 416–455);
  - dimensionless numbers, the Nusselt number, its meaning as convection over conduction and its typical ranges, slides 17–18 (ll. 456–531). Slide 19 was not reached.
- Dr Nader Karimi teaches Section 5 (no lecturer is named on either deck). §§1–5 are checked against `Lecture 5-1 (2025-26 version).txt`, last year's recording, since this year's 5.1 was not recorded. §§6–11 are reconciled with this year's L5-2 transcript. The double-glazing paragraph at the end of §11 is written from slide 19, which the lecture did not reach.
- Worked examples marked "suggested, not lecturer-set" use numbers chosen here to exercise the slide 5.2 formulas, which carry no numerical example of their own. Every number in the note was checked in Python.
- `ExampleSheet3(1).pdf`, Q1 (composite wall pierced by steel bolts, answer 127.8 W/m²): the block of L5.1 slide 15 with a parallel path added; the sheet agrees with the slides.
- Figures: `generate_aerothermo_w09a_figures.py` (`at_w09a_modes.png`, `at_w09a_fourier_sign.png`, `at_w09a_insulated_block.png`, `at_w09a_series_parallel.png`, `at_w09a_radial_setup.png`, `at_w09a_radial_profiles.png`, `at_w09a_convection_wall.png`, `at_w09a_composite_tube.png`). Every number on a figure is computed in the script from the same data as the worked examples.
- Çengel, *Heat Transfer: A Practical Approach* (the convection sketches on L5.2 slide 11 are from it), Chapters 1–3; Incropera and DeWitt, *Fundamentals of Heat and Mass Transfer*, Chapters 1–3.

## Self-study tasks

Tasks citing L5-1 come from `Lecture 5-1 (2025-26 version).txt` (last year's recording of the same deck); the verification check on $T_4$ is set in that recording (L5-1, ll. 434–443). Tasks citing L5-2 come from this year's Lecture 5.2 (Fri 20 Nov), which sets no exercise of its own: it leaves the end of the cylinder integration to be done (l. 97) and poses class questions on blade damage and on forced against free convection. Tasks marked so are suggested, not lecturer-set.

### Core

- [ ] **(L5.1 slides 15–20; L5-1, ll. 303–465; $T_4$ check set at ll. 434–443)** Insulated plane block: find $\dot q$, $T_2$ and $T_3$, check $T_4$ from $T_3$ and $\Delta T_C=\Delta T_A$, and compare with block B alone. Answers 100.36 W/m², 87.27 °C, 72.73 °C, $T_4=10.00$ °C; 966 W/m² without insulation. → [[#Worked example - the insulated plane block]]
- [ ] **(ES3 Q1)** The same block pierced by steel bolts, 10 per m². Answer 127.8 W/m². → [[SESA3029 Example Sheet 3 - Solutions#Q1. Composite wall pierced by steel bolts|ES3 Q1]]
- [ ] **(L5.2 slide 4; L5-2, ll. 58–108, rearrangement left to do at l. 97)** Integrate Fourier's law for a long hollow cylinder, with the area $2\pi rL$ at radius $r$, and derive $\dot Q_r$ and $R_\text{th}=\ln(r_o/r_i)/2\pi kL$, then the temperature profile. → [[#6. Radial conduction in a long hollow cylinder]]
- [ ] **(L5.2 slide 7; L5-2, ll. 152–176)** The same for a spherical shell, with area $4\pi r^2$ and multiplying by $\mathrm dr/r^2$: $\dot Q_r=4\pi k(T_i-T_o)/(1/r_i-1/r_o)$. → [[#8. Conduction in a spherical shell]]
- [ ] **(L5.2 slides 15–16; L5-2, ll. 416–455)** Write the resistance network for a plane wall and for a composite tube with convection on both sides, with the correct area in each convection term; then do the insulated pipe example. Answer 14.31 W/m, outer surface 27.6 °C. → [[#Worked example - an insulated hot-water pipe (suggested, not lecturer-set)]]

### Further practice

- [ ] **(L5.1 slides 10–11; L5-1, ll. 150–187)** Derive Fourier's law from $\dot Q\propto A(T_1-T_2)/L$ and explain the minus sign. → [[#2. Fourier's law of heat conduction]]
- [ ] **(L5.1 slide 7; L5-1, ll. 125–134)** Two blocks at 70 °C joined by a rod: what happens? Answer: no heat flows; they are in thermal equilibrium. → [[#Direction and rate]]
- [ ] **(L5.1 slide 12; L5-1, ll. 223–244)** Water or iron, which has the higher $k$, and by how much? Answer: iron, 132 times. → [[#3. Thermal conductivity]]
- [ ] **(L5.1 slide 14; L5-1, ll. 276–302)** Derive the series and parallel rules for thermal resistances. → [[#5. The electrical analogy and thermal resistance]]
- [ ] **(L5.2 slides 10–13; class questions at L5-2, ll. 225–233 and 311–353)** How does an overheated turbine blade fail, and how is it protected? Which cools a coffee cup faster, forced or free convection, and why? Why is the area in Newton's law the surface the heat is convected over, and why is there no table of $h$? → [[#9. Convection heat transfer]] and [[#Newton's law of cooling]]
- [ ] **(L5.2 slides 17–18; L5-2, ll. 472–529)** Check that Nu is dimensionless, give the typical Nu of laminar, turbulent and boiling flows, and show that $\text{Nu}=\dot Q_\text{conv}/\dot Q_\text{cond}$ for a fluid layer, and say why the fluid's $k$ appears. → [[#11. The Nusselt number]]
- [ ] **(L5.2 slide 19, not reached in L5-2)** For a boiling pot, a radiator, a fan-cooled processor and double glazing, say whether conduction or convection dominates. → [[#11. The Nusselt number]]
- [ ] (suggested, not lecturer-set; L5.2 slide 8) Boil-off from the 1.50 m LOX tank. Answer 2337 W, 948 kg/day. → [[#Worked example - boil-off from a spherical oxygen tank (suggested, not lecturer-set)]]
- [ ] (suggested, not lecturer-set) Show that the cylinder resistance tends to $t/(kA_i)$ for a thin wall, and find the error at $r_o/r_i=1.2$. Answer +9.7 %. → [[#When a tube can be treated as a plane wall]]

## Transcript and slide slips

> [!warning] L5.1 slides 17–20: two values of the heat flux, and a wrong $T_2$
> Where: [[#Worked example - the insulated plane block]].
>
> Slide 17 gives $\dot q=140/1.3949=100.39$ W/m², and slide 20 repeats 100.39; the quotient is 100.36 W/m², the value slides 18–19 use. Slide 18 then writes $T_2=150-62.73=82.27$ °C; the subtraction gives 87.27 °C, which is the value slide 19 uses to get $T_3=72.73$ °C. Both slips are read aloud in `Lecture 5-1 (2025-26 version).txt` (see table below). On slide 20, $k_B$ is printed as "0.69 W m⁻¹ K" in the block-alone line; it is W m⁻¹ K⁻¹.

> [!warning] L5.2 slide 3: "thin cylinder"
> Where: [[#6. Radial conduction in a long hollow cylinder]].
>
> The slide gives "thin cylinder → heat flows mainly in the radial direction". What makes the heat flow radial is a **long** cylinder (end effects negligible) with surface temperatures uniform round and along it, as in the slide's own first line, "long hollow cylinder". A thin wall is not needed: the logarithmic result holds for any $r_o/r_i$, and it is for a thin wall that the result reduces to the plane wall.

> [!warning] L5.2 slide 10: "Bypass air" for the turbine cooling air
> Where: [[#9. Convection heat transfer]].
>
> The slide says bypass air is passed through the cooling holes. The cooling and dilution air is taken from the engine casing, i.e. bled from the compressor through the core, not from the fan's bypass duct; asked how the combustion products are cooled, the class answer "bypass" was accepted in substance with the remark that this air is not called bypass (L5-2, ll. 205–209).

> [!warning] L5.2 slide 16: one area for two convection resistances, and $L_A$, $L_B$
> Where: [[#Composite tubes]].
>
> The slide writes the convection resistances as $1/h_1A$ and $1/h_2A$ and the conduction terms as $\ln(r_2/r_1)/2\pi k_AL_A$ and $\ln(r_3/r_2)/2\pi k_BL_B$. The two convection areas differ: $2\pi r_1L$ inside and $2\pi r_3L$ outside (using one area for both gives 11.4 instead of 14.3 W/m in the pipe example). Both conduction terms use the same tube length $L$; $L_A$ and $L_B$ in the plane-wall slide before it are layer thicknesses, which have no place in the cylindrical formula.

### Transcript slips (L5-1, 2025–26 recording)

These slips are from last year's recording, not this year's lecture; this year's 5.1 was not recorded, so last year's recording is the reference. Whisper writes *"15 degrees Celsius"* for 1500 °C (ll. 27–28), *"12-50 degrees Celsius"* for 1250 °C (l. 29), *"16 degrees Celsius"* for 1600 °C (ll. 32, 59), *"processes"* for processors (ll. 35, 38), *"pan"* for fan (l. 91), *"dou T by dou xi"* for $\partial T/\partial x_i$ (l. 199), *"playing balls"* for plane walls (l. 276), *"panel case"* for parallel case (l. 292) and *"SA unit"* for SI units (l. 366). These are not listed below.

> [!warning] Slips in `Lecture 5-1 (2025-26 version).txt` (L5-1, 2025–26 recording)
> | Where | Said | Correct |
> |---|---|---|
> | ll. 296–297 | *"the total resistance is 1 by R1 plus 1 by R2"* | $1/R_\text{total}=1/R_1+1/R_2$: the reciprocal of the total resistance, not $R_\text{total}$ itself (§5) |
> | l. 326 | *"temperature difference T3"* | interface temperature $T_3$ between block B and insulation layer C (§5) |
> | l. 352 | *"Lb by Kb into B"* | $L_B/(k_B A)$: cross-sectional area $A$, not $B$ (the following term $k_C A$ is self-corrected on the same line) |
> | ll. 357–359 | *"R total by R"* | $R_\text{total}A$, multiplying $R_\text{total}$ by $A$ to form the area-specific resistance $R''=1.3949$ m² K/W (§5) |
> | ll. 381, 405 | *"100.39"* W/m² | $140/1.3949=100.36$ W/m² (repeats the slide 17 slip above) |
> | ll. 425–426 | *"150 minus 62.73 and that gives us around 82 degrees Celsius"* | $T_2=150-62.73=87.27$ °C (repeats the slide 18 slip, 82.27 °C; the next step $T_3=72.73$ °C uses 87.27 °C) |
> | l. 452 | *"966 watt per meter"* | $966$ W/m² (heat flux, per square metre) |

### Transcript slips (L5-2, 20 Nov)

Where: [[#6. Radial conduction in a long hollow cylinder]], [[#8. Conduction in a spherical shell]], [[#9. Convection heat transfer]] and [[#11. The Nusselt number]].

The first four rows are slips of substance in the spherical-shell derivation and the units of $k$; the slides have the right forms. Whisper also writes *"G0"* for $T_o$ (l. 74), *"the coverage of a wire"* for its covering (l. 34) and *"Lenz scale"* for length scale (ll. 478–484); these are not listed.

| Line | Said | Correct |
|---|---|---|
| ll. 152–154 | *"What happens if the shape is a cylindrical shape?"* | a spherical shape: the cylinder was done just before, and the next lines treat the sphere |
| l. 158 | *"the surface area at any arbitrary radii R will be 2 pi times R squared"* | $4\pi r^2$, the area of a sphere; the Fourier's law on the next line uses $4\pi kr^2$ |
| l. 172 | *"the thermal resistance for this configuration will be 1 over pi k"* | $\dfrac{1}{4\pi k}\left(\dfrac1{r_i}-\dfrac1{r_o}\right)$ (slide 7) |
| ll. 487–488 | *"thermal conductivity, it was watts meter times Kelvin"* | W/(m K), watts per metre per kelvin (slide 17) |
| l. 130 | *"the fuel rods for solid rocket motors"* | the propellant of a solid rocket motor, with insulation and casing round it (slide 6) |
| ll. 473–475 | Nusselt described as *"a German aerodynamicist"* of the *"19th century, early 20th century"* | Wilhelm Nusselt (1882–1957), a German engineer known for his work in heat transfer (slide 17) |
| ll. 434–435 | inside convection *"1 over H2 times A"*, outside *"1 over H1A"* | consistent with slide 15 only if the outside is the hot side ($T_1$, $h_1$); the slide labels the fluids hot and cold, not inside and outside |
