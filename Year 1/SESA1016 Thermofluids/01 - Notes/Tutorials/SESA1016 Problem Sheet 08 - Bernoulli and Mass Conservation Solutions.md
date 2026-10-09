---
title: "SESA1016 Problem Sheet 08 - Bernoulli and Mass Conservation Solutions"
module: "SESA1016 Thermofluids"
type: tutorial
stream: "Part B: Fluid Mechanics"
tags: [sesa1016, tutorial-solutions, bernoulli, continuity]
sheet: "Problem Sheet 08 - The Bernoulli Equation and Mass Conservation"
theory_notes: ["[[SESA1016 T10 - Euler and Bernoulli Equations]]", "[[SESA1016 T11 - Conservation of Mass]]"]
key_concepts: ["[[Bernoulli Equation]]", "[[Mass Flow Rate]]", "[[Stagnation Pressure and Pitot Tube]]"]
status: complete
sources: ["02 - Sources/Tutorial Sheets/Problem Sheet 08 - The Bernoulli Equation and Mass Conservation.pdf"]
---

# SESA1016 Problem Sheet 08 - Bernoulli and Mass Conservation Solutions

> [!abstract] Sheet Info
> Eleven questions on Bernoulli, piezometers, continuity, compressible density changes and numerical mass-flux integration.

## Q8.1 Water draining from a tank

Apply Bernoulli from the large-tank free surface to the port. Both points are exposed to atmosphere, and the free-surface speed is negligible:

$$\frac{p_{atm}}\rho+gH
=\frac{p_{atm}}\rho+\frac{V^2}{2}.$$

Thus Torricelli's result is

$$\boxed{V=\sqrt{2gH}}.$$

Density cancels for an incompressible fluid. At $H=10$ m,

$$\boxed{V=14.0\ \mathrm{m\,s^{-1}}}.$$

Real discharge is lower because of contraction and viscous loss.

## Q8.2 Flow past a circular cylinder

The highest pressure occurs at a stagnation point, $V=0$; the lowest occurs where $V=2V_0$. Along a streamline,

$$p+\frac12\rho V^2=p_\infty+\frac12\rho V_0^2.$$

Therefore

$$p_{max}=p_\infty+\frac12\rho V_0^2,$$

$$p_{min}=p_\infty+\frac12\rho(V_0^2-4V_0^2).$$

The difference is

$$
p_{max}-p_{min}=2\rho V_0^2
=2(1.2)(40)^2
=\boxed{3.84\ \mathrm{kPa}}.
$$

At maximum speed,

$$
\boxed{C_p=\frac{p-p_\infty}{\tfrac12\rho V_0^2}
=1-\left(\frac{V}{V_0}\right)^2=-3}.
$$

## Q8.3 Vertical contraction

Each piezometer measures pressure head plus elevation head. Their $0.15$ m difference is therefore

$$\frac{p_1-p_2}{\rho g}+z_1-z_2=0.15.$$

Bernoulli gives

$$gh+\frac{V_1^2}{2}=\frac{V_2^2}{2},$$

so with $V_1=3\ \mathrm{m\,s^{-1}}$,

$$
\boxed{V_2=\sqrt{V_1^2+2gh}=3.46\ \mathrm{m\,s^{-1}}}.
$$

## Q8.4 Flow in a tee

Steady incompressible continuity gives

$$Q_A=Q_B+Q_C.$$

With $D_A=D_B=4$ m, $D_C=2$ m, $V_A=6\ \mathrm{m\,s^{-1}}$ and $V_C=2\ \mathrm{m\,s^{-1}}$,

$$
V_B=\frac{A_AV_A-A_CV_C}{A_B}
=6-\left(\frac24\right)^2(2)
=\boxed{5.5\ \mathrm{m\,s^{-1}}}.
$$

## Q8.5 Industrial heater

Mass conservation requires

$$\rho_1A_1V_1=\rho_2A_2V_2.$$

At equal pressure, ideal-gas density is inversely proportional to absolute temperature. Since $D_1/D_2=2$, $A_1/A_2=4$. With the heater on,

$$
V_2=V_1\frac{A_1}{A_2}\frac{\rho_1}{\rho_2}
=2(4)\frac{413.15}{294.15}
=\boxed{11.24\ \mathrm{m\,s^{-1}}}.
$$

With the heater off, $T_2=T_1$ and

