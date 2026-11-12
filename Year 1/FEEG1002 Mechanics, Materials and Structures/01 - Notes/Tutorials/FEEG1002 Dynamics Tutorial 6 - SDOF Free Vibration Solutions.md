---
title: "FEEG1002 Dynamics Tutorial 6 - SDOF Free Vibration Solutions"
module: "FEEG1002 Mechanics, Materials and Structures"
type: tutorial
stream: "Part D: Dynamics"
tags: [feeg1002, tutorial-solutions, dynamics, vibration, natural-frequency, damping, log-decrement]
sheet: "Problem sheet 6 - SDOF free vibration (2024-25)"
theory_notes: ["[[FEEG1002 D6 - Single Degree of Freedom Vibration]]"]
key_concepts: ["[[Damping Ratio and Natural Frequency]]", "[[Equivalent Spring Stiffness]]", "[[Logarithmic Decrement]]"]
status: lectured
date: 2026-11-05
sources: ["02 - Sources/Dynamics/Tutorials/Tutorial Sheet 06 - SDOF Free Vibration.pdf"]
---

# FEEG1002 Dynamics Tutorial 6 - SDOF Free Vibration Solutions

> [!abstract] Sheet summary
> Five problems on the free vibration of single degree of freedom systems: energy in a mass-spring system (6.1), the tip stiffness and natural frequency of a turbine on a pole (6.2), static deflection, damping coefficient and damped frequency of a generator on springs (6.3), a diving board with damping and a scaling argument (6.4), and the logarithmic decrement of a robot arm (6.5). Final answers are printed for every part except 6.4(iii), and all printed answers are reproduced; 6.4(iii) is worked out here.

Each problem is the same model, a rigid mass on a massless spring with (in 6.3 to 6.5) a viscous damper in parallel, with motion measured from static equilibrium. The work is mostly in finding the spring: a coil spring is given directly, but a pole or a board is a cantilever whose stiffness at the point where the mass sits is $3EI/L^3$. After that, $\omega_n=\sqrt{k/m}$, $\zeta=c/2\sqrt{km}$ and the decaying envelope $e^{-\zeta\omega_nt}$ answer almost everything.

---

## 6.1 - Speed through equilibrium

A 0.3 kg mass hangs at static equilibrium on a 1000 N/m spring. It is pulled a further 0.1 m and released. Find its speed as it passes through equilibrium, with no damping.

Measure the displacement $x$ from the static equilibrium position. The weight and the static spring force $k\delta$ cancel there, so the motion is that of $m\ddot x+kx=0$ and the static stretch ($\delta=mg/k=2.9$ mm) plays no part. Released from rest at $x_0=0.1$ m, all the energy is stored in the spring; at $x=0$ it is all kinetic:

$$
\begin{aligned}
\tfrac12kx_0^2&=\tfrac12m\dot x_{max}^2\\
\dot x_{max}&=x_0\sqrt{\frac km}=x_0\,\omega_n\\
&=0.1\sqrt{\frac{1000}{0.3}}=0.1\times57.74
\end{aligned}
$$

$$
\boxed{\dot x_{max}=5.77\ \mathrm{m/s}}
$$

matching the printed answer. The same result comes from the response $x=x_0\cos\omega_nt$, whose velocity amplitude is $x_0\omega_n$.

