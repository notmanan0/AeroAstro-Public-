---
title: "SESA2028 Structures Tutorial 3 - Torsion Solutions"
module: "SESA2028 Aerospace Materials & Structures"
type: tutorial-solution
stream: "Structures"
order: 3
tags: [sesa2028, structures, tutorial, torsion]
status: complete
parent: ["[[SESA2028 Aerospace Materials & Structures Hub]]"]
topics: ["[[SESA2028 S3 - Shear Flow and Shear Centre]]", "[[SESA2028 S4 - Torsion of Thin-Walled Sections]]"]
sources: ["02 - Sources/SESA2028 green coursework book.pdf, pp. 45-47"]
---

# SESA2028 Structures Tutorial 3 - Torsion Solutions

## Q1 - Symmetric closed hexagon

The median-line area is a $140\times300$ mm rectangle plus two triangles:

$$
A_m=140(300)+2\left(\frac12\,140\,150\right)=63{,}000\ \mathrm{mm^2}.
$$

Each inclined wall has length

$$
\ell=\sqrt{150^2+70^2}=165.53\ \mathrm{mm},
$$

so the median-line perimeter is

$$
s=2(300)+4(165.53)=1262.1\ \mathrm{mm}.
$$

For constant thickness $t=3$ mm,

$$
J=\frac{4A_m^2}{\oint ds/t}
=\frac{4(63{,}000)^2}{1262.1/3}
=\boxed{3.77\times10^7\ \mathrm{mm^4}}.
$$

The cell flow under $T=50$ kNm is

$$
q=\frac{T}{2A_m}=\frac{50\times10^6}{2(63{,}000)}
=396.8\ \mathrm{N/mm}.
$$

Therefore

$$
\tau=\frac qt=\boxed{132\ \mathrm{MPa}},
\qquad
SF=\frac{350}{132}=\boxed{2.65}.
$$

Finally,

$$
\frac{d\phi}{dx}=\frac{T}{GJ}
=\frac{50\times10^6}{79{,}000(3.77\times10^7)}
=1.68\times10^{-5}\ \mathrm{rad/mm},
$$

or

$$
\boxed{\frac{d\phi}{dx}=0.017\ \mathrm{rad/m}=0.96^\circ/\mathrm m}.
$$

## Q2 - Wing-like single-cell section

The median-line area is

$$
A_m=\frac12(1000)(140)+(450)(140)+\frac12\pi(70)^2
=140{,}697\ \mathrm{mm^2}.
$$

The two tapered walls have length $\sqrt{1000^2+70^2}=1002.45$ mm. Hence

$$
\oint\frac{ds}{t}
=\frac{2(1002.45)}{1.5}+\frac{2(450)}2+\frac{\pi(70)}3.
$$

Thus

$$
J=\frac{4A_m^2}{\oint ds/t}
=\boxed{4.26\times10^7\ \mathrm{mm^4}}.
$$

The thinnest skin, $t_{min}=1.5$ mm, reaches yield first. Since $q=T/(2A_m)$,

$$
T_{max}=2A_mt_{min}\tau_y
=2(140{,}697)(1.5)(330)
=\boxed{139\ \mathrm{kNm}}.
$$

For $T=20$ kNm, $L=6.5$ m and $G=27$ GPa,

$$
\phi=\frac{TL}{GJ}
=\frac{20\times10^6(6500)}{27{,}000(4.26\times10^7)}
=\boxed{0.113\ \mathrm{rad}\approx6.5^\circ}.
$$

## Q3 - Open cruciform

For the four thin strips, the total median-line length is $80+50=130$ mm. Therefore

$$
J=\frac13(130)t^3.
$$

For an open thin strip, $\tau_{max}\approx Tt/J$. The allowable stress is

$$
\tau_{allow}=\frac{400}{3}=133.33\ \mathrm{MPa}.
$$

Set $Tt/J=\tau_{allow}$:

