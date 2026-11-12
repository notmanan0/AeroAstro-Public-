---
title: "SESA1015 M10 - Turning Flight and Manoeuvre Performance"
module: "SESA1015 Intro to Aero & Astro"
type: topic
stream: "Mechanics of Flight"
order: 10
tags:
  - sesa1015
  - mechanics-of-flight
  - turning-flight
  - load-factor
  - manoeuvre-performance
aliases: ["SESA1015 Mechanics 10", "Turning Flight", "Turning Performance"]
date: 2026-09-27
status: lectured
coverage: "Course Notes §7.4 (co-ordinated level turn, load factor, radius of turn, stalling speed in the turn, minimum radius from the load-factor and stall limits, thrust-limited radius of turn); Slides v2 pp. 169–182 (turning flight, load factor, radius and rate of turn, thrust-limited turn, worked examples, V–n diagram, rubric)"
parent: ["[[SESA1015 Intro to Aero & Astro Hub]]"]
prerequisites: ["[[SESA1015 M04 - Steady Level Flight and Stall]]", "[[SESA1015 M05 - Minimum Drag, Power and Performance Curves]]"]
next_topics: ["[[SESA1015 M11 - Longitudinal Trim and Static Stability]]", "[[SESA1015 M12 - Aircraft Constraint Analysis]]"]
key_concepts: ["[[Load Factor and Turn Performance]]", "[[V-n Diagram]]", "[[Wing Loading]]", "[[Parabolic Drag Polar]]"]
tutorial_sheets: ["[[SESA1015 T06 - Turning Flight Solutions]]"]
sources: ["02 - Sources/Mechanics of Flight/Mechanics of Flight - Course Notes.pdf (§7.4, pp. 42–48)", "02 - Sources/Mechanics of Flight/Mechanics of Flight - Lecture Slides version 2.pdf (pp. 169–182)", "04 - Labs & Coursework/Revision & Spreadsheets/SESA1015 - Revision Questions (Original).xlsx (Q6, Q25, Q26, Q31)"]
---

# SESA1015 M10 - Turning Flight and Manoeuvre Performance

> [!abstract] Summary
> In a co-ordinated level turn the wings bank through $\phi$ and the lift tilts with them: its vertical component still carries the weight and its horizontal component supplies the centripetal force. The lift must therefore rise to $L=nW$ with load factor $n=1/\cos\phi$, the radius is $R=V^2/(g\sqrt{n^2-1})$ and the stall speed rises to $V_S\sqrt n$. The tightest turn at a given speed is set by whichever binds first of the stall limit ($C_{L,max}$), the structural load-factor limit ($n_{max}$) and, for a sustained turn, the thrust limit $R_{min}=\big(2KW^2V^2/\rho Sg^2\big)^{1/2}/\sqrt{T_{max}-D_L}$.

