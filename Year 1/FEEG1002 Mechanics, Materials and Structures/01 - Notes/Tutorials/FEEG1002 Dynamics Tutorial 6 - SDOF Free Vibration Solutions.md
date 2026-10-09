---
title: "FEEG1002 Dynamics Tutorial 6 - SDOF Free Vibration Solutions"
module: "FEEG1002 Mechanics, Materials and Structures"
type: tutorial
stream: "Part D: Dynamics"
tags: [feeg1002, tutorial-solutions, dynamics, vibration, natural-frequency, damping, log-decrement]
sheet: "Problem sheet 6 - SDOF free vibration (2024-25)"
theory_notes: ["[[FEEG1002 D6 - Single Degree of Freedom Vibration]]"]
key_concepts: ["[[Damping Ratio and Natural Frequency]]", "[[Equivalent Spring Stiffness]]", "[[Logarithmic Decrement]]"]
status: complete
sources: ["02 - Sources/Dynamics/Tutorials/Tutorial Sheet 06 - SDOF Free Vibration.pdf"]
---

# FEEG1002 Dynamics Tutorial 6 - SDOF Free Vibration Solutions

> [!abstract] Sheet Info
> Five problems on the free vibration of lumped SDOF systems. Every printed answer is reproduced ✔.
> - The recurring skill is finding the **equivalent stiffness** from beam theory, then $\omega_n = \sqrt{k/m}$.
> - Q4(iii) asks for scaling arguments, given here.

## Theory Links
- [[FEEG1002 D6 - Single Degree of Freedom Vibration]] · [[Equivalent Spring Stiffness]] · [[Damping Ratio and Natural Frequency]] · [[Logarithmic Decrement]] · [[Standard Beam Deflections]]

---

## 6.1: 0.3 kg on 1000 N/m, pulled 0.1 m beyond equilibrium and released
- Measure from static equilibrium, so the weight drops out.
- The amplitude is $X = 0.1$ m and $\omega_n = \sqrt{1000/0.3} = 57.7$ rad/s.
- At equilibrium all the energy is kinetic: $\tfrac12kX^2 = \tfrac12m\dot x^2$, so $\dot x = \omega_nX$ = **5.77 m/s** ✔

## 6.2: 10 kg wind turbine on a 5 m steel pole ($R_o = 40$ mm, $t = 2$ mm, $E = 210$ GPa)
- (i) $I = \tfrac\pi4(0.040^4 - 0.038^4) = 3.73\times10^{-7}$ m⁴. The pole is a cantilever with the load at its tip, so $k = 3EI/L^3$ = **1880 N/m** ✔
- (ii) $f_n = \frac1{2\pi}\sqrt{1880/10}$ = **2.18 Hz** ✔
- (iii) $f_n\propto\sqrt k\propto L^{-3/2}$. Doubling $f_n$ needs $k\times4$, so $L\times4^{-1/3}$: **$L = 3.15$ m** ✔

The thin-walled approximation $I\approx\pi R_m^3t$, with the mean radius $R_m = 39$ mm, also gives $3.73\times10^{-7}$ m⁴.

## 6.3: 30 kg generator on parallel springs, $f_n = 2$ Hz
- (i) Static deflection $\delta = g/\omega_n^2 = 9.81/(4\pi)^2$ = **62.1 mm** ✔
- (ii) $c = 2\zeta\sqrt{km} = 2\zeta m\omega_n = 2(0.2)(30)(4\pi)$ = **151 N s/m** ✔
- (iii) $f_d = f_n\sqrt{1 - \zeta^2}$ = **1.96 Hz** ✔. Even 20% damping lowers the frequency by only 2%.

## 6.4: Diving board (2 m × 0.4 m × 30 mm, $E = 10$ GPa); father (80 kg) at the tip, son (20 kg) at the midpoint
- **(i) After the father dives**: only the son remains, 1 m from the clamp.
  - The stiffness **at his position** is that of a 1 m cantilever: $k = 3EI/(1)^3$ with $I = 0.4(0.03^3)/12 = 9\times10^{-7}$ m⁴, so $k = 27.0$ kN/m.
  - $f_n = \frac1{2\pi}\sqrt{27000/20}$ = **5.85 Hz** ✔
  - The massless beam beyond the son does not matter.
- **(ii)** $c = 180$ N s/m. The envelope decays as $e^{-\zeta\omega_nt}$ with $\zeta\omega_n = c/2m = 4.5$ s⁻¹. Falling to 1% takes $t = \ln100/4.5$ = **1.02 s** ✔. Here $\zeta = 0.122$, which is small, as assumed.
- **(iii) Swap them** (father, $m\times4$, at the midpoint):

| Quantity | Formula | Factor |
|---|---|---|
| natural frequency | $\propto m^{-1/2}$ | **×1/2** (2.92 Hz) |
| damping ratio | $\zeta = c/2\sqrt{km}\propto m^{-1/2}$ | **×1/2** (0.061) |
| decay time | $t = \ln100\cdot2m/c\propto m$ | **×4** (4.09 s) |

![[d_t6_q4_diving_board.png|760]]

## 6.5: Robot arm, $k = 39.5$ kN/m, 10 kg, amplitude falls to 1/10 in 0.5 s
- (i) $f_n = \frac1{2\pi}\sqrt{3950}$ = **10.0 Hz** ✔
- (ii) The decay spans $n = 10\times0.5 = 5$ cycles, so $\Delta = \tfrac15\ln10$ = **0.461** ✔ and $\zeta\approx\Delta/2\pi$ = **0.0733** ✔
- The exact relation $\zeta = \Delta/\sqrt{4\pi^2 + \Delta^2}$ gives 0.0731. The light-damping approximation is excellent.

## Sources
- FEEG1002 Problem sheet 6: SDOF free vibration (answers printed on the sheet)
