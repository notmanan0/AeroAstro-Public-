---
title: "SESA3029 Past Paper 2021-22 - Solutions"
module: "SESA3029 Aerothermodynamics"
type: past-paper-solutions
tags: [sesa3029, past-paper, solutions, compressible-flow, oblique-shock, shock-expansion, ackeret, prandtl-glauert, moc, dual-bell, finite-difference]
paper: "2021-22"
theory_notes: ["[[SESA3029 W01 - Compressible-Flow Toolkit, Normal Shocks and Pitot Probes]]", "[[SESA3029 W02 - Oblique Shock Relations and Mach Waves]]", "[[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method]]", "[[SESA3029 W04 - Laval Nozzle, Under- and Over-Expanded Flow]]", "[[SESA3029 W05a - Method of Characteristics]]", "[[SESA3029 W05b - Minimum-Length Nozzle Design]]", "[[SESA3029 W07b - Compressible Potential Flow and the Prandtl-Glauert Transformation]]", "[[SESA3029 W07c - Ackeret Theory and Optimum Supersonic Aerofoils]]"]
status: complete
sources: ["03 - Exams & Past Papers/Past Papers/Southampton/SESA3029-202122-01-SESA3029.pdf"]
---

# SESA3029 Past Paper 2021-22 - Solutions

> [!abstract] Paper info
> 2021-22 Semester 1 Assessment: 120 minutes, three questions worth 40, 30 and 30 marks, with a formula sheet on pp. 6–7 and the isentropic and normal-shock tables and oblique-shock chart provided. The front page gives $R=287\ \text{J/(kg K)}$, $c_p=1004.5\ \text{J/(kg K)}$, $\gamma=1.4$, $\rho=1.225\ \text{kg/m}^3$ and $\mu=1.8\times 10^{-5}\ \text{N s/m}^2$. Nearest table values are acceptable unless a question says otherwise, so each answer gives the interpolated or exact value and, where it differs, the nearest-row value. Every number was recomputed in Python. Question 3 is heat transfer (Weeks 9–12, not yet lectured).

| Q | Marks | Topic | Theory |
|---|---:|---|---|
| 1 | 40 | Short compressible-flow parts, critical Mach number, flat plate by shock-expansion and Ackeret, wall reflection | [[SESA3029 W01 - Compressible-Flow Toolkit, Normal Shocks and Pitot Probes|W01]], [[SESA3029 W02 - Oblique Shock Relations and Mach Waves|W02]], [[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method|W03]], [[SESA3029 W07b - Compressible Potential Flow and the Prandtl-Glauert Transformation|W07b]], [[SESA3029 W07c - Ackeret Theory and Optimum Supersonic Aerofoils|W07c]] |
| 2 | 30 | Planar dual-bell minimum-length nozzle ($M_i=1.6$, $M_e=2.7$) and its back-pressure regimes | [[SESA3029 W04 - Laval Nozzle, Under- and Over-Expanded Flow|W04]], [[SESA3029 W05a - Method of Characteristics|W05a]], [[SESA3029 W05b - Minimum-Length Nozzle Design|W05b]] |
| 3 | 30 | Transient 1D rod cooling by explicit finite differences, with grid extrapolation. Heat transfer (Weeks 9–12, not yet lectured) | Not yet lectured |

---

## Q1. Compressible flow, critical Mach number, and flat plate (40 marks)

> (i) A pitot-static probe measures $p=84.8\ \text{kPa}$, $p_0=122\ \text{kPa}$, and $T=243\ \text{K}$. Find the flow velocity in $\text{m/s}$. [4]
> (ii) A converging-diverging nozzle has design exit Mach number $M_e=4.5$ at $p_e=12\ \text{kPa}$. Find the throat pressure in $\text{kPa}$. [4]
> (iii) A Mach $1.5$ flow expands around a $15^\circ$ corner forming an expansion fan. Find the angle of the trailing Mach line relative to the oncoming flow. [4]
> (iv) An aerofoil has $M_{\text{cr}}=0.64$. Compute $C_{p0,\min}$ at low speed. [6]
> Parts (v)–(vii) refer to a flat plate ($c=12\ \text{cm}$, $\alpha=15^\circ$) in $M_1=1.9$, $p_1=50\ \text{kPa}$ at height $h$ above a wind tunnel wall (wall reflection misses plate).
> (v) Normal force per unit width by shock-expansion. [10]
> (vi) Normal force per unit width by Ackeret's method. [6]
> (vii) Whether the leading-edge shock undergoes regular or Mach reflection at the wall and why. [6]

### (i) Pitot-static velocity [4 marks]

The measured pressure ratio is

$$
\frac{p}{p_0}=\frac{84.8}{122}=0.6951 .
$$

This is above the sonic value $p^*/p_0=0.5283$, so the flow is subsonic. No shock stands ahead of the probe and the flow is brought to rest isentropically at its nose ([[SESA3029 W01 - Compressible-Flow Toolkit, Normal Shocks and Pitot Probes|W01]]). The IFT row $M=0.74$ has $p/p_0=0.6951$ to four places, so $M=0.74$ straight from the table. Inverting the isentropic relation confirms it.

$$
M=\sqrt{\frac{2}{\gamma-1}\left[\left(\frac{p_0}{p}\right)^{(\gamma-1)/\gamma}-1\right]}
$$

$$
=\sqrt{5\left[\left(\frac{122}{84.8}\right)^{0.2857}-1\right]}
$$