> [!summary]- Exam use: quick path
> - **Use it when:** a question gives a bank angle, load factor, turn radius or turn rate, asks for the thrust to hold a turn, or asks for the minimum radius "stall limited", "load-factor limited" or "thrust limited".
> - **Assumptions:** steady, level (horizontal-plane), co-ordinated turn; thrust and drag along the flight path; parabolic polar $C_D=C_{D0}+KC_L^2$; $\rho$ at the stated altitude (sea level, 1.225 kg/m³, if none); angles in a turn formula in degrees or radians consistently, rates in rad/s.
> - **Method:** 1. Get $n$ ($=1/\cos\phi$, or $(V/V_S)^2$ at the stall limit, or $n_{max}$). 2. $R=V^2/(g\sqrt{n^2-1})$, $\omega=V/R$. 3. Check $V\ge V_S\sqrt n$. 4. For thrust: $C_L=nW/(qS)$, $T=qS(C_{D0}+KC_L^2)$. 5. For a given excess thrust: $R=\big(2KW^2V^2/\rho Sg^2\big)^{1/2}/\sqrt{T-D_L}$.
> - **Common mistakes:** using $L=W$ in a turn (so the induced drag is $n^2$ times too small); quoting the radius at the corner speed as sustainable when the drag there exceeds the thrust.
> - **Practise:** [[#Corner speed and turn rate (Slides v2 p. 176)]] · [[SESA1015 T06 - Turning Flight Solutions#Question 31]]

An aircraft changes direction by banking, so that part of the lift points towards the centre of the turn. Ailerons alone roll the aircraft but leave it in a sideslip, with extra drag; rudder alone yaws it, the yaw induces a roll that tilts the lift, and the relative wind then comes from outside the turn, which is called skidding. Ailerons and rudder used together keep the aircraft aligned with the relative wind throughout, and that is a **co-ordinated turn**. The results below hold for a co-ordinated turn in the horizontal plane at constant speed.

Since the vertical part of the lift has to stay equal to the weight while the horizontal part does the turning, the total lift in a turn is always larger than the weight. Three limits follow from it. More lift at a given speed needs a higher $C_L$, so the wing reaches $C_{L,max}$ at a higher speed than in level flight (the stall speed rises); the wing structure carries $n$ times the 1 g load, so the structure caps $n$; and induced drag grows as $C_L^2$, so the engine may not be able to hold the speed. The turn radius and rate at any speed come from the force balance, and the achievable turn is whichever of the stall, structural and thrust limits is tightest.

![[mof_m10_turn_forces.png|900]]

---

## 1. Force balance in a co-ordinated level turn

The forces are lift $L$ (normal to the wings, so tilted from the vertical by the bank angle $\phi$), weight $W$, thrust $T$ and drag $D$. The speed is constant and the flight path is a horizontal circle of radius $R$, so the only acceleration is the centripetal acceleration $V^2/R$ towards the centre. Resolving along the flight path, vertically and horizontally (Notes §7.4, p. 42):

$$
T=D,
$$

$$
L\cos\phi=W,
$$

$$
L\sin\phi=\frac{W}{g}\,\frac{V^2}{R}.
$$

The last line is Newton's second law towards the centre with mass $m=W/g$.

### Lift in the turn

Square the vertical and horizontal equations and add them, so that $\sin^2\phi+\cos^2\phi=1$ removes the bank angle:

$$
L^2\sin^2\phi+L^2\cos^2\phi=W^2+\left(\frac{W}{g}\frac{V^2}{R}\right)^2
$$

$$
L^2=W^2\left[1+\left(\frac{V^2}{gR}\right)^2\right]
$$

$$
L=W\sqrt{1+\left(\frac{V^2}{gR}\right)^2}.
$$

### Load factor and bank angle

The **load factor** is the ratio of lift to weight,

$$
n=\frac{L}{W}.
$$

From the vertical balance, $\cos\phi=W/L$, so

$$
\boxed{\,n=\frac{1}{\cos\phi}\,},\qquad \sin\phi=\sqrt{1-\frac{1}{n^2}}=\frac{\sqrt{n^2-1}}{n},\qquad \tan\phi=\sqrt{n^2-1}.
$$

The bank angle and the load factor are the same information: a level co-ordinated turn at 60° bank is a 2 g turn whatever the aircraft or speed. The load factor is also what the occupants feel, and what the wing structure carries.

### Radius of turn

Rearrange the lift equation for $R$:

$$
\left(\frac{L}{W}\right)^2-1=\left(\frac{V^2}{gR}\right)^2
$$

$$
\frac{V^2}{gR}=\sqrt{n^2-1}
$$

$$
\boxed{\,R=\frac{V^2}{g}\,\frac{1}{\sqrt{n^2-1}}\,}.
$$

The same result follows from the horizontal equation alone. Dividing $L\sin\phi=(W/g)(V^2/R)$ by $L$ and solving for $R$,

$$
R=\frac{WV^2}{gL\sin\phi}=\frac{V^2}{g}\,\frac{1}{n\sin\phi},
$$

and with $n=1/\cos\phi$,

$$
R=\frac{V^2}{g}\,\frac{\cos\phi}{\sin\phi}=\frac{V^2}{g}\cot\phi=\frac{V^2}{g\tan\phi}.
$$

With $\tan\phi=\sqrt{n^2-1}$ the two forms are identical. For a fixed bank angle the radius grows as $V^2$; for a fixed speed it shrinks as the bank steepens, but only slowly once $n$ is large, since $\sqrt{n^2-1}\approx n$.

### Rate of turn

The angular velocity of the turn (the turn rate) is

$$
\omega=\frac{V}{R}=\frac{g\sqrt{n^2-1}}{V}=\frac{g\tan\phi}{V},
$$

in rad/s. A full 360° takes $2\pi/\omega$.

### Radius and rate in terms of the lift coefficient

The turn speed can be written in terms of the lift coefficient in the turn (Slides v2 p. 173). From $nW=\tfrac12\rho V^2SC_L$,

$$
V^2=\frac{2nW}{\rho SC_L}.
$$

Substituting into $R$ and $\omega$:

$$
R=\frac{2nW}{\rho SC_L}\,\frac{1}{g\sqrt{n^2-1}}=\frac{2}{\rho gC_L}\left(\frac{W}{S}\right)\frac{n}{\sqrt{n^2-1}},
$$

$$
\omega=\frac{g\sqrt{n^2-1}}{V}=g\sqrt{n^2-1}\,\sqrt{\frac{\rho SC_L}{2nW}}=g\sqrt{\frac{\rho C_L}{2}}\sqrt{\frac{S}{W}}\sqrt{\frac{n^2-1}{n}}.
$$

A small radius and a fast turn therefore both need a high lift coefficient, a low wing loading $W/S$ and a high load factor (Slides v2 p. 173). That is why combat aircraft have low wing loadings and high-lift devices, and why [[Wing Loading]] appears in the turn constraint of [[SESA1015 M12 - Aircraft Constraint Analysis]].

> [!check] A 45° bank at 80 m/s
> $n=1/\cos45°=1.414$, $\tan45°=1$, so $R=80^2/9.81=652.4$ m and $\omega=9.81/80=0.1226$ rad/s $=7.03$°/s; a full circle takes 51.2 s. If the 1 g stall speed is 40 m/s, the stall speed in this turn is $40\sqrt{1.414}=47.6$ m/s, comfortably below 80 m/s.

## 2. Stall speed in a turn

The wing stalls at the same $C_{L,max}$ whether or not the aircraft is turning, but in the turn it must produce $nW$ instead of $W$. Writing the lift equation at $C_{L,max}$ in both cases (Notes §7.4, p. 43):

$$
\text{in the turn:}\quad nW=\tfrac12\rho V_{S_T}^2SC_{L,max}\ \Rightarrow\ V_{S_T}=\left(\frac{nW}{\tfrac12\rho SC_{L,max}}\right)^{1/2},
$$

$$
\text{in level flight:}\quad W=\tfrac12\rho V_S^2SC_{L,max}\ \Rightarrow\ V_S=\left(\frac{W}{\tfrac12\rho SC_{L,max}}\right)^{1/2}.
$$

Dividing,

$$
\boxed{\,\frac{V_{S_T}}{V_S}=\sqrt n=\frac{1}{\sqrt{\cos\phi}}\,}.
$$

At 30° bank the stall speed rises by 7.5 %, at 45° by 18.9 %, at 60° by 41.4 % and at 75° by 96.6 %. The rise is gentle at small bank and very steep beyond about 60°, which is why a steep turn at low speed (for example a turn onto the final approach) is dangerous: an aircraft flying safely above its level-flight stall speed can stall in the turn.

![[mof_m10_load_factor_bank.png|850]]

## 3. Minimum radius: load-factor and stall limits

From $R=V^2/(g\sqrt{n^2-1})$, at a given speed $V$ and weight $W$ the radius is least when the lift, the load factor and the bank angle are as large as possible (Notes §7.4.1, p. 44). Two things cap them.

### Load-factor (structural) limit

The structure is designed for a maximum load factor $n_{max}$ (the limit load, with a safety factor on top for the ultimate load). At that load factor,

$$
\boxed{\,R_{min}=\frac{V^2}{g}\,\frac{1}{\sqrt{n_{max}^2-1}}\,}\qquad\text{(load-factor limit)}.
$$

This grows as $V^2$: the structural limit is the binding one at high speed.

### Stall (maximum-lift) limit

The most lift the wing can produce at speed $V$ is $L_{max}=\tfrac12\rho V^2SC_{L,max}$, and the weight is $W=\tfrac12\rho V_S^2SC_{L,max}$, where $V_S$ is the level-flight stall speed. The largest load factor available at speed $V$ is therefore

$$
n=\frac{L_{max}}{W}=\frac{\tfrac12\rho V^2SC_{L,max}}{\tfrac12\rho V_S^2SC_{L,max}}=\left(\frac{V}{V_S}\right)^2.
$$

Substituting into the radius,

$$
R_{min}=\frac{V^2}{g}\,\frac{1}{\sqrt{\left[(V/V_S)^2\right]^2-1}}
$$

$$
\boxed{\,R_{min}=\frac{V^2}{g}\,\frac{1}{\sqrt{(V/V_S)^4-1}}=\frac{V_S^2}{g}\left(\frac{V}{V_S}\right)^2\frac{1}{\sqrt{(V/V_S)^4-1}}\,}\qquad\text{(stall limit)}.
$$

The curve has two limits. As $V\to V_S$ the root tends to zero and $R_{min}\to\infty$: at the stall speed all the available lift is needed to hold the weight and none is left for turning. As $V\to\infty$, $(V/V_S)^4-1\approx(V/V_S)^4$ and

$$
R_{min}\to\frac{V_S^2}{g}\left(\frac{V}{V_S}\right)^2\frac{1}{(V/V_S)^2}=\frac{V_S^2}{g},
$$

so the stall-limited radius falls towards the floor $V_S^2/g$. Since $V_S^2=2(W/S)/(\rho C_{L,max})$, that floor is $2(W/S)/(\rho gC_{L,max})$: low wing loading and high $C_{L,max}$ are what make a small radius possible. In true airspeed, $V_S$ grows as density falls, so $R_{min}$ grows with altitude and manoeuvrability falls (Notes §7.4.1, p. 46).

### The corner speed

The stall-limited radius falls with speed and the load-factor-limited radius rises, so the absolute minimum radius is where they meet (Notes p. 46; Slides v2 p. 177). Setting $(V/V_S)^2=n_{max}$:

$$
\boxed{\,V^*=V_S\sqrt{n_{max}}\,},\qquad R^*=\frac{V^{*2}}{g\sqrt{n_{max}^2-1}}=\frac{V_S^2}{g}\,\frac{n_{max}}{\sqrt{n_{max}^2-1}}.
$$

$V^*$ is usually called the corner speed (it is the corner $V_A$ of the [[V-n Diagram]]). Below it the aircraft stalls before it reaches $n_{max}$; above it the structure limits the turn. The same speed also gives the highest instantaneous turn rate. On the stall limit, with $x=V/V_S$,

$$
\omega=\frac{g\sqrt{x^4-1}}{V_Sx},\qquad \frac{d}{dx}\left(\frac{\sqrt{x^4-1}}{x}\right)=\frac{2x^4-(x^4-1)}{x^2\sqrt{x^4-1}}=\frac{x^4+1}{x^2\sqrt{x^4-1}}>0,
$$

so the stall-limited turn rate rises with speed, while on the load-factor limit $\omega=g\sqrt{n_{max}^2-1}/V$ falls with speed. The maximum of the lower of the two is where they cross, at $V^*$.

Flight is impossible to the left of the stall limit (the required $C_L$ exceeds $C_{L,max}$), to the right of the load-factor limit (the structure is overloaded) and beyond the design speed $V_{max}$ (Notes p. 45). Those three boundaries enclose the domain of turning flight (Notes p. 45; with numbers, the figure in Section 4).

## 4. Thrust-limited radius of turn

The stall and structural limits say what turn the aircraft can enter. Whether it can hold it at constant speed depends on the engine. At a given speed the lift coefficient in the turn is $n$ times its level-flight value, so the induced drag (proportional to $C_L^2$) is $n^2$ times larger, and the maximum thrust is reached at a lower turning performance than the lift or the structure would allow (Notes §7.4.2, p. 46).

### Derivation

Set the drag in the turn equal to the maximum thrust, with the parabolic polar ([[Parabolic Drag Polar]]):

$$
D=T_{max}
$$

$$
qS\left(C_{D0}+KC_L^2\right)=T_{max},\qquad q=\tfrac12\rho V^2,\quad K=\frac{1}{\pi eAR}.
$$

In the turn the lift is

$$
L=qSC_L=W\sqrt{1+\left(\frac{V^2}{gR_{min}}\right)^2},
$$

so

$$
C_L^2=\frac{W^2}{q^2S^2}\left[1+\left(\frac{V^2}{gR_{min}}\right)^2\right].
$$

Substitute into the drag equation:

$$
qS\left\{C_{D0}+\frac{KW^2}{q^2S^2}\left[1+\left(\frac{V^2}{gR_{min}}\right)^2\right]\right\}=T_{max}
$$

$$
qSC_{D0}+\frac{KW^2}{qS}+\frac{KW^2}{qS}\left(\frac{V^2}{gR_{min}}\right)^2=T_{max}.
$$

The first two terms are the drag in level flight at the same speed,

$$
D_L=qSC_{D0}+\frac{KW^2}{qS},
$$

so

$$
\frac{KW^2}{qS}\left(\frac{V^2}{gR_{min}}\right)^2=T_{max}-D_L.
$$

Solve for $R_{min}$:

$$
R_{min}^2=\frac{KW^2}{qS}\,\frac{V^4}{g^2\,(T_{max}-D_L)}
$$

and with $qS=\tfrac12\rho V^2S$,

$$
R_{min}^2=\frac{2KW^2}{\rho V^2S}\,\frac{V^4}{g^2(T_{max}-D_L)}=\frac{2KW^2V^2}{\rho Sg^2}\,\frac{1}{T_{max}-D_L},
$$

$$
\boxed{\,R_{min}=\left(\frac{2KW^2V^2}{\rho Sg^2}\right)^{1/2}\frac{1}{\sqrt{T_{max}-D_L}}\,}\qquad\text{(thrust limit)}.
$$

Only the **excess thrust** $T_{max}-D_L$ over level flight at the same speed matters, because the parabolic polar splits the drag cleanly: the zero-lift drag $qSC_{D0}$ is unchanged by the turn and only the induced part grows. The same balance gives the sustainable load factor directly. Since $(V^2/gR)^2=n^2-1$,

$$
\frac{KW^2}{qS}\left(n^2-1\right)=T_{max}-D_L\quad\Rightarrow\quad n^2=1+\frac{(T_{max}-D_L)\,qS}{KW^2}.
$$

This is the form behind Revision Q31 ([[SESA1015 T06 - Turning Flight Solutions#Question 31]]).

The shape of the thrust-limited curve follows from the shape of the excess thrust (Notes p. 47). $T_{max}-D_L$ is zero at the two level-flight speed limits and largest near the minimum-drag speed $V_{md}$; $1/\sqrt{T_{max}-D_L}$ is therefore U-shaped and infinite at both ends, and so is $R_{min}(V)$ after the factor $V$ in front is included. The domain of sustained turns lies above this U.

### Where the thrust-limited radius is smallest

The speed for the smallest thrust-limited radius can be found in closed form. Write the level-flight drag as $D_L=AV^2+B/V^2$ with $A=\tfrac12\rho SC_{D0}$ and $B=2KW^2/(\rho S)$, so that $2KW^2V^2/(\rho Sg^2)=BV^2/g^2$, and put $u=V^2$:

$$
R_{min}^2=\frac{B}{g^2}\,\frac{u}{T-Au-B/u}=\frac{B}{g^2}\,\frac{u^2}{Tu-Au^2-B}.
$$

Minimise $f(u)=u^2/(Tu-Au^2-B)$ by the quotient rule:

$$
f'(u)=\frac{2u\,(Tu-Au^2-B)-u^2\,(T-2Au)}{(Tu-Au^2-B)^2}=0
$$

$$
2Tu^2-2Au^3-2Bu-Tu^2+2Au^3=0
$$

$$
Tu^2-2Bu=0\quad\Rightarrow\quad u=\frac{2B}{T}.
$$

So the thrust-limited radius is smallest at

$$
V_{R}^2=\frac{2B}{T_{max}}=\frac{4KW^2}{\rho ST_{max}}.
$$

At this speed $Tu-Au^2-B=B\,(1-4AB/T_{max}^2)$, and $4AB=4KC_{D0}W^2=D_{min}^2$, where $D_{min}=2W\sqrt{KC_{D0}}$ is the minimum drag of [[SESA1015 M05 - Minimum Drag, Power and Performance Curves]]. Hence

$$
R_{min}^2=\frac{B}{g^2}\,\frac{u^2}{B\,(1-D_{min}^2/T_{max}^2)}\quad\Rightarrow\quad R_{min}=\frac{V_R^2}{g\sqrt{1-(D_{min}/T_{max})^2}},
$$

and comparing with $R=V^2/(g\sqrt{n^2-1})$, the load factor there is $n=\sqrt{2-(D_{min}/T_{max})^2}$, never more than $\sqrt2$ (a bank of at most 45°). The best thrust-limited turn is a gentle, slow one. For many aircraft $V_R$ lies below the stall speed, and then the real sustained minimum radius is where the thrust limit crosses the stall limit, the second case of Notes p. 48: stall-limited below that speed, thrust-limited above it.

Two more results follow from the same expression for $n^2$. The sustained load factor $n^2-1=(Tu-Au^2-B)/B$ is greatest where $T-2Au=0$, at $V^2=T_{max}/(\rho SC_{D0})$, and there $n^2-1=T_{max}^2/(4AB)-1$, so

$$
n_{sus,max}=\frac{T_{max}}{D_{min}}=\frac{T_{max}}{W}\left(\frac{L}{D}\right)_{max}.
$$

And the sustained turn rate satisfies $\omega^2=g^2(n^2-1)/V^2=g^2(T_{max}-D_L)/B$, which is largest where $D_L$ is least, at the minimum-drag speed $V_{md}$ (if the stall limit allows it).

![[mof_m10_turn_radius_limits.png|950]]

The aircraft is that of Slides v2 p. 176. At 120.3 m/s the stall and thrust limits cross and give the smallest sustainable radius, 304 m; the corner speed of 132.3 m/s gives an instantaneous 302 m but needs 26.9 kN of thrust against 22.25 kN available, so the aircraft decelerates. Above about 151 m/s the engine can hold $n=6$ and the structural limit binds. The thrust-limit curve dips to 107 m at 32.3 m/s, but that is below the stall speed and is never reached.

![[mof_m10_turn_rate.png|950]]

## 5. The V–n diagram

The V–n diagram plots the allowed load factor against airspeed for one weight and altitude, usually the gross take-off weight with full payload and fuel (Slides v2 pp. 178–179). Its boundaries are the turning limits of Section 3 written for $n$ instead of $R$:

- the aerodynamic (stall) limit, $n=\pm\tfrac12\rho V^2SC_{L,max}/W$, a parabola through the origin; the positive branch rearranged is $V=\sqrt{2nW/(\rho SC_{L,max})}$, the stall speed at load factor $n$;
- the structural limits $n_{max}$ and $n_{min}$, horizontal lines set by the certification authority (roughly $-1.5\le n\le3.8$ for a transport aircraft and $-10\le n\le12$ for a military aircraft, Slides v2 p. 178);
- a maximum speed on the right, $V_{NE}$ or a design dive speed in practice; in the worked example it is the level-flight maximum speed from $T=D$,

$$
V_{max}^2=\frac{T_{av}+\sqrt{T_{av}^2-4AB}}{2A},\qquad A=\tfrac12\rho SC_{D0},\quad B=\frac{2KW^2}{\rho S}.
$$

The positive stall parabola meets $n_{max}$ at $V_A=\sqrt{2n_{max}W/(\rho SC_{L,max})}=V_S\sqrt{n_{max}}$, the corner speed of Section 3. Below $V_A$ the pilot cannot overstress the aircraft with a full pull, because the wing stalls first; above it the structure is the limit. For the full diagram, see [[V-n Diagram]].

![[mof_m10_vn_diagram.png|950]]

## Worked examples

### A 60 degree bank turn

At 60° bank, $\cos60°=0.5$ and $\tan60°=1.732$, so $n=2$ and the stall speed is $\sqrt2=1.414$ times its level value. An aircraft with $V_S=40$ m/s turning at 60 m/s has $V_{S_T}=56.6$ m/s, only 6 % below the flight speed. The radius is $60^2/(9.81\times1.732)=211.9$ m and the rate $9.81\times1.732/60=0.283$ rad/s (16.2°/s).

### Corner speed and turn rate (Slides v2 p. 176)

Data: $W/S=2680$ N/m², $S=15.5$ m², $C_{L,max}=1.5$, $n_{max}=6$, $C_{D0}=0.018$, $K=0.064$, $T_{max}=22\,250$ N, sea level. Find the maximum turn rate, the minimum radius, the speeds at which they occur, and whether the turn can be sustained.

Both extremes are at the corner, with $C_L=C_{L,max}$ and $n=n_{max}$. The weight is $W=2680\times15.5=41\,540$ N. The speed is

$$
V_{S_T}=\sqrt{\frac{2nW}{\rho SC_{L,max}}}=\sqrt{\frac{2\times6\times2680}{1.225\times1.5}}=132.3\ \text{m/s},
$$

which equals $V_S\sqrt6$ with $V_S=54.01$ m/s. Then

$$
R=\frac{2}{\rho gC_{L,max}}\left(\frac{W}{S}\right)\frac{n}{\sqrt{n^2-1}}=\frac{2\times2680}{1.225\times9.81\times1.5}\times\frac{6}{\sqrt{35}}=301.6\ \text{m},
$$

$$
\omega=g\sqrt{\frac{\rho C_{L,max}}{2}}\sqrt{\frac{S}{W}}\sqrt{\frac{n^2-1}{n}}=9.81\times0.9585\times0.01932\times2.415=0.4387\ \text{rad/s}=25.1°/\text{s}.
$$

The bank angle is $\cos^{-1}(1/6)=80.4°$. The drag at this point is

$$
D=\left(C_{D0}+KC_{L,max}^2\right)\tfrac12\rho V^2S=(0.018+0.064\times2.25)\times\tfrac12\times1.225\times132.3^2\times15.5=0.162\times166\,160=26\,918\ \text{N}.
$$

This exceeds $T_{max}=22\,250$ N, so the turn cannot be held: the aircraft slows as soon as it enters it, and the radius and rate change. The slides' radius of 301.87 m is the same calculation with intermediate rounding.

> [!check] Turn rate two ways
> $\omega=V/R=132.30/301.57=0.4387$ rad/s, the same as the formula in $C_L$, $S/W$ and $n$.

### Speed for minimum radius at the highest load factor (Slides v2 p. 177)

Same aircraft. On the load-factor limit $R=V^2/(g\sqrt{35})$, and on the stall limit $R=V^2/\big(g\sqrt{(V/V_S)^4-1}\big)$. Equating the two,

$$
\sqrt{(V/V_S)^4-1}=\sqrt{35}\quad\Rightarrow\quad\left(\frac{V}{V_S}\right)^4=36\quad\Rightarrow\quad V=\sqrt6\,V_S=132.3\ \text{m/s},
$$

with $V_S=\sqrt{2W/(\rho SC_{L,max})}=54.0$ m/s, and $R_{min}=132.3^2/(9.81\sqrt{35})=301.6$ m.

### Best sustained turn for the same aircraft

Here $A=\tfrac12\rho SC_{D0}=0.1709$ kg/m and $B=2KW^2/(\rho S)=1.163\times10^7$ N m²/s². The thrust-limited optimum of Section 4 would be at $V_R=\sqrt{4KW^2/(\rho ST_{max})}=32.3$ m/s, below $V_S=54.0$ m/s, so it cannot be flown. The sustained minimum radius is where the stall and thrust limits cross:

$$
\left(\frac{V}{V_S}\right)^4=1+\frac{(T_{max}-D_L)\,V^2}{B}.
$$

Solving numerically gives $V=120.3$ m/s, where $n=(120.3/54.01)^2=4.96$, $\phi=78.4°$, $R=303.6$ m and $\omega=0.396$ rad/s (22.7°/s). This is also the best sustained turn rate, since below this speed the stall limit is lower and above it the thrust limit falls. The thrust-only maximum rate would be at $V_{md}=(B/A)^{1/4}=90.8$ m/s, but there the stall limit allows only $n=2.83$. With $T_{max}/D_{min}=22\,250/2820=7.89$, the engine could sustain $n=6$ at high speed, between about 151 and 328 m/s by the incompressible model.

### V–n diagram for a military aircraft (Slides v2 p. 179)

Data: $W/S=1500$ N/m², $S=8$ m², $C_{D0}=0.015$, $K=0.06$, $C_{L,max}=2$, $n_{max}=12$, $n_{min}=-10$, $T_{av}=15\,000$ N, sea level. Then $W=12\,000$ N and

$$
V_{stall}=\sqrt{\frac{2W}{\rho SC_{L,max}}}=\sqrt{\frac{24\,000}{1.225\times8\times2}}=35.0\ \text{m/s}.
$$

The corners are $V_A=35.0\sqrt{12}=121.2$ m/s on the positive side and $35.0\sqrt{10}=110.7$ m/s on the negative side. With $A=\tfrac12\times1.225\times8\times0.015=0.0735$ kg/m and $B=2\times0.06\times12\,000^2/(1.225\times8)=1.763\times10^6$ N m²/s²,

$$
V_{max}^2=\frac{15\,000+\sqrt{15\,000^2-4\times0.0735\times1.763\times10^6}}{2\times0.0735}=2.040\times10^5\ \text{m}^2/\text{s}^2,\qquad V_{max}=451.6\ \text{m/s}.
$$

That is Mach 1.33 at sea level, far outside the incompressible parabolic polar used to compute it, so it marks the right-hand edge of the diagram drawn from this model rather than a real top speed (wave drag, [[SESA1015 M07 - Propeller Aircraft Range and Endurance|M07]], would cut it).

## Links

- Parent: [[SESA1015 Intro to Aero & Astro Hub]] · Solutions: [[SESA1015 T06 - Turning Flight Solutions]]
- Previous: [[SESA1015 M09 - Take-off and Landing Performance]] · Next: [[SESA1015 M11 - Longitudinal Trim and Static Stability]]
- Builds on: [[SESA1015 M04 - Steady Level Flight and Stall]] (stall speed, $L=W$) · [[SESA1015 M05 - Minimum Drag, Power and Performance Curves]] (drag curve, $D_{min}$, $V_{md}$, level-flight speed range)
- Used in: [[SESA1015 M12 - Aircraft Constraint Analysis]] (the constant-speed turn constraint at load factor $n$)
- Concepts: [[Load Factor and Turn Performance]] · [[V-n Diagram]] · [[Wing Loading]] · [[Parabolic Drag Polar]] · [[Minimum Drag and Minimum Power]]
- Later in the degree: the induced-drag cost of the extra lift in [[SESA2022 T5 - Finite Wing Theory]]; the steady pull-up and manoeuvre margin in [[SESA2022 T6 - Aircraft Aerodynamics and Static Stability]] and [[Manoeuvre Point and Manoeuvre Margin]]; non-steady manoeuvres from the full equations of motion in [[SESA2027 A1 - Dynamic Systems and Aircraft Equations of Motion]].

## Sources

- Mechanics of Flight Course Notes (Prof. A. Keane, October 2020), §7.4 Turning Performance, pp. 42–48: force balance and radius (pp. 42–43), stalling speed in the turn and the load-factor figure (pp. 43–44), §7.4.1 minimum radius from the load-factor and stall limits and the domain-of-flight diagram (pp. 44–46), §7.4.2 thrust-limited radius and the stall/thrust diagrams (pp. 46–48).
- Mechanics of Flight Lecture Slides version 2: turning flight and co-ordination (pp. 169–170), load factor (p. 171), radius and rate of turn (pp. 172–173), bank angle and turn speed (p. 174), thrust-limited turn (p. 175), worked examples (pp. 176–177), V–n diagram and example (pp. 178–179), take-off, landing and turns rubric (p. 181).
- Revision workbook Q6, Q25, Q26, Q31: [[SESA1015 T06 - Turning Flight Solutions]].

## Self-study tasks

### Core

- [ ] Revision Q6: thrust required in a 6 g co-ordinated turn at 381 kn. → [[SESA1015 T06 - Turning Flight Solutions#Question 6]]
- [ ] Revision Q25 and Q26: stall-limited minimum radius of turn. → [[SESA1015 T06 - Turning Flight Solutions#Question 25]] · [[SESA1015 T06 - Turning Flight Solutions#Question 26]]
- [ ] Revision Q31: thrust-limited minimum radius from a given excess thrust. → [[SESA1015 T06 - Turning Flight Solutions#Question 31]]
- [ ] Slides v2 p. 176 example: maximum turn rate, minimum radius and whether the turn can be sustained. → [[#Corner speed and turn rate (Slides v2 p. 176)]]
- [ ] Slides v2 p. 177 example: speed for minimum radius at the highest load factor, deriving the stall-limit radius. → [[#Speed for minimum radius at the highest load factor (Slides v2 p. 177)]] · [[#Stall (maximum-lift) limit]]

### Further practice

- [ ] Slides v2 p. 179: draw the V–n diagram for the military aircraft and find $V_{stall}$, $V_A$ and $V_{max}$. → [[#V–n diagram for a military aircraft (Slides v2 p. 179)]]
- [ ] Derive the thrust-limited radius from $D=T_{max}$ without notes, then show that it is smallest at $V^2=4KW^2/(\rho ST_{max})$ (suggested, not lecturer-set). → [[#Derivation]] · [[#Where the thrust-limited radius is smallest]]
- [ ] Find the best sustained turn for the Slides p. 176 aircraft by intersecting the stall and thrust limits (suggested, not lecturer-set). → [[#Best sustained turn for the same aircraft]]
- [ ] Revision Q35: the turn constraint in a constraint diagram. → [[SESA1015 T08 - Constraint Analysis Solutions#Question 35]]

## Transcript and slide slips

> [!warning] Slide slip (Slides v2 p. 176)
> Where: [[#Corner speed and turn rate (Slides v2 p. 176)]] and [[#Derivation]].
>
> The last part of the example evaluates the thrust-limited radius "at the steady level flight speed (i.e. $n=1$)", $V=\sqrt{2W/(\rho SC_L)}=54.0$ m/s with $C_L=1.5$, and gives $D_L=6644.65$ N and $R_{min}=150.47$ m. Two things are wrong. At $C_L=C_{L,max}$ the level-flight drag is $D_L=W(C_{D0}+KC_{L,max}^2)/C_{L,max}=41\,540\times0.162/1.5=4486$ N (which would give 140.9 m). More importantly, 54.0 m/s is the stall speed: the stall limit allows only $n=1$ there, so no turn at all is possible and neither radius is achievable. A thrust-limited radius is only meaningful where it lies above the stall-limited one; for this aircraft that first happens at 120.3 m/s ([[#Best sustained turn for the same aircraft]]).
