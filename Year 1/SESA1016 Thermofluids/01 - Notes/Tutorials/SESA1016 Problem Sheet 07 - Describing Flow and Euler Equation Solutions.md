---
title: "SESA1016 Problem Sheet 07 - Describing Flow and Euler Equation Solutions"
module: "SESA1016 Thermofluids"
type: tutorial
stream: "Part B: Fluid Mechanics"
tags: [sesa1016, tutorial-solutions, kinematics, euler-equation]
sheet: "Problem Sheet 07 - Describing Flow and the Euler Equation"
theory_notes: ["[[SESA1016 T9 - Describing Flow and the Material Derivative]]", "[[SESA1016 T10 - Euler and Bernoulli Equations]]"]
key_concepts: ["[[Material Derivative]]", "[[Streamline, Pathline and Streakline]]"]
status: complete
sources: ["02 - Sources/Tutorial Sheets/Problem Sheet 07 - Describing Flow and the Euler Equation.pdf"]
---

# SESA1016 Problem Sheet 07 - Describing Flow and Euler Equation Solutions

> [!abstract] Sheet Info
> Six questions connecting velocity fields to streamlines, particle acceleration, pressure gradients and Mach number.

## Q7.1 Streamlines

The steady velocity field is

$$\mathbf V=2x\mathbf i-2y\mathbf j.$$

A streamline satisfies

$$\frac{dy}{dx}=\frac{v}{u}=\frac{-2y}{2x}=-\frac yx.$$

Separating and integrating,

$$\frac{dy}{y}=-\frac{dx}{x}
\quad\Rightarrow\quad
\ln y=-\ln x+C,
$$

$$\boxed{xy=C\quad\text{or}\quad y=\frac Cx}.$$

The curves are rectangular hyperbolae. In the first quadrant, $u>0$ and $v<0$: particles move to the right and downward along each streamline.

## Q7.2 Convective acceleration in a nozzle

The axial speed is

$$V(x)=\frac{V_0}{1-0.5x/L}.$$

The flow is steady and the centreline is straight, so the material acceleration is entirely convective:

$$a_x=V\frac{dV}{dx}.$$

Now

$$
\frac{dV}{dx}=\frac{0.5V_0/L}{(1-0.5x/L)^2},
$$

and hence

$$
a_x=\frac{0.5V_0^2/L}{(1-0.5x/L)^3}.
$$

At $x/L=0.5$, with $V_0=100\ \mathrm{m\,s^{-1}}$ and $L=0.5$ m,

$$
\boxed{a_x=2.37\times10^4\ \mathrm{m\,s^{-2}}\approx2416g}.
$$

> [!important] Steady does not mean zero acceleration
> The velocity at a fixed point is time-independent, but a particle accelerates as it passes through the spatial velocity gradient.

## Q7.3 Pressure deficit in a tip vortex

Radial Euler balance gives

$$\frac{dp}{dr}=\rho\frac{V_\theta^2}{r}.$$

Inside the core,

$$V_\theta(r)=\frac{4V_{max}}{r_0^2}(r_0-r)r.$$

Since the surrounding pressure at $r=r_0$ is $p_{atm}$,

$$
p_{atm}-p_{core}
=\int_0^{r_0}\rho\frac{V_\theta^2}{r}\,dr.
$$

Substitution gives

$$
p_{atm}-p_{core}
=\frac{16\rho V_{max}^2}{r_0^4}
\int_0^{r_0}(r_0-r)^2r\,dr.
$$

The integral is $r_0^4/12$, so the core radius cancels:

$$
\boxed{p_{atm}-p_{core}=\frac43\rho V_{max}^2}.
$$

For $V_{max}=46\ \mathrm{m\,s^{-1}}$ and standard density $\rho=1.225\ \mathrm{kg\,m^{-3}}$,

$$
\boxed{p_{core}-p_{atm}=-3.46\ \mathrm{kPa}}.
$$

The low core pressure is accompanied by a temperature reduction; sufficiently humid air can therefore reach saturation and condense visibly.

## Q7.4 Visualising vector fields

The accompanying notebook is a computational exercise. For any field $\mathbf V=(u,v)$, the reliable workflow is:

1. sample $(u,v)$ on a grid and plot arrows;
2. plot speed $|\mathbf V|$ separately if useful;
3. integrate $dy/dx=v/u$ for steady two-dimensional streamlines;
4. avoid confusing arrow length with streamline direction.

## Q7.5 Emptying tank

The pipe flow is **unsteady**. As the free-surface height falls, the driving hydrostatic head falls. For an ideal discharge,

$$V(t)\approx\sqrt{2gh(t)},$$

so the velocity at a fixed pipe location changes with time:

$$\boxed{\partial V/\partial t\ne0}.$$

It may be treated as quasi-steady only if the tank level changes slowly compared with the fluid transit time through the pipe.

## Q7.6 Mach number and speed of sound

For a calorically perfect gas,

$$c=\sqrt{\gamma RT},\qquad Ma=\frac Vc.$$

At altitude, $T=-50^\circ\mathrm C=223.15$ K. With $\gamma=1.4$ and $R=287\ \mathrm{J\,kg^{-1}K^{-1}}$,

$$
c=\sqrt{1.4(287)(223.15)}
=\boxed{299.3\ \mathrm{m\,s^{-1}}},
$$

$$\boxed{Ma=250/299.3=0.835}.$$

At sea level, $T=15^\circ\mathrm C=288.15$ K:

$$c=340.3\ \mathrm{m\,s^{-1}},qquad
\boxed{Ma=250/340.3=0.735}.$$

The same flight speed has a lower Mach number in warmer air because the speed of sound rises as $\sqrt T$. At $10\,000$ m, supersonic flight requires

$$\boxed{V>c=299.3\ \mathrm{m\,s^{-1}}}.$$

## Related

- [[SESA1016 T9 - Describing Flow and the Material Derivative]]
- [[SESA1016 T10 - Euler and Bernoulli Equations]]
- [[Material Derivative]]
- [[Streamline, Pathline and Streakline]]

