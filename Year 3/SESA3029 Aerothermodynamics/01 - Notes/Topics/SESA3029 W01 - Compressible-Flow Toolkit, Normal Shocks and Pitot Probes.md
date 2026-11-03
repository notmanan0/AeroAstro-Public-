---
title: "SESA3029 W01 - Compressible-Flow Toolkit, Normal Shocks and Pitot Probes"
module: "SESA3029 Aerothermodynamics"
type: topic
stream: "Block 1: Basic Toolkit"
order: 1
tags: [sesa3029, compressible-flow, normal-shock, pitot-probe]
aliases: ["SESA3029 Week 1", "Aerothermodynamics Toolkit"]
date: 2026-09-25
status: lectured
coverage: "Week 1"
parent: ["[[SESA3029 Aerothermodynamics Hub]]"]
prerequisites: ["[[Speed of Sound and Mach Number]]", "[[Stagnation Properties]]", "[[Normal Shock Waves]]"]
next_topics: ["[[SESA3029 W02 - Oblique Shock Relations and Mach Waves]]"]
key_concepts: ["[[Normal-Shock Jump Relations]]", "[[Shock-Table Interpolation]]", "[[Compressible Pitot Probe]]", "[[Rayleigh Pitot Formula]]"]
tutorial_sheets: []
sources: ["02 - Sources/Lectures/Lecture1-1.pdf", "02 - Sources/Lectures/Lecture 1-1.txt", "02 - Sources/Lectures/Lecture1-2.pdf", "02 - Sources/Lectures/Lecture 1-2.txt", "02 - Sources/Lectures/Lecture1-3.pdf", "02 - Sources/Lectures/Lecture 1-3.txt"]
---

# SESA3029 W01 - Compressible-Flow Toolkit, Normal Shocks and Pitot Probes

> [!abstract] Summary
> Week 1 sets up the toolkit for the rest of the module: Mach number, the isentropic relations between static and stagnation properties, and the normal shock, which conserves mass, momentum and energy but loses stagnation pressure. A Pitot probe then needs one of three models depending on the flow: Bernoulli, an isentropic stagnation relation, or a normal shock followed by isentropic deceleration.