$$\boxed{V_2=2(4)=8.0\ \mathrm{m\,s^{-1}}}.$$

## Q8.6 Water cannon

Continuity gives

$$
V_e=V_p\left(\frac Dd\right)^2
=1.8\left(\frac{0.10}{0.05}\right)^2
=\boxed{7.2\ \mathrm{m\,s^{-1}}}.
$$

Bernoulli between the cylinder and atmospheric exit gives the required cylinder gauge pressure:

$$p_g=\frac12\rho(V_e^2-V_p^2).$$

The piston force is therefore

$$
F=p_g\frac{\pi D^2}{4}
=\frac12(1000)(7.2^2-1.8^2)\frac{\pi(0.10)^2}{4}
=\boxed{191\ \mathrm N}.
$$

## Q8.7 Stagnation-probe flow meter

The water manometer measures $p_{0B}-p_A$. Since total pressure is conserved between A and B,

$$p_{0B}=p_A+\frac12\rho_aV_A^2.$$

Hence

$$\rho_wgh=\frac12\rho_aV_A^2.$$

With $h=0.10$ m, $\rho_w=1000$ and $\rho_a=1.225\ \mathrm{kg\,m^{-3}}$,

$$V_A=40.0\ \mathrm{m\,s^{-1}}.$$

Because $V_B=1.5V_A$,

$$\boxed{V_B=60.0\ \mathrm{m\,s^{-1}}}.$$

## Q8.8 Hand outside a car window

An upper estimate treats the hand as a plate that brings the normal flow to rest:

$$F\sim qA=\frac12\rho V^2A.$$

Taking projected hand area $A\approx0.020\ \mathrm{m^2}$ and $\rho\approx1.225\ \mathrm{kg\,m^{-3}}$:

- at $55$ mph $=24.6\ \mathrm{m\,s^{-1}}$, $F\approx7.4$ N;
- at $164$ mph $=73.3\ \mathrm{m\,s^{-1}}$, $F\approx65.8$ N.

Thus the requested estimates are about $\boxed{7\ \mathrm N}$ and $\boxed{60\ \mathrm N}$. The $V^2$ scaling matters more than the uncertainty in hand area or drag coefficient.

## Q8.9 Flow through a constriction

Assume steady, incompressible, inviscid flow; a horizontal pipe; uniform mean velocity at each station; and no losses. Then

$$A_1V_1=A_2V_2,$$

$$p_1+\frac12\rho V_1^2=p_2+\frac12\rho V_2^2.$$

Eliminating $V_1=(A_2/A_1)V_2$ gives

$$
V_2=\sqrt{
\frac{2(p_1-p_2)}{\rho[1-(A_2/A_1)^2]}}.
$$

Therefore

$$
\boxed{\dot m=\rho A_2
\sqrt{\frac{2(p_1-p_2)}{\rho[1-(A_2/A_1)^2]}}}.
$$

A real meter needs a discharge coefficient because boundary layers, separation and irreversible pressure loss violate the ideal assumptions.

## Q8.10 Numerical mass-flow integration

For a two-dimensional rectangular channel of width $b=0.097$ m,

$$\dot m=b\int_0^H\rho(y)V(y)\,dy,$$

with

$$\rho(y)=\frac{p}{RT(y)},\qquad p=3.4\times10^5\ \mathrm{Pa}.$$

Applying the trapezoidal rule to the seven supplied values,

```python
rho = pressure / (287.0 * temperature)
mdot = width * np.trapezoid(rho * velocity, y)
```

gives

$$\boxed{\dot m=0.3045\ \mathrm{kg\,s^{-1}}\approx0.30\ \mathrm{kg\,s^{-1}}}.$$

The temperature-dependent density must remain inside the integral.

## Q8.11 Hydraulic pistons

Choose the fluid-filled junction as a control volume and assign signs to piston volume displacement rates $AV$. Piston A moves twice as quickly as B, and its larger swept-volume contribution is not balanced by B. Continuity therefore requires piston C to provide the remaining outward volume flux:

$$\boxed{\text{piston C moves upward}}.$$

## Related

- [[SESA1016 T10 - Euler and Bernoulli Equations]]
- [[SESA1016 T11 - Conservation of Mass]]
- [[Bernoulli Equation]]
- [[Mass Flow Rate]]
- [[Stagnation Pressure and Pitot Tube]]

