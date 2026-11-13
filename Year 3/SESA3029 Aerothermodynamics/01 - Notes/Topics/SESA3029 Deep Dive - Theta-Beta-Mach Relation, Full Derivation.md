---
title: "SESA3029 Deep Dive - Theta-Beta-Mach Relation, Full Derivation"
module: "SESA3029 Aerothermodynamics"
type: topic
stream: "Block 2: Oblique Shocks and Expansions"
order: 2.5
tags: [sesa3029, compressible-flow, oblique-shock, theta-beta-m, maximum-deflection, sonic-line, weak-shock, derivation, deep-dive]
aliases: ["Theta-beta-M derivation", "θ–β–M deep dive", "Maximum deflection angle derivation", "Sonic line derivation", "Oblique shock relation in full"]
date: 2026-11-12
status: lectured
coverage: "Every step of the θ–β–M derivation of Lecture 2.1 (slides 3–8), taken from the conservation laws through the normal-component density jump; then, beyond the slides' algebra, the cubic in tan β, the closed forms for θ_max and the sonic line, the weak-shock limit and its link to Ackeret, and the weak/strong branch argument of Lectures 2.1–2.2, checked against the slide and chart numbers"
parent: ["[[SESA3029 Aerothermodynamics Hub]]"]
prerequisites: ["[[SESA3029 W01 - Compressible-Flow Toolkit, Normal Shocks and Pitot Probes]]", "[[SESA3029 W02 - Oblique Shock Relations and Mach Waves]]"]
next_topics: ["[[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method]]", "[[SESA3029 Deep Dive - Ackeret Theory and Optimum Supersonic Aerofoils]]"]
key_concepts: ["[[Theta-Beta-Mach Relation]]", "[[Oblique-Shock Jump Relations]]", "[[Weak and Strong Oblique Shocks]]", "[[Mach Waves and Mach Angle]]"]
tutorial_sheets: ["[[SESA3029 Example Sheet 1 - Solutions]]"]
sources: ["02 - Sources/Lectures/Lecture2-1.pdf", "02 - Sources/Lectures/Lecture2-2.pdf", "02 - Sources/Lectures/Lecture 2-1.txt", "02 - Sources/Lectures/Lecture 2-2.txt"]
---

# SESA3029 Deep Dive - Theta-Beta-Mach Relation, Full Derivation

> [!abstract] Summary
> An oblique shock keeps the tangential velocity and treats the normal component as a normal shock in $M_{n1}=M_1\sin\beta$. Writing the turn of the velocity vector as the ratio of two tangents and the density jump as the normal-shock value gives $\tan\theta=2\cot\beta\,(M_1^2\sin^2\beta-1)/[M_1^2(\gamma+\cos2\beta)+2]$, equivalently a cubic in $\tan\beta$. Maximising $\theta$ and setting $M_2=1$ each give a quadratic in $\sin^2\beta$, so $\theta_{max}$ and the sonic line have closed forms; at small $\theta$ the shock leaves the Mach line linearly and its pressure jump becomes Ackeret's $C_p=2\theta/\sqrt{M_1^2-1}$.