$$
=\sqrt{5\left(1.43868^{0.2857}-1\right)}=\sqrt{5\times0.10951}=\sqrt{0.54757}=0.7400 .
$$

The thermometer reads the static temperature, so the local speed of sound is

$$
a=\sqrt{\gamma RT}=\sqrt{1.4\times287\times243}=\sqrt{97\,637}=312.47\ \text{m/s},
$$

and the velocity is

$$
V=Ma=0.7400\times312.47=\boxed{231.2\ \text{m/s}} .
$$

### (ii) Nozzle throat pressure [4 marks]

At its design condition the nozzle is shock-free, the throat is sonic and the whole expansion is isentropic, so $p_0$ is the same at the throat and the exit ([[SESA3029 W04 - Laval Nozzle, Under- and Over-Expanded Flow|W04]]). At the exit,

$$
\frac{p_e}{p_0}=\left(1+\frac{\gamma-1}{2}M_e^2\right)^{-\gamma/(\gamma-1)}=\left(1+0.2\times4.5^2\right)^{-3.5}=5.05^{-3.5}=0.003455 .
$$

The stagnation pressure follows from the exit pressure.

$$
p_0=\frac{p_e}{p_e/p_0}=\frac{12}{0.003455}=3473\ \text{kPa}.
$$

At the throat $M=1$, so

$$
\frac{p^*}{p_0}=\left(\frac{2}{\gamma+1}\right)^{\gamma/(\gamma-1)}=\left(\frac{2}{2.4}\right)^{3.5}=0.5283,
$$

$$
p^*=0.5283\times3473=\boxed{1835\ \text{kPa}} .
$$

The IFT row $M=4.50$ prints $p/p_0=0.0035$ to four decimal places. Using that value gives $p_0=12/0.0035=3429$ kPa and $p^*=0.5283\times3429=1811$ kPa, which is acceptable as a nearest-value answer. The 1.3 % difference comes entirely from the rounding of 0.003455.

### (iii) Trailing Mach line angle [4 marks]

The expansion is a centred Prandtl–Meyer fan ([[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method|W03]]). Upstream, with $\sqrt{(\gamma+1)/(\gamma-1)}=\sqrt6=2.4495$,

$$
\nu(M_1)=\sqrt6\,\arctan\sqrt{\frac{M_1^2-1}{6}}-\arctan\sqrt{M_1^2-1}
$$

$$
=2.4495\arctan\sqrt{\frac{1.25}{6}}-\arctan\sqrt{1.25}
$$

$$
=2.4495\times24.534^\circ-48.190^\circ=11.905^\circ ,
$$

which is the IFT value at $M=1.50$. Turning through $15^\circ$ adds $15^\circ$ to $\nu$.

$$
\nu(M_2)=\nu(M_1)+\theta=11.905^\circ+15^\circ=26.905^\circ .
$$

The IFT rows that bracket $26.905^\circ$ are

| $M$ | $\nu$ (°) |
|---:|---:|
| 2.00 | 26.3798 |
| 2.02 | 26.9295 |

and linear interpolation gives

$$
M_2=2.00+0.02\times\frac{26.9052-26.3798}{26.9295-26.3798}=2.00+0.02\times\frac{0.5254}{0.5497}=2.00+0.02\times0.9558=2.0191 .
$$

Inverting $\nu$ with a root finder gives the same $M_2=2.0191$. The downstream Mach angle is

$$
\mu_2=\arcsin\frac{1}{M_2}=\arcsin\frac{1}{2.0191}=\arcsin0.49527=29.69^\circ .
$$

The trailing Mach line makes $\mu_2$ with the downstream flow, and that flow is turned $15^\circ$ towards the wall. Measured from the oncoming flow direction, the line is therefore at

$$
\phi_{\text{trail}}=\mu_2-\theta=29.69^\circ-15^\circ=\boxed{14.69^\circ}
$$

on the side away from the wall. The nearest-row answer ($M_2=2.02$, $\mu_2=29.67^\circ$) is $14.67^\circ$.

### (iv) Low-speed minimum pressure coefficient [6 marks]

![[at_pp_202122_q1_mcrit.png|900]]

At $M_\infty=M_{\text{cr}}=0.64$ the minimum-pressure point on the aerofoil has just reached $M=1$, so its pressure coefficient is the critical value $C_{p,\text{cr}}$ ([[SESA3029 W07b - Compressible Potential Flow and the Prandtl-Glauert Transformation|W07b]]). Both the free stream and the sonic point have the same $p_0$, so

$$
\frac{p^*}{p_\infty}=\frac{p^*/p_0}{p_\infty/p_0}=\left(\frac{1+\frac{\gamma-1}{2}M_{\text{cr}}^2}{\frac{\gamma+1}{2}}\right)^{\gamma/(\gamma-1)}
$$

$$
=\left(\frac{1+0.2\times0.64^2}{1.2}\right)^{3.5}=\left(\frac{1.08192}{1.2}\right)^{3.5}=0.90160^{3.5}=0.6959 .
$$

The pressure coefficient written with $\tfrac12\rho_\infty V_\infty^2=\tfrac12\gamma p_\infty M_\infty^2$ is

$$
C_{p,\text{cr}}=\frac{2}{\gamma M_{\text{cr}}^2}\left(\frac{p^*}{p_\infty}-1\right)=\frac{2}{1.4\times0.4096}\,(0.6959-1)=3.4877\times(-0.3041)=-1.0606 .
$$

