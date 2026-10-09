---
title: "SESA3029 W02 - Oblique Shock Relations and Mach Waves"
module: "SESA3029 Aerothermodynamics"
type: topic
stream: "Block 2: Oblique Shocks and Expansions"
order: 2
tags: [sesa3029, compressible-flow, oblique-shock, mach-wave, theta-beta-m]
aliases: ["SESA3029 Week 2", "SESA3029 Lecture 2.1", "SESA3029 Lecture 2.2", "Oblique Shock Waves (SESA3029)"]
date: 2026-09-28
status: complete
coverage: "Week 2 (Lectures 2.1 and 2.2)"
parent: ["[[SESA3029 Aerothermodynamics Hub]]"]
prerequisites: ["[[SESA3029 W01 - Compressible-Flow Toolkit, Normal Shocks and Pitot Probes]]", "[[Normal-Shock Jump Relations]]", "[[Oblique Shock Waves]]"]
next_topics: ["[[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method]]"]
key_concepts: ["[[Oblique-Shock Jump Relations]]", "[[Theta-Beta-Mach Relation]]", "[[Weak and Strong Oblique Shocks]]", "[[Mach Waves and Mach Angle]]"]
tutorial_sheets: ["[[SESA3029 Example Sheet 1 - Solutions]]"]
sources: ["02 - Sources/Lectures/Lecture2-1.pdf", "02 - Sources/Lectures/Lecture 2-1.txt", "02 - Sources/Lectures/Lecture2-2.pdf", "02 - Sources/Lectures/Lecture 2-2.txt"]
---

# SESA3029 W02 - Oblique Shock Relations and Mach Waves

> [!abstract] Summary
> When a supersonic stream is turned **abruptly** through an angle $\theta$, it does so across an **oblique shock** inclined at the shock angle $\beta$. Both angles are measured from the upstream velocity. There is no pressure difference *along* the shock, so the tangential velocity passes through unchanged. Only the normal component jumps. An oblique shock is therefore a normal shock in $M_{n1}=M_1\sin\beta$, and every Week 1 jump relation carries over with $M_1\to M_{n1}$ and $M_2\to M_{n2}$. Combining tangential momentum, mass conservation and the density jump gives the $\theta$–$\beta$–$M$ relation. For each $M_1$ it has a maximum deflection $\theta_{max}$. Below $\theta_{max}$ there are two solutions: a **weak** one, which is normally observed and usually leaves $M_2>1$, and a **strong** one, which leaves $M_2<1$. Above $\theta_{max}$ the shock **detaches**. At $\theta=0$ the relation gives back the normal shock ($\beta=90^\circ$) and the **Mach wave** ($\beta=\mu=\sin^{-1}(1/M_1)$). The sound-pulse picture of a moving source reaches the same Mach angle independently.

## Key concepts

- [[Oblique-Shock Jump Relations]] · [[Theta-Beta-Mach Relation]]
- [[Weak and Strong Oblique Shocks]] · [[Mach Waves and Mach Angle]]
- Foundations: [[Normal-Shock Jump Relations]] · [[Speed of Sound and Mach Number]] · [[Oblique Shock Waves]] (SESA2023)

---

## The whole lecture in one physical picture

Stand on the shock and look at a single parcel of air crossing it.

1. **The parcel only "feels" the shock in the direction normal to it.** Along the shock nothing changes: the pressure is the same on both sides of any sliver of shock front, so nothing pushes the parcel along it. Its velocity component along the shock, $U_t$, sails straight through.
2. **Across the shock it meets exactly the normal-shock problem from Week 1**, with the speed $U_{n1}=V_1\sin\beta$ instead of $V_1$. So it is compressed and slowed by the normal-shock jumps evaluated at $M_{n1}$.
3. **Slowing the normal component while keeping the tangential one bends the velocity vector towards the shock.** That bend is the flow deflection $\theta$. A wedge or ramp therefore needs a shock at just the right angle $\beta$ so that the bend matches the wall. That matching condition *is* the $\theta$–$\beta$–$M$ relation.
4. **Turn the wall more gently and the shock gets weaker.** In the limit of no deflection, the shock degenerates into a Mach wave, the line along which the sound pulses from each point of the body pile up.

Galilean view: an oblique shock is a normal shock watched by an observer sliding along the shock at speed $U_t$. Sliding along the shock changes nothing thermodynamic, which is why the static jumps depend on $M_{n1}$ alone.

## 1. Where oblique shocks come from

The lecture's keyword is **abruptly** (L2-1, ll. 12–15). A supersonic stream cannot "see" a wall corner coming, because disturbances cannot travel upstream faster than the flow. If the wall turns sharply by $\theta$, the flow must turn by $\theta$ almost instantly, and it does so through a thin oblique shock.

- $\theta$: **flow-turning (deflection) angle**, the angle between the upstream velocity $\mathbf V_1$ and the body surface.
- $\beta$: **shock angle**, the angle between $\mathbf V_1$ and the shock.
- Both angles are measured **from the upstream velocity vector** (L2-1, ll. 16–19). If $\mathbf V_1$ is not horizontal, measure from $\mathbf V_1$, not from the page axes. Later examples use this.

![[at_oblique_shock_geometry.png|900]]

*Normal shocks in Week 1 fixed $\beta=90^\circ$ and $\theta=0$, so the angles never mattered. The new question for Lecture 2.1 is: given $M_1$ and $\theta$, what is $\beta$?* (Slide 2; L2-1, ll. 20–23.)

## 2. Resolving the velocities

Resolve each velocity into a component **normal** to the shock (subscript $n$) and **tangential** to it (subscript $t$). From the two right triangles in the figure below:

$$
M_{n1}=M_1\sin\beta,\qquad M_{t1}=M_1\cos\beta,
$$

$$
M_{n2}=M_2\sin(\beta-\theta),\qquad M_{t2}=M_2\cos(\beta-\theta).
$$

Downstream, the velocity has turned through $\theta$ towards the shock, so the angle between $\mathbf V_2$ and the shock is $\beta-\theta$.

> [!warning] $M_{t2}\neq M_{t1}$ even though $U_{t2}=U_{t1}$
> The tangential **velocity** is conserved, not the tangential **Mach number**. The speed of sound rises across the shock ($T_2>T_1$), so $M_{t2}=U_t/a_2<M_{t1}=U_t/a_1$.

