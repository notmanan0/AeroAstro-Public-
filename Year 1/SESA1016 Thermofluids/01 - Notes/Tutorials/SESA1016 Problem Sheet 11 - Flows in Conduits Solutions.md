---
title: "SESA1016 Problem Sheet 11 - Flows in Conduits Solutions"
module: "SESA1016 Thermofluids"
type: tutorial
stream: "Part B: Fluid Mechanics"
tags: [sesa1016, tutorial-solutions, pipe-flow, friction, minor-losses]
sheet: "Problem Sheet 11 - Flows in Conduits"
theory_notes: ["[[SESA1016 T15 - Flow in Conduits]]"]
key_concepts: ["[[Darcy Friction Factor]]", "[[Major and Minor Head Losses]]", "[[Reynolds Number]]"]
status: complete
sources: ["02 - Sources/Tutorial Sheets/Problem Sheet 11 - Flows in Conduits.pdf"]
---

# SESA1016 Problem Sheet 11 - Flows in Conduits Solutions

> [!abstract] Sheet Info
> Ten problems on developed velocity profiles, viscous shear, Reynolds-number classification, Darcy–Weisbach loss, minor losses and iterative pipe-flow design.

## Q11.1 One-seventh-power turbulent pipe profile

For

$$\frac{u(r)}{V_{max}}=\left(1-\frac rR\right)^{1/7},$$

the area mean is

$$
\bar V=\frac{1}{\pi R^2}\int_Au\,dA
=2V_{max}\int_0^1s(1-s)^{1/7}ds,
$$

where $s=r/R$. Since

$$\int_0^1s(1-s)^{1/7}ds=\frac{49}{120},$$

$$
\bar V=\frac{49}{60}V_{max},
\qquad
\boxed{\frac{V_{max}}{\bar V}=\frac{60}{49}=1.224}.
$$

Thus the centreline maximum is about $22\%$ above the mean.

## Q11.2 Plane Poiseuille flow

The profile between plates at $y=\pm h$ is

$$u=V_{max}\left(1-\frac{y^2}{h^2}\right).$$

Per unit plate width,

$$
q'=\int_{-h}^{h}u\,dy
=\boxed{\frac43V_{max}h}.
$$

The shear stress is

$$
\tau(y)=\mu\frac{du}{dy}
=-\frac{2\mu V_{max}}{h^2}y.
$$

It is zero at the centreline, changes sign across the centre, and has wall magnitude

$$\boxed{|\tau_w|=\frac{2\mu V_{max}}h}.$$

![[tf_q11_2_plane_poiseuille.png]]

## Q11.3 Board sliding on an oil film

At terminal speed, the downslope weight component balances Couette shear drag:

$$W\sin20^\circ=\tau A=\mu\frac UhA.$$

Therefore

$$
h=\frac{\mu UA}{W\sin20^\circ}
=\frac{0.05(0.020)(1)}{25\sin20^\circ}
=\boxed{1.17\times10^{-4}\ \mathrm m=0.117\ \mathrm{mm}}.
$$

## Q11.4 Sphere falling in a tube

Relative to the tube, the falling sphere displaces fluid upward through the annular gap. Volume conservation gives

$$
A_sU_s=(A_t-A_s)\bar V_{gap}.
$$

Hence

$$
\bar V_{gap}
=U_s\frac{D_s^2}{D_t^2-D_s^2}
=1\frac{0.15^2}{0.20^2-0.15^2}
=\boxed{1.29\ \mathrm{m\,s^{-1}}\approx1.3\ \mathrm{m\,s^{-1}}}
$$

upward. The velocity is zero at both solid boundaries and reaches a maximum within the narrow gap.

## Q11.5 Laminar or turbulent?

The mean speed is

$$
\bar V=\frac{Q}{A}
=\frac{8\times10^{-4}}{\pi(0.10)^2/4}
=0.1019\ \mathrm{m\,s^{-1}}.
$$

For water at $20^\circ$C, $\nu\approx1.0\times10^{-6}\ \mathrm{m^2\,s^{-1}}$:

$$
Re_D=\frac{\bar VD}{\nu}\approx1.02\times10^4.
$$

Since this is well above the transition range,

$$\boxed{\text{the flow is expected to be turbulent}}.$$

## Q11.6 Oil-tanker delivery line

The flow rate is

$$Q=\frac{1250}{3600}=0.3472\ \mathrm{m^3\,s^{-1}}.$$

### (a) Horizontal 300 mm pipe

