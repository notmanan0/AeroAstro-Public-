---
title: "SESA3029 W09d - Thermal Radiation"
module: "SESA3029 Aerothermodynamics"
type: topic
stream: "Block 5: Heat transfer"
order: 13
tags: [sesa3029, heat-transfer, radiation, blackbody, planck, wien, stefan-boltzmann, kirchhoff, emissivity, shape-factor, solid-angle]
aliases: ["SESA3029 Lecture 5.5", "SESA3029 Lecture 5.6", "SESA3029 W09d", "Thermal radiation"]
date: 2026-11-17
status: written-ahead
coverage: "Lectures 5.5 (all 13 slides) and 5.6 (all 15 slides) written ahead from the slides; no transcript yet"
parent: ["[[SESA3029 Aerothermodynamics Hub]]"]
prerequisites: ["[[SESA3029 W09a - Heat Conduction and Thermal Resistance]]", "[[SESA3029 W09c - Critical Thickness of Insulation and Fins]]", "[[Blackbody Radiation]]", "[[Absorptance and Emittance]]"]
next_topics: ["[[SESA3029 W09e - Numerical Methods in Conduction]]"]
key_concepts: ["[[Kirchhoff's Law of Thermal Radiation]]", "[[Planck's Law]]", "[[Wien's Displacement Law]]", "[[Stefan-Boltzmann Law]]", "[[Emissivity]]", "[[Solid Angle]]", "[[Radiation Shape Factor]]"]
tutorial_sheets: ["[[SESA3029 Example Sheet 3 - Solutions]]"]
sources: ["02 - Sources/Lectures/Lecture5.5(1).pdf", "02 - Sources/Lectures/Lecture5.6(1).pdf"]
---

# SESA3029 W09d - Thermal Radiation

> [!abstract] Summary
> Every body above 0 K emits electromagnetic radiation because of its temperature, and no medium is needed to carry it. A blackbody emits the most any surface can at each wavelength; its spectrum is Planck's law $E_{b,\lambda}=C_1/\{\lambda^5[\exp(C_2/\lambda T)-1]\}$, whose peak sits at $\lambda T=2897.8$ μm K (Wien) and whose integral is $E_b=\sigma T^4$ (Stefan–Boltzmann). A real surface emits $\epsilon\sigma T^4$, and at equilibrium its absorptivity equals its emissivity (Kirchhoff). Exchange between surfaces is governed by the shape factor $F_{i-j}$, the fraction of the radiation leaving $i$ that lands on $j$, which obeys reciprocity $A_iF_{ij}=A_jF_{ji}$ and the summation rule $\sum_jF_{ij}=1$.