The Prandtl–Glauert rule $C_p=C_{p0}/\sqrt{1-M_\infty^2}$ links this to the low-speed value at the same point.

$$
C_{p0,\min}=C_{p,\text{cr}}\sqrt{1-M_{\text{cr}}^2}=-1.0606\sqrt{1-0.4096}=-1.0606\times0.76837=\boxed{-0.815} .
$$

### (v) Normal force by shock-expansion [10 marks]

![[at_pp_202122_q1_flat_plate.png|900]]

The plate turns the flow by $\alpha=15^\circ$ on both sides: into the stream on the lower surface, which needs an oblique shock at the leading edge, and away from it on the upper surface, which needs a centred expansion fan.

#### Lower surface: oblique shock

The weak-shock angle comes from the θ–β–M relation ([[SESA3029 W02 - Oblique Shock Relations and Mach Waves|W02]])

$$
\tan\theta=2\cot\beta\,\frac{M_1^2\sin^2\beta-1}{M_1^2(\gamma+\cos2\beta)+2},
$$

evaluated at $M_1=1.9$ for trial values of $\beta$ that bracket $\theta=15^\circ$.

| $\beta$ (°) | $M_1^2\sin^2\beta-1$ | $M_1^2(\gamma+\cos2\beta)+2$ | $2\cot\beta$ | $\tan\theta$ | $\theta$ (°) |
|---:|---:|---:|---:|---:|---:|
| 47 | 0.93091 | 6.80218 | 1.86503 | 0.25524 | 14.318 |
| 49 | 1.05621 | 6.55159 | 1.73857 | 0.28028 | 15.657 |

Interpolating for $\theta=15^\circ$,

$$
\beta\approx47+2\times\frac{15-14.318}{15.657-14.318}=47+2\times0.5093=48.02^\circ .
$$

The exact root of the relation is $\beta=47.995^\circ$, and the oblique-shock chart reads $48^\circ$. The normal Mach number is

$$
M_{n1}=M_1\sin\beta=1.9\sin47.995^\circ=1.9\times0.74309=1.4119 .
$$

The NST rows bracketing $M_{n1}=1.4119$ are

| $M_{n1}$ | $M_{n2}$ | $p_2/p_1$ |
|---:|---:|---:|
| 1.40 | 0.7397 | 2.1200 |
| 1.42 | 0.7314 | 2.1858 |

The interpolation fraction is $(1.4119-1.40)/0.02=0.593$, so

$$
\frac{p_L}{p_1}=2.1200+0.593\times(2.1858-2.1200)=2.1200+0.593\times0.0658=2.1590,
$$

$$
M_{n2}=0.7397-0.593\times(0.7397-0.7314)=0.7397-0.593\times0.0083=0.7348 .
$$

The normal-shock formulae confirm both.

$$
\frac{p_L}{p_1}=1+\frac{2\gamma}{\gamma+1}\left(M_{n1}^2-1\right)=1+\frac{2.8}{2.4}\left(1.4119^2-1\right)=1+1.1667\times0.9934=2.1589,
$$

$$
M_{n2}=\sqrt{\frac{1+0.2M_{n1}^2}{1.4M_{n1}^2-0.2}}=\sqrt{\frac{1.3987}{2.5907}}=\sqrt{0.53988}=0.7348 .
$$

The lower-surface pressure and Mach number are then

$$
p_L=2.1589\times50=107.95\ \text{kPa},
$$

$$
M_L=\frac{M_{n2}}{\sin(\beta-\alpha)}=\frac{0.7348}{\sin32.995^\circ}=\frac{0.7348}{0.54457}=1.3493 .
$$

#### Upper surface: Prandtl–Meyer expansion

The IFT row $M=1.90$ gives $\nu_1=23.586^\circ$. Turning through $15^\circ$,

$$
\nu_U=\nu_1+\alpha=23.586^\circ+15^\circ=38.586^\circ .
$$

The bracketing IFT rows are

| $M$ | $\nu$ (°) | $p/p_0$ |
|---:|---:|---:|
| 2.46 | 38.1831 | 0.0623 |
| 2.48 | 38.6551 | 0.0604 |

The fraction is $(38.5861-38.1831)/(38.6551-38.1831)=0.4030/0.4720=0.854$, so

$$
M_U=2.46+0.02\times0.854=2.4771 .
$$

The expansion is isentropic, so $p_0$ is unchanged and

$$
\frac{p_U}{p_0}=\left(1+0.2\times2.4771^2\right)^{-3.5}=2.2272^{-3.5}=0.06065,
\qquad
\frac{p_1}{p_0}=\left(1+0.2\times1.9^2\right)^{-3.5}=1.722^{-3.5}=0.14924 .
$$

Interpolating the $p/p_0$ column instead gives $0.0623-0.854\times0.0019=0.06068$, the same to three figures. The upper-surface pressure is

$$
p_U=p_1\,\frac{p_U/p_0}{p_1/p_0}=50\times\frac{0.06065}{0.14924}=20.32\ \text{kPa}.
$$

#### Normal force

The pressures act normal to the plate over its full chord $c=0.12$ m, so per unit span

$$
N'=(p_L-p_U)\,c=(107.95-20.32)\times10^3\times0.12=87.63\times10^3\times0.12=\boxed{10.52\ \text{kN/m}} .
$$

