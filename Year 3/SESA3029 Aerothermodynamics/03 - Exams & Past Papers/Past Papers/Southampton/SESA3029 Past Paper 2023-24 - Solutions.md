---
title: "SESA3029 Past Paper 2023-24 - Solutions"
module: "SESA3029 Aerothermodynamics"
type: past-paper-solutions
tags: [sesa3029, past-paper, solutions, nozzle, oblique-shock, entropy, prandtl-meyer, moc, shock-reflection, ackeret, wavy-wall, heat-exchanger, finite-difference]
paper: "2023-24"
theory_notes: ["[[SESA3029 W01 - Compressible-Flow Toolkit, Normal Shocks and Pitot Probes]]", "[[SESA3029 W02 - Oblique Shock Relations and Mach Waves]]", "[[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method]]", "[[SESA3029 W04 - Laval Nozzle, Under- and Over-Expanded Flow]]", "[[SESA3029 W05a - Method of Characteristics]]", "[[SESA3029 W07c - Ackeret Theory and Optimum Supersonic Aerofoils]]"]
status: complete
sources: ["03 - Exams & Past Papers/Past Papers/Southampton/SESA3029-202324-01-SESA3029.pdf"]
---

# SESA3029 Past Paper 2023-24 - Solutions

> [!abstract] Paper info
> 2023-24 Semester 1 examination, 120 minutes, with four questions worth 40, 20, 20 and 20 marks and a formula sheet on pp. 7–8. The IFT, NST and OSC are provided, and nearest table values are acceptable; Q1 states that its short parts need no interpolation. The front-page constants are $R=287\ \text{J/(kg K)}$, $c_p=1005\ \text{J/(kg K)}$, $\gamma=1.4$, $\text{Pr}=0.7$, $\rho=1.225\ \text{kg/m}^3$, $\mu=1.79\times10^{-5}\ \text{N s/m}^2$ and $1\ \text{bar}=10^5\ \text{N/m}^2$. Below, each table reading shows the bracketing rows and the interpolation, with the nearest-row answer and the exact value from the relation alongside. Every number was recomputed in Python with $\gamma=1.4$. Q1(viii), Q1(ix) and all of Q4 are heat transfer (Weeks 9–12, not yet lectured).

| Q | Marks | Topic | Theory |
|---|---:|---|---|
| 1(i)–(vii) | 28 | Short questions: nozzle, $\theta_{\max}$, Gibbs/entropy, Prandtl–Meyer, MoC, supersonic aerofoil design | [[SESA3029 W01 - Compressible-Flow Toolkit, Normal Shocks and Pitot Probes|W01]], [[SESA3029 W02 - Oblique Shock Relations and Mach Waves|W02]], [[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method|W03]], [[SESA3029 W05a - Method of Characteristics|W05a]], [[SESA3029 W07c - Ackeret Theory and Optimum Supersonic Aerofoils|W07c]] |
| 1(viii)–(ix) | 12 | Flat-plate convective cooling; 1D radial cylindrical FD stencil | Heat transfer (Weeks 9–12, not yet lectured) |
| 2 | 20 | Mach wave, shock reflection off a flat plate, Mach reflection and SWBLI sketches | [[SESA3029 W02 - Oblique Shock Relations and Mach Waves|W02]], [[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method|W03]] |
| 3 | 20 | Linearised wavy-wall flow ($C_p$ on and off the wall, wave drag) | [[SESA3029 W07c - Ackeret Theory and Optimum Supersonic Aerofoils|W07c]] |
| 4 | 20 | Steam-condensing shell-and-tube heat exchanger ($\varepsilon$–NTU) | Heat transfer (Weeks 9–12, not yet lectured) |

---

## Q1. Short-answer aerothermodynamics questions (40 marks)

### (i) Supersonic wind tunnel test-section state [4 marks]

> A supersonic wind tunnel has stagnation pressure $p_0=2.5\ \text{bar}=250\ \text{kPa}$, stagnation temperature $T_0=420\ \text{K}$ and nozzle area ratio $A/A^*=2.588$. Find the test-section pressure and temperature.

The nozzle is isentropic, so the area ratio fixes the test-section Mach number ([[SESA3029 W04 - Laval Nozzle, Under- and Over-Expanded Flow|W04]]). In the supersonic part of the IFT, $A/A^*=2.5880$ is the entry at $M=2.48$ (the neighbouring rows are $2.5403$ at $M=2.46$ and $2.6367$ at $M=2.50$). That row gives $p/p_0=0.0604$ and $T/T_0=0.4484$, so

$$
p=p_0\left(\frac{p}{p_0}\right)=250\times0.0604=\boxed{15.1\ \text{kPa}\ (0.151\ \text{bar})},
$$

$$
T=T_0\left(\frac{T}{T_0}\right)=420\times0.4484=\boxed{188.3\ \text{K}}.
$$

The exact solution of $A/A^*(M)=2.588$ is $M=2.4800$, $p=15.10$ kPa and $T=188.33$ K.

### (ii) Maximum deflection shock angle vs Mach angle at Mach 3.0 [4 marks]

> A 2D wedge has the largest wedge angle that still gives an attached oblique shock at $M_1=3.0$. Find the shock angle and compare it with the Mach angle.

