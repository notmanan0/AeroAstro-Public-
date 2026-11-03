---
title: "SESA2023 W04 - Friction, Heat Addition, Oblique Shocks and Intakes"
module: "SESA2023 Propulsion"
type: topic
stream: "Section 1: Introduction and Fundamentals"
order: 4
tags:
  - sesa2023
  - compressible-flow
  - oblique-shock
  - intakes
  - fanno-rayleigh
aliases: ["Gas dynamics II", "Intakes and diffusers", "SESA2023 Week 4"]
date: 2026-09-24
status: lectured
coverage: "Week 4 (Lectures 10–12)"
parent: ["[[SESA2023 Propulsion Hub]]"]
prerequisites: ["[[SESA2023 W03 - Compressible Flow, Normal Shocks and Nozzles]]"]
next_topics: ["[[SESA2023 W05 - Combustion, Stoichiometry and Chemical Equilibrium]]"]
key_concepts: ["[[Friction and Heat Addition in Constant-Area Ducts]]", "[[Oblique Shock Waves]]", "[[Intake Pressure Recovery]]", "[[Normal Shock Waves]]"]
tutorial_sheets: ["[[SESA2023 Problem Sheet 3 Solutions]]", "[[SESA2023 Problem Sheet 4 Solutions]]"]
sources: ["02 - Sources/Lectures/Week 04 - Gas Dynamics II - Friction, Heat Transfer, Oblique Shocks and Intakes.pdf", "02 - Sources/Lectures/SESA2023 Lecture 2026-02-17.txt", "02 - Sources/Lectures/SESA2023 Lecture 2026-02-20.txt"]
---

# SESA2023 W04 - Friction, Heat Addition, Oblique Shocks and Intakes

> [!abstract] Summary
> Week 4 relaxes the ideal W03 assumptions and uses the results to design the engine's front end. Friction and heat addition in a constant-area duct both push the flow towards $M=1$, and too much of either chokes the duct. An oblique shock is a normal shock acting on the normal velocity component, $M_{n1}=M_1\sin\sigma$, so the flow is turned by $\delta$. Intakes slow the flow to about M 0.4–0.5 for the compressor with the least stagnation-pressure loss: subsonic intakes diverge gently (half-angle 6–7°), while supersonic intakes use a normal shock (up to about M 1.7), several oblique shocks or both. The shock inside a C–D nozzle, reviewed at the start of the 17 Feb lecture, is in [[SESA2023 W03 - Compressible Flow, Normal Shocks and Nozzles#Worked example – shock in the diverging section|W03]].

