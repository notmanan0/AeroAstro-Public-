---
title: "SESA1015 M11 - Longitudinal Trim and Static Stability"
module: "SESA1015 Intro to Aero & Astro"
type: topic
stream: "Mechanics of Flight"
order: 11
tags:
  - sesa1015
  - mechanics-of-flight
  - trim
  - static-stability
  - tailplane
aliases: ["SESA1015 Mechanics 11", "Longitudinal Stability", "Trim, Static Stability and Control"]
date: 2026-09-27
status: lectured
coverage: "Course Notes §8.1–8.4 (trim, static stability, control; moments about the CG with wing and tailplane; tail volume coefficient; downwash at the tail; elevator and all-moving-tail angle to trim; neutral point and C of G margin stick fixed; trim and C of G margin; tailplane and control design); Slides v2 pp. 184–220 (static and dynamic stability, rocket analogy, pitch stability, aerodynamic moment, wing-body and tail moments, zero-lift moment, tail or canard, neutral point, static margin, stick-fixed longitudinal control, yaw and roll, rubric)"
parent: ["[[SESA1015 Intro to Aero & Astro Hub]]"]
prerequisites: ["[[SESA1015 M03 - Aerodynamic Characteristics and the Drag Polar]]", "[[SESA1015 M04 - Steady Level Flight and Stall]]"]
next_topics: ["[[SESA1015 M12 - Aircraft Constraint Analysis]]"]
key_concepts: ["[[Static Margin and Tail Volume]]", "[[Elevator Angle to Trim]]", "[[Neutral Point and Static Margin]]", "[[Downwash and Induced Drag]]", "[[Aerodynamic Centre and Centre of Pressure]]"]
tutorial_sheets: ["[[SESA1015 T07 - Trim and Static Stability Solutions]]"]
sources: ["02 - Sources/Mechanics of Flight/Mechanics of Flight - Course Notes.pdf (§8.1–8.4, pp. 49–57)", "02 - Sources/Mechanics of Flight/Mechanics of Flight - Lecture Slides version 2.pdf (pp. 184–220)", "04 - Labs & Coursework/Revision & Spreadsheets/SESA1015 - Revision Questions (Original).xlsx (Q8, Q13)"]
---

# SESA1015 M11 - Longitudinal Trim and Static Stability

> [!abstract] Summary
> An aircraft is trimmed when the pitching moment about its centre of gravity is zero, $C_{m_G}=0$, and statically stable in pitch when a nose-up disturbance produces a nose-down moment, $dC_{m_G}/d\alpha<0$. With a wing and a tailplane, $C_{m_G}=C_{m0}+(h-h_0)C_L-\bar V C_{L_T}$ with tail volume coefficient $\bar V=S_Tl_T/(S\bar c)$, which gives $dC_{m_G}/d\alpha=-a_1K_n$: the aircraft is stable when the CG lies ahead of the neutral point $h_n=h_0+\bar V\,(a_{1T}/a_1)(1-d\varepsilon/d\alpha)$, by the static margin $K_n=h_n-h$. The elevator moves the trim point, and the elevator angle to trim changes with speed at a rate $d\eta/dV=2C_LK_n/(V\bar Va_{2T})$.

