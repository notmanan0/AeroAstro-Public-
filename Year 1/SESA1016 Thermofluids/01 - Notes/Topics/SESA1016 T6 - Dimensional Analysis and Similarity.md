---
title: "SESA1016 T6 - Dimensional Analysis and Similarity"
module: "SESA1016 Thermofluids"
type: topic
stream: "Part B: Similarity and Fluid Fundamentals"
order: 6
tags: [sesa1016, dimensional-analysis, buckingham-pi, similarity]
aliases: ["Dimensional Analysis", "Buckingham Pi"]
date: 2026-09-25
status: lectured
coverage: "Lecture of 24 Feb 2025 (ll. 1–559: units and dimensions, dimensional homogeneity, the experiment-count argument, dimensionless groups for sphere drag); Chapter 6 §§6.4–6.6 (Buckingham pi, repeating variables, log-log plots, scale models) from the lecture notes, as the following lecture was not recorded"
parent: ["[[SESA1016 Thermofluids Hub]]"]
prerequisites: ["[[SESA1016 T5 - Ideal Heat Engine Models]]"]
next_topics: ["[[SESA1016 T7 - Fluid Properties and Viscosity]]"]
key_concepts: ["[[Buckingham Pi Theorem]]", "[[Reynolds Number]]"]
tutorial_sheets: ["[[SESA1016 Problem Sheet 05 - Dimensional Analysis Solutions]]"]
sources: ["02 - Sources/Lectures/Chapter 6.pdf", "02 - Sources/Lectures/SESA1016 Lecture 2025-02-24.txt", "02 - Sources/Tutorial Sheets/Problem Sheet 05 - Dimensional Analysis.pdf"]
---

# SESA1016 T6 - Dimensional Analysis and Similarity

> [!abstract] Summary
> Every physical quantity has dimensions built from mass [M], length [L] and time [T], and every correct equation is dimensionally homogeneous. The Buckingham pi theorem says that $n$ variables involving $k$ basic dimensions can be combined into $n-k$ independent dimensionless groups, so the drag on a sphere, which depends on four variables, reduces to $C_D=f(Re)$. Matching every dimensionless group between a scale model and the full-size prototype is what lets a wind-tunnel measurement predict real forces.

