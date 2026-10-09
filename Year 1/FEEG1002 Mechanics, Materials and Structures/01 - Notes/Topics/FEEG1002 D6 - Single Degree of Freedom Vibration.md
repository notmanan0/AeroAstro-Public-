---
title: "FEEG1002 D6 - Single Degree of Freedom Vibration"
module: "FEEG1002 Mechanics, Materials and Structures"
type: topic
stream: "Part D: Dynamics"
order: 6
tags: [feeg1002, dynamics, vibration, sdof, natural-frequency, damping, frf, resonance]
aliases: ["Dynamics Lecture 6", "SDOF vibration", "Mass-spring-damper", "Free vibration", "Forced vibration"]
date: 2026-09-25
status: complete
parent: ["[[FEEG1002 Mechanics, Materials and Structures Hub]]"]
prerequisites: ["[[FEEG1002 D1 - Linear Motion of Particles]]", "[[FEEG1002 D3 - Work, Energy and Power]]", "[[FEEG1002 A5 - Beam Deflection and Macaulay's Method]]"]
next_topics: ["[[FEEG1002 D7 - Kinematics of Rigid Bodies]]"]
key_concepts: ["[[Damping Ratio and Natural Frequency]]", "[[Equivalent Spring Stiffness]]", "[[Logarithmic Decrement]]", "[[Frequency Response Function]]", "[[Resonance]]"]
tutorial_sheets: ["[[FEEG1002 Dynamics Tutorial 6 - SDOF Free Vibration Solutions]]"]
sources: ["02 - Sources/Dynamics/Lectures/Lecture 06 - SDOF Vibration.pdf"]
---

# FEEG1002 D6 - Single Degree of Freedom Vibration

> [!abstract] Summary
> Vibration needs **stiffness**, which stores PE and provides the restoring force, and **mass**, which stores KE and carries the motion through equilibrium. **Damping** removes energy.
>
> A structure is modelled by lumped equivalents: a rigid mass on a massless spring $k$ with a viscous damper $c$. Measured from the **static equilibrium** position:
> $$m\ddot x + c\dot x + kx = f(t),\qquad \omega_n = \sqrt{k/m},\quad \zeta = \frac{c}{2\sqrt{km}},\quad \omega_d = \omega_n\sqrt{1-\zeta^2}$$
> - **Free vibration** happens only at the natural frequency and decays as $e^{-\zeta\omega_nt}$. The **log decrement** measures $\zeta$.
> - **Forced harmonic vibration** is described by the **FRF** $X/F = 1/(k - \omega^2m + j\omega c)$. It is stiffness-, damping- or mass-controlled below, near and above $\omega_n$.

## Key Concepts
- [[Damping Ratio and Natural Frequency]] · [[Equivalent Spring Stiffness]] · [[Logarithmic Decrement]] · [[Frequency Response Function]] · [[Resonance]]

---

## 1. The SDOF model (L6.1)
| Ingredient | Law | Units | Energy |
|---|---|---|---|
| Spring (massless) | $F = kx$ | N/m | $PE = \tfrac12kx^2$ |
| Mass (rigid) | $F = m\ddot x$ | kg = N s²/m | $KE = \tfrac12m\dot x^2$ |
| Viscous damper | $F = c\dot x$ | N s/m | dissipates |

- Real springs and dampers are non-linear (drag, Coulomb friction). The linear model is a convenient approximation for modest amplitudes.
- **Degrees of freedom**: the minimum number of variables needed to describe the motion. SDOF means one. The spring and damper act **in parallel**, sharing a displacement and each transmitting its own force.

**Equivalent springs** ([[Equivalent Spring Stiffness]]): the stiffness *where the mass sits*.

![[d_equivalent_springs.png|900]]