> [!summary]- Exam use: quick path
> - **Use it when:** a duct has friction or heating; a wedge, ramp or spike turns a supersonic flow; or an intake (subsonic or supersonic) must be sized or its loss found.
> - **Assumptions:** perfect gas, steady 1-D; constant-area duct with $f$, $q$ given as dimensionless parameters; for oblique shocks, the attached weak solution unless told otherwise; intakes adiabatic ($T_{02}=T_{01}$) with negligible exit KE.
> - **Method:** 1. Oblique shock: $M_{n1}=M_1\sin\sigma$, then $\delta$ from the $\theta$–$\beta$–$M$ relation. 2. Normal-shock table at $M_{n1}$ for $p_2/p_1$, $T_2/T_1$, $M_{n2}$. 3. $M_2=M_{n2}/\sin(\sigma-\delta)$. 4. Intake: $T_{01}$, $p_{01}$ from flight $M$; $p_{02}=\Gamma_dp_{01}$ (or from $\eta_d$). 5. Exit state from the exit Mach number, then areas from $\dot m=\rho uA$.
> - **Common mistakes:** applying the normal-shock relations to $M_1$ instead of $M_{n1}$; forgetting that $M_2$ needs $\sin(\sigma-\delta)$, not $\sin\sigma$.
> - **Practise:** [[#Worked example – oblique shock at Mach 3]] · [[#Worked example – subsonic intake at 6 km]] · [[SESA2023 Problem Sheet 4 Solutions]] Q4.3

In a constant-area duct with friction, the boundary layer grows along the wall and takes up more of the cross-section, so the duct behaves like a converging nozzle (17 Feb, ll. 265–275): subsonic flow speeds up towards $M=1$ and supersonic flow slows down towards it. Heat addition has a similar effect: heating expands the gas, so in a fixed area it has to speed up if subsonic or slow down if supersonic, again towards Mach 1, and cooling does the opposite. Both can choke the duct: once the exit reaches $M=1$, extra friction or heat can't be absorbed, and the duct accepts less mass flow instead.

An oblique shock is a normal shock seen at an angle. Split the velocity into parts normal and parallel to the shock, and only the normal part feels it; the parallel part slides through unchanged, and because the normal part shrinks the flow is turned towards the shock. An intake is then a compressor with no moving parts, turning the aircraft's speed into pressure for the engine. Every shock costs stagnation pressure, so a good supersonic intake uses several weak oblique shocks rather than one strong normal shock.

---

## 1. Friction and heat addition in a constant-area duct (Lecture 10)

### Governing equations

Isolate the two effects in a straight duct, $dA/dx=0$ (17 Feb, ll. 219–241). Between an inlet 1 and outlet 2 (notes §3.2):

$$
\rho_1u_1 = \rho_2u_2
$$

$$
p_1+\rho_1u_1^2 = p_2+\rho_2u_2^2+p_1f
$$

$$
h_1+\tfrac12u_1^2+h_1q = h_2+\tfrac12u_2^2
$$

The dimensionless friction $f$ is the wall friction force divided by $p_1A$. The dimensionless heating $q$ is the heat added per unit mass divided by $h_1$: $q>0$ is a source, $q<0$ a sink (17 Feb, ll. 232–239).

### In terms of Mach number

**Momentum.** For a perfect gas $\rho u^2=\rho a^2M^2=\gamma pM^2$ (since $a^2=\gamma p/\rho$). Substitute:

$$
p_1+\gamma p_1M_1^2-p_1f = p_2+\gamma p_2M_2^2
$$

$$
p_1\left(1+\gamma M_1^2-f\right) = p_2\left(1+\gamma M_2^2\right)
$$

**Energy.** Factor out $h$ and use $u^2/(2h)=u^2/(2c_pT)=\tfrac{\gamma-1}{2}M^2$:

$$
h_1\left(1+\frac{\gamma-1}{2}M_1^2+q\right) = h_2\left(1+\frac{\gamma-1}{2}M_2^2\right)
$$

**Mass.** With $\rho=p/(RT)$ and $u=M\sqrt{\gamma RT}$, $\rho u=pM\sqrt{\gamma/(RT)}$, so

$$
\frac{p_1M_1}{\sqrt{T_1}} = \frac{p_2M_2}{\sqrt{T_2}}\qquad\Longrightarrow\qquad \frac{M_2}{M_1} = \frac{p_1}{p_2}\sqrt{\frac{T_2}{T_1}}
$$

Eliminate $p$ and $T$ with the momentum and energy results ($T_2/T_1=h_2/h_1$):

$$
\frac{M_2}{M_1} = \frac{1+\gamma M_2^2}{1+\gamma M_1^2-f}\left[\frac{1+\frac{\gamma-1}{2}M_1^2+q}{1+\frac{\gamma-1}{2}M_2^2}\right]^{1/2}
$$

**Rearrange.** Square, and collect the $M_2$ terms on the left and the given inlet terms on the right:

$$
\frac{M_2^2\left[1+\frac{\gamma-1}{2}M_2^2\right]}{\left(1+\gamma M_2^2\right)^2} = \frac{M_1^2\left[1+\frac{\gamma-1}{2}M_1^2+q\right]}{\left(1+\gamma M_1^2-f\right)^2}\equiv\mathcal A
$$

> [!warning] Read the notes' version as a ratio
> In the Week 4 notes this equation is printed on one line, so the $(1+\gamma M^2)^2$ factors can look like multipliers. They are denominators, as the derivation above shows.

**Solve.** Put $X=M_2^2$ and $k=(\gamma-1)/2$. Cross-multiply:

$$
X+kX^2 = \mathcal A\left(1+2\gamma X+\gamma^2X^2\right)
$$

$$
\left(k-\mathcal A\gamma^2\right)X^2+\left(1-2\mathcal A\gamma\right)X-\mathcal A = 0
$$

The quadratic formula gives a discriminant $(1-2\mathcal A\gamma)^2+4\mathcal A(k-\mathcal A\gamma^2)=1-4\mathcal A\gamma+2\mathcal A(\gamma-1)=1-2\mathcal A(\gamma+1)$, so

$$
\boxed{M_2^2 = \frac{-(1-2\mathcal A\gamma)\pm\sqrt{1-2\mathcal A(\gamma+1)}}{(\gamma-1)-2\mathcal A\gamma^2}}
$$

the biquadratic solution of notes eq. (3.1). With $f=q=0$ the two roots are $M_2=M_1$ (nothing happens) and the normal-shock $M_2$.

> [!check] The $f=q=0$ limit
> For $M_1=2.5$ and $f=q=0$ the formula gives $M_2=2.500$ and $0.513$. The normal-shock table at 2.5 gives $M_2=0.513$ ✔.

### Reading the plots

![[prop_duct_friction_heating.png|760]]

Each curve is a value of $f$ (left, $q=0$) or $q$ (right, $f=0$). The grey upper-left region ($M_1<1$, $M_2>1$) is inaccessible because it would need $\Delta s<0$ (17 Feb, ll. 245–251).

| | Subsonic inlet ($M_1<1$) | Supersonic inlet ($M_1>1$) |
|---|---|---|
| Friction $f>0$ | accelerates towards M 1; $p$, $\rho$, $T$ fall | two solutions: stays supersonic but decelerates ($1<M_2<M_1$; $p$, $\rho$, $T$ rise), or a normal shock to subsonic ($p$, $\rho$, $T$ rise) |
| Heating $q>0$ | accelerates; $p$, $\rho$ fall; $T$ rises except for $1/\sqrt\gamma<M_1<1$ | as for friction: decelerate, or shock |
| Cooling $q<0$ | decelerates; $p$, $\rho$ rise | always has a solution: accelerates ($M_2>M_1$; $p$, $\rho$, $T$ fall), or a shock |

Which supersonic branch occurs depends on the downstream pressure: a high back pressure forces the shock (17 Feb, ll. 279–291).

- $1/\sqrt\gamma=0.845$ for air. Between M 0.845 and 1 the heat added goes mainly into kinetic energy, so the temperature can fall while heat is added (17 Feb, ll. 314–319).
- The stagnation pressure always falls with friction, because entropy rises.

> [!warning] Transcript slip (17 Feb, ll. 287–288)
> For the supersonic branch without a shock the lecturer says "there is still isentropic case and we have the acceleration of the flow". With friction the flow is not isentropic, and on this branch it decelerates ($1<M_2<M_1$) while $p$, $\rho$, $T$ rise (notes §3.2.1). The lecturer also flags errors on the heat-transfer slide (ll. 333–335); the table above follows the notes.

### Choking

Both effects push the exit towards $M_2=1$. The two roots of the biquadratic merge when the discriminant is zero:

$$
1-2\mathcal A(\gamma+1) = 0\qquad\Longrightarrow\qquad \mathcal A^* = \frac{1}{2(\gamma+1)} = 0.2083\ \ (\gamma=1.4)
$$

For a given $M_1$ that sets a maximum $f$ or $q$. Beyond it there is no steady solution with the same inlet state: the duct chokes and the upstream flow adjusts, passing less mass (notes §3.2.3), just like a converging nozzle with too low a back pressure.

### Worked example – friction in a subsonic duct

Inlet $M_1=0.5$, $\gamma=1.4$, adiabatic ($q=0$).

**(a) With $f=0.1$.** First

$$
\mathcal A = \frac{0.25\times(1+0.2\times0.25)}{(1+1.4\times0.25-0.1)^2} = \frac{0.2625}{1.5625} = 0.168
$$

The subsonic root of the boxed formula is $M_2=0.589$. Then

$$
\frac{p_2}{p_1} = \frac{1+0.35-0.1}{1+1.4\times0.589^2} = 0.842,\qquad \frac{T_2}{T_1} = \frac{1.05}{1+0.2\times0.589^2} = 0.982
$$

$$
\frac{\rho_2}{\rho_1} = \frac{0.842}{0.982} = 0.857,\qquad \frac{p_{02}}{p_{01}} = 0.842\times\left(\frac{1.0693}{1.05}\right)^{3.5} = 0.897
$$

The flow accelerates and its pressure, density and temperature fall, as the table predicts; 10 % of the stagnation pressure is lost.

**(b) Largest friction before choking.** Set $\mathcal A=\mathcal A^*$:

$$
1+\gamma M_1^2-f_{max} = M_1\sqrt{\frac{1+\frac{\gamma-1}{2}M_1^2}{\mathcal A^*}} = 0.5\sqrt{\frac{1.05}{0.2083}} = 1.1225
$$

$$
f_{max} = 1.35-1.1225 = 0.228
$$

With heating instead ($f=0$) the same steps give $q_{max}=0.469$.

> [!check] Lecture reading of the friction plot (17 Feb, ll. 281–285)
> "If we have a Mach 1 of 2.5, we can read two possible values of Mach 2, one that is around 0.6 and one that is about 2.1, 2.2" for $f=0.4$. The formula gives $0.560$ and $2.111$ ✔.

The lecturer was specific about what is examinable here (17 Feb, ll. 343–353): "I'm not going to ask [the Mach-number relation and the differential relations] at the exam. But… only the conservation law with the presence of the additional term for the friction and the [heat] transfer… and of course, the meaning of this graph." So be able to write the three conservation equations with $f$ and $q$, and explain every region of the two plots.

---

## 2. Oblique shocks (Lecture 11)

### Geometry

A shock at shock (wave) angle $\sigma$ to the incoming flow turns it through a deflection angle $\delta$ (17 Feb, ll. 356–399; notes §3.3, Fig. 3.3).

![[prop_oblique_shock_geometry.png|820]]

Rotate the picture so the shock is vertical and split each velocity into a component normal to the shock ($u$) and one parallel to it ($v$):

$$
u_1 = V_1\sin\sigma,\qquad v = V_1\cos\sigma
$$

$$
u_2 = V_2\sin(\sigma-\delta),\qquad v = V_2\cos(\sigma-\delta)
$$

**Why $v$ is unchanged.** Momentum parallel to the shock has no pressure force acting on it (pressure acts normal to the shock face), so the parallel momentum flux is the same on both sides. With $\rho_1u_1=\rho_2u_2$ that gives $v_1=v_2=v$.

The jump in the normal component is then exactly a normal shock, and the parallel velocity "does not affect the static properties". So:

$$
\boxed{M_{n1} = M_1\sin\sigma>1,\qquad M_{n2} = M_2\sin(\sigma-\delta)<1}
$$

and every normal-shock relation (and table) holds with $M_1\to M_{n1}$, $M_2\to M_{n2}$:

$$
\frac{p_2}{p_1} = 1+\frac{2\gamma}{\gamma+1}\left(M_1^2\sin^2\sigma-1\right),\qquad M_2^2\sin^2(\sigma-\delta) = \frac{(\gamma-1)M_1^2\sin^2\sigma+2}{2\gamma M_1^2\sin^2\sigma-(\gamma-1)}
$$

### The deflection angle

**Density ratio from the geometry.** Mass gives $\rho_2/\rho_1=u_1/u_2$. Divide the two normal components by the common $v$:

$$
\frac{u_1}{v} = \tan\sigma,\qquad \frac{u_2}{v} = \tan(\sigma-\delta)\qquad\Longrightarrow\qquad \frac{\rho_2}{\rho_1} = \frac{\tan\sigma}{\tan(\sigma-\delta)}
$$

**Density ratio from the shock.** The normal-shock density ratio with $M_{n1}$:

$$
\frac{\rho_2}{\rho_1} = \frac{(\gamma+1)M_1^2\sin^2\sigma}{(\gamma-1)M_1^2\sin^2\sigma+2}
$$

**Equate and solve for $\delta$.** Expanding $\tan(\sigma-\delta)=(\tan\sigma-\tan\delta)/(1+\tan\sigma\tan\delta)$ and collecting the $\tan\delta$ terms gives the course's $\theta$–$\beta$–$M$ relation (notes §3.3; in the data book):

$$
\boxed{\tan\delta = 2\cot\sigma\,\frac{M_1^2\sin^2\sigma-1}{M_1^2(\gamma+\cos2\sigma)+2}}
$$

### Weak, strong and detached shocks

![[prop_oblique_shock.png|680]]

- $\delta=0$ at $\sigma=90^\circ$ (a normal shock) and at $\sigma=\mu=\sin^{-1}(1/M_1)$ (the Mach angle, an infinitely weak wave). Note $M_{n1}=1$ exactly at $\sigma=\mu$.
- For each $M_1$ there is a maximum deflection $\delta_{max}$ (dotted curve). If a wedge or ramp turns the flow by more than $\delta_{max}$, no attached shock exists: the shock detaches and stands off as a curved bow shock, normal (and so strongly subsonic behind) on the axis (17 Feb, ll. 450–453).
- For $\delta<\delta_{max}$ there are two solutions. The weak shock (smaller $\sigma$) usually leaves the flow supersonic, except in a thin band just below $\delta_{max}$; it is the one seen on wedges and ramps. The strong shock (larger $\sigma$) always leaves it subsonic (17 Feb, ll. 438–456).
- $\delta_{max}$ grows with $M_1$: at M 1.2 only a few degrees of turning is possible before the shock detaches.

### Worked example – oblique shock at Mach 3

From the board example (17 Feb, ll. 458–510): $p_1=101.325$ kPa ("basically atmospheric"), $T_1=288$ K, $M_1=3$, $\sigma=50^\circ$.

**Normal Mach number:**

$$
M_{n1} = 3\sin50^\circ = 2.298
$$

**Deflection:**

$$
\tan\delta = 2\cot50^\circ\,\frac{9\sin^250^\circ-1}{9(1.4+\cos100^\circ)+2} = 2\times0.8391\times\frac{4.281}{13.037} = 0.5511,\qquad \delta = 28.9^\circ
$$

**Normal-shock relations at $M_{n1}=2.298$:** $M_{n2}=0.535$, $p_2/p_1=5.995$, $T_2/T_1=1.945$, so

$$
p_2 = 607\ \mathrm{kPa},\qquad T_2 = 560\ \mathrm K
$$

**Downstream Mach number:**

$$
M_2 = \frac{M_{n2}}{\sin(\sigma-\delta)} = \frac{0.535}{\sin21.1^\circ} = 1.48
$$

The flow stays supersonic: this is a weak shock.

> [!warning] Transcript slip (17 Feb, ll. 489, 505–507)
> The lecturer first reads "Mach normal 2 is 1.48", then catches it: "I read the wrong value, because this has always to be smaller than 1." $M_{n2}=0.535$; the 1.48 is $M_2$, after dividing by $\sin(\sigma-\delta)$.

> [!check] Numerical checks
> - $M_{n2}<1$ ✔ and $M_2>1$, consistent with a weak shock.
> - $p_{02}/p_{01}=0.584$ at $M_{n1}=2.30$. A *normal* shock at M 3 would keep only 0.328: the oblique shock loses far less, which is the whole point of §3.

---

## 3. Intakes and diffusers (Lecture 12)

### Requirements (20 Feb, ll. 44–52)

- Decelerate the flow to M 0.4–0.5 (even 0.3) and raise the static pressure;
- deliver uniform flow to the compressor, or it will not work at its best (often more important than minimum loss);
- minimise the stagnation-pressure loss, the external drag (no "fancy shapes") and the weight (short);
- cope with incidence and yaw.

> [!warning] Transcript slip (20 Feb, l. 46)
> "Decrease the static pressure." A diffuser increases static pressure; the lecturer says so himself at l. 67 ($p_2>p_1$).

The area–velocity relation from W03 sets the shape (20 Feb, ll. 32–43): to slow a subsonic flow, $dA/dx>0$ (diverge); to slow a supersonic flow, $dA/dx<0$ (converge).

### Subsonic intakes

All civil aircraft use them. The design is a compromise (20 Feb, ll. 53–101):

- Short, to save weight and wall-friction loss;
- but a short diffuser has a steep adverse pressure gradient, which, with the wall boundary layer, causes separation and a large $p_0$ loss, so long is better for that;
- the boundary layer also eats into the effective area, so the geometric area ratio must be a little larger than the ideal one.

Result: a half-angle below 10°, typically 6–7°.

### Ideal and real diffusers

The SFEE with no heat, no work and negligible exit KE (W02) gives

$$
h_2 = h_1+\tfrac12u_1^2 = h_{01}
$$

so for a perfect gas the stagnation temperature is conserved, $T_{02}=T_{01}$, with $T_2\approx T_{02}$ and $p_2\approx p_{02}$ at the low exit speed (20 Feb, ll. 102–134). In an ideal diffuser $p_{02}=p_{01}$ too.

A real diffuser loses stagnation pressure to friction (and shocks). The course measures this with the stagnation pressure ratio:

$$
\Gamma_d = \frac{p_{02}}{p_{01}}<1
$$

$\Gamma$ with a subscript is used for every component of the engine (20 Feb, ll. 139–147). The ramjet analysis in W06 uses $\Gamma_d$ (diffuser), $\Gamma_c$ (combustor) and $\Gamma_n$ (nozzle) (Lecture 18, ll. 370–387).

Alternatively, an isentropic efficiency in the W02 style (20 Feb, ll. 156–178):

$$
\eta_d = \frac{T_{2s}-T_1}{T_2-T_1}
$$

where $T_{2s}$ is the temperature reached isentropically from state 1 to the real exit pressure.

Relating $\eta_d$ and $\Gamma_d$ (the "long equation" of the slides). Take the exit as stagnation, so $T_2=T_{02}=T_{01}$ and the exit pressure is $p_{02}$. Divide top and bottom by $T_1$:

$$
\eta_d = \frac{T_{2s}/T_1-1}{T_{01}/T_1-1}
$$

The denominator is the stagnation relation:

$$
\frac{T_{01}}{T_1}-1 = \frac{\gamma-1}{2}M^2
$$

The numerator is isentropic from $p_1$ to $p_{02}$:

$$
\frac{T_{2s}}{T_1} = \left(\frac{p_{02}}{p_1}\right)^{\frac{\gamma-1}{\gamma}} = \left(\frac{p_{02}}{p_{01}}\cdot\frac{p_{01}}{p_1}\right)^{\frac{\gamma-1}{\gamma}} = \Gamma_d^{\frac{\gamma-1}{\gamma}}\left(1+\frac{\gamma-1}{2}M^2\right)
$$

So

$$
\boxed{\eta_d = \frac{\Gamma_d^{(\gamma-1)/\gamma}\left(1+\frac{\gamma-1}{2}M^2\right)-1}{\frac{\gamma-1}{2}M^2}}
$$

For a fixed $\eta_d$, $\Gamma_d$ falls as the flight Mach number rises: the losses grow with $M$ (20 Feb, ll. 187–188).

> [!warning] Slide error confirmed in the lecture (20 Feb, ll. 179–186)
> A student asked whether the exponent on $\Gamma_d$ should have $\gamma$ in the denominator. It should, $(\gamma-1)/\gamma$ as above. "That mistake is also present in the lecture… I will double check that and correct it."

### Worked example – subsonic intake at 6 km

From the 20 Feb exercise (ll. 277–300): cruise at 6 km and M 0.85, 100 kg/s of air, diffuser exit M 0.4, $\eta_d=0.9$, half-angle 6°. Find the exit state, the areas and the length.

**Ambient (data book, 6 km):** $T_1=249.19$ K, $p_1=47.22$ kPa.

**Stagnation state at entry:**

$$
T_{01} = 249.19\times(1+0.2\times0.85^2) = 285.20\ \mathrm K,\qquad p_{01} = 47.22\times1.1445^{3.5} = 75.73\ \mathrm{kPa}
$$

**Isentropic exit temperature from $\eta_d$:**

$$
T_{2s} = T_1+\eta_d(T_{01}-T_1) = 249.19+0.9\times36.01 = 281.60\ \mathrm K
$$

Exit stagnation pressure (isentropic from $p_1$ to $T_{2s}$):

$$
p_{02} = 47.22\times\left(\frac{281.60}{249.19}\right)^{3.5} = 72.44\ \mathrm{kPa},\qquad \Gamma_d = \frac{72.44}{75.73} = 0.957
$$

Exit static state at M 0.4 ($T_{02}=T_{01}$):

$$
T_2 = \frac{285.20}{1.032} = 276.35\ \mathrm K,\qquad p_2 = \frac{72.44}{1.032^{3.5}} = 64.88\ \mathrm{kPa},\qquad \rho_2 = \frac{64\,880}{287\times276.35} = 0.818\ \mathrm{kg/m^3}
$$

Velocities and areas ($\rho_1=0.660$ kg/m³):

$$
u_1 = 0.85\sqrt{1.4\times287\times249.19} = 269.0\ \mathrm{m/s},\qquad u_2 = 0.4\sqrt{1.4\times287\times276.35} = 133.3\ \mathrm{m/s}
$$

$$
A_1 = \frac{100}{0.660\times269.0} = 0.563\ \mathrm{m^2},\qquad A_2 = \frac{100}{0.818\times133.3} = 0.917\ \mathrm{m^2}
$$

**Diameters and length:**

$$
d_1 = 0.847\ \mathrm m,\qquad d_2 = 1.081\ \mathrm m,\qquad L = \frac{(d_2-d_1)/2}{\tan6^\circ} = \frac{0.117}{0.1051} = 1.11\ \mathrm m
$$

> [!check] Numerical checks
> - Putting $\Gamma_d=0.9565$ and $M=0.85$ into the boxed $\eta_d$ formula returns exactly 0.900 ✔.
> - $T_2<T_{02}$ and $p_2<p_{02}$ ✔; $p_2>p_1$ ✔ (the intake compresses).
> - The slide values (285.2 K, 72.43 kPa) agree to rounding.

### Supersonic intakes

Shock-free C–D intake: theoretical only (20 Feb, ll. 189–220). Converge to $M=1$ at a throat, then diverge subsonically. It works only at its design Mach number: designed for M 3 but flown at M 2, the throat is too small to pass the mass flow sonically, so less air gets in and efficiency is lost. (It also has the starting problem: the shock that stands ahead of it at start-up cannot be swallowed.)

A student asked why the flow is slowed below Mach 1 at all (20 Feb, ll. 203–207). The answer is that no one has built a compressor, or a conventional combustor, that works with supersonic through-flow; only a scramjet burns supersonically.

Normal-shock (Pitot) intake (notes §3.3.1; 20 Feb, ll. 224–241): a subsonic divergent intake that, in supersonic flight, has a normal shock standing in front of it. Behind the shock the flow is subsonic, so an ordinary subsonic diffuser follows. It is the simplest and lightest. The loss is the normal-shock ratio (notes eq. 3.12):

$$
\frac{p_{01}}{p_{0a}} = \left[\frac{\frac{\gamma+1}{2}M_a^2}{1+\frac{\gamma-1}{2}M_a^2}\right]^{\frac{\gamma}{\gamma-1}}\left[\frac{2\gamma}{\gamma+1}M_a^2-\frac{\gamma-1}{\gamma+1}\right]^{-\frac{1}{\gamma-1}}
$$

with $a$ the ambient state ahead of the shock and 1 the intake entry behind it.

| Flight M | 1.5 | 1.7 | 1.8 |
|---|---|---|---|
| $p_{01}/p_{0a}$ | 0.930 | 0.856 | 0.813 |

Under 10 % loss up to M 1.5, so acceptable to about M 1.7–1.8.

- **Off-design, less flow needed:** the shock moves out in front of the lip and the excess air spills around the intake (subcritical operation); the loss is unchanged.
- **Supercritical:** the shock is drawn inside, where the flow has accelerated further, so it is stronger and the $p_0$ loss and mass flow both suffer.

External compression with oblique shocks (notes §3.3.2; 20 Feb, ll. 242–268). A centre-body (spike) or ramp generates one or more oblique shocks, then a final weak normal shock. Each oblique shock acts only on $M_n=M\sin\sigma<M$, so it is weaker. $n$ shocks of equal strength give a $\Gamma_d$ that rises with $n$, tending to 1 (isentropic) as $n\to\infty$. But every ramp turns the flow further, so the flow arrives at the subsonic diffuser increasingly inclined, which costs loss there: there is an optimum $n$ for each flight Mach number. Used at high supersonic speed; no starting problem, because the compression is outside the duct.

Mixed external/internal compression (notes §3.3.3; 20 Feb, ll. 269–276). Some shocks outside, some inside, with the nacelle lip generating shocks that turn the flow back towards the axis. Shorter and lighter, but performance depends strongly on Mach number.

> [!check] Why several oblique shocks beat one normal shock
> At M 3 a single normal shock keeps $p_{02}/p_{01}=0.328$. The $\sigma=50^\circ$ oblique shock of §2 keeps 0.584 and leaves M 1.48; a normal shock at 1.48 then keeps 0.935. Two shocks together: $0.584\times0.935=0.546$, 1.7 times the normal-shock recovery.

See [[Intake Pressure Recovery]].

---

## 4. Problem-solving workflow

1. **Duct with $f$ or $q$:** compute $\mathcal A$; if $1-2\mathcal A(\gamma+1)<0$ the duct is choked. Otherwise take the root on the right branch (subsonic inlet → subsonic root; supersonic → depends on back pressure). Then $p_2/p_1$, $T_2/T_1$ from momentum and energy.
2. **Oblique shock:** $M_{n1}=M_1\sin\sigma$ (or find $\sigma$ from $\delta$ on the weak branch); normal-shock table at $M_{n1}$; $M_2=M_{n2}/\sin(\sigma-\delta)$.
3. **Subsonic intake:** ISA → $T_{01}$, $p_{01}$ → $p_{02}$ (via $\Gamma_d$ or $\eta_d$) → exit static state at the exit Mach → areas → diameters → length.
4. **Supersonic intake:** chain the shock losses, $\Gamma_d=\prod(p_{02}/p_{01})_i$, then a subsonic diffuser as above.
5. Check: $T_0$ constant through every adiabatic element; $p_0$ never rises; $M_{n2}<1$.

## Terminology and alternative names

| Course term | Also called | Where the course uses it | Note |
|---|---|---|---|
| friction in a constant-area duct | Fanno flow | notes §3.2.1 | The course does not use the names Fanno and Rayleigh. |
| heat addition in a constant-area duct | Rayleigh flow | notes §3.2.2 | |
| shock angle $\sigma$ | wave angle, $\beta$ | notes §3.3, 17 Feb l. 363 | Most textbooks write $\beta$. |
| deflection angle $\delta$ | turning angle, $\theta$ | notes §3.3 | Hence "$\theta$–$\beta$–$M$ relation". |
| $c$ (in the Kundu figures) | speed of sound $a$ | 17 Feb, ll. 402–405 | The course notes use $a$. |
| stagnation pressure ratio $\Gamma_d$ | pressure recovery, $\pi_d$, total-pressure recovery | 20 Feb, ll. 139–147 | |
| diffuser | intake, inlet | notes §3.1 | |
| normal-shock intake | Pitot intake | notes §3.3.1 | |
| subcritical / supercritical | spillage / swallowed shock | notes §3.3.1 | |

## Links

- Parent: [[SESA2023 Propulsion Hub]] · Previous: [[SESA2023 W03 - Compressible Flow, Normal Shocks and Nozzles]] · Next: [[SESA2023 W05 - Combustion, Stoichiometry and Chemical Equilibrium]]
- Shock inside a C–D nozzle (17 Feb review): [[SESA2023 W03 - Compressible Flow, Normal Shocks and Nozzles#Worked example – shock in the diverging section|W03 worked example]]
- Formula list: [[SESA2023 Formula Sheet]] · Ramjet with an inlet normal shock: [[SESA2023 Problem Sheet 4 Solutions]] Q4.3
- Real-ramjet $\Gamma$ values: [[SESA2023 Exam 2018-19 Solutions]] Q4, [[SESA2023 Exam 2020-21 Solutions]] Q2, [[SESA2023 Exam 2023-24 Solutions]] Q2
- Component $\Gamma$s in cycles: [[SESA2023 W06 - Jet Engine Cycle Analysis - Brayton, Ramjet, Turbojet and Reheat]] · [[Component Stagnation Pressure Ratios]]
- Taken further in Year 3: [[SESA3029 W02 - Oblique Shock Relations and Mach Waves]] · [[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method]]

## Sources

- `Week 04 - Gas Dynamics II - Friction, Heat Transfer, Oblique Shocks and Intakes.pdf`: Week 4 notes (I. Peters, T. Grenga; two handouts: §3.2–3.3 ducts and oblique shocks, §3.1–3.3 intakes) and the Lecture 10–12 slides. Figures after Kundu et al., *Fluid Mechanics*, Ch. 16.
- Transcripts (line numbers refer to these files): `SESA2023 Lecture 2026-02-17.txt` (17 Feb, Lectures 10–11, ll. 206–513: friction, heating, oblique shocks); `SESA2023 Lecture 2026-02-20.txt` (20 Feb, Lecture 12: intakes).
- Data book: normal-shock and oblique-shock relations, ISA Table 25.

## Self-study tasks

Tasks marked *(set)* were set or explicitly pointed to in the Week 4 lectures; the rest are suggested, not lecturer-set. Attempt each closed-book, then check against the linked section.

### Core

- [ ] *(set)* Write the constant-area duct conservation equations with the $f$ and $q$ terms, and explain every region of the friction and heating plots: "this may be on the exam… and of course, the meaning of this graph" (17 Feb, ll. 345–353). → [[#Governing equations]] · [[#Reading the plots]]
- [ ] *(set)* Oblique shock at M 3, $\sigma=50^\circ$ (17 Feb, ll. 458–510). Targets $\delta=28.9^\circ$, $p_2=607$ kPa, $T_2=560$ K, $M_2=1.48$. → [[#Worked example – oblique shock at Mach 3]]
- [ ] *(set)* Subsonic intake at 6 km, M 0.85 (20 Feb, ll. 277–300). Targets $p_{02}=72.4$ kPa, $A_2=0.917$ m², $L=1.11$ m. → [[#Worked example – subsonic intake at 6 km]]
- [ ] *(set)* Explain the three supersonic intake types and when each is used (20 Feb, ll. 189–276). → [[#Supersonic intakes]]
- [ ] *(set)* Work [[SESA2023 Problem Sheet 4 Solutions|Problem Sheet 4]] Q4.3 (ramjet with a normal shock at the inlet), which uses this week's intake loss.

### Further practice

- [ ] Derive the Mach-number forms of the duct momentum and energy equations from the conservation laws. → [[#In terms of Mach number]]
- [ ] Derive the biquadratic solution and the choking condition $\mathcal A^*=1/[2(\gamma+1)]$. → [[#Choking]]
- [ ] Friction in a subsonic duct: $M_2$ for $f=0.1$, and $f_{max}$, $q_{max}$ at $M_1=0.5$. Targets 0.589, 0.228, 0.469. → [[#Worked example – friction in a subsonic duct]]
- [ ] Show why the tangential velocity is unchanged across an oblique shock, and derive $\rho_2/\rho_1=\tan\sigma/\tan(\sigma-\delta)$. → [[#Geometry]] · [[#The deflection angle]]
- [ ] Derive the $\eta_d$–$\Gamma_d$ relation. → [[#Ideal and real diffusers]]
- [ ] Compare one normal shock with an oblique-plus-normal pair at M 3. Target 0.328 vs 0.546. → [[#Supersonic intakes]]
- [ ] *(set)* Week 4 Blackboard quiz, and the propulsion-lab quiz released at the start of the lab week (20 Feb, ll. 1–19).
