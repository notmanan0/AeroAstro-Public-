---
title: "SESA2028 S11 - Spinning Discs"
module: "SESA2028 Aerospace Materials & Structures"
type: topic
stream: "Structures"
order: 11
tags: [sesa2028, structures, spinning-disc, continuum-mechanics]
date: 2026-10-30
status: written-ahead
coverage: "Not lectured in 2025–26: written from slides SL24 only (rotating parts were named as an application of the continuum lectures, 2026-05-06 part 1, l. 12, but the course ended with shrink fits)"
parent: ["[[SESA2028 Aerospace Materials & Structures Hub]]"]
prerequisites: ["[[SESA2028 S10 - Thick Cylinders and Shrink Fits]]"]
next_topics: []
key_concepts: ["[[Spinning Disc Stress]]", "[[Axisymmetric Equilibrium]]"]
tutorial_sheets: []
sources: ["02 - Sources/Structures Lectures/SL24 - Continuum Mechanics 6 - Spinning Discs.pdf"]
---

# SESA2028 S11 - Spinning Discs

> [!abstract] Summary
> A rotating disc is loaded by its own inertia, a radial body force $\rho\omega^2r$ per unit volume, so the axisymmetric equilibrium equation gains a body-force term and the Lamé solution gains an $r^2$ term. For a thin disc in plane stress, $\sigma_{rr}=A-B/r^2-\frac{3+\nu}{8}\rho\omega^2r^2$ and $\sigma_{\theta\theta}=A+B/r^2-\frac{1+3\nu}{8}\rho\omega^2r^2$. A central hole, however small, doubles the peak hoop stress compared with a solid disc. The topic is outside the 2025–26 examined scope.