> [!summary]- Exam use: quick path
> - **Use it when:** you are given $p$, $T$, $\rho$, $M$ or stagnation values in a duct or stream, a normal shock, or a Pitot reading.
> - **Assumptions:** perfect gas, steady, adiabatic; $\gamma=1.4$ for the IFT and NST. Isentropic only away from shocks: across a normal shock $T_0$ is constant but $p_0$ falls.
> - **Method:** 1. Find $M$ (for a Pitot probe, first compare $p_{02}/p_1$ with 1.893 to decide the regime). 2. Isentropic ratios $T_0/T$, $p_0/p$, $\rho_0/\rho$ from $M$. 3. Across a shock, the NST with $M_1$ gives $M_2$, $p_2/p_1$, $p_{02}/p_{01}$. 4. Pitot: Bernoulli ($M\lesssim0.3$), isentropic $p_0/p$ (subsonic) or the Rayleigh Pitot formula (supersonic). 5. Check $M_2<1$, $T_{02}=T_{01}$, $p_{02}<p_{01}$.
> - **Common mistakes:** using isentropic $p_0/p$ straight across a shock; using the subsonic Pitot formula when $p_{02}/p_1>1.893$.
> - **Practise:** [[#Worked Pitot examples]] · [[SESA3029 Test 1 - Solutions#Q5. Supersonic Pitot probe with the static tapping moved behind the shock|Test 1 Q5]]

Follow one small parcel of air through the week's ideas. Its Mach number says whether it can send a pressure signal ahead of itself: below $M=1$ sound outruns the flow and the air upstream can adjust, above it the signal can't get out ahead, so a compression may pile up into a shock.

Stagnation properties describe what the parcel would become if it were brought to rest. In adiabatic deceleration its kinetic energy turns into enthalpy, so $T_0$ follows from energy conservation alone. Getting $p_0$ as well needs the deceleration to be reversible too.

A shock is a very thin layer across which mass, momentum and total enthalpy are all still conserved. What it gives up is reversibility, so entropy rises and stagnation pressure falls. A Pitot probe does the bring-it-to-rest experiment for real, and choosing the right formula is a matter of describing the route the gas takes into the probe: smooth isentropic deceleration if the flow is subsonic, or a shock first and smooth deceleration after it if it is supersonic.

## 1. Mach number and flow regimes

The Mach number compares the flow speed with the local speed at which pressure disturbances propagate:

$$
M=\frac{U}{a},\qquad a=\sqrt{\gamma RT}.
$$

For standard air, $R=287\ \mathrm{J\,kg^{-1}K^{-1}}$ and $\gamma\approx1.4$. At $T=288\ \mathrm K$, $a\approx340.2\ \mathrm{m\,s^{-1}}$.

| Regime | Course convention | Main implication |
|---|---:|---|
| Effectively incompressible | $M<0.3$ | Density changes are usually negligible |
| Subsonic | $M<1$ | Disturbances can propagate upstream |
| Transonic | $0.8<M<1.2$ | Subsonic and supersonic regions may coexist |
| Supersonic | $M>1$ | Shocks and expansion waves become possible |
| Hypersonic | approximately $M>5$ | High-temperature and strong-interaction effects become important |

Mach number uses the local velocity and temperature, so a vehicle flying at a fixed flight Mach number sees a range of local Mach numbers across its flow field.

## 2. Aerodynamic review and the low-speed baseline

For a thin aerofoil at angle of attack $\alpha$, resolve the surface-force resultant into normal and tangential components:

$$
L=F_n\cos\alpha-F_t\sin\alpha,
\qquad
D=F_t\cos\alpha+F_n\sin\alpha.
$$

With $q_\infty=\tfrac12\rho_\infty U_\infty^2$,

$$
C_L=\frac{L}{q_\infty S},\qquad
C_D=\frac{D}{q_\infty S},\qquad
C_M=\frac{M}{q_\infty S\bar c}.
$$

For a two-dimensional section, replace $L,D,M$ by the per-unit-span values $L',D',M'$ and use $c$ or $c^2$ as appropriate.

Moving a pitching moment from the leading edge to a point $x$ gives, in the lecture's form:

$$
M_x'=M_{LE}'+xL',\qquad
C_{m,x}=C_{m,LE}+\frac{x}{c}C_l\quad(\text{lecture; approximate}).
$$

The exact version is worth having. Put the new reference point a distance $x$ aft of the LE along the chord, and split the resultant into $F_n'$ (normal to the chord) and $F_t'$ (along it). Moving the reference point along the chord is a shift parallel to $F_t'$, so the moment of $F_t'$ doesn't change. $F_n'$ is perpendicular to the shift, so its moment changes by $x F_n'$ (nose-up positive, $x$ aft, $F_n'$ up):

$$
M_x'=M_{LE}'+xF_n'.
$$

Divide by $q_\infty c^2$, with $C_n=F_n'/(q_\infty c)$:

$$
C_{m,x}=C_{m,LE}+\frac{x}{c}C_n.
$$

Set $C_{m,x}=0$ for the centre of pressure, and $\mathrm dC_{m,x}/\mathrm d\alpha=0$ for the aerodynamic centre:

$$
\frac{x_{CP}}{c}=-\frac{C_{m,LE}}{C_n},
\qquad
\frac{x_{AC}}{c}=-\frac{\mathrm dC_{m,LE}}{\mathrm dC_n}.
$$

> [!warning] When the lecture's $C_l$ form is good enough
> $C_n=C_l\cos\alpha+C_d\sin\alpha$, so $C_n\approx C_l$ only when $\alpha$ is small and $C_d\sin\alpha\ll C_l$. That is the subsonic thin-aerofoil setting (SESA2022), where the forms are interchangeable. In supersonic flow at $10^\circ$ the difference shows: for the W03 flat plate, the chord-based centre of pressure is exactly $0.5c$ while the lift-based formula gives $0.508c$, and $-\mathrm dC_{m,LE}/\mathrm dC_l$ gives $0.523c$ ([[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method#6. The shock-expansion method|W03 §6]]). Quote the lecture's form when an exam asks for it, but say it assumes small $\alpha$.

The lift-based versions, $x_{CP}/c\approx-C_{m,LE}/C_l$ and $x_{AC}/c\approx-\mathrm dC_{m,LE}/\mathrm dC_l$, are the lecture's (and the official sheet's) approximations.

> [!question] Lecture puzzle: is an inviscid flat plate's force normal to the plate?
> You'd expect yes: with no friction only pressure acts, and pressure acts normal to the surface. The lecture's answer is no. Thin-aerofoil theory gives $C_l=2\pi\alpha$ for lift, perpendicular to the freestream, with zero drag (d'Alembert), so the resultant is $L$, not $F_n$.
>
> The sharp leading edge accounts for the difference. Flow turning round a zero-thickness edge needs infinite velocity, so the pressure goes to $-\infty$ on a point of zero area, and the product is a finite leading-edge suction force pointing upstream along the plate. That negative tangential force $F_t$ cancels the rearward component $F_n\sin\alpha$: $D=F_t\cos\alpha+F_n\sin\alpha=0$ requires $F_t=-F_n\tan\alpha$.
>
> The lecture asks you to *"revisit and consolidate"* this from [[SESA2022 T4 - Thin Aerofoil Theory]] (Lecture 1-1, lines 256–300). It matters here because a supersonic flat plate has no leading-edge suction. Its force really is normal to the plate, and the rearward component is wave drag.

The low-speed thin-aerofoil results $\mathrm dC_l/\mathrm d\alpha=2\pi$ and $x_{AC}/c=1/4$ provide a reference point. Later high-speed theory shows why these results change in supersonic flow.

## 3. Perfect-gas thermodynamics

For a thermally perfect gas,

$$
p=\rho RT.
$$

For a calorically perfect gas with constant $c_p,c_v$,

$$
e=c_vT,\qquad h=e+pv=c_pT,\qquad R=c_p-c_v,\qquad \gamma=\frac{c_p}{c_v}.
$$

The Gibbs relation can be written as

$$
T\,\mathrm ds=\mathrm de+p\,\mathrm dv=\mathrm dh-v\,\mathrm dp.
$$

Integrating between two equilibrium states of a calorically perfect gas gives

$$
s_2-s_1=c_p\ln\frac{T_2}{T_1}-R\ln\frac{p_2}{p_1}.
$$

### Isentropic relations: derivation

Set $s_2=s_1$:

$$
c_p\ln\frac{T_2}{T_1}=R\ln\frac{p_2}{p_1}.
$$

Since $R/c_p=(\gamma-1)/\gamma$,

$$
\ln\frac{T_2}{T_1}=\frac{\gamma-1}{\gamma}\ln\frac{p_2}{p_1}
$$

and therefore

$$
\boxed{\frac{p_2}{p_1}=\left(\frac{T_2}{T_1}\right)^{\gamma/(\gamma-1)}}.
$$

Using $p=\rho RT$ gives the density form. Write the equation of state at both states and divide:

$$
\frac{\rho_2}{\rho_1}=\frac{p_2}{p_1}\,\frac{T_1}{T_2}
=\left(\frac{T_2}{T_1}\right)^{\gamma/(\gamma-1)}\left(\frac{T_2}{T_1}\right)^{-1}
=\left(\frac{T_2}{T_1}\right)^{\frac{\gamma}{\gamma-1}-1}.
$$

Since $\dfrac{\gamma}{\gamma-1}-1=\dfrac{1}{\gamma-1}$,

$$
\boxed{\frac{\rho_2}{\rho_1}=\left(\frac{T_2}{T_1}\right)^{1/(\gamma-1)}}
\quad\Longrightarrow\quad
\left(\frac{\rho_2}{\rho_1}\right)^{\gamma}=\left(\frac{T_2}{T_1}\right)^{\gamma/(\gamma-1)}=\frac{p_2}{p_1}.
$$

This is the step the lecture left "to you to have a practice on" (Lecture 1-2, lines 30–33). Together these give the equivalent set

$$
\boxed{
\frac{p_2}{p_1}
=\left(\frac{\rho_2}{\rho_1}\right)^\gamma
=\left(\frac{T_2}{T_1}\right)^{\gamma/(\gamma-1)}
}.
$$

These relations require an isentropic path. They cannot be applied from one side of a shock to the other.

## 4. Stagnation properties

Static temperature describes the gas as it moves. Stagnation temperature adds on the kinetic energy that would turn into enthalpy if the parcel were stopped adiabatically. The stopping doesn't have to be reversible for $T_0$ to work; reversibility only matters when you go on to a stagnation pressure.

For steady, adiabatic flow with no shaft work and negligible potential-energy change,

$$
h+\frac{U^2}{2}=h_0=\text{constant}.
$$

For a calorically perfect gas,

$$
c_pT+\frac{U^2}{2}=c_pT_0.
$$

Use $U=Ma$, $a^2=\gamma RT$ and $c_p=\gamma R/(\gamma-1)$:

$$
c_p(T_0-T)=\frac{M^2\gamma RT}{2}
$$

so

$$
\boxed{\frac{T_0}{T}=1+\frac{\gamma-1}{2}M^2},
\qquad
\boxed{\frac{a_0^2}{a^2}=1+\frac{\gamma-1}{2}M^2}.
$$

If the fluid is brought to rest isentropically, then

$$
\boxed{
\frac{p_0}{p}=\left(1+\frac{\gamma-1}{2}M^2\right)^{\gamma/(\gamma-1)}
},
$$

$$
\boxed{
\frac{\rho_0}{\rho}=\left(1+\frac{\gamma-1}{2}M^2\right)^{1/(\gamma-1)}
}.
$$

![[at_stagnation_relations.png|760]]

Across an adiabatic normal shock $h_0$ and $T_0$ stay the same, but entropy rises, so $p_0$ falls and $p_{02}<p_{01}$.

### Nozzle example

For an isentropic nozzle with $T_0=1000\ \mathrm K$ and $T_e=600\ \mathrm K$,

$$
\frac{T_e}{T_0}=0.6=\left(1+\frac{\gamma-1}{2}M_e^2\right)^{-1}.
$$

For air,

$$
M_e=\sqrt{\frac{2}{0.4}\left(\frac{1}{0.6}-1\right)}=1.8257.
$$

The same result follows from the isentropic-flow table by linear interpolation.

## 5. Normal shock from conservation laws

What happens inside a shock at the molecular level is complicated, but none of it matters for the jump relations. Wrap the shock in a control volume thin enough that only what goes in and what comes out counts, and mass, momentum and energy conservation do the rest. Take a thin, steady, one-dimensional control volume around a stationary normal shock of constant area $A$.

![[at_normal_shock_control_volume.png|760]]

### Mass

$$
\dot m=\rho_1U_1A=\rho_2U_2A
\quad\Longrightarrow\quad
\rho_1U_1=\rho_2U_2.
$$

### Momentum

$$
\dot m(U_2-U_1)=(p_1-p_2)A,
$$

or, using $\dot m/A=\rho U$,

$$
U_2-U_1=\frac{p_1}{\rho_1U_1}-\frac{p_2}{\rho_2U_2}.
$$

Since $p/\rho=a^2/\gamma$,

$$
U_2-U_1=\frac{a_1^2}{\gamma U_1}-\frac{a_2^2}{\gamma U_2}.
$$

### Energy and the Prandtl relation

Adiabatic energy conservation gives

$$
a_0^2=a_1^2+\frac{\gamma-1}{2}U_1^2
=a_2^2+\frac{\gamma-1}{2}U_2^2.
$$

Thus $a_i^2=a_0^2-\tfrac{\gamma-1}{2}U_i^2$. Substitute this into momentum:

$$
U_2-U_1
=\frac{a_0^2}{\gamma}\left(\frac1{U_1}-\frac1{U_2}\right)
-\frac{\gamma-1}{2\gamma}(U_1-U_2).
$$

Factor $U_2-U_1$ and cancel the non-trivial shock solution:

$$
1=\frac{a_0^2}{\gamma U_1U_2}+\frac{\gamma-1}{2\gamma}.
$$

Therefore

$$
\boxed{U_1U_2=\frac{2a_0^2}{\gamma+1}}.
$$

So $U_1U_2$ is the same for every normal shock with a given stagnation state, weak or strong, and a faster flow into the shock means a slower flow out of it. The shock strength only decides how that fixed product is split between $U_1$ and $U_2$.

Substitution back into the conservation equations yields the [[Normal-Shock Jump Relations]]. The lecture derived the density jump in full and set the rest as homework (Lecture 1-2, lines 276–320). All four derivations are written out below.

### Density jump (shown in lecture)

Mass conservation gives $\rho_2/\rho_1=U_1/U_2$. Eliminate $U_2$ with the Prandtl relation, $U_2=2a_0^2/[(\gamma+1)U_1]$:

$$
\frac{\rho_2}{\rho_1}=\frac{U_1^2}{U_1U_2}=\frac{(\gamma+1)U_1^2}{2a_0^2}.
$$

Multiply top and bottom by $a_1^2$ so that $U_1^2/a_1^2=M_1^2$ appears:

$$
\frac{\rho_2}{\rho_1}=\frac{\gamma+1}{2}\,M_1^2\,\frac{a_1^2}{a_0^2}.
$$

Energy conservation at station 1 gives $a_0^2/a_1^2=1+\tfrac{\gamma-1}{2}M_1^2$, so $a_1^2/a_0^2=2/[2+(\gamma-1)M_1^2]$. Hence

$$
\boxed{\frac{\rho_2}{\rho_1}=\frac{U_1}{U_2}=\frac{(\gamma+1)M_1^2}{2+(\gamma-1)M_1^2}}.
$$

### Pressure jump (homework)

Rearrange momentum, $p_1+\rho_1U_1^2=p_2+\rho_2U_2^2$, and use $\rho_2U_2=\rho_1U_1$:

$$
p_2-p_1=\rho_1U_1^2-\rho_2U_2^2=\rho_1U_1(U_1-U_2)=\rho_1U_1^2\left(1-\frac{U_2}{U_1}\right).
$$

Divide by $p_1$. Because $\rho_1U_1^2/p_1=\gamma U_1^2/a_1^2=\gamma M_1^2$ and $U_2/U_1=\rho_1/\rho_2$,

$$
\frac{p_2}{p_1}=1+\gamma M_1^2\left(1-\frac{\rho_1}{\rho_2}\right).
$$

Insert the density jump:

$$
1-\frac{\rho_1}{\rho_2}
=\frac{(\gamma+1)M_1^2-2-(\gamma-1)M_1^2}{(\gamma+1)M_1^2}
=\frac{2(M_1^2-1)}{(\gamma+1)M_1^2}.
$$

The $M_1^2$ cancels:

$$
\boxed{\frac{p_2}{p_1}=1+\frac{2\gamma}{\gamma+1}(M_1^2-1)=\frac{2\gamma M_1^2-(\gamma-1)}{\gamma+1}}.
$$

The second form is the one that appears inside the Rayleigh Pitot formula.

### Temperature jump (homework)

The equation of state at both stations gives $T=p/(\rho R)$, so

$$
\boxed{\frac{T_2}{T_1}=\frac{p_2/p_1}{\rho_2/\rho_1}
=\frac{\left[2\gamma M_1^2-(\gamma-1)\right]\left[2+(\gamma-1)M_1^2\right]}{(\gamma+1)^2M_1^2}}.
$$

### Downstream Mach number (homework)

The lecture called this one *"slightly more involved"*, but using the two jumps you already have avoids most of it. Write $M_2^2=U_2^2/a_2^2$ and $a^2\propto T$:

$$
\frac{M_2^2}{M_1^2}=\left(\frac{U_2}{U_1}\right)^2\frac{T_1}{T_2}
=\left(\frac{\rho_1}{\rho_2}\right)^2\frac{\rho_2/\rho_1}{p_2/p_1}
=\frac{1}{(\rho_2/\rho_1)(p_2/p_1)}.
$$

So

$$
M_2^2=\frac{M_1^2}{\dfrac{(\gamma+1)M_1^2}{2+(\gamma-1)M_1^2}\cdot\dfrac{2\gamma M_1^2-(\gamma-1)}{\gamma+1}}.
$$

The $(\gamma+1)$ and $M_1^2$ cancel:

$$
\boxed{M_2^2=\frac{2+(\gamma-1)M_1^2}{2\gamma M_1^2-(\gamma-1)}}.
$$

> [!check] Numerical check
> At $M_1=2$, $\gamma=1.4$: $\rho_2/\rho_1=9.6/3.6=2.667$ and $p_2/p_1=4.5$. Then $M_1^2/[(\rho_2/\rho_1)(p_2/p_1)]=4/12=0.3333$, and the boxed formula gives $3.6/10.8=0.3333$. $M_2=0.5774$, matching the normal-shock table.

A quick way to catch algebra slips in the exam is to put $M_1=1$ into every jump. Each ratio, and $M_2$, should come out as 1, because a shock at $M_1=1$ is no shock at all.

For a physical shock with $M_1>1$: $M_2<1$, $p_2>p_1$, $T_2>T_1$, $\rho_2>\rho_1$, $U_2<U_1$, $s_2>s_1$ and $p_{02}<p_{01}$.

![[at_normal_shock_trends.png|760]]

### Strong-shock limits

As $M_1\to\infty$,

$$
M_2^2\to\frac{\gamma-1}{2\gamma},
\qquad
\frac{\rho_2}{\rho_1}\to\frac{\gamma+1}{\gamma-1}.
$$

For air, $M_2\to0.378$ and $\rho_2/\rho_1\to6$. Pressure and temperature ratios grow without bound in the calorically perfect-gas model, which eventually becomes physically inadequate at very high temperature.

To get the limits, divide the numerator and denominator of each jump by $M_1^2$, then let $1/M_1^2\to0$:

$$
M_2^2=\frac{2/M_1^2+(\gamma-1)}{2\gamma-(\gamma-1)/M_1^2}\;\to\;\frac{\gamma-1}{2\gamma}
\quad\Rightarrow\quad M_2\to\sqrt{\tfrac{0.4}{2.8}}=0.378,
$$

$$
\frac{\rho_2}{\rho_1}=\frac{\gamma+1}{2/M_1^2+(\gamma-1)}\;\to\;\frac{\gamma+1}{\gamma-1}=\frac{2.4}{0.4}=6.
$$

The pressure and temperature jumps keep a factor of $M_1^2$ that nothing cancels:

$$
\frac{p_2}{p_1}\sim\frac{2\gamma}{\gamma+1}M_1^2\to\infty,
\qquad
\frac{T_2}{T_1}=\frac{p_2/p_1}{\rho_2/\rho_1}\sim\frac{2\gamma(\gamma-1)}{(\gamma+1)^2}M_1^2\to\infty.
$$

> [!tip] Why density saturates while pressure does not
> A shock can only squeeze the gas so far. Once $\rho_2/\rho_1$ is near 6, extra upstream kinetic energy goes into heating the gas ($T_2\to\infty$) rather than compressing it further. Pressure $p=\rho RT$ follows temperature to infinity. At real hypersonic temperatures, dissociation absorbs energy and lets density exceed 6, which is why the lecture says the 0.378 and 6 limits are indicative only.

## 6. Using flow tables and interpolation

If a target tabulated quantity $x_t$ lies between rows $a$ and $b$, define

$$
\sigma=\frac{x_t-x_a}{x_b-x_a}.
$$

Any other tabulated quantity $y$ is interpolated with the same fraction:

$$
y_t=y_a+\sigma(y_b-y_a).
$$

> [!warning] Table orientation
> The isentropic table may list $p/p_0$ while a question gives $p_0/p$. Invert the ratio before locating the rows. Do not interpolate one column with a different fraction from another column.

### Normal-shock example

Given air, $T_1=15^\circ\mathrm C=288.15\ \mathrm K$ and $p_2/p_1=1.25$, the two bounding table rows give

$$
\sigma=\frac{1.25-1.2450}{1.2968-1.2450}=0.09653.
$$

Then

$$
M_2=0.9118+0.09653(0.8966-0.9118)=0.9103,
$$

$$
\frac{T_2}{T_1}=1.0649+0.09653(1.0776-1.0649)=1.0661,
$$

$$
T_2=307.2\ \mathrm K,
\qquad
U_2=M_2\sqrt{\gamma RT_2}=319.8\ \mathrm{m\,s^{-1}}.
$$

## 7. Pitot probe: three regimes

The static tapping measures the upstream static pressure $p_1$, and the forward-facing tube brings the flow to rest and measures a stagnation pressure. The tube can't tell you how the air got to rest, so you have to pick the route from the measured ratio: Bernoulli at very low Mach number, isentropic compression below Mach 1, or a shock followed by isentropic compression above it.

![[at_pitot_regimes.png|760]]

### Case 1: incompressible

Bernoulli between the freestream and the stagnation point gives

$$
p_1+\frac12\rho_1U_1^2=p_0,
$$

so

$$
\boxed{U_1=\sqrt{\frac{2(p_0-p_1)}{\rho_1}}}.
$$

The stagnation-point pressure coefficient is $C_{p0}=1$.

### Case 2: compressible subsonic

There is no shock, so the complete deceleration is isentropic:

$$
\frac{p_0}{p_1}=\left(1+\frac{\gamma-1}{2}M_1^2\right)^{\gamma/(\gamma-1)}.
$$

Rearrange:

$$
\boxed{
M_1^2=\frac{2}{\gamma-1}
\left[
\left(\frac{p_0}{p_1}\right)^{(\gamma-1)/\gamma}-1
\right]
},
$$

$$
\boxed{
U_1=\sqrt{\frac{2\gamma RT_1}{\gamma-1}
\left[
\left(\frac{p_0}{p_1}\right)^{(\gamma-1)/\gamma}-1
\right]}
}.
$$

The temperature measurement is needed because $a_1=\sqrt{\gamma RT_1}$.

### Low-Mach consistency check

Use $(1+x)^n=1+nx+O(x^2)$ with $x=(\gamma-1)M_1^2/2$ and $n=\gamma/(\gamma-1)$:

$$
\frac{p_0}{p_1}=1+\frac{\gamma}{2}M_1^2+O(M_1^4).
$$

Because $\gamma p_1M_1^2=\rho_1U_1^2$,

$$
p_0=p_1+\frac12\rho_1U_1^2+p_1O(M_1^4).
$$

Bernoulli is recovered as $M_1\to0$.

### Case 3: compressible supersonic

A detached normal shock stands ahead of the Pitot opening. The measured pressure is $p_{02}$, not the upstream total pressure $p_{01}$.

1. State 1 passes through the normal shock to state 2.
2. State 2 decelerates isentropically to the stagnation state $02$.

Thus

$$
\frac{p_{02}}{p_1}=\frac{p_2}{p_1}\frac{p_{02}}{p_2}.
$$

Use the normal-shock relation for the first factor and the isentropic relation for the second:

$$
\frac{p_2}{p_1}=\frac{D}{\gamma+1},
\qquad
\frac{p_{02}}{p_2}=\left(1+\frac{\gamma-1}{2}M_2^2\right)^{\gamma/(\gamma-1)},
\qquad
D\equiv2\gamma M_1^2-(\gamma-1).
$$

#### Deriving the Rayleigh Pitot formula

Substitute $M_2^2=[2+(\gamma-1)M_1^2]/D$ into the bracket:

$$
1+\frac{\gamma-1}{2}M_2^2
=\frac{2D+(\gamma-1)\left[2+(\gamma-1)M_1^2\right]}{2D}
=\frac{4\gamma M_1^2+(\gamma-1)^2M_1^2}{2D}
=\frac{(\gamma+1)^2M_1^2}{2D},
$$

because the constant terms $-2(\gamma-1)+2(\gamma-1)$ cancel and $4\gamma+(\gamma-1)^2=(\gamma+1)^2$. Split that result as

$$
\frac{(\gamma+1)^2M_1^2}{2D}=\left[\frac{(\gamma+1)M_1^2}{2}\right]\left[\frac{\gamma+1}{D}\right].
$$

Multiply by $p_2/p_1=D/(\gamma+1)=[(\gamma+1)/D]^{-1}$. The exponent on $(\gamma+1)/D$ becomes $\gamma/(\gamma-1)-1=1/(\gamma-1)$. This gives the [[Rayleigh Pitot Formula]]:

$$
\boxed{
\frac{p_{02}}{p_1}
=\left[\frac{(\gamma+1)M_1^2}{2}\right]^{\gamma/(\gamma-1)}
\left[\frac{\gamma+1}{2\gamma M_1^2-(\gamma-1)}\right]^{1/(\gamma-1)}
}.
$$

At $M_1=1$, the shock vanishes and

$$
\left.\frac{p_0}{p}\right|_{M=1}
=\left(\frac{\gamma+1}{2}\right)^{\gamma/(\gamma-1)}
=1.8929\quad(\gamma=1.4).
$$

This is the regime discriminator for air:

- measured ratio below $1.8929$: use the subsonic isentropic formula;
- measured ratio above $1.8929$: use the Rayleigh Pitot relation or the normal-shock table.

### Worked Pitot examples

At $T_1=2^\circ\mathrm C$ and $p_1=80\ \mathrm{kPa}$:

1. If the probe reads $150\ \mathrm{kPa}$, then $p_0/p_1=1.875<1.8929$. The flow is subsonic and the isentropic result is

   $$U_1=329.7\ \mathrm{m\,s^{-1}}.$$

2. If the probe reads $400\ \mathrm{kPa}$, then $p_{02}/p_1=5>1.8929$. The normal-shock table or Rayleigh relation gives

   $$M_1=1.8705,\qquad U_1=M_1\sqrt{\gamma RT_1}=621.8\ \mathrm{m\,s^{-1}}.$$

The lecture uses $T_1=275\ \mathrm K$, so $a_1=\sqrt{1.4\times287\times275}=332.4\ \mathrm{m\,s^{-1}}$. Using $275.15\ \mathrm K$ adds about $0.1\ \mathrm{m\,s^{-1}}$ to each answer.

#### Example 1 in full — subsonic, by formula and by table

*Formula route* (the lecture asked you to *"double check these numbers… during the weekend"*):

$$
M_1^2=\frac{2}{0.4}\left[1.875^{0.2857}-1\right]=5(1.1967-1)=0.9835,
\qquad M_1=0.9917,
$$

$$
U_1=0.9917\times332.4=329.7\ \mathrm{m\,s^{-1}}.
$$

*Table route* (the lecture stopped after finding $\sigma$). The isentropic table lists $p/p_0$, so invert: $p_1/p_0=1/1.875=0.5333$. The bounding rows are

| $M$ | $p/p_0$ |
|---:|---:|
| 0.98 | 0.5407 |
| 1.00 | 0.5283 |

$$
\sigma=\frac{0.5333-0.5407}{0.5283-0.5407}=0.597,
\qquad
M_1=0.98+0.597(1.00-0.98)=0.9919,
$$

$$
U_1=0.9919\times332.4=329.7\ \mathrm{m\,s^{-1}}.
$$

The two routes agree to three significant figures.

#### Example 2 in full — supersonic, by table (weekend homework)

Search the $p_{02}/p_1$ column of the normal-shock table for 5:

| $M_1$ | $p_{02}/p_1$ |
|---:|---:|
| 1.86 | 4.9497 |
| 1.88 | 5.0452 |

$$
\sigma=\frac{5-4.9497}{5.0452-4.9497}=0.527,
\qquad
M_1=1.86+0.527(0.02)=1.8705,
$$

$$
U_1=1.8705\times332.4=621.8\ \mathrm{m\,s^{-1}}.
$$

Solving the Rayleigh relation exactly with a root finder gives $M_1=1.8706$. Linear interpolation is fine here because the table spacing is small.

> [!warning] Transcript slip
> In Lecture 1-3 (line 156) the lecturer says $1.875<1.893$ means the aircraft is *"flying at supersonic speed"*. That's a slip of the tongue: a ratio below the sonic value means subsonic, which is why the subsonic formula is used next. The lecture also quotes the sonic value as $1.8934$; the exact value is $(1.2)^{3.5}=1.8929$.

#### Optional — Newton–Raphson for the Rayleigh relation

The lecture suggested a root finder instead of the table. Define $f(M_1)=p_{02}/p_1\big|_{\text{Rayleigh}}(M_1)-5$ and iterate

$$
M^{(k+1)}=M^{(k)}-\frac{f(M^{(k)})}{f'(M^{(k)})},
$$

with $f'$ taken numerically from $[f(M+h)-f(M-h)]/2h$. Starting from $M^{(0)}=2$, it converges to $1.8706$ in two or three steps ($2\to1.8749\to1.8706$). Always start with $M^{(0)}>1$: the Rayleigh relation is only valid for supersonic flow.

## 8. Problem-solving workflow

1. Draw the stations and label $1,2,01,02$.
2. State whether each segment is adiabatic, isentropic, or crosses a shock.
3. Form the measured pressure ratio before choosing a model.
4. Use the $M=1$ ratio to choose subsonic or supersonic Pitot analysis.
5. If using a table, check whether it lists a ratio or its reciprocal.
6. Interpolate once, then reuse the same $\sigma$ for every required column.
7. Recover velocity from $U=M\sqrt{\gamma RT}$ using the local static temperature.
8. Sanity-check directions: a normal shock raises $p,T,\rho$ and lowers $U,M,p_0$.

## Links

- Parent: [[SESA3029 Aerothermodynamics Hub]]
- Next: [[SESA3029 W02 - Oblique Shock Relations and Mach Waves]]
- Prior knowledge: [[SESA2023 W03 - Compressible Flow, Normal Shocks and Nozzles]]
- Aerodynamic review: [[SESA2022 T4 - Thin Aerofoil Theory]]
- Full formula list: [[SESA3029 Formula Sheet]]
- Other modules: the jump relations of §5 are the integral conservation laws applied to a thin control volume round the shock. [[SESA3043 1.2 - Conservation Laws and Governing Equations#1. Integral-to-differential strategy|SESA3043 1.2 §1]] shrinks the control volume further to get the differential equations, which need smooth fields, so across a shock (a few mean free paths thick) only the integral form works. The von Kármán momentum integral in [[SESA3043 3.5 - Momentum Integral Equation|SESA3043 3.5]] is the same kind of momentum balance, taken across a boundary layer instead.

## Sources

- `Lecture1-1.pdf` with transcript `Lecture 1-1.txt`
- `Lecture1-2.pdf` with transcript `Lecture 1-2.txt`
- `Lecture1-3.pdf` with transcript `Lecture 1-3.txt`
- Anderson, *Fundamentals of Aerodynamics* (the module's main text): Week 1 reading is §§1.1, 7.1, 7.2, 7.5, 8.3, 8.4, 8.6 (module schedule, `Lecture1-1.pdf` p. 10), plus §8.7 for Pitot measurements.

## Self-study tasks

Everything here was set, or explicitly left to you, in the Week 1 lectures, and the worked solutions are in this note. Try each one closed-book before checking the linked section.

### Core

- [ ] Pressure jump. *"I will leave all the rest to you once again as a homework"* (L1-2, ll. 276–278). → [[#Pressure jump (homework)]]
- [ ] $M_2^2$ as a function of $M_1$, *"slightly more involved"* (L1-2, ll. 317–320). → [[#Downstream Mach number (homework)]]
- [ ] The Rayleigh Pitot formula: combine the shock pressure jump with isentropic stagnation downstream and eliminate $M_2$ (L1-3, ll. 121–128). → [[#Deriving the Rayleigh Pitot formula]]
- [ ] The subsonic Pitot example by formula and by table: *"please double check these numbers… during the weekend"* (L1-3, l. 159). Target $M_1=0.9919$, $U_1=329.7$ m/s. → [[#Example 1 in full — subsonic, by formula and by table]]
- [ ] The supersonic Pitot example, $p_{02}/p_1=5$, by table interpolation: *"I will leave it as your homework for the weekend"* (L1-3, l. 205). Target $M_1=1.8705$, $U_1=621.8$ m/s. → [[#Example 2 in full — supersonic, by table (weekend homework)]]

### Further practice

- [ ] The isentropic density–temperature relation $\rho_2/\rho_1=(T_2/T_1)^{1/(\gamma-1)}$, from $p_2/p_1=(T_2/T_1)^{\gamma/(\gamma-1)}$ and $p=\rho RT$. *"I will leave it to you to have a practice on that"* (L1-2, ll. 30–33). → [[#3. Perfect-gas thermodynamics]]
- [ ] Reproduce the lecture's derivations of $T_0/T=1+\tfrac{\gamma-1}{2}M^2$, the Prandtl relation and the density jump. → [[#4. Stagnation properties]] · [[#Energy and the Prandtl relation]] · [[#Density jump (shown in lecture)]]
- [ ] Temperature jump (homework). → [[#Temperature jump (homework)]]
- [ ] Strong-shock limits as $M_1\to\infty$ for $M_2$, $\rho_2/\rho_1$, $p_2/p_1$ and $T_2/T_1$: *"You will find them"* (L1-2, ll. 354–379). → [[#Strong-shock limits]]
- [ ] Show that the compressible subsonic Pitot relation reduces to Bernoulli as $M_1\to0$ (L1-3, ll. 58–95; the transcript is garbled here, so redo it cleanly). → [[#Low-Mach consistency check]]
- [ ] Nozzle exit Mach number from $T_0=1000$ K and $T_e=600$ K, exactly and by interpolation. Target $M_e=1.8257$. → [[#Nozzle example]]
- [ ] Normal shock with $p_2/p_1=1.25$, $T_1=15^\circ$C. Target $M_2=0.9103$, $T_2=307.2$ K, $U_2=319.8$ m/s. → [[#Normal-shock example]]
- [ ] Optional: solve the supersonic Pitot case with Newton–Raphson. → [[#Optional — Newton–Raphson for the Rayleigh relation]]
- [ ] Revisit leading-edge suction from SESA2022: why an inviscid thin aerofoil gives pure lift rather than a force normal to the plate (L1-1, ll. 256–300). → [[#2. Aerodynamic review and the low-speed baseline]]
- [ ] Learn the sonic Pitot discriminator, $p_0/p\,|_{M=1}=1.8929$ (L1-3, ll. 142–148).
- [ ] Read the Anderson sections in the Week 1 module schedule (L1-1, ll. 163–173 and L1-3, l. 205: *"It is up to you to grasp these details by reading the textbooks"*) and work the end-of-chapter examples. Solutions are in the Blackboard "Example questions" folder; there are no tutorials in this module (L1-1, ll. 144–155).
- [ ] Download the Week 1 past-paper questions on normal shocks and Pitot probes from Blackboard.