## 3. Conservation laws across the oblique shock

Wrap the shock in a thin control volume of face area $A$ and thickness $\delta\to0$ (slide 4; L2-1, ll. 30–45). Only faces parallel to the shock carry flux, so only the **normal** velocity carries mass through them.

### Mass

$$
\dot m=\rho_1U_{n1}A=\rho_2U_{n2}A\quad\Longrightarrow\quad\rho_1U_{n1}=\rho_2U_{n2}.
$$

### Momentum normal to the shock

Momentum flux out minus momentum flux in equals the net external force. Normal to the shock, the only force is pressure:

$$
\dot m\,(U_{n2}-U_{n1})=(p_1-p_2)A
\quad\Longrightarrow\quad
p_1+\rho_1U_{n1}^2=p_2+\rho_2U_{n2}^2.
$$

### Momentum tangential to the shock

The pressure is uniform along each face and acts normal to it, so it has **no tangential component**. The side faces have vanishing area as $\delta\to0$. Hence

$$
\dot m\,(U_{t2}-U_{t1})=0
\quad\Longrightarrow\quad
\boxed{U_{t1}=U_{t2}\equiv U_t}.
$$

### Energy

The shock is adiabatic with no work, so total enthalpy is conserved using the **full** velocity, $V^2=U_n^2+U_t^2$:

$$
h_1+\tfrac12\left(U_{n1}^2+U_t^2\right)=h_2+\tfrac12\left(U_{n2}^2+U_t^2\right).
$$

The $\tfrac12U_t^2$ terms are identical on both sides and cancel:

$$
h_1+\tfrac12U_{n1}^2=h_2+\tfrac12U_{n2}^2.
$$

> [!note] Transcript wording
> At L2-1, l. 42, the transcript reads *"stagnation temperature or stagnation entropy is constant"*. The conserved quantity is stagnation **enthalpy**, $h_0$, or equivalently $T_0$ for a calorically perfect gas. Entropy rises across any shock.

## 4. It is a normal shock in the normal component

Put the mass, normal-momentum and energy equations beside the Week 1 set (slides 5–6; L2-1, ll. 46–58):

| | Oblique shock | Normal shock (W01) |
|---|---|---|
| mass | $\rho_1U_{n1}=\rho_2U_{n2}$ | $\rho_1U_1=\rho_2U_2$ |
| momentum | $p_1+\rho_1U_{n1}^2=p_2+\rho_2U_{n2}^2$ | $p_1+\rho_1U_1^2=p_2+\rho_2U_2^2$ |
| energy | $h_1+\tfrac12U_{n1}^2=h_2+\tfrac12U_{n2}^2$ | $h_1+\tfrac12U_1^2=h_2+\tfrac12U_2^2$ |