Reading the nearest rows instead ($M_{n1}=1.42$ gives $p_L=109.29$ kPa; $M_U=2.48$ with $p_1/p_0=0.1492$ gives $p_U=20.24$ kPa) gives $N'=10.69$ kN/m.

### (vi) Normal force by Ackeret's method [6 marks]

Ackeret's formula $C_p=2\theta/\lambda$ with $\lambda=\sqrt{M_1^2-1}$ needs $\theta$ in radians, positive where the surface turns the flow into itself ([[SESA3029 W07c - Ackeret Theory and Optimum Supersonic Aerofoils|W07c]]). Here $\alpha=15^\circ=0.26180$ rad, and

$$
\lambda=\sqrt{1.9^2-1}=\sqrt{2.61}=1.6155 .
$$

The free-stream dynamic pressure, written as $\tfrac12\gamma p_1M_1^2$, is

$$
q_1=\tfrac12\times1.4\times50\times1.9^2=126.35\ \text{kPa}.
$$

The lower surface has $\theta_L=+\alpha$ and the upper surface $\theta_U=-\alpha$.

$$
C_{p,L}=\frac{2\alpha}{\lambda}=\frac{2\times0.26180}{1.6155}=+0.3241,
\qquad
C_{p,U}=-0.3241 .
$$

The surface pressures follow from $p=p_1+q_1C_p$.

$$
p_L=50+126.35\times0.3241=50+40.95=90.95\ \text{kPa},
\qquad
p_U=50-40.95=9.05\ \text{kPa}.
$$

The normal force per unit span is

$$
N'_{\text{Ack}}=(p_L-p_U)\,c=(90.95-9.05)\times10^3\times0.12=\boxed{9.83\ \text{kN/m}},
$$

which is also $\dfrac{4\alpha}{\lambda}q_1c=\dfrac{4\times0.26180}{1.6155}\times126.35\times0.12=9.83$ kN/m.

> [!check] Ackeret against shock-expansion
> Ackeret's $N'$ is $6.5\,\%$ below the shock-expansion value: $(9.83-10.52)/10.52=-0.065$. Each surface pressure is further off, by $-17.0$ kPa on the lower side ($90.95$ against $107.95$) and $-11.3$ kPa on the upper side ($9.05$ against $20.32$). Both errors have the same sign, because the neglected second-order term raises the pressure on compression and expansion surfaces alike, so they largely cancel in $p_L-p_U$. At $15^\circ$ the cancellation is incomplete.

### (vii) Wall reflection regime [6 marks]

Behind the leading-edge shock the flow runs parallel to the lower surface, at $M_L=1.3493$ and inclined $15^\circ$ towards the wall. The wall is parallel to the free stream, so the reflected shock has to turn this flow back through $15^\circ$ ([[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method|W03]]). A regular reflection is possible only if $15^\circ$ does not exceed the maximum deflection $\theta_{\max}(M_L)$.

The shock angle at maximum deflection is

$$
\sin^2\beta_{\max}=\frac{1}{\gamma M_L^2}\left[\frac{\gamma+1}{4}M_L^2-1+\sqrt{(\gamma+1)\left(\frac{\gamma+1}{16}M_L^4+\frac{\gamma-1}{2}M_L^2+1\right)}\right].
$$

With $M_L^2=1.82052$ and $M_L^4=3.31428$, the pieces are

$$
\frac{\gamma+1}{4}M_L^2-1=0.6\times1.82052-1=0.09231,
$$

$$
\frac{\gamma+1}{16}M_L^4+\frac{\gamma-1}{2}M_L^2+1=0.15\times3.31428+0.2\times1.82052+1=1.86125,
$$

$$
\sqrt{2.4\times1.86125}=\sqrt{4.46699}=2.11353,
$$

so

$$
\sin^2\beta_{\max}=\frac{0.09231+2.11353}{1.4\times1.82052}=\frac{2.20584}{2.54873}=0.86547,
\qquad
\beta_{\max}=\arcsin\sqrt{0.86547}=68.48^\circ .
$$

Putting $\beta_{\max}$ into the θ–β–M relation.

$$
\tan\theta_{\max}=2\cot68.48^\circ\times\frac{1.82052\times0.86547-1}{1.82052\,(1.4+\cos136.96^\circ)+2}=0.78853\times\frac{0.57560}{3.21805}=0.14104,
$$

$$
\theta_{\max}(M_L=1.3493)=8.03^\circ .
$$

A scan of $\theta(\beta)$ at $M_L=1.3493$ gives the same maximum. The required turn, $15^\circ$, is almost twice $\theta_{\max}=8.03^\circ$, so no attached reflected shock can turn the flow parallel to the wall. The reflection is a **Mach reflection**: a near-normal Mach stem stands at the wall, meeting the incident and reflected shocks at a triple point, and a slip line trails downstream from that point.

---

## Q2. Planar dual-bell minimum-length nozzle (30 marks)

> A symmetric planar (2D) dual-bell nozzle is designed using MoC minimum-length method: low-altitude operation matches $p_b$ at intermediate point $i$, and high-altitude operation expands further from $i$ to exit $e$.
> (i) For high-altitude design $M_i=1.6$, $M_e=2.7$, find turning angles at $t$ and $i$ and sketch characteristic lines (starting with 3 lines per fan). [12]
> (ii) Sketch centreline $M$ and $p$ distributions across the full range of $p_b$, with supporting sketches and commentary. [18]

![[at_pp_202122_q2_dual_bell.png|900]]

