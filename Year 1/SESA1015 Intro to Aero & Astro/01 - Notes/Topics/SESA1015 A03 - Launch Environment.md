---
title: "SESA1015 A03 - Launch Environment"
module: "SESA1015 Intro to Aero & Astro"
type: topic
stream: "Astronautics"
order: 15
tags:
  - sesa1015
  - astronautics
  - launch-environment
  - vibration
  - acoustics
  - loads
aliases: ["SESA1015 Astronautics 3", "Launch Loads"]
date: 2026-09-27
status: lectured
coverage: "Astronautics Part 2 (Environment), pp. 39–47: the launch environment as the main driver of spacecraft structural design; quasi-static acceleration (Ariane 5, Shuttle, Saturn; peak at stage burnout); dynamic acceleration (random vibration) and PSD envelopes; the acoustic environment (engine and aerodynamic noise, lift-off and transonic peaks, SPL spectra); effects on the spacecraft and ground testing"
parent: ["[[SESA1015 Intro to Aero & Astro Hub]]"]
prerequisites: ["[[SESA1015 A02 - Space Environment]]"]
next_topics: ["[[SESA1015 A04 - Rocket Equation and Launch Performance]]"]
key_concepts: ["[[Launch Environment Loads]]", "[[Random Vibration and Acceleration PSD]]", "[[Sound Pressure Level]]", "[[Decibels]]"]
tutorial_sheets: []
sources: ["02 - Sources/Astronautics/Astronautics - Part 2 - Environment.pdf"]
---

# SESA1015 A03 - Launch Environment

> [!abstract] Summary
> Launch lasts minutes but is usually the most severe environment a spacecraft meets, and it is the main input to its structural design. The payload feels the quasi-static load factor $n=(T-D)/(Mg_0)$, which climbs as propellant burns and peaks at stage burnout (about 4 g for Ariane 5, 3 g for the throttled Shuttle). On top of it sits broadband random vibration, specified as an acceleration power spectral density whose area gives the mean-square acceleration ($g_{RMS}\approx7$ g for the Ariane envelope), and an intense acoustic field, about 140 dB overall under the fairing, loudest at lift-off and in transonic flight. Each is specified as an envelope and checked by ground test.

