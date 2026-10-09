---
title: "SESA2028 Structures Tutorial 4 - Buckling Solutions"
module: "SESA2028 Aerospace Materials & Structures"
type: tutorial-solution
stream: "Structures"
order: 4
tags: [sesa2028, structures, tutorial, buckling, beam-column]
status: complete
parent: ["[[SESA2028 Aerospace Materials & Structures Hub]]"]
topics: ["[[SESA2028 S5 - Euler Buckling and Effective Length]]", "[[SESA2028 S6 - Imperfect Columns, Beam-Columns and Plate Buckling]]"]
sources: ["02 - Sources/SESA2028 green coursework book.pdf, pp. 48-50"]
---

# SESA2028 Structures Tutorial 4 - Buckling Solutions

## Q1 - Eccentrically loaded tubular column

For $D_o=60$ mm and $D_i=50$ mm,

$$
A=\frac\pi4(D_o^2-D_i^2)=863.94\ \mathrm{mm^2},
$$

$$
I=\frac\pi{64}(D_o^4-D_i^4)=3.2938\times10^5\ \mathrm{mm^4}.
$$

### 1. Euler load

The column is pin-ended, so $K=1$:

$$
P_E=\frac{\pi^2EI}{L^2}
=\frac{\pi^2(210{,}000)(3.2938\times10^5)}{2800^2}
=\boxed{87.08\ \mathrm{kN}}.
$$

The corresponding average stress is

$$
\sigma_E=\frac{P_E}{A}
=\boxed{100.79\ \mathrm{MPa}}.
$$

It is below the yield stress, so ideal elastic buckling precedes uniform crushing.

### 2. Deflection at $P=50$ kN

For a constant eccentricity $e=6$ mm,

$$
\mu=\sqrt{\frac{P}{EI}}=8.502\times10^{-4}\ \mathrm{mm^{-1}},
$$

$$
v_{max}=e\left[\sec\left(\frac{\mu L}{2}\right)-1\right].
$$

Here $\sec(\mu L/2)=2.6927$, so

$$
\boxed{v_{max}=10.16\ \mathrm{mm}}.
$$

### 3. Maximum compressive stress

The maximum moment is

$$
M_{max}=Pe\sec\left(\frac{\mu L}{2}\right).
$$

At $c=D_o/2=30$ mm,

$$
\sigma_{max}=-\frac PA-\frac{M_{max}c}{I}
=\boxed{-131.45\ \mathrm{MPa}}.
$$

The average direct stress alone is only $-57.9$ MPa; the rest is second-order bending.

## Q2 - Permissible initial curvature of a control rod

For $d=12$ mm,

$$
A=\frac{\pi d^2}{4}=113.10\ \mathrm{mm^2},\qquad
I=\frac{\pi d^4}{64}=1017.88\ \mathrm{mm^4}.
$$

The Euler load is

$$
P_E=\frac{\pi^2EI}{L^2}=723.31\ \mathrm N.
$$

The required safety factor gives an allowable stress

$$
\sigma_{allow}=\frac{430}{3}=143.33\ \mathrm{MPa}.
$$

For a sinusoidal initial curvature $a_0\sin(\pi x/L)$, the total midspan amplitude is

$$
a=\frac{a_0}{1-P/P_E}.
$$

The maximum compressive stress is

$$
\sigma_{max}=\frac PA+\frac{Pa c}{I},\qquad c=6\ \mathrm{mm}.
$$

Set this equal to $\sigma_{allow}$ and solve for $a_0$:

$$
a_0=\left(\sigma_{allow}-\frac PA\right)
\frac{I}{Pc}\left(1-\frac P{P_E}\right)
=\boxed{6.65\ \mathrm{mm}}.
$$

The load is already $83\%$ of the Euler load, which explains the strong imperfection sensitivity.

## Q3 - Water-filled C-channel beam-column

Using a $250\times2$ mm base and two $2\times148$ mm webs,

$$
A_s=1092\ \mathrm{mm^2},\qquad
\bar y=41.66\ \mathrm{mm}
$$

above the bottom surface, and

$$
I_{zz}=2.6055\times10^6\ \mathrm{mm^4}.
$$

The water area is

$$
A_w=(246)(148)=36{,}408\ \mathrm{mm^2}.
$$

Including steel self-weight and water,

$$
w=g(\rho_sA_s+\rho_wA_w)=441.3\ \mathrm{N/m}.
$$

### 1. No axial load

For a simply supported beam under full-span UDL,

$$
v_{max}=\frac{5wL^4}{384EI}
=\boxed{2.82\ \mathrm{mm}}.
$$

