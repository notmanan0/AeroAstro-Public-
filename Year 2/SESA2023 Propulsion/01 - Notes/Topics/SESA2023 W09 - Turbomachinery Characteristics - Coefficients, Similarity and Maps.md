---
title: "SESA2023 W09 - Turbomachinery Characteristics - Coefficients, Similarity and Maps"
module: "SESA2023 Propulsion"
type: topic
stream: "Section 4: Turbomachinery and Propellers"
order: 9
tags:
  - sesa2023
  - turbomachinery
  - dimensional-analysis
  - specific-speed
  - compressor-map
aliases: ["Turbomachinery characteristics", "Compressor maps", "SESA2023 Week 9"]
date: 2026-09-24
status: lectured
coverage: "Week 9 (Lectures 25–26, Turbomachinery Characteristics) and the Lecture 27 design example"
parent: ["[[SESA2023 Propulsion Hub]]"]
prerequisites: ["[[SESA2023 W08 - Turbomachinery Principles - Euler Equation and Velocity Triangles]]", "[[SESA1016 T6 - Dimensional Analysis and Similarity]]"]
next_topics: ["[[SESA2023 W10 - Rocket Performance, Staging and Power Cycles]]"]
key_concepts: ["[[Flow and Work Coefficients]]", "[[Dimensional Analysis of Turbomachines]]", "[[Specific Speed]]", "[[Compressor and Turbine Characteristics]]", "[[Compressor Stall and Surge]]", "[[Actuator Disk Theory]]"]
tutorial_sheets: ["[[SESA2023 Problem Sheet 9 Solutions]]"]
sources: ["02 - Sources/Lectures/Week 09 - Turbomachinery Characteristics.pdf", "02 - Sources/Lectures/Week 09 - Turbomachinery Characteristics - Lecture Slides.pdf", "02 - Sources/Lectures/SESA2023 Lecture 25 - Turbomachinery Characteristics.txt", "02 - Sources/Lectures/SESA2023 Lecture 26 - Turbomachinery Characteristics.txt", "02 - Sources/Lectures/SESA2023 Lecture 27.txt"]
---

# SESA2023 W09 - Turbomachinery Characteristics - Coefficients, Similarity and Maps

> [!abstract] Summary
> Turbomachine behaviour collapses onto a few dimensionless groups. The flow coefficient $\phi=V_x/U$ sets the incidence, and the stage loading $\psi=\Delta h_0/U^2$ sets the turning, with its aerodynamic limit (about 0.4–0.65 for compressors, up to 2.5 for turbines) fixing the number of stages. Dimensional analysis says geometrically similar machines at equal groups behave alike, so a model test can stand in for a full-size machine, and the specific speed $N_s=\phi^{1/2}/\psi^{3/4}$ picks the machine's shape before its size is known. High-speed machines are described by maps of $p_{02}/p_{01}$ and $\eta$ against $\dot m\sqrt{T_{01}}/p_{01}$ at constant $N/\sqrt{T_{01}}$: compressors are bounded by surge and choke, while turbines choke and run at nearly constant non-dimensional flow.