The largest wedge angle is $\theta_{\max}$, the peak of the $M_1=3.0$ curve on the OSC. The chart reads $\theta_{\max}\approx34^\circ$ at $\beta\approx65^\circ$. Setting $\mathrm{d}\theta/\mathrm{d}\beta=0$ in the θ–β–M relation gives the shock angle at the peak ([[Theta-Beta-Mach Relation]]),

$$
\sin^2\beta_{\max}=\frac{1}{\gamma M_1^2}\left[\frac{\gamma+1}{4}M_1^2-1+\sqrt{(\gamma+1)\left(\frac{\gamma+1}{16}M_1^4+\frac{\gamma-1}{2}M_1^2+1\right)}\right].
$$

With $M_1^2=9$ the first part of the bracket is

$$
\frac{\gamma+1}{4}M_1^2-1=0.6\times9-1=4.4,
$$

and the term under the root is

$$
(\gamma+1)\left(\frac{2.4}{16}\times81+0.2\times9+1\right)=2.4\times(12.15+1.8+1)=2.4\times14.95=35.88.
$$

Substituting,

$$
\sin^2\beta_{\max}=\frac{4.4+\sqrt{35.88}}{1.4\times9}=\frac{4.4+5.9900}{12.6}=\frac{10.3900}{12.6}=0.82460,
$$

$$
\beta_{\max}=\sin^{-1}\sqrt{0.82460}=\sin^{-1}0.90808=\boxed{65.2^\circ}.
$$

Putting $\beta=65.24^\circ$ back into the θ–β–M relation confirms the wedge angle,

$$
\tan\theta_{\max}=2\cot65.24^\circ\,\frac{9\sin^265.24^\circ-1}{9(1.4+\cos130.48^\circ)+2}=0.92240\times\frac{6.42142}{8.75715}=0.67638,
$$

so $\theta_{\max}=34.07^\circ$. The Mach angle is

$$
\mu=\sin^{-1}\frac{1}{M_1}=\sin^{-1}\frac{1}{3.0}=\boxed{19.5^\circ}.
$$

The shock at maximum deflection is $65.2^\circ-19.5^\circ=45.8^\circ$ steeper than the Mach angle, more than three times $\mu$. As the wedge angle rises from zero, the weak shock steepens from a Mach wave at $\beta=\mu$ to $\beta_{\max}$ at $\theta_{\max}$; beyond that the shock detaches.

### (iii) Entropy change from Gibbs' relation [4 marks]

> Starting from $T\,\mathrm{d}s=\mathrm{d}h-v\,\mathrm{d}p$ with $v=1/\rho$, show that $s_2-s_1=c_p\ln(T_2/T_1)-R\ln(p_2/p_1)$.

The gas is calorically perfect, so $\mathrm{d}h=c_p\,\mathrm{d}T$ with constant $c_p$, and it obeys $p=\rho RT$ ([[Entropy Change Across a Shock]]). Dividing Gibbs' relation by $T$,

$$
\mathrm{d}s=\frac{\mathrm{d}h}{T}-\frac{v}{T}\,\mathrm{d}p.
$$

Replacing $\mathrm{d}h$ by $c_p\,\mathrm{d}T$,

$$
\mathrm{d}s=c_p\frac{\mathrm{d}T}{T}-\frac{v}{T}\,\mathrm{d}p.
$$

The equation of state gives $v/T=1/(\rho T)=R/p$, so

$$
\mathrm{d}s=c_p\frac{\mathrm{d}T}{T}-R\frac{\mathrm{d}p}{p}.
$$

Integrating from state 1 to state 2 with constant $c_p$ and $R$,

$$
\int_{s_1}^{s_2}\mathrm{d}s=c_p\int_{T_1}^{T_2}\frac{\mathrm{d}T}{T}-R\int_{p_1}^{p_2}\frac{\mathrm{d}p}{p},
$$

$$
\boxed{s_2-s_1=c_p\ln\frac{T_2}{T_1}-R\ln\frac{p_2}{p_1}}.
$$

### (iv) Entropy jump across a normal shock with M₂ = 0.43 [4 marks]

> Using the result of (iii), find $s_2-s_1$ across a normal shock with downstream Mach number $M_2=0.43$.

The NST is read backwards in the $M_2$ column. The value 0.43 lies between two rows.

| $M_1$ | $M_2$ | $p_2/p_1$ | $T_2/T_1$ |
|---:|---:|---:|---:|
| 4.18 | 0.4304 | 20.2178 | 4.3339 |
| 4.20 | 0.4299 | 20.4133 | 4.3666 |

The fraction is $(0.4304-0.43)/(0.4304-0.4299)=0.0004/0.0005=0.8$, so

$$
M_1=4.18+0.8\times0.02=4.196,
$$

$$
\frac{T_2}{T_1}=4.3339+0.8\times(4.3666-4.3339)=4.3339+0.0262=4.3601,
$$

$$
\frac{p_2}{p_1}=20.2178+0.8\times(20.4133-20.2178)=20.2178+0.1564=20.3742.
$$

Substituting into the result of (iii),

$$
s_2-s_1=1005\ln4.3601-287\ln20.3742=1005\times1.47249-287\times3.01427=1479.9-865.1=\boxed{615\ \text{J/(kg K)}}.
$$

The nearest row ($M_1=4.20$) gives $1481.4-865.7=615.7$ J/(kg K), which is also acceptable.