The maximum moment is

$$
M_0=\frac{wL^2}{8}=882.5\ \mathrm{Nm}.
$$

The top fibre is $150-41.66=108.34$ mm from the centroid, giving

$$
\sigma_{max}=\frac{M_0c}{I}
=\boxed{36.7\ \mathrm{MPa}},
$$

$$
\boxed{SF=240/36.7=6.54}.
$$

### 2. With $P=20$ kN

Let $\mu=\sqrt{P/(EI)}$. Solving

$$
EIv''+Pv=M_0(x),\qquad M_0(x)=\frac{wx(L-x)}2
$$

with $v(0)=v(L)=0$ gives the midspan magnitude

$$
v_{max}=\frac{wEI}{P^2}
\left[\sec\left(\frac{\mu L}{2}\right)-1\right]
-\frac{wL^2}{8P}.
$$

Substitution gives

$$
\boxed{v_{max}=3.01\ \mathrm{mm}}.
$$

The second-order maximum moment is

$$
M_{max}=M_0+Pv_{max}=942.7\ \mathrm{Nm}.
$$

Combining direct compression and bending,

$$
\sigma_{max}=-\frac PA-\frac{M_{max}c}{I}
=\boxed{-57.5\ \mathrm{MPa}},
$$

$$
\boxed{SF=240/57.5=4.17}.
$$

## Q4.1 - Pin-ended column under a midspan transverse load

By symmetry, analyse $0\le x\le L/2$. The left reaction is $W/2$, so the first-order moment is $Wx/2$. The beam-column equation is

$$
EIv''+Pv=\frac{Wx}{2},\qquad \mu^2=\frac{P}{EI}.
$$

The solution is

$$
v=A\sin\mu x+B\cos\mu x+\frac{W}{2P}x.
$$

At the pin, $v(0)=0$, so $B=0$. Symmetry requires $v'(L/2)=0$:

$$
A\mu\cos\left(\frac{\mu L}{2}\right)+\frac{W}{2P}=0.
$$

Hence

$$
A=-\frac{W}{2P\mu\cos(\mu L/2)}.
$$

Substitution at midspan gives, in magnitude,

$$
\boxed{v_{max}=\frac{W}{2P}
\left[\frac1\mu\tan\left(\frac{\mu L}{2}\right)-\frac L2\right]}.
$$

The maximum moment follows from $M=P v+Wx/2$ at $x=L/2$:

$$
\boxed{M_{max}=\frac{W}{2\mu}\tan\left(\frac{\mu L}{2}\right)}.
$$

Therefore

$$
\boxed{\sigma_{max}=-\frac PA-
\frac{W}{2\mu}\tan\left(\frac{\mu L}{2}\right)\frac yI}.
$$

## Q4.2 - Numerical beam-column solution

For $L=1500$ mm, $d=25$ mm, $E=210$ GPa and $P=16$ kN,

$$
A=490.87\ \mathrm{mm^2},\qquad
I=1.9175\times10^4\ \mathrm{mm^4},
$$

$$
\mu=1.9934\times10^{-3}\ \mathrm{mm^{-1}}.
$$

With $W=40$ N,

$$
\boxed{v_{max}=7.32\ \mathrm{mm}},
$$

$$
M_{max}=132.15\ \mathrm{Nm},\qquad
\boxed{\sigma_{max}=-118.7\ \mathrm{MPa}}.
$$

Setting the stress magnitude equal to $240$ MPa and solving the linear expression for $W$ gives

$$
\boxed{W=96.3\ \mathrm N}.
$$

## Q4.3 - Approximation using an equivalent initial curvature

Without axial load, the midspan displacement caused by $W$ is

$$
a_0=\frac{WL^3}{48EI}.
$$

Treat this as a sinusoidal initial imperfection. Under the axial load,

$$
v_{max}=\frac{a_0}{1-P/P_E},
\qquad
P_E=\frac{\pi^2EI}{L^2}.
$$

For $W=40$ N,

$$
\boxed{v_{max}=7.42\ \mathrm{mm}}.
$$

The maximum moment includes the original first-order moment and the axial-load contribution:

$$
M_{max}=\frac{WL}{4}+Pv_{max}.
$$

Thus

$$
\boxed{\sigma_{max}=-119.7\ \mathrm{MPa}}.
$$

Solving for yield gives

$$
\boxed{W=95.2\ \mathrm N}.
$$

The approximation is within about $1\%$ because the simply supported point-load deflection resembles the first sine buckling mode. The exact and approximate shapes are not identical, so perfect agreement should not be expected.

