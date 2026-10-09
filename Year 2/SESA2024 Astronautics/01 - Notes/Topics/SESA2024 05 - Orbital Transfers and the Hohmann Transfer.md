---
title: "SESA2024 05 - Orbital Transfers and the Hohmann Transfer"
module: "SESA2024 Astronautics"
type: topic
stream: "Mission Analysis"
order: 5
tags:
  - sesa2024
  - orbital-mechanics
  - hohmann-transfer
  - delta-v
aliases: ["Hohmann transfer", "Impulsive manoeuvres", "Chapter 5 Lectures 11-13"]
date: 2026-09-25
status: complete
parent: ["[[SESA2024 Astronautics Hub]]"]
prerequisites: ["[[SESA2024 04 - Orbital Energy and the Vis-Viva Equation]]"]
next_topics: ["[[SESA2024 06 - Attitude Control]]"]
key_concepts: ["[[Hohmann Transfer]]", "[[Vis-Viva Equation]]", "[[Tsiolkovsky Rocket Equation]]"]
tutorial_sheets: ["[[SESA2024 Workbook Ch5 - Mission Analysis Solutions]]"]
sources: ["02 - Sources/Lectures/Chapter 5/SESA2024 Astronautics - Chapter 5_Hohman transfers_V2.pdf", "02 - Sources/Lectures/Chapter 5/SESA2024 Astronautics - Chapter 5_Hohman transfers worked example_V1.pdf"]
---

# SESA2024 05 - Orbital Transfers and the Hohmann Transfer

> [!abstract] Summary
> An **impulsive** burn changes speed but not position. The burn point is therefore common to the old and new orbits, and a single burn can only reach an *intersecting* orbit.
>
> The **Hohmann transfer** is the minimum-ΔV, two-burn transfer between coplanar circles:
> 1. a tangential burn at $r_1$ enters an ellipse with $2a_T = r_1+r_2$;
> 2. a second tangential burn at $r_2$ circularises.
>
> Each ΔV is a difference of two vis-viva speeds. The transfer time is half the ellipse's period. The rocket equation then turns ΔV into propellant mass.

## Key Concepts
- [[Hohmann Transfer]] · [[Vis-Viva Equation]] · [[Tsiolkovsky Rocket Equation]]

---

## 1. Impulsive-manoeuvre assumptions
1. **High thrust, short duration**: ΔV is acquired before the spacecraft moves far along its orbit.
2. **Small flight-path angle** $\gamma$.

Together these make gravity loss negligible, so the **field-free rocket equation** applies:

$$
\Delta V = V_{ex}\ln\frac{M_0}{M_b},\qquad M_b = M_0-M_f
$$

**Consequences**:
- The burn point belongs to **both** orbits.
- Non-intersecting orbits need **at least two burns**.
- $\Delta V = |\mathbf V_{new}-\mathbf V_{old}|$ at the common point. It is a *vector* difference, but tangential burns reduce it to a subtraction of speeds.

## 2. The RemoveDebris deployment quiz
RemoveDebris was pushed out of the ISS **backwards** (opposite to the ISS velocity).
- **Which orbit?** The orbits must intersect at the deployment point, and energy is removed. So the new orbit is **smaller and elliptical**, with its apogee at the deployment point. (Option B.)
- **Relative motion?** Smaller $a$ means a shorter period (Kepler 3), so RemoveDebris drifts **ahead and below** the ISS. (Option C.)

> [!tip] The counter-intuitive rule
> - Push **forwards**: higher orbit, longer period, so the object **falls behind and rises above**. (2018/19 Q1(viii): the cosmonaut throws a satellite forwards; answer D.)
> - Push **backwards**: the object moves **ahead and below**.
> - The same logic answers 2022/23 A6 (explosion fragments on a Gabbard-type plot): the forward-kicked fragment A has a longer period and higher apogee; the backward-kicked fragment B has a shorter period and lower perigee.

## 3. The Hohmann transfer
Start on a circle $r_1$ with $V_1 = \sqrt{\mu/r_1}$.

**Burn 1 (at perigee of the transfer ellipse, in the direction of $V_1$)**:

$$
2a_T = r_1+r_2,\qquad V_{Tp} = \sqrt{\mu\Big(\frac{2}{r_1}-\frac{1}{a_T}\Big)},\qquad \Delta V_{Tp} = V_{Tp}-V_1
$$

