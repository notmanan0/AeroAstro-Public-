---
title: "SESA2023 W03 - Compressible Flow, Normal Shocks and Nozzles"
module: "SESA2023 Propulsion"
type: topic
stream: "Section 1: Introduction and Fundamentals"
order: 3
tags:
  - sesa2023
  - compressible-flow
  - normal-shock
  - nozzles
  - choked-flow
aliases: ["Gas dynamics I", "Nozzle flow", "SESA2023 Week 3"]
date: 2026-09-24
status: lectured
coverage: "Week 3 (Lectures 7–9) and the 17 Feb review"
parent: ["[[SESA2023 Propulsion Hub]]"]
prerequisites: ["[[SESA2023 W02 - Thermodynamics, Mixtures, SFEE and Isentropic Efficiency]]"]
next_topics: ["[[SESA2023 W04 - Friction, Heat Addition, Oblique Shocks and Intakes]]"]
key_concepts: ["[[Stagnation Properties]]", "[[Speed of Sound and Mach Number]]", "[[Critical Conditions and Choked Flow]]", "[[Normal Shock Waves]]", "[[Stagnation Pressure Loss and Entropy]]", "[[Isentropic Nozzle Flow]]", "[[Converging-Diverging Nozzle Operating Regimes]]"]
tutorial_sheets: ["[[SESA2023 Problem Sheet 3 Solutions]]"]
sources: ["02 - Sources/Lectures/Week 03 - Gas Dynamics I - Compressible Flow, Shocks and Nozzles.pdf", "02 - Sources/Lectures/SESA2023 Lecture 2026-02-10.txt", "02 - Sources/Lectures/SESA2023 Lecture 2026-02-13.txt", "02 - Sources/Lectures/SESA2023 Lecture 2026-02-17.txt", "02 - Sources/Lectures/Week 04 - Gas Dynamics II - Friction, Heat Transfer, Oblique Shocks and Intakes.pdf"]
---

# SESA2023 W03 - Compressible Flow, Normal Shocks and Nozzles

> [!abstract] Summary
> In compressible flow the density is tied to pressure and temperature by $p=\rho RT$, so mass, momentum and energy have to be solved together, and for steady, one-dimensional, inviscid, adiabatic flow they reduce to a handful of algebraic relations: stagnation properties, the speed of sound and Mach number, and critical (sonic) conditions. A normal shock takes supersonic flow to subsonic, conserving $T_0$ but losing $p_0$. The area–velocity relation explains why a converging nozzle can only reach $M=1$ (choking) and why a supersonic jet needs a converging–diverging nozzle, whose choked throat alone sets the mass flow.