> [!summary]- Exam use: quick path
> - **Use it when:** a quantity is said to depend on a list of variables and you must find the dimensionless form, or a model test must be scaled to a prototype.
> - **Assumptions:** the variable list is complete (this is the physics; the method cannot check it); three basic dimensions, M, L, T, unless temperature or others appear.
> - **Method:** 1. List the $n$ variables and their dimensions. 2. Count $k$ and form $n-k$ groups. 3. Pick $k$ repeating variables (not the dependent one, together containing all dimensions, unable to form a group on their own). 4. Make each remaining variable dimensionless with them, solving for the exponents. 5. For a model, match all independent groups, then equate the dependent group to scale the measurement.
> - **Common mistakes:** choosing the dependent variable as a repeating variable; forgetting that an angle or a ratio of lengths is already a dimensionless group.
> - **Practise:** [[#Worked example - scale-model aerofoil]] · [[SESA1016 Problem Sheet 05 - Dimensional Analysis Solutions]] Q5.1–Q5.3

The drag on a sphere held in a wind tunnel plausibly depends on the sphere's diameter, the air speed, and the air's density and viscosity. Measuring the effect of each one properly needs about ten values of it while the others are held fixed, and every combination of the others has to be repeated: ten velocities for each of ten diameters is 100 runs, and adding ten densities and ten viscosities makes 10 000 (24 Feb, ll. 401–475). Changing the density and viscosity of the air in a wind tunnel is impractical anyway, and a smooth curve usually needs more like 100 points than 10.

Dimensional analysis cuts this down, because the laws of physics cannot depend on the units chosen to measure in. The drag must therefore be expressible as a relationship between dimensionless combinations of the variables, and there are far fewer of those than there are variables. For the sphere there are only two, $D/(\rho V^2d^2)$ and $\rho Vd/\mu$, so one curve of one against the other, measured by varying only the speed, holds all 10 000 experiments' worth of information (24 Feb, ll. 491–553).

The same idea makes scale-model testing work. A small model in a wind tunnel and the full-size aircraft obey the same dimensionless relationship, so if the independent dimensionless groups are made equal, the dependent one is equal too, and a force measured on the model converts directly to the force on the prototype.

---

## 1. Units, dimensions and homogeneity

### Units are invented, dimensions are not

Every symbol in an equation has units. In $pV=mRT$, pressure is in Pa, volume in m³, mass in kg, $R$ in J kg⁻¹ K⁻¹ and temperature in K. Writing them out, kg cancels against kg⁻¹ and K against K⁻¹, leaving Pa m³ = J. Since a pascal is N m⁻² and a joule is N m, both sides are N m and everything cancels (24 Feb, ll. 47–83). The same works in pounds, feet and seconds, as long as systems are not mixed.

Units are a human convention: the metre could have been defined as any length. What does not depend on the convention is the **dimension** of a quantity. A length is a length whether it is measured in metres, inches or light years, and its dimension is written [L]. Dimensions go in square brackets and use capitals, so they cannot be confused with variables or units. Most fluid mechanics needs only three basic dimensions:

$$
\text{length }[L],\qquad\text{time }[T],\qquad\text{mass }[M]
$$

Temperature [Θ] and electric current [I] are further basic dimensions, but they rarely enter the fluid problems in this module. The symbol $\doteq$ means "has the dimensions of", to distinguish it from equality.

To find the dimensions of a less familiar quantity, use an equation known to be correct (24 Feb, ll. 167–192). From $F=ma$:

$$
F\doteq[M][L][T]^{-2}
$$

Pressure is force per unit area:

$$
p\doteq\frac{[M][L][T]^{-2}}{[L]^2}=[M][L]^{-1}[T]^{-2}
$$

| Quantity | Symbol | Dimensions |
|---|---|---|
| velocity | $V$ | $[L][T]^{-1}$ |
| acceleration, $g$ | $a$, $g$ | $[L][T]^{-2}$ |
| force, drag, lift | $F$, $D$, $L$ | $[M][L][T]^{-2}$ |
| pressure, stress | $p$, $\tau$ | $[M][L]^{-1}[T]^{-2}$ |
| density | $\rho$ | $[M][L]^{-3}$ |
| dynamic viscosity | $\mu$ | $[M][L]^{-1}[T]^{-1}$ |
| frequency, angular velocity | $f$, $\omega$ | $[T]^{-1}$ |
| moment, energy | $T$, $E$ | $[M][L]^2[T]^{-2}$ |

The viscosity entry comes from [[SESA1016 T7 - Fluid Properties and Viscosity|T7]]: shear stress $\tau=\mu\,du/dy$, so $\mu\doteq[M][L]^{-1}[T]^{-2}/[T]^{-1}=[M][L]^{-1}[T]^{-1}$.

In the fluids half of the module $V$ means velocity; volume is written with a different V (lecture-notes notation) to avoid the clash, since $U$ is already internal energy (24 Feb, ll. 119–138).

### Dimensional homogeneity

An equation can only be physically correct if both sides have the same dimensions, and every term that is added or subtracted has the same dimensions too. This is **dimensional homogeneity**. $F=ma$ passes: $[M][L][T]^{-2}=[M][L][T]^{-2}$. So does $F_1+F_2=ma$. But $F=ma+V$ cannot be right, because it would add $[L][T]^{-1}$ to $[M][L][T]^{-2}$.

Homogeneity can prove an equation wrong but never prove it right. For the total width $w$ of an aircraft with wing length $\ell$ and fuselage diameter $d$, $w=\ell\times d$ is impossible ([L] = [L]²), but both $w=d+2\ell$ and $w=d+\ell$ are homogeneous, and only one of them is correct. A pure number such as 2 has no dimensions, so homogeneity is blind to it.

It is still the quickest check on a long derivation. Suppose two methods give two candidate results for a pressure (24 Feb, ll. 229–341):

$$
p=2p_0\frac{\rho g}{\rho V^2}\qquad\text{or}\qquad p=2p_0\frac{\rho gh}{\rho V^2}
$$

In the first, $\rho$ cancels and

$$
\frac{g}{V^2}\doteq\frac{[L][T]^{-2}}{[L]^2[T]^{-2}}=[L]^{-1}
$$

so the right-hand side has dimensions of pressure per length, and the equation is certainly wrong. In the second, $gh\doteq[L]^2[T]^{-2}$, the same as $V^2$, so the fraction is dimensionless, the right-hand side is a pressure and the equation is homogeneous. That makes it the better candidate, though not proven: a factor of 1000 instead of 2, or the fraction turned upside down, would pass the test equally well.

## 2. Dimensionless groups

### The sphere-drag example

The drag on a sphere is assumed to depend on diameter, velocity, density and viscosity:

$$
D=f(d,V,\rho,\mu)
$$

with dimensions

$$
D\doteq[M][L][T]^{-2},\quad d\doteq[L],\quad V\doteq[L][T]^{-1},\quad \rho\doteq[M][L]^{-3},\quad \mu\doteq[M][L]^{-1}[T]^{-1}
$$

Two combinations of these have no dimensions at all. For the first,

$$
\frac{D}{\rho V^2d^2}\doteq\frac{[M][L][T]^{-2}}{[M][L]^{-3}\,[L]^2[T]^{-2}\,[L]^2}=\frac{[M][L][T]^{-2}}{[M][L][T]^{-2}}=1
$$

and for the second,

$$
\frac{\rho Vd}{\mu}\doteq\frac{[M][L]^{-3}\,[L][T]^{-1}\,[L]}{[M][L]^{-1}[T]^{-1}}=\frac{[M][L]^{-1}[T]^{-1}}{[M][L]^{-1}[T]^{-1}}=1
$$

The problem can then be restated as one dimensionless group depending on the other:

$$
\frac{D}{\rho V^2d^2}=f'\!\left(\frac{\rho Vd}{\mu}\right)
$$

where $f'$ is a different, still unknown, function. Experiments are still needed to find $f'$, but only one series: vary $\rho Vd/\mu$ (by changing just the speed), measure $D/(\rho V^2d^2)$ and plot one against the other. Rearranged, the drag for any combination of the four variables is

$$
D=\rho V^2d^2\,f'\!\left(\frac{\rho Vd}{\mu}\right)
$$

(24 Feb, ll. 525–550). Ten to a hundred experiments replace ten thousand.

The method only works if the list of variables is right. Choosing which variables matter is the hard step, and it needs physical understanding: dimensional analysis cannot tell you that you have forgotten one.

## 3. The Buckingham pi theorem

### Number of groups

The **Buckingham pi theorem** (Edgar Buckingham, 1914) fixes how many independent groups describe the sphere completely. In slightly simplified form:

> $n$ variables can be combined to form $n-k$ independent dimensionless groups, where $k$ is the number of basic dimensions.

For the sphere, $n=5$ ($D$, $d$, $V$, $\rho$, $\mu$) and $k=3$ (M, L, T), so there are $5-3=2$ groups. Usually $k=3$, but check: a problem with no mass anywhere in it has $k=2$. The groups are traditionally written $\Pi_1$, $\Pi_2$, …, hence pi groups.

### Method of repeating variables

The standard way to build the groups has two steps.

First, choose $k$ **repeating variables**. Together they must contain all $k$ dimensions, and it must be impossible to form a dimensionless group from them alone. The dependent variable (here the drag) should not be one of them. Variables with as few dimensions as possible make the algebra easy: a length such as $d$, a velocity for time and a density for mass. For the sphere, $d$, $V$ and $\rho$ work: only $V$ contains [T] and only $\rho$ contains [M], so no combination of the three can be dimensionless.

Second, make each remaining variable dimensionless using only the repeating variables. Each group contains exactly one remaining variable. This can be done by inspection, or systematically by solving for unknown exponents.

For the drag, write

$$
\Pi_1=D\,d^aV^b\rho^c
$$

and require its dimensions to vanish:

$$
[M][L][T]^{-2}\cdot[L]^a\cdot[L]^b[T]^{-b}\cdot[M]^c[L]^{-3c}=[M]^0[L]^0[T]^0
$$

Collect the exponent of each dimension:

$$
[M]:\quad1+c=0
$$

$$
[L]:\quad1+a+b-3c=0
$$

$$
[T]:\quad-2-b=0
$$

The mass and time equations give $c=-1$ and $b=-2$ directly. Then the length equation gives

$$
a=3c-1-b=-3-1+2=-2
$$

so

$$
\Pi_1=Dd^{-2}V^{-2}\rho^{-1}=\frac{D}{\rho V^2d^2}
$$

For the viscosity, $\Pi_2=\mu\,d^aV^b\rho^c$:

$$
[M][L]^{-1}[T]^{-1}\cdot[L]^a\cdot[L]^b[T]^{-b}\cdot[M]^c[L]^{-3c}=[M]^0[L]^0[T]^0
$$

$$
[M]:\quad1+c=0
$$

$$
[L]:\quad-1+a+b-3c=0
$$

$$
[T]:\quad-1-b=0
$$

so $c=-1$, $b=-1$ and $a=1-b+3c=1+1-3=-1$:

$$
\Pi_2=\frac{\mu}{\rho Vd}
$$

Always check the result by substituting the dimensions back in; mistakes are easy.

### The groups are not unique

The theorem fixes how many independent groups there are, not which. Any group can be inverted, raised to a power or multiplied by a number, and the result is still a valid independent group. Inverting $\Pi_2$ gives the more familiar **Reynolds number**

$$
Re=\frac{\rho Vd}{\mu}
$$

and multiplying $\Pi_1$ by $8/\pi$ gives

$$
\frac{D}{\tfrac12\rho V^2\,\tfrac{\pi}{4}d^2}=\frac{D}{\tfrac12\rho V^2A}=C_D
$$

the **drag coefficient**, with $A=\pi d^2/4$ the projected (frontal) area of the sphere. So the sphere result is

$$
\boxed{C_D=f(Re)}
$$

which is the form in which experimental data are tabulated. A different set of repeating variables gives different but equally valid groups: with $d$, $V$ and $\mu$, the method gives $D/(\mu Vd)=f'(\rho Vd/\mu)$.

### Common dimensionless groups

| Group | Symbol | Definition | Compares |
|---|---|---|---|
| Reynolds number | $Re$ | $\rho Vd/\mu$ | inertia to viscous forces |
| Froude number | $Fr$ | $V/\sqrt{gd}$ | inertia to gravity |
| Mach number | $Ma$ | $V/c$ | flow speed to speed of sound |
| Weber number | $We$ | $\rho V^2d/\sigma$ | inertia to surface tension |
| Strouhal number | $St$ | $fd/V$ | oscillation frequency to flow time scale |
| Drag coefficient | $C_D$ | $D/(\tfrac12\rho V^2A)$ | drag to dynamic pressure force |
| Lift coefficient | $C_L$ | $L/(\tfrac12\rho V^2A)$ | lift to dynamic pressure force |

Choosing repeating variables and rearranging so that the standard groups appear is worth the effort, because published data use them.

## 4. Physical insight from dimensionless plots

### Creeping flow and the Stokes limit

At very low Reynolds number, inertia should not matter, so the fluid density drops out of the problem:

$$
D=f(d,V,\mu)
$$

Now $n=4$ and $k=3$, so there is only one group,

$$
\Pi=\frac{D}{\mu Vd}
$$

A single dimensionless group cannot depend on anything, so it must be a constant:

$$
\frac{D}{\mu Vd}=\text{const},\qquad D\propto\mu Vd
$$

Divide both sides by $\rho V^2d^2$:

$$
\frac{D}{\rho V^2d^2}\propto\frac{\mu}{\rho Vd}
$$

$$
C_D=\frac{C}{Re}
$$

Dimensional analysis gives the form but not the constant. The analytical solution for slow flow past a sphere, Stokes' drag $D=3\pi\mu dV$, fixes it:

$$
C_D=\frac{3\pi\mu dV}{\tfrac12\rho V^2\,\tfrac{\pi}{4}d^2}=\frac{24\mu}{\rho Vd}=\frac{24}{Re}
$$

![[tf_dimensional_similarity.png|900]]

### Reading log-log plots

On logarithmic axes the Stokes line $C_D=24/Re$ is straight. Taking base-10 logarithms,

$$
\log_{10}C_D=\log_{10}24-\log_{10}Re
$$

a straight line of slope $-1$; the constant only shifts it vertically. More generally, dimensionless data often follow a power law in some limit, $\Pi_1\propto\Pi_2^{\,a}$, which on log-log axes is

$$
\log_{10}\Pi_1=a\log_{10}\Pi_2+\text{const}
$$

so the slope of the line is the exponent. Log axes also cover several decades of $Re$ at once; the same sphere data on linear axes collapse into a spike near the origin and a flat line, and almost nothing can be read from them.

## 5. Scale models and similarity

A scale model predicts the prototype only if the dimensionless groups match. If

$$
\Pi_1=f(\Pi_2,\Pi_3)
$$

then $\Pi_{1,p}=\Pi_{1,m}$ provided $\Pi_{2,p}=\Pi_{2,m}$ and $\Pi_{3,p}=\Pi_{3,m}$, with $p$ for prototype and $m$ for model. Geometric similarity (all length ratios equal) matches the shape groups such as $s/c$ automatically; matching the others, usually the Reynolds number, is a condition on the test speed or fluid. Once they match, the measured dependent group (such as $C_L$) is transferred unchanged and rearranged for the prototype force.

Matching every group is not always possible. A 1:10 model in air at the same density would need ten times the speed to match $Re$, which may push it to a different Mach number; testing in water instead (Problem Sheet 5, Q5.5) uses water's much lower kinematic viscosity to keep the speed reasonable.

---

## Worked examples

### Worked example - drag on a sphere from the drag curve

A 2 cm sphere is held in a wind tunnel at 40 m/s in air with $\rho=1.2$ kg/m³ and $\mu=1.8\times10^{-5}$ Pa s. Find the drag (Chapter 6, Example 6.2).

$$
Re=\frac{\rho Vd}{\mu}=\frac{1.2\times40\times0.02}{1.8\times10^{-5}}=5.3\times10^4
$$

At this Reynolds number the sphere drag curve is in its flat region, $C_D\approx0.45$. Rearranging the definition of $C_D$:

$$
D=\tfrac12\rho V^2\,\tfrac{\pi}{4}d^2\,C_D=\tfrac12\times1.2\times40^2\times\tfrac{\pi}{4}\times0.02^2\times0.45=0.14\ \mathrm N
$$

> [!check] Reading the curve
> The empirical sphere-drag correlation used for the figure gives $C_D=0.41$ at $Re=5.3\times10^4$, so the chart reading of 0.45 is within the scatter of the data and the drag is 0.13–0.14 N.

### Worked example - scale-model aerofoil

The lift on an aerofoil of chord $c=1$ m and span $s=5$ m is wanted at 10 m/s in air of density 0.5 kg/m³. A 1:10 model is tested in a tunnel with air at 1.2 kg/m³; viscosity is the same in both. At what speed should the model run, and if it gives 30 N of lift, what is the full-size lift? (Chapter 6, Example 6.3.)

The lift depends on $V$, $c$, $s$, $\rho$ and $\mu$: six variables, three dimensions, three groups. A convenient set is

$$
C_L=\frac{L}{\tfrac12\rho V^2cs},\qquad Re=\frac{\rho Vc}{\mu},\qquad \frac{s}{c}
$$

so $C_L=f'(Re,s/c)$. The aspect ratio $s/c=5$ matches automatically because the model is geometrically similar ($c_m=0.1$ m, $s_m=0.5$ m). Matching the Reynolds number with the same $\mu$:

$$
\rho_mV_mc_m=\rho_pV_pc_p
$$

$$
V_m=V_p\frac{\rho_pc_p}{\rho_mc_m}=10\times\frac{0.5\times1}{1.2\times0.1}=41.7\ \mathrm{m/s}
$$

With both independent groups matched, $C_{L,p}=C_{L,m}$:

$$
L_p=L_m\frac{\rho_pV_p^2c_ps_p}{\rho_mV_m^2c_ms_m}=30\times\frac{0.5\times10^2\times1\times5}{1.2\times41.7^2\times0.1\times0.5}=72\ \mathrm N
$$

Any other valid set of groups, such as $L/(\rho V^2s^2)=f'(\rho Vs/\mu,c/s)$, gives the same 72 N.

### Worked example - oscillating plate

A thin plate of height $H$ and length $L$, fixed at one end in a stream of speed $V$, density $\rho$ and viscosity $\mu$, oscillates at frequency $f$. Express $f$ in dimensionless form (Chapter 6, Example 6.1).

$$
f=g(H,L,V,\rho,\mu)
$$

There are $n=6$ variables and $k=3$ dimensions, so three groups. With repeating variables $H$, $V$, $\rho$, the remaining variables $f$, $L$, $\mu$ give

$$
\Pi_1=\frac{fH}{V},\qquad\Pi_2=\frac{L}{H},\qquad\Pi_3=\frac{\mu}{\rho VH}
$$

Recognising the Strouhal number and inverting $\Pi_3$ to the Reynolds number:

$$
St=\frac{fH}{V}=g'\!\left(\frac{L}{H},Re\right)
$$

### Worked example - wind moment on a tall building

The aerodynamic moment $T$ about the base of a tall building depends on the velocity gradient $G=dV/dz$ of the approaching wind, the building height $H$ and the air density $\rho$ (viscosity unimportant at high Reynolds number). A 1 m model at $G_m=1$ s⁻¹ and $\rho=1.25$ kg/m³ gives $T_m=0.03$ N m. Find the moment on a 100 m building with $G_p=0.30$ s⁻¹ (Problem Sheet 5, Q5.1, the tutorial problem).

Four variables, $T\doteq[M][L]^2[T]^{-2}$, $G\doteq[T]^{-1}$, $H\doteq[L]$, $\rho\doteq[M][L]^{-3}$, and three dimensions, so one group. Write $\Pi=T\,G^aH^b\rho^c$:

$$
[M]:\ 1+c=0,\qquad [T]:\ -2-a=0,\qquad [L]:\ 2+b-3c=0
$$

so $c=-1$, $a=-2$, $b=-5$ and

$$
\Pi=\frac{T}{\rho G^2H^5}=\text{const}
$$

The single group must be the same for model and prototype:

$$
T_p=T_m\frac{\rho_p}{\rho_m}\left(\frac{G_p}{G_m}\right)^2\left(\frac{H_p}{H_m}\right)^5=0.03\times1\times0.3^2\times100^5=2.7\times10^7\ \mathrm{N\,m}
$$

For the pressure rise $p(z)-p_\infty$ at height $z$ there is one more variable, $z$, and so two groups: $(p-p_\infty)/(\rho G^2H^2)=F(z/H)$. At corresponding heights $z/H=1/2$, a model reading of 0.1 Pa scales to $0.1\times0.3^2\times100^2=90$ Pa.

---

## Links

- Parent: [[SESA1016 Thermofluids Hub]] · Previous: [[SESA1016 T5 - Ideal Heat Engine Models]] · Next: [[SESA1016 T7 - Fluid Properties and Viscosity]]
- Concepts: [[Buckingham Pi Theorem]] · [[Reynolds Number]] · [[Skin-friction and Pressure Drag]]
- Worked sheet: [[SESA1016 Problem Sheet 05 - Dimensional Analysis Solutions]] · Formula list: [[SESA1016 Formula Sheet]]
- Used again in: [[SESA1016 T14 - Boundary Layers and the Origin of Drag|T14]] (drag coefficients) · [[SESA1016 T15 - Flow in Conduits|T15]] (friction factor against $Re$) · [[SESA2023 W09 - Turbomachinery Characteristics - Coefficients, Similarity and Maps]] (non-dimensional turbomachine maps)

## Sources

- `Chapter 6.pdf`: lecture notes Chapter 6, Dimensional analysis, §§6.1–6.6, Examples 6.1–6.3, Tables 6.1–6.2, Figs 6.1–6.4.
- `SESA1016 Lecture 2025-02-24.txt` (24 Feb 2025): purpose of dimensional analysis (ll. 1–44), units and dimensions (ll. 45–204), dimensional homogeneity and the two-pressure check (ll. 205–346), the 10 000-experiment argument (ll. 347–490), sphere-drag groups (ll. 491–557). The Buckingham pi lecture that followed was not recorded.
- `Problem Sheet 05 - Dimensional Analysis.pdf`: Q5.1–Q5.5, printed answers and the worked solution to Q5.2.

## Self-study tasks

### Core

- [ ] Check the two candidate pressure equations for homogeneity and say which could be right (24 Feb, ll. 229–341). → [[#Dimensional homogeneity]]
- [ ] Q5.1, wind moment on a tall building (Problem Sheet 5, the tutorial problem). Targets $2.7\times10^7$ N m and 90 Pa. → [[#Worked example - wind moment on a tall building]]
- [ ] Q5.2, propeller thrust coefficient and advance ratio (worked solution). Targets 44.3 kN and 32 kN. → [[SESA1016 Problem Sheet 05 - Dimensional Analysis Solutions]]
- [ ] Q5.3, vortex shedding from a jetty pile at 1:12 scale. Target 2.76 Hz. → [[#Common dimensionless groups]] · [[SESA1016 Problem Sheet 05 - Dimensional Analysis Solutions]]
- [ ] Q5.4, lift on a spinning golf ball. Target $C_L=f(Re,\omega d/V)$. → [[#Number of groups]] · [[SESA1016 Problem Sheet 05 - Dimensional Analysis Solutions]]
- [ ] Q5.5, aerofoil drag and a 1:5 water-tunnel model. Target $V_p/V_m=3.0$. → [[#5. Scale models and similarity]] · [[SESA1016 Problem Sheet 05 - Dimensional Analysis Solutions]]

### Further practice

- [ ] Derive both sphere-drag groups by solving for the exponents, then repeat with $d$, $V$, $\mu$ as repeating variables (Chapter 6, §6.4.1). → [[#Method of repeating variables]]
- [ ] Show that a single dimensionless group must be constant, and use it with Stokes' drag to get $C_D=24/Re$ (Chapter 6, §6.5). → [[#Creeping flow and the Stokes limit]]
- [ ] Rework Examples 6.1–6.3 closed-book. → [[#Worked example - oscillating plate]] · [[#Worked example - scale-model aerofoil]]

## Transcript and slide slips

> [!warning] Transcript slip (24 Feb, l. 234)
> Where: [[#Dimensional homogeneity]].
>
> The first candidate is read out as "2 times $p_0$ plus $\rho g$ divided by $\rho v^2$". The dimension check that follows (ll. 279–305) treats $\rho g/(\rho V^2)$ as multiplying $2p_0$, which leaves a stray $[L]^{-1}$; with a plus sign the equation would add a pressure to a quantity of dimension $[L]^{-1}$ and would fail for a different reason. The second candidate is likewise a product, $2p_0\,\rho gh/(\rho V^2)$, for which the check at ll. 306–322 works. Both are written here as products.

> [!warning] Problem-sheet slip (Problem Sheet 5, worked solution Q5.2c, eq. 9)
> Where: [[SESA1016 Problem Sheet 05 - Dimensional Analysis Solutions]].
>
> The worked solution evaluates $0.1\times1.25\times100^2\times2.25^4$ and prints 44.3 kN, repeating the answer to part (b). The product is 32.0 kN, which is the value on the answers page.