The cantilever result $k = 3EI/L^3$ is the standard tip deflection $\delta = PL^3/3EI$ from [[FEEG1002 A5 - Beam Deflection and Macaulay's Method]] turned upside down. Lecture 6 asks you to consider what deforms, and what must be assumed for SDOF, for a bungee jumper, a diver on a board, and an engine on rubber mounts.

## 2. Undamped free vibration (L6.2a)
**Static vs dynamic displacement.**
- Statically, $k\delta = mg$.
- Measuring $x$ from that equilibrium, $mg - k(\delta + x) = m\ddot x$ reduces to $m\ddot x + kx = 0$.
- So **leave weight out of the dynamic FBD**, and measure from static equilibrium. This works for a linear spring.

Try $x = \sin\omega t$ or $\cos\omega t$: $(-\omega^2m + k) = 0$. The only frequency of free vibration is

$$
\omega_n = \sqrt{\frac km}\ \text{rad/s},\qquad f_n = \frac1{2\pi}\sqrt{\frac km}\ \text{Hz},\qquad T_n = \frac1{f_n}
$$

With initial conditions $x(0) = x_0$ and $\dot x(0) = \dot x_0$:

$$
x(t) = x_0\cos\omega_nt + \frac{\dot x_0}{\omega_n}\sin\omega_nt,\qquad X = \sqrt{x_0^2 + (\dot x_0/\omega_n)^2}
$$

![[d_sdof_free_undamped.png|800]]

**Energy**: PE and KE swap back and forth at **twice** the vibration frequency, and their sum stays constant. PE peaks at the extremes; KE peaks at equilibrium. So $\tfrac12kX^2 = \tfrac12m\dot x_{max}^2$, giving $\dot x_{max} = \omega_nX$ (Tutorial 6 Q1).

**Static-deflection shortcut**: $k/m = g/\delta$, so

$$
f_n = \frac1{2\pi}\sqrt{\frac g\delta}
$$

> [!example] Lecture 6 worked examples
> - **Motorway sign**: it sags $\delta = 0.11$ m, so $f_n = \frac1{2\pi}\sqrt{9.81/0.11}$ = **1.5 Hz**.
>   - On the Moon it is the **same**: $\delta$ scales with $g$.
>   - A gust giving $\dot x_0 = 1$ m/s produces $x_{max} = \dot x_0/\omega_n$ = **0.106 m**.
> - **Speed camera** (25 kg on a 3 m hollow square steel post, 100/94 mm):
>   - $I = (0.1^4 - 0.094^4)/12 = 1.83\times10^{-6}$ m⁴;
>   - $k = 3EI/L^3$ = **42.7 kN/m**;
>   - $f_n$ = **6.58 Hz**.
>   - A pigeon's 50 N s impulse gives $\dot x_0 = J/m = 2$ m/s ([[FEEG1002 D4 - Linear Impulse and Momentum]]). The amplitude is $2/(2\pi\times6.58)$ = **48 mm**.

## 3. Damped free vibration (L6.2b)
For $m\ddot x + c\dot x + kx = 0$, try $x = e^{st}$. This gives the **characteristic equation** $ms^2 + cs + k = 0$:

$$
s = \frac{-c\pm\sqrt{c^2 - 4km}}{2m} = -\zeta\omega_n \pm j\omega_n\sqrt{1 - \zeta^2}
$$

- Critical damping: $c_{crit} = 2\sqrt{km}$. Damping ratio: $\zeta = c/c_{crit}$.

| $\zeta$ | Roots | Response |
|---|---|---|
| $<1$ underdamped | complex pair | oscillates at $\omega_d = \omega_n\sqrt{1-\zeta^2}$ inside an $e^{-\zeta\omega_nt}$ envelope |
| $=1$ critical | real, equal | fastest non-oscillatory return |
| $>1$ overdamped | real, distinct | slow creep back |

- The real part $\Re(s) = -\zeta\omega_n$ sets the decay; the imaginary part $\Im(s) = \omega_d$ sets the frequency.
- Most structures have $\zeta\ll1$, so $\omega_d\approx\omega_n$. Car suspension "bounce" is about $\zeta\approx0.3$.
- Negative damping, such as aeroelastic flutter in the lecture's glider video, makes the envelope **grow**.

![[d_damping_regimes.png|760]]

**Logarithmic decrement** ([[Logarithmic Decrement]]). Successive peaks are one damped period apart, so $x_1/x_2 = e^{\zeta\omega_nT_d}\approx e^{2\pi\zeta}$ and

$$
\Delta = \ln\frac{x_1}{x_2}\approx2\pi\zeta,\qquad \text{better over } n \text{ cycles: }\Delta = \frac1n\ln\frac{x_1}{x_{n+1}}
$$

It works for velocity or acceleration peaks as well as displacement.

> [!example] Speed camera ringing after the pigeon (L6)
> - The velocity decays from 2 m/s to 0.02 m/s in 3 s, which is $n = 6.58\times3 = 19.7$ cycles.
> - $\Delta = \ln(100)/19.7 = 0.234$, so **$\zeta\approx\Delta/2\pi = 0.0372$**.
>
> ![[d_log_decrement.png|840]]

## 4. Forced harmonic vibration (L6.3)
**Types of dynamic force**:

| Type | Character | Example |
|---|---|---|
| Harmonic | one frequency | unbalanced rotating machines |
| Periodic | a sum of harmonics | pistons |
| Transient | short | impacts |
| Random | broadband | turbulence, rough roads |

Harmonic forcing is enough to characterise the system.

- After switch-on, the transient at $\omega_n$ decays, leaving a **steady state** at the forcing frequency: $x = X\sin(\omega t + \phi)$.

**Phasors**: write $f = \Re(Fe^{j\omega t})$ and $x = \Re(Xe^{j\omega t})$. Substituting into the equation of motion gives the **frequency response function (receptance)**:

$$
\frac XF(\omega) = \frac1{k - \omega^2m + j\omega c}
$$

| Region | Approximation | Phase | Behaviour |
|---|---|---|---|
| $\omega\ll\omega_n$ | $X/F\approx1/k$ | 0° (in phase) | **stiffness controlled** |
| $\omega\approx\omega_n$ | $X/F\approx1/j\omega c$ | −90° (lagging) | **damping controlled** |
| $\omega\gg\omega_n$ | $X/F\approx-1/\omega^2m$ | −180° (antiphase) | **mass controlled** |

![[d_frf_magnitude_phase.png|800]]

- Plot magnitude on a log axis (almost always), phase on a **linear** axis (never logged), and frequency on either.
- The **resonance frequency** (peak of the forced response) is slightly **below** the **natural frequency** (a free-vibration property). They are different concepts with nearly equal values when damping is light.

> [!example] Speed camera in a 20 m/s wind (L6)
> - Vortex shedding at $f = US_t/d = 20(0.2)/0.1$ = **40 Hz**, far above $f_n = 6.58$ Hz, so the response is **mass controlled**: $|X/F|\approx1/\omega^2m$.
> - The fix is to **add mass** to the camera.
> - Adding damping to the post would only help near resonance ($U\approx3.3$ m/s).
> - Changing stiffness would only matter when $U\ll3.3$ m/s.
>
> ![[d_speed_camera_frf.png|740]]

**Rotating unbalance**: a mass $m_\varepsilon$ at eccentricity $\varepsilon$ spinning at $\omega$ loads the shaft with $f(t) = m_\varepsilon\varepsilon\omega^2e^{j\omega t}$. Here $m_\varepsilon\varepsilon$ (kg m) is the **unbalance**. Balancing (centre of mass on the axis) removes it: wheels, turbofans, washing machines. **Helicopter ground resonance** is blade bunching exciting the airframe rocking on its undercarriage.

## Year 2 bridge
This chapter is the physical foundation of the whole of SESA2027 Part A:
- $ms^2 + cs + k = 0$ is the **characteristic equation**. Its roots are the **poles** $-\zeta\omega_n\pm j\omega_d$ ([[Characteristic Equation and Eigenvalues]], [[Poles and Zeros]], [[Damping Ratio and Natural Frequency]]).
- The FRF is the transfer function $G(s) = 1/(ms^2 + cs + k)$ evaluated at $s = j\omega$ ([[Transfer Function]], [[Frequency Response Function]], [[Bode Plot]]; [[SESA2027 A4 - Laplace Transforms, Transfer Functions and Step Response]], [[SESA2027 A5 - Frequency Response and Bode Plots]]).
- Aircraft modes are damped SDOF-like oscillators: the short-period oscillation and the phugoid ([[SESA2027 A3 - Longitudinal Dynamic Modes - SPO and Phugoid]], [[Short Period Oscillation]], [[Phugoid Mode]]).
- An **accelerometer is an SDOF system**: it is designed so that the measured band sits in the stiffness-controlled region ([[Sensor Dynamic Models]], [[SESA2027 C2 - Sensor Characteristics, Dynamics and Design]]).
- The maths is [[MATH2048 ODE1 - Second-Order Linear ODEs with Constant Coefficients]], with the [[Auxiliary Equation]] and [[Resonance]].
- **Multi-DOF**: many masses give many natural frequencies and mode shapes ([[Natural Frequencies and Mode Shapes]]). SESA2029 computes them for a wing with finite elements ([[SESA2029 C4 - APDL Workflow - Shell Wing Static and Modal (SHELL181 and SHELL281)]]).
- **Structures**: the equivalent stiffnesses come from beam theory ([[SESA2028 S2 - Beam Deflection and Bending Design]]). Every vibration cycle is a stress cycle, so vibration feeds directly into fatigue lifing ([[SESA2028 M2 - Fatigue - Fracture Surfaces, Mechanisms and Lifing]]).

## Links
- Previous: [[FEEG1002 D5 - Angular Impulse and Momentum]] · Next: [[FEEG1002 D7 - Kinematics of Rigid Bodies]]
- Worked problems: [[FEEG1002 Dynamics Tutorial 6 - SDOF Free Vibration Solutions]]

## Sources
- Dynamics Lecture 6 (T. Waters): 6.1 the SDOF system and equivalent springs; 6.2 free vibration, undamped and damped; 6.3 forced vibration, FRFs and unbalance