**Burn 2 (at apogee, in the direction of $V_2$)**:

$$
V_{Ta} = \sqrt{\mu\Big(\frac{2}{r_2}-\frac{1}{a_T}\Big)},\qquad V_2 = \sqrt{\frac{\mu}{r_2}},\qquad \Delta V_{Ta} = V_2-V_{Ta}
$$

$$
\Delta V = \Delta V_{Tp}+\Delta V_{Ta},\qquad t_{transfer} = \frac{\tau_T}{2} = \pi\sqrt{\frac{a_T^3}{\mu}}
$$

**Closed forms** (2015/16, 2017/18 and workbook Q3 derivations), with $x = r_1/r_2$:

$$
\Delta V_1 = \sqrt{\frac{\mu}{r_1}}\left(\sqrt{\frac{2r_2}{r_1+r_2}}-1\right),\qquad \Delta V_2 = \sqrt{\frac{\mu}{r_2}}\left(1-\sqrt{\frac{2r_1}{r_1+r_2}}\right)
$$

$$
\Delta V = V_1\left[\sqrt{\frac{2}{x+1}}(1-x)+\sqrt x-1\right]
$$

**Apogee kick into GEO from a GTO** (2018/19 Q2(iv)): $\Delta V = \sqrt{\mu/r_a}\left(1-\sqrt{2r_p/(r_p+r_a)}\right)$.

## 4. Worked example (L13): 200 km → GEO
$r_1$ = 6578 km, $r_2$ = 42 164 km, so $a_T$ = 24 371 km.

| Quantity | Value |
|---|---|
| $V_1$ (circular, 200 km) | 7.784 km/s |
| $V_{Tp}$ | 10.239 km/s |
| **$\Delta V_1$** | **2.455 km/s** |
| $V_{Ta}$ | 1.597 km/s |
| $V_{GEO}$ | 3.075 km/s |
| **$\Delta V_2$** | **1.478 km/s** |
| **Total** | **3.933 km/s** |
| Transfer time $\pi\sqrt{a_T^3/\mu}$ | 18 932 s = **5.26 h** |

**Fuel for burn 2** with $V_{ex}$ = 2.5 km/s: $x = M_0/M_b = e^{1.478/2.5} = 1.805$, so

$$
\frac{M_f}{M_0} = \frac{x-1}{x} = \mathbf{0.45}
$$

Almost half the mass arriving at apogee is burnt to circularise.

![[ast_hohmann_leo_geo.png|560]]

## 5. How the cost scales
![[ast_hohmann_dv_ratio.png|600]]

- Total ΔV/$V_1$ **peaks at $r_2/r_1\approx15.6$** (0.536). Beyond that, a Hohmann transfer costs *more* than escape ($\sqrt2-1 = 0.414$ for the first burn alone). A bi-elliptic transfer becomes cheaper.
- $\Delta V_1\to(\sqrt2-1)V_1$ as $r_2\to\infty$ (escape).

## 6. Hohmann for interplanetary missions
- ✔ Minimum ΔV (fuel).
- ✘ Long transfer times: Earth→Saturn takes about 6 years; Uranus about 16; Neptune about 30. It needs planetary phasing (launch windows), and it assumes circular, coplanar planetary orbits.
- In a heliocentric transfer the launch vehicle provides $\Delta V_1$ (the departure $V_\infty$). The spacecraft provides $\Delta V_2$ on arrival (2017/18 Q2).

## 7. Small-ΔV Hohmann (orbit maintenance)
For $r_2 = r_1+\Delta r$ with $\Delta r\ll r$:

$$
\Delta V_{total}\approx\frac{V\,\Delta r}{2r}
$$

This is how drag make-up burns are sized in [[SESA2024 14 - Orbit Control, Drag and Payload Data Rate]]. Examples: 3.4 km at 7072 km gives 1.80 m/s (2024/25 B3); 56.6 m at 6997 km gives 0.031 m/s (workbook 11B Q1).

## Links
- Parent: [[SESA2024 Astronautics Hub]] · Previous: [[SESA2024 04 - Orbital Energy and the Vis-Viva Equation]] · Next: [[SESA2024 06 - Attitude Control]]
- Propellant: [[SESA2024 07 - Spacecraft Propulsion]] · SESA2023: [[Tsiolkovsky Rocket Equation]]

## Sources
- Chapter 5 Lecture 11 (orbital transfers), Lecture 13 (Hohmann worked example)