$$
\frac{50{,}000t}{(130/3)t^3}=133.33
\quad\Rightarrow\quad
t=\boxed{2.94\ \mathrm{mm}\approx3\ \mathrm{mm}}.
$$

Using the unrounded thickness,

$$
J=\boxed{1.10\times10^3\ \mathrm{mm^4}}.
$$

The twist rate is

$$
\frac{d\phi}{dx}=\frac{50{,}000}{79{,}000(1.10\times10^3)}
=\boxed{0.57\ \mathrm{rad/m}=32.9^\circ/\mathrm m}.
$$

## Q4 - Closed tube versus the same tube with a slit

The mean radius is $r\approx26.5$ mm and the thickness is $t=3$ mm. For the closed tube,

$$
J_c\approx2\pi r^3t,\qquad
\tau_c=\frac{T}{2\pi r^2t}.
$$

After a longitudinal slit, treat the circumference as an open strip of length $2\pi r$:

$$
J_o\approx\frac13(2\pi r)t^3,\qquad
\tau_o\approx\frac{Tt}{J_o}.
$$

Therefore

$$
\frac{\tau_o}{\tau_c}\approx\frac{3r}{t}\approx26.5,
$$

which becomes the sheet's more exact

$$
\boxed{\tau_{cut}/\tau_{closed}\approx25}.
$$

The twist ratio is the inverse stiffness ratio:

$$
\frac{\phi_{cut}}{\phi_{closed}}=\frac{J_c}{J_o}
\approx3\left(\frac rt\right)^2
=\boxed{235}.
$$

The slit increases both stress and twist; it does not provide a harmless manufacturing convenience.

![[Figures/structures_open_vs_closed_torsion.png]]

## Q5 - Open circular top-hat

Add the torsional constants of the two flat legs and the semicircular strip:

$$
J=\frac13\left[2(50)(2.5)^3+\pi(60)(5)^3\right]
=\boxed{8375\ \mathrm{mm^4}}.
$$

With $L=2250$ mm, $T=40$ Nm and $G=27{,}000\ \mathrm{MPa}$,

$$
\phi=\frac{TL}{GJ}
=\frac{40{,}000(2250)}{27{,}000(8375)}
=\boxed{0.398\ \mathrm{rad}=22.8^\circ}.
$$

The thick curved strip governs the open-section maximum stress. With $SF=1.5$,

$$
\tau_{allow}=300/1.5=200\ \mathrm{MPa},
$$

$$
T_{max}=\frac{\tau_{allow}J}{t_{max}}
=\frac{200(8375)}5
=\boxed{335\ \mathrm{Nm}}.
$$

## Q6 - Eccentrically loaded L-section

The open-section torsional constant is

$$
J=\frac13\left[100(2.5)^3+200(5)^3\right]
=\boxed{8854\ \mathrm{mm^4}}.
$$

Using non-overlapping rectangles and the parallel-axis theorem gives

$$
\boxed{I_{zz}=5.33\times10^6\ \mathrm{mm^4}},
$$

$$
\boxed{I_{yy}=7.10\times10^5\ \mathrm{mm^4}},
\qquad
\boxed{I_{yz}=1.00\times10^6\ \mathrm{mm^4}}.
$$

The clean way to handle the loading is superposition:

1. move $Q_y=1.8$ kN to the shear centre;
2. retain the force through the shear centre and add the torque $T=Q_ye$;
3. calculate the bending shear flow from the general unsymmetric formula;
4. calculate the open-section torsional stress from $Tt/J$ on each leg;
5. add the signed stresses point by point.

The two components reinforce on the web close to the corner. The maximum is

$$
\boxed{\tau_{max}=104.2\ \mathrm{MPa}}
$$

at

$$
\boxed{y=25.9\ \mathrm{mm},\qquad z=7.5\ \mathrm{mm}}.
$$

Checking bending shear and torsional shear separately before adding them is essential; adding magnitudes everywhere would give the wrong location and an over-conservative distribution.