> [!summary]- Exam use: quick path
> - **Use it when:** a question asks you to derive the θ–β–M relation, to explain the two $\theta=0$ solutions, $\theta_{max}$ or the weak and strong branches, or to find $M_1$, $\beta$ or $\theta$ when the other two are given.
> - **Assumptions:** steady, inviscid, adiabatic, planar; calorically perfect gas ($\gamma=1.4$ for air); $\theta$ and $\beta$ measured from $\vec V_1$; uniform flow on each side of a straight shock.
> - **Method:** 1. $U_{t1}=U_{t2}$ from tangential momentum. 2. $\tan\beta/\tan(\beta-\theta)=U_{n1}/U_{n2}=\rho_2/\rho_1$. 3. Normal-shock density jump in $M_{n1}=M_1\sin\beta$. 4. Expand $\tan(\beta-\theta)$, cross-multiply and collect $\tan\theta$. 5. Use $\sin^2\beta+\cos^2\beta=1$ and $\cos^2\beta-\sin^2\beta=\cos2\beta$ to reach the boxed form.
> - **Common mistakes:** dropping the factor $\tan^2\beta$ when the bracket is tidied; calling the turning point of a θ–β curve an inflection point, when it is a maximum of $\theta(\beta)$.
> - **Practise:** [[#Checks against the lecture numbers|the checks in §10]] · [[SESA3029 W02 - Oblique Shock Relations and Mach Waves#10.1 Example 1: M₁ = 1.8, θ = 15°|W02 Example 1]]

A supersonic stream meeting a wedge has to turn through the wedge half-angle $\theta$ at once, and an oblique shock is how it does so. Across the shock the pressure changes, but the pressure is uniform along each face of the shock and pushes only normal to it, so nothing slows the velocity component that runs along the shock. The normal component goes through an ordinary normal shock and comes out slower. A vector with an unchanged tangential part and a shortened normal part has swung towards the shock, and that swing is the deflection. The θ–β–M relation is the statement that the swing equals the wall turn.

Everything about oblique shocks then follows from one function, $\theta(\beta)$ at fixed $M_1$. It is zero at both ends of the physical range of $\beta$, at the Mach angle and at $90^\circ$, so in between it rises to a maximum $\theta_{max}$ and falls again. A wall turn below the maximum is matched twice, by a weak and a strong shock; a turn above it is not matched at all, and the shock detaches. Close to the Mach angle the curve is a straight line through the origin, which is where linear (Ackeret) theory lives.

## 1. Assumptions, angles and notation

The derivation uses these assumptions, each at a definite step:

- **steady and planar**: the shock is a fixed straight line in the $x$–$y$ plane, so the flow on each side is uniform and a thin control volume straddling the shock captures the jump;
- **inviscid and adiabatic**: the only force on the control volume is pressure, and no heat crosses its faces, so the stagnation enthalpy is conserved (§2);
- **calorically perfect gas**: $h=c_pT=a^2/(\gamma-1)$ with constant $\gamma$, used for the density jump (§3) and every closed form after it;
- **angles from the upstream velocity**: $\theta$ (flow turning or deflection angle) and $\beta$ (shock angle) are both measured from $\vec V_1$, not from the page axes.

![[at_theta_beta_m_geometry.png|900]]

| Symbol | Meaning |
|---|---|
| $V_1$, $V_2$ | speeds upstream and downstream of the shock |
| $U_{n1}$, $U_{n2}$ | velocity components normal to the shock |
| $U_{t1}$, $U_{t2}$ | velocity components along the shock |
| $M_{n1}=M_1\sin\beta$, $M_{n2}=M_2\sin(\beta-\theta)$ | normal Mach numbers |
| $a_1$, $a_0$, $a^*$ | upstream, stagnation and sonic speeds of sound |
| $\mu=\sin^{-1}(1/M_1)$ | Mach angle of the upstream flow |
| $x=\sin^2\beta$ | shorthand used from §7 on |

The downstream velocity has turned through $\theta$ towards the shock, so it makes the angle $\beta-\theta$ with the shock. Resolving each velocity into the two components gives

$$
U_{n1}=V_1\sin\beta,\qquad U_{t1}=V_1\cos\beta,\qquad U_{n2}=V_2\sin(\beta-\theta),\qquad U_{t2}=V_2\cos(\beta-\theta).
$$

## 2. Conservation laws across the shock

Take a control volume of face area $A$ parallel to the shock and thickness $\delta\to0$ across it. As $\delta\to0$ the side faces vanish, so only the two faces parallel to the shock carry flux, and only the normal velocity carries mass through them.

Mass:

$$
\dot m=\rho_1U_{n1}A=\rho_2U_{n2}A
\quad\Rightarrow\quad
\rho_1U_{n1}=\rho_2U_{n2}.
$$

Momentum normal to the shock, flux out minus flux in equal to the net pressure force:

$$
\dot m\left(U_{n2}-U_{n1}\right)=\left(p_1-p_2\right)A .
$$

Substitute $\dot m=\rho_1U_{n1}A=\rho_2U_{n2}A$ term by term and divide by $A$:

$$
p_1+\rho_1U_{n1}^2=p_2+\rho_2U_{n2}^2 .
$$

Momentum along the shock. Pressure on the two faces acts normal to them, so it has no tangential component, and the side faces have no area in the limit:

$$
\dot m\left(U_{t2}-U_{t1}\right)=0
\quad\Rightarrow\quad
U_{t1}=U_{t2}\equiv U_t .
$$

Energy. The flow is adiabatic and does no work, so the stagnation enthalpy is the same on both sides:

$$
h_1+\tfrac12\left(U_{n1}^2+U_t^2\right)=h_2+\tfrac12\left(U_{n2}^2+U_t^2\right).
$$

The $\tfrac12U_t^2$ terms are equal and cancel:

$$
h_1+\tfrac12U_{n1}^2=h_2+\tfrac12U_{n2}^2 .
$$

Mass, normal momentum and this energy equation are the normal-shock equations of [[SESA3029 W01 - Compressible-Flow Toolkit, Normal Shocks and Pitot Probes#5. Normal shock from conservation laws|W01 §5]] with $U$ replaced by $U_n$. An observer sliding along the shock at $U_t$ sees exactly a normal shock. The tangential momentum equation is the only new one, and it is what makes the deflection.

## 3. The density jump in normal components

The density ratio is the one jump the θ–β–M relation needs. It follows from the normal-component energy equation through the Prandtl relation, which is quicker than solving the three equations again.

Define the stagnation enthalpy of the normal motion alone, the enthalpy the sliding observer would measure:

$$
h_{0n}=h_1+\tfrac12U_{n1}^2=h_2+\tfrac12U_{n2}^2 .
$$

For the sliding observer the shock is a normal shock with stagnation enthalpy $h_{0n}$, so the Prandtl relation of [[SESA3029 W01 - Compressible-Flow Toolkit, Normal Shocks and Pitot Probes#Energy and the Prandtl relation|W01]], $U_1U_2=2a_0^2/(\gamma+1)$, applies with its stagnation speed of sound built from $h_{0n}$:

$$
U_{n1}U_{n2}=\frac{2a_{0n}^2}{\gamma+1},\qquad a_{0n}^2=(\gamma-1)h_{0n} .
$$

For a perfect gas $h=a^2/(\gamma-1)$, so multiplying the definition of $h_{0n}$ by $\gamma-1$ gives $a_{0n}^2$ in upstream quantities:

$$
a_{0n}^2=a_1^2+\frac{\gamma-1}{2}U_{n1}^2 .
$$

Mass conservation turns the density ratio into a velocity ratio:

$$
\frac{\rho_2}{\rho_1}=\frac{U_{n1}}{U_{n2}} .
$$

Multiply the top and bottom by $U_{n1}$:

$$
\frac{\rho_2}{\rho_1}=\frac{U_{n1}^2}{U_{n1}U_{n2}} .
$$

Substitute the Prandtl relation:

$$
\frac{\rho_2}{\rho_1}=\frac{(\gamma+1)U_{n1}^2}{2a_{0n}^2} .
$$

Substitute $a_{0n}^2$:

$$
\frac{\rho_2}{\rho_1}=\frac{(\gamma+1)U_{n1}^2}{2a_1^2+(\gamma-1)U_{n1}^2} .
$$

Divide the top and bottom by $a_1^2$ and write $U_{n1}/a_1=M_{n1}=M_1\sin\beta$:

$$
\boxed{\frac{\rho_2}{\rho_1}=\frac{(\gamma+1)M_1^2\sin^2\beta}{2+(\gamma-1)M_1^2\sin^2\beta}}
$$

This is the normal-shock density jump at $M_{n1}$. The sonic-line condition of §8 uses the same relation written with the full stagnation state. The two stagnation enthalpies differ by the tangential kinetic energy, $h_{0n}=h_0-\tfrac12U_t^2$, and $a_0^2=(\gamma-1)h_0$, so

$$
a_{0n}^2=a_0^2-\frac{\gamma-1}{2}U_t^2
\quad\Rightarrow\quad
U_{n1}U_{n2}=\frac{2a_0^2-(\gamma-1)U_t^2}{\gamma+1}. \qquad (\dagger)
$$

> [!check] The oblique Prandtl relation at $M_1=2$, $\theta=15^\circ$
> With $a_1=1$, $\beta=45.3436^\circ$: $U_{n1}=2\sin\beta=1.4227$, $U_t=2\cos\beta=1.4057$, $\rho_2/\rho_1=1.72892$, so $U_{n2}=0.82287$ and $U_{n1}U_{n2}=1.17066$. With $a_0^2=1+0.2\times4=1.8$, $(\dagger)$ gives $(3.6-0.4\times1.97609)/2.4=1.17066$ (computed).

## 4. Matching the turn to the wall

Divide the normal velocity by the tangential one on each side of the shock:

$$
\frac{U_{n1}}{U_{t1}}=\frac{V_1\sin\beta}{V_1\cos\beta}=\tan\beta,\qquad
\frac{U_{n2}}{U_{t2}}=\frac{V_2\sin(\beta-\theta)}{V_2\cos(\beta-\theta)}=\tan(\beta-\theta).
$$

Divide the first by the second. $U_{t1}=U_{t2}$ cancels:

$$
\frac{U_{n1}}{U_{n2}}=\frac{\tan\beta}{\tan(\beta-\theta)} .
$$

The left-hand side is $\rho_2/\rho_1$ by mass conservation. Equate it to the boxed jump of §3:

$$
\frac{\tan\beta}{\tan(\beta-\theta)}=\frac{(\gamma+1)M_1^2\sin^2\beta}{2+(\gamma-1)M_1^2\sin^2\beta}\qquad(\star)
$$

Isolating $\theta$ in $(\star)$ takes algebra alone. Write $t=\tan\beta$, $s=\sin\beta$, $c=\cos\beta$, $T=\tan\theta$ and $K=M_1^2s^2$. The difference formula for the tangent is

$$
\tan(\beta-\theta)=\frac{t-T}{1+tT} .
$$

Substitute it into the left-hand side of $(\star)$:

$$
\frac{t\,(1+tT)}{t-T}=\frac{(\gamma+1)K}{2+(\gamma-1)K} .
$$

Cross-multiply:

$$
t\,(1+tT)\left[2+(\gamma-1)K\right]=(\gamma+1)K\,(t-T) .
$$

Expand the left-hand side:

$$
t\left[2+(\gamma-1)K\right]+t^2T\left[2+(\gamma-1)K\right]=(\gamma+1)Kt-(\gamma+1)KT .
$$

Move every term containing $T$ to the left and every other term to the right:

$$
T\left\{t^2\left[2+(\gamma-1)K\right]+(\gamma+1)K\right\}=(\gamma+1)Kt-t\left[2+(\gamma-1)K\right] .
$$

On the right, $(\gamma+1)K-(\gamma-1)K=2K$:

$$
T\left\{t^2\left[2+(\gamma-1)K\right]+(\gamma+1)K\right\}=2t\,(K-1) .
$$

Call the brace $\mathcal A$ and group its $K$ terms:

$$
\mathcal A=2t^2+K\left[(\gamma-1)t^2+(\gamma+1)\right] .
$$

Substitute $K=M_1^2s^2$ and $t^2=s^2/c^2$ inside the square bracket:

$$
\mathcal A=2t^2+M_1^2s^2\left[(\gamma-1)\frac{s^2}{c^2}+(\gamma+1)\right] .
$$

Take $1/c^2$ out of the square bracket:

$$
\mathcal A=2t^2+M_1^2\frac{s^2}{c^2}\left[(\gamma-1)s^2+(\gamma+1)c^2\right] .
$$

Split each coefficient into $\gamma$ and $\pm1$:

$$
(\gamma-1)s^2+(\gamma+1)c^2=\gamma\left(s^2+c^2\right)+\left(c^2-s^2\right) .
$$

Use $s^2+c^2=1$ and $c^2-s^2=\cos2\beta$:

$$
(\gamma-1)s^2+(\gamma+1)c^2=\gamma+\cos2\beta .
$$

Put this back and write $s^2/c^2=t^2$:

$$
\mathcal A=2t^2+M_1^2t^2\left(\gamma+\cos2\beta\right)=t^2\left[M_1^2\left(\gamma+\cos2\beta\right)+2\right] .
$$

Divide both sides of $T\mathcal A=2t(K-1)$ by $\mathcal A$:

$$
T=\frac{2t\,(K-1)}{t^2\left[M_1^2\left(\gamma+\cos2\beta\right)+2\right]} .
$$

Cancel one $t$ and write $1/t=\cot\beta$:

$$
\boxed{\tan\theta=2\cot\beta\left[\frac{M_1^2\sin^2\beta-1}{M_1^2\left(\gamma+\cos2\beta\right)+2}\right]}
$$

This is the θ–β–M relation. It is explicit for $\theta$ given $\beta$, but in practice the wall fixes $\theta$ and $\beta$ is wanted, which is why the chart exists.

Solved for $M_1^2$ instead, the relation is linear (the form used in [[SESA3029 Test 2 - Solutions#Q3. Mach number from the oblique-shock chart|Test 2 Q3]]). Multiply out the denominator:

$$
\tan\theta\left[M_1^2\left(\gamma+\cos2\beta\right)+2\right]=2\cot\beta\left(M_1^2\sin^2\beta-1\right) .
$$

Collect the $M_1^2$ terms on one side, using $2\cot\beta\sin^2\beta=2\sin\beta\cos\beta=\sin2\beta$:

$$
M_1^2\left[\sin2\beta-\tan\theta\left(\gamma+\cos2\beta\right)\right]=2\left(\cot\beta+\tan\theta\right),
$$

$$
M_1^2=\frac{2\left(\cot\beta+\tan\theta\right)}{\sin2\beta-\tan\theta\left(\gamma+\cos2\beta\right)} .
$$

## 5. The relation as a cubic in tan β

The usual direction, $\beta$ from $\theta$, can be written as a polynomial, which shows how many solutions there are. Start again from the cross-multiplied line of §4 and remove $K$ with $s^2=t^2/(1+t^2)$:

$$
K=M_1^2\sin^2\beta=\frac{M_1^2t^2}{1+t^2} .
$$

Multiply the cross-multiplied equation through by $1+t^2$. On the left, $(1+t^2)\left[2+(\gamma-1)K\right]=2(1+t^2)+(\gamma-1)M_1^2t^2$, and on the right $(1+t^2)K=M_1^2t^2$:

$$
t\,(1+tT)\left[2+\left(2+(\gamma-1)M_1^2\right)t^2\right]=(\gamma+1)M_1^2t^2\,(t-T) .
$$

Expand the left-hand side:

$$
2t+2t^2T+\left(2+(\gamma-1)M_1^2\right)t^3+\left(2+(\gamma-1)M_1^2\right)t^4T=(\gamma+1)M_1^2t^3-(\gamma+1)M_1^2t^2T .
$$

Bring everything to the left and collect powers of $t$. The $t^3$ coefficient is $2+(\gamma-1)M_1^2-(\gamma+1)M_1^2=-2(M_1^2-1)$:

$$
\left(2+(\gamma-1)M_1^2\right)T\,t^4-2\left(M_1^2-1\right)t^3+\left(2+(\gamma+1)M_1^2\right)T\,t^2+2t=0 .
$$

Divide by $2t$ ($t\neq0$ for a shock):

$$
\boxed{\left(1+\frac{\gamma-1}{2}M_1^2\right)\tan\theta\,\tan^3\beta-\left(M_1^2-1\right)\tan^2\beta+\left(1+\frac{\gamma+1}{2}M_1^2\right)\tan\theta\,\tan\beta+1=0}
$$

(checked symbolically against $(\star)$). A cubic has three roots. For $0<\theta<\theta_{max}$ two of them are the weak and strong shocks. The third is negative, and it is not a shock at all: $(\star)$ contains $\sin^2\beta$, so it is satisfied equally by a state with $M_{n1}<1$, which would be a compression into subsonic normal flow, an "expansion shock" whose entropy falls ([[Entropy Change Across a Shock]]). The second law removes it.

> [!check] The three roots at $M_1=2$, $\theta=15^\circ$
> The coefficients are $1.8\times0.26795=0.48231$, $-3$, $5.8\times0.26795=1.55411$ and $1$. Their roots are $\tan\beta=5.5755$, $1.01207$ and $-0.36744$, i.e. $\beta=79.832^\circ$ (strong), $45.344^\circ$ (weak) and $-20.18^\circ$. The last has $M_{n1}^2=4\sin^2 20.18^\circ=0.476<1$ and is discarded. The two physical roots are the [[SESA3029 W02 - Oblique Shock Relations and Mach Waves#8.1 Chart example: M₁ = 2, θ = 15°|W02 §8.1]] values.

## 6. The two ends of each curve

### Mach wave and normal shock at zero deflection

Set $\tan\theta=0$ in the boxed relation. The right-hand side is a product, and it vanishes in two ways. The first is

$$
\cot\beta=0\quad\Rightarrow\quad\beta=90^\circ ,
$$

the normal shock, so the oblique-shock solution contains the normal shock. The second is

$$
M_1^2\sin^2\beta-1=0\quad\Rightarrow\quad\sin\beta=\frac1{M_1}\quad\Rightarrow\quad\beta=\mu ,
$$

the Mach wave. There $M_{n1}=1$, so the jump has zero strength. A real shock needs $M_{n1}>1$, so the physical range is $\mu<\beta\le90^\circ$, and $\theta(\beta)$ is positive in between because both factors are positive there.

### Leaving the Mach line: the weak-shock limit

Near the lower end, put $\beta=\mu+\varepsilon$ with $\varepsilon$ small (radians) and expand each factor to first order in $\varepsilon$. The sine first:

$$
\sin(\mu+\varepsilon)\approx\sin\mu+\varepsilon\cos\mu .
$$

Square it and drop $\varepsilon^2$:

$$
\sin^2\beta\approx\sin^2\mu+2\varepsilon\sin\mu\cos\mu .
$$

Multiply by $M_1^2$ and subtract 1. Since $M_1\sin\mu=1$, the first term gives exactly 1:

$$
M_1^2\sin^2\beta-1\approx2\varepsilon M_1^2\sin\mu\cos\mu=2\varepsilon M_1\cos\mu .
$$

From the Mach triangle (hypotenuse $M_1$, opposite side 1), $M_1\cos\mu=\sqrt{M_1^2-1}$:

$$
M_1^2\sin^2\beta-1\approx2\varepsilon\sqrt{M_1^2-1} .
$$

The numerator is already first order, so the other factors are needed only at $\beta=\mu$. With $\cos2\mu=1-2\sin^2\mu=1-2/M_1^2$, the denominator is

$$
M_1^2\left(\gamma+1-\frac2{M_1^2}\right)+2=(\gamma+1)M_1^2 ,
$$

and $\cot\mu=\sqrt{M_1^2-1}$. For small $\theta$, $\tan\theta\approx\theta$, so

$$
\theta\approx2\sqrt{M_1^2-1}\cdot\frac{2\varepsilon\sqrt{M_1^2-1}}{(\gamma+1)M_1^2}=\frac{4\left(M_1^2-1\right)}{(\gamma+1)M_1^2}\,\varepsilon .
$$

Inverted:

$$
\boxed{\beta-\mu\approx\frac{(\gamma+1)M_1^2}{4\left(M_1^2-1\right)}\,\theta}
$$

A weak shock leaves the Mach line linearly in $\theta$, and further for low $M_1$, where $M_1^2-1$ is small.

The pressure jump follows from the normal-shock relation at $M_{n1}$:

$$
\frac{p_2}{p_1}-1=\frac{2\gamma}{\gamma+1}\left(M_{n1}^2-1\right)\approx\frac{2\gamma}{\gamma+1}\cdot2\varepsilon\sqrt{M_1^2-1} .
$$

Substitute $\varepsilon$ from the boxed limit:

$$
\frac{p_2}{p_1}-1\approx\frac{4\gamma\sqrt{M_1^2-1}}{\gamma+1}\cdot\frac{(\gamma+1)M_1^2\theta}{4\left(M_1^2-1\right)}=\frac{\gamma M_1^2\theta}{\sqrt{M_1^2-1}} .
$$

The pressure coefficient based on the upstream state is $C_p=(p_2/p_1-1)\big/\left(\tfrac12\gamma M_1^2\right)$ ([[SESA3029 W07b - Compressible Potential Flow and the Prandtl-Glauert Transformation#5. The linearised pressure coefficient|W07b §5]]):

$$
C_p\approx\frac{2}{\gamma M_1^2}\cdot\frac{\gamma M_1^2\theta}{\sqrt{M_1^2-1}}=\frac{2\theta}{\sqrt{M_1^2-1}} .
$$

This is Ackeret's formula ([[SESA3029 Deep Dive - Ackeret Theory and Optimum Supersonic Aerofoils]]), reached here from the shock side instead of from the linearised potential equation. The entropy rise is of order $(M_{n1}^2-1)^3\propto\theta^3$ ([[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method#4. Entropy across a shock and why shocks compress|W03 §4]]), so to first order in $\theta$ a weak shock is isentropic and indistinguishable from a compressive Mach wave.

![[at_tbm_weak_shock_limit.png|900]]

> [!check] Weak-shock limit at $M_1=2$
> The slope is $(2.4\times4)/(4\times3)=0.800$. For $\theta=2^\circ$ the linear estimate is $\beta=31.600^\circ$ and the exact weak root is $31.646^\circ$; for $5^\circ$, $34.000^\circ$ against $34.302^\circ$. The exact $C_p$ at $\theta=2^\circ$ is $0.04214$ against Ackeret's $0.04031$, 4.5 % higher, the figure quoted in [[SESA3029 W07c - Ackeret Theory and Optimum Supersonic Aerofoils#3. Ackeret's formula|W07c §3]]. At $\theta=1^\circ$ the excess halves to 2.2 %, as it should for an error proportional to $\theta$.

### The hypersonic end

Divide the numerator and denominator of the bracket by $M_1^2$ and let $M_1\to\infty$:

$$
\tan\theta\to2\cot\beta\,\frac{\sin^2\beta}{\gamma+\cos2\beta}=\frac{2\sin\beta\cos\beta}{\gamma+\cos2\beta}=\frac{\sin2\beta}{\gamma+\cos2\beta} .
$$

The curve becomes independent of $M_1$, the purple curve on the [[SESA3029 W02 - Oblique Shock Relations and Mach Waves#6. The oblique-shock chart|W02 chart]]. Its maximum is found in §7.

## 7. The maximum deflection angle

At fixed $M_1$, $\theta(\beta)$ is zero at $\beta=\mu$ and at $90^\circ$ and positive in between, so it has a maximum $\theta_{max}$, where $\mathrm d\theta/\mathrm d\beta=0$. Wall turns above $\theta_{max}$ have no attached solution and the shock detaches.

Between $\mu$ and $90^\circ$, $\tan\theta>0$, so $\theta$, $\tan\theta$ and $\ln\tan^2\theta$ all peak at the same $\beta$. Work with $x=\sin^2\beta$, which rises monotonically with $\beta$ on $(0,90^\circ)$, so the peak in $x$ is the peak in $\beta$. Square the boxed relation and express every factor in $x$, using $\cot^2\beta=(1-x)/x$ and $\cos2\beta=1-2x$:

$$
\tan^2\theta=\frac{4(1-x)}{x}\cdot\frac{\left(M_1^2x-1\right)^2}{D^2},\qquad D=M_1^2(\gamma+1-2x)+2 .
$$

Take logarithms:

$$
\ln\tan^2\theta=\ln4+\ln(1-x)-\ln x+2\ln\left(M_1^2x-1\right)-2\ln D .
$$

Differentiate with respect to $x$, using $\mathrm dD/\mathrm dx=-2M_1^2$, and set the result to zero:

$$
-\frac1{1-x}-\frac1x+\frac{2M_1^2}{M_1^2x-1}+\frac{4M_1^2}{D}=0 .
$$

The first two terms combine over $x(1-x)$:

$$
-\frac1{1-x}-\frac1x=-\frac{x+(1-x)}{x(1-x)}=-\frac{1}{x(1-x)} .
$$

The last two combine over $(M_1^2x-1)D$:

$$
\frac{2M_1^2}{M_1^2x-1}+\frac{4M_1^2}{D}=\frac{2M_1^2\left[D+2\left(M_1^2x-1\right)\right]}{\left(M_1^2x-1\right)D} .
$$

In the square bracket the $x$ terms cancel: $M_1^2(\gamma+1)-2M_1^2x+2+2M_1^2x-2=(\gamma+1)M_1^2$. So the condition is

$$
\frac{2(\gamma+1)M_1^4}{\left(M_1^2x-1\right)D}=\frac{1}{x(1-x)} .
$$

Cross-multiply:

$$
2(\gamma+1)M_1^4x(1-x)=\left(M_1^2x-1\right)\left[(\gamma+1)M_1^2+2-2M_1^2x\right] .
$$

Expand the left-hand side:

$$
2(\gamma+1)M_1^4x-2(\gamma+1)M_1^4x^2 .
$$

Expand the right-hand side:

$$
(\gamma+1)M_1^4x+2M_1^2x-2M_1^4x^2-(\gamma+1)M_1^2-2+2M_1^2x .
$$

Subtract the right from the left and collect powers of $x$. The $x^2$ coefficient is $-2(\gamma+1)M_1^4+2M_1^4=-2\gamma M_1^4$, the $x$ coefficient is $(\gamma+1)M_1^4-4M_1^2$, and the constant is $(\gamma+1)M_1^2+2$. Multiplying by $-1/M_1^2$:

$$
2\gamma M_1^2x^2-\left[(\gamma+1)M_1^2-4\right]x-\left[(\gamma+1)+\frac{2}{M_1^2}\right]=0 .
$$

The product of the two roots is $-\left[(\gamma+1)+2/M_1^2\right]/(2\gamma M_1^2)<0$, so exactly one root is positive: $\theta(\beta)$ has a single maximum on each curve. The quadratic formula gives it:

$$
x=\frac{(\gamma+1)M_1^2-4+\sqrt{\left[(\gamma+1)M_1^2-4\right]^2+8\gamma M_1^2\left[(\gamma+1)+2/M_1^2\right]}}{4\gamma M_1^2} .
$$

Expand the discriminant:

$$
(\gamma+1)^2M_1^4-8(\gamma+1)M_1^2+16+8\gamma(\gamma+1)M_1^2+16\gamma .
$$

Group: $-8(\gamma+1)+8\gamma(\gamma+1)=8(\gamma+1)(\gamma-1)$ and $16+16\gamma=16(\gamma+1)$, so the discriminant is $(\gamma+1)\left[(\gamma+1)M_1^4+8(\gamma-1)M_1^2+16\right]$ and

$$
\boxed{\sin^2\beta_{\theta_{max}}=\frac{(\gamma+1)M_1^2-4+\sqrt{(\gamma+1)\left[(\gamma+1)M_1^4+8(\gamma-1)M_1^2+16\right]}}{4\gamma M_1^2}}
$$

$\theta_{max}$ itself follows by putting this $\beta$ into the θ–β–M relation; there is no tidier closed form for it.

Two limits check the result. At $M_1=1$ the square root is $\sqrt{(\gamma+1)(9\gamma+9)}=3(\gamma+1)$, so $x=[(\gamma+1)-4+3(\gamma+1)]/(4\gamma)=1$: $\beta=90^\circ$ and $\theta_{max}=0$, a sonic stream cannot be turned by an attached shock at all. As $M_1\to\infty$, divide the top and bottom by $M_1^2$; the square root tends to $(\gamma+1)M_1^2$, so

$$
x\to\frac{(\gamma+1)+(\gamma+1)}{4\gamma}=\frac{\gamma+1}{2\gamma},
$$

which is $67.79^\circ$ for $\gamma=1.4$. The hypersonic curve of §6 gives the maximum deflection there directly. Differentiate $\tan\theta=\sin2\beta/(\gamma+\cos2\beta)$ with respect to $2\beta$ and set the numerator of the quotient rule to zero:

$$
\cos2\beta\left(\gamma+\cos2\beta\right)+\sin^22\beta=0 .
$$

Use $\cos^22\beta+\sin^22\beta=1$:

$$
\gamma\cos2\beta+1=0\quad\Rightarrow\quad\cos2\beta=-\frac1\gamma ,
$$

consistent with $x=(1-\cos2\beta)/2=(\gamma+1)/(2\gamma)$. Then $\sin2\beta=\sqrt{1-1/\gamma^2}=\sqrt{\gamma^2-1}/\gamma$, and

$$
\tan\theta_{max}=\frac{\sqrt{\gamma^2-1}/\gamma}{\gamma-1/\gamma}=\frac{\sqrt{\gamma^2-1}}{\gamma^2-1}=\frac{1}{\sqrt{\gamma^2-1}}
\quad\Rightarrow\quad
\boxed{\theta_{max}\big|_{M_1\to\infty}=\sin^{-1}\frac1\gamma}
$$

The last step uses the right triangle with opposite side 1 and adjacent side $\sqrt{\gamma^2-1}$, whose hypotenuse is $\gamma$. For air this is $45.58^\circ$: no single attached shock in air turns a flow by more than about $45.6^\circ$, at any Mach number.

![[at_tbm_curve_anatomy.png|900]]

## 8. The sonic line

On the weak branch $M_2$ is usually above 1, but not always. The **sonic line** on the chart is the locus $M_2=1$. Its closed form comes from the oblique Prandtl relation $(\dagger)$ of §3.

The downstream flow is sonic when its speed equals the critical speed of sound. $T_0$ is the same on both sides, and $T^*/T_0=2/(\gamma+1)$ ([[SESA3029 W04 - Laval Nozzle, Under- and Over-Expanded Flow|W04]]), so $a^{*2}=2a_0^2/(\gamma+1)$ is the same on both sides too. The condition is

$$
U_{n2}^2+U_t^2=a^{*2}=\frac{2a_0^2}{\gamma+1} .
$$

Make everything dimensionless with $V_1$. The stagnation speed of sound is $a_0^2=a_1^2+\tfrac{\gamma-1}2V_1^2$, so

$$
\frac{2a_0^2}{V_1^2}=\frac{2}{M_1^2}+\gamma-1 .
$$

With $x=\sin^2\beta$, $U_t^2/V_1^2=1-x$ and $U_{n1}/V_1=\sqrt x$. From $(\dagger)$:

$$
\frac{U_{n2}}{V_1}=\frac{2a_0^2/V_1^2-(\gamma-1)(1-x)}{(\gamma+1)\sqrt x}=\frac{2/M_1^2+(\gamma-1)x}{(\gamma+1)\sqrt x} .
$$

Substitute into the sonic condition:

$$
\frac{\left[2/M_1^2+(\gamma-1)x\right]^2}{(\gamma+1)^2x}+(1-x)=\frac{2/M_1^2+\gamma-1}{\gamma+1} .
$$

Multiply through by $(\gamma+1)^2x$:

$$
\left[\frac2{M_1^2}+(\gamma-1)x\right]^2+(\gamma+1)^2x(1-x)-(\gamma+1)\left(\frac2{M_1^2}+\gamma-1\right)x=0 .
$$

Expand and collect powers of $x$. The $x^2$ coefficient is $(\gamma-1)^2-(\gamma+1)^2=-4\gamma$. The $x$ coefficient is $[4(\gamma-1)-2(\gamma+1)]/M_1^2+(\gamma+1)^2-(\gamma+1)(\gamma-1)=-2(3-\gamma)/M_1^2+2(\gamma+1)$. The constant is $4/M_1^4$. Multiplying by $-M_1^2/2$:

$$
2\gamma M_1^2x^2-\left[(\gamma+1)M_1^2-(3-\gamma)\right]x-\frac{2}{M_1^2}=0 .
$$

Again the product of the roots is negative, so there is exactly one positive root, and $M_2=1$ happens at exactly one $\beta$ on each curve. The quadratic formula, with the discriminant simplified using $(3-\gamma)^2+16\gamma=\gamma^2+10\gamma+9=(\gamma+1)(\gamma+9)$:

$$
\boxed{\sin^2\beta^*=\frac{(\gamma+1)M_1^2-(3-\gamma)+\sqrt{(\gamma+1)\left[(\gamma+1)M_1^4-2(3-\gamma)M_1^2+\gamma+9\right]}}{4\gamma M_1^2}}
$$

(both quadratics checked symbolically against the θ–β–M relation and the normal-shock $M_{n2}$, and the roots checked against a brute-force search for $M_1=1.2$–$5$). At $M_1=1$ the root is again $x=1$, and as $M_1\to\infty$ it tends to the same $(\gamma+1)/(2\gamma)$ as $\beta_{\theta_{max}}$, so the two loci merge at high Mach number.

| $M_1$ | $\mu$ | $\beta^*$ | $\theta^*$ | $\beta_{\theta_{max}}$ | $\theta_{max}$ | band $\theta_{max}-\theta^*$ | $M_2$ at $\theta_{max}$ |
|---:|---:|---:|---:|---:|---:|---:|---:|
| 1.2 | $56.44^\circ$ | $68.08^\circ$ | $3.70^\circ$ | $71.98^\circ$ | $3.94^\circ$ | $0.24^\circ$ | 0.950 |
| 1.5 | $41.81^\circ$ | $62.26^\circ$ | $11.69^\circ$ | $66.59^\circ$ | $12.11^\circ$ | $0.42^\circ$ | 0.921 |
| 2 | $30.00^\circ$ | $61.49^\circ$ | $22.71^\circ$ | $64.67^\circ$ | $22.97^\circ$ | $0.27^\circ$ | 0.924 |
| 3 | $19.47^\circ$ | $63.77^\circ$ | $34.01^\circ$ | $65.24^\circ$ | $34.07^\circ$ | $0.07^\circ$ | 0.954 |
| 5 | $11.54^\circ$ | $66.08^\circ$ | $41.11^\circ$ | $66.58^\circ$ | $41.12^\circ$ | $0.01^\circ$ | 0.981 |
| $\infty$ | $0$ | $67.79^\circ$ | $45.58^\circ$ | $67.79^\circ$ | $45.58^\circ$ | 0 | 1 |

*(Computed from the closed forms, $\gamma=1.4$.)*

## 9. Weak and strong branches

Along one curve, $M_2$ can be followed from end to end. At $\beta=\mu$ the shock has zero strength, so $M_{n2}=M_{n1}=1$ and $\theta=0$; then $M_2=M_{n2}/\sin(\beta-\theta)=1/\sin\mu=M_1$. At $\beta=90^\circ$ it is the normal-shock value, below 1. $M_2$ varies continuously in between, and §8 showed it equals 1 at exactly one $\beta^*$, so

$$
M_2>1\ \text{for}\ \mu<\beta<\beta^*,\qquad M_2<1\ \text{for}\ \beta^*<\beta\le90^\circ .
$$

The table of §8 has $M_2<1$ at $\theta_{max}$ for every $M_1$, so $\beta^*<\beta_{\theta_{max}}$. Every strong-branch solution ($\beta>\beta_{\theta_{max}}$) therefore lies above the sonic line and has subsonic flow behind it. On the weak branch, $M_2>1$ everywhere except the thin band $\beta^*<\beta<\beta_{\theta_{max}}$, which is the gap between the $\theta_{max}$ line and the sonic line on the chart: $22.71^\circ<\theta<22.97^\circ$ at $M_1=2$.

Which branch appears is not decided by the θ–β–M relation, which only says both satisfy the conservation laws. On a wedge or ramp in an open stream the weak solution forms, because nothing downstream requires the higher pressure of the strong one; the strong solution needs a downstream condition that imposes it, such as a high back pressure or a geometric constraint. The weak shock also has the smaller $M_{n1}$ and so the smaller stagnation-pressure loss: at $M_1=2$, $\theta=15^\circ$, $p_{02}/p_{01}=0.952$ on the weak branch and $0.736$ on the strong ([[SESA3029 W02 - Oblique Shock Relations and Mach Waves#8.1 Chart example: M₁ = 2, θ = 15°|W02 §8.1]]).

For $\theta>\theta_{max}$ no straight attached shock exists. The shock stands off the body as a curved bow shock, normal on the axis and weakening outwards, and along it the local shock passes through every point of the curve, from the normal shock (a) through $\theta_{max}$ (b), the sonic point (c) and the weak branch (d) to a Mach wave far away (e) ([[SESA3029 W02 - Oblique Shock Relations and Mach Waves#10.4 Detachment and the bow shock: every solution on one curve|W02 §10.4]]). The sonic line of §8 is where the subsonic pocket behind the bow shock ends.

## 10. Numerical checks

### Checks against the lecture numbers

All numbers use $\gamma=1.4$ and were computed in Python from the formulas above.

> [!check] Course and chart values
> - **Worked example, $M_1=2$, $\theta=15^\circ$:** the cubic of §5 gives $\beta=45.344^\circ$ and $79.832^\circ$. $(\star)$ checks: $\tan45.344^\circ/\tan30.344^\circ=1.01207/0.58537=1.7289$, and $M_{n1}^2=2.0240$ and $2.4\times2.0240/(2+0.4\times2.0240)=1.7289$.
> - **$M_1=1.96$:** $\theta_{max}=22.27^\circ$ from the closed form of §7 ($\beta=64.71^\circ$), usually rounded to $22.3^\circ$.
> - **The W02 table:** $\theta_{max}=12.11^\circ$, $22.97^\circ$, $34.07^\circ$, $41.12^\circ$ at $M_1=1.5$, 2, 3, 5, and $\sin^{-1}(1/1.4)=45.58^\circ$ as $M_1\to\infty$.
> - **W07a bow shock, $M_1=1.2$:** $\theta_{max}=3.94^\circ$, so a $5^\circ$ turn cannot be made by an attached shock ([[SESA3029 W07a - Euler Equations and the Effect of Mach Number on Aerofoils#Why a bow shock and not an oblique shock|W07a]]).

### Detachment of an intake lip

A $25^\circ$ lip at $M_1=2$ exceeds $\theta_{max}=22.97^\circ$ and carries a detached shock ([[SESA3029 W02 - Oblique Shock Relations and Mach Waves#8.4 Will the shock stay attached?|W02 §8.4]]). The Mach number at which a $25^\circ$ shock first attaches is the root of $\theta_{max}(M_1)=25^\circ$, which a few evaluations of the §7 closed form put at $M_1=2.13$.

## Links

- Parent: [[SESA3029 Aerothermodynamics Hub]]
- Lecture notes: [[SESA3029 W02 - Oblique Shock Relations and Mach Waves]] (the lectured derivation, chart, examples and Mach waves)
- Foundations: [[SESA3029 W01 - Compressible-Flow Toolkit, Normal Shocks and Pitot Probes#Energy and the Prandtl relation|W01, Prandtl relation]] · [[SESA3029 W04 - Laval Nozzle, Under- and Over-Expanded Flow|W04]] ($a^*$)
- Used later: [[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method|W03]] (reflections, shock-expansion) · [[SESA3029 W07a - Euler Equations and the Effect of Mach Number on Aerofoils|W07a]] (bow shock at $M_\infty=1.2$) · [[SESA3029 Deep Dive - Ackeret Theory and Optimum Supersonic Aerofoils]] (the weak-shock limit as Ackeret's formula)
- Concepts: [[Theta-Beta-Mach Relation]] · [[Oblique-Shock Jump Relations]] · [[Weak and Strong Oblique Shocks]] · [[Mach Waves and Mach Angle]] · [[Entropy Change Across a Shock]]
- Earlier years: [[Oblique Shock Waves]] (SESA2023, with $\sigma$ for the shock angle and $\delta$ for the deflection)
- Formulae: [[SESA3029 Formula Sheet#Oblique shock (Week 2)|Formula sheet: oblique shock]]

## Sources

- `Lecture2-1.pdf` (2.1 Oblique Shock Waves), slides 2–10: geometry, conservation laws, the normal-component argument, the θ–β–M relation, the chart and its two $\theta=0$ solutions. Lectured in Week 2.
- `Lecture2-2.pdf` (2.2 Oblique Shock Examples), slides 2–3 and 11–13: the $M_2=1$ band, the cone photographs at $M_1=1.96$ and the bow-shock points a–e.
- `Lecture 2-1.txt` and `Lecture 2-2.txt` (L2-1, L2-2): the recordings, for the slips below and the task line references.
- [[SESA3029 W01 - Compressible-Flow Toolkit, Normal Shocks and Pitot Probes|W01]] for the normal-shock Prandtl relation; [[SESA3029 W04 - Laval Nozzle, Under- and Over-Expanded Flow|W04]] for $T^*/T_0$.
- Anderson, *Modern Compressible Flow*, §§4.3–4.4, for the oblique-shock relations and the shock-angle limits.
- Checks: the quadratics of §§7–8 and the cubic of §5 were verified symbolically (sympy); the closed forms were compared with a brute-force search over $\beta$; every number was computed in Python. Figures from `generate_aerothermo_deepdive_figures.py` (`at_tbm_curve_anatomy.png`, `at_tbm_weak_shock_limit.png`); the geometry figure is from `generate_aerothermo_w02_figures.py`.

## Self-study tasks

Tasks citing L2-1 or L2-2 were set or worked in Lectures 2.1–2.2 (the same tasks appear in [[SESA3029 W02 - Oblique Shock Relations and Mach Waves#Self-study tasks|W02]]). Tasks marked so are suggested, not lecturer-set.

### Core

- [ ] **(L2-1, ll. 30–58)** Write the conservation laws across an oblique shock and show why $U_{t1}=U_{t2}$ and why the $\tfrac12U_t^2$ terms cancel in the energy equation. → [[#2. Conservation laws across the shock|§2]]
- [ ] **(L2-1, ll. 59–178)** Derive the θ–β–M relation from $(\star)$, one algebraic step at a time. → [[#4. Matching the turn to the wall|§4]]
- [ ] **(L2-1, ll. 204–212)** Show that $\theta=0$ gives $\beta=90^\circ$ and $\beta=\mu$, and say what each is. → [[#Mach wave and normal shock at zero deflection|§6]]
- [ ] **(L2-1, ll. 193–204)** Explain the weak and strong solutions, which one normally forms and what happens above $\theta_{max}$. → [[#9. Weak and strong branches|§9]]

### Further practice

- [ ] (suggested, not lecturer-set) Derive the density jump $\rho_2/\rho_1$ in normal components from the Prandtl relation. → [[#3. The density jump in normal components|§3]]
- [ ] (suggested, not lecturer-set) Derive the cubic in $\tan\beta$ and solve it at $M_1=2$, $\theta=15^\circ$; explain why the negative root is rejected. → [[#5. The relation as a cubic in tan β|§5]]
- [ ] (suggested, not lecturer-set) Derive $\sin^2\beta$ at $\theta_{max}$ and show that $\theta_{max}\to\sin^{-1}(1/\gamma)$ as $M_1\to\infty$; then derive the sonic-line formula and check the $M_1=2$ band $22.71^\circ$–$22.97^\circ$ (L2-2, ll. 196–202). → [[#7. The maximum deflection angle|§7]] · [[#8. The sonic line|§8]]
- [ ] (suggested, not lecturer-set) Show that a weak shock leaves the Mach line as $\beta-\mu\approx(\gamma+1)M_1^2\theta/[4(M_1^2-1)]$ and that its $C_p$ tends to $2\theta/\sqrt{M_1^2-1}$. → [[#Leaving the Mach line: the weak-shock limit|§6]]

## Transcript and slide slips

> [!warning] L2.2 slide 12: a cone labelled with a wedge value
> Where: [[#Checks against the lecture numbers]].
>
> L2.2 slide 12 labels the photographs *"Flow past a Cone at $M_1=1.96$"* with $\theta_{max}=22.3^\circ$. That number is the planar (wedge) value from the θ–β–M relation, $22.27^\circ$. A cone has a larger attached-shock limit, because the flow behind a conical shock is relieved sideways (Taylor–Maccoll flow, not lectured), so the number applies to a wedge.

### Transcript slips (L2-1)

> [!warning] Slips in `Lecture 2-1.txt`
> | Where | Said | Correct |
> |---|---|---|
> | L2-1, l. 160 | the $\tan\theta$ factor left off a line, then *"I forgot tangent theta here"* | the corrected line $T\mathcal A=2t(K-1)$ of §4 |
> | L2-1, ll. 168–174 | the bracket simplified without $t^2$, then *"t squared should be there"* | $\mathcal A=t^2[M_1^2(\gamma+\cos2\beta)+2]$ |
> | L2-1, l. 190 | weak solution read as *"42 or 43"* degrees at $M_1=2$, $\theta=15^\circ$ | $45.34^\circ$ |
> | L2-1, l. 201 | the turning point of each curve called *"an inflection point"* | a maximum of $\theta(\beta)$, where $\mathrm d\theta/\mathrm d\beta=0$ (§7) |
