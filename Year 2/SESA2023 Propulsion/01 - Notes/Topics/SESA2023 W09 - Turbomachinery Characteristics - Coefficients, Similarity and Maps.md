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
aliases: ["Turbomachinery characteristics", "Compressor maps"]
date: 2026-09-24
status: complete
parent: ["[[SESA2023 Propulsion Hub]]"]
prerequisites: ["[[SESA2023 W08 - Turbomachinery Principles - Euler Equation and Velocity Triangles]]"]
next_topics: ["[[SESA2023 W10 - Rocket Performance, Staging and Power Cycles]]"]
key_concepts: ["[[Flow and Work Coefficients]]", "[[Dimensional Analysis of Turbomachines]]", "[[Specific Speed]]", "[[Compressor and Turbine Characteristics]]", "[[Compressor Stall and Surge]]", "[[Actuator Disk Theory]]"]
tutorial_sheets: ["[[SESA2023 Problem Sheet 9 Solutions]]"]
sources: ["02 - Sources/Lectures/Week 09 - Turbomachinery Characteristics.pdf", "02 - Sources/Lectures/Week 09 - Turbomachinery Characteristics - Lecture Slides.pdf"]
---

# SESA2023 W09 - Turbomachinery Characteristics - Coefficients, Similarity and Maps

> [!abstract] Summary
> Turbomachine behaviour collapses onto a few dimensionless groups:
> - The **flow coefficient** $\phi = V_x/U$ sets the incidence.
> - The **stage loading** $\psi = \Delta h_0/U^2$ sets the flow turning. Its limit ($\psi\lesssim0.4$–0.65 for compressors, up to 2.5 for turbines) fixes the **number of stages**.
> - **Dimensional analysis** (Buckingham π) says geometrically similar machines at equal groups are dynamically similar. This lets model tests scale to full size.
> - **Specific speed** $N_s = \phi^{1/2}/\psi^{3/4}$ picks the machine *shape* (radial or axial) before its size is known.
> - High-speed machines are described by **characteristic maps** of $p_{02}/p_{01}$ and $\eta$ against $\dot m\sqrt{T_{01}}/p_{01}$ at constant $N/\sqrt{T_{01}}$. Compressors are bounded by **surge** and **choke**. Turbines choke and run at nearly constant non-dimensional flow.

## Key Concepts
- [[Flow and Work Coefficients]] · [[Dimensional Analysis of Turbomachines]] · [[Specific Speed]] · [[Compressor and Turbine Characteristics]] · [[Compressor Stall and Surge]]

---

## 1. Flow and work coefficients

$$
\phi = \frac{V_x}{U},\qquad \psi = \frac{|\Delta h_0|}{U^2} = \frac{\Delta V_\theta}{U}\ (\text{constant radius})
$$

- **Low $\phi$** means highly staggered blades with near-tangential relative flow. **High $\phi$** means low stagger. For a *fixed* blade, $\phi$ below design gives positive incidence (towards stall), and above design gives negative incidence (towards choke).
- **High $\psi$** means more turning per stage and fewer stages, at lower efficiency.
  - Compressors: separation limits it. Upper limit $\psi\le0.65$, typical 0.35–0.5.
  - Turbines: high-Mach and shock losses limit it. $\psi\le2.5$.
- **Smith chart** (turbines): efficiency contours on $(\phi,\psi)$. Raising $\psi$ lowers $\eta$, and the best $\phi$ rises with $\psi$.
- Fan-tip relative Mach number is kept under 1.6 (noise, bird strike). The axial Mach number at the fan face is about 0.6.

$$
n_{stages}\ge\frac{\psi_{overall}}{\psi_{stage,max}} = \frac{\Delta h_{0,overall}}{\psi_{max}U^2}\quad\text{(round **up**)}
$$

> [!example] Turbojet first stage at sea level, M 0.8, M 0.6 into the rotor, $\phi = 0.55$, no IGV
> - $T_{02} = 288(1.128) = 324.9$ K.
> - $V_x/\sqrt{c_pT_{02}} = \sqrt{\gamma-1}\,M(1+\tfrac{\gamma-1}{2}M^2)^{-1/2} = 0.3665$, so $V_x = 209.4$ m/s and $U = V_x/\phi = 380.8$ m/s.
> - Overall compressor pressure ratio 10, isentropic, $\psi_{max} = 0.4$: $\Delta h_{0,overall} = c_pT_{02}(10^{0.2857}-1) = 303.9$ kJ/kg, while $\Delta h_{0,stage}\le0.4(380.8)^2 = 58.0$ kJ/kg.
> - $n = 5.24$, so **6 stages**.

## 2. Dimensional analysis (Buckingham π)
**Mental experiment**: which variables change the streamline pattern? If the streamline patterns (hence the velocity triangles) are similar, **all** dimensionless groups match.

### Incompressible machines (pumps, fans, hydraulic turbines)
The variables are $Q$, $\Omega$, $D$, $\rho$, $\mu$: 5 variables and 3 dimensions give **2 groups**.

$$
\phi\sim\frac{Q}{\Omega D^3},\qquad Re = \frac{\rho\Omega D^2}{\mu}\quad\Rightarrow\quad \frac{\Delta p}{\rho\Omega^2D^2},\ \eta,\ \frac{\dot W}{\rho\Omega^3D^5} = fn(\phi,Re)
$$

For $Re>2\times10^5$ the boundary layers are thin and turbulent, so Re has a weak effect: a factor of 10 in Re changes $\eta$ by only 1–2 %. This is justified by **experiment**, not theory. Liquids add a cavitation group involving the vapour pressure.