> [!summary]- Exam use: quick path
> - **Use it when:** a question asks for a static margin, a neutral point, a tailplane area or tail volume, the moment about the CG of a wind-tunnel model, the tailplane or elevator angle to trim, or the location of an aerodynamic centre from moment data.
> - **Assumptions:** controls fixed (stick fixed); thrust and drag through the CG; tailplane's own pitching moment neglected; linear lift curves $C_L=a_1\alpha$, $C_{L_T}=a_{1T}\alpha_T+a_{2T}\eta$; downwash $\varepsilon=(d\varepsilon/d\alpha)\alpha$; distances as fractions of $\bar c$ from the wing leading edge; slopes per radian or per degree, consistently.
> - **Method:** 1. Write $h$, $h_0$ (quarter chord if not given), $\bar V=S_Tl_T/(S\bar c)$. 2. $h_n=h_0+\bar V(a_{1T}/a_1)(1-d\varepsilon/d\alpha)$. 3. $K_n=h_n-h$, $dC_{m_G}/d\alpha=-a_1K_n$. 4. For trim set $C_{m_G}=0$ and solve for $\alpha$, $\eta$ or $\alpha_s$. 5. For sizing, invert step 2 for $\bar V$, then $S_T=\bar VS\bar c/l_T$.
> - **Common mistakes:** measuring $l_T$ from the CG when it is defined from the wing aerodynamic centre (it makes no difference only when they coincide); forgetting the factor $(1-d\varepsilon/d\alpha)$, which makes the tail look more effective than it is.
> - **Practise:** [[#Tail area for a given static margin]] · [[SESA1015 T07 - Trim and Static Stability Solutions#Question 8]]

Treating the aircraft as a point at which lift, drag, thrust and weight balance ignores moments. A real aircraft also has to balance moments, and keep them balanced when it is disturbed. Three separate requirements follow. **Trim**: in a steady flight condition (which may include a steady acceleration such as a correctly banked turn, a steady climb or a dive) all forces and moments balance, which in the pitching plane means zero moment about the centre of gravity, $M_G=0$. **Static stability**: when a small disturbance such as a gust moves the aircraft away from that condition, the forces and moments it causes initially tend to return it. **Control**: the pilot can move from one trimmed condition to another and correct for disturbances. An aircraft can be trimmed but unstable, like a pencil balanced on its point, and stable but not trimmed at the current elevator setting.

Static stability is about the initial tendency only. Whether the aircraft then actually settles back, or overshoots and oscillates with growing amplitude, is dynamic stability, which also depends on inertia and damping; a dynamically stable aircraft is statically stable, but not the other way round. On a finned rocket the fins move the centre of pressure behind the CG, and a gust that increases the angle of attack makes a moment that reduces it; without fins the centre of pressure is near the nose and the moment increases the angle, which finless rockets correct with thrust vectoring.

For an aircraft in pitch the corresponding condition is on the slope of the pitching moment about the CG. With nose-up moments positive, a positive change in $\alpha$ must produce a negative change in $M_G$:

$$
\frac{dM_G}{d\alpha}<0\qquad\Longleftrightarrow\qquad\frac{dC_{m_G}}{d\alpha}<0 .
$$

A wing on its own usually fails this test or cannot trim, and the job of the tailplane is to supply both the restoring moment and the trimming moment.

## 1. Moments about the CG: wing and body alone

The lift of the wing and body acts at the aerodynamic centre (AC), about which the pitching moment does not change with incidence ([[Aerodynamic Centre and Centre of Pressure]], [[SESA1015 M03 - Aerodynamic Characteristics and the Drag Polar|M03]]). Measure positions from the wing leading edge as fractions of the reference chord $\bar c$: the AC at $h_0\bar c$ and the CG at $h\bar c$. With the CG a distance $(h-h_0)\bar c$ behind the AC, the lift $L_w$ at the AC has a nose-up moment arm about the CG, so

$$
M_G=M_0+L_w\,(h-h_0)\bar c .
$$

Dividing by $\tfrac12\rho V^2S\bar c$, with $C_{m0}=M_0/(\tfrac12\rho V^2S\bar c)$ the moment coefficient about the AC (the slides' $C_M$):

$$
C_{m_G}=C_{m0}+C_L\,(h-h_0).
$$

With $C_L=a_1\alpha$ ($\alpha$ measured from the zero-lift line),

$$
\frac{dC_{m_G}}{d\alpha}=a_1\,(h-h_0).
$$

This is negative only if the CG is ahead of the AC ($h<h_0$). But then trim, $C_{m_G}=0$, needs $C_{m0}=-C_L(h-h_0)>0$, a nose-up moment at zero lift, and a cambered wing has $C_{m0}<0$. A conventional cambered wing alone therefore cannot be both trimmed and stable at positive lift; it needs a tailplane, or a reflexed or swept-and-twisted wing that makes $C_{m0}$ positive, as on flying wings and hang gliders.

## 2. Moments about the CG with a tailplane

Add a horizontal tailplane whose lift $P$ acts a distance $l_T$ behind the wing AC. Thrust and drag are taken to act through the CG, so they contribute no moment (symbols as in the course notes):

| Symbol | Meaning |
|---|---|
| $L_w$ | lift of the wing plus body, excluding the tailplane |
| $P$ | lift of the tailplane alone |
| $M_0$ | pitching moment of the wing plus body at zero lift (about its AC) |
| $h\bar c$, $h_0\bar c$ | CG and AC positions behind the wing leading edge |
| $S$, $S_T$ | wing and tailplane reference areas |
| $l_T$ | distance of the tailplane centre of lift behind the wing AC |

![[mof_m11_pitch_plane_forces.png|950]]

The tail lift acts at $l_T-(h-h_0)\bar c$ behind the CG, and lift behind the CG pitches the nose down. Taking moments about the CG, nose-up positive:

$$
M_G=\big\{M_0+(h-h_0)\bar c\,L_w\big\}-P\big[l_T-(h-h_0)\bar c\big].
$$

The first bracket is the wing-plus-body contribution and the second the tailplane's. Expanding the tail term,

$$
M_G=M_0+(h-h_0)\bar c\,L_w+(h-h_0)\bar c\,P-Pl_T .
$$

### Coefficient form and the tail volume coefficient

Divide by $\tfrac12\rho V^2S\bar c$. The tailplane lift coefficient is defined on the tailplane's own area, $P=\tfrac12\rho V^2S_TC_{L_T}$ (the tailplane's own pitching moment, $\propto S_T\bar c_T$, is small and neglected):

$$
C_{m_G}=C_{m0}+(h-h_0)\left(C_{L_w}+C_{L_T}\frac{S_T}{S}\right)-\frac{S_Tl_T}{S\bar c}\,C_{L_T}.
$$

The group in the last term is the **tail volume coefficient** (or tail volume ratio),

$$
\boxed{\,\bar V=\frac{S_Tl_T}{S\bar c}\,},
$$

the tail area times its moment arm, made non-dimensional by the wing area times the wing chord. Vertical equilibrium in level flight gives

$$
L=L_w+P=W=\tfrac12\rho V^2SC_L\quad\Rightarrow\quad C_L=C_{L_w}+C_{L_T}\frac{S_T}{S},
$$

so the bracket in the second term is the whole-aircraft lift coefficient, and

$$
\boxed{\,C_{m_G}=C_{m0}+(h-h_0)\,C_L-\bar V\,C_{L_T}\,}.
$$

The trim conditions are then $C_{m_G}=0$ (from $M_G=0$) together with $C_L=C_{L_w}+C_{L_T}S_T/S$ (from $W=L_w+P$). Both have to be satisfied at once: the tail load changes the lift the wing must carry.

> [!tip] Where the tail force goes
> With $l_T$ measured between the two aerodynamic centres and $l_{CG}$ from the wing AC to the CG, the moment is $M_{CG}=L_wl_{CG}+M_W-L_T(l_T-l_{CG})+M_T$, and regrouping gives $(L_w+L_T)l_{CG}+M_W-L_Tl_T+M_T$. This and the derivation above both lead to $C_{m_G}=C_L(h-h_0)+C_{m0}-\bar VC_{L_T}$: the tail lift appears once inside $C_L$, acting at the wing AC, and once as a pure couple $-\bar VC_{L_T}$.

### Downwash and the tailplane angle of attack

The tailplane sits in the flow behind the wing, which the trailing vortices deflect downwards by the **downwash angle** $\varepsilon$ ([[Downwash and Induced Drag]]). With downwash velocity $w$,

$$
\varepsilon\approx\tan\varepsilon=\frac{w}{V},
$$

and since $w/V$ is proportional to $C_L/(\pi AR)$, which is proportional to $\alpha$, the downwash is written as

$$
\varepsilon=\frac{d\varepsilon}{d\alpha}\,\alpha,
$$

with $d\varepsilon/d\alpha$ usually between 0.25 and 0.5, depending on where the tailplane sits. A downwash $\varepsilon_0$ at zero wing lift can be included, $\varepsilon=\varepsilon_0+(d\varepsilon/d\alpha)\alpha$, and is usually taken as $\varepsilon_0=0$.

The tailplane is set at a rigging (setting) angle $\alpha_s$ to the wing datum (the slides' $i_H$), and carries an elevator deflected by $\eta$, positive trailing edge down (the slides' $\delta_e$). Measured from the local, deflected flow, the tailplane angle of attack is

$$
\alpha_T=\alpha+\alpha_s-\varepsilon
$$

$$
\alpha_T=\alpha+\alpha_s-\frac{d\varepsilon}{d\alpha}\alpha
$$

$$
\alpha_T=\alpha\left(1-\frac{d\varepsilon}{d\alpha}\right)+\alpha_s .
$$

![[mof_m11_tail_downwash.png|950]]

The tailplane lift is linear in its angle of attack and in the elevator angle:

$$
C_{L_T}=a_{1T}\,\alpha_T+a_{2T}\,\eta,\qquad a_{1T}=\frac{\partial C_{L_T}}{\partial\alpha_T}\ (\eta\text{ fixed}),\quad a_{2T}=\frac{\partial C_{L_T}}{\partial\eta}\ (\alpha_T\text{ fixed}).
$$

$a_{1T}$ is the tailplane lift-curve slope and $a_{2T}$ the elevator effectiveness (the slides' $dC_{L_T}/d\delta_e$, normally constant for a given elevator). For the complete aircraft $C_L=a_1\alpha$ with $a_1=dC_L/d\alpha$.

### The full moment equation

Substitute $C_L=a_1\alpha$ and the tailplane lift into $C_{m_G}=C_{m0}+(h-h_0)C_L-\bar VC_{L_T}$:

$$
\boxed{\,C_{m_G}=C_{m0}+(h-h_0)\,a_1\alpha-\bar V\left\{a_{1T}\left[\alpha_s+\alpha\left(1-\frac{d\varepsilon}{d\alpha}\right)\right]+a_{2T}\,\eta\right\}\,}.
$$

The wing-plus-body part rises with $\alpha$ when the CG is aft of the AC (destabilising), and the tailplane part falls with $\alpha$ (stabilising), starting from a nose-up value at zero lift when the tail is set at negative incidence. Their sum is the complete-aircraft line, and where it crosses zero is the trimmed lift coefficient. A different tailplane or elevator angle shifts the tailplane line up or down and so moves the trim point without changing the slope.

![[mof_m11_cm_components.png|900]]

## 3. Trim: elevator angle and tailplane angle

At trim $C_{m_G}=0$. Solving the full moment equation for the elevator angle:

$$
\bar Va_{2T}\,\eta=C_{m0}+(h-h_0)\,a_1\alpha-\bar Va_{1T}\left[\alpha_s+\alpha\left(1-\frac{d\varepsilon}{d\alpha}\right)\right].
$$

On an all-moving tailplane the whole surface is rotated instead ($\eta=0$), and the tailplane angle to trim is

$$
\bar Va_{1T}\,\alpha_s=C_{m0}+(h-h_0)\,a_1\alpha-\bar Va_{1T}\,\alpha\left(1-\frac{d\varepsilon}{d\alpha}\right).
$$

The angle of attack $\alpha$ in these equations is the one the flight condition needs: $\alpha=C_L/a_1$ with $C_L=2W/(\rho SV^2)$. Slower flight needs a higher $\alpha$, so a stable aircraft needs a different elevator angle at every speed (Section 5).

### Trim in terms of the zero-lift moment

Grouping the terms that do not depend on $\alpha$ gives a zero-lift moment about the CG. With the wing and body at zero incidence from their zero-lift line ($\alpha_{wb}=0$) the wing lift is zero, so only $C_M$ and the tail lift at zero wing incidence remain:

$$
C_{M_0}=C_M+V_{HT}\,a_T\,(\varepsilon_0-i_H).
$$

With $C_M<0$, $\varepsilon_0\approx0$ and the tail set at negative incidence ($i_H<0$), the tail produces a download at zero lift and $C_{M_0}$ becomes positive, which is what a stable aircraft needs to trim at positive lift. With the elevator term $C_{L_T}=a_T\alpha_T+(dC_{L_T}/d\delta_e)\delta_e$, the moment becomes

$$
C_{M_{CG}}=C_{M_0}+\frac{dC_{M_{CG}}}{d\alpha}\,\alpha_{wb}-V_{HT}\frac{dC_{L_T}}{d\delta_e}\,\delta_e,
$$

and setting it to zero at the required incidence $\alpha_{wb}=\alpha_{req}$ gives the elevator angle to trim:

$$
\boxed{\,\delta_e=\frac{C_{M_0}+\left(\dfrac{dC_{M_{CG}}}{d\alpha}\right)\alpha_{req}}{V_{HT}\left(\dfrac{dC_{L_T}}{d\delta_e}\right)}\,}.
$$

A negative $\delta_e$ is trailing edge up. This is the earlier elevator equation regrouped, with $C_{M_0}=C_{m0}-\bar Va_{1T}\alpha_s$.

### Trim drag and the forward CG limit

The design case for the largest up-elevator angle is the highest-$C_L$ condition, $\alpha=\alpha_{stall}$, and the most forward CG is set by the largest negative elevator angle available at maximum $C_L$. When the tailplane carries a download, the wing must carry the weight plus that download, so both surfaces produce extra induced drag. This is **trim drag**, and it is one reason not to put the CG further forward than stability needs.

## 4. Static stability, the neutral point and the static margin

With the controls held fixed ($\eta$ and $\alpha_s$ constant, "stick fixed"), differentiate the full moment equation with respect to $\alpha$:

$$
\frac{dC_{m_G}}{d\alpha}=(h-h_0)\,a_1-\bar Va_{1T}\left(1-\frac{d\varepsilon}{d\alpha}\right).
$$

The first term grows as the CG moves aft (larger $h$); the second does not depend on the CG. So there is a CG position $h=h_n$ at which the slope is zero, the **neutral point** (stick fixed):

$$
(h_n-h_0)\,a_1-\bar Va_{1T}\left(1-\frac{d\varepsilon}{d\alpha}\right)=0
$$

$$
\boxed{\,h_n=h_0+\bar V\,\frac{a_{1T}}{a_1}\left(1-\frac{d\varepsilon}{d\alpha}\right)\,}.
$$

The neutral point is the rearmost CG position for static stability: any CG aft of it gives a statically unstable aircraft, stick fixed, and the condition for stability is $h<h_n$. It is in effect the aerodynamic centre of the whole aircraft, the point about which the total pitching moment does not change with incidence. A larger tail volume, a more effective tail ($a_{1T}$) and less downwash all move it aft.

The **C of G margin** (stick fixed), usually called the **static margin**, is

$$
\boxed{\,K_n=h_n-h\,},
$$

which must be positive. Subtracting the neutral-point condition from the slope equation,

$$
\frac{dC_{m_G}}{d\alpha}-0=(h-h_0)a_1-(h_n-h_0)a_1
$$

$$
\boxed{\,\frac{dC_{m_G}}{d\alpha}=-a_1\,(h_n-h)=-a_1K_n\,}.
$$

Dividing by $dC_L/d\alpha=a_1$ gives the equivalent form $dC_{m_G}/dC_L=-K_n$. The static margin is a direct measure of longitudinal static stability: the larger it is, the stronger the restoring moment per unit change in lift coefficient, and the more elevator is needed to change the trimmed condition, so a very stable aircraft is also less manoeuvrable. The stick-free case is added in [[Neutral Point and Static Margin]] (SESA2022).

![[mof_m11_cg_sweep.png|900]]

The figure shows the same aircraft with the CG at four positions. The zero-lift moment $C_{M_0}$ does not depend on the CG (at zero lift there is no wing lift to have a moment arm), so every line passes through the same point and the CG changes only the slope. Moving the CG aft rotates the line anticlockwise through neutral ($K_n=0$, horizontal) to unstable. Moving the CG is therefore one way to change trim; the elevator, which shifts the line up or down, is the other.

## 5. Trim and C of G margin, elevator angle against speed

In level flight $L=W$, so $\tfrac12\rho V^2SC_L$ is constant and $V^2C_L$ is constant. Differentiating with respect to $V$,

$$
\frac{d(V^2C_L)}{dV}=V^2\frac{dC_L}{dV}+2VC_L=0
$$

$$
\frac{dC_L}{dV}=-\frac{2C_L}{V}.
$$

By the chain rule, with $dC_L/d\alpha=a_1$,

$$
\frac{d\eta}{dV}=\frac{d\eta}{d\alpha}\,\frac{d\alpha}{dC_L}\,\frac{dC_L}{dV}=\frac{d\eta}{d\alpha}\left(-\frac{2C_L}{a_1V}\right).
$$

Differentiate the elevator-to-trim equation of Section 3 with respect to $\alpha$ (the setting $\alpha_s$ is fixed):

$$
\bar Va_{2T}\,\frac{d\eta}{d\alpha}=(h-h_0)\,a_1-\bar Va_{1T}\left(1-\frac{d\varepsilon}{d\alpha}\right)=a_1\,(h-h_n),
$$

using the neutral-point result. Multiply by $-2C_L/(a_1V)$:

$$
\bar Va_{2T}\,\frac{d\eta}{dV}=-\frac{2C_L}{a_1V}\,a_1\,(h-h_n)=-\frac{2C_L}{V}\,(h-h_n)
$$

$$
\boxed{\,\frac{d\eta}{dV}=\frac{2C_L}{V}\,\frac{K_n}{\bar Va_{2T}}\,}.
$$

For a stable aircraft ($K_n>0$) the elevator angle to trim increases (more trailing edge down) as speed rises, and more up-elevator is needed to fly slower. The rate is largest when the speed is low (high $C_L$, and $V$ in the denominator) and when the static margin is large, that is with the CG well forward. With $K_n=0$ the elevator angle does not change with speed at all, and with $K_n<0$ the gradient reverses, which a pilot would feel as the aircraft trying to diverge from any trimmed speed. See also [[Elevator Angle to Trim]].

![[mof_m11_elevator_trim_speed.png|900]]

## 6. Tailplane and control design

The tailplane must give adequate pitch stability in every configuration and must not need an excessive $C_{L_T}$ in the forward-CG, flaps-extended case. To save weight and drag it should be as small as possible, so the ideal CG range is the one for which the stability requirement (aft CG limit) and the control requirement (forward CG limit) call for the same tailplane size. Where possible the tailplane should be kept out of strong downwash (high $d\varepsilon/d\alpha$ reduces its effectiveness through $1-d\varepsilon/d\alpha$), out of the wake of flaps and dive brakes, and out of intense propeller slipstream.

The elevator must be able to trim and manoeuvre the aircraft in all configurations, stall it in all configurations, land it in a tail-down attitude, and lift the nose wheel on take-off below the stalling speed; the last three usually size it, and the critical case is usually the forward CG. The aileron is usually sized by the landing approach, for example to roll to 60° of bank in 7 seconds, and must allow cross-wind landings in gusty conditions. The rudder is sized to counter an engine failure on take-off or to allow safe cross-wind landings.

Directional (yaw) stability is provided by the fin in the same way as pitch stability by the tailplane, with a vertical tail volume coefficient based on span instead of chord, $V_{VT}=l_{VT}S_{VT}/(bS)$, whose typical values are much smaller than those of $V_{HT}$. In roll, dihedral provides a restoring moment, anhedral reduces roll stability for manoeuvrability, and a vertical offset between the CG and the centre of pressure (a high wing) also helps; see [[Lateral and Directional Stability]].

A canard puts the horizontal lifting surface ahead of the wing. Its lift then acts ahead of the CG and is destabilising, which makes the aircraft manoeuvrable but harder to balance, places the CG awkwardly on large aircraft, and disturbs the flow over the main wing.

## Worked examples

### Aerodynamic centre from wind-tunnel moments

A wing-body model has zero lift at $\alpha=-1.5°$ and $C_L=0.52$ at $5°$. The moment coefficients about the CG are $-0.01$ at $1°$ and $0.05$ at $7.88°$, and the CG is at $0.35\bar c$. Find the AC position and $C_M$.

The lift slope is

$$
a=\frac{0.52-0}{5-(-1.5)}=0.08\ \text{per degree}.
$$

With $\tilde l_{CG}=h-h_{ac}$ and $C_L=a(\alpha-\alpha_0)$, each measurement gives one equation in the two unknowns:

$$
-0.01=0.08\times(1+1.5)\,\tilde l_{CG}+C_M=0.2\,\tilde l_{CG}+C_M,
$$

$$
0.05=0.08\times(7.88+1.5)\,\tilde l_{CG}+C_M=0.7504\,\tilde l_{CG}+C_M.
$$

Subtracting the first from the second,

$$
0.06=0.5504\,\tilde l_{CG}\quad\Rightarrow\quad\tilde l_{CG}=0.109,
$$

and back-substituting, $C_M=-0.01-0.2\times0.109=-0.0318$. The AC is at

$$
h_{ac}=0.35-0.109=0.241\ (\approx0.24\bar c),
$$

close to the quarter chord, as thin-aerofoil theory predicts. The slope $dC_{m_G}/d\alpha=a\,\tilde l_{CG}=+0.0087$/deg is positive: the wing-body alone with this CG is unstable.

### Moment about the CG of a model with a tailplane

A wind-tunnel model has $S=0.1$ m², $\bar c=0.1$ m, $S_T=0.02$ m², tail setting $i_H=-2.7°$ relative to the wing, $a_T=0.1$/deg, $d\varepsilon/d\alpha=0.35$, $a=0.08$/deg and $C_M=-0.032$. The wing AC is 0.011 m ahead of the CG and the CG is 0.17 m ahead of the tail AC. Find $C_{M_{CG}}$ at $\alpha=7.88°$.

The assumptions are those of Section 2: thrust and drag through the CG, tailplane moment neglected, linear lift curves, $\varepsilon_0=0$ and $C_L\approx C_{L_w}$. The geometry gives

$$
h-h_{ac}=\frac{0.011}{0.1}=0.11,\qquad l_T=0.011+0.17=0.181\ \text{m},\qquad V_{HT}=\frac{S_Tl_T}{S\bar c}=\frac{0.02\times0.181}{0.1\times0.1}=0.362 .
$$

With $C_{L_T}=a_T\big[\alpha(1-d\varepsilon/d\alpha)-\varepsilon_0+i_H\big]$,

$$
C_{M_{CG}}=a\alpha\,(h-h_{ac})+C_M-a_T\alpha V_{HT}\left(1-\frac{d\varepsilon}{d\alpha}\right)+a_TV_{HT}\,(\varepsilon_0-i_H)
$$

$$
=0.08(7.88)(0.11)-0.032-0.1(7.88)(0.65)(0.362)+0.1(0.362)(2.7)
$$

$$
=0.06934-0.032-0.18542+0.09774=-0.0503 .
$$

The moment is nose down, so at $7.88°$ the model is above its trim incidence. The same numbers also give the trim point and the margin. The zero-lift moment and slope are

$$
C_{M_0}=-0.032+0.362\times0.1\times2.7=0.0657,\qquad\frac{dC_{M_{CG}}}{d\alpha}=0.08\times0.11-0.1\times0.362\times0.65=-0.01473\ \text{per degree},
$$

so it trims at $\alpha=0.0657/0.01473=4.46°$ and is stable. The neutral point and margin are

$$
h_n-h_{ac}=\frac{a_T}{a}V_{HT}\left(1-\frac{d\varepsilon}{d\alpha}\right)=1.25\times0.362\times0.65=0.294,\qquad K_n=0.294-0.110=0.184,
$$

and $-aK_n=-0.08\times0.184=-0.01473$ per degree, as before.

### Tail area for a given static margin

A small UAV has a rectangular wing of aspect ratio 6 and area 1.2 m², $C_L=5(\alpha+2/57.3)$, a tailplane with $C_{L_T}=5\alpha_T$ placed 1 m behind the wing (between aerodynamic centres), $d\varepsilon/d\alpha=0.2$, and the CG at mid-chord. The aerodynamic centres are at the quarter chord. Find the tailplane area for a static margin of 0.15.

The positions are $h=0.5$ and $h_{ac}=0.25$, so the required neutral point is $h_n=h+K_n=0.65$. The lift slopes are $a=5$ and $a_T=5$ per radian (the $+2/57.3$ only shifts the zero-lift angle and does not affect the slope). Rearranging the neutral-point equation for the tail volume:

$$
V_{HT}=(h_n-h_{ac})\,\frac{a}{a_T}\,\frac{1}{1-d\varepsilon/d\alpha}=0.4\times\frac55\times\frac{1}{0.8}=0.5 .
$$

For a rectangular wing $S=b\bar c$ and $A=b^2/S$, so $b=\sqrt{SA}=\sqrt{7.2}=2.683$ m and $\bar c=S/b=0.4472$ m, giving $S\bar c=0.5367$ m³. Then

$$
S_T=V_{HT}\,\frac{S\bar c}{l_T}=0.5\times\frac{0.5367}{1}=0.268\ \text{m}^2 .
$$

> [!check] Back-substitution
> $V_{HT}=0.268\times1/0.5367=0.500$, and $h_n=0.25+0.5\times1\times0.8=0.65$, so $K_n=0.65-0.5=0.15$.

### Elevator angle to trim

A full-scale aircraft has $S=19$ m², $W=22.7$ kN, elevator effectiveness $dC_{L_T}/d\delta_e=0.04$/deg, $a=0.08$/deg, $C_{M_0}=0.06$, $dC_{M_{CG}}/d\alpha=-0.0133$/deg and $V_{HT}=0.34$. Find the elevator angle to trim at 61 m/s at sea level.

The lift coefficient and incidence required are

$$
C_L=\frac{2W}{\rho SV^2}=\frac{2\times22\,700}{1.225\times19\times61^2}=0.524,\qquad\alpha_{req}=\frac{C_L}{a}=\frac{0.524}{0.08}=6.55°.
$$

Then

$$
\delta_e=\frac{C_{M_0}+(dC_{M_{CG}}/d\alpha)\,\alpha_{req}}{V_{HT}\,(dC_{L_T}/d\delta_e)}=\frac{0.06-0.0133\times6.55}{0.34\times0.04}=\frac{-0.0271}{0.0136}=-2.00°,
$$

so the elevator is deflected 2° trailing edge up. The static margin is $K_n=0.0133/0.08=0.166$, and the trim gradient at this speed, from Section 5 with $\bar Va_{2T}=0.0136$ per degree, is

$$
\frac{d\eta}{dV}=\frac{2\times0.524}{61}\times\frac{0.166}{0.0136}=0.210\ \text{degrees per m/s}.
$$

The elevator would be neutral at the speed where $\alpha_{req}=0.06/0.0133=4.51°$, which is 73.5 m/s.

> [!check] Gradient by finite difference
> Evaluating $\delta_e(V)$ at 60.99 and 61.01 m/s gives a slope of 0.2101°/(m/s), matching the formula.

## Terminology and alternative names

The course notes and the slides use different symbols for the same quantities; both appear in questions.

| Course notes (§8) | Slides v2 (pp. 199–220) | Meaning |
|---|---|---|
| $h_0$ | $h_{ac}$ | wing AC position, fraction of $\bar c$ from the leading edge |
| $C_{m0}$, $M_0$ | $C_M$, $M_W$ | moment of wing plus body about its AC (at zero lift) |
| $\bar V$ | $V_{HT}$ | tail volume coefficient $S_Tl_T/(S\bar c)$ |
| $a_1$ | $a$ | lift-curve slope (aircraft, or wing-body) |
| $a_{1T}$ | $a_T$ | tailplane lift-curve slope |
| $a_{2T}$ | $dC_{L_T}/d\delta_e$ | elevator effectiveness ("elevator control effectiveness") |
| $\alpha_s$ | $i_H$ | tailplane setting (rigging) angle |
| $\eta$ | $\delta_e$ | elevator angle, positive trailing edge down |
| $P$ | $L_T$ | tailplane lift |
| C of G margin (stick fixed) | static margin | $K_n=h_n-h$ |

## Links

- Parent: [[SESA1015 Intro to Aero & Astro Hub]] · Solutions: [[SESA1015 T07 - Trim and Static Stability Solutions]]
- Previous: [[SESA1015 M10 - Turning Flight and Manoeuvre Performance]] · Next: [[SESA1015 M12 - Aircraft Constraint Analysis]]
- Builds on: [[SESA1015 M03 - Aerodynamic Characteristics and the Drag Polar]] (pitching moment, centre of pressure, aerodynamic centre) · [[SESA1015 M04 - Steady Level Flight and Stall]] ($C_L=2W/\rho SV^2$)
- Concepts: [[Static Margin and Tail Volume]] · [[Elevator Angle to Trim]] · [[Neutral Point and Static Margin]] · [[Aerodynamic Centre and Centre of Pressure]] · [[Downwash and Induced Drag]] · [[Lateral and Directional Stability]]
- Later in the degree: the full trim and stability treatment with stick-free margins, manoeuvre margin and flight-test neutral points in [[SESA2022 T6 - Aircraft Aerodynamics and Static Stability]], [[Stick-Fixed vs Stick-Free Stability]] and [[Manoeuvre Point and Manoeuvre Margin]]; static derivatives in the state-space model of [[SESA2027 A2 - Longitudinal State-Space Model and Aerodynamic Derivatives]]; dynamic stability (short-period and phugoid) in [[SESA2027 A3 - Longitudinal Dynamic Modes - SPO and Phugoid]]; the trade-off in [[Stability vs Manoeuvrability]].

## Sources

- Mechanics of Flight Course Notes (Prof. A. Keane, October 2020), §8 Introduction to Longitudinal Stability: §8.1 trim, static stability and control, moments about the CG, tail volume coefficient, downwash, elevator and tailplane angle to trim, trim drag (pp. 49–54); §8.2 longitudinal static stability, neutral point and C of G margin stick fixed (pp. 54–55); §8.2.1 trim and C of G margin (pp. 55–56); §8.3 tailplane design (pp. 56–57); §8.4 control design (p. 57).
- Mechanics of Flight Lecture Slides version 2: stability introduction, trim, static and dynamic stability (pp. 184–188); rocket static stability (pp. 189–191); aircraft pitch stability (pp. 192–195); aerodynamic moment (pp. 196–198); wing-body moment and example (pp. 199–200); moments with a tail, tail lift and downwash (pp. 203–205); zero-lift moment (p. 206); tail or canard (p. 207); example (p. 208); neutral point and static margin (pp. 209–210); example (p. 211); stick-fixed longitudinal control and example (pp. 212–217); yaw and roll (pp. 218–219); rubric (p. 220).
- Revision workbook Q8 and Q13: [[SESA1015 T07 - Trim and Static Stability Solutions]].

## Self-study tasks

### Core

- [ ] Revision Q8: tailplane area for a static margin of 0.18 ("there will be a static margin question in the exam", workbook sheet Q8). → [[SESA1015 T07 - Trim and Static Stability Solutions#Question 8]]
- [ ] Revision Q13: stabiliser trim angle with the CG at the wing-body AC. → [[SESA1015 T07 - Trim and Static Stability Solutions#Question 13]]
- [ ] Slides v2 p. 211 example: tail area for a static margin of 0.15. → [[#Tail area for a given static margin]]
- [ ] Slides v2 p. 208 example: moment about the CG of the model, deriving the equation and stating the assumptions. → [[#Moment about the CG of a model with a tailplane]]
- [ ] Derive the neutral point and $dC_{m_G}/d\alpha=-a_1K_n$ from the moment equation without notes. → [[#4. Static stability, the neutral point and the static margin]]

### Further practice

- [ ] Slides v2 p. 200 example: aerodynamic centre and $C_M$ from two wind-tunnel moment readings. → [[#Aerodynamic centre from wind-tunnel moments]]
- [ ] Slides v2 p. 217 example: elevator angle to trim at 61 m/s. → [[#Elevator angle to trim]]
- [ ] Derive $d\eta/dV=2C_LK_n/(V\bar Va_{2T})$ (Notes §8.2.1) and check it on the p. 217 aircraft (suggested, not lecturer-set). → [[#5. Trim and C of G margin, elevator angle against speed]]
- [ ] Once SESA2022 Topic 6 is reached: [[SESA2022 Examples Sheet 6 - Static Stability Solutions]] extends the same model to stick-free and manoeuvre margins.

## Transcript and slide slips

> [!warning] Slide slip (Slides v2 p. 217)
> Where: [[#Elevator angle to trim]].
>
> The incidence is rounded to $\alpha_{req}=6.5°$ before it is used, which gives $\delta_e=(0.06-0.0133\times6.5)/0.0136=-1.94°$. The unrounded value is $\alpha_{req}=0.5242/0.08=6.55°$, which gives $\delta_e=-2.00°$. The numerator is a small difference of two similar numbers, so the rounding moves the answer by 3 %.

> [!warning] Slide slip (Slides v2 p. 219)
> Where: [[#6. Tailplane and control design]].
>
> The slide on dihedral and ailerons is titled "Directional static stability - Roll". Roll stability is lateral stability; directional stability refers to yaw (the previous slide, p. 218).
