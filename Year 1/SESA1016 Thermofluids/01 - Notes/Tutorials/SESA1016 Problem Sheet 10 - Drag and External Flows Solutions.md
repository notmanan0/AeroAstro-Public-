---
title: "SESA1016 Problem Sheet 10 - Drag and External Flows Solutions"
module: "SESA1016 Thermofluids"
type: tutorial
stream: "Part B: Fluid Mechanics"
tags: [sesa1016, tutorial-solutions, boundary-layers, drag]
sheet: "Problem Sheet 10 - Drag and Its Sources: External Flows"
theory_notes: ["[[SESA1016 T14 - Boundary Layers and the Origin of Drag]]"]
key_concepts: ["[[Boundary-layer Thickness Measures]]", "[[Skin-friction and Pressure Drag]]"]
status: complete
sources: ["02 - Sources/Tutorial Sheets/Problem Sheet 10 - Drag and Its Sources - External Flows.pdf"]
---

# SESA1016 Problem Sheet 10 - Drag and External Flows Solutions

> [!abstract] Sheet Info
> Seven problems linking boundary-layer profiles, thickness integrals, wake momentum, surface pressure and wind-tunnel corrections.

## Q10.1 Laminar boundary layer on a flat plate

For a laminar flat-plate boundary layer,

$$\delta\approx\frac{5x}{\sqrt{Re_x}},
\qquad
Re_x=\frac{U_\infty x}{\nu}.$$

Using water properties near room temperature, $\nu\approx1.14\times10^{-6}\ \mathrm{m^2\,s^{-1}}$, with $U_\infty=1.5\ \mathrm{m\,s^{-1}}$ and $Re_x=5.0\times10^5$:

$$
x=\frac{Re_x\nu}{U_\infty}
=\boxed{0.38\ \mathrm m},
$$

$$
\delta=\frac{5(0.38)}{\sqrt{5.0\times10^5}}
=\boxed{2.69\ \mathrm{mm}}.
$$

Etching increases disturbance and roughness sensitivity, so transition is likely to occur earlier. The downstream turbulent boundary layer will be thicker and usually exert greater skin friction.

## Q10.2 Polynomial boundary-layer profile

The proposed profile is

$$
f(\eta)=\frac{u}{U_\infty}=2\eta+A\eta^3+B\eta^4+C,
\qquad \eta=y/\delta.
$$

At the wall, no slip requires $f(0)=0$, hence $C=0$. At the edge, velocity matching and zero shear require

$$f(1)=1,\qquad f'(1)=0.$$

Thus

$$A+B=-1,\qquad 3A+4B=-2,$$

and

$$\boxed{A=-2,\quad B=1,\quad C=0}.$$

The displacement thickness is

$$
\delta^*=\delta\int_0^1[1-f(\eta)]\,d\eta
=\boxed{\frac{3}{10}\delta}.
$$

The momentum thickness is

$$
\theta=\delta\int_0^1f(\eta)[1-f(\eta)]\,d\eta
=\boxed{\frac{37}{315}\delta\approx0.1175\delta\approx0.12\delta}.
$$

At the wall,

$$
\tau_w=\mu\left.\frac{du}{dy}\right|_0
=\frac{\mu U_\infty}{\delta}f'(0)
=\frac{2\mu U_\infty}{\delta}.
$$

For air at $20^\circ$C, $\mu=1.81\times10^{-5}\ \mathrm{Pa\,s}$, $U_\infty=30\ \mathrm{m\,s^{-1}}$ and $\delta=0.01$ m:

$$\boxed{\tau_w=0.109\ \mathrm{Pa}}.$$

![[tf_q10_2_boundary_profile.png]]

## Q10.3 Displacement thickness from measured data

Use

$$
\delta^*=\int_0^\infty\left(1-\frac{u}{U_\infty}\right)dy.
$$

The integrand is zero after the measured profile reaches $U_\infty=9.8\ \mathrm{m\,s^{-1}}$, so the finite data range is sufficient. Applying the trapezoidal rule to the supplied millimetre coordinates:

```python
delta_star_mm = np.trapezoid(1 - velocity / 9.8, y_mm)
```

gives

$$\boxed{\delta^*=2.443\ \mathrm{mm}}.$$

As required physically, $\delta^*$ is smaller than the observed $\delta_{99}$ of roughly $5$–$6$ mm.

## Q10.4 Drag reduction from riblets