> [!summary]- Exam use: quick path
> - **Use it when:** a surface loses or gains heat by radiation (a hot wall in vacuum, a re-entry heat shield, a planet in sunlight), or a question asks for a peak wavelength, a total emissive power or a shape factor.
> - **Assumptions:** temperatures in **kelvin**; black or grey, diffuse, opaque surfaces ($\tau=0$); no absorbing gas between surfaces; steady state for balance problems.
> - **Method:** 1. Draw the surfaces and decide which are black, grey or openings. 2. Get every shape factor from the obvious ones ($F_{ii}=0$ for a convex surface, $F=1$ when one surface is wrapped by another), then reciprocity and the summation rule. 3. Emission $\epsilon\sigma T^4A$; net black exchange $\dot Q_{1-2}=A_1F_{12}\sigma(T_1^4-T_2^4)$. 4. Write the steady balance (absorbed = emitted, or convection in = radiation out) and solve for $T$; a quartic needs Newton iteration. 5. Wien: $\lambda_{max}=2897.8/T$ μm.
> - **Common mistakes:** using °C inside $T^4$ (278.75 K is not 278.75 °C, and $5.6^4$ is meaningless); treating $\sigma AT^4$ as the net heat loss when the surroundings also radiate back.
> - **Practise:** [[#13. Worked example: steady temperature of the Earth|the Sun–Earth balance]] · [[SESA3029 Example Sheet 3 - Solutions#Q4. Meteor stagnation-point heating|ES3 Q4]] (convection in, grey radiation out)

Conduction and convection need matter: molecules pass energy to their neighbours, or a moving fluid carries it. Radiation does not. Every body emits photons, in random directions, with random phase and frequency, because its molecules, atoms and electrons are constantly changing energy state, and temperature is the measure of that activity. The photons travel at the speed of light through a vacuum as easily as through air, which makes radiation the fastest of the three modes and the only one by which the Sun heats the Earth. Radiation also passes through a medium colder than both the source and the receiver: a person standing near a 900 °C bonfire in 5 °C air is warmed directly by the fire's radiation, while the air between them stays cold.

Radiation matters in aerothermodynamics wherever surfaces are hot or the surroundings are a vacuum. A re-entry heat shield at 2000 K sheds most of its convective heat load by radiation (the radiative-equilibrium surface temperature of [[SESA3029 Example Sheet 3 - Solutions#Q4. Meteor stagnation-point heating|ES3 Q4]]), and a spacecraft in orbit has no other way to lose heat at all ([[Spacecraft Thermal Balance Equation]]).

The subject splits into two parts. The first concerns a single surface: how incident radiation divides at it, what a blackbody is, and how emission depends on wavelength and temperature (§§1–7). The second concerns exchange between surfaces, which needs the solid angle and the shape factor (§§8–12), and the radiative balance of the Earth applies both (§13).

## 1. Thermal radiation and the electromagnetic spectrum

**Thermal radiation** is the electromagnetic radiation a body emits because of its temperature. It is emitted by all bodies above absolute zero, by solids, liquids and gases alike. On the electromagnetic spectrum, which runs from electrical power waves ($\lambda\sim10^{10}$ nm) through radio, microwave, infrared, visible, ultraviolet, X-rays and γ-rays to cosmic rays ($\lambda\sim10^{-9}$ nm), thermal radiation occupies the band from about 0.1 μm to 100 μm. That band covers part of the ultraviolet, all of the visible (0.40–0.76 μm) and most of the infrared. Shorter wavelength means higher photon energy, $E=h\nu=hc_0/\lambda$.

What a body emits depends on three things: its temperature, its material and the condition of its surface. Measured spectra of different bodies at the same temperature (600 K, say) differ in shape and size, but they all lie below one limiting curve. That limiting curve is always measured from the pin hole of an isothermal cavity, and the same curve comes from a surface coated in carbon black (soot). It is the blackbody spectrum of §4.

## 2. Reflection, absorption and transmission

Radiation falling on a surface (the irradiation $G$, in W/m²) can take three pathways. Part is reflected, part is absorbed and part is transmitted through the body. The fractions are the **reflectivity** $\rho$, the **absorptivity** $\alpha$ and the **transmissivity** $\tau$:

$$
\rho=\frac{G_{ref}}{G},\qquad \alpha=\frac{G_{abs}}{G},\qquad \tau=\frac{G_{tr}}{G}.
$$

Energy is conserved at the surface, so the three parts add up to the incident radiation:

$$
G_{ref}+G_{abs}+G_{tr}=G .
$$

Divide by $G$:

$$
\boxed{\rho+\alpha+\tau=1}
$$

Most solids are **opaque**, with $\tau=0$, so $\alpha=1-\rho$. A polished metal surface has $\rho\to1$ and absorbs almost nothing; a surface painted matt black has $\rho\to0$ and absorbs almost everything. The colours of objects come from reflection in the visible band: a red dress looks red because its pigment reflects red light and absorbs the other colours.

![[at_w09d_surface_and_kirchhoff.png|900]]

The symbol $\alpha$ is absorptivity throughout this note; [[SESA3029 W09e - Numerical Methods in Conduction|W09e]] uses the same letter for thermal diffusivity, so check which is meant when the two topics meet in one question.

## 3. Kirchhoff's law of thermal radiation

Put a body at temperature $T$ inside a closed enclosure whose walls are held at the same temperature $T$, with a vacuum between them (panel (b) above). An isothermal enclosure is the isothermal cavity of §1, so the radiation filling it is blackbody radiation and the irradiation on the body is $G=E_b(T)=\sigma T^4$ (§6). The body, of area $A$, absorbs

$$
\dot Q_{abs}=\alpha\,G\,A=\alpha\,\sigma T^4A .
$$

It emits $\dot Q_{emit}=E\,A$, and writing its emission as a fraction $\epsilon$ (the **emissivity**, §7) of the blackbody value at the same temperature,

$$
\dot Q_{emit}=\epsilon\,\sigma T^4A .
$$

Body and enclosure are at the same temperature, so they are in thermal equilibrium. If the body absorbed more than it emitted there would be a net energy flow into it and its temperature would rise above the enclosure's, which the second law forbids. Hence

$$
\alpha\,\sigma T^4A=\epsilon\,\sigma T^4A
\quad\Rightarrow\quad
\boxed{\alpha=\epsilon}
$$

This is **Kirchhoff's law**: a good absorber is an equally good emitter. Soot absorbs all wavelengths and, by the same token, emits at all wavelengths with the maximum intensity.

The argument assumes equilibrium, with the incident radiation coming from a source at the body's own temperature. Repeated wavelength by wavelength (a filter in the enclosure that passes one band only) it gives $\alpha_\lambda=\epsilon_\lambda$, which holds generally. The total values $\alpha$ and $\epsilon$ are only equal when the body is grey (§7) or the irradiation has the spectrum of a blackbody at the body's own temperature. Sunlight on a 300 K surface is the standard exception: white paint has a solar absorptivity near 0.2 but an infrared emissivity near 0.9, which is the basis of spacecraft thermal control ([[Absorptance and Emittance]]).

## 4. The blackbody and Planck's law

A **blackbody** is the limiting case of §1. It is a perfect absorber ($\alpha=1$ at every wavelength and direction) and therefore, by Kirchhoff, a perfect emitter: at a given temperature and wavelength no surface can emit more energy than a blackbody. It also emits uniformly in all directions (it is a diffuse emitter), which is used in §9.

Classical statistical mechanics, which relates the temperature of a system to the average energy of its modes, predicts a blackbody spectrum that matches experiment at long wavelengths but grows without bound at short ones. The failure at short wavelengths is the **ultraviolet catastrophe**. Max Planck found a formula that fits the measured limiting curve at all wavelengths by assuming that electromagnetic energy is emitted in discrete packets (quanta, or photons) of energy

$$
E=h\nu ,\qquad h=6.6256\times10^{-34}\ \text{J s (Planck's constant)},
$$

with $\nu$ the frequency in Hz. The resulting **spectral blackbody emissive power**, the power emitted per unit area per unit wavelength, is **Planck's law**:

$$
\boxed{E_{b,\lambda}(\lambda,T)=\frac{C_1}{\lambda^5\left[\exp\left(C_2/\lambda T\right)-1\right]}}\qquad\left[\mathrm{W\,m^{-2}\,\mu m^{-1}}\right]
$$

with $\lambda$ in μm, $T$ the absolute temperature in K, and

$$
C_1=2\pi hc_0^2=3.742\times10^8\ \mathrm{W\,\mu m^4\,m^{-2}},\qquad
C_2=\frac{hc_0}{k_B}=1.439\times10^4\ \mathrm{\mu m\,K},
$$

where $c_0=2.998\times10^8$ m/s is the speed of light in vacuum and $k_B=1.38065\times10^{-23}$ J/K is Boltzmann's constant.

> [!check] The two constants
> $2\pi hc_0^2=2\pi(6.6256\times10^{-34})(2.998\times10^8)^2=2.3415\times10^{-16}$ W m², and $1\ \mathrm{m^2}=10^{24}\ \mathrm{\mu m^4\,m^{-2}}$, so $C_1=3.7415\times10^8$ W μm⁴/m² ✓. $hc_0/k_B=1.4387\times10^{-2}$ m K $=1.439\times10^4$ μm K ✓. With the current value $h=6.62607\times10^{-34}$ J s, $C_1=3.7418\times10^8$; the difference is in the fifth figure.

The two limits of Planck's law show where the classical theory went wrong. Write $x=C_2/\lambda T$.

At long wavelength $x\ll1$, and $e^x\simeq1+x$:

$$
\exp\left(\frac{C_2}{\lambda T}\right)-1\simeq\frac{C_2}{\lambda T}
\quad\Rightarrow\quad
E_{b,\lambda}\simeq\frac{C_1}{\lambda^5}\,\frac{\lambda T}{C_2}=\frac{C_1T}{C_2\lambda^4}.
$$

This is the classical (Rayleigh–Jeans) result. It is correct at long wavelengths, but as $\lambda\to0$ it grows like $\lambda^{-4}$ and its integral over all wavelengths is infinite: the ultraviolet catastrophe.

At short wavelength $x\gg1$, the exponential dominates the $-1$:

$$
E_{b,\lambda}\simeq\frac{C_1}{\lambda^5}\exp\left(-\frac{C_2}{\lambda T}\right)\to0\quad\text{as }\lambda\to0 .
$$

The quantisation makes high-energy photons expensive, the exponential wins over $\lambda^{-5}$, and the spectrum turns over.

![[at_w09d_planck_spectra.png|900]]

The curves have four features (log axes above). Emission is a continuous function of wavelength that rises, peaks and falls. At any wavelength a hotter blackbody emits more, so the curves never cross. As temperature rises the peak shifts to shorter wavelengths. The line joining the peaks is straight on log axes, which is Wien's displacement law.

## 5. Wien's displacement law

To find the peak, write Planck's law in terms of $x=C_2/\lambda T$. Since $\lambda=C_2/(xT)$,

$$
\frac{1}{\lambda^5}=\frac{x^5T^5}{C_2^5}
\quad\Rightarrow\quad
E_{b,\lambda}=\frac{C_1T^5}{C_2^5}\,\frac{x^5}{e^x-1}=\frac{C_1T^5}{C_2^5}\,f(x),\qquad f(x)=\frac{x^5}{e^x-1}.
$$

At fixed $T$ the prefactor is constant, so the whole family of curves is one curve $f(x)$ scaled in height by $T^5$ and in wavelength by $1/T$ (panel (a) below). By the chain rule,

$$
\frac{\partial E_{b,\lambda}}{\partial\lambda}=\frac{C_1T^5}{C_2^5}\,\frac{\mathrm df}{\mathrm dx}\,\frac{\mathrm dx}{\mathrm d\lambda},
\qquad
\frac{\mathrm dx}{\mathrm d\lambda}=-\frac{C_2}{\lambda^2T}\neq0,
$$

so the maximum over $\lambda$ is where $\mathrm df/\mathrm dx=0$. By the quotient rule,

$$
\frac{\mathrm df}{\mathrm dx}=\frac{5x^4(e^x-1)-x^5e^x}{(e^x-1)^2}.
$$

Setting the numerator to zero and dividing by $x^4$ (the peak is at $x>0$):

$$
5(e^x-1)=x\,e^x .
$$

Divide by $e^x$:

$$
x=5\left(1-e^{-x}\right).
$$

This is transcendental. Iterate $x_{k+1}=5(1-e^{-x_k})$ from $x_0=5$:

$$
x_1=5(1-e^{-5})=4.96631,\quad x_2=4.96516,\quad x_3=4.96512,\quad x_4=4.96511 .
$$

So the peak is at $C_2/(\lambda T)=4.96511$, that is

$$
\lambda_{max}T=\frac{C_2}{4.96511}=\frac{14\,388}{4.96511}\quad\Rightarrow\quad\boxed{\left(\lambda T\right)_{max\ power}=2897.8\ \mathrm{\mu m\,K}}
$$

This is **Wien's displacement law**. Wien obtained the form $\lambda_{max}T=$ const from classical thermodynamics before Planck; Planck's law supplies the constant. With the rounded $C_2=1.439\times10^4$ μm K the quotient is 2898.2, so the fourth figure depends on how $C_2$ is rounded.

![[at_w09d_wien_and_grey.png|900]]

The peaks of the curves in §4 follow at once:

| Source | $T$ (K) | $\lambda_{max}$ (μm) | Band |
|---|---:|---:|---|
| Solar surface | 5800 | 0.50 | visible |
| Tungsten-like filament | 2000 | 1.45 | near infrared |
| Hot wall | 600 | 4.83 | infrared |
| Room-temperature surface | 300 | 9.66 | infrared |

The Sun's peak at 0.5 μm sits in the visible range (0.40–0.76 μm), which is no coincidence for eyes that evolved under it. A human body peaks near 9.7 μm in the infrared, which is why people do not glow in the dark but show up brightly on an infrared camera; 9.72 μm corresponds to $2897.8/9.72=298$ K. A body has to reach about 800 K before the short-wavelength tail of its spectrum is visible as a dull red glow.

## 6. The Stefan–Boltzmann law

The **total emissive power** $E_b$ is the energy emitted by a blackbody per unit time and per unit area, over all wavelengths:

$$
E_b(T)=\int_0^\infty E_{b,\lambda}(\lambda,T)\,\mathrm d\lambda=\int_0^\infty\frac{C_1}{\lambda^5\left[\exp(C_2/\lambda T)-1\right]}\,\mathrm d\lambda .
$$

Change variable to $x=C_2/\lambda T$, so that

$$
\lambda=\frac{C_2}{xT},\qquad \mathrm d\lambda=-\frac{C_2}{x^2T}\,\mathrm dx,\qquad \frac{1}{\lambda^5}=\frac{x^5T^5}{C_2^5}.
$$

As $\lambda$ runs from 0 to $\infty$, $x$ runs from $\infty$ to 0. Substitute:

$$
E_b=\int_\infty^0 C_1\frac{x^5T^5}{C_2^5}\,\frac{1}{e^x-1}\left(-\frac{C_2}{x^2T}\right)\mathrm dx .
$$

Collect the powers of $T$ and $C_2$, and use the minus sign to swap the limits:

$$
E_b=\frac{C_1T^4}{C_2^4}\int_0^\infty\frac{x^3}{e^x-1}\,\mathrm dx .
$$

The temperature has come out of the integral as $T^4$; what remains is a pure number. To evaluate it, expand the denominator as a geometric series in $e^{-x}<1$:

$$
\frac{1}{e^x-1}=\frac{e^{-x}}{1-e^{-x}}=\sum_{n=1}^\infty e^{-nx}.
$$

Integrate term by term. Each term is a standard integral, $\int_0^\infty x^3e^{-nx}\,\mathrm dx=3!/n^4=6/n^4$, so

$$
\int_0^\infty\frac{x^3}{e^x-1}\,\mathrm dx=\sum_{n=1}^\infty\frac{6}{n^4}=6\,\zeta(4)=6\cdot\frac{\pi^4}{90}=\frac{\pi^4}{15}=6.4939 .
$$

Hence

$$
E_b=\frac{\pi^4C_1}{15\,C_2^4}\,T^4
\quad\Rightarrow\quad
\boxed{E_b(T)=\sigma T^4},\qquad
\sigma=\frac{\pi^4C_1}{15C_2^4}=5.67\times10^{-8}\ \mathrm{W\,m^{-2}\,K^{-4}}.
$$

The units work: $C_1/C_2^4$ is $(\mathrm{W\,\mu m^4\,m^{-2}})/(\mathrm{\mu m^4\,K^4})=\mathrm{W\,m^{-2}\,K^{-4}}$. This is the **Stefan–Boltzmann law**, with $\sigma$ the Stefan–Boltzmann constant. Josef Stefan found the $T^4$ dependence experimentally and Ludwig Boltzmann derived it from thermodynamics, both before Planck; Planck's law shows where $\sigma$ comes from, $\sigma=2\pi^5k_B^4/(15h^3c_0^2)$.

> [!check] Numbers
> $\pi^4(3.742\times10^8)/[15(1.439\times10^4)^4]=5.667\times10^{-8}$ W/m²K⁴; the exact constants give $5.670\times10^{-8}$ ✓. Integrating Planck's law numerically at $T=5778$ K gives $63.17$ MW/m², against $\sigma T^4=63.20$ MW/m² (the 0.05 % gap is the rounding of $C_1$ and $C_2$). Of that, 42.5 % lies in the visible band 0.40–0.76 μm, while a 300 K surface emits a fraction of order $10^{-23}$ there.

For a black surface of area $A$ the rate of emission is

$$
\dot Q=E_b\times A=\sigma AT^4\qquad[\mathrm W].
$$

This is what the surface emits, not its net heat loss. The surroundings radiate back, and the net exchange needs the shape factors of §9–§11. For a small black body of area $A$ at $T_1$ inside a large enclosure at $T_2$ (or open sky), every ray it emits is absorbed by the surroundings and it receives $\sigma T_2^4$ per unit area, so the net loss is $\sigma A(T_1^4-T_2^4)$. The same form, with $\epsilon$ in front, is the radiation boundary condition of [[SESA3029 W09e - Numerical Methods in Conduction#3. Boundary conditions|W09e §3]].

## 7. Emissivity and grey bodies

The **emissivity** of a surface is the ratio of the power it emits to the power a blackbody at the same temperature emits:

$$
\epsilon=\frac{E}{E_b}.
$$

A blackbody has $\epsilon=1$ and every real object has $\epsilon<1$. Emissivity depends on temperature and on wavelength, so the full description is the **spectral (monochromatic) emissivity** $\epsilon_\lambda=E_\lambda/E_{b,\lambda}$ at each wavelength. The total emissivity is then an average of $\epsilon_\lambda$ weighted by the blackbody spectrum:

$$
E=\int_0^\infty\epsilon_\lambda E_{b,\lambda}\,\mathrm d\lambda
\quad\Rightarrow\quad
\epsilon=\frac{1}{\sigma T^4}\int_0^\infty\epsilon_\lambda E_{b,\lambda}\,\mathrm d\lambda .
$$

A **grey body** is the idealisation in which $\epsilon_\lambda$ does not depend on wavelength. Its emission is the blackbody curve lowered by a constant proportion at every wavelength (panel (b) of the figure in §5). Take the constant outside the integral:

$$
E=\epsilon\int_0^\infty E_{b,\lambda}\,\mathrm d\lambda=\epsilon E_b
\quad\Rightarrow\quad
\boxed{E=\epsilon E_b=\epsilon\sigma T^4}\qquad[\mathrm{W\,m^{-2}}].
$$

For a grey body Kirchhoff's law holds for the totals, $\alpha=\epsilon$, whatever the source of the incident radiation, because $\alpha_\lambda=\epsilon_\lambda$ at every wavelength and both are the same constant. Real surfaces have wavy $\epsilon_\lambda$ curves, so the grey model is an approximation, and it is the model meant whenever a problem gives a single $\epsilon$. At 600 K a grey surface with $\epsilon=0.6$ emits $0.6\times5.67\times10^{-8}\times600^4=4.41$ kW/m², against 7.35 kW/m² for a blackbody.

## 8. Solid angle

A **plane angle** $\theta$ is the arc length $s$ it cuts from a circle divided by the radius, $\theta=s/r$ in radians. On a circle of unit radius the arc length equals the angle, and the full circle is $2\pi$.

A **solid angle** $\omega$ is the three-dimensional version: join every point of a patch on a sphere to the centre and the patch subtends a cone-like solid angle

$$
\omega=\frac{S}{r^2}\qquad[\text{steradian, sr}],
$$

where $S$ is the area of the patch on the sphere of radius $r$. On a unit sphere the area equals the solid angle, and the whole sphere is $4\pi r^2/r^2=4\pi$ sr.

For integrals over directions, use spherical angles: the polar angle $\theta$ from the surface normal and the azimuth $\phi$ around it. A small patch on a sphere of radius $R$ has sides $R\,\mathrm d\theta$ and $R\sin\theta\,\mathrm d\phi$, so

$$
\mathrm dA_n=R^2\sin\theta\,\mathrm d\theta\,\mathrm d\phi
\quad\Rightarrow\quad
\mathrm d\omega=\frac{\mathrm dA_n}{R^2}=\sin\theta\,\mathrm d\theta\,\mathrm d\phi .
$$

The hemisphere above a surface element covers $0\le\theta\le\pi/2$ and $0\le\phi\le2\pi$:

$$
\omega_{hemisphere}=\int_0^{2\pi}\!\!\int_0^{\pi/2}\sin\theta\,\mathrm d\theta\,\mathrm d\phi=2\pi\left[-\cos\theta\right]_0^{\pi/2}=2\pi\ \text{sr}.
$$

A surface element $\mathrm dA$ that is not perpendicular to the line of sight, but tilted so that its normal makes an angle $\theta$ with that line, presents only its projected area $\mathrm dA\cos\theta$, so it subtends $\mathrm d\omega=\mathrm dA\cos\theta/R^2$ at a distance $R$. Seen from the Sun, the Earth subtends $\pi R_E^2/d^2=5.70\times10^{-9}$ sr.

![[at_w09d_solid_angle_geometry.png|900]]

## 9. The shape factor

Two black surfaces exchange radiation, but in general not all the radiation leaving one reaches the other. The **shape factor** (also called the view factor) is

$$
F_{i-j}=\text{fraction of the energy leaving surface }i\text{ that reaches surface }j,
$$

written $F_{ij}$ for short. It depends only on geometry: sizes, distance and orientation. The energy leaving black surface $i$ that arrives at $j$ is then $E_{bi}A_iF_{ij}$.

Two cases are obvious. For two infinite parallel plates every ray leaving one plate hits the other, so $F_{12}=F_{21}=1$, $\dot Q_{12}=E_{b1}A_1F_{12}$ and $\dot Q_{21}=E_{b2}A_2F_{21}$. For a sphere (1) inside a hollow enclosure (2), every ray leaving the sphere hits the enclosure, so $F_{12}=1$; but radiation leaving the inner face of the enclosure can miss the sphere and land on another part of the enclosure, so $F_{21}<1$ (worked out in §12).

![[at_w09d_enclosures.png|900]]

For a general pair of surfaces the shape factor is found by asking how large surface 2 looks from each point of surface 1, that is, what solid angle it fills, or equivalently what area it projects onto a hemisphere drawn over surface 1. The derivation needs one more quantity, the **radiation intensity** $I$: the power emitted per unit area of the emitting surface projected normal to the direction of travel, per unit solid angle. A blackbody emits uniformly in all directions (§4), so its intensity $I_b$ is the same in every direction.

The power leaving element $\mathrm dA_1$ into a small solid angle $\mathrm d\omega$ at angle $\theta_1$ from its normal is intensity times projected area times solid angle:

$$
\mathrm d\dot Q=I_b\,\mathrm dA_1\cos\theta_1\,\mathrm d\omega .
$$

Integrate over the hemisphere to get the total emission, using $\mathrm d\omega=\sin\theta\,\mathrm d\theta\,\mathrm d\phi$ from §8:

$$
E_b\,\mathrm dA_1=I_b\,\mathrm dA_1\int_0^{2\pi}\!\!\int_0^{\pi/2}\cos\theta\sin\theta\,\mathrm d\theta\,\mathrm d\phi .
$$

The inner integral is $\left[\tfrac12\sin^2\theta\right]_0^{\pi/2}=\tfrac12$, and the outer one multiplies by $2\pi$:

$$
E_b\,\mathrm dA_1=\pi I_b\,\mathrm dA_1
\quad\Rightarrow\quad
I_b=\frac{E_b}{\pi}.
$$

(The factor is $\pi$, not $2\pi$, because emission at grazing angles is weighted by $\cos\theta$.) Now let the solid angle be the one subtended at $\mathrm dA_1$ by an element $\mathrm dA_2$ a distance $R$ away whose normal makes angle $\theta_2$ with the line joining them (panel (b) above):

$$
\mathrm d\omega_{2}=\frac{\mathrm dA_2\cos\theta_2}{R^2}.
$$

The power going from $\mathrm dA_1$ to $\mathrm dA_2$ is therefore

$$
\mathrm d\dot Q_{1\to2}=\frac{E_{b1}}{\pi}\,\frac{\cos\theta_1\cos\theta_2}{R^2}\,\mathrm dA_1\,\mathrm dA_2 .
$$

Integrate over both surfaces and divide by the total $E_{b1}A_1$ leaving surface 1. $E_{b1}$ cancels, which is why the shape factor is purely geometric:

$$
\boxed{F_{12}=\frac{1}{A_1}\int_{A_1}\!\int_{A_2}\frac{\cos\theta_1\cos\theta_2}{\pi R^2}\,\mathrm dA_2\,\mathrm dA_1}
$$

Assumptions: diffuse surfaces (uniform intensity), uniform emission over $A_1$, and nothing absorbing between the surfaces.

> [!check] An element facing a coaxial disk
> Let $\mathrm dA_1$ face a parallel disk of radius $a$ centred on its normal at distance $H$. Take $\mathrm dA_2$ as a ring of radius $r$ and width $\mathrm dr$: $\mathrm dA_2=2\pi r\,\mathrm dr$, $R^2=r^2+H^2$ and $\cos\theta_1=\cos\theta_2=H/\sqrt{r^2+H^2}$. Then
> $$F_{d1-2}=\int_0^a\frac{H^2}{r^2+H^2}\,\frac{2\pi r\,\mathrm dr}{\pi(r^2+H^2)}=H^2\int_0^a\frac{2r\,\mathrm dr}{(r^2+H^2)^2}=H^2\left[-\frac{1}{r^2+H^2}\right]_0^a=\frac{a^2}{a^2+H^2}.$$
> For $a=1$, $H=2$ this is 0.2, and a direct numerical double integral gives 0.2000 ✓. As $a\to\infty$ it tends to 1, the infinite parallel plate.

## 10. Reciprocity relation

Take two black surfaces $A_1$ at $T_1$ and $A_2$ at $T_2$. The energy leaving 1 and arriving at 2 is $E_{b1}A_1F_{12}$, and the energy leaving 2 and arriving at 1 is $E_{b2}A_2F_{21}$. Black surfaces absorb everything that reaches them, so the net exchange from 1 to 2 is

$$
\dot Q_{1-2}=E_{b1}A_1F_{12}-E_{b2}A_2F_{21}.
$$

If the two surfaces are at the same temperature, $T_1=T_2$, there can be no net exchange (the second law again), so $\dot Q_{1-2}=0$, and also $E_{b1}=E_{b2}$. Substituting both:

$$
0=E_{b1}\left(A_1F_{12}-A_2F_{21}\right)
\quad\Rightarrow\quad
\boxed{A_1F_{12}=A_2F_{21}}
$$

The shape factors are geometric, so a relation found at $T_1=T_2$ holds at any temperatures. In general, for any two surfaces,

$$
A_iF_{ij}=A_jF_{ji}.
$$

The integral of §9 shows the same thing directly: $A_1F_{12}$ is the double integral of $\cos\theta_1\cos\theta_2/(\pi R^2)$ over both surfaces, which is symmetric in 1 and 2 and so also equals $A_2F_{21}$. With reciprocity the net exchange takes either form:

$$
\dot Q_{1-2}=A_1F_{12}\left(E_{b1}-E_{b2}\right)=A_2F_{21}\left(E_{b1}-E_{b2}\right)=A_1F_{12}\,\sigma\left(T_1^4-T_2^4\right).
$$

This holds for black surfaces with no other surface reflecting radiation between them.

## 11. Summation rule

An **enclosure** is a set of surfaces that together close off a volume. All radiation leaving surface $i$ of an enclosure must either hit some other surface of the enclosure or hit itself. The fractions therefore account for all of it:

$$
\boxed{\sum_{j=1}^NF_{i\to j}=1}
$$

This is the **summation rule**: the sum of the shape factors from one surface of an enclosure to all the surfaces of the enclosure, including itself, is unity. $F_{ii}=0$ for a flat or convex surface, which cannot see itself, but $F_{ii}>0$ for a concave one, such as the inside of a sphere.

Radiation does not always take place inside an enclosure; there can be openings. An opening is treated as an imaginary surface spanning it, with radiation properties equivalent to the opening: radiation leaving through it never comes back, so it acts as a black surface at the temperature of whatever lies beyond (about 0 K for deep space, the ambient temperature for a window to the room). With that trick every problem becomes an enclosure and the summation rule applies.

For $N$ surfaces there are $N^2$ shape factors. The summation rule gives $N$ equations and reciprocity gives $N(N-1)/2$ more, so only $N(N-1)/2$ need to be found by integration or from charts, and fewer still when some are obvious ($F_{ii}=0$, $F=1$).

## 12. Worked example: two concentric spheres

*Determine the shape factors associated with an enclosure formed by two concentric spheres, sphere 1 of radius $r_1$ inside the inner face of sphere 2 of radius $r_2$.*

There are four shape factors: $F_{11}$, $F_{12}$, $F_{21}$ and $F_{22}$.

Sphere 1 is convex, so radiation leaving it cannot strike itself, $F_{11}=0$. The summation rule for surface 1 then gives all the rest of its radiation to surface 2:

$$
F_{11}+F_{12}=1\quad\Rightarrow\quad F_{12}=1 .
$$

Reciprocity gives $F_{21}$:

$$
A_1F_{12}=A_2F_{21}
\quad\Rightarrow\quad
F_{21}=\frac{A_1}{A_2}F_{12}=\frac{4\pi r_1^2}{4\pi r_2^2}\times1=\left(\frac{r_1}{r_2}\right)^2 .
$$

The summation rule for surface 2 gives the rest:

$$
F_{21}+F_{22}=1\quad\Rightarrow\quad F_{22}=1-F_{21}=1-\left(\frac{r_1}{r_2}\right)^2 .
$$

Most of what the outer sphere emits lands back on itself unless the inner sphere nearly fills it (panel (c) of the §9 figure). This is the sphere-in-an-enclosure case of §9: $F_{21}<1$ because the inner face of the enclosure sees itself. Radiation from the enclosure's outer face to the ambient is a separate surface with its own shape factors and does not enter $F_{21}$.

> [!check] Numbers (suggested, not lecturer-set)
> $r_1=0.1$ m, $r_2=0.2$ m: $F_{21}=0.25$, $F_{22}=0.75$. With both surfaces black, $T_1=600$ K and $T_2=300$ K, $\dot Q_{1-2}=A_1F_{12}\sigma(T_1^4-T_2^4)=4\pi(0.1)^2(5.67\times10^{-8})(600^4-300^4)=866$ W. From the other side, $A_2F_{21}=4\pi(0.2)^2(0.25)=0.1257$ m², the same as $A_1F_{12}$, so the result is identical ✓.

## 13. Worked example: steady temperature of the Earth

*Consider the radiative heat exchange between the Earth and the Sun. Find the surface temperature of the Earth at steady state. Assume that the Earth has no atmosphere and treat both the Sun and the Earth as black bodies.* Data: $R_S=6.9634\times10^8$ m, $d=1.49598\times10^{11}$ m (centre to centre), $T_S=5778$ K.

![[at_w09d_sun_earth.png|900]]

**Shape factor from Sun to Earth.** At a distance $d$ the Sun's radiation is spread uniformly over a sphere of area $4\pi d^2$ ($d\gg R_S$, so the Sun acts as a point source). From the Sun the Earth looks like a disk of area $\pi R_E^2$, so the fraction of the Sun's emission it intercepts is the fraction of that sphere it covers:

$$
F_{S\to E}=\frac{\text{Earth projected area}}{\text{sphere area at distance }d}=\frac{\pi R_E^2}{4\pi d^2}=\frac{R_E^2}{4d^2}.
$$

With $R_E=6.371\times10^6$ m this is $4.53\times10^{-10}$, the solid angle of §8 divided by $4\pi$.

**Power received.** The Sun's emissive power is $E_S=\sigma T_S^4$ and its total emission is

$$
\dot Q_S=\sigma T_S^4\times A_S=4\pi R_S^2\sigma T_S^4 .
$$

The Earth intercepts

$$
\dot Q_{S\to E}=\dot Q_S\times F_{S\to E}=4\pi R_S^2\sigma T_S^4\times\frac{R_E^2}{4d^2}=\sigma T_S^4\,\pi R_S^2\,\frac{R_E^2}{d^2}.
$$

**Power emitted.** The Earth is black and, in this model, at one uniform temperature $T_E$ (fast rotation and heat transport spread the heat round it), so it emits from its whole surface:

$$
\dot Q_E=\sigma T_E^4A_E=4\pi R_E^2\sigma T_E^4 .
$$

**Steady state.** Energy absorbed equals energy radiated:

$$
\sigma T_S^4\,\pi R_S^2\,\frac{R_E^2}{d^2}=4\pi R_E^2\,\sigma T_E^4 .
$$

$\sigma$, $\pi$ and $R_E^2$ cancel. The size of the Earth drops out, since both absorption and emission scale with its area:

$$
\boxed{T_E^4=\frac{T_S^4R_S^2}{4d^2}}
\quad\Rightarrow\quad
T_E=T_S\sqrt{\frac{R_S}{2d}} .
$$

**Numbers.**

$$
\frac{R_S}{2d}=\frac{6.9634\times10^8}{2\times1.49598\times10^{11}}=2.3274\times10^{-3},
\qquad
\sqrt{2.3274\times10^{-3}}=0.048243,
$$

$$
T_E=5778\times0.048243=278.75\ \text{K}=5.60\ ^\circ\text{C}.
$$

The temperature of the Sun itself comes from its spectrum: fitting Planck's law to the measured solar spectrum, or applying Wien's law to its peak, gives $T_S\approx5778$ K. The solar flux arriving at the Earth's distance is $\sigma T_S^4(R_S/d)^2=1369$ W/m², close to the measured solar constant of about 1361 W/m².

A mean surface temperature of 5.6 °C is too cold for the Earth as it is, because the model leaves out two things. First, the Earth reflects part of the sunlight (albedo $a\approx0.3$, from clouds, ice and oceans), so it absorbs only $(1-a)$ of the intercepted power. Second, it has an atmosphere. Making the Earth grey, with absorptivity $\alpha$ for sunlight and emissivity $\epsilon$ for its own infrared emission, the balance becomes

$$
\alpha\,\sigma T_S^4\,\pi R_S^2\,\frac{R_E^2}{d^2}=\epsilon\,4\pi R_E^2\sigma T_E^4
\quad\Rightarrow\quad
T_E=T_S\sqrt{\frac{R_S}{2d}}\left(\frac{\alpha}{\epsilon}\right)^{1/4}.
$$

If $\alpha=\epsilon$ (a truly grey Earth, Kirchhoff) the emissivity cancels and $T_E$ is still 278.75 K. What lowers it is that the Earth reflects sunlight (in the visible) more than its emission (in the infrared) is reduced: with $\alpha=1-a=0.70$ in the visible and $\epsilon\approx1$ in the infrared, $T_E=278.75\times0.70^{1/4}=254.97$ K $=-18.2$ °C, the −18 °C usually quoted for an airless Earth.

The real mean surface temperature is about 15 °C. The difference is the greenhouse effect. The atmosphere, with small amounts of greenhouse gases such as carbon dioxide and water vapour, absorbs about 23 % of the incoming solar radiation and transmits the rest, but it absorbs about 90 % of the infrared radiated back by the surface, and re-emits part of that downwards. Climate models with several atmospheric layers and their emissivities reproduce the 15 °C.

## Problem-solving workflow

1. Convert all temperatures to kelvin.
2. Decide the surface model for each surface: black ($\epsilon=1$), grey ($\epsilon<1$, $\alpha=\epsilon$), or an opening (black at the temperature beyond).
3. Find the shape factors: obvious ones first ($F_{ii}=0$ for flat or convex surfaces, $F=1$ for a surface wrapped by another), then reciprocity and the summation rule; projected area over sphere area for a small, distant receiver.
4. Write the energy balance: absorbed (or convected in) = emitted, with emission $\epsilon\sigma AT^4$ and net black exchange $A_1F_{12}\sigma(T_1^4-T_2^4)$.
5. Solve. A balance with convection and radiation is a quartic in $T$; use Newton's method ([[SESA3029 Example Sheet 3 - Solutions#Q4. Meteor stagnation-point heating|ES3 Q4]]).

## Terminology and alternative names

| Course term | Also called | Where the course uses it | Note |
|---|---|---|---|
| shape factor; radiation shape factor | view factor; configuration factor; angle factor | 5.6 slides 3–9 | slide 3 names "view factor" once |
| emissivity $\epsilon$ | emittance; emission coefficient | 5.5 slide 6; 5.6 slide 10 | SESA2024 uses "emittance" ([[Absorptance and Emittance]]) |
| absorptivity, reflectivity, transmissivity | absorptance, reflectance, transmittance | 5.5 slides 4–5 | the "-ance" forms are common for real, finite surfaces |
| blackbody | black body; ideal radiator; Planckian radiator | 5.5 slides 9–12 | |
| grey body | gray body (US) | 5.6 slide 10 | |
| spectral blackbody emissive power $E_{b,\lambda}$ | spectral emissive power; monochromatic emissive power | 5.5 slide 9 | spectral radiance $=E_{b,\lambda}/\pi$ per steradian (5.5 slide 7 axis) |
| total emissive power $E_b$ | blackbody emissive power; radiant exitance | 5.5 slide 12 | |
| monochromatic emissivity $\epsilon_\lambda$ | spectral emissivity | 5.6 slide 10 | |

## Links

- Parent: [[SESA3029 Aerothermodynamics Hub]]
- Previous: [[SESA3029 W09c - Critical Thickness of Insulation and Fins]] · Next: [[SESA3029 W09e - Numerical Methods in Conduction]] (the radiation boundary condition)
- New concepts: [[Kirchhoff's Law of Thermal Radiation]] · [[Planck's Law]] · [[Wien's Displacement Law]] · [[Stefan-Boltzmann Law]] · [[Emissivity]] · [[Solid Angle]] · [[Radiation Shape Factor]]
- Earlier years: [[Blackbody Radiation]] · [[Absorptance and Emittance]] · [[Spacecraft Thermal Balance Equation]] (SESA2024: the same laws applied to spacecraft thermal control)
- Block 5: [[SESA3029 W09a - Heat Conduction and Thermal Resistance]] · [[SESA3029 W09b - Convective Heat Transfer and the Reynolds Analogy]]
- Practice: [[SESA3029 Example Sheet 3 - Solutions#Q4. Meteor stagnation-point heating|ES3 Q4]] · lunar re-entry radiation in [[SESA3029 Past Paper 2014-15 - Solutions#(ii) Lunar re-entry shock layer and surface radiative equilibrium [6 marks]|2014–15 Q4(ii)]], [[SESA3029 Past Paper 2015-16 - Solutions#(iii) Lunar re-entry shock layer, radiation and surface thermal equilibrium [5 marks]|2015–16 Q4(iii)]] and [[SESA3029 Past Paper 2017-18 - Solutions#(ii) Lunar re-entry shock layer and radiative heating [6 marks]|2017–18 Q4(ii)]]

## Sources

- `Lecture5.5(1).pdf`: Lecture 5.5, 13 slides: thermal radiation and the electromagnetic spectrum (slides 2–3), reflection, absorption and transmission (4–5), Kirchhoff's law (6), radiation spectra and the failure of the classical theory (7–8), Planck's law (9), spectral blackbody emissive power and Wien's displacement law (10–11), total emissive power and the Stefan–Boltzmann law (12), applications of Planck's law (13). The spectra figures are credited to Çengel, *Heat Transfer: A Practical Approach*.
- `Lecture5.6(1).pdf`: Lecture 5.6, 15 slides: the Stefan–Boltzmann law recap (slide 2), shape factor (3–4), solid angle (5), reciprocity relation (6–7), summation rule (8), the concentric-sphere example (9), emissivity and grey bodies (10), the Earth–Sun example (11–15).
- Both decks are last year's files re-issued, with no lecturer named on them. The lectures are expected in late November and early December 2026. This note is written from the slides alone, with no transcript yet, and will be reconciled with the transcripts once the lectures have been given.
- Beyond the slides: the Rayleigh–Jeans and short-wavelength limits (§4), the Wien and Stefan–Boltzmann derivations (§§5–6, which the slides state without derivation), the radiation intensity and the shape-factor integral (§9), the grey-Earth and albedo extension (§13).
- Figures: `generate_aerothermo_w09de_figures.py` (`at_w09d_surface_and_kirchhoff.png`, `at_w09d_planck_spectra.png`, `at_w09d_wien_and_grey.png`, `at_w09d_solid_angle_geometry.png`, `at_w09d_enclosures.png`, `at_w09d_sun_earth.png`), all computed with the course constants $C_1$, $C_2$, $\sigma$ and 2897.8 μm K. The "real surface" curve in `at_w09d_wien_and_grey.png` is illustrative.
- Çengel and Ghajar, *Heat and Mass Transfer*, Ch. 12–13; Incropera et al., *Fundamentals of Heat and Mass Transfer*, Ch. 12–13.

## Self-study tasks

No transcript yet; the tasks below cite the slide where each example or question is set. Tasks marked so are suggested, not lecturer-set.

### Core

- [ ] **(5.6 slides 11–14)** Derive $T_E^4=T_S^4R_S^2/(4d^2)$ for a black, airless Earth and evaluate it. Answer 278.75 K $=5.60$ °C. → [[#13. Worked example: steady temperature of the Earth|§13]]
- [ ] **(5.6 slide 9)** Find $F_{11}$, $F_{12}$, $F_{21}$ and $F_{22}$ for two concentric spheres. Answer $0$, $1$, $(r_1/r_2)^2$, $1-(r_1/r_2)^2$. → [[#12. Worked example: two concentric spheres|§12]]
- [ ] **(5.6 slides 6–8)** Derive the reciprocity relation from the $T_1=T_2$ argument and state the summation rule. → [[#10. Reciprocity relation|§§10–11]]
- [ ] **(5.5 slides 10–12)** Show that the peak of Planck's law is at $\lambda T=2897.8$ μm K and that its integral is $\sigma T^4$ with $\sigma=\pi^4C_1/(15C_2^4)$. → [[#5. Wien's displacement law|§§5–6]]
- [ ] **(ES3 Q4)** Radiative-equilibrium temperature of a meteor's stagnation point, $h(T_0-T_s)=\epsilon\sigma T_s^4$. Answer 1919 K. → [[SESA3029 Example Sheet 3 - Solutions#Q4. Meteor stagnation-point heating|ES3 Q4]]

### Further practice

- [ ] **(5.5 slide 11)** Peak wavelengths of the Sun (5800 K) and of a 300 K surface, and the temperature that peaks at 9.72 μm. Answers 0.50 μm, 9.66 μm, 298 K. → [[#5. Wien's displacement law|§5]]
- [ ] **(5.5 slide 6)** Derive Kirchhoff's law $\alpha=\epsilon$ from a body in an isothermal enclosure, and say when the total values differ. → [[#3. Kirchhoff's law of thermal radiation|§3]]
- [ ] **(5.6 slide 14)** Explain why a grey Earth with $\alpha=\epsilon$ is no colder than a black one, and find $T_E$ for an albedo of 0.3. Answer −18.2 °C. → [[#13. Worked example: steady temperature of the Earth|§13]]
- [ ] **(5.5 slide 2)** Which is the fastest mode of heat transfer, and why? → [[#SESA3029 W09d - Thermal Radiation|introduction]]
- [ ] Past papers: lunar re-entry radiation, [[SESA3029 Past Paper 2014-15 - Solutions#(ii) Lunar re-entry shock layer and surface radiative equilibrium [6 marks]|2014–15 Q4(ii)]] and [[SESA3029 Past Paper 2017-18 - Solutions#(ii) Lunar re-entry shock layer and radiative heating [6 marks]|2017–18 Q4(ii)]].
- [ ] (suggested, not lecturer-set) Derive $F=a^2/(a^2+H^2)$ for an element facing a coaxial disk from the shape-factor integral. → [[#9. The shape factor|§9]]
- [ ] (suggested, not lecturer-set) Net exchange between concentric black spheres, $r_1=0.1$ m at 600 K and $r_2=0.2$ m at 300 K. Answer 866 W. → [[#12. Worked example: two concentric spheres|§12]]

## Transcript and slide slips

> [!warning] Units of $E_{b,\lambda}$ (5.5 slide 9)
> Where: [[#4. The blackbody and Planck's law]].
>
> The units are printed as $[\mathrm{W\,m^{-2}\,\mu m}]$. Spectral emissive power is per unit wavelength, $\mathrm{W\,m^{-2}\,\mu m^{-1}}$, which is also what the $C_1$ and $C_2$ units give and what the 5.5 slide 10 axis (W/m²·μm, meaning per μm) shows.

> [!warning] Visible range quoted two ways (5.5 slides 3 and 11)
> Where: [[#1. Thermal radiation and the electromagnetic spectrum]].
>
> Slide 3 gives visible light as 0.4–0.6 μm, slide 11 as 0.46–0.76 μm. The usual range, and the one on the slide 10 figure, is 0.40–0.76 μm.

> [!warning] Spectral radiance described as per volume (5.5 slide 7)
> Where: [[#1. Thermal radiation and the electromagnetic spectrum]].
>
> Slide 7 defines spectral radiance as "radiated energy per volume per solid angle". It is power per unit area per unit wavelength per steradian; the axis unit W sr⁻¹ m⁻³ combines m⁻² (area) with m⁻¹ (wavelength) and is not a volume.

> [!warning] Why the enclosure's shape factor is below 1 (5.6 slides 3–4)
> Where: [[#9. The shape factor]].
>
> The slides explain $F_{21}<1$ for the sphere in an enclosure by energy radiated from the enclosure into the ambient. The radiation to the ambient leaves the enclosure's outer face, which is a different surface. $F_{21}<1$ because the inner face sees itself: $F_{22}=1-A_1/A_2$ (§12).

> [!warning] 278.75 K is 5.60 °C (5.6 slide 14)
> Where: [[#13. Worked example: steady temperature of the Earth]].
>
> The slide converts $T_E=278.75$ K to 5.75 °C, which subtracts 273. With 273.15 it is 5.60 °C. The kelvin value is right.

> [!warning] Sun–Earth distance drawn to the Sun's surface (5.6 slides 11–15)
> Where: [[#13. Worked example: steady temperature of the Earth]].
>
> The sketch puts $d$ from the Sun's surface to the orbit, but the formula and the value $d=1.49598\times10^{11}$ m (one astronomical unit) are centre to centre. Measured from the surface the result would be 279.40 K, a 0.2 % change.

> [!warning] Smaller points
> Where: [[#7. Emissivity and grey bodies]] and [[#6. The Stefan–Boltzmann law]].
>
> 5.6 slide 10 says a grey body's emissivity is independent of wavelength and then names the "monochromatic emissivity $\epsilon_\lambda$"; for a grey body $\epsilon_\lambda$ is a constant equal to $\epsilon$. 5.6 slide 2 calls $\dot Q=\sigma AT^4$ the heat transfer rate due to radiation; it is the rate of emission, and the net rate subtracts what the surroundings send back. 5.5 slide 8 uses the older $h=6.6256\times10^{-34}$ J s (current value $6.62607\times10^{-34}$). 5.5 slide 11 places the human-body peak at 9.72 μm, which is the peak at 298 K; skin at about 306 K peaks nearer 9.5 μm.