They are **the same equations** with $U\to U_n$. The solution must also be the same. No new derivation is needed: take every normal-shock result from [[SESA3029 W01 - Compressible-Flow Toolkit, Normal Shocks and Pitot Probes#5. Normal shock from conservation laws|W01 §5]] and replace $M_1\to M_{n1}$ and $M_2\to M_{n2}$. These are the [[Oblique-Shock Jump Relations]]:

$$
\boxed{M_{n1}=M_1\sin\beta}
$$

$$
\frac{\rho_2}{\rho_1}=\frac{U_{n1}}{U_{n2}}=\frac{(\gamma+1)M_{n1}^2}{2+(\gamma-1)M_{n1}^2},
\qquad
\frac{p_2}{p_1}=1+\frac{2\gamma}{\gamma+1}\left(M_{n1}^2-1\right),
$$

$$
\frac{T_2}{T_1}=\frac{p_2/p_1}{\rho_2/\rho_1},
\qquad
M_{n2}^2=\frac{2+(\gamma-1)M_{n1}^2}{2\gamma M_{n1}^2-(\gamma-1)},
$$

$$
\boxed{M_2=\frac{M_{n2}}{\sin(\beta-\theta)}}.
$$

The shock tables can be used directly: enter the normal-shock table with $M_{n1}$ in the $M_1$ column. The "$M_2$" column then gives $M_{n2}$.

### Why p₀₂/p₀₁ depends only on Mₙ₁ (derivation)

It is tempting to think that the stagnation pressure, which includes the tangential kinetic energy, needs a new formula. It does not. From W01,

$$
s_2-s_1=c_p\ln\frac{T_2}{T_1}-R\ln\frac{p_2}{p_1}.
$$

A stagnation state has the same entropy as its static state, because it is reached isentropically. Apply the same formula between the two stagnation states and use $T_{02}=T_{01}$:

$$
s_2-s_1=s_{02}-s_{01}=c_p\ln\underbrace{\frac{T_{02}}{T_{01}}}_{=1}-R\ln\frac{p_{02}}{p_{01}}
\quad\Longrightarrow\quad
\frac{p_{02}}{p_{01}}=e^{-(s_2-s_1)/R}.
$$

The right-hand side contains only $T_2/T_1$ and $p_2/p_1$, and both depend on $M_{n1}$ alone. So the normal-shock table's $p_{02}/p_{01}$ column, read at $M_{n1}$, is correct for the oblique shock too. The tangential velocity is a "passenger": it adds the same kinetic energy to both $T_{01}$ and $T_{02}$ and generates no entropy.

> [!warning] What does **not** carry over
> - $M_2$ is **not** the table's downstream Mach number. The table gives $M_{n2}$; divide by $\sin(\beta-\theta)$.
> - $T_0/T$ and $p_0/p$ at either station use the **full** Mach number ($M_1$ or $M_2$), not $M_n$.
> - A shock needs $M_{n1}\ge1$, so $\sin\beta\ge1/M_1$ and $\beta\ge\mu$. See §7.

## 5. The θ–β–M relation, step by step

We now know how to get everything once $\beta$ is known. The remaining question is how $\beta$ is set by $\theta$ and $M_1$ (slide 7; L2-1, ll. 59–97). The figure below carries the whole derivation. The text beneath it gives each step in words.

![[at_theta_beta_m_derivation.png|900]]

### Step 1 — two tangents from the two triangles

Divide the normal component by the tangential one on each side:

$$
\frac{U_{n1}}{U_{t1}}=\frac{M_1\sin\beta}{M_1\cos\beta}=\tan\beta,
\qquad
\frac{U_{n2}}{U_{t2}}=\tan(\beta-\theta).
$$

### Step 2 — tangential momentum removes $U_t$

Because $U_{t1}=U_{t2}$, dividing the first ratio by the second cancels $U_t$:

$$
\frac{U_{n1}}{U_{n2}}=\frac{\tan\beta}{\tan(\beta-\theta)}.
$$

Geometrically, this is two right triangles sharing the same $U_t$ leg (panel 3 of the figure).

### Step 3 — mass conservation brings in the density jump

From $\rho_1U_{n1}=\rho_2U_{n2}$, $U_{n1}/U_{n2}=\rho_2/\rho_1$. Use the normal-shock density jump in $M_{n1}=M_1\sin\beta$:

$$
\boxed{\frac{\tan\beta}{\tan(\beta-\theta)}=\frac{(\gamma+1)M_1^2\sin^2\beta}{2+(\gamma-1)M_1^2\sin^2\beta}}\qquad(\star)
$$

This is already the complete answer. The rest is algebra to isolate $\tan\theta$. The lecturer calls it *"a bit tedious algebra you could do it in 10 minutes"* (L2-1, ll. 177–178). The transcript of that algebra (ll. 98–176) is hard to follow: the lecturer corrects two slips on the fly (*"I forgot tangent theta here"*, l. 160; *"I have missed this guy here"*, l. 169). Here is a clean version, one move per line.

### Step 4 — the algebra

Use the lecture's shorthand $t=\tan\beta$, $s=\sin\beta$, $c=\cos\beta$, and write $T=\tan\theta$ and $K=M_1^2s^2$ (L2-1, l. 107).

**(a) Trigonometric identity.**

$$
\tan(\beta-\theta)=\frac{t-T}{1+tT}
\quad\Longrightarrow\quad
(\star):\ \ \frac{t\,(1+tT)}{t-T}=\frac{(\gamma+1)K}{2+(\gamma-1)K}.
$$

**(b) Cross-multiply.**

$$
t\,(1+tT)\left[2+(\gamma-1)K\right]=(\gamma+1)K\,(t-T).
$$

**(c) Expand and collect every $T$ on the left.** The left side is $t[2+(\gamma-1)K]+t^2T[2+(\gamma-1)K]$. Move the $-(\gamma+1)KT$ term from the right:

$$
T\left\{t^2\left[2+(\gamma-1)K\right]+(\gamma+1)K\right\}
=t\left[(\gamma+1)K-2-(\gamma-1)K\right]
=2t\,(K-1).
$$

The right-hand side simplifies because $(\gamma+1)K-(\gamma-1)K=2K$.

**(d) Tidy the bracket.** Call it $\mathcal A$. Group the $K$ terms, then substitute $K=M_1^2s^2$ and $t^2=s^2/c^2$:

$$
\mathcal A=2t^2+K\left[(\gamma-1)t^2+(\gamma+1)\right]
=2t^2+M_1^2\frac{s^2}{c^2}\left[(\gamma-1)s^2+(\gamma+1)c^2\right].
$$

**(e) Two identities.** $s^2+c^2=1$ and $c^2-s^2=\cos2\beta$ (L2-1, ll. 148–150) give

$$
(\gamma-1)s^2+(\gamma+1)c^2=\gamma\left(s^2+c^2\right)+\left(c^2-s^2\right)=\gamma+\cos2\beta.
$$

Take $c^2$ outside the bracket and use $s^2/c^2=t^2$ (L2-1, ll. 152–155):

$$
\mathcal A=t^2\left[2+M_1^2(\gamma+\cos2\beta)\right].
$$

**(f) Divide.**

$$
T=\frac{2t\,(K-1)}{t^2\left[2+M_1^2(\gamma+\cos2\beta)\right]}
=\frac{2}{t}\,\frac{M_1^2s^2-1}{M_1^2(\gamma+\cos2\beta)+2}.
$$

With $1/t=\cot\beta$, this is the $\theta$–$\beta$–$M$ relation (slide 8):

$$
\boxed{\tan\theta=2\cot\beta\left[\frac{M_1^2\sin^2\beta-1}{M_1^2\left(\gamma+\cos2\beta\right)+2}\right]}
$$

> [!check] Numerical check of $(\star)$
> $M_1=2$, $\theta=15^\circ$ gives $\beta=45.34^\circ$ (§8). Left side: $\tan45.34^\circ/\tan30.34^\circ=1.0120/0.5854=1.729$. Right side: $M_{n1}^2=(2\sin45.34^\circ)^2=2.024$, so $2.4\times2.024/(2+0.4\times2.024)=4.858/2.810=1.729$. ✓

### The relation runs "the wrong way"

The formula gives $\theta$ explicitly for a known $\beta$. Usually $\theta$ is known (the wall geometry) and $\beta$ is wanted. The lecture's point (L2-1, ll. 180–186; slide 8): *"the direction of travel is the other way around"*. For $\beta(\theta,M_1)$ you either:

1. read the **oblique-shock chart** (§6), or
2. solve numerically (§8.2).

## 6. The oblique-shock chart

![[at_theta_beta_m_chart.png|900]]

The chart plots $\beta$ against $\theta$ for several $M_1$ (slides 9–10; L2-1, ll. 187–191). To use it: go up from $\theta$ on the horizontal axis to the curve for $M_1$, then across to read $\beta$.

### Weak and strong solutions

A horizontal line $\theta=\text{const}<\theta_{max}$ cuts each $M_1$ curve **twice**, because the relation is nonlinear in $\beta$ (L2-1, ll. 193–197):

- **Weak solution (lower $\beta$):** the shock leans closer to the wall. Its normal Mach number $M_1\sin\beta$ is smaller, so the jumps are smaller. $M_2$ is **usually still supersonic** (L2-1, ll. 199–201).
- **Strong solution (higher $\beta$):** the shock is closer to normal and gives larger jumps. $M_2$ is **always subsonic**.

The weak solution is what forms on wedges and compression corners in practice. The strong one appears only when something downstream forces it, typically a high back pressure or a geometric constraint (slide 9: *"unless there is a restriction in geometric and/or pressure conditions"*). See [[Weak and Strong Oblique Shocks]].

![[at_oblique_shock_strength.png|900]]

> [!note] "Usually" supersonic
> On the weak branch, $M_2$ drops below 1 only in the thin band between the dotted $M_2=1$ locus and the dashed $\theta_{max}$ locus, just below $\theta_{max}$. For $M_1=2$ that band is $22.71^\circ<\theta<22.97^\circ$. The lecturer hedges for this reason: *"not completely always… I'm going to talk about that later"* (L2-1, l. 200).

### Maximum deflection and detachment

Each $M_1$ curve has a turning point at $\theta_{max}$. The transcript calls it an "inflection point" (L2-1, l. 201), but it is a **maximum** of $\theta(\beta)$, where $\mathrm d\theta/\mathrm d\beta=0$. If the wall turns the flow by more than $\theta_{max}$, no attached straight shock can satisfy the conservation laws. The shock then **detaches** and stands off the body as a curved bow shock (L2-1, ll. 201–204). It is locally normal on the axis and weakens further out. This is the Week 1 Pitot-probe picture: a blunt nose is the extreme case $\theta=90^\circ>\theta_{max}$ at any $M_1$.

| $M_1$ | $\mu=\sin^{-1}(1/M_1)$ | $\theta_{max}$ | $\beta$ at $\theta_{max}$ | $\theta$ where weak $M_2=1$ |
|---:|---:|---:|---:|---:|
| 1.5 | $41.81^\circ$ | $12.11^\circ$ | $66.6^\circ$ | $11.69^\circ$ |
| 2 | $30.00^\circ$ | $22.97^\circ$ | $64.7^\circ$ | $22.71^\circ$ |
| 3 | $19.47^\circ$ | $34.07^\circ$ | $65.2^\circ$ | $34.01^\circ$ |
| 5 | $11.54^\circ$ | $41.12^\circ$ | $66.6^\circ$ | $41.11^\circ$ |
| $\infty$ | $0^\circ$ | $45.58^\circ$ | $67.8^\circ$ | — |

*(Computed from the $\theta$–$\beta$–$M$ relation, $\gamma=1.4$.)* Even at infinite Mach number, air cannot be turned through more than about $45.6^\circ$ by a single attached shock.

### The two ends of every curve (θ = 0)

Set $\tan\theta=0$ in the boxed relation. The product $2\cot\beta\,[\cdots]$ vanishes in two ways (slide 10; L2-1, ll. 204–212):

1. $\cot\beta=0\ \Rightarrow\ \beta=90^\circ$: the **normal shock**. *"Oblique shock solution contains the normal shock solution naturally."*
2. $M_1^2\sin^2\beta-1=0\ \Rightarrow\ \sin\beta=1/M_1$, so $\beta=\mu$: an infinitely weak wave, the **Mach wave**.

Every attached oblique shock therefore lies between these limits:

$$
\boxed{\mu\le\beta\le90^\circ}
$$

The lower bound is the physical condition $M_{n1}\ge1$ written as an angle. A Mach wave has $M_{n1}=M_1\sin\mu=1$ **exactly**. Its normal component is precisely sonic, so it is the weakest possible "normal shock" in the normal direction, with zero jump.

### The M₁ → ∞ curve

Divide the numerator and denominator by $M_1^2$ and let $1/M_1^2\to0$:

$$
\tan\theta\ \to\ 2\cot\beta\,\frac{\sin^2\beta}{\gamma+\cos2\beta}=\frac{\sin2\beta}{\gamma+\cos2\beta}.
$$

The curve no longer depends on $M_1$. This is the purple limiting curve on the chart, with $\theta_{max}=45.58^\circ$ for $\gamma=1.4$. (The same "hypersonic independence" appeared in the W01 strong-shock limits.)

## 7. Mach waves and the Mach angle

Why should the weakest oblique shock sit at $\sin\beta=1/M_1$? The last part of the lecture answers this from scratch with a point sound source (slides 11–14; L2-1, ll. 212–235).

> [!tip] Intuition: gradual versus abrupt
> *"Abruptly was the key word to generate shocks"* (L2-1, l. 212). If the surface curves **smoothly**, each tiny change in slope sends out only a tiny, almost isentropic disturbance: a **Mach wave**. Many Mach waves together can compress or expand a flow gradually. Expansion fans (Lecture 2.4) and the method of characteristics (Weeks 4–5) are built entirely from Mach waves.

![[at_mach_waves.png|900]]

A source emits a sound pulse every $\Delta t$. Each pulse spreads as a circle at speed $a$ from wherever the source was when it was emitted. The source itself moves at $U=Ma$. Look at $t=3\Delta t$:

| Case | What happens | Consequence |
|---|---|---|
| $M=0$ | Concentric circles of radius $a\Delta t,2a\Delta t,3a\Delta t$ | Sound is heard everywhere at once |
| $M<1$ | Circles are offset, crowding ahead of the source, but each stays ahead of it | Doppler shift: higher pitch ahead. Sound still reaches everywhere |
| $M=1$ | Every circle passes through the source's current position | All pulses arrive together as a single plane front: the **sonic boom** (L2-1, ll. 224–229). The region ahead is a **zone of silence** |
| $M>1$ | The source outruns its own pulses. The circles are enveloped by two straight lines (a cone in 3D) | Sound is heard only **inside the Mach cone** |

### Deriving the Mach angle

Take the oldest pulse (supersonic panel). It was emitted $3\Delta t$ ago at a point now $3U\Delta t$ behind the source, and has radius $3a\Delta t$. The envelope line is **tangent** to the circle, so the radius to the tangent point is perpendicular to it. The right triangle has hypotenuse $3U\Delta t$ and opposite side $3a\Delta t$:

$$
\sin\mu=\frac{3a\Delta t}{3U\Delta t}=\frac{a}{U}=\frac1M
\qquad\Longrightarrow\qquad
\boxed{\mu=\sin^{-1}\!\left(\frac1M\right)}.
$$

The factor 3 cancels. Any pulse gives the same angle, which is why all the circles share one straight envelope. (The transcript says *"arc sine of m"* at l. 235. It is $\sin^{-1}(1/M)$, as on slide 14.)

| $M$ | 1.1 | 1.5 | 2 | 3 | 5 |
|---|---:|---:|---:|---:|---:|
| $\mu$ | $65.4^\circ$ | $41.8^\circ$ | $30.0^\circ$ | $19.5^\circ$ | $11.5^\circ$ |

These are exactly the open-circle intercepts on the oblique-shock chart. The oblique-shock relation *"also contains Mach wave solution"* (L2-1, ll. 235–236), and the two independent routes agree. As $M\to1^+$, $\mu\to90^\circ$ and the Mach wave becomes a normal (sonic) front, matching the $M=1$ panel.

## 8. Worked examples

### 8.1 Lecture chart example: M₁ = 2, θ = 15°

The lecture reads $\beta$ off the chart for $\theta=15^\circ$, $M_1=2$ (L2-1, ll. 188–191).

**Shock angles.** Solving the θ–β–M relation (§8.2) gives

$$
\beta_{weak}=45.34^\circ,\qquad\beta_{strong}=79.83^\circ.
$$

> [!warning] Transcript slip
> The lecture reads the weak solution as *"42 or 43"* degrees (L2-1, l. 190). The exact value is $45.3^\circ$, and a careful chart reading agrees. Around $42^\circ$ is the weak solution for $\theta\approx13^\circ$. Treat the lecture number as a quick eyeball, not a result.

**Weak solution, step by step.**

$$
M_{n1}=2\sin45.34^\circ=1.4227.
$$

Normal-shock relations at $M_{n1}=1.4227$ (or the table):

$$
\frac{p_2}{p_1}=1+\frac{2.8}{2.4}\left(1.4227^2-1\right)=2.195,
\qquad
\frac{\rho_2}{\rho_1}=\frac{2.4\times2.024}{2+0.4\times2.024}=1.729,
$$

$$
\frac{T_2}{T_1}=\frac{2.195}{1.729}=1.269,
\qquad
M_{n2}^2=\frac{2+0.4\times2.024}{2.8\times2.024-0.4}=0.5335\ \Rightarrow\ M_{n2}=0.7304,
$$

$$
M_2=\frac{0.7304}{\sin(45.34^\circ-15^\circ)}=\frac{0.7304}{0.5051}=1.446,
\qquad
\frac{p_{02}}{p_{01}}=0.9524.
$$

*Check with $T_0$:* $T_0/T_1=1+0.2\times4=1.8$, so $T_0/T_2=1.8/1.269=1.418$ and $M_2=\sqrt{(1.418-1)/0.2}=1.446$. ✓

**Strong solution.** $M_{n1}=1.9686$, $p_2/p_1=4.355$, $M_{n2}=0.5828$, $M_2=0.5828/\sin64.83^\circ=0.644$, $p_{02}/p_{01}=0.7355$.

**Compare with a normal shock at $M_1=2$:** $p_2/p_1=4.5$, $M_2=0.577$, $p_{02}/p_{01}=0.7209$.

| | $\beta$ | $p_2/p_1$ | $M_2$ | $p_{02}/p_{01}$ |
|---|---:|---:|---:|---:|
| weak oblique | $45.3^\circ$ | 2.19 | 1.45 | 0.952 |
| strong oblique | $79.8^\circ$ | 4.35 | 0.64 | 0.736 |
| normal shock | $90^\circ$ | 4.50 | 0.58 | 0.721 |

> [!tip] Design lesson
> The weak oblique shock loses under 5% of the stagnation pressure. The normal shock at the same $M_1$ loses 28%. This is why supersonic intakes decelerate the flow through one or more weak oblique shocks before a final weak normal shock. See [[Intake Pressure Recovery]] (SESA2023).

### 8.2 Solving for β numerically

Define $f(\beta)=\theta(\beta,M_1)-\theta_{target}$ and apply Newton–Raphson with a numerical derivative, as W01 did for the Rayleigh Pitot formula:

$$
\beta^{(k+1)}=\beta^{(k)}-\frac{f(\beta^{(k)})}{f'(\beta^{(k)})}.
$$

For $M_1=2$, $\theta=15^\circ$, starting at $\beta^{(0)}=40^\circ$:

| $k$ | $\beta^{(k)}$ | $f$ (deg) |
|---:|---:|---:|
| 0 | $40.000^\circ$ | $-4.377$ |
| 1 | $44.876^\circ$ | $-0.350$ |
| 2 | $45.339^\circ$ | $-0.003$ |
| 3 | $45.344^\circ$ | $\approx0$ |

> [!tip] Choosing the starting guess picks the branch
> Start between $\mu$ and $\beta_{\theta_{max}}$ (about $65^\circ$) to converge to the **weak** solution. Start between $\beta_{\theta_{max}}$ and $90^\circ$ (e.g. $85^\circ$) to get the **strong** one. A bracketing method such as bisection on $[\mu,\beta_{\theta_{max}}]$ is guaranteed to find the weak root. This is the *"iterative methods"* route the lecture mentions (L2-1, l. 192).

### 8.3 The easy direction: given β, find θ

A shadowgraph shows a shock at $\beta=40^\circ$ on a wedge in an $M_1=3$ stream. Find the wedge half-angle and the downstream state.

$$
\tan\theta=2\cot40^\circ\,\frac{9\sin^240^\circ-1}{9(1.4+\cos80^\circ)+2}
=2(1.1918)\frac{2.7186}{16.1628}=0.4009
\ \Rightarrow\ \theta=21.85^\circ.
$$

Then $M_{n1}=3\sin40^\circ=1.928$, $p_2/p_1=4.172$, $\rho_2/\rho_1=2.559$, $M_{n2}=0.5902$, and

$$
M_2=\frac{0.5902}{\sin(40^\circ-21.85^\circ)}=\frac{0.5902}{0.3115}=1.894,
\qquad
\frac{p_{02}}{p_{01}}=0.754.
$$

*Check:* $\tan40^\circ/\tan18.15^\circ=0.8391/0.3279=2.559=\rho_2/\rho_1$. ✓ Is it weak or strong? $\theta_{max}(M_1=3)$ occurs at $\beta=65.2^\circ$, and $40^\circ<65.2^\circ$, so it is the weak branch, consistent with $M_2>1$.

### 8.4 Will the shock stay attached?

A $25^\circ$ wedge-shaped intake lip meets an $M_1=2$ stream. From the table, $\theta_{max}(2)=22.97^\circ<25^\circ$, so **no attached oblique shock is possible**. A detached bow shock stands ahead of the lip. Solving $\theta_{max}(M_1)=25^\circ$ shows that the shock attaches only for $M_1>2.13$.

### 8.5 Mach angle

A slender projectile flies at $M=2.5$. Its nose sends out Mach waves at $\mu=\sin^{-1}(1/2.5)=23.6^\circ$. An observer on the ground hears nothing until the Mach cone sweeps over them, then hears the boom.

## 9. Problem-solving workflow

1. **Sketch** the wall, $\mathbf V_1$, the shock and both angles. Measure $\theta$ and $\beta$ **from $\mathbf V_1$**.
2. **Check attachment:** is $\theta<\theta_{max}(M_1)$? If not, the shock is detached. Stop and treat the problem as a bow shock.
3. **Find $\beta$:** from the chart, or numerically on the weak branch unless the question forces the strong one.
4. **Normal component:** $M_{n1}=M_1\sin\beta$. Confirm $M_{n1}>1$, i.e. $\beta>\mu$.
5. **Jumps:** normal-shock formulas or table at $M_{n1}$ give $p_2/p_1$, $\rho_2/\rho_1$, $T_2/T_1$, $p_{02}/p_{01}$ and $M_{n2}$.
6. **Downstream Mach number:** $M_2=M_{n2}/\sin(\beta-\theta)$.
7. **Sanity checks:** $\rho_2/\rho_1=\tan\beta/\tan(\beta-\theta)$; $T_0$ is unchanged; the weak branch usually has $M_2>1$ and the strong branch has $M_2<1$.

---

## 10. Lecture 2.2: oblique-shock examples

Lecture 2.2 is a worked-examples lecture. It opens with the Concorde intake (L2-2, ll. 1–6) and asks why the lip is *slanted* rather than square to the flow. Everything in it uses the §6 chart and the §9 workflow. Three reminders come first (ll. 7–50):

- $\theta$ and $\beta$ are measured from $\mathbf V_1$, not the page axes: *"if m1 vector is angled… then theta and beta should also be measured from that angle"* (ll. 28–30).
- The chart's two extra curves are the $\theta_{max}$ locus (red on the slides, dashed on our chart), which separates strong from weak, and the $M_2=1$ locus (blue on the slides, dotted on our chart) (ll. 37–50).
- Steeper shock means stronger shock: strong solution means $M_2<1$, and weak means usually $M_2>1$.

> [!important] Exam instruction (L2-2, ll. 74–80)
> *"Each question will tell you what to do"*: use the table or chart at the **nearest value**, the **average** of two lines, **linear interpolation**, or the **exact** equations. Practise all four on Example 1. Example Sheet 1 answers are quoted both ways ("nearest value, reading OSC to 0.5 deg").

### 10.1 Example 1: M₁ = 1.8, θ = 15°

**Route 1: chart plus nearest table row** (ll. 51–72).

1. Chart: up from $\theta=15^\circ$ to the $M_1=1.8$ curve, then across: $\beta\approx51^\circ$ (ll. 54–57).
2. $M_{n1}=1.8\sin51^\circ=1.399$ (ll. 59–61).
3. Normal-shock table at the nearest row, 1.40: $M_{n2}=0.7397$ (ll. 65–67).
4. $M_2=\dfrac{M_{n2}}{\sin(\beta-\theta)}=\dfrac{0.7397}{\sin36^\circ}=1.258$ (ll. 68–72). It is still supersonic, because this is the weak branch.

> [!warning] Calculator mode (ll. 61–64)
> $\sin51$ in radian mode is $0.670$, not $0.777$. Either set degree mode or use $51\pi/180$. It is the commonest lost mark in this module.

**Route 2: linear interpolation in the table** (homework, ll. 79–80). $M_{n1}=1.3989$ lies between the 1.38 and 1.40 rows:

$$
\sigma=\frac{1.3989-1.38}{1.40-1.38}=0.943,
\qquad
M_{n2}=0.7483+0.943\,(0.7397-0.7483)=0.7402,
$$

$$
M_2=\frac{0.7402}{\sin36^\circ}=1.259.
$$

**Route 3: the exact solution** (*"you can find an exact solution by using an iterative approach"*, ll. 81–89; slide 6 calls it homework). Solve $f(\beta)=\theta(\beta,1.8)-15^\circ=0$ with Newton's method from the chart value:

| $k$ | $\beta^{(k)}$ | $f$ (deg) |
|---:|---:|---:|
| 0 | $51.000^\circ$ | $-0.1934$ |
| 1 | $51.333^\circ$ | $-0.0019$ |
| 2 | $51.3365^\circ$ | $\approx0$ |

Then:

$$
M_{n1}=1.8\sin51.336^\circ=1.4055,
\qquad
M_{n2}=0.7374,
\qquad
M_2=\frac{0.7374}{\sin36.336^\circ}=1.2445,
$$

$$
\frac{p_2}{p_1}=2.138,
\qquad
\frac{p_{02}}{p_{01}}=0.957.
$$

This matches the lecture's *"beta is 51.3 and then m2 is 1.245 instead of 1.259"* (l. 84). The strong solution would be $\beta=76.76^\circ$ with $M_2=0.712$.

> [!tip] Why bother with the exact answer?
> The chart route is about 1% out in $M_2$. The lecturer's point (ll. 85–88) is that aerospace safety factors are about 1.3, against about 10 in civil engineering, so small errors matter.

### 10.2 Example 2: a supersonic intake at M₁ = 3

![[at_intake_shock_systems.png|900]]

**(a) Pitot (normal-shock) intake** (ll. 89–109). A subsonic-style intake flown at $M_1=3$ sits behind a detached normal shock. From the normal-shock table at $M_1=3$:

$$
\frac{p_{02}}{p_{01}}=0.3283
\quad\Rightarrow\quad
\text{67.2\% of the stagnation pressure is lost.}
$$

Stagnation pressure is what the engine turns into thrust (ll. 100–102; [[Intake Pressure Recovery]]).

**(b) Slanted lip: oblique shock, then a normal shock** (ll. 110–157). Sweep the lower lip back so that the upper lip turns the flow by $\theta=22^\circ$ through an oblique shock. The lower lip sits behind that shock, so no reflection forms inside the duct (ll. 113–117). This is the Concorde shape.

1. Chart: $\theta=22^\circ$ on the $M_1=3$ curve gives $\beta\approx40^\circ$ (ll. 118–122).
2. $M_{n1}=3\sin40^\circ=1.928$, about 1.93. The transcript's *"3 times 40 degrees"* (l. 127) means $3\sin40^\circ$.
3. 1.93 lies midway between the 1.92 and 1.94 rows, so average them (ll. 128–136). The lecturer first went for $p_0$, then corrected himself to find $M_{n2}$ first (l. 132):

$$
M_{n2}=\tfrac12(0.5918+0.5880)=0.590,
\qquad
M_2=\frac{0.590}{\sin(40^\circ-22^\circ)}=1.91,
$$

$$
\frac{p_{02}}{p_{01}}=\tfrac12(0.7581+0.7488)=0.754.
$$

4. The supersonic $M_2=1.91$ must be slowed to subsonic for the compressor, so a **normal shock** stands inside the intake (ll. 137–141). At $M=1.91$, average the 1.90 and 1.92 rows:

$$
\frac{p_{03}}{p_{02}}=\tfrac12(0.7674+0.7581)=0.763,
\qquad
M_3=0.594
$$

The lecture reads these as 0.762 and 0.593 (ll. 143–149).

5. **Chain the stagnation-pressure ratios.** Each factor is the ratio across one shock, and the intermediate $p_{02}$ cancels:

$$
\frac{p_{03}}{p_{01}}=\frac{p_{03}}{p_{02}}\cdot\frac{p_{02}}{p_{01}}=0.762\times0.754=0.574.
$$

The loss is 43%, compared with 67% for the single normal shock (ll. 150–157).

> [!warning] Slide slip (corrected live)
> The lecture said and showed $p_{02}/p_{01}=0.762$ for the oblique shock (l. 136), the same number as the normal-shock step. At ll. 153–155 the lecturer corrects it: *"it should be five four"*, i.e. **0.754**. Use 0.754. The product 0.574 on the slide already uses the corrected value.

> [!check] Exact version of Example 2
> Solving exactly gives $\beta=40.19^\circ$, $M_{n1}=1.936$, $M_2=1.886$, $p_{02}/p_{01}=0.7507$, $M_3=0.598$ and $p_{03}/p_{02}=0.7739$, so $p_{03}/p_{01}=0.581$. Panel (d) of the figure scans $\theta$: the best single ramp is $\theta=22.6^\circ$, with recovery 0.5812. **The lecture's $22^\circ$ is essentially optimal.**

**Why several weak shocks beat one strong one.** Week 3 shows that the entropy rise across a shock grows as the **cube** of its strength, $\Delta s\propto(M_{n1}^2-1)^3$ ([[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method#4. Entropy across a shock and why shocks compress|W03 §4]]). Split a compression of "strength" $m$ into two shocks of strength $m/2$. The total entropy rise falls from $m^3$ to $2(m/2)^3=m^3/4$. With two oblique ramps plus a normal shock at $M_1=3$, the best recovery is **0.744**, at $\theta=15.0^\circ$ then $18.8^\circ$. At that optimum all three shocks have the same normal Mach number, $M_n=1.599$ (*suggested extension*: Oswatitsch's equal-strength rule).

**(c) The Concorde idea: isentropic compression** (ll. 158–194). Replace the straight ramp by a smooth concave one. At the start $\theta=0$, so the "shock" there is a Mach wave (ll. 170–174). Each further increment of turning sends out another Mach wave, and the waves converge (ll. 175–178). Every Mach wave is isentropic, so the stagnation-pressure loss tends to zero (ll. 185–188). Concorde's variable ramps also let the intake work at subsonic take-off and landing (ll. 189–193).

### 10.3 Weak shocks with subsonic downstream flow (ll. 195–203)

Between the $M_2=1$ locus and the $\theta_{max}$ locus there is a thin band of **weak** solutions with $M_2<1$. For $M_1=2$ the band is $22.71^\circ<\theta<22.97^\circ$ (§6). *"Don't be confused… if you are in this tiny area"* (ll. 200–202).

> [!note] Transcript wording, ll. 196–199
> The two sentences about which side is subsonic contradict each other in the recording. The rule is: **below** the $M_2=1$ locus (smaller $\beta$) the flow behind the shock is supersonic; **above** it, the flow is subsonic.

### 10.4 Detachment and the bow shock: every solution on one curve

*(L2-2, ll. 204–242.)*

- At $M_1=1.96$, $\theta_{max}=22.27^\circ$ (lecture: 22.3°). A $22.5^\circ$ wedge is *"ever so slightly larger"*, so its shock looks attached but stands off by a tiny gap (ll. 209–212). At $60^\circ$ a clear bow shock forms (ll. 213–214).
- The bow shock is locally normal **on the axis only**. *"Detached shock is normally a normal shock"* (l. 209) means "normal at its nose". Away from the axis it curves back and weakens.

![[at_bow_shock_solutions.png|900]]

Walk along the bow shock from the axis outwards (ll. 215–242):

| Point | Local $\beta$ | Local turning $\theta^*$ | Flow behind |
|---|---|---|---|
| **a** (axis) | $90^\circ$ | 0 (normal shock) | subsonic |
| a → b | falling | rising to $\theta^*_{max}$ | strong branch, subsonic |
| **b** | $\beta(\theta_{max})$ | $\theta_{max}$ | subsonic |
| b → c | falling | falling slightly | weak branch, still subsonic |
| **c** | $\beta$ on the $M_2=1$ locus | just below $\theta_{max}$ | sonic: the **sonic line** starts here |
| c → d → e | falling to $\mu$ | falling to 0 | supersonic |
| **e** (far field) | $\mu$ | 0 | Mach wave |

> [!warning] Transcript slip (l. 234)
> *"c was where angle is maximum"* should say **b**. At l. 233 the lecturer has just said b is the maximum, and c is the sonic point.

*"All the solution is in here on the bow shock. Interesting, isn't it, that is nature"* (l. 242).

---

## Links

- Parent: [[SESA3029 Aerothermodynamics Hub]]
- Previous: [[SESA3029 W01 - Compressible-Flow Toolkit, Normal Shocks and Pitot Probes]]
- Next: [[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method]]
- Year 2 foundation: [[Oblique Shock Waves]] and [[Intake Pressure Recovery]] in [[SESA2023 W04 - Friction, Heat Addition, Oblique Shocks and Intakes]] (note the different symbols: SESA2023 used $\sigma$ for the shock angle and $\delta$ for the deflection)
- Full formula list: [[SESA3029 Formula Sheet]]

## Sources

- `Lecture2-1.pdf` (2.1 Oblique Shock Waves, 14 slides) with transcript `Lecture 2-1.txt` (Prof. Jae-Wook Kim). Line references `L2-1, l. …` point to that file.
- `Lecture2-2.pdf` (2.2 Oblique Shock Examples, 13 slides) with transcript `Lecture 2-2.txt` (§10). Line references `L2-2, l. …` point to that file.
- Anderson, *Fundamentals of Aerodynamics*: Week 2 reading is §§9.1, 9.2 and 9.5 (module schedule, `Lecture1-1.pdf` p. 10)
- Next: [[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method]] (Lectures 2.3–2.5). Worked solutions to the related sheet: [[SESA3029 Example Sheet 1 - Solutions]]

## Self-study tasks set in lectures

> [!todo] How to use this list
> Every task below was set, or explicitly left to you, in Lecture 2.1. Worked solutions are in this note. **Attempt each one closed-book first**, then check against the linked section. Tick the box once you can reproduce it unaided.

### Derivations

- [ ] **Normal-shock jump relations**, if not done last week: *"have you done that as a homework last week… if you haven't please do so, those are some good examples of some derivation questions in the exam"* (L2-1, ll. 51–54). → [[SESA3029 W01 - Compressible-Flow Toolkit, Normal Shocks and Pitot Probes#Pressure jump (homework)|W01 §5]]
- [ ] **Conservation laws across an oblique shock**, including tangential momentum ⇒ $U_{t1}=U_{t2}$, and why $\tfrac12U_t^2$ cancels in the energy equation (L2-1, ll. 30–45). → [[#3. Conservation laws across the oblique shock|§3]]
- [ ] **Why the normal-shock relations apply with $M_n$**: write the oblique and normal equation sets side by side (L2-1, ll. 46–58). → [[#4. It is a normal shock in the normal component|§4]]
- [ ] **$\theta$–$\beta$–$M$ relation from scratch**: tangents → $U_{n1}/U_{n2}$ → density jump → identity → algebra. *"A bit tedious algebra you could do it in 10 minutes"* (L2-1, ll. 97–178). The transcript's version contains two on-the-fly corrections, so work from the clean version. → [[#5. The θ–β–M relation, step by step|§5]]
- [ ] **The two $\theta=0$ solutions**: show that they are $\beta=90^\circ$ and $\beta=\mu$ (L2-1, ll. 204–212). → [[#The two ends of every curve (θ = 0)|§6]]
- [ ] **Mach angle** $\mu=\sin^{-1}(1/M)$ from the sound-pulse construction (L2-1, ll. 230–235). → [[#Deriving the Mach angle|§7]]
- [ ] *(Suggested, not lecturer-set)* Show that $p_{02}/p_{01}$ depends only on $M_{n1}$. → [[#Why p₀₂/p₀₁ depends only on Mₙ₁ (derivation)|§4]]

### Calculations

- [ ] **Chart reading**: $\theta=15^\circ$, $M_1=2$ ⇒ $\beta$ (L2-1, ll. 188–191). Target: weak $45.3^\circ$, strong $79.8^\circ$ (not the "42 or 43" in the recording). → [[#8.1 Lecture chart example: M₁ = 2, θ = 15°|§8.1]]
- [ ] Complete the downstream state for that shock: $p_2/p_1=2.19$, $M_2=1.45$, $p_{02}/p_{01}=0.952$. Compare with a normal shock.
- [ ] **Solve for $\beta$ numerically** *"by using some iterative methods"* (L2-1, l. 192). → [[#8.2 Solving for β numerically|§8.2]]
- [ ] Find $\theta_{max}$ for $M_1=2$ from the chart and check it against $22.97^\circ$ (L2-1, ll. 201–204). → [[#Maximum deflection and detachment|§6]]

### Concepts and reading

- [ ] Explain **weak versus strong** solutions and which one is normally observed (L2-1, ll. 193–201; slide 9). → [[#Weak and strong solutions|§6]]
- [ ] Explain **shock detachment** above $\theta_{max}$ and its link to the Pitot bow shock (L2-1, ll. 201–204).
- [ ] Explain the **four sound-source cases**, the zone of silence and the sonic boom (L2-1, ll. 213–232). → [[#7. Mach waves and the Mach angle|§7]]
- [ ] Read Anderson §§9.1, 9.2, 9.5 (Week 2 on the module schedule).
- [ ] Preview `Lecture2-2.pdf` (*Oblique Shock Examples*) before the Thursday lecture: *"we are going to have a look at some examples of oblique shocks… Thursday"* (L2-1, ll. 236–237).
- [ ] Blackboard **Test 1 is due Sun 11 Oct**. The quiz is released after Lecture 2.3: *"after that a quiz will be released… deadline is Sunday next week"* (L2-2, ll. 243–244).

### Lecture 2.2 tasks

- [ ] **Example 1 by linear interpolation**: *"I want you to try this first using a linear interpolation"* (L2-2, ll. 79–80). Target: $M_2=1.259$. → [[#10.1 Example 1: M₁ = 1.8, θ = 15°|§10.1]]
- [ ] **Example 1 exactly, by iteration**: homework (L2-2, ll. 81–89; slide 6). Target: $\beta=51.34^\circ$, $M_2=1.245$. → [[#10.1 Example 1: M₁ = 1.8, θ = 15°|§10.1]]
- [ ] **Example 2 intake**: reproduce 0.328, then 0.754 × 0.762 = 0.574 (L2-2, ll. 89–157). Note the corrected 0.754 (ll. 153–155). → [[#10.2 Example 2: a supersonic intake at M₁ = 3|§10.2]]
- [ ] Explain why the Concorde intake is slanted and has variable ramps (L2-2, ll. 158–194). → [[#10.2 Example 2: a supersonic intake at M₁ = 3|§10.2(c)]]
- [ ] Walk the points a → e along a bow shock and place each on the chart (L2-2, ll. 215–242). → [[#10.4 Detachment and the bow shock: every solution on one curve|§10.4]]
- [ ] *(Suggested, not lecturer-set)* Find the optimum ramp angle at $M_1=3$ (22.6°) and the two-ramp optimum (0.744). → [[#10.2 Example 2: a supersonic intake at M₁ = 3|§10.2]]
- [ ] Example Sheet 1, Q1–Q3 and Q5 (Weeks 1–2 material). → [[SESA3029 Example Sheet 1 - Solutions]]
