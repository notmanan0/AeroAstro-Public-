---
title: "SESA2024 10 - Thermal Control"
module: "SESA2024 Astronautics"
type: topic
stream: "Spacecraft Subsystems"
order: 10
tags: [sesa2024, thermal-control, radiation, thermal-balance]
aliases: ["Thermal control subsystem", "Chapter 10", "Spacecraft thermal balance"]
date: 2026-10-30
status: lectured
coverage: "Weeks 8–9 (2025-11-20, ll. 136–end; 2025-11-25, ll. 1–500)"
parent: ["[[SESA2024 Astronautics Hub]]"]
prerequisites: ["[[SESA2024 08 - Electrical Power Subsystem]]", "[[SESA2024 09 - Communications]]"]
next_topics: ["[[SESA2024 01 - Systems Engineering and Spacecraft Design]]", "[[SESA2024 04 - Orbital Energy and the Vis-Viva Equation]]"]
key_concepts: ["[[Blackbody Radiation]]", "[[Absorptance and Emittance]]", "[[Spacecraft Thermal Balance Equation]]", "[[Passive vs Active Thermal Control]]"]
tutorial_sheets: ["[[SESA2024 Workbook Ch10 - Thermal Control Solutions]]"]
sources: ["02 - Sources/Lectures/Chapter 10/2025 WEEK 8 - Chapter 10 - Thermal Control - Lecture slides - complete.pdf", "02 - Sources/Lectures/SESA2024 Lecture 2025-11-20.txt", "02 - Sources/Lectures/SESA2024 Lecture 2025-11-25.txt"]
---

# SESA2024 10 - Thermal Control

> [!abstract] Summary
> Spacecraft components only work reliably within temperature limits, often near room temperature, so the thermal subsystem has to hold them there in an environment where one side may face the Sun and the other deep space. In vacuum, radiation is the only significant way heat enters or leaves, so the spacecraft's temperature is set by a balance: absorbed sunlight, albedo and Earth infrared plus internal dissipation must equal the power radiated as $\varepsilon\sigma T^4$ from its surface. Because sunlight dominates, the ratio of solar absorptance to infrared emittance, $\alpha_S/\varepsilon$, largely sets the temperature, and choosing surface finishes is the first and cheapest means of control.

