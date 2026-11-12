---
title: "SESA1015 M08 - Glide and Climb Performance"
module: "SESA1015 Intro to Aero & Astro"
type: topic
stream: "Mechanics of Flight"
order: 8
tags:
  - sesa1015
  - mechanics-of-flight
  - glide
  - climb
  - excess-power
aliases: ["SESA1015 Mechanics 8", "Gliding and Climbing Flight", "Glide and Climb"]
date: 2026-09-27
status: lectured
coverage: "Course Notes §7.1 (gliding flight without thrust: glide angle, minimum glide angle, rate of descent, minimum sink) and §7.2 (steady climbing flight with a thrust vector angle, specific excess thrust, shallow-climb method); Slides v2 pp. 131–145 (climb equations with acceleration, specific excess power, energy exchange, best climb rate and best climb angle for a jet, glide angle and descent rate, worked examples, rubric)"
parent: ["[[SESA1015 Intro to Aero & Astro Hub]]"]
prerequisites: ["[[SESA1015 M04 - Steady Level Flight and Stall]]", "[[SESA1015 M05 - Minimum Drag, Power and Performance Curves]]"]
next_topics: ["[[SESA1015 M09 - Take-off and Landing Performance]]"]
key_concepts: ["[[Glide Angle and Rate of Descent]]", "[[Specific Excess Power and Rate of Climb]]", "[[Minimum Drag and Minimum Power]]", "[[Parabolic Drag Polar]]"]
tutorial_sheets: ["[[SESA1015 T05 - Climb and Glide Solutions]]"]
sources: ["02 - Sources/Mechanics of Flight/Mechanics of Flight - Course Notes.pdf (§7.1–7.2, pp. 36–38)", "02 - Sources/Mechanics of Flight/Mechanics of Flight - Lecture Slides version 2.pdf (pp. 131–145)"]
---

# SESA1015 M08 - Glide and Climb Performance

> [!abstract] Summary
> In a steady glide without thrust, lift and drag together balance the weight, so the glide angle obeys $\tan\theta=D/L$: the flattest glide and the longest still-air distance come at $(L/D)_{max}$, the minimum-drag condition, with $\theta_{min}\approx2\sqrt{KC_{D0}}$. The rate of descent is $V\sin\theta\approx DV/W$, the power required divided by the weight, so the slowest sink comes at the minimum-power condition instead. In a climb the same force balance with thrust gives $\sin\theta=(T\cos\gamma-D)/W$ (specific excess thrust sets the angle) and $dh/dt=V(T\cos\gamma-D)/W$ (specific excess power sets the rate); for a jet at constant thrust the steepest climb is at $V_{MD}$ and the fastest climb at a much higher speed.