### (i) Wall turning angles and characteristic network [12 marks]

The IFT rows $M=1.60$ and $M=2.70$ give ([[SESA3029 W05b - Minimum-Length Nozzle Design|W05b]])

$$
\nu(M_i)=\nu(1.6)=14.860^\circ,
\qquad
\nu(M_e)=\nu(2.7)=43.622^\circ .
$$

The working uses the course invariants $R^+=\nu-\theta$, constant along $C^+$, and $R^-=\nu+\theta$, constant along $C^-$ ([[SESA3029 W05a - Method of Characteristics|W05a]]).

#### First bell, throat to i

The flow at the throat is sonic and parallel ($\nu=0$, $\theta=0$). The sharp corner at $t$ turns the wall outward by $\theta_t$ and sends a centred fan of $C^-$ waves towards the centreline. Every $C^+$ line crossing the fan comes from the sonic throat, so it carries

$$
R^+=\nu-\theta=0-0=0 .
$$

On the last ray of the fan the flow angle is $\theta_t$, so $\nu=\theta_t$ there and that $C^-$ ray carries

$$
R^-=\nu+\theta=\theta_t+\theta_t=2\theta_t .
$$

Where this ray meets the centreline, $\theta=0$, so $\nu=R^-=2\theta_t$. The contoured wall from $t$ to $i$ cancels every wave that reflects off the centreline, so the flow leaving the first bell is uniform and parallel at $M_i$. That requires

$$
\nu(M_i)=2\theta_t,
$$

$$
\theta_t=\frac{\nu(M_i)}{2}=\frac{14.860^\circ}{2}=\boxed{7.43^\circ} .
$$

#### Second bell, i to e

A minimum-length contour ends parallel to the axis, so the wall at the end of the first bell is horizontal and the flow at $i$ is uniform with $\theta=0$ and $\nu=\nu(M_i)$. The second corner at $i$ turns the wall outward by $\Delta\theta_i$. Every $C^+$ line crossing the second fan comes from this uniform stream, so

$$
R^+=\nu(M_i)-0=\nu(M_i).
$$

On the last ray $\theta=\Delta\theta_i$, so

$$
\nu=R^++\theta=\nu(M_i)+\Delta\theta_i,
\qquad
R^-=\nu+\theta=\nu(M_i)+2\Delta\theta_i .
$$

At the centreline $\theta=0$ and the exit flow is uniform at $M_e$, so

$$
\nu(M_e)=\nu(M_i)+2\Delta\theta_i,
$$

$$
\Delta\theta_i=\frac{\nu(M_e)-\nu(M_i)}{2}=\frac{43.622^\circ-14.860^\circ}{2}=\frac{28.762^\circ}{2}=\boxed{14.38^\circ} .
$$

The wall just downstream of $i$ is therefore inclined at $14.38^\circ$ to the axis, and the second contour brings it back to $0^\circ$ at $e$. The lower wall is the mirror image, with corners of $-7.43^\circ$ and $-14.38^\circ$.

#### Characteristic network

The sketch starts with three $C^-$ rays from $t$, at $\theta=\theta_t/3$, $2\theta_t/3$ and $\theta_t$ (2.48°, 4.95° and 7.43°). Each reflects off the centreline as a $C^+$ line, the rays cross one another in a triangular interaction region next to the axis, and each $C^+$ line ends on the curved wall $t$–$i$, which is shaped so that nothing reflects back. Downstream of the last $C^+$ line the flow is uniform at $M_i$. The second fan repeats the pattern from $i$, with three $C^-$ rays at $\theta=4.79^\circ$, $9.59^\circ$ and $14.38^\circ$ reflecting off the centreline and ending on the wall $i$–$e$, leaving uniform parallel flow at $M_e$.

### (ii) Centreline Mach number and pressure distributions over the range of back pressure [18 marks]

The stagnation conditions upstream of the throat are fixed and $p_b$ is lowered from $p_0$ towards vacuum ([[SESA3029 W04 - Laval Nozzle, Under- and Over-Expanded Flow|W04]]). Two pressure levels mark the supersonic operating points. At the inflection point,

$$
\frac{p_i}{p_0}=\left(1+0.2\times1.6^2\right)^{-3.5}=1.512^{-3.5}=0.2353,
$$

and at the exit,

$$
\frac{p_e}{p_0}=\left(1+0.2\times2.7^2\right)^{-3.5}=2.458^{-3.5}=0.0430 .
$$

The regimes, in order of falling $p_b$, are

| Regime | Back pressure | Centreline $M$ | Centreline $p$ |
|---|---|---|---|
| Subsonic venturi | just below $p_0$, above the first critical pressure | rises to a subsonic peak at $t$, then falls through both bells | dips to a minimum at $t$, recovers to $p_b$ at $e$ |
| Choked, normal shock in bell 1 | below the first critical pressure, above the value that puts the shock at $i$ | $1$ at $t$, supersonic up to the shock, then a jump to subsonic and deceleration to $e$ | falls along the isentropic curve, jumps up across the shock, then rises to $p_b$ |
| Sea-level mode | of the order of $p_i$ | rises monotonically to about $M_i=1.6$ at $i$, then roughly constant in the separated extension | falls to $p_i=0.235\,p_0$ at $i$, then stays close to $p_b$ |
| Transition | falls below the separation limit of the extension | the separation point jumps from $i$ to $e$ | the curve switches from the sea-level shape to the altitude shape |
| Altitude mode, over-expanded | $p_e<p_b<$ transition pressure | rises monotonically to $M_e=2.7$ at $e$ | falls to $p_e=0.043\,p_0$ at $e$; oblique shocks at the lip raise it to $p_b$ outside |
| Altitude design | $p_b=p_e=0.043\,p_0$ | $1$ at $t$, $1.6$ at $i$, $2.7$ at $e$, smooth and monotonic | $0.528\,p_0$ at $t$, $0.235\,p_0$ at $i$, $p_b$ at $e$; parallel exit jet |
| Altitude mode, under-expanded | $p_b<p_e$ | internal curve as at design | internal curve as at design; expansion fans at the lip lower it to $p_b$ outside |