The Pitot-manometer relation is

$$\frac12\rho_a u^2\approx\rho_wgh.$$

Because both runs have the same free-stream reading $h_\infty=9.8$ mm,

$$\frac{u}{U_\infty}=\sqrt{\frac{h}{h_\infty}}.$$

For a zero-pressure-gradient plate, drag per unit span is proportional to the trailing-edge momentum thickness

$$\theta=\int_0^\infty\frac{u}{U_\infty}
\left(1-\frac{u}{U_\infty}\right)dy.$$

Trapezoidal integration gives

$$
\theta_{base}=0.8202\ \mathrm{mm},\qquad
\theta_{texture}=0.7730\ \mathrm{mm}.
$$

Therefore

$$
\boxed{\text{drag reduction}
=\frac{\theta_{base}-\theta_{texture}}{\theta_{base}}100
=5.8\%}.
$$

The bonus aircraft-fuel estimate cannot be inferred directly from this local skin-friction reduction: total aircraft drag includes pressure, induced, interference and excrescence drag, and mission fuel depends on the full flight profile.

## Q10.5 Pressure drag on a rectangular cylinder

The front pressure varies linearly from $p_{stag}$ at the centreline to $p_{side}$ at the upper and lower edges. Per unit span,

$$
F_{front}=2\left(\frac{p_{side}+p_{stag}}2\right)\frac H2
=33\,920\ \mathrm{N\,m^{-1}}.
$$

The rear pressure is uniform:

$$F_{rear}=p_{back}H=31\,360\ \mathrm{N\,m^{-1}}.$$

Hence

$$\boxed{D_p'=F_{front}-F_{rear}=2560\ \mathrm{N\,m^{-1}}}.$$

Atmospheric reference pressure cancels; using all pressures as either absolute or gauge gives the same net force.

## Q10.6 Pressure drag on a diamond airfoil

Each tap represents a projected chord length $\Delta x=0.02$ m. A face inclined at the half-angle $\varepsilon$ to the chord has length $\Delta x/\cos\varepsilon$ per tap, and the streamwise component of the pressure force on it is $p\,\Delta x\tan\varepsilon$ per unit span. Front-face pressure pushes downstream; rear-face suction also acts downstream. Symmetry doubles the upper-surface result:

$$
D_p'=2\tan\varepsilon\,\Delta x
\left(\sum p_{front}-\sum p_{rear}\right)
=2\tan\varepsilon\times0.02\times(136\,052+22\,650).
$$

The sheet's figure marks the 27° angle between the upper and lower faces at the leading edge, i.e. the included angle, so $\varepsilon=13.5^\circ$:

$$\boxed{D_p'=1.52\ \mathrm{kN\,m^{-1}}},\qquad
\boxed{C_{dp}=\frac{D_p'}{\tfrac12\rho V_\infty^2c}=0.117}.$$

> [!note] Correction
> The earlier version took 27° as the angle of each face to the chord, giving $D_p'=3.23$ kN/m and $C_{dp}=0.248$. That reading makes the aerofoil 51 % thick, and the figure shows the angle as the included angle. No answer is printed for this question, so state the angle convention you use.

## Q10.7 Wind-tunnel buoyancy correction

The water-manometer Pitot readings give

$$q(x)\approx(\rho_w-\rho_a)gh(x).$$

Along the inviscid core, rising dynamic pressure corresponds to falling static pressure:

$$p(x)-p_{ref}=-q(x)+C.$$

A least-squares line through the data gives

$$\boxed{\frac{dp}{dx}=-14.39\ \mathrm{Pa\,m^{-1}}}.$$

The NACA0015 cross-sectional area is approximately $0.103c^2$. With $c=0.6$ m and span $b=1.2$ m,

$$\mathcal V=0.103c^2b=0.04450\ \mathrm{m^3}.$$

The streamwise buoyancy force is

$$
F_b=-\frac{dp}{dx}\mathcal V
=\boxed{0.640\ \mathrm N}
$$

in the downstream direction, so it must be subtracted from the measured drag. Future designs can mitigate it by contouring the test-section area to compensate for boundary-layer displacement, applying wall suction, or shortening the useful test section.

## Related

- [[SESA1016 T14 - Boundary Layers and the Origin of Drag]]
- [[Boundary-layer Thickness Measures]]
- [[Skin-friction and Pressure Drag]]
- [[Pressure Coefficient]]