> [!summary]- Exam use: quick path
> - **Use it when:** a nozzle, duct or shock problem gives a reservoir ($p_0$, $T_0$) or a local state and asks for $M$, $p$, $T$, $\dot m$, an area or the thrust.
> - **Assumptions:** perfect gas, steady, quasi-1D, adiabatic, inviscid; isentropic everywhere except across a shock; $\gamma=1.4$ for air unless told (rocket gases differ).
> - **Method:** 1. Decide the regime: is the throat choked ($p_b<p^*$, or any supersonic flow downstream)? 2. Isentropic ratios from $M$: $T_0/T$, $p_0/p$, $\rho_0/\rho$. 3. Choked mass flow $\dot m=0.0404\,A_tp_0/\sqrt{T_0}$ (air) or $\rho^*a^*A_t$. 4. Across a shock use the normal-shock relations or table; restart the isentropic relations with the new $p_0$. 5. Thrust $F=\dot mU_e+A_e(p_e-p_b)$.
> - **Common mistakes:** applying isentropic relations straight across a shock; using the reservoir $p_0$ downstream of a shock.
> - **Practise:** [[#Worked example – shock in the diverging section]] · [[SESA2023 Problem Sheet 3 Solutions]] Q3.3–Q3.4

Above about Mach 0.3 the pressure changes in a flow are large enough to change its density appreciably, and density, pressure and temperature then move together; that coupling is what "compressible" means (Lecture 1, ll. 13–19). Small disturbances move through the gas at the speed of sound $a$, so if the flow itself moves faster than $a$ they can't travel upstream, and the flow ahead of an obstacle can't adjust gradually. Instead, successive compression waves travel faster than the ones ahead of them, catch up and steepen into a shock, a jump a few micrometres thick, which conserves mass, momentum and energy but not entropy, so stagnation pressure is lost.

Nozzles behave the other way round above Mach 1. Subsonic gas speeds up in a narrowing duct and supersonic gas in a widening one, and the changeover can only happen at a throat, where $M=1$. Once the throat is sonic, no disturbance from downstream can travel upstream through it, so the mass flow depends only on the reservoir conditions and the throat area, and whatever happens after the throat, a shock or an under- or over-expanded jet, affects only the diverging section.

---

## 1. The simplified equations (Lecture 7)

The full compressible Navier–Stokes equations (mass, momentum, energy with density inside the derivatives, plus $p=\rho RT$) are simplified for a whole-engine "block" analysis (10 Feb, ll. 26–83; notes §3.2.2) by assuming:

- 1-D flow along $x$ (one momentum equation, not three);
- steady flow (all $\partial/\partial t$ terms vanish);
- inviscid flow (no stresses, no viscous heating);
- **no thermal diffusion**.

That leaves

$$
\frac{d}{dx}(\rho U) = 0,\qquad \frac{d}{dx}(\rho U^2)+\frac{dp}{dx} = 0,\qquad \frac{d}{dx}(\rho Uh)-U\frac{dp}{dx} = 0,\qquad p = \rho RT
$$

**Simplifying the momentum equation.** Expand the convective term by the product rule, treating $\rho U^2$ as $(\rho U)\,U$:

$$
\frac{d}{dx}(\rho U^2) = \rho U\frac{dU}{dx}+U\frac{d(\rho U)}{dx}
$$

The last term is zero by continuity, so

$$
\rho U\frac{dU}{dx}+\frac{dp}{dx} = 0
$$

Simplifying the energy equation the same way, with $\rho Uh=(\rho U)h$:

$$
\frac{d}{dx}(\rho Uh) = \rho U\frac{dh}{dx}+h\frac{d(\rho U)}{dx} = \rho U\frac{dh}{dx}
$$

so $\rho U\,dh/dx=U\,dp/dx$. Substitute $dp/dx=-\rho U\,dU/dx$ from momentum and cancel $\rho U$:

$$
\frac{dh}{dx}+U\frac{dU}{dx} = 0
$$

Along a streamline from state 1 to state 2, integrate each equation:

$$
\rho_1U_1 = \rho_2U_2,\qquad \tfrac12U_2^2+\int_1^2\frac{dp}{\rho} = \tfrac12U_1^2,\qquad h_1+\tfrac12U_1^2 = h_2+\tfrac12U_2^2
$$

The pressure integral cannot be done until we know how $\rho$ depends on $p$. In incompressible flow $\rho$ is constant and it gives Bernoulli, $p/\rho+\tfrac12U^2$ = const. In compressible flow $p$, $\rho$ and $T$ are coupled (10 Feb, ll. 123–134).

Derivations can be examined, but the lecturer advised against memorising every step (10 Feb, ll. 295–308): "Are we expected to memorize the derivations?" "Yes. Derivation can be part of the [exam]. But… don't memorize all the steps." Start from conservation of mass and momentum (and energy), and work towards the result, which is in the data book.

---

## 2. Stagnation properties

Bring the flow to rest reversibly and adiabatically (an imaginary wall, 10 Feb, ll. 135–158). The energy equation says $h+\tfrac12U^2$ is the same at every point, and at the wall $U=0$, so all the kinetic energy has become enthalpy:

$$
h_0 = h+\tfrac12U^2
$$

**Stagnation temperature.** For a perfect gas $h=c_pT$; divide by $c_p$:

$$
T_0 = T+\frac{U^2}{2c_p}
$$

In terms of Mach number (10 Feb, ll. 239–250). Divide by $T$:

$$
\frac{T_0}{T} = 1+\frac{U^2}{2c_pT}
$$

Use $a^2=\gamma RT$ (§3), so $T=a^2/(\gamma R)$:

$$
\frac{T_0}{T} = 1+\frac{\gamma R}{2c_p}\frac{U^2}{a^2}
$$

Use $R=c_p-c_v$, so $\gamma R/c_p=\gamma(1-1/\gamma)=\gamma-1$, and $U/a=M$:

$$
\boxed{\frac{T_0}{T} = 1+\frac{\gamma-1}{2}M^2}
$$

**Stagnation pressure and density.** The deceleration is isentropic, so the W02 relations apply:

$$
\boxed{\frac{p_0}{p} = \left(1+\frac{\gamma-1}{2}M^2\right)^{\frac{\gamma}{\gamma-1}},\qquad \frac{\rho_0}{\rho} = \left(1+\frac{\gamma-1}{2}M^2\right)^{\frac{1}{\gamma-1}}}
$$

- $T_0$ is constant in any adiabatic, no-work flow, even an irreversible one (it comes from energy alone).
- $p_0$ and $\rho_0$ are constant only if the flow is also isentropic (they used the isentropic relation).
- "Pressure" with no qualifier means static pressure (10 Feb, ll. 145–147).
- Static and stagnation values coincide only when the fluid is at rest in the chosen frame.

> [!warning] Transcript slip (10 Feb, ll. 141–143)
> "All the kinetic energy has been transformed to entropy. And we consider this quantity as the stagnation entropy." Both words should be enthalpy: the kinetic energy becomes enthalpy, giving the stagnation enthalpy $h_0$. (The entropy does *not* change in this reversible, adiabatic deceleration.)

---

## 3. Speed of sound and Mach number

### Derivation (Lecture 7)

Consider still gas ($p$, $\rho$, $T$, $U=0$) through which a weak wave moves to the right at speed $a$. Behind the wave the gas has been nudged to $p+dp$, $\rho+d\rho$ and a small velocity $dU$ (10 Feb, ll. 159–179; notes §3.3.1).

![[prop_sound_wave_cv.png|820]]

Put a control volume around the wave, moving with it. In that frame the undisturbed gas enters from the right at $a$, and the disturbed gas leaves on the left at $a-dU$. The two faces have the same area $A$.

**Mass:**

$$
\rho aA = (\rho+d\rho)(a-dU)A
$$

Cancel $A$ and expand:

$$
\rho a = \rho a-\rho\,dU+a\,d\rho-d\rho\,dU
$$

Drop the second-order product $d\rho\,dU$ and cancel $\rho a$:

$$
\rho\,dU = a\,d\rho
$$

Momentum (momentum flux out minus in equals the net pressure force, positive to the left in the direction the gas leaves):

$$
\rho aA\big[(a-dU)-a\big] = pA-(p+dp)A
$$

The mass flux $\rho aA$ is the same on both faces. Cancel $A$:

$$
-\rho a\,dU = -dp\qquad\Longrightarrow\qquad dp = \rho a\,dU
$$

**Combine.** From mass, $dU=a\,d\rho/\rho$; substitute into momentum:

$$
dp = \rho a\cdot\frac{a\,d\rho}{\rho} = a^2\,d\rho
$$

$$
a^2 = \frac{dp}{d\rho}
$$

The wave is weak, so it is reversible and adiabatic, i.e. isentropic. Hence

$$
a^2 = \left(\frac{\partial p}{\partial\rho}\right)_s
$$

**Perfect gas.** Along an isentrope $p=K\rho^\gamma$, so

$$
\left(\frac{\partial p}{\partial\rho}\right)_s = \gamma K\rho^{\gamma-1} = \gamma\frac{p}{\rho} = \gamma RT
$$

$$
\boxed{a = \sqrt{\gamma RT},\qquad M = \frac{U}{a}}
$$

The speed of sound depends on the gas (through $\gamma$ and $R$) and on its temperature only (10 Feb, ll. 231–234).

> [!warning] Transcript slips in the derivation (10 Feb, ll. 171, 198–199)
> - l. 171: "Let's make some assumption that this process is adiabatic and irreversible". It must be reversible (isentropic), which is what lets the lecture use $p\propto\rho^\gamma$ at l. 228.
> - ll. 198–199: the mass result is transcribed as "rho du is equal to the product A du". It is $\rho\,dU=a\,d\rho$ (speed of sound $a$, not area $A$).

### Worked example – same speed, different Mach number (10 Feb, ll. 258–270)

A jet flies at M 1.1 where $T=220$ K. Air: $\gamma=1.4$, $R=287$.

$$
U = 1.1\sqrt{1.4\times287\times220} = 1.1\times297.3 = 327\ \mathrm{m/s}
$$

At the same speed but at a lower altitude where $T=300$ K:

$$
M = \frac{327}{\sqrt{1.4\times287\times300}} = \frac{327}{347.2} = 0.94
$$

The aircraft is subsonic: Mach number depends on temperature as well as speed.

---

## 4. Critical properties (Mach 1)

Put $M=1$ in the stagnation relations. Starred quantities are the static values where $M=1$ (10 Feb, ll. 271–285):

$$
\frac{T^*}{T_0} = \frac{2}{\gamma+1},\qquad \frac{p^*}{p_0} = \left(\frac{2}{\gamma+1}\right)^{\frac{\gamma}{\gamma-1}},\qquad \frac{\rho^*}{\rho_0} = \left(\frac{2}{\gamma+1}\right)^{\frac{1}{\gamma-1}}
$$

For $\gamma=1.4$: $T^*/T_0=0.8333$, $p^*/p_0=0.5283$, $\rho^*/\rho_0=0.6339$.

The number to remember is 0.528: a converging nozzle fed from a reservoir of air chokes when the back pressure falls below about 53 % of the reservoir pressure, and no lower back pressure can raise the mass flow.

---

## 5. Normal shocks (Lecture 8)

### What a shock is

A sequence of weak compression waves: each later wave travels through gas that is already slightly hotter and faster, so it catches up with the one ahead. They merge into a finite jump of thickness of order micrometres, treated as a discontinuity (10 Feb, ll. 347–363). A normal shock is perpendicular to the flow, like the centre of the bow shock in front of a sphere (Van Dyke, notes Fig. 3.4). The key property: a shock is not isentropic (10 Feb, ll. 381–383).

### Jump conditions

Across the thin shock there is no area change (notes eqs. 3.53–3.55):

$$
\rho_1U_1 = \rho_2U_2,\qquad p_1+\rho_1U_1^2 = p_2+\rho_2U_2^2,\qquad h_1+\tfrac12U_1^2 = h_2+\tfrac12U_2^2
$$

Four unknowns ($p_2$, $\rho_2$, $U_2$, $h_2$) and three equations: close with a perfect gas.

### The board derivation: energy in pressure–density form (10 Feb, ll. 396–463)

The lecturer did this "like in an exam where you don't know what to do": look up the target in the data book and work towards it.

Start from $h_2-h_1=c_p(T_2-T_1)$. Write $c_p$ in terms of $\gamma$ and $R$. From $\gamma=c_p/c_v$ and $R=c_p-c_v$:

$$
\frac{\gamma R}{\gamma-1} = \frac{(c_p/c_v)(c_p-c_v)}{(c_p-c_v)/c_v} = c_p
$$

So

$$
h_2-h_1 = \frac{\gamma R}{\gamma-1}(T_2-T_1)
$$

Use the equation of state, $T=p/(\rho R)$:

$$
h_2-h_1 = \frac{\gamma R}{\gamma-1}\left(\frac{p_2}{\rho_2R}-\frac{p_1}{\rho_1R}\right) = \frac{\gamma}{\gamma-1}\left(\frac{p_2}{\rho_2}-\frac{p_1}{\rho_1}\right)
$$

Substitute into the energy equation, $h_2-h_1=\tfrac12(U_1^2-U_2^2)$ (notes eq. 3.59):

$$
\boxed{\frac{\gamma}{\gamma-1}\left(\frac{p_2}{\rho_2}-\frac{p_1}{\rho_1}\right) = \tfrac12\left(U_1^2-U_2^2\right)}
$$

### From the jump conditions to the Mach-number relations (the lecture skips this)

The lecture goes straight from here to the four Rankine–Hugoniot relations ("I will not ask to remember these, they are written in the data book", l. 472). Here is one clean route.

**Step 1: energy with the critical speed.** Write the energy equation with $h=c_pT=a^2/(\gamma-1)$. At the (imaginary) sonic state of the same $T_0$, $U=a=a^*$, so

$$
\frac{a^2}{\gamma-1}+\frac{U^2}{2} = \frac{a^{*2}}{\gamma-1}+\frac{a^{*2}}{2} = \frac{\gamma+1}{2(\gamma-1)}a^{*2}
$$

$T_0$ is the same on both sides of the shock, so $a^*$ is too. Rearranged:

$$
a^2 = \frac{\gamma+1}{2}a^{*2}-\frac{\gamma-1}{2}U^2
$$

**Step 2: the Prandtl relation.** Divide momentum by mass, $\rho_1U_1=\rho_2U_2$:

$$
\frac{p_1}{\rho_1U_1}-\frac{p_2}{\rho_2U_2} = U_2-U_1
$$

Use $p/\rho=a^2/\gamma$:

$$
\frac{a_1^2}{\gamma U_1}-\frac{a_2^2}{\gamma U_2} = U_2-U_1
$$

Substitute Step 1 for $a_1^2$ and $a_2^2$:

$$
\frac{\gamma+1}{2\gamma}a^{*2}\left(\frac{1}{U_1}-\frac{1}{U_2}\right)+\frac{\gamma-1}{2\gamma}(U_2-U_1) = U_2-U_1
$$

Use $1/U_1-1/U_2=(U_2-U_1)/(U_1U_2)$ and divide by $U_2-U_1\ne0$:

$$
\frac{\gamma+1}{2\gamma}\frac{a^{*2}}{U_1U_2}+\frac{\gamma-1}{2\gamma} = 1
$$

$$
\frac{\gamma+1}{2\gamma}\frac{a^{*2}}{U_1U_2} = \frac{\gamma+1}{2\gamma}\qquad\Longrightarrow\qquad \boxed{U_1U_2 = a^{*2}}
$$

**Step 3: characteristic Mach number.** Define $M^*=U/a^*$. Divide Step 1 by $U^2$ and use $a/U=1/M$:

$$
\frac{1}{(\gamma-1)M^2}+\frac12 = \frac{\gamma+1}{2(\gamma-1)}\frac{1}{M^{*2}}
$$

Solve for $M^{*2}$:

$$
M^{*2} = \frac{(\gamma+1)M^2}{2+(\gamma-1)M^2}
$$

**Step 4: density ratio.** From mass and the Prandtl relation:

$$
\frac{\rho_2}{\rho_1} = \frac{U_1}{U_2} = \frac{U_1^2}{U_1U_2} = \frac{U_1^2}{a^{*2}} = M_1^{*2}
$$

$$
\boxed{\frac{\rho_2}{\rho_1} = \frac{(\gamma+1)M_1^2}{(\gamma-1)M_1^2+2}}
$$

**Step 5: pressure ratio.** From momentum, $p_2-p_1=\rho_1U_1^2-\rho_2U_2^2=\rho_1U_1(U_1-U_2)$. Divide by $p_1$, use $\rho_1U_1^2/p_1=\gamma M_1^2$:

$$
\frac{p_2}{p_1} = 1+\gamma M_1^2\left(1-\frac{U_2}{U_1}\right) = 1+\gamma M_1^2\left(1-\frac{\rho_1}{\rho_2}\right)
$$

Substitute Step 4:

$$
1-\frac{\rho_1}{\rho_2} = 1-\frac{(\gamma-1)M_1^2+2}{(\gamma+1)M_1^2} = \frac{2(M_1^2-1)}{(\gamma+1)M_1^2}
$$

$$
\boxed{\frac{p_2}{p_1} = 1+\frac{2\gamma}{\gamma+1}\left(M_1^2-1\right)}
$$

**Step 6: downstream Mach number.** $M_2^*=U_2/a^*=a^*/U_1=1/M_1^*$. Invert Step 3, $M^2=2M^{*2}/[(\gamma+1)-(\gamma-1)M^{*2}]$, with $M_2^{*2}=1/M_1^{*2}$:

$$
M_2^2 = \frac{2}{(\gamma+1)M_1^{*2}-(\gamma-1)}
$$

Substitute Step 3 for $M_1^{*2}$ and simplify the denominator, using $(\gamma+1)^2-(\gamma-1)^2=4\gamma$:

$$
(\gamma+1)M_1^{*2}-(\gamma-1) = \frac{4\gamma M_1^2-2(\gamma-1)}{2+(\gamma-1)M_1^2}
$$

$$
\boxed{M_2^2 = \frac{(\gamma-1)M_1^2+2}{2\gamma M_1^2-(\gamma-1)}}
$$

**Step 7: temperature ratio.** Equation of state, $T_2/T_1=(p_2/p_1)(\rho_1/\rho_2)$; multiplying out gives the data-book form

$$
\frac{T_2}{T_1} = 1+\frac{2(\gamma-1)}{(\gamma+1)^2}\,\frac{\gamma M_1^2+1}{M_1^2}\left(M_1^2-1\right)
$$

### Entropy, the Second Law and stagnation pressure

From the W02 entropy relation in dimensionless form (notes eq. 3.65):

$$
\frac{\Delta s}{R} = \frac{\gamma}{\gamma-1}\ln\frac{T_2}{T_1}-\ln\frac{p_2}{p_1}
$$

- $\Delta s=0$ at $M_1=1$: the infinitesimal sound wave is recovered.
- $\Delta s>0$ for $M_1>1$.
- $\Delta s<0$ for $M_1<1$: forbidden by the Second Law, so an expansion shock (subsonic → supersonic) cannot exist (10 Feb, ll. 492–509).

**Stagnation temperature is unchanged**: the shock is adiabatic with no work, so $h_0$ and hence $T_0$ are conserved.

**Stagnation pressure falls.** Since $T_{02}=T_{01}$, the entropy relation applied between the two (imaginary) stagnation states gives

$$
s_2-s_1 = c_p\ln\frac{T_{02}}{T_{01}}-R\ln\frac{p_{02}}{p_{01}} = -R\ln\frac{p_{02}}{p_{01}}
$$

$$
\frac{p_{02}}{p_{01}} = e^{-\Delta s/R}<1
$$

The entropy rise *is* the stagnation-pressure loss. In practice compute it as a chain of three ratios:

$$
\frac{p_{02}}{p_{01}} = \frac{p_{02}}{p_2}\cdot\frac{p_2}{p_1}\cdot\frac{p_1}{p_{01}}
$$

![[prop_normal_shock.png|760]]

Properties to remember (10 Feb, ll. 475–491; 17 Feb, ll. 51–62):

- $M_2<1$ always, tending to $\sqrt{(\gamma-1)/(2\gamma)}=0.378$ as $M_1\to\infty$.
- $\rho_2/\rho_1$ rises to a plateau, $(\gamma+1)/(\gamma-1)=6$.
- $p_2/p_1$ grows fastest and without limit; $T_2/T_1$ also grows without limit.
- $T_0$ unchanged; $p_0$ falls.

> [!warning] Transcript slip (17 Feb, l. 51)
> "The Mach number after a shock is always negative." It is always less than one.

The formula and the normal-shock table are both in the data book and give "exactly the same" answer (10 Feb, ll. 536–561). Use the table when $M_1$ is a round number and the formula when you would otherwise have to interpolate; a small Python code on Blackboard gives the same values.

### Worked example – normal shock at Mach 2 (10 Feb, ll. 510–535)

Air at $T_1=250$ K, $p_1=0.5$ bar, $U_1=634$ m/s meets a normal shock. Find the stagnation conditions before and after.

**Upstream Mach number:**

$$
a_1 = \sqrt{1.4\times287\times250} = 316.9\ \mathrm{m/s},\qquad M_1 = \frac{634}{316.9} = 2.00
$$

**Upstream stagnation state:**

$$
T_{01} = 250\times(1+0.2\times4) = 450\ \mathrm K,\qquad p_{01} = 0.5\times1.8^{3.5} = 3.91\ \mathrm{bar}
$$

Across the shock (formula or table at $M_1=2$): $M_2=0.5774$, $p_2/p_1=4.5$, $\rho_2/\rho_1=2.667$, $T_2/T_1=1.6875$, so

$$
T_2 = 421.9\ \mathrm K,\qquad p_2 = 2.25\ \mathrm{bar},\qquad U_2 = \frac{U_1}{\rho_2/\rho_1} = \frac{634}{2.667} = 238\ \mathrm{m/s}
$$

**Downstream stagnation state:**

$$
T_{02} = 421.9\times(1+0.2\times0.5774^2) = 450\ \mathrm K
$$

$$
p_{02} = 2.25\times(1+0.2\times0.3333)^{3.5} = 2.82\ \mathrm{bar},\qquad \frac{p_{02}}{p_{01}} = 0.721
$$

> [!check] Numerical checks
> - $T_{02}=T_{01}=450$ K ✔ (adiabatic). $p_{02}<p_{01}$ ✔ (irreversible). $M_2<1$ ✔.
> - $\Delta s/R=-\ln0.721=0.327$, positive ✔.
> - Normal-shock table at $M_1=2.00$: $M_2=0.5774$, $p_{02}/p_{01}=0.7209$ ✔.

> [!warning] Transcript slips in this example (10 Feb, ll. 530–535)
> - "The temperature after the shock is lower… is 250 and now becomes 442." The temperature rises, to 422 K ($250\times1.6875$).
> - "You see the static temperature is the same… while the static pressure is lower because it is isentropic." It is the stagnation temperature that is the same, and the stagnation pressure that is lower, because the shock is not isentropic.

---

## 6. Duct flow and nozzles (Lecture 9)

### The area–velocity relation

Assume quasi-1D flow: the area $A(x)$ changes slowly enough that the flow is still one-dimensional; steady, frictionless, adiabatic, isentropic except across shocks (13 Feb, ll. 50–57).

**Mass:** $\rho UA$ is constant, so its $x$-derivative is zero. By the product rule, then dividing by $\rho UA$:

$$
\frac{1}{\rho}\frac{d\rho}{dx}+\frac{1}{U}\frac{dU}{dx}+\frac{1}{A}\frac{dA}{dx} = 0
$$

**Momentum:** $\rho U\,dU/dx=-dp/dx$. Write $dp/dx=(dp/d\rho)(d\rho/dx)=a^2\,d\rho/dx$ (the flow is isentropic, so $dp/d\rho=a^2$):

$$
\rho U\frac{dU}{dx} = -a^2\frac{d\rho}{dx}
$$

Divide by $\rho a^2$ and use $U^2/a^2=M^2$:

$$
\frac{1}{\rho}\frac{d\rho}{dx} = -M^2\frac{1}{U}\frac{dU}{dx}
$$

**Combine:** substitute into the mass equation:

$$
-M^2\frac{1}{U}\frac{dU}{dx}+\frac{1}{U}\frac{dU}{dx}+\frac{1}{A}\frac{dA}{dx} = 0
$$

$$
\boxed{\frac{1}{A}\frac{dA}{dx} = \frac{1}{U}\frac{dU}{dx}\left(M^2-1\right)}
$$

| Regime | $M^2-1$ | To accelerate ($dU>0$) | To decelerate ($dU<0$) |
|---|---|---|---|
| subsonic | negative | converging duct | diverging duct (subsonic diffuser) |
| supersonic | positive | diverging duct | converging duct (supersonic diffuser) |

At $M=1$ the right-hand side is zero, so $dA/dx=0$: sonic flow can only occur at a throat (a minimum of area).

Supersonic flow speeds up in a widening duct because in supersonic flow a 1 % rise in speed causes a fall in density of $M^2$ per cent, which is more than 1 %. So $\rho U$ falls, and keeping $\rho UA$ constant needs the area to grow. In subsonic flow the density barely changes, and the familiar narrower-is-faster applies.

### Converging nozzle and choking

A converging nozzle fed by a large reservoir at $p_0$, discharging into a back pressure $p_b$ (13 Feb, ll. 113–147; notes Fig. 3.8):

- $p_b=p_0$: no flow.
- $p^*<p_b<p_0$: subsonic everywhere, exit pressure $p_e=p_b$; lowering $p_b$ raises the flow.
- $p_b=p^*$: $M_e=1$ at the exit.
- $p_b<p^*$: the exit stays at $p_e=p^*$, $M_e=1$. The flow is choked: $\dot m$ and everything inside the nozzle no longer depend on $p_b$, and $\dot m$ is the maximum possible.

> [!warning] Transcript slip (13 Feb, ll. 136–137)
> "If the pressure becomes lower than the back pressure, so the pressure outside, will be lower than the critical pressure…" garbles the condition. Choking happens when the back pressure falls below the critical pressure $p^*$.

### Converging–diverging (de Laval) nozzle: eight regimes

As $p_b$ falls (notes Fig. 3.9; 13 Feb, ll. 152–207; reviewed 17 Feb, ll. 100–130):

1. $p_b=p_0$: no flow.
2. Subsonic everywhere; the throat is not sonic.
3. Sonic at the throat only; subsonic deceleration after it. The flow is now choked, and the converging part never changes again.
4. Supersonic after the throat, then a normal shock in the diverging section; subsonic deceleration to $p_b$. The shock moves downstream as $p_b$ falls.
5. Normal shock exactly at the exit plane.
6. **Over-expanded**: no shock inside; oblique shocks and "shock diamonds" outside.
7. **Design**: $p_e=p_b$, no waves.
8. **Under-expanded**: $p_b<p_e$; expansion waves outside.

![[prop_cd_nozzle_regimes.png|680]]

See [[Converging-Diverging Nozzle Operating Regimes]]. A rocket climbing through the atmosphere sweeps through regimes 6–8 as $p_b$ falls with altitude (13 Feb, ll. 195–199).

### Mass flow rate

Start from $\dot m=\rho AU$ and replace $U$ with the stagnation-temperature relation $U=\sqrt{2c_p(T_0-T)}$ (notes eqs. 3.75–3.76):

$$
\dot m = \rho A\sqrt{2c_pT_0}\left(1-\frac{T}{T_0}\right)^{1/2}
$$

Use the isentropic relations to express $\rho$ and $T$ through the local pressure, $\rho/\rho_0=(p/p_0)^{1/\gamma}$ and $T/T_0=(p/p_0)^{(\gamma-1)/\gamma}$:

$$
\boxed{\frac{\dot m}{\rho_0(2c_pT_0)^{1/2}} = A\left(\frac{p}{p_0}\right)^{1/\gamma}\left[1-\left(\frac{p}{p_0}\right)^{\frac{\gamma-1}{\gamma}}\right]^{1/2}}
$$

Only one local property, $p$, appears; the rest are the area, the reservoir and the gas.

At a choked throat $p/p_0=p^*/p_0=[2/(\gamma+1)]^{\gamma/(\gamma-1)}$. Then $(p^*/p_0)^{1/\gamma}=[2/(\gamma+1)]^{1/(\gamma-1)}$ and $1-(p^*/p_0)^{(\gamma-1)/\gamma}=1-2/(\gamma+1)=(\gamma-1)/(\gamma+1)$, so

$$
\boxed{\frac{\dot m}{\rho_0(2c_pT_0)^{1/2}} = A_t\left(\frac{2}{\gamma+1}\right)^{\frac{1}{\gamma-1}}\left(\frac{\gamma-1}{\gamma+1}\right)^{1/2}}
$$

**Compact form.** Substitute $\rho_0=p_0/(RT_0)$ and $c_p=\gamma R/(\gamma-1)$ and collect the powers of $2/(\gamma+1)$:

$$
\dot m = \frac{A_tp_0}{\sqrt{T_0}}\sqrt{\frac{\gamma}{R}}\left(\frac{2}{\gamma+1}\right)^{\frac{\gamma+1}{2(\gamma-1)}}
$$

For air, $\sqrt{1.4/287}\times0.8333^{3}=0.0404$, so $\dot m=0.0404\,A_tp_0/\sqrt{T_0}$ (SI units). With the reservoir fixed, only the throat area changes a choked mass flow. Equivalently, $\dot m=\rho^*a^*A_t$ with the critical density and sound speed, which is how the 17 Feb example does it.

### Area ratio

Apply $\dot m=\rho UA$ at any section and at the (real or imaginary) sonic section, $\rho UA=\rho^*a^*A^*$:

$$
\frac{A}{A^*} = \frac{\rho^*}{\rho}\,\frac{a^*}{U} = \frac{\rho^*/\rho_0}{\rho/\rho_0}\cdot\frac{1}{M}\sqrt{\frac{T^*}{T}}
$$

Substitute the stagnation and critical ratios and collect the powers:

$$
\frac{A}{A^*} = \frac{1}{M}\left[\frac{2}{\gamma+1}\left(1+\frac{\gamma-1}{2}M^2\right)\right]^{\frac{\gamma+1}{2(\gamma-1)}}
$$

Every area ratio above 1 has two solutions, one subsonic and one supersonic; the data-book isentropic table lists both branches.

![[prop_area_mach.png|620]]

After a shock the reference area changes. $A^*$ is tied to $p_0$: for a fixed $\dot m$ and $T_0$, $A^*\propto1/p_0$, so a shock, which lowers $p_0$, makes the flow behind it behave as if it came from a larger imaginary throat, $A_2^*=A_t\,(p_{01}/p_{02})$. Use $A_2^*$ to march on to the exit.

### Worked example – isentropic nozzle and thrust (13 Feb, ll. 208–267)

$p_0=10$ bar, $T_0=400$ K, $M_e=2$, $A_t=0.1$ m²; air.

Exit state (fully supersonic, so isentropic throughout):

$$
T_e = \frac{400}{1.8} = 222\ \mathrm K,\qquad p_e = \frac{10}{7.824} = 1.28\ \mathrm{bar}
$$

$$
U_e = 2\sqrt{1.4\times287\times222} = 598\ \mathrm{m/s}
$$

Mass flow (a supersonic exit means the throat is choked):

$$
\rho_0 = \frac{10\times10^5}{287\times400} = 8.71\ \mathrm{kg/m^3},\qquad \dot m = 0.0404\times\frac{0.1\times10^6}{\sqrt{400}} = 202\ \mathrm{kg/s}
$$

Thrust (lecture: momentum term only):

$$
F = \dot mU_e = 202\times598 = 121\ \mathrm{kN}
$$

> [!check] The lecture's thrust assumes a matched exit
> $F=\dot mU_e$ holds only if $p_b=p_e=1.28$ bar. The exit area is $A_e=A_t(A/A^*)_{M=2}=0.1\times1.6875=0.169$ m². Discharging into 1 bar instead, the pressure thrust adds $(1.28-1.00)\times10^5\times0.169=4.7$ kN, giving 125 kN.

### Worked example – shock in the diverging section

From the 17 Feb review (ll. 145–205; slides 11–16 in the Week 4 deck). A C–D nozzle runs off-design with a normal shock in the diverging section. Reservoir air at $p_0=400$ kPa, $T_0=800$ K; $A_t=0.2$ m²; $M_1=2.44$ just upstream of the shock; $A_e=0.7$ m². Find the area at the shock.

The flow is isentropic from the reservoir to the shock and from the shock to the exit; only the shock itself is not (17 Feb, ll. 161–166).

**Throat (choked, $M=1$):**

$$
\rho_0 = \frac{400\,000}{287\times800} = 1.742\ \mathrm{kg/m^3}
$$

$$
T^* = 0.8333\times800 = 666.7\ \mathrm K,\qquad p^* = 0.5283\times400 = 211.3\ \mathrm{kPa},\qquad \rho^* = 0.6339\times1.742 = 1.104\ \mathrm{kg/m^3}
$$

$$
a^* = \sqrt{1.4\times287\times666.7} = 517.6\ \mathrm{m/s},\qquad \dot m = \rho^*a^*A_t = 1.104\times517.6\times0.2 = 114.3\ \mathrm{kg/s}
$$

**Just before the shock (state 1, $M_1=2.44$):**

$$
\frac{T_0}{T_1} = 1+0.2\times2.44^2 = 2.191,\qquad T_1 = 365.2\ \mathrm K
$$

$$
p_1 = \frac{400}{2.191^{3.5}} = 25.7\ \mathrm{kPa},\qquad \rho_1 = \frac{25\,700}{287\times365.2} = 0.245\ \mathrm{kg/m^3}
$$

$$
a_1 = \sqrt{1.4\times287\times365.2} = 383.1\ \mathrm{m/s},\qquad U_1 = 2.44\times383.1 = 934.6\ \mathrm{m/s}
$$

Area at the shock from mass conservation:

$$
A_1 = \frac{\dot m}{\rho_1U_1} = \frac{114.3}{0.245\times934.6} = 0.499\ \mathrm{m^2}
$$

After the shock (table at $M_1=2.44$): $M_2=0.519$, $T_2/T_1=2.079$, $p_2/p_1=6.779$, $p_{02}/p_{01}=0.523$, so $T_2=759$ K, $p_2=174$ kPa, $p_{02}=209$ kPa.

**Exit (extension; the lecturer says "if needed… we can find also the temperature and the pressure" at the exit, ll. 201–205).** The new reference throat is

$$
A_2^* = \frac{A_t}{p_{02}/p_{01}} = \frac{0.2}{0.5234} = 0.382\ \mathrm{m^2}
$$

so $A_e/A_2^*=0.7/0.382=1.832$, whose subsonic solution is $M_e=0.338$. Then

$$
p_e = \frac{209.4}{(1+0.2\times0.338^2)^{3.5}} = 193\ \mathrm{kPa},\qquad T_e = \frac{800}{1+0.2\times0.338^2} = 782\ \mathrm K
$$

and that $p_e$ is the back pressure that holds the shock at $A=0.499$ m².

![[prop_w03_shock_in_nozzle.png|760]]

> [!check] Numerical checks
> - Isentropic table: $(A/A^*)_{M=2.44}=2.494$, and $2.494\times0.2=0.499$ m² ✔ (the same answer without computing $\rho_1U_1$).
> - Behind the shock, $(A/A^*)_{M_2=0.519}=1.305$; $0.499/1.305=0.382$ m² $=A_2^*$ ✔.
> - $T_0$ is 800 K throughout; $p_0$ drops from 400 to 209 kPa at the shock.

> [!warning] Transcript slip (17 Feb, ll. 161–162)
> "The only known isentropic part of this flow is the one across the shock, while what happened before the shock and after the shock is isentropic." The first half should say non-isentropic: the shock is the only part where the isentropic relations do not apply.

---

## 7. Problem-solving workflow

1. Sketch the duct; mark the throat, any shock and the exit; label stations.
2. Decide whether the throat is choked (back pressure below $p^*$, or any supersonic flow downstream).
3. Choked: $\dot m=0.0404A_tp_0/\sqrt{T_0}$ for air (or $\rho^*a^*A_t$). Not choked: the general $\dot m(p)$ with $p_e=p_b$.
4. March isentropically with $A/A^*$, $T_0/T$, $p_0/p$; at a shock switch to the normal-shock relations, then restart with $p_{02}$ and $A_2^*$.
5. Thrust from $F=\dot mU_e+A_e(p_e-p_b)$.
6. Sanity checks: $M_2<1$; $T_0$ constant; $p_0$ never rises; $\Delta s\ge0$ (17 Feb, ll. 70–72).

## Terminology and alternative names

| Course term | Also called | Where the course uses it | Note |
|---|---|---|---|
| stagnation property ($T_0$, $p_0$) | total property | notes §3.2.4, 10 Feb ll. 145–147 | The lecture uses both words. |
| critical property ($T^*$, $p^*$) | sonic property, star condition | notes §3.3.2 | |
| Rankine–Hugoniot equations | normal-shock relations | notes eqs. 3.60–3.63 | Strictly, the Hugoniot relation is the $p$–$\rho$ form; the course uses the name for all four. |
| converging–diverging nozzle | de Laval nozzle, C–D nozzle | notes §3.5.2 | |
| back pressure $p_b$ | ambient, receiver pressure | notes Fig. 3.8 | $P_A$ in W01. |
| choked flow | critical flow | notes §3.5.2 | |
| over-/under-expanded | — | regimes 6 and 8 | |
| $M^*$ | characteristic Mach number | this note only | Not used in the course. |

## Links

- Parent: [[SESA2023 Propulsion Hub]] · Previous: [[SESA2023 W02 - Thermodynamics, Mixtures, SFEE and Isentropic Efficiency]] · Next: [[SESA2023 W04 - Friction, Heat Addition, Oblique Shocks and Intakes]]
- Shared with SESA2022 legacy content: [[Normal Shock Waves]] · [[Isentropic Nozzle Flow]]
- Worked sheet: [[SESA2023 Problem Sheet 3 Solutions]] · Formula list: [[SESA2023 Formula Sheet]] · Exams: [[SESA2023 Exam 2020-21 Solutions]] Q1, [[SESA2023 Exam 2021-22 Solutions]] Q1, [[SESA2023 Exam 2022-23 Solutions]] Q1, [[SESA2023 Exam 2024-25 Solutions]] Q1(iii–iv)
- Used for rockets: [[SESA2023 W10 - Rocket Performance, Staging and Power Cycles]] · [[SESA2023 W11 - Solid Propellants and Rocket Nozzle Design]]
- Taken further in Year 3: [[SESA3029 W01 - Compressible-Flow Toolkit, Normal Shocks and Pitot Probes]] (shock tables, Pitot probes) · [[SESA3029 W04 - Laval Nozzle, Under- and Over-Expanded Flow]]

## Sources

- `Week 03 - Gas Dynamics I - Compressible Flow, Shocks and Nozzles.pdf`: Week 3 notes (I. Peters, T. Grenga) §§3.2–3.5 and the Lecture 7–9 slides.
- `Week 04 - Gas Dynamics II - Friction, Heat Transfer, Oblique Shocks and Intakes.pdf`: slides 11–16 (the shock-in-nozzle example).
- Transcripts (line numbers refer to these files): `SESA2023 Lecture 2026-02-10.txt` (10 Feb, Lectures 7–8: equations, stagnation, sound speed, normal shocks); `SESA2023 Lecture 2026-02-13.txt` (13 Feb, Lecture 9: nozzles); `SESA2023 Lecture 2026-02-17.txt` (17 Feb, ll. 1–206: review and the shock-in-nozzle example).
- Data book pp. 11–12 and gas-flow Tables 19–22 (isentropic and normal-shock tables).

## Self-study tasks

Tasks marked *(set)* were set or explicitly pointed to in the Week 3 lectures; the rest are suggested, not lecturer-set. Attempt each closed-book, then check against the linked section.

### Core

- [ ] *(set)* Reproduce and comment on the normal-shock property plot ($M_2$, $p_2/p_1$, $\rho_2/\rho_1$, $T_2/T_1$ against $M_1$): "in last year's exam, there was to reproduce this graph and comment it" (10 Feb, l. 491). → [[#Entropy, the Second Law and stagnation pressure]]
- [ ] *(set)* Derivations may be examined (10 Feb, ll. 295–305): derive $a=\sqrt{\gamma RT}$ from mass and momentum on a moving wave. → [[#Derivation (Lecture 7)]]
- [ ] *(set)* Derive the energy equation across a shock in the $p/\rho$ form, as done on the board (10 Feb, ll. 396–463). → [[#The board derivation: energy in pressure–density form (10 Feb, ll. 396–463)]]
- [ ] *(set)* Normal shock at $U_1=634$ m/s (10 Feb, ll. 510–535). Targets $M_2=0.577$, $p_{02}=2.82$ bar. → [[#Worked example – normal shock at Mach 2 (10 Feb, ll. 510–535)]]
- [ ] *(set)* Shock in the diverging section (17 Feb, ll. 145–205). Target $A=0.499$ m². → [[#Worked example – shock in the diverging section]]
- [ ] *(set)* Work [[SESA2023 Problem Sheet 3 Solutions|Problem Sheet 3]]: "the problem[s] are on the same style that are in the exam. So do that" (17 Feb, ll. 12–21).

### Further practice

- [ ] Derive $T_0/T=1+\tfrac{\gamma-1}{2}M^2$ from $h_0=h+\tfrac12U^2$. → [[#2. Stagnation properties]]
- [ ] Derive the area–velocity relation and explain the table of four cases. → [[#The area–velocity relation]]
- [ ] Derive the general and choked mass-flow equations and the 0.0404 constant. → [[#Mass flow rate]]
- [ ] Derive $p_2/p_1$, $\rho_2/\rho_1$ and $M_2$ from the jump conditions (beyond the lecture). → [[#From the jump conditions to the Mach-number relations (the lecture skips this)]]
- [ ] Show why $p_{02}/p_{01}=e^{-\Delta s/R}$. → [[#Entropy, the Second Law and stagnation pressure]]
- [ ] Continue the shock-in-nozzle example to the exit. Targets $M_e=0.338$, $p_e=193$ kPa. → [[#Worked example – shock in the diverging section]]
- [ ] Add the pressure thrust to the 10-bar nozzle example for a 1 bar back pressure. Target 125 kN. → [[#Worked example – isentropic nozzle and thrust (13 Feb, ll. 208–267)]]
- [ ] *(set)* Read the nozzle-lab notebook on Blackboard before the lab: "after Friday lecture, you should also be able to completely understand it" (10 Feb, ll. 338–342).
- [ ] *(set)* Week 3 Blackboard quiz (13 Feb, ll. 1–5); the shock code on Blackboard "can be useful to solve the quiz" (10 Feb, ll. 536–537).