> [!check] Exact root and stagnation-pressure route
> Solving $M_2(M_1)=0.43$ gives $M_1=4.1973$, $T_2/T_1=4.3622$ and $p_2/p_1=20.3874$, so $s_2-s_1=615.1$ J/(kg K). The adiabatic-shock form $s_2-s_1=-R\ln(p_{02}/p_{01})$ with $p_{02}/p_{01}=0.11759$ gives $-287\ln0.11759=614.3$ J/(kg K); the two differ by 0.1 % because $\gamma=1.4$ makes $c_p=3.5R=1004.5$ rather than the front-page 1005.

### (v) Prandtl–Meyer expansion from Mach 4 over a 10° convex corner [4 marks]

> A Mach 4.0 flow expands around a $10^\circ$ convex corner. Find the downstream Mach number.

The IFT row $M=4.00$ gives $\nu_1=65.7848^\circ$ ([[Prandtl-Meyer Function]]). The expansion turn adds to $\nu$,

$$
\nu_2=\nu_1+\Delta\theta=65.7848^\circ+10^\circ=75.7848^\circ.
$$

The target lies between two IFT rows.

| $M$ | $\nu$ |
|---:|---:|
| 4.88 | $75.7752^\circ$ |
| 4.90 | $75.9691^\circ$ |

The fraction is $(75.7848-75.7752)/(75.9691-75.7752)=0.0096/0.1939=0.050$, so

$$
M_2=4.88+0.02\times0.050=4.881\approx\boxed{4.88}.
$$

The nearest row is also 4.88, and the exact inverse is 4.8810.

### (vi) Point state from Riemann invariants [4 marks]

> Point $P$ in a MoC nozzle calculation lies on characteristics with $R^+=14^\circ$ and $R^-=26^\circ$. Find $M_P$ and $\theta_P$.

With the module's $R^+=\nu-\theta$ and $R^-=\nu+\theta$ ([[Riemann Invariants]]), adding and subtracting the two invariants gives

$$
\nu_P=\frac{R^-+R^+}{2}=\frac{26^\circ+14^\circ}{2}=20.0^\circ,
$$

$$
\theta_P=\frac{R^--R^+}{2}=\frac{26^\circ-14^\circ}{2}=\boxed{6.0^\circ}.
$$

With Anderson's signs ($K^+=\theta-\nu$) the same data would give $\theta_P=-6^\circ$, so the convention should be stated in the answer. The value $\nu=20.0^\circ$ lies between two IFT rows.

| $M$ | $\nu$ |
|---:|---:|
| 1.76 | $19.5646^\circ$ |
| 1.78 | $20.1458^\circ$ |

The fraction is $(20.0-19.5646)/(20.1458-19.5646)=0.4354/0.5812=0.749$, so

$$
M_P=1.76+0.02\times0.749=1.775\approx\boxed{1.78}.
$$

The nearest row is 1.78 and the exact inverse is 1.7750.

### (vii) Efficient supersonic aerofoil design features [4 marks]

> What design features would you recommend for an aerofoil section that operates efficiently in supersonic flight, and why?