### Compressible machines
The variables are $\dot m$, $\gamma$, $c_pT_{01}$, $D$, $N$, $p_{01}$ ($\mu$ is neglected). The speed of sound enters through $c = \sqrt{(\gamma-1)c_pT}$.

$$
\gamma,\quad \frac{\dot m\sqrt{c_pT_{01}}}{D^2p_{01}},\quad \frac{ND}{\sqrt{c_pT_{01}}}\quad\Rightarrow\quad \frac{p_{02}}{p_{01}},\ \frac{T_{02}}{T_{01}},\ \eta,\ \frac{\dot W}{\dot mc_pT_{01}} = fn\left(\frac{\dot m\sqrt{c_pT_{01}}}{D^2p_{01}},\frac{ND}{\sqrt{c_pT_{01}}}\right)
$$

For one machine running on one gas, $D$, $c_p$ and $\gamma$ drop out, leaving $\dot m\sqrt{T_{01}}/p_{01}$ and $N/\sqrt{T_{01}}$. These are often "corrected" to standard conditions: $\dot m\sqrt{\theta}/\delta$ and $N/\sqrt\theta$.

**Using similarity** (typical exam steps):
1. Hold $N D/\sqrt{T_{01}}$ constant to get the test speed.
2. Hold $\dot m\sqrt{T_{01}}/(D^2p_{01})$ constant to scale the flow.
3. Hold $\dot W/(\dot mc_pT_{01})$ constant to scale the power.

These are [[SESA2023 Problem Sheet 9 Solutions]] Q9.3–9.4 and [[SESA2023 Exam 2021-22 Solutions]] Q4(ii–iii).

## 3. Specific speed (shape factor)
We need a group without $D$, because the size is not yet known:

$$
N_s = \frac{\phi^{1/2}}{\psi^{3/4}} = \frac{Q^{1/2}\,\Omega}{(\Delta p/\rho)^{3/4}}\quad(\Omega\text{ in rad/s, SI units; inlet volume flow for compressible machines})
$$

| $N_s$ | Optimum machine |
|---|---|
| Very low | Positive displacement |
| < ~0.4 | **Centrifugal / radial**: short blades, large radius ratio |
| ~0.4–2 | Mixed flow |
| > ~2 | **Axial**, propellers: few, long, widely spaced blades |

Low-$\phi$, high-$\psi$ machines (vacuum-cleaner fan) sit at low $N_s$. High-$\phi$, low-$\psi$ machines (windmill, propeller) sit at high $N_s$. Aero engines use axial machines because they are the most efficient at high flow and can be stacked in stages. Multistage centrifugal compressors lose pressure between stages.

## 4. Characteristic maps
![[prop_compressor_map.png|680]]

**High-speed compressor**:
- Plot $p_{02}/p_{01}$ and $\eta$ against $\dot m\sqrt{T_{01}}/p_{01}$, with lines of constant $N/\sqrt{T_{01}}$.
- At **low flow** (high incidence) each speed line ends at the **surge/stall line**, where violent flow oscillation occurs. Never operate beyond it.
- At **high flow** the lines turn **vertical** at choke, where the pressure ratio collapses.
- At high speed the lines get steep.
- Per stage, the pressure-ratio limit is about 2 (axial, shocks) or about 10 (centrifugal). Overall, $\pi = \pi_{stage}^n$.
- Multistage compressors with overall pressure ratio above about 10 are hard to **start**, because at low speed the volume flow is mismatched to the annulus area and the stages "snowball". Hence **multiple spools**, variable stators and bleed valves.

**Turbine**:
- Stable boundary layers allow a high pressure ratio per stage, so the blade rows **choke**.
- The non-dimensional flow becomes **constant**, independent of speed and pressure ratio.
- The mass flow is then varied only through the inlet $p_0$ and $T_0$ (e.g. throttling a steam turbine).
- There is no instability. A stage can take about 4:1, and a machine about 100:1 overall.

**Isentropic nozzle**: it has a characteristic too. The non-dimensional flow rises with pressure ratio until it chokes at $p/p_0 = 0.528$.

## 5. Propellers and actuator disk (examined 2023-24)
The Week 9 material stops at maps, but the 2023-24 paper examined **propellers**:
- the advance ratio $J = V_\infty/(nD)$;
- velocity triangles at cruise;
- actuator-disk theory, $V_{disk} = \tfrac12(V_\infty+V_j)$.

See [[Actuator Disk Theory]] and [[SESA2023 Exam 2023-24 Solutions]] Q4.

## Links
- Parent: [[SESA2023 Propulsion Hub]] · Previous: [[SESA2023 W08 - Turbomachinery Principles - Euler Equation and Velocity Triangles]] · Next: [[SESA2023 W10 - Rocket Performance, Staging and Power Cycles]]
- Thermofluids foundation: [[SESA1016 T6 - Dimensional Analysis and Similarity]]
- Worked sheet: [[SESA2023 Problem Sheet 9 Solutions]]
- Exams: [[SESA2023 Exam 2020-21 Solutions]] Q4 (LPT stage count, geared fan), [[SESA2023 Exam 2021-22 Solutions]] Q4 (map sketch, scaling, throttling to surge), [[SESA2023 Exam 2022-23 Solutions]] Q4(i–ii)

## Sources
- Week 9 handout (E. Richardson) and Lectures 25–26; Smith (1965) turbine efficiency chart
