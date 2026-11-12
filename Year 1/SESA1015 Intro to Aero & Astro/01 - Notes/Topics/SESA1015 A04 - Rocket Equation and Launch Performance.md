---
title: "SESA1015 A04 - Rocket Equation and Launch Performance"
module: "SESA1015 Intro to Aero & Astro"
type: topic
stream: "Astronautics"
order: 16
tags:
  - sesa1015
  - astronautics
  - rocket-equation
  - launch-performance
aliases: ["SESA1015 Astronautics 4", "Rocket Performance", "Rocket Equation (SESA1015)"]
date: 2026-09-27
status: lectured
coverage: "Astronautics Part 3 (Launch Vehicles) pp. 3–23: conservation of momentum and exhaust velocity, derivation of the rocket equation (3.1), the rocket equation with gravity and drag (3.2)–(3.3), the vector form, gravity–drag trade and ascent profile, the Delta-V budget to LEO, single stage to orbit."
parent: ["[[SESA1015 Intro to Aero & Astro Hub]]"]
prerequisites: ["[[SESA1015 A03 - Launch Environment]]"]
next_topics: ["[[SESA1015 A05 - Staging and Payload Fraction]]"]
key_concepts: ["[[Tsiolkovsky Rocket Equation]]", "[[Gravity and Drag Losses]]", "[[Rocket Mass Fractions]]", "[[Rocket Performance Parameters]]"]
tutorial_sheets: []
sources: ["02 - Sources/Astronautics/Astronautics - Part 3 - Launch Vehicles.pdf (pp. 3–23)", "02 - Sources/Astronautics/Astronautics - Part 1 - Introduction.pdf (p. 5, LEO)"]
---

# SESA1015 A04 - Rocket Equation and Launch Performance

> [!abstract] Summary
> A rocket gains speed by throwing mass backwards: the momentum carried away by the exhaust equals the momentum gained by the vehicle. Because the vehicle gets lighter as it burns, the velocity change is logarithmic in the mass ratio, $\Delta V=V_{ex}\ln(M_0/M_b)$, the rocket equation (3.1). A launch vehicle also has to pay a gravity loss and a drag loss, $\Delta V=\Delta V_{ideal}-\Delta V_g-\Delta V_D$ (3.3), which raises the requirement for low Earth orbit from about 7.8 km/s to about 8.75 km/s. With realistic tank structure, a single stage then needs an exhaust velocity beyond common propellants, which is the case for staging.