In supersonic flow the drag that matters is wave drag, so every feature aims to keep the waves weak ([[SESA3029 W07c - Ackeret Theory and Optimum Supersonic Aerofoils#9. Thickness drag and the optimum section|W07c §9]], [[Supersonic Wave Drag]]). A sharp leading edge lets the bow shock stay attached and oblique. A blunt nose holds a detached bow shock with a near-normal section in front of it, where the stagnation-pressure loss and the drag are large. A sharp trailing edge likewise avoids a base region.

The section should be thin. In Ackeret theory the thickness wave drag grows with the square of the thickness ratio; for a double wedge it is $C_{D,w}=4(t/c)^2/\sqrt{M_\infty^2-1}$. Halving $t/c$ therefore quarters this drag, and structural stiffness sets the lower limit. For a given $t/c$, the double wedge with its maximum thickness at mid-chord gives the least thickness drag.

Camber should be small or zero. In linear supersonic theory the lift depends only on the angle of attack, so camber adds wave drag in proportion to the mean of $(\mathrm{d}y_c/\mathrm{d}x)^2$ and gives no lift in return. Symmetric diamond or biconvex sections are the usual choice.

On the wing as a whole, sweeping the leading edge behind the Mach cone ($M_\infty\cos\Lambda<1$) makes the flow normal to the leading edge subsonic, which allows a rounder, lower-drag leading edge and reduces wave drag at supersonic cruise.

### (viii) Flat-plate convective cooling by high-pressure air [6 marks]

> Cooling air at $p=2\ \text{bar}$ and $T_\infty=800\ \text{K}$ flows at $U=30\ \text{m/s}$ over a flat plate. With a uniform wall heat flux $\dot q_w=60\ \text{kW/m}^2$, estimate the wall temperature at $x=0.3\ \text{m}$ from the leading edge.

This is heat transfer (Weeks 9–12, not yet lectured); check the notation against those lectures when they are written up.

The density follows from the ideal-gas law at the given state,

$$
\rho=\frac{p}{RT_\infty}=\frac{2\times10^5}{287\times800}=0.8711\ \text{kg/m}^3.
$$

No property table is given, so $\mu$ and $\text{Pr}$ are the front-page values. The conductivity follows from the definition of the Prandtl number,

$$
k=\frac{\mu c_p}{\text{Pr}}=\frac{1.79\times10^{-5}\times1005}{0.7}=0.02570\ \text{W/(m K)}.
$$

The local Reynolds number at $x=0.3$ m is

$$
Re_x=\frac{\rho Ux}{\mu}=\frac{0.8711\times30\times0.3}{1.79\times10^{-5}}=4.380\times10^5.
$$

This is below the transition value $5\times10^5$, so the boundary layer is laminar. The formula-sheet correlation for a laminar boundary layer with uniform wall heat flux gives the local Nusselt number,

$$
Nu_x=0.453\,Re_x^{1/2}\,\text{Pr}^{1/3}=0.453\times(4.380\times10^5)^{0.5}\times0.7^{1/3}=0.453\times661.80\times0.8879=266.2.
$$

The local heat transfer coefficient is

$$
h_x=\frac{Nu_x\,k}{x}=\frac{266.2\times0.02570}{0.3}=22.80\ \text{W/(m}^2\text{ K)}.
$$

The air cools the plate, so heat flows from the wall into the stream and $T_w>T_\infty$,

$$
T_w=T_\infty+\frac{\dot q_w}{h_x}=800+\frac{60\,000}{22.80}=800+2631=\boxed{3431\ \text{K}}.
$$

The result is far hotter than any real plate could survive, which comes from the large flux and the room-temperature properties; see [[#Paper slips and ambiguities]].

### (ix) 1D radial cylindrical finite-difference equation [6 marks]

> Derive the steady finite-difference equation for $T_i$ at an interior node of an equidistant radial grid ($r_i=i\,\Delta r$) with no volumetric generation, using $\dot q_r=-2\pi kr\,\dfrac{\partial T}{\partial r}$.

This is heat transfer (Weeks 9–12, not yet lectured). The same question is [[SESA3029 Past Paper 2024-25 B - Solutions#Q5. Finite-difference stencils for 2D internal corner and 1D radial cylindrical conduction (16 marks)|2024-25 Paper B Q5(ii)]].

$\dot q_r$ is the heat flow per unit axial length through a cylinder of radius $r$. The control volume around node $i$ is the annulus between the faces $r_{i\pm1/2}=(i\pm\tfrac12)\Delta r$, and in steady state with no generation

$$
\dot q_{r,\,i-1/2}-\dot q_{r,\,i+1/2}=0.
$$

The gradient at each face is the difference between the nodes on either side of it,

$$
\dot q_{r,\,i-1/2}=-2\pi k\left(i-\tfrac12\right)\Delta r\,\frac{T_i-T_{i-1}}{\Delta r}=-2\pi k\left(i-\tfrac12\right)(T_i-T_{i-1}),
$$

$$
\dot q_{r,\,i+1/2}=-2\pi k\left(i+\tfrac12\right)\Delta r\,\frac{T_{i+1}-T_i}{\Delta r}=-2\pi k\left(i+\tfrac12\right)(T_{i+1}-T_i).
$$

Substituting into the balance and dividing by $2\pi k$,

$$
-\left(i-\tfrac12\right)(T_i-T_{i-1})+\left(i+\tfrac12\right)(T_{i+1}-T_i)=0.
$$

Expanding the brackets,

$$
\left(i-\tfrac12\right)T_{i-1}-\left(i-\tfrac12\right)T_i-\left(i+\tfrac12\right)T_i+\left(i+\tfrac12\right)T_{i+1}=0.
$$

The two $T_i$ coefficients add to $2i$,

$$
\left(i-\tfrac12\right)T_{i-1}-2i\,T_i+\left(i+\tfrac12\right)T_{i+1}=0,
$$

$$
\boxed{T_i=\frac{\left(i-\tfrac12\right)T_{i-1}+\left(i+\tfrac12\right)T_{i+1}}{2i}}.
$$

---

## Q2. Mach wave, oblique shock reflection and increased generator angle (20 marks)

> A flat plate in a wind tunnel produces a weak leading-edge Mach wave at $\phi=30^\circ$ from viscous effects. A shock generator of angle $\theta_g=10^\circ$ produces an oblique shock at angle $\beta$ that reflects from the plate as a wave at angle $\psi$ to the plate.
> (i) Deduce $M_1$ and $\beta$. [4]
> (ii) Given $M_2=1.64$ and $p_2=80\ \text{kPa}$ behind the incident shock, find $p_3$, $M_3$ and $\psi$ for a regular reflection. [10]
> (iii) Give two reasons why the wave pattern becomes substantially different as $\theta_g$ increases, with an annotated sketch for each. [6]

![[at_pp_202324_q2_reflection_regimes.png|900]]

### (i) Upstream Mach number and incident shock angle [4 marks]

The leading-edge wave is a Mach wave, so its angle is the Mach angle of the oncoming flow, $\phi=\mu_1=30^\circ$ ([[Mach Waves and Mach Angle]]),

$$
M_1=\frac{1}{\sin\mu_1}=\frac{1}{\sin30^\circ}=\boxed{2.00}.
$$

The shock generator deflects the flow by $\theta_g=10^\circ$. The OSC at $M_1=2.0$, $\theta=10^\circ$ reads $\beta\approx39^\circ$ on the weak branch. Solving the θ–β–M relation by trial ($M_1^2=4$).

| $\beta$ | $M_1^2\sin^2\beta-1$ | $M_1^2(\gamma+\cos2\beta)+2$ | $2\cot\beta$ | $\tan\theta$ | $\theta$ |
|---:|---:|---:|---:|---:|---:|
| $39^\circ$ | 0.58418 | 8.43165 | 2.46979 | 0.17112 | $9.7102^\circ$ |
| $40^\circ$ | 0.65270 | 8.29459 | 2.38351 | 0.18756 | $10.6229^\circ$ |

$$
\beta=39^\circ+1^\circ\times\frac{10-9.7102}{10.6229-9.7102}=39^\circ+1^\circ\times\frac{0.2898}{0.9127}=39.318^\circ.
$$

At $39.318^\circ$ the relation returns $\theta=10.003^\circ$, and a secant step gives the exact root $39.314^\circ$,

$$
\beta=\boxed{39.3^\circ}.
$$

> [!check] The given M₂ follows from this shock
> $M_{n1}=2.0\sin39.314^\circ=1.2671$. Between NST rows 1.26 ($M_{n2}=0.8071$) and 1.28 ($0.7963$) the fraction is 0.355, so $M_{n2}=0.8071-0.355\times0.0108=0.8033$. Then $M_2=0.8033/\sin29.314^\circ=0.8033/0.48959=1.641$, which matches the $M_2=1.64$ given in (ii).

### (ii) Regular reflection off the flat plate [10 marks]

Behind the incident shock the flow is inclined at $\theta_g=10^\circ$ towards the plate. The plate forces it back to horizontal, so the reflected shock must turn the region-2 flow through $10^\circ$ ([[Regular Shock Reflection]]). The trial solution at $M_2=1.64$ ($M_2^2=2.6896$) is

| $\beta$ | $M_2^2\sin^2\beta-1$ | $M_2^2(\gamma+\cos2\beta)+2$ | $2\cot\beta$ | $\tan\theta$ | $\theta$ |
|---:|---:|---:|---:|---:|---:|
| $49^\circ$ | 0.53196 | 5.39112 | 1.73857 | 0.17155 | $9.7344^\circ$ |
| $50^\circ$ | 0.57832 | 5.29840 | 1.67820 | 0.18318 | $10.3801^\circ$ |

$$
\beta_r=49^\circ+1^\circ\times\frac{10-9.7344}{10.3801-9.7344}=49^\circ+1^\circ\times\frac{0.2656}{0.6457}=49.411^\circ.
$$

At $49.411^\circ$ the relation returns $\theta=10.004^\circ$, and a secant step gives the exact root $\beta_r=49.405^\circ$. This angle is measured from the region-2 flow, which points $10^\circ$ down towards the plate, so the angle to the plate is

$$
\psi=\beta_r-\theta_g=49.405^\circ-10^\circ=\boxed{39.4^\circ}.
$$

The normal Mach number into the reflected shock is

$$
M_{n,r}=M_2\sin\beta_r=1.64\sin49.405^\circ=1.64\times0.75933=1.2453.
$$

The NST rows that bracket it are 1.24 and 1.26.

| $M_{n1}$ | $M_{n2}$ | $p_2/p_1$ |
|---:|---:|---:|
| 1.24 | 0.8183 | 1.6272 |
| 1.26 | 0.8071 | 1.6855 |

The fraction is $(1.2453-1.24)/0.02=0.265$, so

$$
M_{n3}=0.8183+0.265\times(0.8071-0.8183)=0.8183-0.0030=0.8153,
$$

$$
\frac{p_3}{p_2}=1.6272+0.265\times(1.6855-1.6272)=1.6272+0.0155=1.6426.
$$

The region-3 flow is parallel to the plate, at $\psi$ to the reflected shock, so

$$
M_3=\frac{M_{n3}}{\sin\psi}=\frac{0.8153}{\sin39.405^\circ}=\frac{0.8153}{0.63480}=\boxed{1.284},
$$

$$
p_3=1.6426\times80\ \text{kPa}=\boxed{131.4\ \text{kPa}}.
$$

With nearest rows only ($M_{n,r}\to1.24$) the answers are $M_3=0.8183/0.63480=1.289$ and $p_3=1.6272\times80=130.2$ kPa. The exact normal-shock relations give $M_{n3}=0.8153$ and $p_3/p_2=1.6426$, the same as the interpolation.

### (iii) Changes as the shock generator angle increases [6 marks]

Panels (b) and (c) of the figure above are the two sketches.

The first change is the switch from regular to Mach reflection. A larger $\theta_g$ makes the incident shock stronger, so $M_2$ falls, while the reflected shock still has to turn the flow through $\theta_g$. The maximum deflection an attached shock can give falls with $M_2$, and the two curves cross at $\theta_g\approx12.9^\circ$ for $M_1=2.0$, where $M_2=1.53$ and $\theta_{\max}(M_2)=12.9^\circ$. Above this angle no regular reflection exists. A near-normal Mach stem stands on the plate instead, with a subsonic region behind it, and a slip line runs downstream from the triple point between the gas that crossed the stem and the gas that crossed the incident and reflected shocks ([[Mach Reflection]]). At still larger angles, $\theta_g>\theta_{\max}(2.0)=23.0^\circ$, the shock on the generator itself detaches and the tunnel may choke.

The second change comes from the boundary layer on the plate, whose presence the viscous Mach wave at the leading edge already shows. The reflection imposes a pressure rise $p_3/p_2$ on that boundary layer, and the rise grows with $\theta_g$. The pressure rise travels upstream through the subsonic part of the boundary layer, and once it is large enough the layer separates ahead of the impingement point. The separation bubble deflects the outer flow, which produces a separation shock where the layer lifts off, an expansion fan where the incident shock meets the top of the bubble, and compression waves where the flow reattaches. This is a shock-wave/boundary-layer interaction, and the clean two-shock pattern of Figure Q.2 is lost.

---

## Q3. Linearised supersonic flow over a wavy wall (20 marks)

> The skin of a supersonic fuselage is modelled as a wavy wall of length $L=1\ \text{m}$ with profile $y=h\sin(2\pi nx)$, $h=0.002\ \text{m}$, $n=3$, in flow at $M_1=2$. Small angles may be assumed and Ackeret's method used. Given $\int_0^1\sin^2(2\pi nx)\,\mathrm{d}x=\int_0^1\cos^2(2\pi nx)\,\mathrm{d}x=\tfrac12$:
> (i) Sketch $C_p(x)$ (a) on the wavy surface and (b) along the line A–B at $y_{AB}=0.289\ \text{m}$, giving $C_p$ at $(0,0)$ and $(0.5,0.289)$. [12]
> (ii) Find the wave drag coefficient based on $L$. [8]

![[at_pp_202324_q3_wavy_wall.png|900]]

### (i) Pressure coefficient on the wall and along y = 0.289 m [12 marks]

At $M_1=2$ the Ackeret factor and the Mach angle are

$$
\lambda=\sqrt{M_1^2-1}=\sqrt{4-1}=\sqrt3=1.7321,\qquad\mu_1=\sin^{-1}\frac12=30^\circ.
$$

For small slopes the local flow angle of the wall is its slope,

$$
\theta(x)=\frac{\mathrm{d}y}{\mathrm{d}x}=2\pi nh\cos(2\pi nx)=2\pi\times3\times0.002\cos(6\pi x)=0.03770\cos(6\pi x).
$$

On the wall, Ackeret's formula $C_p=2\theta/\lambda$ gives ([[Ackeret Theory]])

$$
C_p(x,0)=\frac{4\pi nh}{\sqrt{M_1^2-1}}\cos(2\pi nx)=\frac{0.024\pi}{\sqrt3}\cos(6\pi x)=0.04353\cos(6\pi x).
$$

This is a cosine of amplitude 0.0435 with three cycles over the plate. It peaks where the wall slopes most steeply upwards into the flow ($x=0,\tfrac13,\tfrac23,1$) and is most negative on the steepest downslopes. The pressure is therefore a quarter-wavelength ahead of the wall shape, high on the front of each crest and low on the back, which is why the wall has drag. At the start of the wall,

$$
C_p(0,0)=0.04353\cos0=\boxed{+0.0435}.
$$

Away from the wall, linear supersonic theory carries each disturbance unchanged along the Mach line that leaves the wall upwards and downstream at $\mu_1=30^\circ$ to the stream. A disturbance made at $x_w$ reaches height $y$ at $x=x_w+y\cot\mu_1=x_w+\lambda y$, so

$$
C_p(x,y)=C_p(x-\lambda y,\,0),
$$

with $C_p=0$ wherever $x-\lambda y<0$, ahead of the first Mach wave from the start of the wall. On the line A–B that first wave arrives at

$$
x=\lambda y_{AB}=0.289\sqrt3=0.5006\ \text{m}\approx0.5\ \text{m}.
$$

Ahead of it, for $0\le x<0.5$ m, the flow is undisturbed and $C_p=0$. Behind it, for $0.5<x\le1$ m,

$$
C_p(x,y_{AB})=0.04353\cos\big(6\pi(x-0.5)\big)=0.04353\cos(6\pi x-3\pi)=-0.04353\cos(6\pi x),
$$

which is the wall distribution delayed by 0.5 m: one and a half cycles over the second half of A–B. The point $(0.5,0.289)$ lies on the first Mach wave itself, where $C_p$ jumps from $\boxed{0}$ just ahead of it to $\boxed{+0.0435}$ just behind it. Taken literally, $0.5-0.289\sqrt3=-0.0006$ m places the point just ahead of the wave, where $C_p=0$; the question's $y_{AB}=0.289$ is $0.5/\sqrt3$ rounded, chosen to put the point on the wave.

### (ii) Wave drag coefficient [8 marks]

On a surface element of slope $\mathrm{d}y/\mathrm{d}x$ the pressure force has a streamwise component $p\,\mathrm{d}y=p\,(\mathrm{d}y/\mathrm{d}x)\,\mathrm{d}x$ per unit span. The free-stream part integrates to $p_\infty[y(L)-y(0)]=0$, so only the perturbation pressure contributes, and

$$
C_{D,w}=\frac{1}{L}\int_0^LC_p(x,0)\,\frac{\mathrm{d}y}{\mathrm{d}x}\,\mathrm{d}x.
$$

Substituting both distributions with $L=1$ m,

$$
C_{D,w}=\int_0^1\left[\frac{4\pi nh}{\sqrt{M_1^2-1}}\cos(2\pi nx)\right]\left[2\pi nh\cos(2\pi nx)\right]\mathrm{d}x.
$$

Collecting the constants,

$$
C_{D,w}=\frac{8\pi^2n^2h^2}{\sqrt{M_1^2-1}}\int_0^1\cos^2(2\pi nx)\,\mathrm{d}x.
$$

The given integral is $\tfrac12$, so

$$
C_{D,w}=\frac{4\pi^2n^2h^2}{\sqrt{M_1^2-1}}=\frac{4\pi^2\times3^2\times0.002^2}{\sqrt3}=\frac{1.4212\times10^{-3}}{1.7321}=\boxed{8.21\times10^{-4}}.
$$

> [!check] General Ackeret form
> For any thin surface, Ackeret theory gives $C_D=\dfrac{2}{\lambda}\cdot\dfrac{1}{L}\displaystyle\int_0^L\theta^2\,\mathrm{d}x$ for one side. The mean of $\theta^2$ here is $\tfrac12\times0.03770^2=7.106\times10^{-4}$, and $\tfrac{2}{1.7321}\times7.106\times10^{-4}=8.21\times10^{-4}$.

---

## Q4. Steam-condensing shell-and-tube heat exchanger (20 marks)

> Saturated steam at atmospheric pressure ($T_s=100^\circ\text{C}$, $h_{fg}=2257\ \text{kJ/kg}$) condenses on the outside of thin-walled tubes in a one-shell, two-tube-pass exchanger ($D=14\ \text{mm}$, $0.5\ \text{m}$ per pass, outer coefficient $h_o=21\,800\ \text{W/(m}^2\text{ K)}$). Cooling water enters at $15^\circ\text{C}$ with mean velocity $3.5\ \text{m/s}$; for water $\rho=998\ \text{kg/m}^3$, $c_p=4181\ \text{J/(kg K)}$, $\mu=9.59\times10^{-4}\ \text{N s/m}^2$, $k=0.603\ \text{W/(m K)}$, $\text{Pr}=6.62$.
> (i) Find the tube Reynolds number and the combined heat transfer coefficient $h'$. [5]
> (ii) Using $\varepsilon=\dfrac{1-\exp[-\text{NTU}(1+C_r)]}{1+C_r}$, find the number of tubes needed to condense $2.3\ \text{kg/s}$ of steam, and their total surface area. [10]
> (iii) Find the water outlet temperature and the largest steam condensation rate possible under ideal conditions with the same water flow rate and inlet temperature. [5]

This is heat transfer (Weeks 9–12, not yet lectured); check the notation against those lectures when they are written up.

### (i) Tube Reynolds number and combined heat transfer coefficient [5 marks]

The Reynolds number in a tube is

$$
Re_D=\frac{\rho vD}{\mu}=\frac{998\times3.5\times0.014}{9.59\times10^{-4}}=\frac{48.902}{9.59\times10^{-4}}=\boxed{5.10\times10^4}.
$$

This is well above 2300, so the flow is turbulent. The water is being heated, so the formula-sheet Dittus–Boelter correlation takes $n=0.4$,

$$
Nu_D=0.023\,Re_D^{4/5}\,\text{Pr}^{0.4}=0.023\times50\,993^{0.8}\times6.62^{0.4}=0.023\times5834.5\times2.1298=285.8.
$$

The inner coefficient is

$$
h_i=\frac{Nu_D\,k}{D}=\frac{285.8\times0.603}{0.014}=12\,310\ \text{W/(m}^2\text{ K)}.
$$

The tubes are thin-walled, so the wall resistance is neglected and the inner and outer resistances add in series,

$$
\frac{1}{h'}=\frac{1}{h_i}+\frac{1}{h_o}=\frac{1}{12\,310}+\frac{1}{21\,800}=8.123\times10^{-5}+4.587\times10^{-5}=1.2710\times10^{-4}\ \text{m}^2\text{ K/W},
$$

$$
h'=\frac{1}{1.2710\times10^{-4}}=\boxed{7868\ \text{W/(m}^2\text{ K)}}.
$$

### (ii) Number of tubes and total surface area [10 marks]

The steam condenses at a fixed $100^\circ$C, so its heat capacity rate is effectively infinite and

$$
C_r=\frac{C_{\min}}{C_{\max}}=0.
$$

With $C_r=0$ the given relation reduces to

$$
\varepsilon=1-\exp(-\text{NTU}).
$$

Each tube runs through both passes, so it is $2\times0.5=1.0$ m long, and the water velocity fixes its flow rate. The flow area, mass flow, heat capacity rate and surface area of one tube are

$$
A_c=\frac{\pi D^2}{4}=\frac{\pi\times0.014^2}{4}=1.5394\times10^{-4}\ \text{m}^2,
$$

$$
\dot m_1=\rho vA_c=998\times3.5\times1.5394\times10^{-4}=0.5377\ \text{kg/s},
$$

$$
C_1=\dot m_1c_p=0.5377\times4181=2248.2\ \text{W/K},
$$

$$
A_1=\pi D\times1.0\ \text{m}=\pi\times0.014\times1.0=0.04398\ \text{m}^2.
$$

With $N$ tubes, both $h'A$ and $C_c$ are $N$ times the single-tube values, so $N$ cancels from NTU,

$$
\text{NTU}=\frac{h'NA_1}{NC_1}=\frac{7868\times0.04398}{2248.2}=\frac{346.0}{2248.2}=0.15392,
$$

$$
\varepsilon=1-e^{-0.15392}=1-0.85734=0.14266.
$$

The heat that must be removed to condense 2.3 kg/s of steam is

$$
\dot Q=\dot m_sh_{fg}=2.3\times2.257\times10^6=5.1911\times10^6\ \text{W}.
$$

The exchanger delivers $\dot Q=\varepsilon C_c(T_s-T_{c,\text{in}})$ with $C_c=NC_1$, so

$$
N=\frac{\dot Q}{\varepsilon C_1(T_s-T_{c,\text{in}})}=\frac{5.1911\times10^6}{0.14266\times2248.2\times(100-15)}=\frac{5.1911\times10^6}{27\,261}=190.4.
$$

A whole number of tubes is needed, and 190 would fall slightly short, so

$$
N=\boxed{191\ \text{tubes}},
$$

$$
A=NA_1=191\times0.04398=\boxed{8.40\ \text{m}^2}.
$$

Each of these tubes makes both passes; with straight tubes the same exchanger has 191 tubes in each pass.

### (iii) Outlet water temperature and maximum steam condensation rate [5 marks]

For $C_r=0$ the effectiveness is the water's temperature rise as a fraction of the largest possible rise, $\varepsilon=(T_{c,\text{out}}-T_{c,\text{in}})/(T_s-T_{c,\text{in}})$, so

$$
T_{c,\text{out}}=T_{c,\text{in}}+\varepsilon(T_s-T_{c,\text{in}})=15+0.14266\times(100-15)=15+12.13=\boxed{27.1^\circ\text{C}}.
$$

Under ideal conditions ($\varepsilon\to1$) the water would leave at $100^\circ$C. With the same 191 tubes, the water capacity rate and the ideal heat transfer are

$$
C_c=NC_1=191\times2248.2=429\,400\ \text{W/K},
$$

$$
\dot Q_{\max}=C_c(T_s-T_{c,\text{in}})=429\,400\times85=3.650\times10^7\ \text{W}.
$$

The steam that this heat would condense is

$$
\dot m_{s,\max}=\frac{\dot Q_{\max}}{h_{fg}}=\frac{3.650\times10^7}{2.257\times10^6}=\boxed{16.2\ \text{kg/s}}.
$$

With the unrounded $N=190.4$ this becomes $\dot m_s/\varepsilon=2.3/0.14266=16.1$ kg/s.

> [!check] Water-side energy balance
> With 191 tubes the water flow is $191\times0.5377=102.7$ kg/s. Heating it by $12.13$ K takes $102.7\times4181\times12.13=5.21\times10^6$ W, enough to condense $5.21\times10^6/2.257\times10^6=2.31$ kg/s, just above the required 2.3 kg/s.

---

## Paper slips and ambiguities

- Q1(viii): no air properties at 800 K are given, so the front-page $\mu=1.79\times10^{-5}$ N s/m² and $\text{Pr}=0.7$ (room-temperature values) are used with the ideal-gas density at 2 bar and 800 K, which gives $T_w=3431$ K. Sutherland's law gives $\mu(800\ \text{K})=3.62\times10^{-5}$ N s/m². With that viscosity, $k=\mu c_p/\text{Pr}=0.052$ W/(m K), $Re_x=2.16\times10^5$ (still laminar), $h_x=32.4$ W/(m² K), $\Delta T=1849$ K and $T_w=2649$ K. Either way the wall is impossibly hot, so the 60 kW/m² flux is not realistic for this flow. The wording "cooling air" means the air removes heat from a hotter wall, so $T_w>T_\infty$.
- Q3(i): $y_{AB}\sqrt{M_1^2-1}=0.289\sqrt3=0.5006$ m, so the point $(0.5,0.289)$ is 0.6 mm ahead of the first Mach wave if the numbers are taken literally. The intended value is $y_{AB}=0.5/\sqrt3$, which puts the point on the jump from $C_p=0$ to $C_p=+0.0435$.
- Q4(ii): the paper prints the parallel-flow relation $\varepsilon=[1-\exp(-\text{NTU}(1+C_r))]/(1+C_r)$ for a one-shell, two-pass exchanger. With condensing steam $C_r=0$, and every exchanger type reduces to $\varepsilon=1-e^{-\text{NTU}}$, so the mismatch does not change the answer.
- Corrections to the earlier draft of this note: in Q2(iii) the generator angle above which regular reflection is impossible at $M_1=2.0$ was given as $15.1^\circ$; the correct value is $12.9^\circ$ (where $\theta_{\max}(M_2)=\theta_g$ with $M_2=1.53$). In Q4(i) the intermediate values are $Re_D^{0.8}=5834.5$ and $\text{Pr}^{0.4}=2.1298$, not 5828.4 and 2.1322 ($Nu_D=285.8$ was right). In Q4(iii) the boxed $\dot m_{s,\max}$ now uses the 191 tubes actually fitted (16.2 kg/s; the earlier 16.1 kg/s used the unrounded 190.4).