> [!summary]- Exam use: quick path
> - **Use it when:** asked how many stages a compressor or turbine needs; to scale a test (model speed, flow, power) to full size; to choose a machine type; or to sketch and explain a compressor or turbine map.
> - **Assumptions:** mean-line, constant radius; equal work in every stage; $\psi_{max}$ given; geometric similarity; Reynolds-number effects neglected above $Re\approx2\times10^5$; same gas ($\gamma$, $c_p$) in model and full size unless stated.
> - **Method:** 1. Overall $\Delta h_0$ from the pressure ratio and $\eta$ (W02). 2. $U=\Omega r$; $\Delta h_{0,stage}\le\psi_{max}U^2$. 3. $n\ge\Delta h_{0,overall}/(\psi_{max}U^2)$, rounded up. 4. Similarity: hold $ND/\sqrt{T_{01}}$ (or $\phi$ and $M$), $\dot m\sqrt{T_{01}}/(D^2p_{01})$ and $\dot W/(\dot mc_pT_{01})$ constant. 5. Read the map at constant $N/\sqrt{T_{01}}$; check the surge margin.
> - **Common mistakes:** rounding the stage count *down*; forgetting $D^2$ when scaling the non-dimensional mass flow between different sizes.
> - **Practise:** [[#Worked example – the Lecture 27 HP compressor design]] · [[SESA2023 Problem Sheet 9 Solutions]] Q9.1, Q9.3–Q9.4

Two numbers describe a blade row's working point: $\phi$ says at what angle the gas meets the blade, its incidence, and $\psi$ how hard the blade is turning it. Keep both near their design values and the blade is efficient. Turning is limited, so the work is split into stages. A compressor blade can turn the flow only so far before its boundary layer separates, and the total work needed divided by the most a stage can do gives the minimum number of stages.

If two machines are geometric scale models and their dimensionless groups match, their velocity triangles and streamline patterns match too, so everything dimensionless, such as efficiency and pressure ratio, is the same and the dimensional quantities scale predictably. The type of machine depends on the duty: one that moves a large volume with a small pressure rise wants a few long blades (axial, or a propeller), while one that makes a big pressure rise on a small flow wants a radial impeller, and specific speed captures that without knowing the size. Maps then show the range in which a machine can operate. At low flow a compressor stalls and surges and at high flow it chokes, whereas a turbine's accelerating flow is stable and soon chokes, so its non-dimensional flow is nearly fixed.

---

## 1. Flow and work coefficients (Lecture 25)

### Definitions

$$
\phi = \frac{V_x}{U},\qquad \psi = \frac{|\Delta h_0|}{U^2}
$$

At constant radius the Euler equation (W08) gives $\Delta h_0=U\Delta V_\theta$, so

$$
\psi = \frac{\Delta V_\theta}{U}
$$

$\psi$ is called the stage loading or work coefficient.

$\psi$ is always taken as positive, using $|\Delta h_0|$; decide from context whether the machine adds or removes work. All of a stage's $\Delta h_0$ happens in the rotor (a stator has no shaft work), so $\psi$ measures how much the rotor turns the flow (L25, ll. 76–97). Because $U$ varies with radius, state where $\psi$ is evaluated, usually mid-span: root and tip values can differ by a factor of two (L26, ll. 3–13).

$\phi$ has two readings (L25, ll. 186–234):

- At the design stage it sets the blade stagger. Low $\phi$ (small $V_x$, large $U$) means a highly staggered row with more metal facing backwards, better for a high pressure rise per stage. High $\phi$ means a low-stagger, open row, better for a high volume flow.
- For a machine already built, $\phi$ measures how far it is from its design point. Below design $\phi$ the incidence becomes positive (towards suction-surface stall, like a wing at high angle of attack); above it, negative, and eventually separation on the pressure surface, which needs a larger change because of the blade's curvature.

- **High $\psi$**: more turning per stage and fewer stages, at lower efficiency.

### Limits on stage loading

- **Compressors**: the overall adverse pressure gradient makes separation the limit. Upper limit about $\psi\le0.65$, typical 0.35–0.5.
- **Turbines**: even with a favourable pressure gradient overall, the suction surface always has a region of adverse gradient near the trailing edge, and at high turning, shock waves from the trailing edge strike the adjacent blade's boundary layer (L25, ll. 120–132). Upper limit $\psi\le2.5$.
- So a turbine rotor can do about $2.5/0.65\approx4$ times the work of a compressor rotor at the same blade speed, which is why a gas turbine has several times more compressor rows than turbine rows (L25, ll. 136–142).

> [!warning] Transcript slip (L25, l. 137)
> "Upper values that we might consider acceptable for a compressor rotor would be about 0.065." The value is 0.65 (the slide's figure, and the "four times" comparison with 2.5 only works for 0.65).

- Smith chart (turbines): efficiency contours on axes of $(\phi,\psi)$. Raising $\psi$ lowers $\eta$, and the best $\phi$ rises with $\psi$ (handout; Smith 1965). Many different Rolls-Royce turbines collapse onto one chart once non-dimensionalised, which is the point of the method (L25, ll. 235–303).

### Worked example – reading the Smith chart (L25, ll. 257–301)

A turbine must deliver a fixed total work.

- Designed at $\psi=1.3$, the best achievable efficiency (moving along that line to the peak contour) is about 94 %, but the turbine needs 8 stages: heavy and costly.
- Halve the stage count to 4. Each stage must now do twice the work, so $\psi=2.6$. The best efficiency on that line is only about 88 %, and it occurs at a higher $\phi$.

The trade-off: 6 points of efficiency for half the stages. "Why does halving the number of stages double the work?" Because the total $\Delta h_0$ is fixed: merge two stages into one super-stage and it does twice the work each (ll. 291–301).
- The fan-tip relative Mach number is kept below about 1.6 (noise, bird strike); the axial Mach number at the fan face is about 0.6.

### The stage count

The choice of $\psi$ is an economic trade-off: low loading is aerodynamically efficient but needs more stages, so a longer, heavier engine with more parts and maintenance (L25, ll. 143–159). With equal work per stage, at least

$$
\boxed{n_{stages}\ge\frac{\Delta h_{0,overall}}{\psi_{max}U^2}}\qquad\text{(round up to an integer)}
$$

> [!warning] Slide inequality reversed (L25, ll. 163–165)
> "This sign here should be the other way around… It should be greater than or equal to this ratio." And: "If you put [in] a number that's a fraction, it just says you're not really thinking" (l. 170). Always round up.

### Worked example – stage count for a turbojet compressor

Handout example: sea level, flight at M 0.8, axial Mach number 0.6 into the first rotor, $\phi=0.55$, no IGV; overall compressor pressure ratio 10, treated as isentropic; $\psi_{max}=0.4$.

**Intake stagnation temperature:**

$$
T_{02} = 288\times(1+0.2\times0.8^2) = 324.9\ \mathrm K
$$

Axial velocity from the Mach number at the rotor face. Using $a^2=(\gamma-1)c_pT$ and $T=T_{02}/(1+\tfrac{\gamma-1}{2}M^2)$:

$$
\frac{V_x}{\sqrt{c_pT_{02}}} = \sqrt{\gamma-1}\;M\left(1+\frac{\gamma-1}{2}M^2\right)^{-1/2} = 0.6325\times0.6\times1.0360^{-1/2} = 0.3665
$$

$$
V_x = 0.3665\sqrt{1005\times324.9} = 209.4\ \mathrm{m/s},\qquad U = \frac{V_x}{\phi} = \frac{209.4}{0.55} = 380.8\ \mathrm{m/s}
$$

**Overall and stage work:**

$$
\Delta h_{0,overall} = c_pT_{02}\left(10^{0.2857}-1\right) = 303.9\ \mathrm{kJ/kg},\qquad \Delta h_{0,stage}\le0.4\times380.8^2 = 58.0\ \mathrm{kJ/kg}
$$

$$
n\ge\frac{303.9}{58.0} = 5.24\qquad\Longrightarrow\qquad \mathbf{6\ stages}
$$

---

## 2. Dimensional analysis (Lecture 25)

### The mental experiment

Ask which variables could change the streamline pattern in the machine. If the streamline patterns, and so the velocity triangles, are similar, then every dimensionless group matches, including efficiency and pressure coefficients (handout; [[SESA2023 Problem Sheet 9 Solutions]] Q9.2).

**Buckingham π**: $n$ variables with $m$ independent dimensions give $n-m$ independent dimensionless groups (L25, l. 307; [[SESA1016 T6 - Dimensional Analysis and Similarity]]).

### Incompressible machines (pumps, fans, hydraulic turbines)

The lecture's thought experiment (L25, ll. 317–390): a pump driven by a motor at speed $\Omega$, with a throttle valve on its outlet. We control the flow $Q$ (with the valve) and $\Omega$; the fluid brings $\rho$ and $\mu$; a geometrically similar family is scaled by $D$; we measure $\Delta p$ (the dependent variable). The independent variables are $Q$, $\Omega$, $D$, $\rho$, $\mu$: five variables, three dimensions (M, L, T), so two groups. There are infinitely many valid choices; use the conventional ones (ll. 15–21, 391–393):

- **Reynolds number**: we need a velocity scale, and $\Omega D$ (proportional to blade speed) is used. Factors of 2 or π do not matter as long as the definition is always the same (ll. 396–405).
- Non-dimensional flow $Q/(\Omega D^3)$: like $\phi=V_x/U$ with $V_x\sim Q/D^2$ and $U\sim\Omega D$ (ll. 409–423).
- Pressure coefficient $\Delta p/(\rho\Omega^2D^2)$: like $\psi$, because $\Delta h_0\approx\Delta p_0/\rho$ for an isentropic constant-density fluid (ll. 425–436).

$$
\frac{Q}{\Omega D^3}\ (\sim\phi),\qquad Re = \frac{\rho\Omega D^2}{\mu}
$$

Every other dimensionless output is a function of these two:

$$
\frac{\Delta p}{\rho\Omega^2D^2},\quad \eta,\quad \frac{\dot W}{\rho\Omega^3D^5} = fn\left(\frac{Q}{\Omega D^3},\,Re\right)
$$

For $Re>2\times10^5$ the boundary layers are thin and turbulent and Re has a weak effect: a factor of 10 in Re changes $\eta$ by only 1–2 %. This is justified by experiment (pump data in the lecture show the curves barely moving with Re). The lecture's one-minute explanation, "not going to be examined on" (L25, ll. 453–471): in laminar flow momentum is carried by molecular motion, whose speed does not grow with the flow, so viscous effects fade as Re rises; in turbulent flow it is carried mainly by eddies whose speed scales with the flow, so everything stays in proportion and the streamline pattern stops changing. Liquids add a cavitation group involving the vapour pressure.

### Compressible machines

Above about M 0.3 compressibility matters, and compressibility $d\rho/dp$ is measured by the speed of sound, $a^2=(\partial p/\partial\rho)_s$, so $\gamma$ and $c_pT$ enter (L26, ll. 108–126). Mass flow replaces volume flow because it is the same at inlet and outlet when density changes (ll. 132–142). The seven variables $\dot m$, $N$, $D$, $\mu$, $\gamma$, $c_pT_{01}$, $p_{01}$ with three dimensions give four groups: a Reynolds-like group, $\gamma$, a flow group and a blade Mach number. The first two are "swept under the carpet": Re for the reason above, and $\gamma$ because a given compressor (or turbine) always handles the same gas (ll. 149–167). That leaves (with $a=\sqrt{(\gamma-1)c_pT}$):

$$
\gamma,\quad \frac{\dot m\sqrt{c_pT_{01}}}{D^2p_{01}},\quad \frac{ND}{\sqrt{c_pT_{01}}}
$$

$$
\frac{p_{02}}{p_{01}},\ \frac{T_{02}}{T_{01}},\ \eta,\ \frac{\dot W}{\dot mc_pT_{01}} = fn\left(\frac{\dot m\sqrt{c_pT_{01}}}{D^2p_{01}},\ \frac{ND}{\sqrt{c_pT_{01}}}\right)
$$

- The first group is the non-dimensional mass flow of W03, so it is fixed by the Mach number of the flow.
- The second is a blade Mach number.
- For one machine on one gas, $D$, $c_p$ and $\gamma$ drop out, leaving $\dot m\sqrt{T_{01}}/p_{01}$ and $N/\sqrt{T_{01}}$, often "corrected" to standard conditions as $\dot m\sqrt\theta/\delta$ and $N/\sqrt\theta$.

Using similarity (typical exam steps):

1. Hold $ND/\sqrt{T_{01}}$ (equivalently $\phi$ at fixed Mach number) to get the test speed.
2. Hold $\dot m\sqrt{T_{01}}/(D^2p_{01})$ to scale the flow.
3. Hold $\dot W/(\dot mc_pT_{01})$ (equivalently $\psi$) to scale the work and power.

These are [[SESA2023 Problem Sheet 9 Solutions]] Q9.3–Q9.4 and [[SESA2023 Exam 2021-22 Solutions]] Q4(ii–iii).

### Worked example – the Lecture 27 HP compressor design

An extended "preliminary design" exercise that ties together W06–W09 (L27, ll. 1–434): specify an HP compressor and plan a cheap scale test. Inlet $T_{023}$, $p_{023}=40$ kPa; overall pressure ratio 15; isentropic efficiency 0.9; input power 5 MW from the HP turbine; 10,000 rpm; cold air ($c_p=1005$, $\gamma=1.4$). Design guidelines: $\psi_{max}$ and $\phi=0.7$, axial flow into every stage ($\alpha_1=0$), constant $V_x$.

> [!warning] Reconciling the spoken data with the lecture's own answers
> - The slide says pressure ratio 20; "the value of pressure ratio I've actually used in the calculation is 15" (ll. 23–25, 283–284).
> - The lecturer says $T_{023}=350$ K ("I think it was", l. 103) and $\psi_{max}=0.6$ (l. 33), with $r=0.25$ m (l. 62). But every answer he quotes (430 kJ/kg, 6.23 stages, $U=314$ m/s, 69 kJ/kg, $V_x=219$ m/s, test $V_x=209$ m/s, mass-flow ratio $1.78\times10^{-3}$) is reproduced exactly with $T_{023}=330$ K, $\eta_c=0.9$, $\psi_{max}=0.7$ and $U=314$ m/s (i.e. $r=0.3$ m at 10,000 rpm). Those values are used below.

**(a) Number of stages.** Overall work from the W02 compressor relations:

$$
\Delta h_{0,overall} = \frac{c_pT_{023}\left(15^{0.2857}-1\right)}{\eta_c} = \frac{1005\times330\times1.1678}{0.9} = 430\ \mathrm{kJ/kg}
$$

"Hundreds of kilojoules per kilogram is typical" (l. 136). Blade speed:

$$
U = r\Omega = 0.3\times\frac{2\pi\times10\,000}{60} = 314\ \mathrm{m/s}
$$

Maximum work per stage and the stage count:

$$
\Delta h_{0,stage,max} = \psi_{max}U^2 = 0.7\times314^2 = 69.1\ \mathrm{kJ/kg},\qquad n\ge\frac{430}{69.1} = 6.23\ \Rightarrow\ \mathbf{7\ stages}
$$

Each stage then does $430/7=61.5$ kJ/kg, i.e. $\psi=0.62$. The mass flow is $\dot m=5\ \mathrm{MW}/430\ \mathrm{kJ/kg}=11.6$ kg/s.

(b) First-rotor blade angles (zero incidence: $\beta_1=\alpha_{1,rel}$; zero deviation: $\beta_2=\alpha_{2,rel}$; ll. 173–259).

$$
V_x = \phi U = 0.7\times314 = 219.9\ \mathrm{m/s}
$$

All the stage work is done in the rotor (no shaft work in a stator), and $V_{\theta1}=0$, so by Euler

$$
V_{\theta2} = \frac{\Delta h_{0,stage}}{U} = \frac{61\,500}{314} = 195.7\ \mathrm{m/s}
$$

$$
\beta_1 = \alpha_{1,rel} = \tan^{-1}\frac{0-314}{219.9} = -55.0^\circ,\qquad \beta_2 = \alpha_{2,rel} = \tan^{-1}\frac{195.7-314}{219.9} = -28.3^\circ
$$

About 27° of turning: "maybe a bit less than you might expect from a modern compressor… we might aim for maybe 45 or 50 degrees" (ll. 254–256).

**(c) A 1/10-scale test at ambient outlet pressure.** Match the Mach number, $\phi$ and $\psi$; accept a Reynolds number about 10 times lower (weak effect, ll. 303–320). Run with atmospheric pressure at outlet and a throttle valve at inlet, so $p_{023,t}=101.325/15=6.76$ kPa. The throttle is adiabatic with no work, so $T_0$ is unchanged through it (ll. 365–374): $T_{023,t}=298$ K.

Matching the Mach number fixes $V_x/\sqrt{c_pT_{023}}$:

$$
V_{x,t} = 219.9\sqrt{\frac{298}{330}} = 209.0\ \mathrm{m/s},\qquad U_t = \frac{V_{x,t}}{\phi} = 298.5\ \mathrm{m/s}
$$

Matching $\psi$ for the whole machine: $\Delta h_{0,t}/\Delta h_0=(U_t/U)^2=0.903$.

Matching the non-dimensional mass flow $\dot m\sqrt{c_pT_{01}}/(D^2p_{01})$:

$$
\frac{\dot m_t}{\dot m} = \left(\frac{D_t}{D}\right)^2\frac{p_{023,t}}{p_{023}}\sqrt{\frac{T_{023}}{T_{023,t}}} = 0.01\times\frac{6.76}{40}\times\sqrt{\frac{330}{298}} = 1.78\times10^{-3}
$$

Power:

$$
\frac{\dot W_t}{\dot W} = 1.78\times10^{-3}\times0.903 = 1.60\times10^{-3},\qquad \dot W_t = 5\ \mathrm{MW}\times1.60\times10^{-3} = 8.0\ \mathrm{kW}
$$

"You can't run it out of a conventional plug, but with a simple three-phase power supply" it is affordable (l. 431).

> [!check] Numerical checks
> - The lecture's 430 kJ/kg, 6.23, 69 and 61 kJ/kg, −55° and −28°, 209 and 298.5 m/s, $1.78\times10^{-3}$, $1.6\times10^{-3}$ and 8.02 kW are all reproduced.
> - The model must spin at $U_t/r_t=298.5/0.03=9950$ rad/s, about 95,000 rpm, nearly ten times the full-size speed: small models of high-Mach machines run very fast.
> - The lecture estimates the Reynolds number falls "by a factor of 10" from the size alone (l. 433). The throttled inlet also cuts the density: $\rho\propto p_0/T_0$ gives $(6.76/40)\times(330/298)=0.19$. With $U_t/U=0.95$ and $D_t/D=0.1$, $Re_t/Re\approx0.19\times0.95\times0.1=0.018$, about 55 times lower. The Reynolds-number mismatch is the main uncertainty in the test.

---

## 3. Specific speed (Lecture 26)

To choose the machine type before its size is known, we need a group without $D$. Eliminate $D$ between $\phi\sim Q/(\Omega D^3)$ and $\psi\sim\Delta h/(\Omega^2D^2)$:

$$
\phi^{1/2}\propto\frac{Q^{1/2}}{\Omega^{1/2}D^{3/2}},\qquad \psi^{3/4}\propto\frac{(\Delta h)^{3/4}}{\Omega^{3/2}D^{3/2}}
$$

Divide; the $D^{3/2}$ cancels:

$$
\boxed{N_s = \frac{\phi^{1/2}}{\psi^{3/4}} = \frac{\Omega\,Q^{1/2}}{(\Delta p/\rho)^{3/4}}}
$$

with $\Omega$ in rad/s and SI units; for compressible machines use the inlet volume flow and $\Delta h_0$.

| $N_s$ | Optimum machine |
|---|---|
| very low | positive displacement |
| below about 0.4 | centrifugal / radial: short blades, large radius ratio |
| about 0.4–2 | mixed flow |
| above about 2 | axial, propellers: few, long, widely spaced blades |

Low-$\phi$, high-$\psi$ machines (a vacuum-cleaner fan, a car supercharger) sit at low $N_s$; high-$\phi$, low-$\psi$ machines (wind turbine, aircraft or ship propeller) at high $N_s$ (L26, ll. 20–93). The lecture's chart runs from $N_s\approx0.05$ to 20: Pelton wheels (cups on a wheel, very high turning) at the low end of turbines; positive-displacement machines (Roots or gear pumps, as in car superchargers) at the low end of compressors; then centrifugal, then axial, which reach the highest efficiencies; fans and propellers at the top. "Specific speed isn't really very intuitively meaningful to me. I think of it more as a shape factor" (ll. 46–51). $N$ is often rotations per second; $\Omega$ is rad/s. Aero engines use axial machines because they are the most efficient at high flow and can be stacked into many stages; multistage centrifugal compressors lose pressure in the ducting between stages.

> [!warning] Slide note (L26, l. 43)
> On the specific-speed chart the lecturer notes that a curve has "migrated a little bit, but it should be over the $D^{3/2}$" — the elimination of $D$ above is what fixes the exponents.

---

## 4. Characteristic maps (Lecture 26)

![[prop_compressor_map.png|680]]

### High-speed compressor

- Plot $p_{02}/p_{01}$ and $\eta$ against $\dot m\sqrt{T_{01}}/p_{01}$, with lines of constant $N/\sqrt{T_{01}}$.
- Each speed line is what you get by holding the speed and opening a throttle downstream: the flow rises and the pressure ratio falls (L26, ll. 199–209).
- At low flow (high incidence) each speed line ends at the surge/stall line. With nothing physically holding the pressure in, a stalled compressor lets the high-pressure combustor gas surge out of the front of the engine: a loud bang (the pressure difference can drive supersonic flow and a blast wave) and probably a flame-out (L25, ll. 108–115; L26, ll. 225–231). Never operate beyond it. Surge itself "isn't something we really get into in this module" (L26, l. 258).
- At high flow the lines turn vertical at choke, where the pressure ratio collapses (L26, ll. 233, 266: "high flow rate, you get choking… low flow rate, it's going to stall", after the lecturer swaps them by mistake).
- At high speed the lines become steep.
- Per stage, the pressure-ratio limit is about 2 (axial, shocks) or about 10 (centrifugal). Overall, $\pi=\pi_{stage}^n$ for equal stages.
- Multistage compressors with an overall ratio above about 10 are hard to start: at low speed the volume flow is mismatched to the annulus areas designed for high density, and the mismatch "snowballs" from stage to stage. Hence multiple spools, variable stators and bleed valves.

### Turbine

- Stable boundary layers allow a high pressure ratio per stage, so the blade rows choke.
- If the first stator (a converging nozzle) chokes, nothing the rotor does downstream can change the flow, so the maximum non-dimensional flow is the same at every speed. If choking happens further downstream, the choked flow varies with speed (L26, ll. 268–281).
- The non-dimensional flow is then constant, independent of pressure ratio.
- The mass flow can then be changed only through the inlet $p_0$ and $T_0$ (for example, throttling a steam turbine, [[SESA2023 Problem Sheet 9 Solutions]] Q9.5).
- No instability; a stage can take about 4:1, and a machine about 100:1 overall.

### Isentropic nozzle

A nozzle has a characteristic too: the non-dimensional flow rises with pressure ratio until it chokes at $p/p_0=0.528$ (W03).

Strictly, $\dot m\sqrt{T_{01}}/p_{01}$ and $N/\sqrt{T_{01}}$ have units, because $D$, $c_p$ and $R$ have been dropped for a single machine on a single gas (L26, ll. 290–295). They are still called the non-dimensional flow and speed; some maps use corrected flow and speed referred to standard-day conditions instead.

---

## 5. Propellers and actuator disk (examined 2023-24, not lectured this year)

The 2025-26 lectures mention propellers only as the high-$N_s$ end of the machine family (L26). The 2023-24 paper examined them:

- the advance ratio $J=V_\infty/(nD)$;
- velocity triangles at cruise;
- actuator-disk theory, $V_{disk}=\tfrac12(V_\infty+V_j)$.

See [[Actuator Disk Theory]] and [[SESA2023 Exam 2023-24 Solutions]] Q4. Treat as background unless the 2025-26 problem sheets cover it.

---

## 6. Problem-solving workflow

1. Overall work from the pressure ratio and efficiency (W02), or from the power and mass flow.
2. Blade speed $U=\Omega r_m$ with $\Omega$ in rad/s.
3. Stage count $n\ge\Delta h_{0,overall}/(\psi_{max}U^2)$; round up; recompute the actual $\psi$.
4. Blade angles: $V_x=\phi U$, Euler for $V_{\theta2}$, then $\alpha_{rel}$ for zero incidence and deviation.
5. Similarity: list what is matched (Mach number or $ND/\sqrt{T_0}$, $\phi$, $\psi$, non-dimensional flow) and what is not (Re); scale speed, flow and power.
6. Maps: locate the operating point; say which way surge and choke lie.

## Terminology and alternative names

| Course term | Also called | Where the course uses it | Note |
|---|---|---|---|
| flow coefficient $\phi$ | — | handout, L25 | $V_x/U$. |
| stage loading coefficient $\psi$ | work coefficient, loading coefficient | handout, L25, L27 | $\Delta h_0/U^2$; some texts use $\psi=\Delta h_0/(\tfrac12U^2)$, double the course value. |
| specific speed $N_s$ | shape factor, $\Omega_s$ | handout, L26 | Dimensionless only in consistent units (rad/s). |
| characteristic | map | handout, L26 | |
| non-dimensional mass flow / speed | corrected flow / speed, $\dot m\sqrt\theta/\delta$, $N/\sqrt\theta$ | handout, L26 | |
| surge / stall line | surge margin boundary | L26 | |
| midline blade speed $U_m$ | mean-line, meridional | L27, l. 143 | The lecture calls it "meridional"; strictly it is the mid-span (mean-radius) speed. |
| Smith chart | — | handout | turbine efficiency on $(\phi,\psi)$. |

## Links

- Parent: [[SESA2023 Propulsion Hub]] · Previous: [[SESA2023 W08 - Turbomachinery Principles - Euler Equation and Velocity Triangles]] · Next: [[SESA2023 W10 - Rocket Performance, Staging and Power Cycles]]
- Thermofluids foundation: [[SESA1016 T6 - Dimensional Analysis and Similarity]]
- Non-dimensional mass flow and choking: [[SESA2023 W03 - Compressible Flow, Normal Shocks and Nozzles#Mass flow rate|W03]]
- Worked sheet: [[SESA2023 Problem Sheet 9 Solutions]] · Formula list: [[SESA2023 Formula Sheet]]
- Exams: [[SESA2023 Exam 2020-21 Solutions]] Q4 (LPT stage count, geared fan), [[SESA2023 Exam 2021-22 Solutions]] Q4 (map sketch, scaling, throttling to surge), [[SESA2023 Exam 2022-23 Solutions]] Q4(i–ii)

## Sources

- `Week 09 - Turbomachinery Characteristics.pdf` (handout, E. Richardson) and `Week 09 - Turbomachinery Characteristics - Lecture Slides.pdf`; Smith (1965) turbine efficiency chart.
- Transcripts (line numbers refer to these files): L25 `SESA2023 Lecture 25 - Turbomachinery Characteristics.txt` (21 Apr: coefficients, stage count, Buckingham π); L26 `SESA2023 Lecture 26 - Turbomachinery Characteristics.txt` (21 Apr: specific speed, maps); L27 `SESA2023 Lecture 27.txt` (24 Apr: extended HP-compressor design example).

## Self-study tasks

Tasks marked *(set)* were set or explicitly pointed to in the Week 9 lectures; the rest are suggested, not lecturer-set. Attempt each closed-book, then check against the linked section.

### Core

- [ ] *(set)* Lecture 27 design exercise: stage count, first-rotor angles and the 1/10-scale test power; "put the numbers in, which you can do at home" (L27, l. 135). Targets 430 kJ/kg, 7 stages, −55° and −28°, 8.0 kW. → [[#Worked example – the Lecture 27 HP compressor design]]
- [ ] *(set)* Stage count for the handout's turbojet compressor. Target 6 stages. → [[#Worked example – stage count for a turbojet compressor]]
- [ ] *(set)* Work [[SESA2023 Problem Sheet 9 Solutions|Problem Sheet 9]] and the summative Week 9 quiz (L26, ll. 309–311).
- [ ] *(set)* Sketch a compressor map and a turbine map, labelling surge, choke, the speed lines and the efficiency islands: "being able to sketch out a plot like this and label the different phenomena of choking and stall would be something you'd want to be able to do" (L26, ll. 251–252). → [[#4. Characteristic maps (Lecture 26)]]
- [ ] Read the Smith chart example: why halving the stages costs about 6 points of efficiency. → [[#Worked example – reading the Smith chart (L25, ll. 257–301)]]
- [ ] Give both interpretations of the flow coefficient (design stagger and off-design incidence). → [[#Definitions]]

### Further practice

- [ ] Derive the incompressible and compressible dimensionless groups with Buckingham π. → [[#Incompressible machines (pumps, fans, hydraulic turbines)]] · [[#Compressible machines]]
- [ ] Derive $N_s=\phi^{1/2}/\psi^{3/4}$ by eliminating $D$. → [[#3. Specific speed (Lecture 26)]]
- [ ] Explain why a turbine stage can take about four times the loading of a compressor stage. → [[#Limits on stage loading]]
- [ ] Explain why a high-ratio multistage compressor is hard to start and list three fixes. → [[#High-speed compressor]]
- [ ] Find the model rotational speed for the Lecture 27 test. Target about 95,000 rpm. → [[#Worked example – the Lecture 27 HP compressor design]]