> [!summary]- Exam use: quick path
> - **Use it when:** a question gives an exhaust velocity (or $I_{sp}$), masses before and after a burn, or a required $\Delta V$, and asks for the velocity change, the propellant needed, or whether a single stage can reach orbit.
> - **Assumptions:** constant $V_{ex}$ over the burn; $M_b$ is everything still attached at burnout (payload and structure); natural logarithm; thrust along the velocity for the loss equation; in course notation $M_f$ is **fuel** mass, not final mass.
> - **Method:** 1. Write the required $\Delta V$ (about 7.8 km/s for LEO) and add the losses ($\Delta V_g\approx0.75$–$1.5$ km/s, $\Delta V_D\approx0.2$–$0.3$ km/s). 2. Divide by $V_{ex}$ to get $\ln(M_0/M_b)$. 3. Exponentiate for the mass ratio. 4. Split $M_0$ and $M_b$ into payload, structure and fuel, or use $(1+s)/(p+s)$. 5. Check the result is physical ($p>0$, propellant positive).
> - **Common mistakes:** using $\log_{10}$; leaving the structure out of $M_b$ (or reading $M_f$ as final mass).
> - **Practise:** [[#Propellant to put 1000 kg into LEO]] · [[#9. Single stage to orbit]]

A rocket is a body that carries its own reaction mass. Nothing outside it is pushed against: the engine throws exhaust backwards, and since the total momentum of vehicle plus exhaust cannot change without an external force, the vehicle moves forwards. That is why a rocket works in vacuum, and why its performance is set by two things only, the speed at which the exhaust leaves relative to the vehicle and how much of the vehicle is exhaust-to-be.

The second quantity enters in a less obvious way than the first. Early in the burn the engine is accelerating a heavy vehicle full of propellant; late in the burn the same exhaust flow accelerates a nearly empty one. Each kilogram of propellant therefore buys more speed than the one before it, and summing these contributions gives a logarithm. The logarithm is the source of every difficulty in launch: doubling the mass ratio adds only $V_{ex}\ln2\approx0.69V_{ex}$ to the velocity change.

A launch vehicle also has to climb out of a gravity field through an atmosphere. Thrust that holds the vehicle up against gravity, or pushes it through air, is thrust not spent on speed, so the vehicle must carry enough propellant for the orbital speed plus these losses. The losses pull in opposite directions (climbing steeply saves drag and costs gravity loss, flattening the trajectory does the opposite), so the ascent is a trade between them.

---

## 1. Conservation of momentum with one ejected mass

The simplest model (Part 3, pp. 3–5) is a vehicle of mass $M$ carrying a lump of mass $m$, moving at speed $V$ along the positive axis. The lump is thrown out once. Afterwards the vehicle moves at $V+V_1$ and the lump at $V_2$, both measured by a fixed observer.

![[astro_a04_momentum_states.png|900]]

With no external force the momentum before (state A) equals the momentum after (state B):

$$
(M+m)V=M(V+V_1)+mV_2 .
$$

Expanding both sides,

$$
MV+mV=MV+MV_1+mV_2 .
$$

The $MV$ terms cancel:

$$
mV=MV_1+mV_2 .
$$

Solving for the vehicle's velocity gain,

$$
MV_1=mV-mV_2,
$$

$$
V_1=\frac{m}{M}\,(V-V_2).
$$

Here $V_2$ is the absolute velocity of the ejected mass, negative if it moves backwards. The bracket $V-V_2$ is the speed at which the mass leaves, measured relative to the vehicle, and is called the **exhaust velocity** $V_{ex}$:

$$
V_{ex}=V-V_2,\qquad V_1=\frac{m}{M}V_{ex}.
$$

Two performance conclusions follow (p. 4). The velocity gain grows with the ratio of ejected mass to remaining mass, and with the speed at which the mass is thrown backwards. Strictly, $V-V_2$ is the relative speed measured against the vehicle's velocity before ejection; against its velocity afterwards it is $V+V_1-V_2$. The two differ by $V_1$, which is why this one-shot model is only a first approximation.

The model fails for a real rocket because the mass leaves continuously (p. 5). The first kilogram of exhaust pushes against the full mass $M+m$, and the last against almost none of it, so treating all of $m$ as pushing against the final mass $M$ overstates the gain. Ejecting the mass in infinitesimal pieces removes the error (Section 2).

## 2. The rocket equation for a rocket in space

### Setting up the momentum balance

At time $t=0$ (Part 3, p. 7) the rocket has mass $M+\Delta m$ and speed $V$. In the interval $\Delta t$ it ejects $\Delta m$, which leaves at absolute velocity $V_2$, and the remaining mass $M$ moves at $V+\Delta V$. Newton's second law in momentum form is

$$
F_{ext}=\lim_{\Delta t\to0}\frac{\text{momentum at } t+\Delta t-\text{momentum at } t}{\Delta t},
$$

which here reads

$$
F_{ext}=\lim_{\Delta t\to0}\frac{\big[M(V+\Delta V)+\Delta m\,V_2\big]-(M+\Delta m)V}{\Delta t}.
$$

### Taking the limit

For a rocket in space there is no external force, so $F_{ext}=0$. As $\Delta t\to0$ the small changes become differentials ($\Delta V\to dV$, $\Delta m\to dm$, $\Delta t\to dt$):

$$
0=\frac{M(V+dV)+dm\,V_2-(M+dm)V}{dt}.
$$

Expand the brackets in the numerator:

$$
0=\frac{MV+M\,dV+dm\,V_2-MV-dm\,V}{dt}.
$$

Cancel $MV$:

$$
0=\frac{M\,dV+dm\,V_2-dm\,V}{dt}.
$$

Split into separate rates:

$$
0=M\frac{dV}{dt}+\frac{dm}{dt}V_2-\frac{dm}{dt}V .
$$

No product of two small quantities appears, because $M$ is defined as the mass that remains after the interval, so nothing has to be neglected. Rearrange (p. 9):

$$
M\frac{dV}{dt}=\frac{dm}{dt}\,(V-V_2).
$$

With $V-V_2=V_{ex}$, the exhaust velocity relative to the vehicle as in Section 1 (now exact in the limit, since $\Delta V\to0$):

$$
\frac{dV}{dt}=V_{ex}\,\frac{1}{M}\frac{dm}{dt}.
$$

This is the differential form of $V_1=(m/M)V_{ex}$: each small piece of exhaust $dm$ gives the vehicle $dV=V_{ex}\,dm/M$ against the mass $M$ present at that instant.

### Relating ejected mass to vehicle mass

$dm/dt$ is the mass of propellant ejected per unit time, the mass flow rate. Every kilogram ejected is a kilogram the rocket loses, so the rocket's own mass $M$ changes at the same rate with the opposite sign (p. 10):

$$
\frac{dM}{dt}=-\frac{dm}{dt}.
$$

Substituting,

$$
\frac{dV}{dt}=-V_{ex}\,\frac{1}{M}\frac{dM}{dt}.
$$

### Integrating

Multiply through by $dt$:

$$
dV=-V_{ex}\,\frac{dM}{M}.
$$

Integrate from the start of the burn (speed $u$, mass $M_0$) to burnout (speed $v$, mass $M_b$), with $V_{ex}$ constant:

$$
\int_u^v dV=-V_{ex}\int_{M_0}^{M_b}\frac{dM}{M}.
$$

$$
v-u=-V_{ex}\big[\ln M\big]_{M_0}^{M_b}.
$$

$$
v-u=-V_{ex}\left(\ln M_b-\ln M_0\right).
$$

$$
v-u=V_{ex}\ln\frac{M_0}{M_b}.
$$

Writing $\Delta V=v-u$ gives the **rocket equation** (Tsiolkovsky, 1903; Part 3, p. 11, equation 3.1):

$$
\boxed{\Delta V=V_{ex}\ln\frac{M_0}{M_b}}
$$

where $M_0$ is the initial mass and $M_b$ the **burnout mass**, everything still attached when the propellant is exhausted. The ratio $M_0/M_b$ is the **mass ratio**.

![[astro_a04_mass_ratio.png|800]]

The figure compares the rocket equation with the one-shot estimate of Section 1. Putting $m=M_0-M_b$ and $M=M_b$ in $V_1=(m/M)V_{ex}$ gives $V_1/V_{ex}=M_0/M_b-1$, which is the first term of the series $\ln(1+x)=x-x^2/2+\dots$ with $x=m/M$. The two agree only when a small fraction of the vehicle is burnt. For a realistic mass ratio the one-shot estimate is far too optimistic.

> [!tip] Reading the logarithm
> $\Delta V/V_{ex}=1$ needs $M_0/M_b=e=2.72$, so 63 % of the vehicle is propellant. $\Delta V/V_{ex}=2$ needs $e^2=7.39$ (86 % propellant) and $\Delta V/V_{ex}=3$ needs $e^3=20.1$ (95 %). Each further multiple of $V_{ex}$ multiplies the mass ratio by 2.72 again.

## 3. Thrust

Multiplying the equation of motion of Section 2 by $M$ gives

$$
M\frac{dV}{dt}=V_{ex}\frac{dm}{dt}=\dot m\,V_{ex},
$$

so the force the exhaust exerts on the vehicle, the **thrust**, is the propellant mass flow rate times the exhaust velocity, $T=\dot mV_{ex}$. For a fixed propellant flow, a higher exhaust velocity gives both more thrust and more $\Delta V$ per kilogram of propellant. The engine-side description of $V_{ex}$ (pressure thrust at the nozzle exit and specific impulse $I_{sp}=V_{ex}/g_0$) is not part of this course; it is in [[SESA2023 W10 - Rocket Performance, Staging and Power Cycles]] and [[Rocket Performance Parameters]].

## 4. The rocket equation for a launch vehicle

### Forces on the ascending vehicle

Inside the atmosphere and the gravity field there are external forces (Part 3, pp. 13–14). The vehicle flies at speed $V$ along a path inclined at the **flight-path angle** $\gamma$ above the horizontal. Axes are taken with $\mathbf i$ along the velocity and $\mathbf j$ normal to it. The external forces are the weight $Mg$, acting vertically down, the drag $D$, acting along $-\mathbf i$, and (in the vector form of Section 6) a lift $L$ along $\mathbf j$. Thrust is assumed to act along the velocity.

![[astro_a04_ascent_forces.png|800]]

Resolving the weight, its component along $\mathbf i$ is $-Mg\sin\gamma$ and along $\mathbf j$ is $-Mg\cos\gamma$. The drag is

$$
D=\tfrac12\rho V^2SC_D,
$$

with $\rho$ the air density, $S$ a reference area (normally the body cross-section) and $C_D$ the drag coefficient, the same definition as for aircraft in [[Dynamic Pressure and Aerodynamic Coefficients]].

### Equation of motion along the path

The momentum balance of Section 2 is unchanged except that $F_{ext}$ along $\mathbf i$ is no longer zero (p. 14):

$$
\frac{M(V+dV)+dm\,V_2-(M+dm)V}{dt}=-Mg\sin\gamma-D .
$$

The left side simplifies exactly as before (p. 15):

$$
M\frac{dV}{dt}+\frac{dm}{dt}(V_2-V)=-Mg\sin\gamma-D .
$$

With $V_2-V=-V_{ex}$,

$$
M\frac{dV}{dt}-V_{ex}\frac{dm}{dt}=-Mg\sin\gamma-D .
$$

With $dm/dt=-dM/dt$,

$$
M\frac{dV}{dt}+V_{ex}\frac{dM}{dt}=-Mg\sin\gamma-D .
$$

Move the thrust term to the right:

$$
M\frac{dV}{dt}=-V_{ex}\frac{dM}{dt}-Mg\sin\gamma-D .
$$

Divide by $M$:

$$
\frac{dV}{dt}=-V_{ex}\frac{1}{M}\frac{dM}{dt}-g\sin\gamma-\frac{D}{M}.
$$

This is the rocket equation of Section 2 with two extra decelerations, the component of gravity along the path and the drag per unit mass.

## 5. Gravity loss and drag loss

Multiply by $dt$ and integrate over the burn, from $t=0$ (mass $M_0$, speed $u$) to burnout at $t$ (mass $M_b$, speed $v$), Part 3, p. 16:

$$
\int_u^v dV=-V_{ex}\int_{M_0}^{M_b}\frac{dM}{M}-\int_0^t g\sin\gamma\,dt-\int_0^t\frac{D}{M}\,dt .
$$

The first integral on the right is the one done in Section 2, so

$$
\Delta V=\underbrace{V_{ex}\ln\frac{M_0}{M_b}}_{\Delta V_{ideal}}-\underbrace{\int_0^t g\sin\gamma\,dt}_{\text{gravity}}-\underbrace{\int_0^t\frac{D}{M}\,dt}_{\text{drag}}\qquad(3.2)
$$

which is written (equation 3.3)

$$
\boxed{\Delta V=\Delta V_{ideal}-\Delta V_g-\Delta V_D}
$$

with $\Delta V_g$ the **gravity loss** and $\Delta V_D$ the **drag loss** ([[Gravity and Drag Losses]]). $\Delta V_{ideal}$ is what the propellant could deliver in free space; $\Delta V$ is the speed actually gained.

The gravity loss is largest when the vehicle climbs steeply ($\sin\gamma\approx1$) for a long time. For a purely vertical burn with constant $g$ it is $g$ times the burn time. The burn time follows from the mass flow: with thrust $T=\dot m V_{ex}$ (Section 3) and constant $T$,

$$
t_b=\frac{M_0-M_b}{\dot m}=\frac{(M_0-M_b)V_{ex}}{T}.
$$

Then

$$
\Delta V_g=g\,t_b=\frac{gV_{ex}(M_0-M_b)}{T}.
$$

Dividing numerator and denominator by $M_0$,

$$
\Delta V_g=V_{ex}\,\frac{1-M_b/M_0}{T/(M_0g)} ,
$$

so a higher lift-off thrust-to-weight ratio $T/(M_0g)$ burns the propellant faster and cuts the gravity loss in proportion. A thrust-to-weight ratio below 1 means the vehicle cannot leave the pad at all.

The drag loss grows with $\rho V^2$, so it is largest if the vehicle builds speed while still low in dense air. A faster burn reaches high speed lower down, so it reduces gravity loss and increases drag loss.

![[astro_a04_loss_trade.png|850]]

The figure integrates the equation of Section 4 for a vertical climb of a small 30 t vehicle with the stated (assumed) data. Gravity loss falls as $1/(T/W_0)$, as derived above; drag loss rises; their sum has a shallow minimum. Real launchers lift off at $T/W_0\approx1.2$–$1.5$, well left of that minimum, because engine mass grows with thrust and the aerodynamic loads around maximum dynamic pressure limit how fast the vehicle may fly low down ([[SESA1015 A03 - Launch Environment]]).

## 6. Vector form and the turn of the trajectory

The same analysis can be done in vector form, handling the $\mathbf i$ and $\mathbf j$ directions together and including lift (Part 3, pp. 17–18). Newton's second law for a system with momentum inflow and outflow is

$$
\frac{d}{dt}(M\mathbf V)=\mathbf F_{ext}+\{\text{rate of momentum inflow}\}-\{\text{rate of momentum outflow}\}.
$$

For a rocket nothing flows in. The exhaust leaves at mass flow rate $\sigma$ with absolute velocity $V-V_{ex}$ along $\mathbf i$, so the momentum outflow rate is $\sigma(V-V_{ex})\mathbf i$. The external forces are $-D\mathbf i$, the weight $-Mg\sin\gamma\,\mathbf i-Mg\cos\gamma\,\mathbf j$ and the lift $L\mathbf j$. With $\mathbf V=V\mathbf i$:

$$
\dot M\mathbf V+M\dot{\mathbf V}=-D\mathbf i-Mg\sin\gamma\,\mathbf i-Mg\cos\gamma\,\mathbf j+L\mathbf j-\sigma(V-V_{ex})\mathbf i .
$$

The mass falls at the exhaust flow rate, $\dot M=-\sigma$. The unit vector $\mathbf i$ turns with the path: if $\gamma$ increases at rate $\dot\gamma$, then $\dot{\mathbf i}=\dot\gamma\,\mathbf j$, so

$$
\dot{\mathbf V}=\frac{d}{dt}(V\mathbf i)=\dot V\mathbf i+V\dot\gamma\,\mathbf j .
$$

Substitute both:

$$
-\sigma V\mathbf i+M\dot V\mathbf i+MV\dot\gamma\,\mathbf j=-D\mathbf i-Mg\sin\gamma\,\mathbf i-Mg\cos\gamma\,\mathbf j+L\mathbf j-\sigma V\mathbf i+\sigma V_{ex}\mathbf i .
$$

The $\mathbf i$ components give (the $-\sigma V$ terms cancel)

$$
M\dot V=\sigma V_{ex}-D-Mg\sin\gamma ,
$$

which is the equation of Section 4, since $\sigma=-dM/dt$. The $\mathbf j$ components give a new equation for the turning of the path:

$$
MV\dot\gamma=L-Mg\cos\gamma .
$$

With no lift (a slender rocket at zero incidence), $\dot\gamma=-g\cos\gamma/V$: gravity turns the velocity vector down towards the horizontal, quickly while the vehicle is slow and slowly once it is fast. Launchers use this **gravity turn**: after a short vertical rise the vehicle is tipped slightly from the vertical and gravity bends the path over without the vehicle needing to fly at incidence, which would add lift-induced loads and drag.

## 7. Ascent optimisation and a real ascent profile

A realistic launch is a trade between the two losses (Part 3, p. 19). A trajectory that climbs steeply out of the atmosphere and turns over late keeps the drag loss small but spends a long time fighting gravity, so its gravity loss is large. A trajectory that turns over early and gains speed near the ground has a small gravity loss but a large drag loss. Trajectory optimisation chooses the pitch programme between these; typical values are

$$
\Delta V_g\approx0.75\text{ to }1.5\ \mathrm{km/s},\qquad\Delta V_D\approx0.2\text{ to }0.3\ \mathrm{km/s}.
$$

Gravity loss is the larger of the two, which is why launchers are not throttled down to minimise drag more than the structure requires.

The ascent profile of a classical three-stage expendable launcher, Ariane 44LP (p. 20), shows the result. Speed rises slowly at first, while the vehicle is heavy and climbing near-vertically, then increasingly fast as each stage empties, reaching orbital speed at around 1000 s. Altitude rises to about 200 km within the first few hundred seconds, so the vehicle is out of the dense atmosphere early, and then levels off (even dips) while the upper stage builds horizontal speed. Ground range grows slowly at first and almost linearly once the vehicle is moving fast and horizontally.

## 8. The velocity budget to low Earth orbit

The speed needed for a circular orbit follows from equating gravity to the centripetal force on a body of mass $m$ at radius $r$ from Earth's centre, with $\mu=GM_E=3.986\times10^{14}\ \mathrm{m^3\,s^{-2}}$:

$$
\frac{\mu m}{r^2}=\frac{mV^2}{r},
$$

$$
V=\sqrt{\frac{\mu}{r}} .
$$

At 200 km altitude ($r=6378+200=6578$ km, the bottom of LEO in Part 1, p. 5),

$$
V=\sqrt{\frac{3.986\times10^{14}}{6.578\times10^{6}}}=7784\ \mathrm{m/s}\approx7.8\ \mathrm{km/s},
$$

the $\Delta V$ required for LEO (Part 3, p. 16). The launch site's eastward speed due to Earth's rotation (about 0.4 km/s at mid latitudes, [[SESA1015 A06 - Launch Vehicles, Systems and Interfaces]]) slightly reduces what the vehicle must supply for an eastward launch; the numbers used here ignore it.

Adding the lower ends of the typical losses (p. 21),

$$
V_{ex}\ln\frac{M_0}{M_b}=\Delta V+\Delta V_g+\Delta V_D=7.8+0.75+0.2=8.75\ \mathrm{km/s}.
$$

### Propellant to put 1000 kg into LEO

Take $V_{ex}=3$ km/s and a 1000 kg payload, with (as on p. 21) nothing else at burnout, so $M_b=1000$ kg and $M_0=1000+M_f$ with $M_f$ the fuel mass:

$$
3\ln\frac{1000+M_f}{1000}=8.75 .
$$

$$
\ln\frac{1000+M_f}{1000}=\frac{8.75}{3}=2.917 .
$$

$$
\frac{1000+M_f}{1000}=e^{2.917}=18.48 .
$$

$$
M_f=1000(18.48-1)=17\,480\ \mathrm{kg}\approx17\,500\ \mathrm{kg}.
$$

A 1 t payload needs 17.5 t of propellant, even with tanks and engines of zero mass.

> [!check] Numerical check
> $3\ln(18\,480/1000)=3\times2.9167=8.750$ km/s. With the upper end of the losses ($1.5+0.3$) the requirement is 9.6 km/s and $M_f=1000(e^{3.2}-1)=23\,500$ kg.

## 9. Single stage to orbit

### Mass bookkeeping

Split the lift-off mass into payload $M_p$, structure $M_s$ (tanks, engines, everything that is not payload or propellant) and fuel $M_f$ (Part 3, p. 22; the subscript $f$ means fuel, not final):

$$
M_0=M_p+M_s+M_f,\qquad M_b=M_p+M_s .
$$

Equation (3.3) becomes

$$
\Delta V+\Delta V_g+\Delta V_D=V_{ex}\ln\frac{M_p+M_s+M_f}{M_p+M_s}.
$$

Two ratios describe the vehicle:

$$
p=\frac{M_p}{M_0}\ \text{(payload fraction)},\qquad s=\frac{M_s}{M_f}\ \text{(propellant tankage structural efficiency)} .
$$

A small $s$ means light tanks for the propellant they hold. ([[Rocket Mass Fractions]] relates $s$ and $p$ to other conventions.)

### Deriving the mass ratio in terms of p and s

The mass ratio is

$$
\frac{M_0}{M_b}=\frac{M_0}{M_p+M_s}=\frac{1}{p+M_s/M_0}.
$$

$M_s/M_0$ is needed in terms of $p$ and $s$. Divide $M_0=M_p+M_s+M_f$ by $M_0$:

$$
1=p+\frac{M_s}{M_0}+\frac{M_f}{M_0}.
$$

Since $M_s=sM_f$, $M_f/M_0=(M_s/M_0)/s$:

$$
1=p+\frac{M_s}{M_0}+\frac{1}{s}\frac{M_s}{M_0}.
$$

$$
1-p=\frac{M_s}{M_0}\cdot\frac{s+1}{s}.
$$

$$
\frac{M_s}{M_0}=\frac{s(1-p)}{1+s}.
$$

Substitute back:

$$
\frac{M_0}{M_b}=\frac{1}{p+\dfrac{s(1-p)}{1+s}}=\frac{1+s}{p(1+s)+s(1-p)}=\frac{1+s}{p+ps+s-ps}.
$$

The $ps$ terms cancel, leaving an exact result:

$$
\boxed{\frac{M_0}{M_b}=\frac{1+s}{p+s}},\qquad \Delta V+\Delta V_g+\Delta V_D=V_{ex}\ln\frac{1+s}{p+s}.
$$

The largest possible mass ratio, with no payload at all, is $(1+s)/s$: structure alone limits the vehicle.

### The single stage to orbit limit

The most generous case (p. 23) has $\Delta V=7.8$ km/s, no losses, a good structure $s=0.1$, and no payload $p=0$. Then

$$
7.8=V_{ex}\ln\frac{1+0.1}{0+0.1}=V_{ex}\ln11,
$$

$$
V_{ex}=\frac{7.8}{\ln 11}=\frac{7.8}{2.398}=3.25\ \mathrm{km/s}.
$$

Even with no payload and no losses a single stage needs $V_{ex}=3.25$ km/s, at the top of what kerosene and liquid oxygen deliver, so single stage to orbit is achievable only with high-energy propellants. With the 8.75 km/s requirement including losses, $V_{ex}=8.75/\ln11=3.65$ km/s, which only hydrogen and oxygen reach.

![[astro_a04_ssto_requirement.png|800]]

The curve shows how sharply the requirement depends on $s$. Hydrogen is the propellant that could make a single stage work, but its low density needs large, heavy tanks, which raises $s$ and pushes the requirement up again. Since the propellant tankage is a large mass that is useless once empty, performance improves greatly if it is shed progressively during the ascent: staging, [[SESA1015 A05 - Staging and Payload Fraction]].

> [!check] Payload of a hydrogen single stage
> Rearranging $V_{ex}\ln\frac{1+s}{p+s}=\Delta V$ gives $p=(1+s)e^{-\Delta V/V_{ex}}-s$. With $\Delta V=8.75$ km/s, $s=0.1$ and $V_{ex}=4.4$ km/s, $p=1.1e^{-1.989}-0.1=1.1(0.1369)-0.1=0.051$: about 5 % payload, if the hydrogen tanks could be built at $s=0.1$. With $V_{ex}=3.25$ km/s, $p=-0.026$: impossible.

## Worked examples

### Upper stage burn in orbit

An upper stage in orbit has mass 5000 kg, of which 3000 kg is propellant, and $V_{ex}=3.0$ km/s. With no gravity or drag loss along the burn,

$$
\Delta V=3000\ln\frac{5000}{2000}=3000\ln2.5=3000(0.9163)=2749\ \mathrm{m/s}.
$$

The one-shot model of Section 1 would give $V_1=(m/M)V_{ex}=(3000/2000)(3000)=4500$ m/s, 64 % too high, because it lets every kilogram of propellant push against the burnout mass only.

### Gravity loss of a vertical burn

A vehicle lifts off vertically with $T/(M_0g)=1.5$, burns 75 % of its mass ($M_b/M_0=0.25$), and has $V_{ex}=3$ km/s. Its burn time is

$$
t_b=\frac{(1-M_b/M_0)V_{ex}}{g\,T/(M_0g)}=\frac{0.75\times3000}{9.807\times1.5}=153\ \mathrm{s},
$$

and if it stayed vertical the gravity loss would be

$$
\Delta V_g=g\,t_b=V_{ex}\frac{1-M_b/M_0}{T/(M_0g)}=3000\times\frac{0.75}{1.5}=1500\ \mathrm{m/s},
$$

out of an ideal $\Delta V_{ideal}=3000\ln4=4159$ m/s, more than a third. The integration in Section 5 for this vehicle (30 t, 3 m diameter) adds a drag loss of 275 m/s. A real vehicle turns over and the loss is smaller, since only $g\sin\gamma$ acts along the path, which is why the typical figure is 0.75–1.5 km/s.

## Links

- Parent: [[SESA1015 Intro to Aero & Astro Hub]]
- Previous: [[SESA1015 A03 - Launch Environment]] · Next: [[SESA1015 A05 - Staging and Payload Fraction]] · Then: [[SESA1015 A06 - Launch Vehicles, Systems and Interfaces]]
- Concepts: [[Tsiolkovsky Rocket Equation]] · [[Gravity and Drag Losses]] · [[Rocket Mass Fractions]] · [[Rocket Performance Parameters]] · [[Thrust Equation]] · [[Dynamic Pressure and Aerodynamic Coefficients]]
- Earlier: momentum conservation in [[Principle of Linear Impulse and Momentum]] (FEEG1002) and control-volume momentum flux in [[Momentum Flux]] (SESA1016).
- Later in the degree: [[SESA2023 W10 - Rocket Performance, Staging and Power Cycles]] (chamber and nozzle performance, the rocket equation with structural ratio $\delta$) · [[SESA2023 W11 - Solid Propellants and Rocket Nozzle Design]] · [[SESA2024 07 - Spacecraft Propulsion]] (in-space $\Delta V$) · [[SESA2024 04 - Orbital Energy and the Vis-Viva Equation]] (orbital speeds beyond the circular case).

## Sources

- Astronautics Part 3, Launch Vehicles: pp. 3–5 (conservation of momentum, exhaust velocity), pp. 6–12 (derivation of the rocket equation, equation 3.1), pp. 13–16 (launch vehicle forces, equations 3.2 and 3.3), pp. 17–18 (vector form), pp. 19–20 (ascent optimisation, Ariane 44LP ascent profile), p. 21 (numbers for LEO), pp. 22–23 (single stage to orbit), p. 58 (reading: Fortescue, Stark and Swinerd, Chapter 7; *How Spacecraft Fly*, Chapter 5).
- Astronautics Part 1, Introduction: p. 5 (LEO altitude range).
- The gravity-loss formula for a vertical burn, the loss-trade simulation and the gravity-turn reading of the $\mathbf j$ equation are background added to the slides.
- Figures: `01 - Notes/Figures/generate_astro_a04_figures.py`.

## Self-study tasks

There are no exercises set in the Part 3 deck; the tasks below rework the slide derivations and examples, plus three suggested problems.

### Core

- [ ] Derive the rocket equation from the momentum balance of a rocket in space, starting from the picture on Part 3, p. 7, without notes (pp. 7–11). → [[#2. The rocket equation for a rocket in space]]
- [ ] Rework the 1000 kg to LEO example: losses, mass ratio and fuel mass (Part 3, p. 21). → [[#Propellant to put 1000 kg into LEO]]
- [ ] Show that $M_0/M_b=(1+s)/(p+s)$ exactly and reproduce $V_{ex}=3.25$ km/s for single stage to orbit (Part 3, pp. 22–23). → [[#Deriving the mass ratio in terms of p and s]] · [[#The single stage to orbit limit]]
- [ ] Derive equation (3.2) from the launch-vehicle force diagram, naming each loss term (Part 3, pp. 13–16). → [[#4. The rocket equation for a launch vehicle]] · [[#5. Gravity loss and drag loss]]

### Further practice

- [ ] Resolve the vector equation of Part 3, p. 18 into its $\mathbf i$ and $\mathbf j$ components and explain what the $\mathbf j$ equation says when $L=0$. → [[#6. Vector form and the turn of the trajectory]]
- [ ] Suggested, not lecturer-set: an orbiting stage of 5000 kg burns 3000 kg of propellant at $V_{ex}=3$ km/s. Find $\Delta V$ and compare with the one-shot estimate. → [[#Upper stage burn in orbit]]
- [ ] Suggested, not lecturer-set: find the burn time and vertical gravity loss for $T/W_0=1.5$, $M_b/M_0=0.25$, $V_{ex}=3$ km/s. → [[#Gravity loss of a vertical burn]]

## Transcript and slide slips

> [!warning] Slide slip (Part 3, p. 4)
> Where: [[#1. Conservation of momentum with one ejected mass]].
>
> "Make $V_2$ as large and as negative as possible" mixes two ideas. $V_1=(m/M)(V-V_2)$ grows as $V_2$ becomes more negative, that is, as the mass is thrown backwards faster; "large" here means large in magnitude, not a large positive value.

> [!warning] Slide slip (Part 3, p. 18)
> Where: [[#6. Vector form and the turn of the trajectory]].
>
> The outflow term is written $\sigma(\mathbf V+\mathbf V_{ex})$, with $\mathbf V_{ex}$ a vector pointing backwards, and on the next line as $\sigma(V-V_{ex})\mathbf i$, with $V_{ex}$ a positive magnitude. Both are the same quantity, but the change of meaning of $V_{ex}$ between the two lines is not stated.
