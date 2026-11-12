---
title: "FEEG1002 D6 - Single Degree of Freedom Vibration"
module: "FEEG1002 Mechanics, Materials and Structures"
type: topic
stream: "Part D: Dynamics"
order: 6
tags: [feeg1002, dynamics, vibration, sdof, natural-frequency, damping, frf, resonance]
aliases: ["Dynamics Lecture 6", "SDOF vibration", "Mass-spring-damper", "Free vibration", "Forced vibration"]
date: 2026-11-05
status: lectured
coverage: "Dynamics Lecture 6 (slides pp. 1-62) in full: the SDOF model and equivalent springs (6.1), undamped and damped free vibration with the logarithmic decrement (6.2), steady-state forced vibration, the frequency response function and out-of-balance forces (6.3), with the gantry sign, speed camera and vortex-shedding examples. Live lectures L13 (12 Mar 2025), L14 and L14b (13 Mar 2025, the same lecture to two groups), L15 (19 Mar 2025) and L16 (20 Mar 2025, wheel-hop example and quiz); pre-recorded S6-1 to S6-3b. Base excitation, transmissibility and isolation were not taught."
parent: ["[[FEEG1002 Mechanics, Materials and Structures Hub]]"]
prerequisites: ["[[FEEG1002 D1 - Linear Motion of Particles]]", "[[FEEG1002 D3 - Work, Energy and Power]]", "[[FEEG1002 A5 - Beam Deflection and Macaulay's Method]]"]
next_topics: ["[[FEEG1002 D7 - Kinematics of Rigid Bodies]]"]
key_concepts: ["[[Damping Ratio and Natural Frequency]]", "[[Equivalent Spring Stiffness]]", "[[Logarithmic Decrement]]", "[[Frequency Response Function]]", "[[Resonance]]"]
tutorial_sheets: ["[[FEEG1002 Dynamics Tutorial 6 - SDOF Free Vibration Solutions]]"]
sources: ["02 - Sources/Dynamics/Lectures/Lecture 06 - SDOF Vibration.pdf", "02 - Sources/Lectures/FEEG1002 Lecture 2025-03-12.txt", "02 - Sources/Lectures/FEEG1002 Lecture 2025-03-13 - Dynamics 14 - 13 March 2025 at 12 00.txt", "02 - Sources/Lectures/FEEG1002 Lecture 2025-03-13 - Dynamics 14b - 13 March 2025 at 14 00.txt", "02 - Sources/Lectures/FEEG1002 Lecture 2025-03-19.txt", "02 - Sources/Lectures/FEEG1002 Lecture 2025-03-20.txt", "02 - Sources/Lectures/FEEG1002 Lecture 2022-02-18 - Section 6-1.txt", "02 - Sources/Lectures/FEEG1002 Lecture 2022-02-18 - section 6-2a.txt", "02 - Sources/Lectures/FEEG1002 Lecture 2022-02-18 - Section 6-2b.txt", "02 - Sources/Lectures/FEEG1002 Lecture 2022-02-23.txt", "02 - Sources/Lectures/FEEG1002 Lecture 2022-02-24.txt", "02 - Sources/Dynamics/Tutorials/Tutorial Sheet 06 - SDOF Free Vibration.pdf"]
---

# FEEG1002 D6 - Single Degree of Freedom Vibration

> [!abstract] Summary
> A mass on a spring with a viscous damper, $m\ddot x+c\dot x+kx=f(t)$, is the simplest model of a vibrating structure. Disturbed and left alone, it oscillates at its natural frequency $\omega_n=\sqrt{k/m}$ if undamped, or at $\omega_d=\omega_n\sqrt{1-\zeta^2}$ inside a decaying envelope $e^{-\zeta\omega_nt}$ if the damping ratio $\zeta=c/2\sqrt{km}$ is below 1; the logarithmic decrement of successive peaks, $\Delta\approx2\pi\zeta$, measures the damping. Driven by a harmonic force, it settles to a steady response at the driving frequency given by the frequency response function $X/F=1/(k-\omega^2m+j\omega c)$, which is stiffness controlled well below $\omega_n$, damping controlled near it and mass controlled well above it.

