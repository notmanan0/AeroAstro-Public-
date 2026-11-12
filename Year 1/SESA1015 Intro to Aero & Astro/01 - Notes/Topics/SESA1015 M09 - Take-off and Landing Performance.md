---
title: "SESA1015 M09 - Take-off and Landing Performance"
module: "SESA1015 Intro to Aero & Astro"
type: topic
stream: "Mechanics of Flight"
order: 9
tags:
  - sesa1015
  - mechanics-of-flight
  - takeoff
  - landing
  - ground-run
  - high-lift
aliases: ["SESA1015 Mechanics 9", "Take-off and Landing", "Takeoff and Landing Performance"]
date: 2026-09-27
status: lectured
coverage: "Course Notes §7.3 (take-off critical speeds and definitions, take-off distance to the 35 ft screen, runway equation of motion with friction, ground run with lift and drag neglected, s1 in terms of wing loading, CLmax and T/W, effects of density, wind and slope); Slides v2 pp. 146–168 (accelerated performance, high-lift devices, take-off speeds and conditions, take-off calculations, sea-level, Denver and Mexico City examples, numerical integration with lift and drag, landing phases and landing ground run, ground effect)"
parent: ["[[SESA1015 Intro to Aero & Astro Hub]]"]
prerequisites: ["[[SESA1015 M04 - Steady Level Flight and Stall]]", "[[SESA1015 M08 - Glide and Climb Performance]]"]
next_topics: ["[[SESA1015 M10 - Turning Flight and Manoeuvre Performance]]"]
key_concepts: ["[[Take-off Ground Run]]", "[[Take-off Reference Speeds]]", "[[Wing Loading]]", "[[Parabolic Drag Polar]]"]
tutorial_sheets: ["[[SESA1015 T02 - Take-off and Landing Solutions]]"]
sources: ["02 - Sources/Mechanics of Flight/Mechanics of Flight - Course Notes.pdf (§7.3, pp. 38–41)", "02 - Sources/Mechanics of Flight/Mechanics of Flight - Lecture Slides version 2.pdf (pp. 146–168)"]
---

# SESA1015 M09 - Take-off and Landing Performance

> [!abstract] Summary
> On the take-off run the aircraft accelerates along the runway under thrust, opposed by drag and by rolling friction $\mu_r(W-L)$, until it reaches a lift-off speed tied to the stall speed, typically $V_2=1.2V_s$. Writing $dV/dt=V\,dV/dx$ turns Newton's law into an integral for the ground run; with $T/W$ constant and $L/W$, $D/W$ neglected it gives $s_1=V_2^2/[2g(T/W-\mu_r)]=\frac{1.44}{\rho g}\frac{W}{S}\frac{1}{C_{L_{max}}}\frac{1}{T/W-\mu_r}$, so a short run needs low wing loading, high $C_{L_{max}}$, high $T/W$ and dense air. Including lift and drag lengthens the run (by 31 % for the Mexico City example) and is done in closed form or numerically. Landing reverses the process: from touchdown the aircraft is slowed by drag and friction, $dV/dt=-\frac{g}{W}\left(\frac12\rho V^2SC_{D0}+\mu_rW\right)$.