Theory: [[FEEG1002 D6 - Single Degree of Freedom Vibration#Static and dynamic displacement]] · [[FEEG1002 D6 - Single Degree of Freedom Vibration#Energy]]

## 6.2 - Wind turbine on a steel pole

A 10 kg turbine sits on top of a 5 m hollow steel pole, outer radius 40 mm, wall 2 mm, $E=210$ GPa; the pole's mass is neglected. Find the bending stiffness at the top, the natural frequency, and the pole length that would double it.

The hollow section is a solid circle of radius $r_o=40$ mm minus one of $r_i=38$ mm, so with $I=\tfrac14\pi r^4$ for each:

$$
\begin{aligned}
I&=\frac\pi4\left(r_o^4-r_i^4\right)\\
&=\frac\pi4\left(0.040^4-0.038^4\right)\\
&=\frac\pi4\left(2.560-2.085\right)\times10^{-6}\\
&=3.730\times10^{-7}\ \mathrm{m^4}
\end{aligned}
$$

The pole is a cantilever built in at the ground with the turbine at its free tip, and a tip load $F$ deflects it by $FL^3/3EI$, so the stiffness at the tip is

$$
\begin{aligned}
k&=\frac{3EI}{L^3}=\frac{3\times210\times10^9\times3.730\times10^{-7}}{5^3}\\
&=1880\ \mathrm{N/m}
\end{aligned}
$$

$$
\boxed{k=1880\ \mathrm{N/m}}
$$

The natural frequency of the 10 kg turbine on this spring is

$$
\begin{aligned}
\omega_n&=\sqrt{\frac km}=\sqrt{\frac{1880}{10}}=13.71\ \mathrm{rad/s}\\
f_n&=\frac{\omega_n}{2\pi}
\end{aligned}
$$

$$
\boxed{f_n=2.18\ \mathrm{Hz}}
$$

For part (iii), the frequency depends on length through $k$ alone:

$$
\begin{aligned}
f_n&\propto\sqrt k\propto\sqrt{L^{-3}}=L^{-3/2}\\
\frac{f_{n2}}{f_{n1}}&=\left(\frac{L_2}{L_1}\right)^{-3/2}=2\\
L_2&=L_1\,2^{-2/3}=5\times0.630
\end{aligned}
$$

$$
\boxed{L_2=3.15\ \mathrm m}
$$

All three match the printed answers. Doubling the frequency needs four times the stiffness, which a cubic dependence on length delivers with only a 37% shorter pole. As a check on $I$, the thin-walled approximation $I\approx\pi r_m^3t$ with mean radius $r_m=39$ mm gives $3.727\times10^{-7}$ m⁴.

Theory: [[FEEG1002 D6 - Single Degree of Freedom Vibration#Equivalent springs]] · [[FEEG1002 D6 - Single Degree of Freedom Vibration#Natural frequency]] · [[FEEG1002 A4 - Engineer's Bending Theory and Second Moment of Area#Circle]]

## 6.3 - Generator on parallel springs

A 30 kg generator on coil springs in parallel is to have $f_n=2$ Hz. Find the static deflection, the total damping coefficient for $\zeta=0.2$, and the damped natural frequency.

The springs in parallel act as one spring of stiffness $k$, and $\omega_n=2\pi f_n=4\pi=12.57$ rad/s. The static deflection under the weight is $\delta=mg/k$, and since $k=m\omega_n^2$ the mass cancels:

$$
\begin{aligned}
\delta&=\frac{mg}{k}=\frac{g}{\omega_n^2}\\
&=\frac{9.81}{(4\pi)^2}=\frac{9.81}{157.9}
\end{aligned}
$$

$$
\boxed{\delta=0.0621\ \mathrm m}
$$

The sheet calls the machine "the engine" in part (i); it is the generator. Dampers in parallel with the springs add their coefficients, and the total must give $\zeta=0.2$. With $k=m\omega_n^2=4737$ N/m:

$$
\begin{aligned}
c&=\zeta c_{crit}=2\zeta\sqrt{km}\\
&=2\zeta m\omega_n\\
&=2\times0.2\times30\times12.57
\end{aligned}
$$

$$
\boxed{c=151\ \mathrm{N\,s/m}}
$$

The damped natural frequency is

$$
\begin{aligned}
f_d&=f_n\sqrt{1-\zeta^2}\\
&=2\sqrt{1-0.04}=2\times0.980
\end{aligned}
$$

$$
\boxed{f_d=1.96\ \mathrm{Hz}}
$$

All three match the printed answers. Even with 20% of critical damping the frequency falls by only 2%, because the reduction depends on $\zeta^2$.

Theory: [[FEEG1002 D6 - Single Degree of Freedom Vibration#Static and dynamic displacement]] · [[FEEG1002 D6 - Single Degree of Freedom Vibration#Damping ratio and the three regimes]]

## 6.4 - Diving board

A wooden board 2 m long, 0.4 m wide and 30 mm thick ($E=10$ GPa, mass neglected) is built in at one end. An 80 kg man stands at the free end and his 20 kg son at the midpoint. (i) Find the frequency after the man dives off, without damping. (ii) With $c=180$ N s/m, find the time for the amplitude to fall to 1/100. (iii) If they swap, find the factors by which the natural frequency, damping ratio and decay time change.

![[d_t6_q4_diving_board.png|760]]

### Part (i) - natural frequency with the son at the midpoint

After the dive only the son remains, 1 m from the clamp. The board is massless, so the 1 m beyond him carries no load and simply follows; the spring he sits on is the stiffness at his position, that of a 1 m cantilever loaded at its tip. The rectangular section has

$$
\begin{aligned}
I&=\frac{bh^3}{12}=\frac{0.4\times0.03^3}{12}\\
&=9.0\times10^{-7}\ \mathrm{m^4}
\end{aligned}
$$

$$
\begin{aligned}
k&=\frac{3EI}{a^3}=\frac{3\times10\times10^9\times9.0\times10^{-7}}{1^3}\\
&=27.0\ \mathrm{kN/m}
\end{aligned}
$$

$$
\begin{aligned}
\omega_n&=\sqrt{\frac km}=\sqrt{\frac{27\,000}{20}}=36.74\ \mathrm{rad/s}\\
f_n&=\frac{36.74}{2\pi}
\end{aligned}
$$

$$
\boxed{f_n=5.85\ \mathrm{Hz}}
$$

matching the printed answer. Using the tip stiffness of the full 2 m board, $3EI/2^3=3.4$ kN/m, would be wrong: the son is not at the tip.

### Part (ii) - time to decay to one hundredth

The underdamped free vibration decays inside the envelope $e^{-\zeta\omega_nt}$, and the decay rate is

$$
\zeta\omega_n=\frac{c}{2\sqrt{km}}\sqrt{\frac km}=\frac{c}{2m}=\frac{180}{2\times20}=4.5\ \mathrm{s^{-1}}
$$

The amplitude falls to 1/100 of its initial value when

$$
\begin{aligned}
e^{-\zeta\omega_nt}&=\frac1{100}\\
\zeta\omega_nt&=\ln100\\
t&=\frac{\ln100}{4.5}=\frac{4.605}{4.5}
\end{aligned}
$$

$$
\boxed{t=1.02\ \mathrm s}
$$

matching the printed answer. The damping ratio is $\zeta=4.5/36.74=0.122$. The envelope result holds for any underdamped system, so the small-damping assumption is not needed here; it would matter only if the decay were counted in cycles, where $f_d=5.80$ Hz differs from $f_n$ by 0.7%.

### Part (iii) - scaling when father and son swap

No answer is printed for this part. After the swap the son dives from the tip and the 80 kg father stays at the midpoint: the spring ($k=27$ kN/m, the same point on the board) and the damper ($c=180$ N s/m) are unchanged, and only the mass changes, by a factor of 4. The three formulae scale as

$$
\begin{aligned}
\omega_n&=\sqrt{k/m}\propto m^{-1/2}&&\Rightarrow\ \times\tfrac12\\
\zeta&=\frac{c}{2\sqrt{km}}\propto m^{-1/2}&&\Rightarrow\ \times\tfrac12\\
t&=\frac{\ln100}{\zeta\omega_n}=\frac{2m\ln100}{c}\propto m&&\Rightarrow\ \times4
\end{aligned}
$$

$$
\boxed{f_n\times\tfrac12\ (2.92\ \mathrm{Hz}),\qquad\zeta\times\tfrac12\ (0.061),\qquad t\times4\ (4.09\ \mathrm s)}
$$

The decay time grows by more than the period does: the heavier system has a lower decay rate $c/2m$, so it rings for longer in seconds and also for more cycles ($1.02\times5.85\approx6$ cycles before, $4.09\times2.92\approx12$ after).

Theory: [[FEEG1002 D6 - Single Degree of Freedom Vibration#Equivalent springs]] · [[FEEG1002 D6 - Single Degree of Freedom Vibration#Damping ratio and the three regimes]] · [[FEEG1002 D6 - Single Degree of Freedom Vibration#Speed camera on a cantilever post]]

## 6.5 - Robot arm stopping suddenly

A robot arm of equivalent stiffness 39.5 kN/m carries a 10 kg component and vibrates at its natural frequency after stopping suddenly. Find the undamped natural frequency, and the logarithmic decrement and damping ratio if the amplitude falls to one tenth in 0.5 s.

$$
\begin{aligned}
\omega_n&=\sqrt{\frac km}=\sqrt{\frac{39\,500}{10}}=62.85\ \mathrm{rad/s}\\
f_n&=\frac{62.85}{2\pi}
\end{aligned}
$$

$$
\boxed{f_n=10.0\ \mathrm{Hz}}
$$

With light damping the arm vibrates at very nearly $f_n$, so in 0.5 s it completes $n=0.5\times10.0=5.0$ cycles, over which the amplitude ratio is $x_1/x_{n+1}=10$:

$$
\begin{aligned}
\Delta&=\frac1n\ln\frac{x_1}{x_{n+1}}\\
&=\frac15\ln10=\frac{2.303}{5}
\end{aligned}
$$

$$
\boxed{\Delta=0.461}
$$

and for small damping

$$
\begin{aligned}
\zeta&\approx\frac{\Delta}{2\pi}=\frac{0.4605}{2\pi}
\end{aligned}
$$

$$
\boxed{\zeta=0.0733}
$$

All three match the printed answers, and $\zeta=0.073$ is indeed small. The same damping ratio follows without counting cycles at all, directly from the envelope: $e^{-\zeta\omega_n(0.5)}=1/10$ gives $\zeta=\ln10/(0.5\,\omega_n)=2.303/31.42=0.0733$, which is exact. The two small-damping approximations (counting cycles at $f_n$ rather than $f_d$, and $\Delta\approx2\pi\zeta$) cancel exactly here, so the printed 0.0733 is not merely approximate.

Theory: [[FEEG1002 D6 - Single Degree of Freedom Vibration#Logarithmic decrement]] · [[FEEG1002 D6 - Single Degree of Freedom Vibration#Natural frequency]]

---

## Links

- Topic note: [[FEEG1002 D6 - Single Degree of Freedom Vibration]] · beam stiffness from [[FEEG1002 A5 - Beam Deflection and Macaulay's Method]] · second moments from [[FEEG1002 A4 - Engineer's Bending Theory and Second Moment of Area]]
- Concepts: [[Damping Ratio and Natural Frequency]] · [[Equivalent Spring Stiffness]] · [[Logarithmic Decrement]] · [[Standard Beam Deflections]]
- Hub: [[FEEG1002 Mechanics, Materials and Structures Hub]]

## Sources

- `Tutorial Sheet 06 - SDOF Free Vibration.pdf` (FEEG1002 Problem sheet 6, 2024-25): Q6.1–Q6.5 with printed final answers except 6.4(iii), no worked solutions.