> [!summary]- Exam use: quick path
> - **Use it when:** a disc, rotor or flywheel spins and its stresses or burst speed are needed (not examinable in 2025–26).
> - **Assumptions:** thin disc (plane stress), uniform thickness, constant angular velocity $\omega$ in rad/s, linear elastic, isotropic.
> - **Method:** 1. Write the solution with the $\rho\omega^2r^2$ terms. 2. Solid disc: $B=0$; disc with a hole: $\sigma_{rr}=0$ at $r_i$ (or the shrink-fit pressure). 3. $\sigma_{rr}(r_o)=0$, or the blade loading spread over the rim. 4. Peak stress: the centre (solid) or the bore hoop stress (hole). 5. Yield check by von Mises or Tresca.
> - **Common mistakes:** keeping $B$ in a solid disc; using rev/min instead of rad/s.
> - **Practise:** [[#Worked example: a DVD at full speed]]

Rotating parts, turbine and compressor discs above all, are loaded by their own inertia, which grows with the square of the speed. Every element of a spinning disc has to be pulled inwards to stay on its circle, and that pull has to come from the material itself: from the radial stress on its faces and, as for a hoop, from the hoop stress round the circumference. The analysis is the Lamé problem of [[SESA2028 S9 - Continuum Mechanics in Cylindrical Coordinates|S9]] with a body force added, and the stress in complex rotating parts is often estimated from this thin-disc solution.

## 1. Governing equation

### The body force

An element of the disc at radius $r$, of size $\delta r$ by $r\,\delta\theta$ and thickness $z$, has volume $V=r\,\delta\theta\,\delta r\,z$ and mass $m=\rho V$. Turning at $\omega$, it needs a centripetal force $m\omega^2r$, which the surrounding material supplies. In the equilibrium equation this appears as a radial body force $f_r$ per unit volume, with

$$
f_rV=\rho V\omega^2r\quad\Longrightarrow\quad f_r=\rho\omega^2r .
$$

The axisymmetric equilibrium equation of S9 becomes

$$
\frac{d\sigma_{rr}}{dr}+\frac{\sigma_{rr}-\sigma_{\theta\theta}}{r}=-\rho\omega^2r .
$$

### Stresses in terms of the displacement

With axial symmetry, $\varepsilon_{rr}=du_r/dr$ and $\varepsilon_{\theta\theta}=u_r/r$. A thin disc is in plane stress, so Hooke's law, inverted, is

$$
\sigma_{rr}=\frac{E}{1-\nu^2}\left(\frac{du_r}{dr}+\nu\frac{u_r}{r}\right),\qquad\sigma_{\theta\theta}=\frac{E}{1-\nu^2}\left(\frac{u_r}{r}+\nu\frac{du_r}{dr}\right).
$$

Differentiate the radial stress, using the quotient rule on $u_r/r$:

$$
\frac{d\sigma_{rr}}{dr}=\frac{E}{1-\nu^2}\left(\frac{d^2u_r}{dr^2}+\frac\nu r\frac{du_r}{dr}-\nu\frac{u_r}{r^2}\right).
$$

The difference term is

$$
\frac{\sigma_{rr}-\sigma_{\theta\theta}}{r}=\frac{E}{1-\nu^2}\cdot\frac{(1-\nu)}{r}\left(\frac{du_r}{dr}-\frac{u_r}{r}\right).
$$

Add the two; the $\nu$ terms cancel:

$$
\frac{E}{1-\nu^2}\left(\frac{d^2u_r}{dr^2}+\frac1r\frac{du_r}{dr}-\frac{u_r}{r^2}\right)=-\rho\omega^2r .
$$

So the radial displacement satisfies

$$
\frac{d^2u_r}{dr^2}+\frac1r\frac{du_r}{dr}-\frac{u_r}{r^2}=-\frac{(1-\nu^2)\rho\omega^2r}{E},
$$

a second-order inhomogeneous ODE. The left-hand side is $\frac{d}{dr}\left[\frac1r\frac{d}{dr}(ru_r)\right]$, which is how it is integrated.

### Solution

The complementary function, solving the equation with zero on the right, is $u_r=C_0r+C_1/r$: substituting $r$ gives $0+1/r-1/r=0$, and $1/r$ gives $2/r^3-1/r^3-1/r^3=0$. For the particular integral try $u_r=Kr^3$:

$$
6Kr+3Kr-Kr=8Kr=-\frac{(1-\nu^2)\rho\omega^2r}{E}\quad\Longrightarrow\quad K=-\frac{(1-\nu^2)\rho\omega^2}{8E}.
$$

So

$$
u_r=C_0r+\frac{C_1}{r}-\frac{(1-\nu^2)\rho\omega^2r^3}{8E}.
$$

Substitute $u_r/r=C_0+C_1/r^2+Kr^2$ and $du_r/dr=C_0-C_1/r^2+3Kr^2$ into the stresses. Writing $A=EC_0/(1-\nu)$ and $B=EC_1/(1+\nu)$, the $K$ terms give $(3+\nu)K$ and $(1+3\nu)K$ times $E/(1-\nu^2)$:

$$
\boxed{\sigma_{rr}=A-\frac{B}{r^2}-\frac{3+\nu}{8}\rho\omega^2r^2,\qquad\sigma_{\theta\theta}=A+\frac{B}{r^2}-\frac{1+3\nu}{8}\rho\omega^2r^2}
$$

With $\omega=0$ this is the Lamé solution again. $A$ and $B$ come from the boundary conditions.

## 2. Solid disc and disc with a hole

### Solid disc

At the centre the stress must be finite, so $B=0$. The rim is unloaded, $\sigma_{rr}(r_o)=0$:

$$
A=\frac{3+\nu}{8}\rho\omega^2r_o^2 .
$$

So

$$
\sigma_{rr}=\frac{3+\nu}{8}\rho\omega^2\left(r_o^2-r^2\right),\qquad\sigma_{\theta\theta}=\frac{\rho\omega^2}{8}\left[(3+\nu)r_o^2-(1+3\nu)r^2\right].
$$

Both are largest at the centre, where they are equal:

$$
\sigma_{rr,max}=\sigma_{\theta\theta,max}=\frac{3+\nu}{8}\rho\omega^2r_o^2 .
$$

### Disc with a central hole

With a hole of radius $r_i$ and both edges unloaded,

$$
A-\frac{B}{r_i^2}-\frac{3+\nu}{8}\rho\omega^2r_i^2=0,\qquad A-\frac{B}{r_o^2}-\frac{3+\nu}{8}\rho\omega^2r_o^2=0 .
$$

Subtract the first from the second: $B(1/r_i^2-1/r_o^2)=\tfrac{3+\nu}{8}\rho\omega^2(r_o^2-r_i^2)$, and since $1/r_i^2-1/r_o^2=(r_o^2-r_i^2)/r_i^2r_o^2$,

$$
B=\frac{3+\nu}{8}\rho\omega^2r_i^2r_o^2,\qquad A=\frac{3+\nu}{8}\rho\omega^2\left(r_i^2+r_o^2\right).
$$

The stresses are

$$
\sigma_{rr}=\frac{3+\nu}{8}\rho\omega^2\left(r_i^2+r_o^2-\frac{r_i^2r_o^2}{r^2}-r^2\right),\qquad\sigma_{\theta\theta}=\frac{3+\nu}{8}\rho\omega^2\left(r_i^2+r_o^2+\frac{r_i^2r_o^2}{r^2}-\frac{1+3\nu}{3+\nu}r^2\right).
$$

The hoop stress is largest at the bore. Putting $r=r_i$:

$$
\sigma_{\theta\theta,max}=\frac{3+\nu}{4}\rho\omega^2\left(r_o^2+\frac{1-\nu}{3+\nu}r_i^2\right).
$$

The radial stress is zero at both edges, and its maximum is where $d\sigma_{rr}/dr=2r_i^2r_o^2/r^3-2r=0$, at $r=\sqrt{r_ir_o}$:

$$
\sigma_{rr,max}=\frac{3+\nu}{8}\rho\omega^2\left(r_o-r_i\right)^2 .
$$

As $r_i\to0$ the bore hoop stress tends to $\tfrac{3+\nu}{4}\rho\omega^2r_o^2$, twice the solid-disc value: even a pinhole doubles the peak stress, a stress-concentration factor of 2 ([[Spinning Disc Stress]]).

![[structures_spinning_disc_stress.png|640]]

### Loaded rims and shrink-fitted discs

Compressor and turbine discs carry blades on their rims. With the mass and centre of mass of one blade known, each blade's centrifugal force at $\omega$ follows; multiplied by the number of blades it gives a total, which is spread as a uniform load round the rim and divided by the rim area to give the radial stress used as the outer boundary condition. A disc can also be shrink-fitted to a shaft without fasteners: the shrink-fit and spinning stresses superpose. At rest the interface radial stress is compressive, holding the disc on; spinning adds radial tension there, and the compressive shrink-fit stress must always exceed it, or the disc loosens on the shaft at speed.

## Worked example: a DVD at full speed

A polycarbonate DVD ($\rho=1200$ kg/m³, $E=3$ GPa, $\nu=0.32$, tensile yield strength 60 MPa) is 120 mm across with a 15 mm central hole and 1.2 mm thick. At its maximum speed of 1600 rev/min, what is the safety factor against yield by von Mises?

Convert the speed: $\omega=1600\times2\pi/60=167.6$ rad/s, so $\rho\omega^2=1200\times167.6^2=3.37\times10^7$ N/m⁴. The radii are $r_o=0.060$ m and $r_i=0.0075$ m. At the bore $\sigma_{rr}=0$ and $\sigma_{zz}=0$ (plane stress), so the von Mises stress is the hoop stress there:

$$
\sigma_{\theta\theta}(r_i)=\frac{\rho\omega^2}{4}\left[(3+\nu)r_o^2+(1-\nu)r_i^2\right]=\frac{3.37\times10^7}{4}\left[3.32\times0.060^2+0.68\times0.0075^2\right].
$$

$$
\sigma_{\theta\theta}(r_i)=8.42\times10^6\times0.01199=1.01\times10^5\text{ Pa}=0.101\text{ MPa}.
$$

The safety factor is

$$
n=\frac{60}{0.101}=594 .
$$

A DVD is in no danger from its own rotation; the stress is a few hundredths of a percent of its strength.

> [!check] Where the von Mises stress peaks, and the factor of 2
> Evaluating $\sqrt{\sigma_{rr}^2+\sigma_{\theta\theta}^2-\sigma_{rr}\sigma_{\theta\theta}}$ across the disc confirms the maximum is at the bore, 0.101 MPa. A solid DVD would peak at $\tfrac{3+\nu}{8}\rho\omega^2r_o^2=0.050$ MPa at its centre, so the 15 mm hole raises the peak by a factor of 2.01, close to the pinhole limit of 2 because $r_i/r_o=0.125$ is small. The largest radial stress, 0.039 MPa, is at $r=\sqrt{r_ir_o}=21$ mm.

![[structures_s11_dvd_disc.png|800]]

## Links

- Parent: [[SESA2028 Aerospace Materials & Structures Hub]] · Previous: [[SESA2028 S10 - Thick Cylinders and Shrink Fits]]
- Concepts: [[Spinning Disc Stress]] · [[Axisymmetric Equilibrium]] · [[Lame Equations]]
- Materials for hot discs: [[SESA2028 M8 - High Temperature Materials - Creep, Oxidation and Superalloys]]

## Sources

- Slides: `SL24 - Continuum Mechanics 6 - Spinning Discs.pdf` (derivation on slides 4–12, loaded rims and shrink-fitted discs on 13–14, the DVD example on slide 16). Not lectured in 2025–26, so there is no transcript and the scope is not confirmed.
- The ODE solution was checked with SymPy and the DVD example recomputed in Python. Figures: `generate_structures_s11_figures.py` and `generate_structures_figures.py` (normalised solid-disc stresses).

## Self-study tasks

No tasks were set, because the topic was not lectured. Suggested tasks, not lecturer-set:

### Further practice

- [ ] Derive the disc solution from the equilibrium equation with the body force. → [[#1. Governing equation]]
- [ ] Show that a pinhole doubles the peak hoop stress of a solid disc. → [[#Disc with a central hole]]
- [ ] The DVD safety factor (SL24 slide 16). → [[#Worked example: a DVD at full speed]]
