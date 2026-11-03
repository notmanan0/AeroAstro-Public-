---
title: "SESA2023 W08 - Turbomachinery Principles - Euler Equation and Velocity Triangles"
module: "SESA2023 Propulsion"
type: topic
stream: "Section 4: Turbomachinery and Propellers"
order: 8
tags:
  - sesa2023
  - turbomachinery
  - euler-work-equation
  - velocity-triangles
aliases: ["Turbomachinery principles", "Velocity triangles", "SESA2023 Week 8"]
date: 2026-09-24
status: lectured
coverage: "Week 8 (Lectures 22–24)"
parent: ["[[SESA2023 Propulsion Hub]]"]
prerequisites: ["[[SESA2023 W07 - Turbofan Architectures and Fan Pressure Ratio Selection]]", "[[SESA2023 W02 - Thermodynamics, Mixtures, SFEE and Isentropic Efficiency]]"]
next_topics: ["[[SESA2023 W09 - Turbomachinery Characteristics - Coefficients, Similarity and Maps]]"]
key_concepts: ["[[Euler Work Equation]]", "[[Velocity Triangles]]", "[[Degree of Reaction]]", "[[Compressor Stall and Surge]]"]
tutorial_sheets: ["[[SESA2023 Problem Sheet 8 Turbomachinery Solutions]]"]
sources: ["02 - Sources/Lectures/Week 08 - Turbomachinery Principles.pdf", "02 - Sources/Lectures/SESA2023 Lecture 22.txt", "02 - Sources/Lectures/SESA2023 Lecture 23.txt", "02 - Sources/Lectures/SESA2023 Lecture 24.txt"]
---

# SESA2023 W08 - Turbomachinery Principles - Euler Equation and Velocity Triangles

> [!abstract] Summary
> A turbomachine exchanges energy with a flow by changing its angular momentum (swirl) across a rotor, and Newton's second law for rotation combined with the SFEE gives the Euler work equation, $\Delta h_0=U_2V_{\theta2}-U_1V_{\theta1}$. Compressors turn the flow towards axial, diffusing it against an adverse pressure gradient that risks stall, so each stage manages a pressure ratio under 2; turbines turn it away from axial, and one turbine stage can drive about six compressor stages. Velocity triangles convert between the stationary frame (stators, kinetic energy, Mach number) and the rotating frame (rotors, $V_{\theta,rel}=V_\theta-U$), turning the Euler equation into flow angles.