In every supersonic regime the centreline distributions up to the point where the flow separates or leaves the nozzle are the same isentropic curve, because the supersonic flow inside cannot feel $p_b$. Only the downstream end of the curve changes.

The two bells are what make the dual-bell nozzle useful. In the sea-level mode the flow separates cleanly at the inflection point $i$, because the extra turn of $14.38^\circ$ there forces a strong expansion that an over-expanded boundary layer cannot follow. The first bell then runs full and close to adapted, the extension carries a separated region at roughly $p_b$, and the jet leaves the first bell with a shock-cell pattern whose strength depends on how far $p_b$ is from $p_i$. A conventional bell of exit Mach number 2.7 would instead separate at an unpredictable, moving point and produce side loads.

As the vehicle climbs, $p_b$ falls until the extension can no longer hold the separation at $i$. The separation point then jumps rapidly from $i$ to the exit lip, and the nozzle switches to the altitude mode with both bells running full. The switch shows hysteresis: the return to sea-level mode happens at a slightly higher $p_b$ than the forward transition. In the altitude mode the behaviour at the exit is that of an ordinary Laval nozzle, with oblique lip shocks when over-expanded, a parallel jet at design, and Prandtl–Meyer fans at the lip when under-expanded.

The supporting sketches should show the separated flow and shock cells in the sea-level mode, the lip shocks and diamond pattern of the over-expanded altitude mode, and the lip expansion fans of the under-expanded mode, alongside the $M(x)$ and $p(x)$ curves of panels (b) and (c) above.

---

## Q3. Transient 1D rod cooling by explicit finite difference (30 marks)

> [!warning] Heat transfer (Weeks 9–12)
> This question uses material from Weeks 9–12, which have not yet been lectured. Check the notation and conventions against those lectures when they are written up.

> A rod of diameter $d=10\ \text{mm}$ and length $L=18\ \text{cm}$ ($k=14.8\ \text{W/(m K)}$, $\alpha=3.63\times 10^{-6}\ \text{m}^2/\text{s}$) has its base maintained at $T_0=200^\circ\text{C}$ and is initially uniform at $200^\circ\text{C}$. At $t=0$, it is exposed to air at $T_\infty=25^\circ\text{C}$ with $h=30\ \text{W/(m}^2\text{ K)}$.
> (i) Derive the interior and free-end explicit FD equations in terms of $F$, $B$, $D$. [14]
> (ii) Verify $F=0.2420$, $B=0.7297$, $D=0.0608$ for $\Delta x=3\ \text{cm}$, $\Delta t=60\ \text{s}$ and estimate the time for the mid-length to reach $110^\circ\text{C}$ using linear interpolation. [10]
> (iii) Use the provided $\Delta x=2.25\ \text{cm}$ output table and the result from (ii) to extrapolate for $\Delta t\to 0$ and $\Delta x\to 0$, and comment. [6]

### (i) Derivation of the explicit finite-difference equations [14 marks]

The rod has cross-sectional area $A_c=\pi d^2/4$ and perimeter $P=\pi d$, so

$$
\frac{P}{A_c}=\frac{\pi d}{\pi d^2/4}=\frac{4}{d}.
$$

#### Interior node

Node $i$ owns a slice of length $\Delta x$. Over one time step its stored energy changes by the conduction from both neighbours minus the convection from its side surface, with every flux evaluated at the old time level $n$ (explicit scheme).

$$
\rho c_pA_c\Delta x\,\frac{T_i^{n+1}-T_i^n}{\Delta t}=kA_c\frac{T_{i+1}^n-T_i^n}{\Delta x}+kA_c\frac{T_{i-1}^n-T_i^n}{\Delta x}-hP\Delta x\left(T_i^n-T_\infty\right).
$$

Multiply both sides by $\Delta t/(\rho c_pA_c\Delta x)$.

$$
T_i^{n+1}-T_i^n=\frac{k\Delta t}{\rho c_p\Delta x^2}\left(T_{i+1}^n+T_{i-1}^n-2T_i^n\right)-\frac{hP\Delta t}{\rho c_pA_c}\left(T_i^n-T_\infty\right).
$$

With $\alpha=k/(\rho c_p)$ the first coefficient is

$$
F=\frac{\alpha\Delta t}{\Delta x^2}.
$$

Multiply and divide the second coefficient by $k\Delta x^2$.

$$
\frac{hP\Delta t}{\rho c_pA_c}=\frac{\alpha\Delta t}{\Delta x^2}\cdot\frac{hP\Delta x^2}{kA_c}=F\,B,
\qquad
B=\frac{hP\Delta x^2}{kA_c}=\frac{4h\Delta x^2}{kd}.
$$

Substituting both,

