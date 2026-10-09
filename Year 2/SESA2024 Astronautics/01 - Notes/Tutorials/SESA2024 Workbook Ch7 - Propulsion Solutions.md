---
title: "SESA2024 Workbook Ch7 - Propulsion Solutions"
module: "SESA2024 Astronautics"
type: tutorial
stream: "Spacecraft Subsystems"
tags:
  - sesa2024
  - tutorial-solutions
  - propulsion
  - electric-propulsion
sheet: "Problem Sheet Workbook 2025-26, Chapter 7 (pp. 25-35)"
theory_notes: ["[[SESA2024 07 - Spacecraft Propulsion]]"]
key_concepts: ["[[Tsiolkovsky Rocket Equation]]", "[[Rocket Performance Parameters]]", "[[Electric Propulsion Sizing]]", "[[Chemical Propulsion Systems]]"]
status: complete
sources: ["02 - Sources/Lectures/SESA2024 Astronautics PROBLEM SHEET WORKBOOK 2025-26 V1.1.pdf"]
---

# SESA2024 Workbook Ch7 - Propulsion Solutions

> [!abstract] Sheet Info
> Twelve questions. Q1–9 are definitions and trade-offs; Q10–12 are electric-propulsion sizing. Use $g_0 = 9.81$ m/s² throughout. Every number below was reproduced in Python ✔. The Pluto orbiter (Q12) is the one to master, because the same method answers 2024/25 exam **A2**.

## Theory Links
- [[SESA2024 07 - Spacecraft Propulsion]]
- Concepts: [[Tsiolkovsky Rocket Equation]] · [[Rocket Performance Parameters]] · [[Electric Propulsion Sizing]] · [[Chemical Propulsion Systems]]

---

## Q1: Show $I_{sp} = V_{ex}/g_0$, and why $I_{sp}$ matters
The total impulse, with $T = \sigma V_{ex}$ and $\sigma = -dM/dt$, is

$$
I = \int_0^tT\,dt = \int_0^t-\frac{dM}{dt}V_{ex}\,dt = -V_{ex}\int_{M_0}^{M_b}dM = V_{ex}(M_0-M_b) = V_{ex}M_e
$$

Specific impulse is **impulse per unit weight of propellant**:

$$
I_{sp} = \frac{I}{M_eg_0} = \frac{V_{ex}}{g_0}\quad\Rightarrow\quad V_{ex} = g_0I_{sp}
$$

**Why it matters**: substitute into the rocket equation, $\Delta V = g_0I_{sp}\ln(M_0/M_b)$. For a fixed mass ratio this is $\Delta V = K\,I_{sp}$, so **$\Delta V$ is directly proportional to $I_{sp}$**. $I_{sp}$ measures how efficiently propellant mass is converted into vehicle momentum.

## Q2: How a monopropellant hydrazine thruster works
1. Liquid N₂H₄ is fed under pressure. When firing is commanded, an electrically actuated valve opens.
2. Propellant passes through an injector onto a **catalytic bed** (platinum/iridium on a large-area aluminium-oxide substrate).
3. The **exothermic** decomposition produces hot N₂, NH₃ and H₂ gas.
4. The gas expands through a nozzle, giving thrust with $I_{sp} \approx 230$ s. The lecture gives about 240 s, or 290 s with power augmentation, and thrust of 1–10 N.

## Q3: Two sources of thrust

$$
T = \underbrace{\sigma V_e}_{\text{impulse (momentum) thrust}}+\underbrace{(P_e-P_a)A_e}_{\text{pressure thrust}}
$$

- **Impulse thrust** comes from the momentum flow of the exhaust.
- **Pressure thrust** comes from the difference between exit pressure and ambient pressure across the nozzle exit plane.

See [[Thrust Equation]].

## Q4: Hypergolic
A fuel and oxidiser that **ignite spontaneously on contact**, so no ignition system is needed. Example: MMH with N₂O₄ (the oxidiser).

## Q5: Three functions of spacecraft propulsion
1. **Primary**: orbit-transfer manoeuvres.
2. **Secondary**: orbit-control (station-keeping) manoeuvres.
3. **Secondary**: attitude control (including momentum dumping).

## Q6: Two advantages and two disadvantages of each system

| System | ✔ | ✘ |
|---|---|---|
| Liquid monoprop | low complexity; small minimum impulse | hazardous fuel handling; low $I_{sp}$ (~230 s) |
| Liquid biprop | restartable (multiple burns); higher $I_{sp}$ (~310 s MMH/N₂O₄, ~450 s LOX/LH₂) | complex feed system (hypergols must not mix early); hazardous handling |
| Solid | low complexity; easy storage | one firing only; low $I_{sp}$ (~260 s) |
| Cold gas | low complexity; tiny minimum impulse; easy handling (N₂) | very low $I_{sp}$ (~50 s); low total impulse |
| Ion | very high $I_{sp}$ (~4000 s); high $\Delta V$ capability | high electrical power (with system impacts); possible contamination by propellant |
| Nuclear | high $I_{sp}$ (~1000 s); high thrust for long durations | not "green"; radiation hazard |

## Q7: Highest $I_{sp}$
**Ion** propulsion (2000–6000 s).

## Q8: Which could launch payloads to LEO?
**Liquid bipropellant** and **solid**. Nuclear is possible in principle but has not been demonstrated. Launch needs thrust greater than weight, which rules out electric, cold-gas and monoprop.