> [!summary]- Exam use: quick path
> - **Use it when:** a stage is described by blade speed, axial velocity, flow angles, or work per kilogram, and you need the missing angles, velocities, torque, power or $\Delta h_0$; or you must sketch blades and triangles.
> - **Assumptions:** steady (or periodic, time-averaged); adiabatic, so $\Delta h_0$ is the shaft work; mean-line analysis at constant radius ($U_1=U_2=U$); constant $V_x$ unless told; angles from the axial direction, positive in the direction of blade motion; flow leaves each row along its metal angle (no deviation) unless told.
> - **Method:** 1. Sketch the blades and the direction of $U$. 2. Inlet triangle: $V_\theta=V_x\tan\alpha$, then $V_{\theta,rel}=V_\theta-U$. 3. Euler: $\Delta h_0=U(V_{\theta2}-V_{\theta1})$ gives the exit swirl. 4. Exit triangle, both frames: $\tan\alpha=V_\theta/V_x$, $V=V_x/\cos\alpha$. 5. Power $\dot W=\dot m\Delta h_0$, torque $\dot W/\Omega$; mirror blading or repeating stages give extra relations.
> - **Common mistakes:** using the relative velocity for the kinetic energy or Mach number in the stationary frame (and vice versa); getting the sign of $V_\theta$ wrong when the swirl opposes the blade motion.
> - **Practise:** [[#Worked example – repeating compressor stage]] · [[SESA2023 Problem Sheet 8 Turbomachinery Solutions]] Q8.1–Q8.3

A rotor can only push on the gas sideways, in the direction it moves, so the work it does shows up as a change in the gas's swirl velocity $V_\theta$ multiplied by the blade speed. In a compressor the rotor adds kinetic energy and the stator converts it to pressure: the rotor flings the gas round faster (work in), and the stator straightens it out again, slowing it and raising the pressure, so the velocity rises and falls like a sawtooth while the pressure climbs steadily (L24, ll. 66–90). Each blade row sees the flow in its own frame. A rotor blade cares about the velocity relative to itself and the next stator about the absolute velocity, and the velocity triangles are the vector sum $\mathbf V=\mathbf V_{rel}+\mathbf U$.

Compressors have the harder job. Slowing a flow against rising pressure thickens the boundary layer and risks stall, so each compressor stage turns the flow only a little, about 30°, while a turbine's accelerating flow tolerates about twice the turning, which is why one turbine stage drives many compressor stages (L22, ll. 400–451).

---

## 1. Turbomachines (Lecture 22)

- A turbomachine transfers energy to or from a fluid by steadily rotating aerodynamic surfaces, unlike positive-displacement machines (pistons) whose enclosed volume changes (handout §8.2).
- Examples: jet-engine compressors and turbines, aircraft propellers, rocket turbopumps.
- Axial machines have negligible radial velocity; radial machines have negligible axial velocity at rotor inlet or outlet. A centrifugal impeller (turbocharger) takes axial flow in and sends radial flow out. Real machines are rarely purely either.
- Large gas turbines use axial machines for their high efficiency at high volume flow, with many stages for the pressure ratio. Small helicopter engines use centrifugal compressors (lower volume flow; see specific speed in W09).
- Through a compressor of pressure ratio 15 the density rises by a large factor (about 10 in a high-OPR core), so the annulus height must fall to keep $V_x$ roughly constant (L22, l. 75; L24, ll. 290–296).
- There is no physical barrier holding the pressure in: "you can put a string from the inlet of a gas turbine to the outlet". A 40 : 1 pressure ratio is held purely by the aerodynamics of moving aerofoils (L22, ll. 19–25; L24, ll. 27–31).
- **Materials:** compressors run below about 800 K, too hot for aluminium (creep) but fine for titanium alloys; turbines see up to about 1700 K at take-off and use single-crystal nickel superalloys (L24, ll. 21–24).

### Centrifugal compressors (L22, ll. 197–239)

Axial flow enters, and the impeller's near-radial vanes fling it outwards with swirl. Its advantage: even if the vanes stalled, spinning the fluid sets up a centripetal pressure difference between centre and rim (like the blood pressure in your hands when you spin with arms out). So a centrifugal stage supports a much larger pressure ratio: about 4 per stage against about 1.5 for an axial stage. An overall ratio of 16 needs two centrifugal stages but about seven axial ones ($1.5^7\approx17$). They suit small machines (helicopter engines, car turbochargers) and rocket propellant pumps, which handle small volume flows (L22, ll. 186–196).

---

## 2. The Euler work equation (Lecture 23)

### Derivation

Consider a stream tube through a rotor from radius $r_1$ to $r_2$, with steady mass flow $\dot m$ (L23, ll. 150–196; handout §8.3).

**Angular momentum flux.** A packet of mass $\delta m=\dot m\,dt$ with swirl velocity $V_\theta$ at radius $r$ carries angular momentum $\delta m\,rV_\theta$. So the angular-momentum flux is $\dot m\,rV_\theta$.

**Torque.** By Newton's second law for rotation, the torque applied to the fluid equals the flux out minus the flux in (the same $\dot m$ in and out by continuity):

$$
T = \dot m\left(r_2V_{\theta2}-r_1V_{\theta1}\right)
$$

**Power.** Multiply by the shaft speed $\Omega$ and use the blade speed $U=r\Omega$:

$$
\dot W_{in} = T\Omega = \dot m\left(U_2V_{\theta2}-U_1V_{\theta1}\right)
$$

**SFEE.** For an adiabatic machine ($\dot Q=0$) the power input is $\dot W_{in}=\dot m\,\Delta h_0$. Equate and cancel $\dot m$:

$$
\boxed{\Delta h_0 = U_2V_{\theta2}-U_1V_{\theta1}}
$$

At constant radius (mean-line analysis), $U_1=U_2=U$:

$$
\Delta h_0 = U\left(V_{\theta2}-V_{\theta1}\right)
$$

and since $V_\theta=V_{\theta,rel}+U$, the $U$s cancel in the difference:

$$
\Delta h_0 = U\left(V_{\theta2,rel}-V_{\theta1,rel}\right)
$$

> [!warning] Sign convention: torque *input* (L23, ll. 185–196)
> The lecturer first set up the torque as an *output*, then checked it against a turbine ("a high swirl velocity coming in, in the direction of rotation… less angular momentum coming out") and reversed it: "this would be torque input rather than torque output". With the form above, $\Delta h_0>0$ for a compressor and $\Delta h_0<0$ for a turbine ($V_{\theta1}>V_{\theta2}$).

> [!warning] Not in the data book (L23, ll. 238–241)
> "This equation is not in your data book… you essentially need to be able to derive it and know where it comes from. It's not a complicated derivation. You just need to be careful about the signs."

### When does it hold?

The lecture's checklist (L23, ll. 242–307):

- The whole flow? No: only along one stream tube, which must have a single $V_\theta$ at inlet and outlet. $V_\theta$ varies from root to tip, so apply it shell by shell (usually at mid-span).
- **With blade friction:** yes. Viscous shear on the blades is just another way of changing the fluid's angular momentum (a bladeless disc turbine works that way), and friction converts kinetic to thermal energy without changing the total.
- **With hub friction:** only if the hub rotates with the rotor; friction on a stationary hub upstream is outside the control volume.
- **Accelerating (unsteady) flow:** no; the SFEE assumed steady flow.
- **With losses:** yes. Losses do not change the work for a given change of swirl; they change the pressure change that work achieves (a bigger pressure drop in a turbine for the same work, a smaller rise in a compressor) (handout §8.7.1).
- **Compressible flow:** yes; nothing assumed incompressibility.
- Unsteady but periodic flow (rotor blades cutting stator wakes): yes, if the velocities are averaged over a whole number of blade-passing periods (L23, ll. 295–302).
- **With heat transfer:** not as written; keep the $\dot Q$ term in the SFEE (L23, ll. 303–307).

Blade aerodynamics is studied in a linear cascade (L23, ll. 84–122), a row of extruded blades side by side in a wind tunnel, such as at Oxford's Osney Lab, with only the central passage measured so the others hide the end walls. "If you get asked a question about a linear cascade in an exam… you know it's not moving, and if it's not moving there's no work done on the fluid", so $h_0$ is constant. The results transfer to rotating rows by switching to the relative frame.

### Worked example – centrifugal impeller

Handout §8.3.1: 10 kg/s, outer radius $r_2=0.1$ m, 20,000 rpm, radial vanes, no inlet swirl ($V_{\theta1}=0$). Radial vanes mean the flow leaves with the blade's tangential speed, $V_{\theta2}=U_2$.

$$
U_2 = 0.1\times\frac{2\pi\times20\,000}{60} = 209.4\ \mathrm{m/s}
$$

$$
T = \dot m\,r_2V_{\theta2} = 10\times0.1\times209.4 = 209.4\ \mathrm{N\,m}
$$

$$
\dot W = \dot mU_2V_{\theta2} = 10\times209.4^2 = 438.6\ \mathrm{kW},\qquad \Delta h_0 = \frac{\dot W}{\dot m} = 43.9\ \mathrm{kJ/kg}
$$

### Worked example – axial turbine

Handout §8.3.2: $r=0.3$ m, $\Omega=1000$ rad/s, inlet swirl $V_{\theta1}=500$ m/s, $\Delta h_0=-200$ kJ/kg.

$$
U = 0.3\times1000 = 300\ \mathrm{m/s}
$$

$$
V_{\theta2} = V_{\theta1}+\frac{\Delta h_0}{U} = 500-\frac{200\,000}{300} = -167\ \mathrm{m/s}
$$

The flow leaves swirling against the blade motion: the turbine has reversed its swirl to extract the work.

---

## 3. Axial compressors and turbines (Lectures 22 and 24)

### Compressor stage

A stage is a rotor followed by a stator (handout §8.4.1).

- **Rotor:** does work, so $V_\theta$ and $h_0$ rise. The absolute velocity goes up, and so does the static pressure, because $p_0$ is rising (work input) while the relative flow is diffused (L24, ll. 58–67).
- **Stator:** removes the swirl at constant $h_0$; the kinetic energy falls and the static pressure rises (a diffuser). The velocity returns to about its starting value, ready for the next rotor (L24, ll. 69–80).
- A second rotor straight after the first would not work: the gas is already swirling at about blade speed, so the blades could not push it further without going faster still (L24, ll. 69–73).
- Inlet guide vanes (IGVs) are a special stator before the first rotor that sets the preferred swirl into it, reducing the relative Mach number on the first rotor and letting every stage use the same optimised design (L24, ll. 91–93, 319–326). Adding swirl speeds the flow up, so the static pressure actually falls through the IGV, not ideal in a compressor but worth it for the rotor incidence (L24, ll. 42–56). Most modern engines start with the fan rotor instead, followed by outlet guide vanes (L22, ll. 56–59).
- **Stagnation pressure:** it falls slightly through a stator (viscous losses, no work) and rises through a rotor (work input, minus losses). Static pressure rises in both (L24, ll. 185–193).
- In the rotor's own frame there is no shaft work, so the rotor is simply a diffuser: turning the flow towards axial widens the relative stream tube, the relative velocity falls and the static pressure rises (L24, ll. 196–221).
- Typical Mach numbers (L24, ll. 259–270): a compressor row decelerates its (relative) flow from about M 0.6 to M 0.3; a turbine row accelerates from about M 0.3 to about M 1 or more, in both stator and rotor frames.

### Turbine stage

A stator (nozzle guide vanes) followed by a rotor (handout §8.4.2). The flow from the combustor has almost no swirl, so the stator first gives it a large swirl, which then pushes the rotor round "like a water wheel" (L22, ll. 259–267). The flow accelerates in both rows; the favourable pressure gradient keeps boundary layers thin, so much more turning is possible.

A turbine passage is a nozzle (L22, ll. 345–395; "you don't need to really go into that in your exam"). Turning the flow *away* from axial narrows the stream tube, so a subsonic flow accelerates. The pressure ratio across a turbine row is often about 2, above the critical 1.89, so the passage chokes at a throat between one blade's trailing edge and its neighbour. Downstream the blade thins while the flow direction barely changes, so the channel slightly diverges and the exit can be supersonic, with oblique trailing-edge shocks. A whole turbine (pressure ratio 20–30) typically has only about five stages.

### Blade aerodynamics and why compressors need more stages

- Compressor blading turns the flow towards axial. The stream tube widens, the flow decelerates and the pressure rises, so the boundary layer is pushed against a rising pressure. At high positive incidence (low flow, high speed) it separates: stall, and in the whole machine surge (W09) (handout §8.6; L22, ll. 400–405).
- Cascade data (L22, ll. 406–430): a compressor cascade with 21° metal exit angle ran at about 9° deviation at design, rising to 15° at positive incidence before separating; acceptable incidence was only about ±8°, and the flow was turned about 30°.
- A turbine cascade had practically zero deviation over about 50° of incidence and turned the flow about 65° ("one of these should be minus 18 to plus 47", L22, l. 444): twice the compressor's turning (L22, ll. 431–447).
- So a compressor stage is limited to a pressure ratio under 2, and one turbine stage can drive about six compressor stages.
- Blade loading falls with more stages, or with more blades per row, at the cost of weight, cost and wetted area.

### Blade anatomy and angles

Hub, casing, root, tip, leading and trailing edges, camber (the curvature between inlet and outlet) (handout §8.4.3; L22, ll. 106–158, 342). The course symbols:

| Quantity | Symbol | Note |
|---|---|---|
| chord | $c$ | leading to trailing edge |
| axial chord | $c_x$ | the chord projected on the axis |
| span (height) | $h$ | root to tip |
| pitch (spacing) | $s$ | circumferential distance between blades; often quoted as an angle, since it differs at root and tip |
| tip clearance | — | kept small to limit leakage from pressure to suction side |

Blades machined integrally with their disc form a blisk (bladed disc), or a bling on a hollow ring. Large turbine blades are slotted in with fir-tree roots so they can be replaced individually without the stress concentrations of welding (L22, ll. 140–148, 244–252).

> [!warning] Transcript slip (L23, ll. 38–40)
> "A concave surface which we've described as the pressure surface and a convex surface, this upper surface we described as the pressure surface." The convex surface is the suction surface.

- $\alpha$ is the flow angle and $\beta$ the metal angle.
- Incidence $i=\alpha_{in}-\beta_{in}$: the turbomachinery counterpart of angle of attack (the name is not used because there is no "horizontal" inside a rotating machine, L22, ll. 337–341).
- Deviation $\delta$: the difference between the flow and metal angles at exit, caused by boundary-layer growth even when the Kutta condition holds.

> [!warning] Deviation sign (L22, ll. 332–336)
> The slide defines $\delta=\alpha_{out}-\beta_{out}$. The lecturer then says "that should be the other way around I think. Beta out minus alpha out. So in this case it would be positive". Which form gives a positive number depends on the blade's turning direction. Quote the magnitude, say which way the flow under-turns, and state your sign.

### Mean-line analysis

The mean-line (mid-span) analysis treats the flow at one representative radius as 2-D, steady and at constant radius (handout §8.5).

- Each blade passage is identical, so conditions repeat from one passage to the next.
- At exit the Kutta–Joukowski condition makes the flow leave the trailing edge smoothly, close to the metal angle.
- Between blade rows there is no torque on the fluid, so the angular momentum $rV_\theta$ is conserved until the next row.

The lecturer's advice is to sketch the blades first (L24, ll. 95–108; L22, ll. 343–345): "when I'm drawing velocity triangles it's something that you need to be able to do for your exam. I like to draw the blade shape first." A rotor moving to the right must lean so the relative flow meets its leading edge; draw the relative velocity along the metal angle, then add $U$ to get $V$. "I would expect you to be able to sketch out this kind of blade… in your exam and in your careers."

---

## 4. Velocity triangles (Lecture 24)

### Relations

$$
\mathbf V = \mathbf V_{rel}+\mathbf U
$$

The blade moves tangentially, so only the tangential component changes between frames:

$$
V_{x,rel} = V_x,\qquad V_{\theta,rel} = V_\theta-U
$$

With angles from the axial direction, positive in the direction of blade motion:

$$
\tan\alpha = \frac{V_\theta}{V_x},\qquad \tan\alpha_{rel} = \frac{V_{\theta,rel}}{V_x},\qquad V = \frac{V_x}{\cos\alpha},\qquad V_{rel} = \frac{V_x}{\cos\alpha_{rel}}
$$

- Use the relative velocity for the rotor's own aerodynamics (incidence, relative Mach number).
- Use the absolute velocity for kinetic energy and Mach number in the stationary frame, and for the stators (L24, ll. 122–127).

### The Euler equation in angles

With constant $V_x$, substitute $V_\theta=V_x\tan\alpha$ into $\Delta h_0=U(V_{\theta2}-V_{\theta1})$:

$$
\Delta h_0 = UV_x\left(\tan\alpha_2-\tan\alpha_1\right)
$$

and, since $\tan\alpha_{rel}=\tan\alpha-U/V_x$ and the $U/V_x$ terms cancel in the difference,

$$
\Delta h_0 = UV_x\left(\tan\alpha_{2,rel}-\tan\alpha_{1,rel}\right)
$$

### Design choices

- **Constant $V_x$**: the usual starting assumption; it corresponds roughly to a constant axial Mach number, and requires the annulus to shrink through a compressor and flare out through a turbine (L24, ll. 290–299).
- High $V_x$ gives power density, but is limited by compressibility (relative tip Mach number).
- **Repeating stages**: $V_3=V_1$ and $\alpha_3=\alpha_1$, so each stage can reuse the same optimised design, scaled down as the blades get shorter (L24, ll. 300–326).
- **Mirror blading**: the stator is the mirror image of the rotor. If both rows' exit flows follow their metal angles, the velocity triangles are mirror images too, which gives extra equations (L24, ll. 327–346):

$$
V_{\theta3} = -V_{\theta2,rel},\qquad V_{\theta3,rel} = -V_{\theta2},\qquad \alpha_3 = -\alpha_{2,rel}
$$

For a repeating mirror stage, $\alpha_1=\alpha_3=-\alpha_{2,rel}$, i.e. $V_{\theta1}=-(V_{\theta2}-U)$, so

$$
V_{\theta1}+V_{\theta2} = U
$$

The rotor and stator then share the static-pressure rise equally: this is the 50 % reaction stage of [[SESA2023 Problem Sheet 8 Turbomachinery Solutions]] Q8.3 (the term "degree of reaction" is used on the problem sheet, not in the lectures). See [[Degree of Reaction]].

### Worked example – repeating compressor stage

Handout §8.7.2: $U=300$ m/s, $\alpha_1=\alpha_3=26^\circ$, $V_x=0.55U=165$ m/s, $\Delta h_0=0.45U^2=40.5$ kJ/kg; constant $V_x$.

**Rotor inlet, absolute:**

$$
V_{\theta1} = 165\tan26^\circ = 80.5\ \mathrm{m/s},\qquad V_1 = \frac{165}{\cos26^\circ} = 183.6\ \mathrm{m/s}
$$

**Rotor inlet, relative:**

$$
V_{\theta1,rel} = 80.5-300 = -219.5\ \mathrm{m/s},\qquad \alpha_{1,rel} = \tan^{-1}\frac{-219.5}{165} = -53.1^\circ,\qquad V_{1,rel} = 274.6\ \mathrm{m/s}
$$

**Euler equation for the exit swirl:**

$$
V_{\theta2} = V_{\theta1}+\frac{\Delta h_0}{U} = 80.5+\frac{40\,500}{300} = 215.5\ \mathrm{m/s}
$$

**Rotor exit, absolute and relative:**

$$
\alpha_2 = \tan^{-1}\frac{215.5}{165} = 52.6^\circ,\qquad V_2 = 271.4\ \mathrm{m/s}
$$

$$
V_{\theta2,rel} = 215.5-300 = -84.5\ \mathrm{m/s},\qquad \alpha_{2,rel} = -27.1^\circ,\qquad V_{2,rel} = 185.4\ \mathrm{m/s}
$$

| | Absolute | Relative |
|---|---|---|
| Rotor inlet | $V_{\theta1}=80.5$, $V_1=183.6$ m/s, $\alpha_1=26^\circ$ | $V_{\theta1,rel}=-219.5$, $V_{1,rel}=274.6$ m/s, $\alpha_{1,rel}=-53.1^\circ$ |
| Rotor exit | $V_{\theta2}=215.5$, $V_2=271.4$ m/s, $\alpha_2=52.6^\circ$ | $V_{\theta2,rel}=-84.5$, $V_{2,rel}=185.4$ m/s, $\alpha_{2,rel}=-27.1^\circ$ |

The absolute speed rises through the rotor (work input) while the relative speed falls: the rotor diffuses the flow in its own frame, which raises the static pressure. The stator then diffuses $V_2=271$ back to $V_3=V_1=184$ m/s in the absolute frame.

![[prop_compressor_velocity_triangles.png|760]]

> [!check] Numerical checks
> - Rotor turning: $-53.1^\circ\to-27.1^\circ$, i.e. 26° towards axial; stator turning $52.6^\circ\to26^\circ$, also about 26°: within the compressor's ~30° budget.
> - Near-mirror stage: $\alpha_1=26^\circ\approx-\alpha_{2,rel}=27.1^\circ$, and $(V_{\theta1}+V_{\theta2})/U=296/300=0.99$, so the reaction is about 50 %.
> - Euler two ways: $UV_x(\tan\alpha_2-\tan\alpha_1)=300\times165\times(1.306-0.488)=40.5$ kJ/kg ✔, and with relative angles $300\times165\times(-0.512+1.330)=40.5$ kJ/kg ✔.

---

## 5. Problem-solving workflow

1. Sketch the blade rows, mark $U$, and decide which rows are rotors.
2. Write the known triangle (usually rotor inlet) in both frames.
3. Use the Euler equation (or the work coefficient, W09) for the change in swirl.
4. Complete the exit triangle in both frames; use repeating-stage or mirror conditions if given.
5. Power, torque and, if needed, temperatures via $\Delta T_0=\Delta h_0/c_p$ and the pressure via $\eta$ (W02).
6. Check: compressor rotor relative speed falls; turbine rotor relative speed rises; turning angles plausible (≈30° compressor, ≈65° turbine).

## Terminology and alternative names

| Course term | Also called | Where the course uses it | Note |
|---|---|---|---|
| swirl velocity $V_\theta$ | whirl velocity, tangential velocity, $c_u$, $V_w$ | L23, L24 | |
| blade speed $U$ | peripheral speed | handout §8.7 | $U=r\Omega$. |
| Euler work equation | Euler turbomachinery equation | handout §8.3 | |
| velocity triangle | velocity diagram, vector diagram | L24, l. 347 | |
| flow angle $\alpha$, $\alpha_{rel}$ / metal angle $\beta$ | gas angle / blade angle | handout §8.6; L22, ll. 318–324 | "Sometimes they use alpha for absolute angles and beta for relative flow angles, but I just… put the relative label explicitly." |
| incidence $i$ | angle of attack | handout §8.5 | |
| nozzle guide vanes (NGV) | turbine stator | handout §8.4.2 | |
| inlet guide vanes (IGV) | — | L24, ll. 91–93 | |
| mirror blading | symmetric blading; 50 % reaction | L24, ll. 327–346 | "Reaction" appears on Problem Sheet 8. |
| bladed disc | blisk, "bling" (bladed ring) | L22, l. 148 | |

## Links

- Parent: [[SESA2023 Propulsion Hub]] · Previous: [[SESA2023 W07 - Turbofan Architectures and Fan Pressure Ratio Selection]] · Next: [[SESA2023 W09 - Turbomachinery Characteristics - Coefficients, Similarity and Maps]]
- SFEE and isentropic efficiency for the thermodynamics of a stage: [[SESA2023 W02 - Thermodynamics, Mixtures, SFEE and Isentropic Efficiency]]
- Worked sheet: [[SESA2023 Problem Sheet 8 Turbomachinery Solutions]] · Formula list: [[SESA2023 Formula Sheet]]
- Exams: [[SESA2023 Exam 2021-22 Solutions]] Q4, [[SESA2023 Exam 2022-23 Solutions]] Q4 (turbine), [[SESA2023 Exam 2024-25 Solutions]] Q4, [[SESA2023 Exam 2023-24 Solutions]] Q4 (propeller)

## Sources

- `Week 08 - Turbomachinery Principles.pdf`: Week 8 handout (E. Richardson) §§8.2–8.7 and the Lecture 22–24 slides; Rolls-Royce, *The Jet Engine* (1992) figures.
- Transcripts (line numbers refer to these files): L22 `SESA2023 Lecture 22.txt` (17 Mar: machines, blade rows, cascade data); L23 `SESA2023 Lecture 23.txt` (17 Mar: Euler equation); L24 `SESA2023 Lecture 24.txt` (20 Mar: stages, velocity triangles, repeating and mirror stages).

## Self-study tasks

Tasks marked *(set)* were set or explicitly pointed to in the Week 8 lectures; the rest are suggested, not lecturer-set. Attempt each closed-book, then check against the linked section.

### Core

- [ ] *(set)* Derive the Euler work equation: "Do the derivation, do some examples, there are some in the problem sheet for this week" (L23, ll. 308–309). It is not in the data book (ll. 238–241). → [[#Derivation]]
- [ ] *(set)* Draw velocity triangles, blade shapes first: "the key thing that you kind of need to be able to do in the exam… Have a practice" (L24, ll. 348–350). → [[#Worked example – repeating compressor stage]]
- [ ] *(set)* Sketch compressor and turbine blade rows with the flow and metal angles (L22, ll. 343–345). → [[#Blade anatomy and angles]]
- [ ] *(set)* Work [[SESA2023 Problem Sheet 8 Turbomachinery Solutions|Problem Sheet 8 (turbomachinery)]] and the Week 8 quiz (L24, l. 362).

### Further practice

- [ ] Centrifugal impeller and axial turbine examples. Targets 209 N m, 439 kW; $V_{\theta2}=-167$ m/s. → [[#Worked example – centrifugal impeller]] · [[#Worked example – axial turbine]]
- [ ] Derive $\Delta h_0=UV_x(\tan\alpha_2-\tan\alpha_1)$ and its relative-angle form. → [[#The Euler equation in angles]]
- [ ] Show that a repeating mirror stage has $V_{\theta1}+V_{\theta2}=U$. → [[#Design choices]]
- [ ] Explain, using pressure gradients and boundary layers, why one turbine stage can drive about six compressor stages. → [[#Blade aerodynamics and why compressors need more stages]]
- [ ] State when the Euler equation holds (whole flow, blade and hub friction, unsteady and periodic flow, losses, compressibility, heat transfer). → [[#When does it hold?]]
- [ ] Explain why a centrifugal stage can reach a pressure ratio of about 4 while an axial stage manages about 1.5. → [[#Centrifugal compressors (L22, ll. 197–239)]]
- [ ] Explain why a turbine blade passage can choke and deliver supersonic flow. → [[#Turbine stage]]