$$
V=\frac{4Q}{\pi D^2}=4.912\ \mathrm{m\,s^{-1}},
\qquad
Re=\frac{\rho VD}{\mu}=3.93\times10^4.
$$

Linear interpolation of the supplied table gives $f=0.02271$. The major head loss is

$$
h_f=f\frac LD\frac{V^2}{2g}=46.55\ \mathrm m.
$$

With pump efficiency $\eta_p=0.60$,

$$
\boxed{P=\frac{\rho gQh_f}{\eta_p}=211.4\ \mathrm{kW}}.
$$

### (b) Additional 25 m rise through a 200 mm pipe

For the vertical pipe,

$$V_2=11.05\ \mathrm{m\,s^{-1}},\qquad Re_2=5.89\times10^4,$$

and interpolation gives $f_2=0.02051$. Its required head is

$$
h_2=25+f_2\frac{25}{0.20}\frac{V_2^2}{2g}=40.96\ \mathrm m.
$$

Therefore

$$
\boxed{P=\frac{\rho gQ(h_f+h_2)}{\eta_p}=397.5\ \mathrm{kW}}.
$$

## Q11.7 Overall pipe force balance

For steady, fully developed flow, inlet and outlet momentum fluxes cancel. The pressure force balances wall shear:

$$
\Delta p\frac{\pi D^2}{4}=\tau_w\pi DL.
$$

Thus

$$
\boxed{\tau_w=\frac{\Delta pD}{4L}
=\frac{4800(0.10)}{4(12)}=10.0\ \mathrm{Pa}}.
$$

At $58^\circ$C, $\mu=4.804\times10^{-4}\ \mathrm{Pa\,s}$. Newton's law of viscosity gives

$$
\boxed{\left|\frac{du}{dy}\right|_w
=\frac{\tau_w}{\mu}=2.08\times10^4\ \mathrm{s^{-1}}}.
$$

> [!note] Source inconsistency
> The worked solution gives $10$ Pa and $20\,815\ \mathrm{s^{-1}}$, which follow directly from the stated data. The isolated “926 Pa” in the final answer block does not correspond to Q11.7 and appears to be a typographical error.

## Q11.8 Capillary rheometer

The measured volume flow is

$$
Q=\frac{50\times10^{-6}}{167}
=2.994\times10^{-7}\ \mathrm{m^3\,s^{-1}}.
$$

The driving pressure is $\Delta p=\rho gh$. For laminar circular-pipe flow,

$$
Q=\frac{\pi D^4}{128\mu L}\Delta p.
$$

Therefore

$$
\boxed{\mu=\frac{\pi D^4\rho gh}{128LQ}
=0.104\ \mathrm{Pa\,s}}.
$$

## Q11.9 Electro-valve minor-loss coefficient

The piezometer difference represents loss head:

$$h_L=K\frac{V^2}{2g},qquad V=\frac QA.$$

For $D=0.042$ m, the three tests give

| Test | $V$ (m/s) | $K=2gh/V^2$ |
|---:|---:|---:|
| 1 | 0.866 | 0.364 |
| 2 | 1.660 | 0.322 |
| 3 | 2.310 | 0.323 |

The arithmetic mean is

$$\boxed{\bar K=0.336}.$$

The first test is more sensitive to reading error because its pressure head is smallest.

## Q11.10 SAF delivery line

The available pressure drop is $\Delta p=5.0\times10^5$ Pa. For a trial mean speed $V$,

$$
Re=\frac{\rho VD}{\mu},
$$

and the Darcy factor satisfies Colebrook–White:

$$
\frac1{\sqrt f}=-2\log_{10}\left[
\frac{\epsilon/D}{3.7}+\frac{2.51}{Re\sqrt f}
\right].
$$

The energy equation is

$$
\Delta p=f\frac LD\frac{\rho V^2}{2}.
$$

Iterate between the friction-factor relation and

$$
V=\sqrt{\frac{2\Delta pD}{fL\rho}},
\qquad Q=\frac{\pi D^2}{4}V.
$$

The converged result is

$$
\boxed{Q=1.107\times10^{-3}\ \mathrm{m^3\,s^{-1}}},
$$

$$
\boxed{Re=2.89\times10^5},
\qquad
\boxed{\text{turbulent flow}}.
$$

The relative roughness is $\epsilon/D=0.005$, large enough that a smooth-pipe correlation would be inappropriate.

## Related

- [[SESA1016 T15 - Flow in Conduits]]
- [[Darcy Friction Factor]]
- [[Major and Minor Head Losses]]
- [[Reynolds Number]]
- [[SESA1016 Formula Sheet]]