> [!summary]- Exam use: quick path
> - **Use it when:** you must find an equilibrium temperature in sunlight or eclipse, choose a finish for a temperature window, or discuss passive versus active control.
> - **Assumptions:** steady state (a snapshot of one point in the orbit); uniform temperature; Earth infrared absorbed with $\alpha_{IR}=\varepsilon$ (Kirchhoff, as spacecraft and Earth are both near 290 K); average albedo $a=0.34$; flux $Q_S\approx1350\text{–}1400\ \mathrm{W/m^2}$, $Q_E\approx240\ \mathrm{W/m^2}$.
> - **Method:** 1. Identify which inputs act (Sun? albedo? Earth? eclipse?). 2. Projected areas for each input; total radiating area for the output. 3. Height factor $F=[R_E/(R_E+h)]^2$, albedo factor $\cos\phi$. 4. $\varepsilon\sigma A_{surf}T^4=\alpha_SQ_SA_S+\alpha_SQ_SA_aaF\cos\phi+\varepsilon Q_EA_EF+P$. 5. Solve for $T$ and convert to °C.
> - **Common mistakes:** using projected area instead of total surface area for the emission; using $\alpha_S$ for the Earth infrared term instead of $\varepsilon$.
> - **Practise:** [[#A painted sphere in low Earth orbit]] · [[SESA2024 Workbook Ch10 - Thermal Control Solutions#Q7. Solar-array temperature profile at 18 000 km (= 2022/23 B2(i))|Workbook Q7]]

Most of what is built on Earth is designed for room temperature, and it fails if pushed far from it; Dr Sykulska-Lawrence's example was a television in a freezer (2025-11-20, ll. 151–200). On a spacecraft each item has its own window: batteries ideally just below room temperature, hydrazine between about +10 and +50 °C before it freezes or boils off, electronics between about −5 and +40 °C, with bearings and arrays having their own. Some payloads add demands of their own: infrared detectors work best cold (Planck's detectors ran at a few kelvin), and optical benches such as Hubble's must be held with small temperature gradients so that the optics stay aligned.

A spacecraft is surrounded by vacuum, which limits how it can exchange heat. Conduction moves heat between parts of the spacecraft, and the structure can be used as a deliberate heat path, but it cannot exchange heat with space. Convection needs a gas, and at 400 km the distance between molecules is of the order of kilometres. That leaves radiation. Sunlight, sunlight reflected by the Earth, and the Earth's own infrared glow pour in; the electronics add heat from inside; and the spacecraft radiates from all its surfaces according to its temperature. The temperature rises or falls until output equals input (ll. 201–325).

## 1. Absorption, reflection and transmission

Radiation of wavelength $\lambda$ and intensity $Q_i$ falling on a surface is partly absorbed, partly reflected and partly transmitted (ll. 326–370):

$$
Q_i=Q_a+Q_r+Q_t.
$$

Dividing by $Q_i$ defines the spectral absorptance, reflectance and transmittance:

$$
\alpha=\frac{Q_a}{Q_i},\quad\rho=\frac{Q_r}{Q_i},\quad\tau=\frac{Q_t}{Q_i},
\qquad
\alpha+\rho+\tau=1.
$$

Spacecraft surfaces are almost all opaque, so $\tau\approx0$ and $\alpha+\rho\approx1$.

A black body absorbs all radiation at every wavelength ($\alpha=1$, $\rho=0$) and emits the most possible at a given temperature (ll. 370–380). A grey body absorbs a constant fraction less than 1, independent of wavelength. Real surfaces have $\alpha$ that varies with wavelength, which is why they have colour: a blue bottle reflects blue and absorbs red and green; white paint reflects across the visible; gold reflects red and green and absorbs blue, so it looks yellow (ll. 376–400).

### Total solar absorptance

What matters is the absorption integrated over the spectrum of the source (ll. 401–430). For sunlight,

$$
\alpha_S=\frac{\int_0^\infty\alpha(\lambda)\,Q_{i,\lambda}\,d\lambda}{\int_0^\infty Q_{i,\lambda}\,d\lambda}.
$$

So $\alpha_S$ depends on both the material and the source. The Sun radiates almost as a black body at about 6000 K, and 97 % of its energy lies between 0.2 and 3.0 μm, so integrating over that band is a good approximation (2025-11-25, ll. 26–50).

> [!warning] Transcript slip (2025-11-20, l. 430)
> The Sun is said to approximate "a black body at 600 Kelvin". It is about 6000 K (5800 K for the effective temperature), as the 2025-11-25 recap says.

## 2. Emission

A black body's spectral emission is given by Planck's law, which depends only on temperature (2025-11-25, ll. 51–100). As the temperature rises, the emission grows and its peak moves to shorter wavelength, following Wien's displacement law:

$$
\lambda_{max}T=2898\ \mu\mathrm m\,\mathrm K.
$$

The Earth's emission peaks near 10 μm, so it radiates like a black body at about $2898/10\approx290$ K, room temperature, while the Sun's peak is in the visible. A spacecraft absorbs short-wavelength sunlight but emits long-wavelength infrared, which is why a surface's solar absorptance and its infrared emittance can be very different.

Integrating Planck's law over all wavelengths gives the Stefan–Boltzmann law for the total emission of a black body (ll. 101–150):

$$
Q_{BB}=\sigma T^4,\qquad\sigma=5.67\times10^{-8}\ \mathrm{W\,m^{-2}\,K^{-4}}.
$$

A real surface emits less. Its emittance is the ratio to a black body at the same temperature, always below 1:

$$
\varepsilon=\frac{Q}{Q_{BB}}
\quad\Longrightarrow\quad
Q=\varepsilon\sigma T^4.
$$

## 3. The spacecraft thermal balance equation

There are four inputs and one output (2025-11-20, ll. 250–325; 2025-11-25, ll. 151–330).

Direct sunlight, absorbed over the area projected towards the Sun $A_S$ (a cylinder side-on presents a rectangle):

$$
\dot Q_{sun}=\alpha_SQ_SA_S.
$$

Albedo, the sunlight reflected by the Earth, about 34 % on average but anything from bright cloud to dark forest. It is absorbed over the area facing the Earth $A_a$, scaled by the angle $\phi$ between the Earth–Sun line and the Earth–spacecraft line (1 over the subsolar point, falling to zero at the terminator), by a switch $\beta$ that is zero over the night side, and by a height factor $F$ that falls with distance from the Earth:

$$
\dot Q_{albedo}=\alpha_SQ_SA_a\,a\,F\cos\phi\,\beta.
$$

No height factor appears in the direct solar term because the spacecraft's distance from the Sun barely changes, whereas its distance from the Earth can change a great deal (2025-11-25, ll. 220–230). The course uses $F=[R_E/(R_E+h)]^2$, consistent with the inverse-square fall-off of the Earth's flux. The $\cos\phi$ and $\beta$ terms are approximations; Dr Sykulska-Lawrence admitted she "got quite bogged down" in specular and diffuse reflection before settling on them (ll. 226–235).

Earth infrared, about 240 W/m², absorbed over the area facing the Earth:

$$
\dot Q_{Earth}=\varepsilon Q_EA_EF.
$$

The absorptance here is for the Earth's infrared, not for sunlight. By Kirchhoff's law a surface's absorptance and emittance are equal at the same wavelength, and since the Earth (about 290 K) and the spacecraft (kept near 290 K) radiate in the same infrared band, the infrared absorptance can be replaced by the emittance $\varepsilon$ (ll. 251–290). That substitution turns out to matter in eclipse (§4).

Internal dissipation $P$ from electronics, batteries, payload and thruster firings depends entirely on the spacecraft, so it is simply given (ll. 290–300).

The output is the emission from the whole surface area, not a projected area:

$$
\dot Q_{out}=\varepsilon\sigma A_{surf}T^4.
$$

In equilibrium inputs equal output:

$$
\boxed{\alpha_SQ_SA_S+\alpha_SQ_SA_a\,a\,F\cos\phi\,\beta+\varepsilon Q_EA_EF+P=\varepsilon\sigma A_{surf}T^4}
$$

Divide by $\varepsilon\sigma A_{surf}$ to get the temperature:

$$
T^4=\frac{1}{\sigma A_{surf}}\left[\frac{\alpha_S}{\varepsilon}Q_S\left(A_S+A_a\,a\,F\cos\phi\,\beta\right)+Q_EA_EF+\frac{P}{\varepsilon}\right].
$$

A surface made of several finishes uses area-weighted values, for example $\alpha_S=0.9\alpha_{S1}+0.1\alpha_{S2}$ if the first finish covers 90 % of the area (2025-11-25, ll. 326–360). The equation is a static snapshot: the albedo, the angles and the projected areas all change continuously round the orbit, so in design it is evaluated at the hot and cold extremes.

## 4. What the equation tells you

Sunlight dominates the inputs whenever the spacecraft is lit, since $Q_EA_EF$ and $P$ are usually much smaller than $Q_SA_S$, so the temperature is governed by the ratio $\alpha_S/\varepsilon$ that multiplies it (ll. 376–420). A surface with high absorptance and low emittance (polished metal, black nickel) runs hot; one with low absorptance and high emittance (white paint, optical solar reflectors) runs cold. Choosing the finish is therefore a way of setting the temperature with no power and no moving parts.

![[ast_thermal_alpha_eps.png|760]]

In eclipse with no internal power, only the Earth infrared term is left:

$$
\varepsilon Q_EA_EF=\varepsilon\sigma A_{surf}T^4
\quad\Longrightarrow\quad
T=\left(\frac{Q_EA_EF}{\sigma A_{surf}}\right)^{1/4},
$$

and the emittance cancels: the eclipse temperature of an unpowered body does not depend on its finish (2024/25 A8). This is the reason for the Kirchhoff substitution.

Surface properties change over the mission: ultraviolet and atomic oxygen erode coatings and Kapton blankets, so $\alpha_S$ typically rises and the spacecraft runs warmer at end of life (ll. 420–430).

## 5. Passive and active control

The polar bear is the lecture's model of passive control (ll. 426–450): its fur is an excellent insulating blanket, while its dark nose and pads radiate heat away when it needs to cool. A spacecraft does the same. The first step is to cover most of it with insulating, non-radiating surfaces, chiefly multi-layer insulation (MLI), which is most of what you see on a spacecraft's exterior. Then radiating surfaces are sized large enough to keep equipment below its upper limits in the hot phases, and heaters sized to keep it above its lower limits in the cold phases (ll. 450–470).

| | Passive | Active |
|---|---|---|
| Means | coatings, MLI, radiators, heat paths through structure | fluid loops, pumped heat transport, louvres, controlled heaters |
| Power | none | needed |
| Moving parts | none | mechanisms (reliability) |
| Mass and cost | low | higher |
| Flexibility | fixed at design | adapts to large swings, high heat transfer rates |

Industry uses passive methods wherever it can, and every spacecraft has some; active control is added only where the environment swings too much or a component's tolerance is too tight (ll. 470–500). The thermal engineer is involved with almost every other subsystem, because every heat source and every tolerance is theirs to manage.

## Worked examples

### Earth's black-body temperature from Wien's law

The Earth's emission peaks at about 10 μm (2025-11-25, ll. 101–110):

$$
T=\frac{2898}{10}=290\ \mathrm K\approx17^\circ\mathrm C.
$$

### A painted sphere in low Earth orbit

*(Suggested, not lecturer-set: it puts numbers into the balance equation as derived in the lecture.)* A sphere of diameter 1 m at 500 km, directly over the subsolar point ($\phi=0$, $\beta=1$), dissipates $P=100$ W. Take $Q_S=1350$, $Q_E=240\ \mathrm{W/m^2}$, $a=0.34$. Every projected area is $\pi r^2=0.785\ \mathrm{m^2}$ and the surface area is $4\pi r^2=3.14\ \mathrm{m^2}$. The height factor is $F=(6378/6878)^2=0.860$.

For white paint ($\alpha_S=0.2$, $\varepsilon=0.9$):

$$
T^4=\frac{0.2\times1350\times0.785(1+0.34\times0.860)+0.9\times240\times0.785\times0.860+100}{0.9\times5.67\times10^{-8}\times3.14},
$$

which gives $T=239$ K, or −35 °C. With black paint ($\alpha_S=0.95$, $\varepsilon=0.9$) the same sphere reaches +40 °C. In eclipse, with only Earth infrared and the 100 W, both finishes give −75 °C, and with $P=0$ both give −99 °C, the finish-independent eclipse temperature of §4. All values computed in Python.

The workbook's solar-array problem (Workbook Ch10 Q7, the same as 2022/23 B2) does the full noon, terminator and midnight cases for a flat array at 18 000 km.

![[ast_array_temperature_profile.png|700]]

## Links

- Parent: [[SESA2024 Astronautics Hub]]
- Previous: [[SESA2024 09 - Communications]]
- Next: [[SESA2024 01 - Systems Engineering and Spacecraft Design#7. How the payload drives the design (Chapter 4)|Chapter 4, payload]] (end of the same lecture) and [[SESA2024 04 - Orbital Energy and the Vis-Viva Equation]] (next lecture)
- Concepts: [[Blackbody Radiation]] · [[Absorptance and Emittance]] · [[Spacecraft Thermal Balance Equation]] · [[Passive vs Active Thermal Control]]
- Workbook: [[SESA2024 Workbook Ch10 - Thermal Control Solutions]]
- Eclipse and the cold case: [[Eclipse Duration]]

## Sources

- `2025 WEEK 8 - Chapter 10 - Thermal Control - Lecture slides - complete.pdf` with transcripts `SESA2024 Lecture 2025-11-20.txt`, ll. 136–end, and `SESA2024 Lecture 2025-11-25.txt`, ll. 1–500 (Dr H. Sykulska-Lawrence)
- Fortescue, Stark and Swinerd, *Spacecraft Systems Engineering*, Ch. 11

## Self-study tasks

No numerical task was set in the thermal lectures; the workbook and past papers carry the calculations.

### Core

- [ ] Why thermal control is needed, and the inputs and outputs of the balance (Workbook Ch10 Q1, Q4). → [[#3. The spacecraft thermal balance equation]] · [[SESA2024 Workbook Ch10 - Thermal Control Solutions#Q4. Inputs and outputs|Workbook Q4]]
- [ ] Why the temperature depends on $\alpha_S/\varepsilon$ (Workbook Ch10 Q5). → [[#4. What the equation tells you]] · [[SESA2024 Workbook Ch10 - Thermal Control Solutions#Q5. Why the temperature depends on the ratio of absorptance to emittance|Workbook Q5]]
- [ ] Solar-array temperature at noon, terminator and midnight at 18 000 km (Workbook Ch10 Q7; 2022/23 B2(i)). → [[SESA2024 Workbook Ch10 - Thermal Control Solutions#Q7. Solar-array temperature profile at 18 000 km (= 2022/23 B2(i))|Workbook solution]]
- [ ] Show that an unpowered body's eclipse temperature does not depend on its emittance (2024/25 A8). → [[#4. What the equation tells you]] · [[SESA2024 2024-25 Exam Solutions#Section A|2024/25 A8]]

### Further practice

- [ ] Spectral absorptance and the emittance of a real surface (Workbook Ch10 Q2, Q3). → [[#1. Absorption, reflection and transmission]] · [[#2. Emission]]
- [ ] When is active control needed? (Workbook Ch10 Q6) → [[#5. Passive and active control]]
- [ ] Repeat the painted-sphere example for a polished aluminium finish and explain the result. → [[#A painted sphere in low Earth orbit]]