> [!summary]- Exam use: quick path
> - **Use it when:** a structure or machine vibrates: find its natural frequency from a stiffness and a mass, its response to an initial displacement, velocity or impulse, its damping from a decaying record, or its steady response to a harmonic or out-of-balance force.
> - **Assumptions:** linear spring, linear viscous damper, rigid lumped mass, motion measured from static equilibrium; forced response at steady state only.
> - **Method:** 1. Identify the spring and find its equivalent stiffness ($3EI/L^3$, $EA/L$, series or parallel). 2. $\omega_n=\sqrt{k/m}$, $f_n=\omega_n/2\pi$. 3. Free response: apply $x_0$ and $\dot x_0$ (an impulse $J$ gives $\dot x_0=J/m$). 4. Damping: $\Delta=\frac1n\ln(x_1/x_{n+1})$, $\zeta\approx\Delta/2\pi$. 5. Forced: compare $\omega$ with $\omega_n$ and use $|X/F|\approx1/k$, $1/(\omega c)$ or $1/(\omega^2m)$.
> - **Common mistakes:** mixing $\omega$ (rad/s) and $f$ (Hz); calling the resonance frequency the natural frequency.
> - **Practise:** [[#Speed camera on a cantilever post]] · [[FEEG1002 Dynamics Tutorial 6 - SDOF Free Vibration Solutions]] (Q4 diving board)

A real structure such as a bridge, a car body or a speed-camera post has mass and stiffness spread throughout it and can vibrate in many patterns. Often one pattern dominates, and for that one the structure behaves like a single rigid mass on a single spring. When the mass is pushed and released, the spring pulls it back, it overshoots because of its inertia, and the cycle repeats, with energy passing back and forth between the spring (potential) and the mass (kinetic). Friction in the joints and the material slowly turns that energy into heat, so the oscillation dies away.

The stiff-and-light structure vibrates fast; the soft-and-heavy one slowly. The frequency at which a system vibrates freely is a property of the system alone, set by $k$ and $m$. When a force drives the system at some other frequency, the response depends on how the driving frequency compares with that natural frequency: driven slowly, the system just follows the spring law; driven fast, its inertia dominates and it barely moves; driven near its natural frequency, only the damping limits the motion. Much of vibration engineering is deciding which of those three regions a problem lies in.

---

## 1. The single degree of freedom model

### Stiffness, mass and damping

A **stiffness** element (spring) resists displacement. For a linear spring the force is proportional to the extension, $F=kx$, with $k$ the gradient of the force-displacement line in N/m, and the potential energy stored is

$$
V=\int_0^xkx\,dx=\tfrac12kx^2
$$

Real springs stiffen at large deflection, but the model treats them as linear.

A **mass** element resists acceleration, $F=m\ddot x$, and stores kinetic energy $KE=\tfrac12m\dot x^2$.

A **damper** resists velocity. The linear viscous damper (dashpot) gives $F=c\dot x$, with $c$ in N s/m. Unlike the other two, a damper stores no energy: it dissipates it. Shock absorbers are dampers, though their force is closer to velocity squared; in most structures the damping actually comes from friction in joints, which the viscous model approximates.

### Lumped-parameter models

A **lumped-parameter** model represents a structure by rigid masses, massless springs and massless dampers with equivalent (effective) values. The number of **degrees of freedom** is the minimum number of independent coordinates needed to describe the motion at any instant. A rigid body in space has six; the model here has one, the displacement $x$ of the mass.

In the standard SDOF model the spring and damper connect the mass to fixed ground and act **in parallel**: they share the same displacement and velocity but carry different forces. Elements **in series** share the same force but have different displacements. That is the test for which arrangement a real system is. (A spring and damper in series could carry no static load, since the damper would creep indefinitely.)

### Equivalent springs

The spring in a real system is usually a structural member, and its stiffness is the force per unit deflection at the point where the mass sits (slides pp. 10–11).

![[d_equivalent_springs.png|900]]

A rod loaded axially extends by $\delta=FL/EA$ (from $\sigma=E\varepsilon$ with $\sigma=F/A$ and $\varepsilon=\delta/L$), so

$$
k=\frac{F}{\delta}=\frac{EA}{L}
$$

A cantilever with a tip load deflects at the tip by $\delta=FL^3/3EI$ ([[FEEG1002 A5 - Beam Deflection and Macaulay's Method|A5]]), so

$$
k=\frac{3EI}{L^3}
$$

Likewise a block in shear has $k=GA/L$ and a shaft in torsion has torsional stiffness $k=GJ/L$ in N m/rad ([[FEEG1002 A8 - Torsion of Circular Shafts|A8]]). A helical coil spring of wire diameter $d$, coil diameter $D$ and $n$ turns has $K=Gd^4/8D^3n$, which depends on the shear modulus because the wire twists. An air spring of area $S$ and volume $V$ has $k=B_0S^2/V$. Other beam supports give other constants: a beam fixed at both ends and loaded at midspan has $k=192EI/L^3$, a simply supported one $48EI/L^3$.

Springs in parallel share the displacement $x$, so their forces add:

$$
F=k_1x+k_2x\quad\Rightarrow\quad k=k_1+k_2
$$

Springs in series carry the same force $F$, so their extensions add:

$$
x=\frac F{k_1}+\frac F{k_2}\quad\Rightarrow\quad\frac1k=\frac1{k_1}+\frac1{k_2}
$$

These rules are the opposite way round from resistors in an electrical circuit. A badly clamped post is a flexible clamp in series with the post, which lowers the overall stiffness and so the natural frequency.

## 2. Undamped free vibration

### Static and dynamic displacement

For a mass $m$ hanging on a spring, with displacements positive downwards (slide p. 15), at static equilibrium the spring is stretched by $\delta$:

$$
mg-k\delta=0
$$

Let $x(t)$ be the displacement from that equilibrium position. The spring's total extension is $x+\delta$, and Newton's law gives

$$
mg-k(x+\delta)=m\ddot x
$$

$$
mg-k\delta-kx=m\ddot x
$$

$$
m\ddot x+kx=0
$$

using $mg=k\delta$. The weight and the static spring force cancel exactly. So the dynamic displacement is measured from the static equilibrium position, static forces are left out of the dynamic FBD, and for a linear spring the vibration does not depend on $\delta$ at all. The term $m\ddot x$ is sometimes called the inertia force.

### Natural frequency

Try $x=\sin\omega t$ (or $\cos\omega t$) in $m\ddot x+kx=0$:

$$
-m\omega^2\sin\omega t+k\sin\omega t=0
$$

$$
(k-\omega^2m)\sin\omega t=0
$$

which holds for all $t$ only if $\omega^2=k/m$. The **natural frequency** is

$$
\boxed{\omega_n=\sqrt{\frac km}\ \ \mathrm{rad/s},\qquad f_n=\frac{1}{2\pi}\sqrt{\frac km}\ \ \mathrm{Hz}}
$$

the only frequency at which the system can vibrate freely. It is a property of the system. The **natural period** is $T_n=1/f_n=2\pi/\omega_n$. $\omega$ is always in rad/s and $f$ always in Hz.

### Response to initial conditions

Both $\cos\omega_nt$ and $\sin\omega_nt$ satisfy the equation, so the general solution is

$$
x(t)=A_1\cos\omega_nt+A_2\sin\omega_nt
$$

with velocity $\dot x=-A_1\omega_n\sin\omega_nt+A_2\omega_n\cos\omega_nt$. At $t=0$, $x(0)=x_0$ gives $A_1=x_0$, and $\dot x(0)=\dot x_0$ gives $A_2\omega_n=\dot x_0$:

$$
\boxed{x(t)=x_0\cos\omega_nt+\frac{\dot x_0}{\omega_n}\sin\omega_nt}
$$

An initial displacement gives a cosine response and an initial velocity a sine response of amplitude $\dot x_0/\omega_n$. A sudden impulse $J$ on a mass at rest is equivalent to an initial velocity, $\dot x_0=J/m$ (from [[FEEG1002 D4 - Linear Impulse and Momentum|D4]]).

![[d_sdof_free_undamped.png|900]]

### Energy

For a release from $x_0$ at rest, $x=x_0\cos\omega_nt$ and $\dot x=-x_0\omega_n\sin\omega_nt$. Then

$$
V=\tfrac12kx_0^2\cos^2\omega_nt=\tfrac14kx_0^2(1+\cos2\omega_nt)
$$

$$
KE=\tfrac12m\omega_n^2x_0^2\sin^2\omega_nt=\tfrac14kx_0^2(1-\cos2\omega_nt)
$$

using $m\omega_n^2=k$. Adding, $V+KE=\tfrac12kx_0^2$, constant: energy passes back and forth between spring and mass at twice the vibration frequency, with none lost.

## 3. Damped free vibration

### Equation of motion and characteristic equation

Add a viscous damper and take $x$ positive upwards from static equilibrium (slide p. 32). The spring force $kx$ opposes the displacement and the damper force $c\dot x$ opposes the velocity:

$$
-kx-c\dot x=m\ddot x
$$

$$
m\ddot x+c\dot x+kx=0
$$

The left-hand side holds the internal forces due to the motion; a right-hand side, when there is one, holds externally applied forces. Try $x=e^{st}$, so that $\dot x=se^{st}$ and $\ddot x=s^2e^{st}$:

$$
(ms^2+cs+k)e^{st}=0
$$

$$
ms^2+cs+k=0
$$

This is the **characteristic equation**, with roots

$$
s_{1,2}=\frac{-c\pm\sqrt{c^2-4km}}{2m}
$$

In general $s=\Re(s)+j\Im(s)$, so $e^{st}=e^{\Re(s)t}e^{j\Im(s)t}$: the first factor grows or decays exponentially and the second oscillates (by Euler's formula, $e^{j\theta}=\cos\theta+j\sin\theta$).

### Damping ratio and the three regimes

The nature of the roots depends on the sign of $c^2-4km$. The boundary value is the **critical damping**

$$
c_{crit}=2\sqrt{km}
$$

and the **damping ratio** is the non-dimensional

$$
\zeta=\frac{c}{c_{crit}}=\frac{c}{2\sqrt{km}}
$$

Since $c/2m=\zeta\cdot2\sqrt{km}/2m=\zeta\omega_n$ and $\sqrt{c^2-4km}/2m=\omega_n\sqrt{\zeta^2-1}$, the roots are

$$
s_{1,2}=-\zeta\omega_n\pm\omega_n\sqrt{\zeta^2-1}
$$

Dividing the equation of motion by $m$ gives the standard form $\ddot x+2\zeta\omega_n\dot x+\omega_n^2x=0$.

![[d_damping_regimes.png|900]]

**Underdamped**, $\zeta<1$ ($c<c_{crit}$). The roots are complex:

$$
s_{1,2}=-\zeta\omega_n\pm j\omega_n\sqrt{1-\zeta^2}=-\zeta\omega_n\pm j\omega_d
$$

where the **damped natural frequency** is

$$
\boxed{\omega_d=\omega_n\sqrt{1-\zeta^2}}
$$

Combining $e^{s_1t}$ and $e^{s_2t}$ into real functions with Euler's formula gives

$$
x(t)=e^{-\zeta\omega_nt}\left(A_1\cos\omega_dt+A_2\sin\omega_dt\right)
$$

an oscillation at $\omega_d$ inside the decaying envelope $e^{-\zeta\omega_nt}$. Free vibration (oscillation) happens only in this regime; in most practical structures $\zeta\ll1$, so $\omega_d$ is barely below $\omega_n$ (for small $\zeta$, $\omega_d\approx\omega_n(1-\tfrac12\zeta^2)$). The decay rate uses $\omega_n$, not $\omega_d$: $\Re(s)=-c/2m=-\zeta\omega_n$, the inverse of the decay time constant. A car's suspension has $\zeta\approx0.3$, up to about 0.5 for a sporty car; a slinky well under 1%.

**Critically damped**, $\zeta=1$. The roots are equal, $s_1=s_2=-\omega_n$. One solution is $e^{-\omega_nt}$; with a repeated root the second is $te^{-\omega_nt}$ (substituting $(A_1+A_2t)e^{-\omega_nt}$ into $\ddot x+2\omega_n\dot x+\omega_n^2x=0$ gives zero identically), so

$$
x(t)=(A_1+A_2t)\,e^{-\omega_nt}
$$

The system returns to rest without oscillating, as fast as any non-oscillating system can.

**Overdamped**, $\zeta>1$. The roots are real, distinct and negative, $s_{1,2}=-\omega_n(\zeta\mp\sqrt{\zeta^2-1})$, and

$$
x(t)=A_1e^{s_1t}+A_2e^{s_2t}
$$

a sluggish return to rest, slower than critical. The closed forms for the critically damped response follow from the characteristic roots in the same way as the underdamped one.

### Response to an initial displacement

For the underdamped system released from $x_0$ at rest: $x(0)=x_0$ gives $A_1=x_0$. Differentiating,

$$
\dot x=e^{-\zeta\omega_nt}\left[(A_2\omega_d-\zeta\omega_nA_1)\cos\omega_dt-(A_1\omega_d+\zeta\omega_nA_2)\sin\omega_dt\right]
$$

so $\dot x(0)=0$ gives $A_2\omega_d=\zeta\omega_nA_1$ and

$$
x(t)=x_0e^{-\zeta\omega_nt}\left(\cos\omega_dt+\frac{\zeta}{\sqrt{1-\zeta^2}}\sin\omega_dt\right)
$$

For light damping the sine term is small and $x\approx x_0e^{-\zeta\omega_nt}\cos\omega_dt$, which is the form on slide p. 38; the oscillation repeats every **damped period** $T_d=2\pi/\omega_d$.

### Logarithmic decrement

Successive peaks of an underdamped response are one damped period apart, and between them the bracket in $x(t)$ repeats exactly, so the ratio of any two successive peaks is set by the envelope alone:

$$
\frac{x_1}{x_2}=\frac{e^{-\zeta\omega_nt_1}}{e^{-\zeta\omega_n(t_1+T_d)}}=e^{\zeta\omega_nT_d}
$$

The **logarithmic decrement** is the natural log of this ratio:

$$
\Delta=\ln\frac{x_1}{x_2}=\zeta\omega_nT_d=\zeta\omega_n\frac{2\pi}{\omega_n\sqrt{1-\zeta^2}}=\frac{2\pi\zeta}{\sqrt{1-\zeta^2}}
$$

With light damping, $\omega_d\approx\omega_n$ and

$$
\boxed{\Delta\approx2\pi\zeta,\qquad\zeta\approx\frac{\Delta}{2\pi}}
$$

Measuring over $n$ cycles is more accurate. The logs of the successive ratios add:

$$
\ln\frac{x_1}{x_{n+1}}=\ln\left(\frac{x_1}{x_2}\cdot\frac{x_2}{x_3}\cdots\frac{x_n}{x_{n+1}}\right)=\sum_{i=1}^{n}\ln\frac{x_i}{x_{i+1}}=n\Delta
$$

$$
\boxed{\Delta=\frac1n\ln\frac{x_1}{x_{n+1}}}
$$

The same applies to velocity peaks. The velocity $\dot x$ found above is $e^{-\zeta\omega_nt}$ times a combination of $\cos\omega_dt$ and $\sin\omega_dt$, which repeats every $T_d$, so successive velocity peaks also fall by $e^{\zeta\omega_nT_d}$.

![[d_log_decrement.png|900]]

If $c$ were negative the envelope would grow instead of decay. Negative damping happens when energy is fed in by the motion itself, as in aeroelastic flutter of a wing; it is mentioned only qualitatively.

## 4. Forced vibration

### Dynamic forces and the steady state

Dynamic forces can be time-harmonic (rotating machines), periodic (a Fourier sum of harmonics), transient (impacts) or random (a rough road). Only time-harmonic forces are treated. When a harmonic force is switched on, the response at first contains both the driving frequency and the natural frequency; the natural-frequency part is a free vibration and decays, leaving the **steady state** at the driving frequency alone. The forced-vibration results below are for the steady state of a linear system.

For a single-input single-output system, a force $f(t)=F\sin\omega t$ produces $x(t)=X\sin(\omega t+\phi)$. The quantities of interest are the amplitude ratio $X/F$ and the phase $\phi$.

### Phasors and the FRF

A harmonic force can be written $f(t)=F\cos\omega t=\Re\left(Fe^{j\omega t}\right)$, a vector (phasor) of length $F$ rotating anticlockwise at $\omega$ whose projection on the real axis is the force. By convention the $\Re$ is dropped and the force written $Fe^{j\omega t}$. The response is then $x(t)=Xe^{j\omega t}$ with $X$ complex: its magnitude is the amplitude and its angle the phase. The **frequency response function** (FRF) is

$$
\frac XF(\omega),\qquad\left|\frac XF\right|=\frac{|X|}{|F|}\ \ (\mathrm{m/N}),\qquad\angle\frac XF=\angle X-\angle F
$$

Its real part is the component of response in phase with the force per unit force; its imaginary part is the component in quadrature (90° out of phase). The output need not be a displacement, but here it is.

### FRF of the SDOF system

Apply $Fe^{j\omega t}$ to the mass:

$$
m\ddot x+c\dot x+kx=Fe^{j\omega t}
$$

With $x=Xe^{j\omega t}$, $\dot x=j\omega Xe^{j\omega t}$ and $\ddot x=-\omega^2Xe^{j\omega t}$:

$$
(-\omega^2m+j\omega c+k)Xe^{j\omega t}=Fe^{j\omega t}
$$

$$
\boxed{\frac XF=\frac{1}{k-\omega^2m+j\omega c}}
$$

The FRF is complex only because of the damper. Its magnitude and phase follow from the modulus and argument of the denominator:

$$
\left|\frac XF\right|=\frac{1}{\sqrt{(k-\omega^2m)^2+(\omega c)^2}},\qquad\phi=-\arctan\frac{\omega c}{k-\omega^2m}
$$

with $\phi$ running from 0 through $-90°$ (at $\omega=\omega_n$) to $-180°$.

### Stiffness, damping and mass controlled regions

Which term in the denominator dominates depends on $\omega$ (slide p. 54):

| Range | Approximation | Region | Phase of $x$ relative to $f$ |
|---|---|---|---|
| $\omega\ll\omega_n$ | $X/F\approx1/k$ | stiffness controlled (Hooke's law) | in phase |
| $\omega\approx\omega_n$ | $X/F\approx1/(j\omega c)=-j/(\omega c)$ | damping controlled | 90° behind |
| $\omega\gg\omega_n$ | $X/F\approx-1/(\omega^2m)$ | mass controlled (Newton's law) | 180°, out of phase |

At $\omega=\omega_n$ exactly, $k-\omega_n^2m=0$ and $X/F=1/(j\omega_nc)$ is exact. Driving a mass on a spring by hand shows all three: slowly, it feels like just a spring; fast, it moves opposite to the hand. Set problems sit firmly in one region, so the approximate form is the one to use.

![[d_frf_magnitude_phase.png|900]]

The magnitude is plotted on a logarithmic axis, the phase on a linear one, and the frequency axis is often logarithmic too. On log axes, the stiffness lines $1/k$ are horizontal and the mass lines $1/(\omega^2m)$ slope down; the FRF follows the stiffness line at low frequency and the mass line at high frequency, and they cross at $\omega_n$. More damping lowers and broadens the peak and makes the phase change more gradual, but every curve passes through $-90°$ at $\omega_n$.

> [!warning] Natural frequency is not resonance frequency
> The **resonance frequency** is where $|X/F|$ is greatest; with light damping ($\zeta<1/\sqrt2$) it is slightly below the natural frequency, and it is not the damped natural frequency either. It is a property of the forced response. The natural frequency is a property of the free vibration. The two names are not interchangeable.

## 5. Out-of-balance forces

A rotating body of mass $m_\varepsilon$ whose centre of mass sits at eccentricity $\varepsilon$ from the axis of rotation moves its centre of mass on a circle of radius $\varepsilon$. At constant speed $\omega$ that needs a centripetal force $m_\varepsilon\varepsilon\omega^2$ ([[FEEG1002 D2 - Curvilinear Motion#Circular paths|D2]]) from the shaft, and the body pushes back on the shaft, and so on the machine, with an equal and opposite force rotating at $\omega$. Its component in any fixed direction is $m_\varepsilon\varepsilon\omega^2\cos(\omega t+\phi)$, written as the phasor

$$
f(t)=m_\varepsilon\varepsilon\omega^2e^{j\omega t}
$$

The **unbalance** $m_\varepsilon\varepsilon$ is in kg m. The force grows with the square of the speed and has the frequency of the rotation. A small mass added to (or missing from) an otherwise balanced rotor at radius $\varepsilon$ gives the same result with $m_\varepsilon$ the small mass, not the mass of the whole rotor. Car wheels, washing machines (which carry about 25 kg of concrete ballast to raise $m$ and so reduce the response) and helicopter rotors (ground resonance) all suffer from it.

---

## Worked examples

### Gantry sign

A sign on a motorway gantry deflects statically by 0.11 m under its own weight. Find its natural frequency, and the amplitude of vibration if a gust gives it an initial velocity of 1 m/s (slides pp. 21–25; L13, ll. 569–655).

The static deflection gives the stiffness, $k=mg/\delta$, so the mass cancels:

$$
\omega_n=\sqrt{\frac km}=\sqrt{\frac g\delta}=\sqrt{\frac{9.81}{0.11}}=9.44\ \mathrm{rad/s},\qquad f_n=\frac{9.44}{2\pi}=1.50\ \mathrm{Hz}
$$

From rest at equilibrium with $\dot x_0=1$ m/s,

$$
x_{max}=\frac{\dot x_0}{\omega_n}=\frac{1}{9.44}=0.106\ \mathrm m
$$

On the Moon the frequency would be the same: $g$ is smaller, but the static deflection is smaller in the same proportion, while $k$ and $m$ are unchanged (L13, ll. 600–641).

### Speed camera on a cantilever post

A 25 kg speed camera sits on top of a 3 m steel post of hollow square section, 100 mm outside and 94 mm inside, with $E=210$ GPa. Treating the post as a massless cantilever and the camera as a rigid mass, find the natural frequency, the amplitude if a bird strike delivers an impulse of 50 N s, the damping ratio if a free vibration's velocity falls from 2 m/s to 0.02 m/s in 3 s, and the response to vortex shedding in a 20 m/s wind (slides pp. 27–29, 44, 57; L14, ll. 10–183; L15, ll. 25–81, 484–534).

The second moment of area of the hollow square is

$$
I=\frac{0.1^4-0.094^4}{12}=1.827\times10^{-6}\ \mathrm{m^4}
$$

and the tip stiffness of the post is

$$
k=\frac{3EI}{L^3}=\frac{3\times210\times10^9\times1.827\times10^{-6}}{27}=42.6\ \mathrm{kN/m}
$$

$$
\omega_n=\sqrt{\frac{42\,632}{25}}=41.3\ \mathrm{rad/s},\qquad f_n=6.57\ \mathrm{Hz}
$$

The bird's impulse sets the camera moving from rest at $\dot x_0=J/m=50/25=2$ m/s, so the amplitude is

$$
\frac{\dot x_0}{\omega_n}=\frac{2}{41.3}=0.048\ \mathrm m
$$

For the damping, in 3 s the post completes $n=f_n\times3=19.7$ cycles, and the velocity peaks fall by a factor of 100:

$$
\Delta=\frac1n\ln\frac{x_1}{x_{n+1}}=\frac{\ln100}{19.7}=0.234
$$

$$
\zeta\approx\frac{\Delta}{2\pi}=0.037
$$

which is light damping, so the approximation is sound (the exact relation gives 0.0371).

Vortices shed from the 0.1 m post in a 20 m/s wind at the Strouhal frequency, with Strouhal number $St=0.2$:

$$
f=\frac{U\,St}{d}=\frac{20\times0.2}{0.1}=40\ \mathrm{Hz}
$$

six times $f_n$, so the response is mass controlled, $|X/F|\approx1/(\omega^2m)$. Making the camera heavier would reduce it; changing the damping would do almost nothing. Damping matters only near $U=f_nd/St=3.3$ m/s, and stiffness only well below that speed.

![[d_speed_camera_frf.png|900]]

### Wheel hop of a car

A car wheel is held by the tyre ($k=300$ kN/m) and the suspension spring ($k=30$ kN/m), with the body treated as fixed. The wheel has 20 g of unbalance at 0.2 m radius, and the suspension damping is $c=2000$ N s/m. Find the natural frequency, the road speed at which it is excited, and the response amplitude there (L16, ll. 66–223; the slide is not in the vault copy of the deck).

Both springs connect the wheel to ground (the road and the fixed body) and share its displacement, so they act in parallel: $k=300+30=330$ kN/m. The wheel mass is not recorded; the stated 12.9 Hz implies about 50 kg, used here:

$$
\omega_n=\sqrt{\frac{330\,000}{50}}=81.2\ \mathrm{rad/s},\qquad f_n=12.9\ \mathrm{Hz}\ (776\ \mathrm{rpm})
$$

The unbalance force has the frequency of the wheel's rotation, so it is resonant when the wheel turns 12.9 times a second; for a rolling diameter of about 0.59 m that is $12.9\times\pi\times0.59=24$ m/s, about 86 km/h. The force there is

$$
F=m_\varepsilon\varepsilon\omega_n^2=0.02\times0.2\times81.2^2=26.4\ \mathrm N
$$

and at $\omega=\omega_n$ the response is damping controlled, exactly:

$$
|X|=\frac{F}{\omega_nc}=\frac{26.4}{81.2\times2000}=0.16\ \mathrm{mm}
$$

Lowering the tyre pressure lowers $k$, $f_n$ and the speed at which the hop occurs.

### Quick FRF checks

The low-frequency asymptote of a measured FRF is $2\times10^{-6}$ m/N; the stiffness is $k=1/(2\times10^{-6})=500$ kN/m (L16, ll. 266–277). An out-of-balance force of 10 N at 1200 rpm becomes $10\times(3600/1200)^2=90$ N at 3600 rpm, at 60 Hz, since the force scales with $\omega^2$ (L16, ll. 317–335). Balls placed symmetrically on a spinning roulette wheel produce no net force: their unbalance vectors cancel (L16, ll. 336–356).

---

## Links

- Parent: [[FEEG1002 Mechanics, Materials and Structures Hub]] · Previous: [[FEEG1002 D5 - Angular Impulse and Momentum]] · Next: [[FEEG1002 D7 - Kinematics of Rigid Bodies]]
- Concepts: [[Damping Ratio and Natural Frequency]] · [[Equivalent Spring Stiffness]] · [[Logarithmic Decrement]] · [[Frequency Response Function]] · [[Resonance]]
- Worked sheet: [[FEEG1002 Dynamics Tutorial 6 - SDOF Free Vibration Solutions]] · Formula list: [[FEEG1002 Formula Sheet]]
- Background: [[FEEG1002 A5 - Beam Deflection and Macaulay's Method]] (beam stiffnesses) · [[MATH2048 ODE1 - Second-Order Linear ODEs with Constant Coefficients]] (the characteristic-equation method)
- Used again in: [[SESA2027 A4 - Laplace Transforms, Transfer Functions and Step Response]] (poles of $ms^2+cs+k$) · [[SESA2027 A5 - Frequency Response and Bode Plots]] · [[SESA2027 A3 - Longitudinal Dynamic Modes - SPO and Phugoid]] (aircraft modes as damped oscillators)

## Sources

- `Lecture 06 - SDOF Vibration.pdf`: slides pp. 1–62 (6.1 the SDOF system pp. 3–12, 6.2 free vibration pp. 14–45, 6.3 forced vibration pp. 47–62). The wheel-hop slide used in L16 is not in this copy.
- Transcript labels used in this note:
  - L13 = `FEEG1002 Lecture 2025-03-12.txt` (12 Mar 2025): SDOF model, equivalent springs, undamped vibration, gantry sign.
  - L14 = `FEEG1002 Lecture 2025-03-13 - Dynamics 14 - 13 March 2025 at 12 00.txt` and L14b = `...Dynamics 14b - 13 March 2025 at 14 00.txt` (13 Mar 2025, the same lecture to two groups): speed camera, damped vibration, log decrement.
  - L15 = `FEEG1002 Lecture 2025-03-19.txt` (19 Mar 2025): log-decrement example, forced vibration, FRF, vortex shedding, out-of-balance forces.
  - L16 = `FEEG1002 Lecture 2025-03-20.txt` (20 Mar 2025): unbalance applications, wheel hop, quiz.
  - S6-1 = `FEEG1002 Lecture 2022-02-18 - Section 6-1.txt`; S6-2a = `...section 6-2a.txt`; S6-2b = `...Section 6-2b.txt`; S6-3a = `FEEG1002 Lecture 2022-02-23.txt`; S6-3b = `FEEG1002 Lecture 2022-02-24.txt` (pre-recorded 2022 versions).
- `Tutorial Sheet 06 - SDOF Free Vibration.pdf`: Q6.1–Q6.5, worked in the tutorial note.

## Self-study tasks

### Core

- [ ] What happens statically if the spring and damper are in series? (slide p. 9; L13, ll. 199–200). → [[#Lumped-parameter models]]
- [ ] For a bungee jumper, a diver on a board and an engine on rubber blocks, identify the spring and the SDOF assumptions (slide p. 12; L13, ll. 327–331). → [[#Equivalent springs]]
- [ ] Gantry sign, including the Moon question (L13, ll. 569–655). Targets 1.50 Hz and 0.106 m. → [[#Gantry sign]]
- [ ] Speed camera: stiffness, natural frequency and bird-strike amplitude (L14, ll. 10–183). Targets 42.6 kN/m, 6.57 Hz, 0.048 m. → [[#Speed camera on a cantilever post]]
- [ ] Log-decrement example (L15, ll. 25–81). Target $\zeta=0.037$. → [[#Speed camera on a cantilever post]]
- [ ] Tutorial 6 Q6.1–Q6.5. → [[FEEG1002 Dynamics Tutorial 6 - SDOF Free Vibration Solutions]]
- [ ] L16 quiz: which systems the FRF applies to, $k$ from the asymptote, the mass-controlled region, the force at 3600 rpm (L16, ll. 238–356). → [[#Quick FRF checks]]

### Further practice

- [ ] Play with a masses-and-springs simulation and check $\omega_n=\sqrt{k/m}$ (S6-2a, ll. 111–115; L13, ll. 567–568). → [[#Natural frequency]]
- [ ] Derive the critically damped and overdamped responses to an initial displacement. → [[#Damping ratio and the three regimes]]
- [ ] Finish the wheel-hop example: the effect of tyre pressure (L16, l. 223). → [[#Wheel hop of a car]]

## Transcript and slide slips

> [!warning] Slide slips (Lecture 06 slides)
> Where: [[#Response to an initial displacement]] · [[#Logarithmic decrement]].
>
> Slide p. 38 gives $x=x_0e^{-\zeta\omega_nt}\cos\omega_dt$ for a release from rest; the exact response has an extra term $\frac{\zeta}{\sqrt{1-\zeta^2}}\sin\omega_dt$ ($0.204x_0$ in amplitude at $\zeta=0.2$), which is negligible only for light damping. Slide p. 40 omits $\zeta=\Delta/2\pi$ (given orally, L14, ll. 542–546). Slide p. 44's velocity plot runs from about 1 m/s to 0.01 m/s (the 2022 data) while its text says 2 m/s to 0.02 m/s. Slide p. 57 gives $f_n=6.57$ Hz and p. 28 gives 6.58 Hz, from rounding $k$ to 42.7 kN/m.

> [!warning] Unverified result (L16, l. 208)
> Where: [[#Wheel hop of a car]].
>
> The wheel-hop amplitude is given as "about 1.5 millimetres". With the data spoken in the same lecture ($F=26.4$ N, $\omega_n=81.2$ rad/s, $c=2000$ N s/m) the damping-controlled amplitude is 0.16 mm; 1.6 mm would need $c=200$ N s/m. The revised slide is not in the vault, so check it on Blackboard.

### Transcript slips (S6, L13–L16)

| Ref | Said | Correct |
|---|---|---|
| S6-1, l. 124 | stiffness depends on "one over the cubed root of the length" | $1/L^3$ |
| L13, ll. 163–164 | $c$ "has got units of newtons per metre" | N s/m |
| L13, ll. 252–254 | a simply supported beam "might be 192" | 192 is fixed-fixed; simply supported is 48 |
| L14, ll. 438–439 | $\omega_d$ expansion garbled | $\omega_d\approx\omega_n(1-\tfrac12\zeta^2)$ |
| L14b, ll. 390–392 | oscillation "doesn't happen if c is smaller" | it does happen when $c<c_{crit}$ |
| L14b, l. 531 | "compared with an underdamped system" | an undamped system |
| L15, l. 43 | velocity falls to "one tenth" | one hundredth |
| S6-3a, l. 259; L15, l. 526 | vortex resonance at "three and a half" / "about 3" m/s | 3.3 m/s |
| L16, l. 119 | wheel hop "about 30 hertz" | 12.9 Hz (l. 146) |
| L16, ll. 168, 175 | unbalance "400 millimetres from the axis", then radius 0.2 m | the 400 mm is a diameter |
| L16, l. 335 | "if you cube the speed" | triple the speed |