$$
T_i^{n+1}-T_i^n=F\left(T_{i+1}^n+T_{i-1}^n-2T_i^n\right)-FB\left(T_i^n-T_\infty\right).
$$

Move $T_i^n$ to the right and collect its terms.

$$
\boxed{T_i^{n+1}=(1-2F-FB)\,T_i^n+F\left(T_{i+1}^n+T_{i-1}^n\right)+FB\,T_\infty} .
$$

#### Free-end node

The end node $I$ owns half a slice, of length $\Delta x/2$. It conducts to node $I-1$ only, convects from a side surface of area $P\Delta x/2$, and also convects from the end face of area $A_c$.

$$
\rho c_pA_c\frac{\Delta x}{2}\,\frac{T_I^{n+1}-T_I^n}{\Delta t}=kA_c\frac{T_{I-1}^n-T_I^n}{\Delta x}-hP\frac{\Delta x}{2}\left(T_I^n-T_\infty\right)-hA_c\left(T_I^n-T_\infty\right).
$$

Multiply both sides by $2\Delta t/(\rho c_pA_c\Delta x)$.

$$
T_I^{n+1}-T_I^n=\frac{2\alpha\Delta t}{\Delta x^2}\left(T_{I-1}^n-T_I^n\right)-\frac{hP\Delta t}{\rho c_pA_c}\left(T_I^n-T_\infty\right)-\frac{2h\Delta t}{\rho c_p\Delta x}\left(T_I^n-T_\infty\right).
$$

The first two coefficients are $2F$ and $FB$. The third is

$$
\frac{2h\Delta t}{\rho c_p\Delta x}=2\,\frac{\alpha\Delta t}{\Delta x^2}\cdot\frac{h\Delta x}{k}=2FD,
\qquad
D=\frac{h\Delta x}{k}.
$$

Substituting,

$$
T_I^{n+1}-T_I^n=2F\left(T_{I-1}^n-T_I^n\right)-FB\left(T_I^n-T_\infty\right)-2FD\left(T_I^n-T_\infty\right).
$$

Collecting the $T_I^n$ terms,

$$
\boxed{T_I^{n+1}=(1-2F-FB-2FD)\,T_I^n+2F\,T_{I-1}^n+(FB+2FD)\,T_\infty} .
$$

### (ii) Parameter check and time stepping with a 3 cm grid and 60 s step [10 marks]

With $\Delta x=0.03$ m, $\Delta t=60$ s and $d=0.01$ m,

$$
F=\frac{\alpha\Delta t}{\Delta x^2}=\frac{3.63\times10^{-6}\times60}{0.03^2}=\frac{2.178\times10^{-4}}{9\times10^{-4}}=\boxed{0.2420},
$$

$$
B=\frac{4h\Delta x^2}{kd}=\frac{4\times30\times0.03^2}{14.8\times0.01}=\frac{0.108}{0.148}=\boxed{0.7297},
$$

$$
D=\frac{h\Delta x}{k}=\frac{30\times0.03}{14.8}=\frac{0.9}{14.8}=\boxed{0.0608}.
$$

The rod has $L/\Delta x=18/3=6$ intervals: node 0 is the fixture at $200^\circ$C, the mid-length $x=9$ cm is node 3, and the free end is node 6. The coefficients are

$$
1-2F-FB=1-0.4840-0.2420\times0.7297=1-0.4840-0.1766=0.3394,
$$

$$
FB\,T_\infty=0.1766\times25=4.415,
$$

$$
1-2F-FB-2FD=0.3394-2\times0.2420\times0.0608=0.3394-0.0294=0.3100,
$$

$$
(FB+2FD)\,T_\infty=(0.1766+0.0294)\times25=5.150 .
$$

All the coefficients multiplying old temperatures are positive, which is the stability condition for the explicit scheme. The six node equations are then

$$
\begin{aligned}
T_1^{n+1}&=0.3394\,T_1^n+0.2420\left(T_2^n+200\right)+4.415,\\
T_2^{n+1}&=0.3394\,T_2^n+0.2420\left(T_3^n+T_1^n\right)+4.415,\\
T_3^{n+1}&=0.3394\,T_3^n+0.2420\left(T_4^n+T_2^n\right)+4.415,\\
T_4^{n+1}&=0.3394\,T_4^n+0.2420\left(T_5^n+T_3^n\right)+4.415,\\
T_5^{n+1}&=0.3394\,T_5^n+0.2420\left(T_6^n+T_4^n\right)+4.415,\\
T_6^{n+1}&=0.3100\,T_6^n+0.4840\,T_5^n+5.150 .
\end{aligned}
$$

Starting from $200^\circ$C everywhere, the first step gives every interior node

$$
T_i^1=0.3394\times200+0.2420\times(200+200)+4.415=67.88+96.80+4.415=169.10^\circ\text{C},
$$

and the free end

$$
T_6^1=0.3100\times200+0.4840\times200+5.150=62.00+96.80+5.150=163.95^\circ\text{C}.
$$

The mid-length node evolves as

$$
\begin{aligned}
T_3^2&=0.3394\times169.10+0.2420\times(169.10+169.10)+4.415=143.65,\\
T_3^3&=0.3394\times143.65+0.2420\times(143.65+143.65)+4.415=122.70,\\
T_3^4&=0.3394\times122.70+0.2420\times(122.40+124.51)+4.415=105.81,
\end{aligned}
$$

with the neighbours taken from the full table (temperatures in °C).

