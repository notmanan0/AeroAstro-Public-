---
title: "SESA2028 Structures Tutorial 5 - Continuum Mechanics Solutions"
module: "SESA2028 Aerospace Materials & Structures"
type: tutorial-solution
stream: "Structures"
order: 5
tags: [sesa2028, structures, tutorial, continuum-mechanics, thick-cylinder]
status: complete
parent: ["[[SESA2028 Aerospace Materials & Structures Hub]]"]
topics: ["[[SESA2028 S9 - Continuum Mechanics in Cylindrical Coordinates]]", "[[SESA2028 S10 - Thick Cylinders and Shrink Fits]]"]
sources: ["02 - Sources/SESA2028 green coursework book.pdf, pp. 51-52"]
---

# SESA2028 Structures Tutorial 5 - Continuum Mechanics Solutions

## Q1 - Thick cylinder under internal and external pressure

Given

$$
r_i=100\ \mathrm{mm},\quad r_o=150\ \mathrm{mm},\quad
p_i=60\ \mathrm{MPa},\quad p_o=30\ \mathrm{MPa},
$$

Lamé's constants are

$$
A=\frac{p_ir_i^2-p_or_o^2}{r_o^2-r_i^2}
=\frac{60(100^2)-30(150^2)}{150^2-100^2}
=-6\ \mathrm{MPa},
$$

$$
B=\frac{(p_i-p_o)r_i^2r_o^2}{r_o^2-r_i^2}
=5.40\times10^5\ \mathrm{MPa\,mm^2}.
$$

The stresses are

$$
\sigma_{rr}=A-\frac{B}{r^2},\qquad
\sigma_{\theta\theta}=A+\frac{B}{r^2}.
$$

At $r_i$,

$$
\boxed{\sigma_{rr}=-60\ \mathrm{MPa}},\qquad
\boxed{\sigma_{\theta\theta}=48\ \mathrm{MPa}}.
$$

At $r_o$,

$$
\boxed{\sigma_{rr}=-30\ \mathrm{MPa}},\qquad
\boxed{\sigma_{\theta\theta}=18\ \mathrm{MPa}}.
$$

The attached end caps give the uniform longitudinal stress

$$
\sigma_{zz}=\frac{p_ir_i^2-p_or_o^2}{r_o^2-r_i^2}
=\boxed{-6\ \mathrm{MPa}}.
$$

![[Figures/structures_thick_cylinder_lame_stress.png]]

## Q2 - Maximum pressure and diameter change

Here

$$
r_i=80\ \mathrm{mm},\qquad r_o=160\ \mathrm{mm},\qquad p_o=10\ \mathrm{MPa}.
$$

The bore hoop stress is

$$
\sigma_{\theta\theta}(r_i)
=\frac{p_i(r_i^2+r_o^2)-2p_or_o^2}{r_o^2-r_i^2}.
$$

Set this equal to the allowable $30$ MPa:

$$
30=\frac{p_i(80^2+160^2)-2(10)(160^2)}{160^2-80^2}.
$$

Therefore

$$
\boxed{p_{i,max}=34\ \mathrm{MPa}}.
$$

At this pressure,

$$
A=-2.0\ \mathrm{MPa},\qquad
B=2.048\times10^5\ \mathrm{MPa\,mm^2}.
$$

Because the cylinder has closed ends, $\sigma_{zz}=A$. The circumferential strain at the outer surface is

$$
\varepsilon_{\theta}(r_o)
=\frac1E\left[\sigma_{\theta\theta}
-\nu(\sigma_{rr}+\sigma_{zz})\right]_{r_o}.
$$

At $r_o$, $\sigma_{\theta\theta}=6$ MPa, $\sigma_{rr}=-10$ MPa and $\sigma_{zz}=-2$ MPa, so

$$
\varepsilon_{\theta}(r_o)
=\frac{6-0.29(-12)}{207{,}000}
=4.580\times10^{-5}.
$$

The change in outside diameter is

$$
\Delta D_o=D_o\varepsilon_{\theta}
=320(4.580\times10^{-5})
=\boxed{0.0147\ \mathrm{mm}=14.7\ \mu m}.
$$

## Q3 - Contact pressure in a shrink fit

The inner tube has radii $a=25$ mm and $b=50$ mm. The outer tube has radii $b=50$ mm and $c=75$ mm. Let the unknown contact pressure be $p$.

For the inner tube under external pressure, the inward displacement magnitude at $b$ is

$$
\frac{|u_i(b)|}{p}
=\frac{b}{E}
\frac{(1-\nu)b^2+(1+\nu)a^2}{b^2-a^2}.
$$

For the outer tube under internal pressure, the outward displacement at $b$ is

$$
\frac{u_o(b)}{p}
=\frac{b}{E}
\frac{(1-\nu)b^2+(1+\nu)c^2}{c^2-b^2}.
$$

Compatibility requires the two radial movements to remove the radial interference:

$$
\delta_r=u_o(b)-u_i(b)=0.01\ \mathrm{mm}.
$$

For the equal-modulus geometry in this problem, the Poisson-ratio terms cancel in the summed compliance. With $E=208{,}000$ MPa,

$$
\frac{\delta_r}{p}=1.0256\times10^{-3}\ \mathrm{mm/MPa}.
$$

Therefore

$$
p=\frac{0.01}{1.0256\times10^{-3}}
=\boxed{9.75\ \mathrm{MPa}\approx9.74\ \mathrm{MPa}}.
$$

This pressure acts externally on the inner tube and internally on the outer tube. The radial stress is continuous at the interface, while the hoop stress changes from compression in the inner tube to tension in the outer tube.

![[Figures/structures_shrink_fit_residual_stress.png]]