> [!summary]- Exam use: quick path
> - **Use it when:** a question asks for a glide angle, glide distance or sink rate, the thrust needed for a given rate of climb, the climb rate or angle for given thrust and drag, or the best climb rate and best climb angle of a jet.
> - **Assumptions:** steady flight ($dV/dt=0$), straight path, still air; $\theta$ is the climb (or glide) angle and $\gamma$ the thrust vector angle; shallow path so $L\approx W$ sets the speed or $C_L$; parabolic polar $C_D=C_{D0}+KC_L^2$; angles in radians in $\theta\approx(T-D)/W$; speeds are true airspeeds unless the question works in EAS.
> - **Method:** 1. Draw the forces along and normal to the flight path. 2. Glide: $\tan\theta=D/L$, distance $=hL/D$, sink $=V\sin\theta$. 3. Climb at a given speed: $C_L=2W/(\rho V^2S)$, then $C_D$, then $D$. 4. $T\cos\gamma=D+W\,(dh/dt)/V$, or $dh/dt=V(T\cos\gamma-D)/W$. 5. For best rate or angle use $C_{L,\dot h_{max}}$ or $(\sin\theta)_{max}=T/W-1/(L/D)_{max}$.
> - **Common mistakes:** taking minimum sink to occur at $(L/D)_{max}$ (that is the flattest glide; minimum sink is at minimum power); using degrees in $\theta=(T-D)/W$ or dividing excess power by mass instead of weight.
> - **Practise:** [[#Thrust for a steady climb at 400 knots]] · [[SESA1015 T05 - Climb and Glide Solutions#Question 17]]

A glider, or an aircraft whose engines have stopped, cannot hold height: the only force able to balance drag is a component of the weight, and that component exists only if the flight path points downwards. The aircraft trades height for the work done against drag. A steady glide is the state in which the rate of loss of potential energy, $W\times$ (sink rate), equals the rate at which drag dissipates energy, $DV$. Two different quantities follow from this balance. The distance travelled from a given height depends on the path angle, so on $L/D$. The time aloft depends on the sink rate, so on $DV$, the power required.

A climb is the same picture with thrust added. Whatever thrust exceeds the drag can either push the aircraft up the slope or accelerate it along the path. Divided by the weight, the excess thrust is the sine of the steepest steady climb angle, and the excess power is the steepest steady rate of climb. Because thrust and power depend on speed differently, the speed for the steepest climb (best angle, to clear an obstacle) differs from the speed for the fastest climb (best rate, to reach altitude soonest). The glide results are the special case $T=0$ of the climb results, with the sign of $dh/dt$ reversed.

The curves of drag and power required against speed from [[SESA1015 M05 - Minimum Drag, Power and Performance Curves|M05]] determine the glide and climb results: minimum drag gives the flattest glide and, for a jet, the steepest climb; minimum power gives the slowest sink.

---

## 1. Steady glide without thrust

The aircraft flies along a straight path inclined at $\theta$ below the horizontal at constant true airspeed $V$ (Notes §7.1, p. 36). With no thrust, three forces act: lift $L$ normal to the flight path, drag $D$ opposite to the velocity, and weight $W$ vertically down.

![[mof_m08_glide_climb_forces.png|900]]

Resolving the weight into components along and normal to the path, steady flight requires each component to be balanced:

$$
L=W\cos\theta,
$$

$$
D=W\sin\theta .
$$

Dividing the second by the first eliminates $W$:

$$
\frac{D}{L}=\frac{W\sin\theta}{W\cos\theta}
$$

$$
\boxed{\tan\theta=\frac{D}{L}=\frac{C_D}{C_L}} .
$$

This is exact for any steady straight glide; no small-angle step has been taken. For small angles $\tan\theta\approx\theta$, so $\theta\approx D/L$ in radians. The glide angle depends only on the lift-to-drag ratio at which the aircraft is flown, so it is set by the angle of attack (through $C_L$) and not by the weight or the altitude.

The glide ratio follows from the geometry. If the path angle is constant, a height loss $h$ is accompanied by a horizontal distance $R$ with $\tan\theta=h/R$, so

$$
R=\frac{h}{\tan\theta}
$$

$$
\boxed{R=h\,\frac{L}{D}} .
$$

A glider with $L/D=40$ covers 40 km for each kilometre of height. For comparison, $(L/D)_{max}$ is about 4 for a house sparrow, 10 for a seagull, 20 for an albatross, 15–20 for a light aircraft and 30–60 for a sailplane (Slides v2, p. 63).

Lift in a glide is slightly less than the weight, $L=W\cos\theta$. For the glide angles of real aircraft (a few degrees) $\cos\theta>0.99$, which is why the flight speed is found from $L\approx W$ in the shallow-glide approximation used throughout §7.1:

$$
V\approx\sqrt{\frac{2W}{\rho SC_L}} .
$$

## 2. Flattest glide: the minimum-drag condition

Since $\tan\theta=C_D/C_L$, the flattest glide is flown at the $C_L$ that minimises $C_D/C_L$, which is the condition for maximum $L/D$ and, in level flight, minimum drag. With the parabolic polar $C_D=C_{D0}+KC_L^2$ (written $a+bC_L^2$ in Notes §7.1, so $a=C_{D0}$, $b=K$),

$$
\frac{C_D}{C_L}=\frac{C_{D0}}{C_L}+KC_L .
$$

Differentiating with respect to $C_L$ and setting the result to zero:

$$
\frac{d}{dC_L}\left(\frac{C_D}{C_L}\right)=-\frac{C_{D0}}{C_L^2}+K=0
$$

$$
KC_L^2=C_{D0}
$$

$$
C_{L_{MD}}=\sqrt{\frac{C_{D0}}{K}} .
$$

The middle line says induced drag equals profile drag. The drag coefficient there is

$$
C_{D_{MD}}=C_{D0}+KC_L^2=C_{D0}+C_{D0}=2C_{D0},
$$

and the second derivative $2C_{D0}/C_L^3>0$ confirms a minimum of $C_D/C_L$. The maximum lift-to-drag ratio is

$$
\left(\frac{L}{D}\right)_{max}=\frac{C_{L_{MD}}}{C_{D_{MD}}}=\frac{\sqrt{C_{D0}/K}}{2C_{D0}}
$$

$$
\left(\frac{L}{D}\right)_{max}=\frac{1}{2\sqrt{KC_{D0}}} .
$$

The minimum glide angle is therefore

$$
\theta_{min}=\tan^{-1}\frac{1}{(L/D)_{max}}\approx\frac{1}{(L/D)_{max}}
$$

$$
\boxed{\theta_{min}\approx2\sqrt{KC_{D0}}}\quad\text{(radians, shallow glide)},
$$

or $\theta_{min}=2(ab)^{1/2}$ in the $a$, $b$ notation (Notes §7.1, p. 36). Weight does not appear: a heavier glider of the same shape glides at the same angle, but faster, since $V_{MD}=\sqrt{2W/(\rho SC_{L_{MD}})}$ grows as $\sqrt{W/S}$. Altitude does not appear either; the same angle is flown at a higher true airspeed in thinner air.

### Engine-out glide after a bird strike

A twin-engined airliner loses both engines at 975 m above the ground. It has $(L/D)_{max}=18.1$ and $C_D=0.017+0.045C_L^2$ (Slides v2, p. 144). Find the minimum glide angle and the still-air distance over the ground.

The polar is consistent with the stated ratio: $1/(2\sqrt{0.045\times0.017})=18.08$. The minimum glide angle is

$$
\theta_{min}=\tan^{-1}\frac{1}{18.1}=\tan^{-1}(0.05525)=3.16^\circ ,
$$

and the distance covered while losing 975 m is

$$
R=h\left(\frac{L}{D}\right)_{max}=975\times18.1=17\,647.5\ \text{m}\approx17.6\ \text{km}.
$$

> [!check] Numerical check
> Flying instead at the minimum-sink condition of §3, $C_D/C_L=\frac{4}{\sqrt3}\sqrt{KC_{D0}}=0.0639$, so $L/D=15.66$ and the distance falls to $975/0.0639=15.2$ km. Minimum sink is the wrong choice when the aim is to reach a runway.

## 3. Rate of descent and minimum sink

The rate of descent is the vertical component of the velocity (Notes §7.1, p. 37):

$$
-\frac{dh}{dt}=-\dot h=V\sin\theta .
$$

Substituting $\sin\theta=D/W$ from the force balance along the path,

$$
-\dot h=V\,\frac{D}{W}
$$

$$
\boxed{-\dot h=\frac{DV}{W}=\frac{P_{req}}{W}} .
$$

The sink rate is the power required divided by the weight: potential energy is lost at the rate $W(-\dot h)$, and drag dissipates energy at the rate $DV$. The slowest sink therefore comes at the minimum-power condition, not at minimum drag.

To find that condition in terms of $C_L$, use $L\approx W$ for the speed, $V=\sqrt{2W/(\rho SC_L)}$, and $D/W\approx D/L=C_D/C_L$:

$$
-\dot h\approx V\frac{C_D}{C_L}
$$

$$
-\dot h\approx\sqrt{\frac{2W}{\rho SC_L}}\;\frac{C_D}{C_L}
$$

$$
-\dot h\approx\sqrt{\frac{2W}{\rho S}}\;\frac{C_D}{C_L^{3/2}} .
$$

For a given aircraft at a given altitude only $C_D/C_L^{3/2}$ varies, so the minimum sink comes where that ratio is least (Slides v2, p. 143). Write it out with the parabolic polar:

$$
\frac{C_D}{C_L^{3/2}}=C_{D0}C_L^{-3/2}+KC_L^{1/2}.
$$

Differentiate and set to zero:

$$
\frac{d}{dC_L}\left(\frac{C_D}{C_L^{3/2}}\right)=-\frac32C_{D0}C_L^{-5/2}+\frac12KC_L^{-1/2}=0 .
$$

Multiply through by $2C_L^{5/2}$:

$$
-3C_{D0}+KC_L^2=0
$$

$$
KC_L^2=3C_{D0}
$$

$$
C_{L_{MP}}=\sqrt{\frac{3C_{D0}}{K}} .
$$

Induced drag is now three times the profile drag, and

$$
C_{D_{MP}}=C_{D0}+3C_{D0}=4C_{D0}.
$$

The glide angle at this condition is steeper than the minimum:

$$
\theta_{\dot h_{min}}\approx\frac{C_{D_{MP}}}{C_{L_{MP}}}=\frac{4C_{D0}}{\sqrt{3C_{D0}/K}}
$$

$$
\theta_{\dot h_{min}}\approx\frac{4}{\sqrt3}\sqrt{KC_{D0}}=2.309\sqrt{KC_{D0}} ,
$$

which is $2/\sqrt3=1.155$ times $\theta_{min}$. The speed is lower than $V_{MD}$:

$$
V_{\dot h_{min}}=V_{MP}=\sqrt{\frac{2W}{\rho SC_{L_{MP}}}}=\sqrt{\frac{2W}{\rho S}}\left(\frac{K}{3C_{D0}}\right)^{1/4}=3^{-1/4}V_{MD}=0.760\,V_{MD}.
$$

The minimum sink rate is the product of the two:

$$
-\dot h_{min}=V_{\dot h_{min}}\,\theta_{\dot h_{min}}
$$

$$
-\dot h_{min}=\sqrt{\frac{2W}{\rho S}}\left(\frac{K}{3C_{D0}}\right)^{1/4}\cdot\frac{4}{\sqrt3}\left(KC_{D0}\right)^{1/2}
$$

$$
-\dot h_{min}=\frac{4}{3^{3/4}}\sqrt{\frac{2W}{\rho S}}\;K^{3/4}C_{D0}^{1/4}
$$

$$
\boxed{-\dot h_{min}=1.755\sqrt{\frac{2W}{\rho S}}\left(C_{D0}K^3\right)^{1/4}} .
$$

The sink rate grows as $\sqrt{W/S}$ and as $1/\sqrt\rho$: a heavily loaded aircraft, or the same aircraft high up, comes down faster, although at the same angle.

![[mof_m08_glide_hodograph.png|900]]

The hodograph plots sink rate against horizontal speed for every $C_L$. A straight line from the origin to any point on the curve has slope $\tan\theta$, so the flattest glide is where the line from the origin just touches the curve (minimum drag), and the minimum sink is the top of the curve (minimum power). Flying slower than $V_{MP}$ increases both the angle and the sink rate, which is the wrong side of the curve in every respect.

### Best glide and minimum sink of a 15-tonne jet

The jet of Slides v2, p. 139 with its engines off has $m=15\,000$ kg, $S=50$ m², $C_D=0.013+0.157C_L^2$, at sea level ($\rho=1.225$ kg m⁻³), so $W=147\,150$ N and $2W/(\rho S)=4805$ m² s⁻².

At minimum drag, $C_{L_{MD}}=\sqrt{0.013/0.157}=0.2878$ and $C_{D_{MD}}=0.026$, so

$$
\left(\frac{L}{D}\right)_{max}=\frac{0.2878}{0.026}=11.07,\qquad\theta=\tan^{-1}\frac{1}{11.07}=5.16^\circ,
$$

$$
V_{MD}=\sqrt{\frac{4805}{0.2878}}=129.2\ \text{m s}^{-1},\qquad-\dot h=129.2\sin5.16^\circ=11.63\ \text{m s}^{-1}.
$$

At minimum power, $C_{L_{MP}}=\sqrt{3}\times0.2878=0.4984$ and $C_{D_{MP}}=0.052$, so

$$
\frac{L}{D}=\frac{0.4984}{0.052}=9.58,\qquad\theta=\tan^{-1}\frac{1}{9.58}=5.96^\circ,
$$

$$
V_{MP}=\sqrt{\frac{4805}{0.4984}}=98.2\ \text{m s}^{-1},\qquad-\dot h=98.2\sin5.96^\circ=10.19\ \text{m s}^{-1}.
$$

From 975 m the aircraft stays up $975/10.19=95.7$ s at minimum sink but only $975/11.63=83.8$ s at best glide, while best glide takes it $975\times11.07=10.8$ km against $975\times9.58=9.3$ km.

> [!check] Numerical check
> The closed form gives $-\dot h_{min}=1.755\sqrt{4805}\,(0.013\times0.157^3)^{1/4}=10.25$ m s⁻¹. The 0.6 % difference from 10.19 m s⁻¹ is the small-angle step $\sin\theta\approx\tan\theta$ in the closed form.

## 4. Steady climbing flight

In a climb the flight path is inclined at $\theta$ above the horizontal and the thrust line is inclined at the thrust vector angle $\gamma$ to the flight path (Notes §7.2, p. 37; Slides v2, p. 133). Here $\theta$ is the path angle and $\gamma$ the thrust angle, the reverse of many textbooks.

Newton's second law along the flight path, allowing the speed to change, and equilibrium normal to it give

$$
m\frac{dV}{dt}=T\cos\gamma-D-W\sin\theta,
$$

$$
0=L+T\sin\gamma-W\cos\theta,
$$

and the rate of climb is the vertical component of the velocity,

$$
\frac{dh}{dt}=V\sin\theta .
$$

Divide the first equation by $W=mg$:

$$
\frac{T\cos\gamma-D}{W}=\sin\theta+\frac1g\frac{dV}{dt}.
$$

Multiply by $V$ and use $V\sin\theta=dh/dt$:

$$
\boxed{\frac{(T\cos\gamma-D)V}{W}=\frac{dh}{dt}+\frac{V}{g}\frac{dV}{dt}} .
$$

With $TV=P_{av}$ and $DV=P_{req}$ the left side is $(P_{av}\cos\gamma-P_{req})/W$, the specific excess power, a velocity. The equation says excess power can be spent on climbing, on accelerating, or on a mix of the two (Slides v2, p. 134). With the thrust along the path ($\gamma=0$), dividing instead by $V$ gives the specific excess thrust form:

$$
\frac{T-D}{W}=\frac1V\frac{dh}{dt}+\frac1g\frac{dV}{dt}.
$$

The same energy statement with no excess power at all says height and speed can be exchanged. Integrating $dh=-(V/g)\,dV$ from $V_1$ to $V_2$ gives $mg(h_2-h_1)=\frac12m(V_1^2-V_2^2)$. Slowing from 90 to 60 m s⁻¹ buys

$$
\Delta h=\frac{90^2-60^2}{2\times9.81}=\frac{4500}{19.62}=229\ \text{m}
$$

of height (Slides v2, p. 134), a useful reserve in an emergency.

For a steady climb $dV/dt=0$, and the boxed equation becomes (Notes §7.2, p. 38)

$$
\boxed{\frac{dh}{dt}=V\sin\theta=\frac{V\,(T\cos\gamma-D)}{W}},\qquad\sin\theta=\frac{T\cos\gamma-D}{W}.
$$

With $\gamma=0$, $(T-D)/W$ is the specific excess thrust and equals $\sin\theta$. The thrust needed for a required rate of climb follows by rearranging:

$$
T\cos\gamma=D+W\,\frac{1}{V}\frac{dh}{dt}.
$$

### The shallow-climb method

For a shallow climb with zero thrust angle ($\gamma=0$, $\cos\theta\approx1$, so $L\approx W$), the climb angle at a given speed $V$ is found in four steps (Notes §7.2, p. 38). First the lift coefficient from $L=W$:

$$
C_L=\frac{2W}{\rho V^2S}.
$$

Then the drag coefficient from the polar, $C_D=C_{D0}+KC_L^2$, and the drag $D=\frac12\rho V^2SC_D$. Finally the climb angle from the specific excess thrust,

$$
\theta=\sin^{-1}\left(\frac{T-D}{W}\right),
$$

or for small angles $\theta\approx(T-D)/W$ in radians, with rate of climb $dh/dt=V\theta$. The approximation $L\approx W$ is only as good as $\cos\theta\approx1$: at $\theta=15^\circ$ the true lift is 3.4 % below the weight, so the method loses accuracy at the steep climbs a high-$T/W$ aircraft can fly.

### Thrust for a steady climb at 400 knots

An aircraft with wing loading 4700 N m⁻², wing area 78 m² and $C_D=0.018+0.06C_L^2$ is to climb steadily at 6 m s⁻¹ at 400 kn at sea level, with a small thrust angle (Slides v2, pp. 132 and 135). Find the thrust.

The weight and speed are

$$
W=\frac{W}{S}\,S=4700\times78=366\,600\ \text{N},
$$

$$
V=400\times0.5144=205.76\ \text{m s}^{-1}.
$$

With $L\approx W$,

$$
C_L=\frac{2(W/S)}{\rho V^2}=\frac{2\times4700}{1.225\times205.76^2}=0.1812,
$$

$$
C_D=0.018+0.06\times0.1812^2=0.01997,
$$

$$
D=\tfrac12\rho V^2SC_D=\tfrac12\times1.225\times205.76^2\times78\times0.01997=40\,395\ \text{N}.
$$

The climb term is

$$
W\frac{1}{V}\frac{dh}{dt}=366\,600\times\frac{6}{205.76}=10\,690\ \text{N},
$$

so, with $\cos\gamma\approx1$,

$$
T=D+\frac{W}{V}\frac{dh}{dt}=40\,395+10\,690=51\,085\ \text{N}.
$$

The climb angle is $\sin^{-1}(6/205.76)=1.67^\circ$, comfortably shallow. About a fifth of the thrust goes into lifting the aircraft; the rest balances drag.

## 5. Best climb rate and best climb angle at constant thrust

A jet's thrust varies little with speed at a given altitude, so take $T$ constant and $\gamma=0$ (Slides v2, p. 140). With $L\approx W$ ("quasi-level flight") the speed is $V=\sqrt{2W/(\rho SC_L)}$ and $D/W\approx C_D/C_L$, so

$$
\frac{dh}{dt}=V\left(\frac TW-\frac DW\right)
$$

$$
\frac{dh}{dt}=\sqrt{\frac{2W}{\rho SC_L}}\left(\frac TW-\frac{C_D}{C_L}\right)
$$

$$
\frac{dh}{dt}=\sqrt{\frac{2W}{\rho S}}\left(\frac TW\,C_L^{-1/2}-\frac{C_D}{C_L^{3/2}}\right).
$$

The first term in the bracket falls as $C_L$ rises (higher $C_L$ means lower speed, and the excess thrust is converted into height more slowly); the second term is the sink-rate function of §3. Substitute the polar:

$$
f(C_L)=\frac TW\,C_L^{-1/2}-C_{D0}C_L^{-3/2}-KC_L^{1/2}.
$$

Differentiate and set to zero:

$$
f'(C_L)=-\frac12\frac TW\,C_L^{-3/2}+\frac32C_{D0}C_L^{-5/2}-\frac12KC_L^{-1/2}=0 .
$$

Multiply by $-2C_L^{5/2}$:

$$
\frac TW\,C_L-3C_{D0}+KC_L^2=0
$$

$$
KC_L^2+\frac TW\,C_L-3C_{D0}=0 .
$$

This quadratic has one positive root:

$$
\boxed{C_{L_{\dot h_{max}}}=\frac{-(T/W)+\sqrt{(T/W)^2+12KC_{D0}}}{2K}} .
$$

With $T=0$ it reduces to $\sqrt{3C_{D0}/K}$, the minimum-sink value, as it must. As $T/W$ grows, the root falls, so the best-rate speed rises well above $V_{MD}$: a powerful jet climbs fastest at high speed.

The best climb angle comes from $\sin\theta=T/W-D/W$. At constant $T$ this is largest where $D/W\approx C_D/C_L$ is least, which is the minimum-drag condition:

$$
\boxed{(\sin\theta)_{max}=\frac TW-\frac{1}{(L/D)_{max}}}\qquad\text{at }V_{MD}.
$$

![[mof_m08_climb_performance.png|900]]

If instead the power available is roughly constant with speed, as for a propeller aircraft, the specific excess power $(P_{av}-P_{req})/W$ is largest where $P_{req}$ is least, so the best rate of climb is at $V_{MP}$ and equals $(P_{av}-P_{req,min})/W$.

### Best climb rate and angle of a jet

A jet of mass 15 000 kg and wing area 50 m² has $C_D=0.013+0.157C_L^2$ and $T/W=0.429$. Find the climb angle at the best climb rate and the corresponding equivalent climb rate, then the best climb angle (unaccelerated shallow climb, zero thrust angle; Slides v2, pp. 139 and 141).

The weight is $W=15\,000\times9.81=147\,150$ N. The lift coefficient for best rate is

$$
C_{L_{\dot h_{max}}}=\frac{-0.429+\sqrt{0.429^2+12\times0.157\times0.013}}{2\times0.157}
$$

$$
C_{L_{\dot h_{max}}}=\frac{-0.429+\sqrt{0.18404+0.02449}}{0.314}=\frac{-0.429+0.45666}{0.314}=0.0881 .
$$

Then

$$
C_D=0.013+0.157\times0.0881^2=0.01422,
$$

$$
\sin\theta=\frac TW-\frac{C_D}{C_L}=0.429-\frac{0.01422}{0.0881}=0.429-0.1614=0.2676,
$$

so $\theta=15.5^\circ$. The speed at sea-level density is

$$
V_e=\sqrt{\frac{2W}{\rho_0SC_L}}=\sqrt{\frac{2\times147\,150}{1.225\times50\times0.0881}}=233.6\ \text{m s}^{-1},
$$

an equivalent airspeed because $\rho_0$ was used, and the equivalent climb rate is

$$
\dot h_e=V_e\sin\theta=233.6\times0.2676=62.5\ \text{m s}^{-1}.
$$

For the best angle, $(L/D)_{max}=1/(2\sqrt{0.157\times0.013})=11.07$, so

$$
(\sin\theta)_{max}=0.429-\frac{1}{11.07}=0.429-0.0904=0.3386,\qquad\theta_{max}=19.8^\circ .
$$

That steepest climb is flown at $V_{MD}=129.2$ m s⁻¹ EAS, where the rate of climb is only $129.2\times0.3386=43.8$ m s⁻¹. The best-angle climb gains height per metre of ground; the best-rate climb gains height per second.

> [!check] Numerical check
> A brute-force search over $C_L$ of $\sqrt{2W/(\rho_0SC_L)}\,(T/W-C_D/C_L)$ peaks at $C_L=0.0881$ with 62.50 m s⁻¹, confirming the quadratic. The "shallow climb" here is $15.5^\circ$, so $L\approx W$ overstates the lift by $1/\cos15.5^\circ-1=3.8$ %. Iterating with $L=W\cos\theta$ at the same $C_L$ gives $V=229$ m s⁻¹, $\theta=15.9^\circ$ and 62.7 m s⁻¹: the rate barely changes, because the lower speed and the steeper angle almost cancel.

## 6. Limits of the steady analysis

The results above hold for shallow climbs at modest rates (Notes §7.2, p. 38). Many high-performance aircraft have $T/W$ above 1, and can then climb vertically, which a steady analysis with $L\approx W$ cannot describe at all: in a vertical climb $\cos\theta=0$ and the wing carries no load. At very high climb rates the density changes appreciably during the climb, so neither $T$ nor $D$ is constant and the climb is no longer steady; optimum climb schedules then become an energy-height problem beyond this steady analysis. The same caution applies to the glide: the glide angle is fixed by $L/D$, but the true airspeed for that angle falls as the aircraft descends into denser air if the pilot holds $C_L$ constant, which is what "flying at $(L/D)_{max}$" means.

## Links

- Parent: [[SESA1015 Intro to Aero & Astro Hub]] · Solutions: [[SESA1015 T05 - Climb and Glide Solutions]]
- Previous: [[SESA1015 M07 - Propeller Aircraft Range and Endurance]] · Next: [[SESA1015 M09 - Take-off and Landing Performance]]
- Builds on: [[SESA1015 M04 - Steady Level Flight and Stall]] (lift equation, flight speed from $L=W$) · [[SESA1015 M05 - Minimum Drag, Power and Performance Curves]] (minimum drag and minimum power conditions)
- Concepts: [[Glide Angle and Rate of Descent]] · [[Specific Excess Power and Rate of Climb]] · [[Minimum Drag and Minimum Power]] · [[Parabolic Drag Polar]] · [[Wing Loading]] · [[Airspeed Measures]] · [[Maximum Lift-to-Drag Ratio]]
- Used in: [[SESA1015 M12 - Aircraft Constraint Analysis]] (the climb constraint is $T/W=\frac{1}{V}\frac{dh}{dt}+\frac{q}{W/S}C_D$)
- Later in the degree: thrust lapse with speed and altitude in [[SESA2023 W01 - Thrust, Efficiency, Range and the ISA]]; the exchange of height and speed as a dynamic mode in [[Phugoid Mode]] and [[SESA2027 A3 - Longitudinal Dynamic Modes - SPO and Phugoid]].

## Sources

- Mechanics of Flight Course Notes (Keane, October 2020): §7.1 Gliding flight without thrust (pp. 36–37), §7.2 Steady climbing flight (pp. 37–38)
- Mechanics of Flight Lecture Slides version 2: climb example (pp. 132, 135), climbing-flight equations (pp. 133–134, 138), jet climb (pp. 139–141), glide angle and descent rate (pp. 142–143), bird-strike glide (p. 144), climb, descent and glide rubric (p. 145); lift-to-drag ratios of birds and aircraft (p. 63)
- Worked solutions: [[SESA1015 T05 - Climb and Glide Solutions]]

## Self-study tasks

### Core

- [ ] Revision Q17: thrust for a 7 m s⁻¹ climb at 452 kn with a 9° thrust angle. → [[#Thrust for a steady climb at 400 knots]] · [[SESA1015 T05 - Climb and Glide Solutions#Question 17]]
- [ ] Revision Q18: climb rate from given thrust, drag and thrust-vectoring angle. → [[#4. Steady climbing flight]] · [[SESA1015 T05 - Climb and Glide Solutions#Question 18]]
- [ ] Slides v2, pp. 132 and 135: thrust for a steady 6 m s⁻¹ climb; derive the relation first. → [[#Thrust for a steady climb at 400 knots]]
- [ ] Slides v2, pp. 139 and 141: best climb rate, its climb angle and the best climb angle of a jet with $T/W=0.429$. → [[#Best climb rate and angle of a jet]]
- [ ] Slides v2, p. 144: minimum glide angle and glide distance after a double engine failure at 975 m. → [[#Engine-out glide after a bird strike]]

### Further practice

- [ ] Derive $C_{L_{MP}}=\sqrt{3C_{D0}/K}$ and the 1.755 coefficient of the minimum sink rate from $C_D/C_L^{3/2}$ (Notes §7.1, p. 37; Slides v2, p. 143). → [[#3. Rate of descent and minimum sink]]
- [ ] Derive the quadratic $KC_L^2+(T/W)C_L-3C_{D0}=0$ for the best climb rate and show it reduces to the minimum-sink condition when $T=0$ (Slides v2, p. 140). → [[#5. Best climb rate and best climb angle at constant thrust]]
- [ ] Energy exchange: height gained by slowing from 90 to 60 m s⁻¹ (Slides v2, p. 134). → [[#4. Steady climbing flight]]
- [ ] Glide of the 15-tonne jet: best-glide and minimum-sink speeds, angles and sink rates at sea level; repeat at 6 km ($\rho=0.660$ kg m⁻³) and show the angles are unchanged while speeds and sink rates rise by $\sqrt{1.225/0.660}$ (suggested, not set in the course). → [[#Best glide and minimum sink of a 15-tonne jet]]

## Transcript and slide slips

> [!warning] Slide slip (Slides v2, p. 135)
> Where: [[#Thrust for a steady climb at 400 knots]].
>
> The weight is printed as $W=78\times4700=36\,660$ N; the product is $366\,600$ N. The thrust on the slide, 51 084.7 N, uses the correct weight, so only the printed line is wrong.

> [!warning] Slide slip (Slides v2, pp. 142 and 144)
> Where: [[#Engine-out glide after a bird strike]].
>
> The glide angle is written $\sin\theta=D/L$ and $\theta_{min}=\sin^{-1}\big(1/(L/D)_{max}\big)=3.17^\circ$. In a steady glide $D=W\sin\theta$ and $L=W\cos\theta$, so the exact relation is $\tan\theta=D/L$ (Notes §7.1, p. 36), giving $3.16^\circ$; $\sin\theta=D/L$ holds only in the shallow-glide approximation $L\approx W$. The slide's distance, 17 647 m, equals $975\times18.1$, which is the exact $\tan$ result; $975/\tan3.17^\circ$ would give 17 621 m.