| $n$ | $t$ (s) | $T_1$ | $T_2$ | $T_3$ (mid) | $T_4$ | $T_5$ | $T_6$ (end) |
|---:|---:|---:|---:|---:|---:|---:|---:|
| 0 | 0 | 200.00 | 200.00 | 200.00 | 200.00 | 200.00 | 200.00 |
| 1 | 60 | 169.10 | 169.10 | 169.10 | 169.10 | 169.10 | 163.95 |
| 2 | 120 | 151.13 | 143.65 | 143.65 | 143.65 | 142.41 | 137.81 |
| 3 | 180 | 138.87 | 124.51 | 122.70 | 122.40 | 120.86 | 116.80 |
| 4 | 240 | 130.08 | 109.98 | 105.81 | 104.90 | 103.32 | 99.85 |

The mid-length passes $110^\circ$C between steps 3 and 4. Interpolating linearly,

$$
t_{110}=180+60\times\frac{122.70-110}{122.70-105.81}=180+60\times\frac{12.70}{16.89}=180+45.12=\boxed{225.1\ \text{s}} .
$$

### (iii) Fine-grid result and extrapolation [6 marks]

With $\Delta x=2.25$ cm the rod has $18/2.25=8$ intervals, so the mid-length is node 4. The printed times step by $\Delta t=202.50-168.75=33.75$ s, which keeps $F$ unchanged.

$$
F=\frac{3.63\times10^{-6}\times33.75}{0.0225^2}=\frac{1.2251\times10^{-4}}{5.0625\times10^{-4}}=0.2420 .
$$

$T_4$ passes $110^\circ$C between $t=202.50$ s ($118.6^\circ$C) and $t=236.25$ s ($109.5^\circ$C).

$$
t_{110}=202.50+33.75\times\frac{118.6-110}{118.6-109.5}=202.50+33.75\times\frac{8.6}{9.1}=202.50+31.90=\boxed{234.4\ \text{s}} .
$$

The explicit scheme has a time error of order $\Delta t$ and a space error of order $\Delta x^2$. Holding $F$ fixed ties the two together, since $\Delta t=(F/\alpha)\,\Delta x^2$, so both errors scale as $\Delta x^2$ and a single Richardson step with order $p=2$ extrapolates to $\Delta t\to0$ and $\Delta x\to0$ at once. The refinement ratio is

$$
r=\frac{\Delta x_{\text{coarse}}}{\Delta x_{\text{fine}}}=\frac{3.0}{2.25}=\frac43,
\qquad
r^2=\frac{16}{9},
$$

which is also the ratio of the time steps, $60/33.75=16/9$. The extrapolated time is

$$
t_{\text{ext}}=t_{\text{fine}}+\frac{t_{\text{fine}}-t_{\text{coarse}}}{r^2-1}=234.40+\frac{234.40-225.12}{16/9-1}=234.40+\frac{9.28}{7/9}=234.40+11.93=\boxed{246.3\ \text{s}} .
$$

The two grid results differ by 9.3 s, about 4 %, so neither is converged, and the coarse grid underestimates the time by more than the fine one. Both cool too fast because each explicit step multiplies a decaying mode by $1-\lambda\Delta t$, which is smaller than $e^{-\lambda\Delta t}$. The extrapolated value lies 12 s above the finer result, which shows how much of the fine-grid answer is still discretisation error.

> [!check] Extrapolation against a converged solution
> The same scheme on a very fine grid ($\Delta x=1.5$ mm, $\Delta t=0.05$ s) reaches $110^\circ$C at the mid-length at $t=247.2$ s. The coarse and fine errors are $22.1$ s ($8.9\,\%$) and $12.8$ s ($5.2\,\%$). Their ratio, $1.72$, is close to $r^2=1.78$, which confirms second-order behaviour, and the extrapolated $246.3$ s is within $0.4\,\%$ of the converged value.

---

## Paper slips and ambiguities

- The front page prints the constants as "=γ1.4ρ ,=1.225 kg/m3", a symbol-ordering glitch. The intended values are $\gamma=1.4$ and $\rho=1.225\ \text{kg/m}^3$.
- Q2(i) asks for "the turning angle of the flow at points t and i". At $t$ this is the wall corner angle $\nu(M_i)/2=7.43^\circ$. At $i$ the wall is already back to $0^\circ$, so the turning angle is the second corner, $[\nu(M_e)-\nu(M_i)]/2=14.38^\circ$, not $\nu(M_e)/2=21.81^\circ$.
- The formula sheet (p. 7) gives $\text{Nu}=0.022\,\text{Pr}^{0.5}\text{Re}^{0.8}$ for turbulent pipe flow and $\text{Nu}_x=0.029\,\text{Re}_x^{0.8}\text{Pr}^{0.6}$ for a turbulent boundary layer. Q3 does not need either, because $h$ is given.
- Corrections to the earlier draft of these solutions. In Q1(vii) the draft gave $\beta_{\max}=65.17^\circ$; the correct value at $M_L=1.3493$ is $68.48^\circ$. The quoted $\theta_{\max}=8.03^\circ$ and the conclusion (Mach reflection) were right. In Q1(iv) the draft printed $p^*/p_\infty=0.69567$; the value is $0.6959$, and the $C_p$ values were unaffected. In Q3(iii) the draft said linear interpolation biases a convex cooling curve downwards. The chord of a convex curve lies above it, so linear interpolation, if anything, makes the crossing time slightly late; the comment was removed, because the discretisation error dominates either way.