> [!summary]- Exam use: quick path
> - **Use it when:** a question asks for the load on a payload or component during ascent, why the acceleration peaks at burnout, the RMS acceleration of a PSD envelope, an SPL in pascals or an overall level from band levels, or where in the ascent the loads are worst.
> - **Assumptions:** rigid launcher and payload for the quasi-static load (no structural amplification); PSD segments straight on log–log axes; acoustic bands uncorrelated; $p_{ref}=2\times10^{-5}$ Pa; $g_0=9.81$ m/s².
> - **Method:** 1. Quasi-static: $n=(T-D)/(Mg_0)$, interface force $F_i=n\,m_pg_0$; with constant thrust $n_{bo}=n_0M_0/M_{bo}$. 2. Random: for each segment $G=G_1(f/f_1)^m$, area $=\frac{G_1f_1}{m+1}[(f_2/f_1)^{m+1}-1]$; sum, square-root for $g_{RMS}$. 3. Acoustic: $p_{rms}=p_{ref}10^{L/20}$; overall level $10\log_{10}\sum10^{L_i/10}$. 4. Compare with the structure's strength and natural frequencies. 5. Say how it is tested.
> - **Common mistakes:** using $dV/dt$ instead of $dV/dt+g\sin\gamma$ (so a coasting payload is wrongly loaded by gravity); adding decibels arithmetically instead of adding mean-square pressures.
> - **Practise:** [[#Payload and component loads at Ariane 5 burnout]] · [[#Self-study tasks]]

On the pad a satellite carries 1 g, its own weight. Once the engines light, three kinds of load arrive together. The first is the steady push of the thrust, which grows relative to the vehicle's mass as propellant is used up, so the payload is pressed into its adapter harder and harder until the stage burns out. The second is vibration: engines, turbopumps and unsteady combustion shake the whole stack, and the shaking reaches the payload through the adapter across a broad band of frequencies. The third is sound. The exhaust of a large rocket is among the loudest noise sources made, and at lift-off it reflects off the pad; later, in transonic flight, turbulent flow over the fairing adds aerodynamic noise. Lightweight panels, solar arrays and antennas are driven directly by the pressure fluctuations.

None of these lasts long, but a spacecraft that is light enough to be worth launching is easily broken by them, and once in orbit its structure carries almost nothing (there is no weight in free fall, [[SESA1015 A02 - Space Environment#Microgravity|A02 §6]]). The structure is therefore sized for launch (p. 39). The launch vehicle's user manual gives the environments as envelopes, and the spacecraft is tested against them on the ground before it flies (p. 46).

---

## 1. Launch as the design case

The launch environment is usually the most severe a spacecraft experiences and is the main driver of its structural design (p. 39). It is one of the induced environments of [[SESA1015 A02 - Space Environment#1. Natural and induced environments|A02 §1]], along with fabrication, testing and transport. The environments it contains, and the way each is quantified, are (pp. 39–45):

| Environment | Source | How it is specified |
|---|---|---|
| quasi-static (static) acceleration | thrust and drag acting on the decreasing vehicle mass | load factor in $g_0$ against flight time |
| dynamic acceleration (random vibration) | machinery, combustion, structure excited by the acoustic field | acceleration PSD envelope in $g^2$/Hz against frequency |
| acoustic | engine noise, aerodynamic noise | sound pressure level in dB against frequency |

## 2. Quasi-static acceleration

![[astro_a03_payload_fbd.png|900]]

### What the payload feels

Take the launcher, total mass $M$, flying along its velocity vector at flight-path angle $\gamma$ above the horizontal, with thrust $T$ along the velocity and drag $D$ against it. Newton's second law along the flight path ([[Newton's Laws of Motion]]) gives

$$
M\frac{dV}{dt}=T-D-Mg\sin\gamma .
$$

The payload, mass $m_p$, is bolted to the launcher through an adapter and has the same acceleration. The force the adapter exerts on it is $F_i$, positive forwards. Its own equation of motion along the path is

$$
m_p\frac{dV}{dt}=F_i-m_pg\sin\gamma .
$$

Rearrange for the interface force:

$$
F_i=m_p\left(\frac{dV}{dt}+g\sin\gamma\right).
$$

Substitute $dV/dt$ from the vehicle equation:

$$
F_i=m_p\left(\frac{T-D-Mg\sin\gamma}{M}+g\sin\gamma\right)
$$

$$
=m_p\,\frac{T-D}{M}.
$$

The gravity terms cancel. The force on the payload depends only on the non-gravitational forces on the vehicle per unit vehicle mass, because gravity acts on every particle of the payload directly and needs no support from the adapter. Dividing by the payload's weight on the ground defines the **load factor**, the "static acceleration" in units of $g_0$ (pp. 40–41):

$$
n=\frac{F_i}{m_pg_0}=\frac{T-D}{Mg_0}.
$$

Every component in the payload sees the same $n$, so a component of mass $m$ needs a mounting that carries $nmg_0$. When the engines stop, $T=0$ and above the atmosphere $D=0$, so $n=0$: the payload is weightless in the coast, even though it is accelerating downwards at $g\sin\gamma$.

### Why the peak comes at burnout

With constant thrust $T$ and constant propellant mass flow $\dot m$, the vehicle mass falls linearly, $M(t)=M_0-\dot mt$. Neglecting drag, which is small by the time the vehicle is high and fast,

$$
n(t)=\frac{T}{g_0\,(M_0-\dot mt)} .
$$

The numerator is fixed and the denominator shrinks, so $n$ rises throughout the burn and is largest at burnout, when $M=M_{bo}$ (p. 39):

$$
n_{bo}=\frac{T}{M_{bo}g_0}=\frac{T}{M_0g_0}\cdot\frac{M_0}{M_{bo}}=n_0\,\frac{M_0}{M_{bo}},
$$

where $n_0=T/(M_0g_0)$ is the thrust-to-weight ratio at ignition. A stage that lifts off at $n_0=1.3$ with a burnout mass ratio $M_0/M_{bo}=3.5$ ends its burn at $n_{bo}=1.3\times3.5=4.55$. The mass ratio that the rocket equation wants large ([[SESA1015 A04 - Rocket Equation and Launch Performance]]) is the same ratio that drives the peak load up.

![[astro_a03_quasi_static_acceleration.png|900]]

Peak static accelerations are about 4 g for Ariane 5, 3 g for the Space Shuttle and 8 g for Saturn (p. 39; but see [[#Transcript and slide slips]]). The flight histories show the burnout pattern (pp. 40–41):

- Ariane 5: the load factor climbs to about 4.4 g at about 130 s as the solid boosters burn out, drops to about 0.6 g when they separate, climbs again to about 3.3 g as the core stage approaches burnout near 590 s, and falls to about 0.2 g for the low-thrust upper stage.
- Space Shuttle: the load rises to about 2.7 g at solid-booster burnout near 125 s, drops to about 0.9 g, then climbs again on the main engines until it reaches 3 g at about 450 s. From there the main engines are throttled back so that the load stays at 3 g until main-engine cutoff, about 510 s.

Holding $n$ constant at $n_{max}$ while the mass keeps falling needs

$$
T(t)=n_{max}\,M(t)\,g_0,
$$

so the thrust is reduced in proportion to the remaining mass. The Shuttle used this to protect its crew and its large, lightly built payloads. Throttling costs some performance, because the vehicle then spends longer climbing against gravity (the gravity loss of [[SESA1015 A04 - Rocket Equation and Launch Performance]]).

## 3. Dynamic acceleration: random vibration

On top of the quasi-static load the payload receives **dynamic acceleration**, also called oscillatory acceleration or random vibration (p. 42). It is generated by functioning machinery (turbopumps, valves), by combustion phenomena in the engines, and by the structure being excited by the acoustic field of §4. The motion is random: it has no single frequency and never repeats, so it is described statistically, by how its mean-square value is distributed over frequency.

### The power spectral density

The **acceleration power spectral density** (PSD) $G(f)$ is the mean-square acceleration per unit bandwidth around frequency $f$, in $g^2$/Hz. If the acceleration were passed through a narrow filter of width $\Delta f$ at $f$, the mean square of the output would be $G(f)\Delta f$. Adding all the bands gives the total mean square, and its square root is the RMS acceleration:

$$
\overline{a^2}=\int_{f_1}^{f_2}G(f)\,df,\qquad g_{RMS}=\sqrt{\int_{f_1}^{f_2}G(f)\,df}.
$$

The square root comes from the units: $G$ is in $g^2$/Hz, so its area is in $g^2$. The same RMS idea for a periodic signal is in [[RMS Value]].

Launch-vehicle PSDs are given as envelopes made of straight segments on log–log axes (p. 42). A straight segment from $(f_1,G_1)$ to $(f_2,G_2)$ is a power law

$$
G(f)=G_1\left(\frac{f}{f_1}\right)^m,\qquad m=\frac{\log_{10}(G_2/G_1)}{\log_{10}(f_2/f_1)} .
$$

Integrate it over the segment:

$$
\int_{f_1}^{f_2}G\,df=\frac{G_1}{f_1^m}\int_{f_1}^{f_2}f^m\,df
$$

$$
=\frac{G_1}{f_1^m}\cdot\frac{f_2^{m+1}-f_1^{m+1}}{m+1}
$$

$$
=\frac{G_1f_1}{m+1}\left[\left(\frac{f_2}{f_1}\right)^{m+1}-1\right]\qquad(m\neq-1).
$$

For $m=-1$ the integral of $1/f$ gives $G_1f_1\ln(f_2/f_1)$ instead. Envelope slopes are usually quoted in dB per octave. One octave doubles $f$, which multiplies $G$ by $2^m$, so

$$
\text{slope}=10\log_{10}(2^m)=3.01\,m\ \text{dB/octave};
$$

a rise of $+6$ dB/octave means $m\approx2$.

![[astro_a03_random_vibration_psd.png|900]]

The Ariane envelope (p. 42) has four corner points, $(24\ \text{Hz},\ 0.001)$, $(160,\ 0.04)$, $(700,\ 0.04)$ and $(2000,\ 0.012)$ in $g^2$/Hz:

| Segment | $m$ | dB/octave | Area ($g^2$) |
|---|---|---|---|
| 24 to 160 Hz | 1.94 | +5.8 | 2.17 |
| 160 to 700 Hz | 0 | 0 | 21.6 |
| 700 to 2000 Hz | $-1.15$ | $-3.5$ | 27.2 |
| total | | | 51.0 |

so $g_{RMS}=\sqrt{51.0}=7.1$ g. The Shuttle envelope, $(76,\ 0.004)$, $(130,\ 0.025)$, $(300,\ 0.025)$, $(850,\ 0.001)$, gives areas 0.67, 4.25 and 3.18 $g^2$, a total of 8.1 $g^2$ and $g_{RMS}=2.8$ g. Ariane's envelope is both higher and much wider, and more than half of its mean square lies above 700 Hz.

For random vibration with a Gaussian distribution, the instantaneous acceleration lies within $\pm3g_{RMS}$ for 99.7% of the time, so peaks of about $3\times7.1=21$ g occur on the Ariane envelope. These peaks last milliseconds and alternate in sign, so their effect on a structure depends on how it responds at those frequencies, not on the peak value alone.

A component with a natural frequency inside the plateau of the envelope responds at that frequency much more strongly than the input, by a factor set by its damping ([[FEEG1002 D6 - Single Degree of Freedom Vibration]], [[Resonance]]). Spacecraft and equipment are therefore designed so that their main natural frequencies avoid the most energetic part of the launch spectrum, and launcher user manuals set minimum stiffness requirements for that reason.

## 4. The acoustic environment

The intense acoustic field during launch is generated by engine noise, from the turbulent mixing of the exhaust jets with the surrounding air, and by aerodynamic noise, from turbulent flow and shock oscillations over the vehicle (p. 43). It is greatest at two moments: at launcher release, when the exhaust is close to the ground and reflects off the pad, and at transonic speed, when aerodynamic noise peaks. Flame trenches and water deluge systems at the pad (p. 44) reduce the reflected noise.

### Sound pressure level

An acoustic field is a fluctuating pressure $p(t)$ about the ambient value, measured by its RMS value. Because levels span many orders of magnitude, they are given as a **sound pressure level** in decibels ([[Decibels]], [[Sound Pressure Level]]):

$$
L_p=10\log_{10}\frac{p_{rms}^2}{p_{ref}^2}=20\log_{10}\frac{p_{rms}}{p_{ref}},\qquad p_{ref}=2\times10^{-5}\ \text{Pa}.
$$

The factor is 20 rather than 10 because power, the quantity a decibel compares, goes as pressure squared. Inverting,

$$
p_{rms}=p_{ref}\,10^{L_p/20}.
$$

So 120 dB is 20 Pa, 130 dB is 63 Pa and 140 dB is 200 Pa; every 20 dB is a factor of ten in pressure.

### Adding bands

Spectra are given as levels in frequency bands, usually octaves. The pressure fluctuations in different bands are uncorrelated, so their mean squares add, just as the PSD areas of §3 add:

$$
p_{rms,tot}^2=\sum_ip_{rms,i}^2 .
$$

Express each band in decibels, $p_{rms,i}^2=p_{ref}^2\,10^{L_i/10}$, and substitute:

$$
p_{rms,tot}^2=p_{ref}^2\sum_i10^{L_i/10}.
$$

Take $10\log_{10}$ of $p_{rms,tot}^2/p_{ref}^2$:

$$
\text{OASPL}=10\log_{10}\sum_i10^{L_i/10}.
$$

This is the **overall sound pressure level**. Two equal bands give $10\log_{10}2=3$ dB more than one, not double the decibels.

![[astro_a03_acoustic_spectrum.png|900]]

The Ariane under-fairing spectrum (p. 43) in octave bands from 31.5 Hz to 8 kHz is 114, 127, 132, 136, 137, 134, 128, 122 and 120 dB. The sum gives an OASPL of 141.6 dB, an RMS pressure of $2\times10^{-5}\times10^{141.6/20}=241$ Pa, dominated by the bands from 125 Hz to 1 kHz. The Shuttle payload-bay curves peak at about 129 dB near 200 Hz at lift-off and about 125 dB near 400 Hz for aerodynamic noise, with the reference level stated as 0 dB $=2\times10^{-5}$ Pa.

A surface of area $A$ exposed to $p_{rms}$ carries a fluctuating force of about $p_{rms}A$ if the pressure is in phase across it. A 2 m² solar-array panel in the 137 dB band ($p_{rms}=142$ Pa) carries about 283 N RMS; if the panel has a mass of 10 kg, that force alone would give it $283/(10\times9.81)=2.9$ g RMS. The ratio of area to mass decides the response, so large, light structures (solar arrays, antenna reflectors, thin panels) are the ones that acoustics damage, while compact, dense boxes are loaded mainly through their mountings by the random vibration of §3.

### Why aerodynamic noise peaks near transonic speed

Aerodynamic noise and loads scale with the dynamic pressure $q=\tfrac12\rho V^2$. During ascent $V$ rises while $\rho$ falls, so $q$ passes through a maximum, **max-q**. A simple model locates it: a vertical climb from rest at constant acceleration $a$ through an exponential atmosphere $\rho=\rho_0e^{-h/H}$ (the form of [[Exponential Atmosphere and Scale Height]], with $H\approx7.2$ km in the lower atmosphere). Constant acceleration from rest gives

$$
V^2=2ah .
$$

Substitute into $q$:

$$
q=\tfrac12\rho_0e^{-h/H}\cdot2ah=\rho_0a\,h\,e^{-h/H}.
$$

Differentiate with respect to $h$:

$$
\frac{dq}{dh}=\rho_0a\,e^{-h/H}\left(1-\frac{h}{H}\right).
$$

This is zero at $h=H$, where

$$
q_{max}=\frac{\rho_0aH}{e},\qquad V_{max\text{-}q}=\sqrt{2aH}.
$$

![[astro_a03_max_q.png|900]]

With $a=5$ m/s² and $H=7.2$ km, max-q comes at 7.2 km with $V=\sqrt{2\times5\times7200}=268$ m/s and $q=1.225\times5\times7200/e=16.2$ kPa. The speed of sound at 7.2 km in the standard atmosphere is about 311 m/s, so the vehicle is at Mach 0.86: max-q falls in the transonic range, which is why the aerodynamic part of the acoustic and buffet load peaks there. Real launchers reach max-q at roughly 10 to 15 km, because their acceleration grows during the climb and the trajectory pitches over, but the conclusion that max-q comes about one scale height up and near Mach 1 holds.

## 5. Effects on the spacecraft and ground testing

The launch environment is the main input to the structural design of the spacecraft, and ground testing is used to make sure the spacecraft survives it (p. 46). The quasi-static load factors size the primary structure and the adapter; the random-vibration envelope sizes equipment mountings and sets stiffness targets; the acoustic spectrum sizes large panels and appendages. Tests reproduce each environment: a shaker table drives the spacecraft through its adapter with sine and random vibration; an acoustic chamber, a reverberant room with loudspeakers or horns, surrounds it with the specified spectrum; and static or centrifuge tests apply the quasi-static loads. Qualification tests on a test model use levels above the expected flight envelope to demonstrate margin, and lower acceptance tests on the flight model screen it for workmanship faults without using up its life.

Pyrotechnic release devices at stage and fairing separation produce short, high-frequency shocks, and the pressure inside the fairing drops from one atmosphere to near vacuum within a couple of minutes, so closed volumes in the spacecraft must be vented. The launcher's choice also fixes the mass, volume and centre-of-mass constraints treated in [[Launch Vehicle Interfaces]] and [[SESA1015 A06 - Launch Vehicles, Systems and Interfaces]].

## Worked examples

### Payload and component loads at Ariane 5 burnout

A 3000 kg satellite rides Ariane 5 through solid-booster burnout, where the load factor peaks at about 4.4 g (p. 40). The axial force through the adapter is

$$
F_i=n\,m_pg_0=4.4\times3000\times9.81=1.29\times10^5\ \text{N}=129\ \text{kN}.
$$

A 5 kg electronics box inside it needs brackets that carry $4.4\times5\times9.81=216$ N axially, before any factor of safety and before the dynamic loads of §3 are added. At core-stage burnout (about 3.3 g) the force is $3.3/4.4=75\%$ of the booster peak.

> [!check] Numerical check
> On the pad $n=1$ and the adapter carries $3000\times9.81=29.4$ kN, the satellite's weight. The ratio $129/29.4=4.4$ recovers the load factor.

### Burnout load factor and throttling

A stage lifts off at $n_0=1.5$ and burns propellant at a constant rate, $M(t)=M_0(1-0.72\,t/t_b)$, so its burnout mass is $0.28M_0$ and $M_0/M_{bo}=3.57$. At full thrust,

$$
n_{bo}=1.5\times3.57=5.36 .
$$

To cap the load at 3 g, throttling must start when $n_0M_0/M=3$, that is when $M=M_0/2$:

$$
1-0.72\,\frac{t}{t_b}=\frac12\quad\Rightarrow\quad\frac{t}{t_b}=\frac{0.5}{0.72}=0.69,
$$

the knee in the right-hand panel of the quasi-static figure. At that moment $T=3\times\tfrac12M_0g_0=1.5M_0g_0$, the full thrust, as it must be. From there the thrust follows $T=3M(t)g_0$ and ends at $3\times0.28M_0g_0=0.84M_0g_0$, which is $0.84/1.5=56\%$ of full thrust.

### RMS acceleration of the Ariane random-vibration envelope

The table in §3 gives the areas of the three segments: 2.17, 21.6 and 27.2 $g^2$. As a check on the first, $m=\log_{10}(0.04/0.001)/\log_{10}(160/24)=1.602/0.824=1.944$. Since $G_2/G_1=(f_2/f_1)^m$, the bracket simplifies: $(f_2/f_1)^{m+1}=(G_2/G_1)(f_2/f_1)=40\times6.667=266.7$. Then

$$
\frac{0.001\times24}{2.944}\left(266.7-1\right)=0.008152\times265.7=2.17\ g^2 .
$$

The flat segment is a rectangle, $0.04\times(700-160)=21.6\ g^2$.

The total is 51.0 $g^2$, $g_{RMS}=7.1$ g and the $3\sigma$ peak is 21 g.

### Overall level from octave bands

Two bands of 136 and 137 dB combine to $10\log_{10}(10^{13.6}+10^{13.7})=139.5$ dB. All nine Ariane bands give

$$
\text{OASPL}=10\log_{10}\sum_i10^{L_i/10}=141.6\ \text{dB},\qquad p_{rms}=241\ \text{Pa},
$$

about $2.4\times10^{-3}$ of an atmosphere, fluctuating hundreds of times a second over the whole fairing.

## Links

- Parent: [[SESA1015 Intro to Aero & Astro Hub]] · Previous: [[SESA1015 A02 - Space Environment]] · Next: [[SESA1015 A04 - Rocket Equation and Launch Performance]]
- Astronautics stream: [[SESA1015 A05 - Staging and Payload Fraction]] · [[SESA1015 A06 - Launch Vehicles, Systems and Interfaces]]
- Concepts: [[Launch Environment Loads]] · [[Random Vibration and Acceleration PSD]] · [[Sound Pressure Level]] · [[Decibels]] · [[Launch Vehicle Interfaces]] · [[Exponential Atmosphere and Scale Height]] · [[RMS Value]]
- Builds on: [[Newton's Laws of Motion]] · [[FEEG1002 D6 - Single Degree of Freedom Vibration]] · [[Resonance]]
- Later in the degree: [[SESA2028 Aerospace Materials & Structures Hub]] for structural sizing and margins; [[Natural Frequencies and Mode Shapes]] (SESA2029) and [[Damping Ratio and Natural Frequency]] (SESA2027) for structural response; [[SESA2024 01 - Systems Engineering and Spacecraft Design]] for the test and verification programme.

## Sources

- SESA1015 Astronautics Part 2, Environment (Dr S.J.I. Walker), pp. 39–47: launch environment p. 39; Ariane 5 and Shuttle static acceleration pp. 40–41; dynamic acceleration and PSD envelopes p. 42; acoustic environment pp. 43–45; effects on the spacecraft p. 46; summary p. 47. Part 3 (Launch Vehicles) has no further launch-load material.
- The PSD corner points and octave-band levels are read by eye from the graphs on pp. 42–43, so the derived $g_{RMS}$ and OASPL are approximate. The load-factor derivation, the burnout and throttling relations, the segment-integration formula, the band-addition rule and the max-q model are worked from these data.
- Shock, fairing depressurisation and the qualification/acceptance distinction in §5 are added context, not quantified on the slides.
- All numbers were recomputed in Python; figures from `01 - Notes/Figures/generate_astro_a03_figures.py`.

## Self-study tasks

No exercises are set for the launch environment (Part 2, pp. 39–47). Suggested, not lecturer-set:

### Core

- [ ] Derive $n=(T-D)/(Mg_0)$ from free-body diagrams of the launcher and the payload, and explain why the payload is weightless in a coast. Then find the adapter force on a 3000 kg payload at 4.4 g. → [[#What the payload feels]] · [[#Payload and component loads at Ariane 5 burnout]]
- [ ] Integrate the Ariane PSD envelope segment by segment to find $g_{RMS}$. → [[#The power spectral density]] · [[#RMS acceleration of the Ariane random-vibration envelope]]

### Further practice

- [ ] Convert the Ariane octave-band levels to pressures and combine them into an overall level; then show that max-q occurs at $h=H$ for a constant-acceleration vertical climb. → [[#Overall level from octave bands]] · [[#Why aerodynamic noise peaks near transonic speed]]

## Transcript and slide slips

> [!warning] Slide slip (Part 2, p. 39), probable
> Where: [[#Why the peak comes at burnout]].
>
> The peak static acceleration for Saturn is given as "≈ 8 g0". For the Saturn V, the burnout relation gives about 4 g at first-stage cutoff: with lift-off thrust about 34 MN, lift-off mass about $2.97\times10^6$ kg and about $2.1\times10^6$ kg of first-stage propellant, $n_{bo}\approx34\times10^6/(0.87\times10^6\times9.81)\approx4.0$, and Apollo flights recorded a peak of about 4 g, with the centre engine shut down early to limit it. The 8 g figure does not match the Saturn V; treat 4 g as the Saturn V value unless a different Saturn vehicle is meant.