## Q9: Why solids are not used for attitude control, and one exception
- They are **one-shot**: they cannot be stopped, restarted or pulsed.
- **Exception**: launch-vehicle attitude control using **gimballed solid-motor nozzles**. Vectoring the thrust about the centre of mass produces control torques, as on the Space Shuttle SRBs.

## Q10: Power for a 50 mN thrust (Table 1)
Method:
- $V_{ex} = g_0I_{sp}$;
- $\sigma = T/V_{ex}$;
- jet power $W_{jet} = \tfrac12\sigma V_{ex}^2 = \tfrac12TV_{ex}$;
- electrical power $W = W_{jet}/\eta$.

| Thruster | $I_{sp}$ (s) | $\eta$ | $V_{ex}$ (m/s) | $\sigma$ (kg/s) | $W$ |
|---|---|---|---|---|---|
| Resistojet | 700 | 0.9 | 6 867 | $7.281\times10^{-6}$ | **≈ 190 W** |
| Arcjet | 1 500 | 0.3 | 14 715 | $3.398\times10^{-6}$ | **≈ 1 230 W** |
| Ion | 5 000 | 0.75 | 49 050 | $1.019\times10^{-6}$ | **≈ 1 640 W** |

> [!tip] Shortcut
> $W = TV_{ex}/(2\eta) = Tg_0I_{sp}/(2\eta)$. For a fixed thrust, **power scales with $I_{sp}$**, so high-$I_{sp}$ thrusters are power-hungry.

**System implications**:
- The power overhead is large for arcjet and ion.
- It drives power-subsystem mass and solar-array size, and therefore the configuration.
- It also affects thermal design (dissipating $(1-\eta)W$) and long burn times.

## Q11: $\Delta V/V_c$ against $V_{ex}/V_c$ for $M_p/M_0$ = 0.1 and 0.5; why a maximum?
Equation (7.15), with $x = V_{ex}/V_c$ and $p = M_p/M_0$:

$$
\frac{\Delta V}{V_c} = x\ln\left[\frac{1+x^2}{p+x^2}\right]
$$

![[ast_ep_optimisation.png|650]]

| $M_p/M_0$ | optimum $V_{ex}/V_c$ | peak $\Delta V/V_c$ |
|---|---|---|
| 0.1 | 0.63 | 0.651 |
| 0.25 | 0.74 | 0.490 |
| 0.5 | 0.85 | 0.291 |

**Why a maximum**:
- Raising $V_{ex}$ saves propellant.
- But the required power grows as $V_{ex}^2$, and so does the power-plant mass $M_W$. That cuts acceleration and eventually the achievable $\Delta V$.
- At low $V_{ex}$ the rocket equation starves the vehicle of propellant.
- So an EP system should operate **near the peak**: choose $V_{ex}$ to suit the mission $\Delta V$ and payload fraction.

## Q12: Pluto orbiter by electric propulsion
**Given**: $\Delta V$ = 17 km/s, $M_p/M_0$ = 0.1, $t_b$ = 2 years = $6.31152\times10^7$ s, $M_0$ = 3000 kg, $\eta$ = 1.

**Why not chemical?** With a typical $V_{ex}\approx3$ km/s:

$$
\frac{M_e}{M_0} = 1-e^{-17/3} = 0.9965
$$

Almost the whole vehicle would be propellant, which is not feasible.

**Step 1: choose the optimum.** From Q11, the peak for $p = 0.1$ is at $V_{ex}/V_c\approx0.65$ with $\Delta V/V_c\approx0.65$ (the equality is a coincidence). So

$$
V_c = \frac{17\,000}{0.65} = 26\,154\ \text{m/s},\qquad V_{ex} = 0.65V_c = 17\,000\ \text{m/s},\qquad I_{sp} = \frac{17\,000}{9.81} = 1733\ \text{s}
$$

→ **ion thrusters** (arcjets reach at most 1500 s).

**Step 2: specific power.** From $V_c = \sqrt{2\eta\beta t_b}$:

$$
\beta = \frac{V_c^2}{2\eta t_b} = \frac{26\,154^2}{2(1)(6.31152\times10^7)} \approx 5.4\ \text{W/kg}
$$

This is low specific power over a long time a long way from the Sun, so **RTGs** are the appropriate source.

**Step 3: mass breakdown** ($x = 0.65$):

$$
M_p = 0.1(3000) = 300\ \text{kg},\qquad M_e = \frac{M_0-M_p}{1+x^2} = \frac{2700}{1.4225}\approx\mathbf{1900\ kg},\qquad M_W = x^2M_e\approx\mathbf{800\ kg}
$$

(Equivalently use (7.12) and (7.13): $M_e = (M_0-M_p)/(1+V_{ex}^2/2\eta\beta t_b)$.)

**Step 4: power, flow rate and thrust.**

$$
W = \beta M_W\approx\mathbf{4.3\ kW},\qquad \sigma = \frac{M_e}{t_b}\approx3.01\times10^{-5}\ \text{kg/s},\qquad T = \sigma V_{ex}\approx\mathbf{0.5\ N}
$$

> [!check] Python cross-check
> With the exact optimum $x^* = 0.633$ ($\Delta V/V_c = 0.651$) the results barely change: $V_c = 26\,114$ m/s, $\beta = 5.40$ W/kg, $M_e = 1898$ kg, $M_W = 802$ kg, $W = 4.34$ kW, $T = 0.51$ N.

## Sources
- Workbook 2025-26 Chapter 7 questions (p. 25–26) and solutions (p. 31–35)
- Chapter 7 lecture slides (7.1–7.16, EP examples p. 43–46)