> [!summary]- Exam use: quick path
> - **Use it when:** a question asks for a take-off ground run, the $T/W$ or $C_{L_{max}}$ needed for a given runway, the effect of altitude, temperature, weight or wind on the run, a take-off with an engine failure, or a landing run or landing wing loading.
> - **Assumptions:** level runway, still air; $T/W$ constant; for the standard result $L/W$ and $D/W$ small during the run, acceleration stops at lift-off so $V_2\approx V_{LOF}$; $V_2=1.2V_s$ for a jet (1.15 for a piston aircraft) unless stated; $V_s$ uses $C_{L_{max}}$ in the take-off configuration and the airfield density.
> - **Method:** 1. $S=b^2/AR$, $W=mg$. 2. $V_s=\sqrt{2W/(\rho SC_{L_{max}})}$, $V_2=kV_s$. 3. $s_1=V_2^2/[2g(T/W-\mu_r)]$, or rearrange for $T/W$ or $V_2$. 4. Inverse for $C_L$: $V_2\to V_s\to C_L=2(W/S)/(\rho V_s^2)$. 5. With lift and drag: $s_1=\frac{1}{2gb}\ln\frac{a}{a-bV_2^2}$ or integrate numerically.
> - **Common mistakes:** using sea-level density at a high or hot airfield; forgetting to subtract $\mu_r$ from $T/W$, or using total thrust per engine after a failure.
> - **Practise:** [[#Thrust-to-weight ratio for a 1723 m runway]] · [[SESA1015 T02 - Take-off and Landing Solutions#Question 3]]

Take-off and landing are the two parts of a flight in which the speed changes a great deal, so the steady-flight balances do not apply. At the start of the take-off run the wing produces no lift and the whole weight sits on the wheels; the aircraft must accelerate until the wing can carry the weight with a safe margin over the stall. The runway needed depends on how much speed is needed and how hard the aircraft can accelerate to it. The speed is set by the stall speed, and so by wing loading, $C_{L_{max}}$ and air density; the acceleration is set by thrust minus drag minus friction, per unit mass.

That is why take-off is the problem that high-lift devices are designed for. Flaps and slats raise $C_{L_{max}}$, which lowers the stall speed and hence the lift-off speed, and the run falls with the square of that speed. It is also why hot, high airfields need long runways: the thinner air raises the true airspeed needed for the same lift. Landing is the take-off run in reverse. The aircraft arrives at an approach speed with a margin over the stall and must lose all its kinetic energy on the runway through aerodynamic drag, wheel friction and braking, and possibly reverse thrust.

---

## 1. Take-off phases and critical speeds

During take-off the aircraft accelerates from rest through a sequence of critical speeds (Notes §7.3, pp. 38–39; Slides v2, pp. 154–155).

![[mof_m09_takeoff_profile.png|900]]

The **decision speed** $V_1$ is the speed up to which, if the critical engine fails, the aircraft can still decelerate to rest within the available runway; above $V_1$ the take-off must be continued. At the **rotation speed** $V_R$ the pilot raises the nose, increasing the angle of attack so that the lift rises rapidly. The aircraft continues to accelerate to the **lift-off speed** $V_{LOF}$, at which it leaves the ground, for example with lift 10 % greater than the weight, enough to unstick the aircraft from the runway (Slides v2, p. 154). A transition phase follows, curving the path into a constant climb angle, and the aircraft keeps accelerating to the **take-off safety speed** or screen speed $V_2$, reached at the imaginary screen height of 35 ft (10.7 m). The take-off distance is the total distance from the start of the run to the screen, $s_1+s_2$.

The speeds are tied to each other and to the stall speed by certification rules (Notes §7.3, p. 39):

| Speed | Meaning | Condition |
|---|---|---|
| $V_s$ | stall speed in the take-off configuration | |
| $V_{mu}$ | minimum unstick speed: lowest speed at which the aircraft can safely lift off and continue the take-off | |
| $V_{mca}$ | minimum control speed in the air: with the critical engine inoperative, control can be recovered and straight flight held | |
| $V_{mcg}$ | minimum control speed on the ground: a straight path can be held with a failed engine without nose-gear reactions | |
| $V_1$ | decision speed, shortly after the critical engine-failure speed | aerodynamic controls alone adequate above it |
| $V_R$ | rotation speed | $V_R>V_1$ and $V_R\ge1.05V_{mca}$ |
| $V_{LOF}$ | lift-off speed | $V_{LOF}\ge1.1V_{mu}$ all engines, $1.05V_{mu}$ engine out |
| $V_2$ | take-off climb speed at 35 ft | $V_2\ge1.1V_{mca}$ and $V_2\ge1.2V_s$ (jet), $1.15V_s$ (piston) |

Strictly, $V_2$ is the speed a twin should reach at the screen after a critical engine failure at $V_1$. Here acceleration is taken to stop at lift-off, so that $V_2\approx V_{LOF}$, and the ground run $s_1$ is the distance to reach $V_2$ (Notes §7.3, p. 40).

Throughout the run the flaps and slats are at their take-off settings. These give a greater $C_L$ than the clean wing and so a lower stall speed. Take-off flap angles are much smaller than landing flap angles, so the drag increase is modest.

## 2. The equation of motion on the runway

![[mof_m09_runway_forces.png|900]]

Three forces act along a level runway: thrust $T$ forwards, drag $D$ backwards, and the rolling friction at the wheels, also backwards. The friction is the friction coefficient times the normal reaction on the wheels, and the normal reaction is whatever part of the weight the wing does not yet carry, $W-L$:

$$
F_{fr}=\mu_r(W-L).
$$

Newton's second law along the runway, with mass $m=W/g$, is (Notes §7.3, p. 40; Slides v2, p. 156)

$$
T-D-\mu_r(W-L)=\frac{W}{g}\frac{dV}{dt}.
$$

The run is wanted as a distance, not a time, so change the independent variable with the chain rule:

$$
\frac{dV}{dt}=\frac{dV}{dx}\frac{dx}{dt}=V\frac{dV}{dx}.
$$

Substituting and dividing by $W$:

$$
\boxed{\frac TW-\frac DW-\mu_r\left(1-\frac LW\right)=\frac Vg\frac{dV}{dx}} .
$$

Here $L$ and $D$ are the values on the ground run, functions of the angle of attack held on the runway and of the speed, $L=\frac12\rho V^2SC_L$ and $D=\frac12\rho V^2SC_D$. As the speed rises, drag grows and friction falls; the net accelerating force changes along the run, so the acceleration is not constant. Strictly the equation is integrated from $V=0$ to $V_2$ with these $L$ and $D$ substituted, a numerical task in general (Slides v2, p. 156); §4 gives a closed form for constant coefficients.

## 3. Ground run with lift and drag neglected

An approximate ground run follows from two assumptions (Notes §7.3, p. 40): $T/W$ is constant, and $D/W$ and $L/W$ are both very small during the ground run before lift-off. The equation of motion becomes

$$
\frac TW-\mu_r=\frac Vg\frac{dV}{dx}.
$$

The left side is constant, so the variables separate:

$$
g\left(\frac TW-\mu_r\right)dx=V\,dV .
$$

Integrate from rest at $x=0$ to $V_2$ at $x=s_1$:

$$
g\left(\frac TW-\mu_r\right)\int_0^{s_1}dx=\int_0^{V_2}V\,dV
$$

$$
g\left(\frac TW-\mu_r\right)s_1=\frac{V_2^2}{2}
$$

$$
\boxed{s_1=\frac{1}{\left(\frac TW-\mu_r\right)}\frac{V_2^2}{2g}} .
$$

This is the constant-acceleration result $s=V^2/(2a)$ with $a=g(T/W-\mu_r)$. For $V_2=1.2V_s$, with the stall speed in the take-off configuration given by

$$
V_s^2=\frac{2W}{\rho SC_{L_{max}}},
$$

so that

$$
V_2^2=1.44\,V_s^2=1.44\,\frac{2W}{\rho SC_{L_{max}}}.
$$

Then

$$
s_1=\frac{1}{\left(\frac TW-\mu_r\right)}\cdot\frac{1}{2g}\cdot1.44\,\frac{2W}{\rho SC_{L_{max}}}
$$

$$
\boxed{s_1=\frac{1.44}{\rho g}\left(\frac WS\right)\left(\frac{1}{C_{L_{max}}}\right)\frac{1}{\left(\frac TW-\mu_r\right)}} .
$$

The last factor can also be written $\dfrac{W/T}{1-\mu_rW/T}$ (Notes §7.3); multiplying top and bottom by $T/W$ shows this is the same as $1/(T/W-\mu_r)$. $C_{L_{max}}$ is the maximum lift coefficient in the take-off configuration and in ground effect (Notes §7.3, p. 41).

For a given $C_{L_{max}}$, the ground run depends on three groups (Notes §7.3, p. 41; Slides v2, p. 157):

| Parameter | Effect on $s_1$ | Reason |
|---|---|---|
| wing loading $W/S$ | low $W/S$ gives short $s_1$ | lower stall speed, so lower $V_2$ |
| thrust-to-weight ratio $T/W$ | high $T/W$ gives short $s_1$ | larger acceleration |
| density $\rho$ | low $\rho$ gives long $s_1$ | higher true airspeed needed; hot, high airports need longer runways |
| $C_{L_{max}}$ | high $C_{L_{max}}$ gives short $s_1$ | lower stall speed (flaps, slats) |

Weight enters twice, through $W/S$ and through $T/W$ at fixed thrust, so its effect is stronger than proportional. For the sea-level aircraft below ($T/W=0.1677$, $\mu_r=0.02$), a 10 % heavier take-off multiplies $s_1$ by

$$
1.1\times\frac{0.1677-0.02}{0.1677/1.1-0.02}=1.1\times\frac{0.1477}{0.1325}=1.227,
$$

a 23 % longer run. Since $s_1\propto1/\rho$, a fixed-thrust comparison between two airfields is just the density ratio; on a hot day at constant pressure $\rho=p/(RT)$, so $s_1\propto T$ (Revision Q28).

### Wind and runway slope

All the above assumes still air and a level runway; taking off into wind or down a slope shortens the run (Notes §7.3, p. 41). Both effects follow from the same integration. Lift depends on airspeed, so the aircraft still needs airspeed $V_2$ to lift off; with a headwind $V_w$ it already has airspeed $V_w$ at rest, so the ground speed it must reach is only $V_2-V_w$. If the acceleration is unchanged,

$$
s_1=\frac{(V_2-V_w)^2}{2g\left(\frac TW-\mu_r\right)} .
$$

For the sea-level case below, a 10 m s⁻¹ headwind cuts 1723 m to $1723\times(60.67/70.67)^2=1270$ m. On a runway sloping down at angle $\phi$, the weight has a component $W\sin\phi$ along the runway that helps the thrust, and the normal reaction becomes $W\cos\phi-L$; with small $\phi$ in radians

$$
s_1\approx\frac{V_2^2}{2g\left(\frac TW-\mu_r+\phi\right)} .
$$

A 1° downslope adds 0.0175 to the effective $T/W-\mu_r$ of 0.148, shortening the same run to 1541 m. An upslope lengthens it by the same mechanism.

### Thrust-to-weight ratio for a 1723 m runway

A twin-engined aircraft must take off on a 1723 m runway at sea level, with $V_2=1.2V_s$, span 28.42 m, aspect ratio 12.8, $C_{L_{max}}=2.0$, $C_D=0.12$, take-off mass 27 330 kg and $\mu_r=0.02$ (Slides v2, p. 158). Find the $T/W$ required, assuming $T/W$ constant and $L/W$, $D/W$ small.

The wing area and weight are

$$
S=\frac{b^2}{AR}=\frac{28.42^2}{12.8}=63.10\ \text{m}^2,\qquad W=mg=27\,330\times9.81=268\,107\ \text{N}.
$$

The stall and screen speeds are

$$
V_s=\sqrt{\frac{2W}{\rho SC_{L_{max}}}}=\sqrt{\frac{2\times268\,107}{1.225\times63.10\times2.0}}=58.89\ \text{m s}^{-1},\qquad V_2=1.2V_s=70.67\ \text{m s}^{-1}.
$$

Rearranging the ground-run result for the thrust ratio,

$$
\frac TW=\mu_r+\frac{V_2^2}{2gs_1}
$$

$$
\frac TW=0.02+\frac{70.67^2}{2\times9.81\times1723}=0.02+0.1477=0.1677 .
$$

The drag coefficient is not needed in this model; it matters only when drag is included (§4).

### The same aircraft at Denver

The aircraft, with $T/W=0.1671$, takes off from Denver at 1609 m (Slides v2, p. 159). The ISA density there is $\rho=1.047$ kg m⁻³ (from $\rho/\rho_0=(T/T_0)^{4.256}$ with $T=288.15-0.0065\times1609=277.7$ K; see [[SESA1015 M01 - Atmosphere, Airspeed and Mach Number|M01]]). Then

$$
V_s=\sqrt{\frac{2\times268\,107}{1.047\times63.10\times2.0}}=63.71\ \text{m s}^{-1},\qquad V_2=76.46\ \text{m s}^{-1},
$$

$$
s_1=\frac{76.46^2}{2\times9.81\times(0.1671-0.02)}=\frac{5846}{2.886}=2025\ \text{m}.
$$

The run is 17 % longer than at sea level for the same aircraft, which is just $\rho_0/\rho=1.170$.

![[mof_m09_altitude_effect.png|900]]

## 4. Ground run with lift and drag

The neglected terms matter. At lift-off the drag of a flapped aircraft can be half the thrust, and the friction falls to zero as the wing takes the weight. If $T$, $C_L$ and $C_D$ are held constant along the run (the aircraft rolls at a fixed attitude), the net force per unit weight is a quadratic in $V$:

$$
F=\frac TW-\frac{\frac12\rho V^2SC_D}{W}-\mu_r\left(1-\frac{\frac12\rho V^2SC_L}{W}\right)
$$

$$
F=\left(\frac TW-\mu_r\right)-\frac{\rho S}{2W}\left(C_D-\mu_rC_L\right)V^2 .
$$

Write $a=T/W-\mu_r$ and $b=\dfrac{\rho S}{2W}(C_D-\mu_rC_L)$, so $F=a-bV^2$. The equation of motion $F=\frac Vg\frac{dV}{dx}$ separates:

$$
dx=\frac{V\,dV}{g\,(a-bV^2)} .
$$

Integrate from rest to $V_2$, using the substitution $u=a-bV^2$, $du=-2bV\,dV$:

$$
s_1=\int_0^{V_2}\frac{V\,dV}{g\,(a-bV^2)}=-\frac{1}{2gb}\Big[\ln\left(a-bV^2\right)\Big]_0^{V_2}
$$

$$
\boxed{s_1=\frac{1}{2gb}\ln\left(\frac{a}{a-bV_2^2}\right)} .
$$

For small $bV_2^2/a$, $\ln\big(a/(a-bV_2^2)\big)\approx bV_2^2/a$ and the result returns to $V_2^2/(2ga)$, the §3 formula. When $T$ varies with speed, or $C_L$ changes at rotation, the integral is done numerically instead (Slides v2, pp. 164–165). Writing $G(V)=V/(gF)$ so that $dx/dV=G(V)$, the basic Euler method steps through speed:

$$
x_{n+1}=x_n+G(V_n)\,(V_{n+1}-V_n).
$$

Integrating to any speed above $V_2$ and reading the distance at $V_2$ gives the run.

![[mof_m09_mexico_ground_run.png|900]]

### Mexico City with lift and drag

The same aircraft ($T/W=0.1671$, $C_D=0.12$) takes off at Mexico City, 2240 m, with $C_L=0.8C_{L_{max}}=1.6$ throughout the run (Slides v2, pp. 162–165). Find the take-off distance including lift and drag.

The ISA density at 2240 m is 0.9824 kg m⁻³, so

$$
V_s=\sqrt{\frac{2\times268\,107}{0.9824\times63.10\times2.0}}=65.76\ \text{m s}^{-1},\qquad V_2=78.92\ \text{m s}^{-1}.
$$

With lift and drag neglected, $s_1=78.92^2/(2\times9.81\times0.1471)=2158$ m. With them,

$$
\frac{\rho S}{2W}=\frac{0.9824\times63.10}{2\times268\,107}=1.1561\times10^{-4}\ \text{s}^2\,\text{m}^{-2},
$$

$$
b=1.1561\times10^{-4}\times(0.12-0.02\times1.6)=1.0174\times10^{-5}\ \text{s}^2\,\text{m}^{-2},
$$

$$
bV_2^2=1.0174\times10^{-5}\times78.92^2=0.0634,\qquad a=0.1471,
$$

$$
s_1=\frac{1}{2\times9.81\times1.0174\times10^{-5}}\ln\frac{0.1471}{0.1471-0.0634}=\frac{\ln1.7566}{1.9961\times10^{-4}}=\frac{0.5634}{1.9961\times10^{-4}}=2822\ \text{m}.
$$

Drag lengthens the run by 31 %, and the run is about 1.1 km longer than the 1723 m sea-level runway. The simple formula underestimates the runway length.

> [!warning] Lift exceeds weight before $V_2$
> With $C_L=1.6=0.8C_{L_{max}}$ held to $V_2=1.2V_s$, the lift at $V_2$ is $0.8\times1.44=1.152\,W$. Lift equals weight at $V=V_s/\sqrt{0.8}=1.118V_s=73.5$ m s⁻¹, so from there on the term $\mu_r(1-L/W)$ in the model is negative: the "friction" pushes the aircraft forwards. A real aircraft would be airborne at 73.5 m s⁻¹ (2346 m along the runway from the same formula), and with the friction set to zero once $L\ge W$ the distance to reach $V_2$ becomes 2831 m. The effect is small here because $\mu_r=0.02$, but the model is only physical while $L<W$.

## 5. Engine failure during take-off

The decision speed exists because an engine can fail during the run. Below $V_1$ the pilot abandons the take-off and brakes to a stop; above it the aircraft continues on the remaining engines, and must still reach $V_2$ and clear the screen. Both cases use the runway equation of motion with the appropriate forces. For a continued take-off on a twin, the run splits into two parts with different constant accelerations (lift and drag neglected):

$$
s_1=\frac{V_{fail}^2}{2g\left(\frac TW-\mu_r\right)}+\frac{V_2^2-V_{fail}^2}{2g\left(\frac{T}{2W}-\mu_r\right)} .
$$

Each part comes from integrating $g(T/W-\mu_r)\,dx=V\,dV$ between its own speed limits; after the failure only half the thrust remains. For an abandoned take-off the thrust goes to zero and the deceleration is $g\mu$ with the braking coefficient in place of rolling friction (plus drag, as in the landing analysis of §7).

### Continued take-off after an engine failure

A twin-engined aircraft with $T/W=0.8$ (both engines), take-off $C_L=1.5$, span 52.4 m, aspect ratio 6, take-off weight 6 MN and $\mu_r=0.02$ takes off at sea level with $V_2=1.2V_s$. One engine fails at 65 m s⁻¹ and the take-off is continued. Find the ground run (exam-style data).

$$
S=\frac{52.4^2}{6}=457.6\ \text{m}^2,\qquad V_s=\sqrt{\frac{2\times6\times10^6}{1.225\times457.6\times1.5}}=119.46\ \text{m s}^{-1},\qquad V_2=143.35\ \text{m s}^{-1}.
$$

The accelerations before and after the failure are

$$
a_1=g\left(\frac TW-\mu_r\right)=9.81\times(0.8-0.02)=7.652\ \text{m s}^{-2},
$$

$$
a_2=g\left(\frac{T}{2W}-\mu_r\right)=9.81\times(0.4-0.02)=3.728\ \text{m s}^{-2}.
$$

The two distances are

$$
d_1=\frac{65^2}{2\times7.652}=276\ \text{m},\qquad d_2=\frac{143.35^2-65^2}{2\times3.728}=2190\ \text{m},
$$

so $s_1=2466$ m, against $143.35^2/(2\times7.652)=1343$ m with both engines. Losing half the thrust early in the run nearly doubles it.

## 6. High-lift devices and ground effect

Lift is $L=\frac12\rho V^2SC_L$, and during take-off and landing the speed is low, so the lift coefficient must be raised to carry the weight (Slides v2, p. 148). Flaps and slats do this by changing the effective camber of the aerofoil. A trailing-edge flap shifts the lift curve upwards, so the lift-curve slope is unchanged but $C_L$ at a given angle of attack is higher, $C_{L_{max}}$ increases significantly, and the stall angle shifts (Slides v2, pp. 148–153). The design aim is a large $C_{L_{max}}$ for a modest drag increase at take-off, and a large $C_{L_{max}}$ with high drag at landing, where drag helps.

At a given stall speed, the lift equation fixes the ratio of wing loading to $C_{L_{max}}$:

$$
C_{L_{max}}=\frac{2(W/S)}{\rho V_s^2}.
$$

Two aircraft with the same minimum landing speed at the same density therefore need $C_{L_{max}}$ in proportion to their wing loadings: an airliner with 40 % higher $W/S$ needs a 40 % higher $C_{L_{max}}$ (Revision Q40). The same equation gives the landing constraint on wing loading for a required approach speed, $W/S\le\frac12\rho V_A^2C_{L_{max}}$, used in [[SESA1015 M12 - Aircraft Constraint Analysis|constraint analysis]] (Revision Q39).

Close to the ground the wing behaves as if it had a higher aspect ratio: the ground blocks the downwash, so the induced drag falls significantly and the lift rises (Slides v2, p. 168). This is why $C_{L_{max}}$ in the ground-run formula is the value in ground effect, and why an aircraft tends to float in the flare.

## 7. Landing

Landing, like take-off, has at least two parts (Slides v2, pp. 166–167): the approach over a 35 ft obstacle to touchdown, and the landing ground run. The approach is normally a powered descent rather than an unpowered glide; it is the powered climb of [[SESA1015 M08 - Glide and Climb Performance|M08]] with $dh/dt$ negative. The air distance divides into approach and flare, and the ground roll into free roll, reverse thrust and braking distance.

On the ground with no thrust and the lift dumped ($T=0$, $L=0$), the runway equation gives the deceleration:

$$
-D-\mu_rW=\frac Wg\frac{dV}{dt}
$$

$$
\frac{dV}{dt}=-\frac gW\left(D+\mu_rW\right)=-\frac gW\left(\tfrac12\rho V^2SC_{D0}+\mu_rW\right)=G(V) .
$$

Write $k=\dfrac{\rho SC_{D0}}{2W}$, so $G(V)=-g(\mu_r+kV^2)$. The stopping time follows from $dt=dV/G(V)$ integrated from the landing speed $V_L$ to zero:

$$
t_{stop}=\int_{V_L}^{0}\frac{dV}{G(V)}=\int_0^{V_L}\frac{dV}{g(\mu_r+kV^2)}
$$

$$
\boxed{t_{stop}=\frac{1}{g\sqrt{\mu_rk}}\tan^{-1}\left(V_L\sqrt{\frac{k}{\mu_r}}\right)} .
$$

The stopping distance follows the same way as the take-off run, from $V\,dV/dx=G(V)$:

$$
x_{stop}=\int_0^{V_L}\frac{V\,dV}{g(\mu_r+kV^2)}
$$

$$
\boxed{x_{stop}=\frac{1}{2gk}\ln\left(1+\frac{kV_L^2}{\mu_r}\right)} .
$$

For $kV_L^2\ll\mu_r$ (drag negligible) this returns to $V_L^2/(2g\mu_r)$. The integral can equally be done numerically, stepping $V$ in time and accumulating distance (Slides v2, p. 167).

![[mof_m09_landing_run.png|900]]

### Landing run of the 27-tonne twin

Take the aircraft of §3 ($W=268\,107$ N, $S=63.10$ m²) touching down at 70 m s⁻¹ ($1.19V_s$ with $C_{L_{max}}=2.0$) at sea level, with $C_{D0}=0.12$ in the landing configuration, no reverse thrust and the lift dumped. Then

$$
k=\frac{1.225\times63.10\times0.12}{2\times268\,107}=1.730\times10^{-5}\ \text{s}^2\,\text{m}^{-2}.
$$

With rolling friction only, $\mu_r=0.02$:

$$
x_{stop}=\frac{1}{2\times9.81\times1.730\times10^{-5}}\ln\left(1+\frac{1.730\times10^{-5}\times70^2}{0.02}\right)=\frac{\ln5.238}{3.394\times10^{-4}}=4879\ \text{m},
$$

$$
t_{stop}=\frac{1}{9.81\sqrt{0.02\times1.730\times10^{-5}}}\tan^{-1}(2.059)=\frac{1.119}{5.770\times10^{-3}}=194\ \text{s}.
$$

Drag does most of the early work: without it the roll would be $70^2/(2\times9.81\times0.02)=12.5$ km. Wheel brakes raise the effective coefficient; with an illustrative braking value of 0.3 (suggested, not set in the course) the same formulas give 733 m and 21.9 s, and drag now shortens the run by only 12 % (from 832 m without it).

> [!check] Numerical check
> Integrating $dV/dt=-g(\mu_r+kV^2)$ and $dx/dt=V$ with a Runge–Kutta solver from 70 m s⁻¹ gives $V=0$ at $t=193.86$ s and $x=4879.1$ m for $\mu_r=0.02$, matching both closed forms.

## Links

- Parent: [[SESA1015 Intro to Aero & Astro Hub]] · Solutions: [[SESA1015 T02 - Take-off and Landing Solutions]]
- Previous: [[SESA1015 M08 - Glide and Climb Performance]] · Next: [[SESA1015 M10 - Turning Flight and Manoeuvre Performance]]
- Builds on: [[SESA1015 M04 - Steady Level Flight and Stall]] (stall speed, $C_{L_{max}}$) · [[SESA1015 M01 - Atmosphere, Airspeed and Mach Number]] (ISA density at an airfield)
- Concepts: [[Take-off Ground Run]] · [[Take-off Reference Speeds]] · [[Wing Loading]] · [[Parabolic Drag Polar]] · [[Specific Excess Power and Rate of Climb]] · [[International Standard Atmosphere]]
- Used in: [[SESA1015 M12 - Aircraft Constraint Analysis]] (take-off constraint $T/W=\mu_r+V_2^2/(2gs_1)$ and landing constraint on $W/S$)
- Later in the degree: flap camber in [[Trailing-Edge Flap in Thin Aerofoil Theory]] and [[SESA2022 T4 - Thin Aerofoil Theory]]; separation and the stall in [[SESA2022 T2 - Boundary Layers]] and [[Aerofoil Stall]]; ground effect by the [[Method of Images]]; thrust lapse with speed and altitude in [[SESA2023 W01 - Thrust, Efficiency, Range and the ISA]].

## Sources

- Mechanics of Flight Course Notes (Keane, October 2020): §7.3 Take-off and §7.3.1 Definitions (pp. 38–41)
- Mechanics of Flight Lecture Slides version 2: accelerated performance (p. 147), high-lift devices (pp. 148–153), take-off speeds and conditions (pp. 154–155), take-off calculations (pp. 156–157), sea-level and Denver examples (pp. 158–159), Mexico City numerical example (pp. 162–165), landing (pp. 166–167), ground effect (p. 168)
- Revision workbook (`04 - Labs & Coursework/Revision & Spreadsheets/SESA1015 - Revision Questions (Original).xlsx`): Questions 3, 7, 19, 21–24, 28, 38–40; engine-failure example data from the exam working spreadsheet (`Keane Exam.xlsx`, sheet Q5)
- Worked solutions: [[SESA1015 T02 - Take-off and Landing Solutions]]

## Self-study tasks

### Core

- [ ] Revision Q3: total thrust for a 1500 m runway. → [[#Thrust-to-weight ratio for a 1723 m runway]] · [[SESA1015 T02 - Take-off and Landing Solutions#Question 3]]
- [ ] Revision Q7 and Q19: ground run from the aircraft data, and from a given stall speed. → [[#3. Ground run with lift and drag neglected]] · [[SESA1015 T02 - Take-off and Landing Solutions#Question 7]] · [[SESA1015 T02 - Take-off and Landing Solutions#Question 19]]
- [ ] Revision Q21–Q24: take-off lift coefficient required for a given runway (inverse problem). → [[SESA1015 T02 - Take-off and Landing Solutions#Question 21]] · [[SESA1015 T02 - Take-off and Landing Solutions#Question 24]]
- [ ] Revision Q28: summer against winter ground roll. → [[SESA1015 T02 - Take-off and Landing Solutions#Question 28]]
- [ ] Slides v2, pp. 158–159: $T/W$ for a 1723 m sea-level runway, then the run at Denver; derive the formula first. → [[#Thrust-to-weight ratio for a 1723 m runway]] · [[#The same aircraft at Denver]]

### Further practice

- [ ] Slides v2, pp. 162–165: Mexico City run including lift and drag, by the closed form and by an Euler integration in Python. → [[#Mexico City with lift and drag]]
- [ ] Revision Q38–Q40: take-off $T/W$ for a UAV, landing wing-loading limit, $C_{L_{max}}$ comparison of two airliners. → [[#6. High-lift devices and ground effect]] · [[SESA1015 T02 - Take-off and Landing Solutions#Question 38]] · [[SESA1015 T02 - Take-off and Landing Solutions#Question 39]] · [[SESA1015 T02 - Take-off and Landing Solutions#Question 40]]
- [ ] Engine failure at 65 m s⁻¹ on a twin: continued ground run (exam-style). → [[#Continued take-off after an engine failure]]
- [ ] Slides v2, p. 167: landing run with $T=0$, $L=0$; derive $t_{stop}$ and $x_{stop}$ and evaluate them. → [[#Landing run of the 27-tonne twin]]

## Transcript and slide slips

> [!warning] Course-notes slip (Notes §7.3, p. 40)
> Where: [[#2. The equation of motion on the runway]].
>
> The force diagram labels the runway friction $\mu(L-W)$; the text beside it, and the equation of motion, use $\mu(W-L)$, which is the positive magnitude of a force acting backwards while $L<W$.

> [!warning] Slide slip (Slides v2, p. 154)
> Where: [[#1. Take-off phases and critical speeds]].
>
> The decision speed is said to be possibly greater than $V_2$ on a long runway. The definitions require $V_R>V_1$ (Notes §7.3, p. 39), and $V_2$ is reached after rotation, so $V_1$ cannot exceed $V_R$, let alone $V_2$; on a long runway $V_1$ is limited to $V_R$.

> [!warning] Slide slip (Slides v2, pp. 158–159)
> Where: [[#Thrust-to-weight ratio for a 1723 m runway]] and [[#The same aircraft at Denver]].
>
> | Where | Slide gives | Correct |
> |---|---|---|
> | p. 158 | $W=mg=267\,834$ N, $\rho=1.23$ kg m⁻³ | $W=27\,330\times9.81=268\,107$ N; the slide's $V_s=58.894$ m s⁻¹ follows from 268 107 N and 1.225 kg m⁻³, not from the printed values |
> | p. 158 | $T/W=0.1671$ | $0.02+70.672^2/(2\times9.81\times1723)=0.1677$ |
> | p. 159 | $\rho=1.051$ kg m⁻³ at 1609 m, $s_1=2017.2$ m | ISA gives 1.047 kg m⁻³ and $s_1=2025$ m with $T/W=0.1671$ |

> [!warning] Slide slip (Slides v2, p. 167)
> Where: [[#7. Landing]].
>
> The landing deceleration is said to be solvable only numerically because drag depends on speed. With constant $C_{D0}$ and $\mu_r$ the deceleration $-g(\mu_r+kV^2)$ integrates in closed form for both time and distance; numerical integration is needed only when thrust, braking or the drag coefficient vary along the run. The same holds for the take-off run of pp. 162–165 at constant $T$, $C_L$ and $C_D$.
