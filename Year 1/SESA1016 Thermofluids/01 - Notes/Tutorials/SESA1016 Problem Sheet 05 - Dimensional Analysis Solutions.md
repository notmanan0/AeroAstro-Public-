---
title: "SESA1016 Problem Sheet 05 - Dimensional Analysis Solutions"
module: "SESA1016 Thermofluids"
type: tutorial
stream: "Part B: Fluid Mechanics"
tags: [sesa1016, tutorial-solutions, dimensional-analysis, similarity]
sheet: "Problem Sheet 05 - Dimensional Analysis"
theory_notes: ["[[SESA1016 T6 - Dimensional Analysis and Similarity]]"]
key_concepts: ["[[Buckingham Pi Theorem]]", "[[Reynolds Number]]"]
status: complete
sources: ["02 - Sources/Tutorial Sheets/Problem Sheet 05 - Dimensional Analysis.pdf"]
---

# SESA1016 Problem Sheet 05 - Dimensional Analysis Solutions

> [!abstract] Sheet Info
> Five model-testing problems. The durable method is always the same: list the variables, write their dimensions, select repeating variables, form independent $\Pi$ groups, then match every dynamically important group between model and prototype.

## Q5.1 Wind loading on a building

Let the overturning moment depend on air density $\rho$, building height $H$ and the atmospheric velocity gradient $G=dV/dz$:

$$T=f(\rho,H,G).$$

Since $[T]=ML^2T^{-2}$, $[\rho]=ML^{-3}$ and $[G]=T^{-1}$, the single dimensionless group is

$$
\Pi_T=\frac{T}{\rho G^2H^5},
\qquad
\boxed{T=C\rho G^2H^5}.
$$

For a 1:100 model, $H_p/H_m=100$, $G_p/G_m=0.30$ and $\rho_p/\rho_m=1$. With $T_m=0.03\ \mathrm{N\,m}$,

$$
\frac{T_p}{T_m}
=\frac{\rho_p}{\rho_m}
\left(\frac{G_p}{G_m}\right)^2
\left(\frac{H_p}{H_m}\right)^5,
$$

$$
\boxed{T_p=0.03(0.30)^2(100)^5=2.7\times10^7\ \mathrm{N\,m}}.
$$

For a local pressure rise $\Delta p=f(\rho,G,H,z)$,

$$
\boxed{\frac{\Delta p}{\rho G^2H^2}=F\left(\frac{z}{H}\right)}.
$$

At corresponding positions $z/H$, a measured model rise of $0.10$ Pa scales as

$$
\Delta p_p=0.10(0.30)^2(100)^2
=\boxed{90\ \mathrm{Pa}}.
$$

> [!tip] Scaling lesson
> Force-like quantities often scale strongly with size; a moment carries one additional length and here scales as $H^5$. Pressure scales only as $H^2$.

## Q5.2 Propeller thrust

Take $T=f(\rho,\omega,D,V,\beta)$, with pitch angle $\beta$ already dimensionless. Using $\rho$, $\omega$ and $D$ as repeating variables gives

$$
\boxed{\frac{T}{\rho\omega^2D^4}
=F\left(\frac{V}{\omega D},\beta\right)}.
$$

The sheet's conventional propeller form uses rotation rate $n$ in revolutions per second:

$$
C_T=\frac{T}{\rho n^2D^4},
\qquad
J=\frac{V}{nD},
\qquad C_T=F(J,\beta).
$$

### (b) Similar propeller test

Matching advance ratio and pitch angle makes $C_T$ equal. With the same fluid,

$$
\frac{T_p}{T_m}
=\left(\frac{n_p}{n_m}\right)^2
\left(\frac{D_p}{D_m}\right)^4.
$$

Hence

$$
T_p=1.2\left(\frac{6000}{5000}\right)^2(2.25)^4
=\boxed{44.3\ \mathrm{kN}}.
$$

### (c) Reading the supplied thrust chart

For $V=225\ \mathrm{m\,s^{-1}}$, $D=2.25$ m and $n=6000/60=100\ \mathrm{s^{-1}}$,

$$J=\frac{225}{100(2.25)}=1.00.$$

At $J=1.0$ and $\beta=30^\circ$, the chart gives $C_T\approx0.10$. Therefore

$$
T=C_T\rho n^2D^4
=0.10(1.25)(100)^2(2.25)^4
=\boxed{32.0\ \mathrm{kN}}.
$$

## Q5.3 Vortex shedding

Frequency $f$, pile diameter $d$ and speed $V$ form the Strouhal number

$$
\boxed{St=\frac{fd}{V}}.
$$

Assuming $St$ is Reynolds-independent and equal for model and prototype,

$$
\frac{f_md_m}{V_m}=\frac{f_pd_p}{V_p}.
$$

With $d_m=d_p/12$, $V_m=0.6\ \mathrm{m\,s^{-1}}$, $V_p=6\ \mathrm{m\,s^{-1}}$ and $f_p=2.3$ Hz,

$$
f_m=f_p\frac{V_m}{V_p}\frac{d_p}{d_m}
=2.3(0.1)(12)
=\boxed{2.76\ \mathrm{Hz}}.
$$

## Q5.4 Spinning golf ball

For lift coefficient $C_L$, the dimensional inputs are $\rho,V,d,\mu,\omega$. Buckingham's theorem leaves two independent groups:

$$
\boxed{C_L=F\left(\frac{\rho Vd}{\mu},\frac{\omega d}{V}\right)
=F(Re,\text{spin ratio})}.
$$

The first group controls viscous regime; the second measures surface rotational speed relative to the flight speed and therefore the strength of the Magnus effect.

## Q5.5 Water-tunnel model of a car

Let drag depend on density, viscosity, speed, car length and surface roughness:

$$D=f(\rho,\mu,V,L,s).$$

A convenient result is

$$
\boxed{\frac{D}{\rho V^2L^2}=F\left(Re_L,\frac{s}{L}\right)},
\qquad Re_L=\frac{\rho VL}{\mu}.
$$

Exact similarity requires both Reynolds number and relative roughness to match. With $L_m=L_p/5$,

$$
\frac{V_pL_p}{\nu_{air}}=\frac{V_m(L_p/5)}{\nu_{water}},
$$

$$
\boxed{\frac{V_p}{V_m}=\frac{\nu_{air}}{5\nu_{water}}\approx3.0}
$$

using $\nu_{air}\approx1.5\times10^{-5}$ and $\nu_{water}\approx1.0\times10^{-6}\ \mathrm{m^2\,s^{-1}}$ near room temperature. Thus the full-size road speed is about three times the water-tunnel speed.

## Exam-ready checklist

1. Angles, coefficients and geometry ratios are already dimensionless.
2. Similar geometry alone is not dynamic similarity.
3. Match the $\Pi$ groups before applying any force or moment scale factor.
4. Keep $n$ and $\omega=2\pi n$ consistent; changing convention changes the numerical coefficient.

## Related

- [[SESA1016 T6 - Dimensional Analysis and Similarity]]
- [[Buckingham Pi Theorem]]
- [[Reynolds Number]]
- [[SESA1016 Formula Sheet]]

