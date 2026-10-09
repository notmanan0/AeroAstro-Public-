---
title: "SESA2023 W07 - Turbofan Architectures and Fan Pressure Ratio Selection"
module: "SESA2023 Propulsion"
type: topic
stream: "Section 3: Ramjets, Gas Turbines, Turbojets and Turbofans"
order: 7
tags:
  - sesa2023
  - turbofan
  - bypass-ratio
  - fan-pressure-ratio
  - engine-architecture
aliases: ["Turbofan design", "Fan pressure ratio"]
date: 2026-09-24
status: complete
parent: ["[[SESA2023 Propulsion Hub]]"]
prerequisites: ["[[SESA2023 W06 - Jet Engine Cycle Analysis - Brayton, Ramjet, Turbojet and Reheat]]"]
next_topics: ["[[SESA2023 W08 - Turbomachinery Principles - Euler Equation and Velocity Triangles]]"]
key_concepts: ["[[Bypass Ratio and Fan Pressure Ratio]]", "[[Propulsive Efficiency]]", "[[Turbojet]]", "[[Actuator Disk Theory]]"]
tutorial_sheets: ["[[SESA2023 Problem Sheet 8 Turbofans Solutions]]"]
sources: ["02 - Sources/Lectures/Week 06-07 - Jet Engines.pdf"]
---

# SESA2023 W07 - Turbofan Architectures and Fan Pressure Ratio Selection

> [!abstract] Summary
> Propulsive efficiency needs a **large mass flow with a small velocity increase**. The turbofan does this by using the core's surplus energy (via an LP turbine) to drive a fan that pushes a large **bypass** stream.
>
> The **fan pressure ratio (fpr)** is the fundamental design variable. It alone sets the bypass jet velocity, and hence $\eta_P$ and specific thrust. For a fixed core it sets the **bypass ratio**.
>
> Lower fpr improves bare-engine sfc, but the fan diameter grows, so nacelle drag and engine weight rise. The effective sfc therefore has a **minimum near fpr ≈ 1.5**, which is where current engines sit (bpr ≈ 10–12).

## Key Concepts
- [[Bypass Ratio and Fan Pressure Ratio]] · [[Propulsive Efficiency]] · [[Turbojet]]

---

## 1. Architectures (Lecture 20)

| Architecture | Example | Features |
|---|---|---|
| Turbojet (single spool) | RR Viper (target drones, trainers) | Light and cheap; high $V_j$; suits supersonic flight |
| Twin-spool turbojet | RR Olympus 593 (Concorde, M 2) | HP spool spins faster; better off-design operation and starting |
| Low-bpr turbofan | P&W JT8D (727/737, bpr 0.3–1.5) | First step to higher $\eta_P$ |
| High-bpr, 2-spool + booster | GE GEnx (bpr ≈ 9.5) | fpr × booster ≈ 2.5, HPC ≈ 20, OPR ≈ 45 |
| High-bpr, 3-spool | RR Trent 1000 (bpr ≈ 9.5) | Fan ≈ 1.5, IPC ≈ 7, HPC ≈ 4; better off-design operation but more complex |
| Geared turbofan | P&W GTF/GT1524 (bpr 12) | A gearbox lets a small, fast LPT drive a slow, large fan; the gear efficiency is critical |
| Turboprop | | Very high effective bpr; propeller-tip Mach limits flight speed |
| Open rotor | CFM RISE | Rotor + stator to remove swirl; containment and noise are the challenges |
| Turbo-electric / distributed fans | NASA STARC-ABL, E-Thrust | Free choice of fan number and position; **boundary-layer ingestion** cuts wasted jet KE; heavy electrical machines |

- **Bypass ratio**: $BPR = \dot m_b/\dot m_c$.
- **Jet noise** scales roughly with $V_j^8$, so a low $V_j$ is also quiet.
- **Station numbering** (two-spool turbofan): 2 fan face; 13 bypass after the fan; 19 bypass nozzle exit; 23 core after fan/booster; 3 HPC exit; 4 HPT entry; 45 LPT entry; 5 LPT exit; 9 core nozzle exit.

## 2. Spool power balances
In steady operation the net shaft work on each spool is zero:

$$
\text{HP spool: }\dot m_c(h_{03}-h_{023}) = (\dot m_c+\dot m_f)(h_{04}-h_{045})
$$

$$
\text{LP spool: }\dot m_b(h_{013}-h_{02})+\dot m_c(h_{023}-h_{02}) = (\dot m_c+\dot m_f)(h_{045}-h_{05})
$$

$$
\Rightarrow\quad BPR = \frac{(1+f)(h_{045}-h_{05})-(h_{023}-h_{02})}{h_{013}-h_{02}}
$$

## 3. Fan pressure ratio sets the bypass jet (Lecture 21)
The intake flow to 2 is isentropic, so $T_{02} = T_a(1+\tfrac{\gamma-1}{2}M^2)$ and $p_{02}/p_a = (T_{02}/T_a)^{\gamma/(\gamma-1)}$. Then

$$
T_{013} = T_{02}\left(1+\frac{fpr^{(\gamma-1)/\gamma}-1}{\eta_f}\right),\qquad V_{jb} = \sqrt{2c_pT_{013}\left[1-\left(\frac{p_a}{fpr\,p_{02}}\right)^{(\gamma-1)/\gamma}\right]}
$$

For a given flight condition and fan efficiency, $V_{jb}$ depends **only on fpr**, and so does $\eta_P$.

**Design procedure** (core fixed by OPR and TET):
1. Choose the fpr, which gives $V_{jb}$.
2. Choose the core jet velocity. **$V_{jc} = V_{jb}$** maximises $\eta_P$ and minimises noise.
3. Iterate the LPT pressure ratio $p_{045}/p_{05}$ until $V_{jc}$ matches.
4. The LP spool balance then gives the **BPR**.

**Specific thrust** is a better single descriptor than bpr:

$$
X = \frac{F_N}{\dot m_{air}} = V_j-V
$$

> [!example] PS8 Q8.3: M 0.78 at 35,000 ft, OPR 45, TET 1500 K, all efficiencies 0.9
>
> | fpr | $V_j$ (m/s) | $\eta_P$ | bpr | $X = F_N/\dot m_a$ (N s/kg) | sfc bare (g/s/kN) | sfc with drag |
> |---|---|---|---|---|---|---|
> | 1.4 | 323 | 0.834 | 13.8 | 91.9 | 12.16 | 13.52 |
> | 1.5 | 340 | 0.810 | 11.2 | 108.7 | 12.47 | 13.63 |
> | 1.6 | 355 | 0.789 | 9.4 | 124.0 | 12.75 | 13.78 |
>
> A pure turbojet with the same core (PS8 Q8.2) has $V_j = 975$ m/s, $\eta_P = 0.38$ and sfc = 22.2 g/s/kN.

![[prop_turbofan_fpr.png|760]]

**Trends**:
- Lower fpr gives a higher bpr for a fixed core, and needs more LPT work.
- Reducing fpr from 1.8 to 1.5 cuts sfc by about 6 %, but specific thrust falls. The air mass flow must rise by about 36 % for the same thrust.

## 4. Nacelle drag and engine weight
- **Bare vs installed**: the nacelle and bypass-duct losses scale as $D_{nac}\propto A_w\rho V^2\propto\dot mV = kV(F_N/X)$. This gives $F_{N,eff} = F_{N,bare}(1-kV/X)\approx F_{N,bare}(1-9.25/X)$, roughly a 10 % reduction. Low fpr (low $X$) is hit hardest.
- **Weight**: engine weight scales as $W_{eng}\propto d^{2.4}$, about 12 t for a 3 m fan including nacelle and pylon. The extra lift needed costs drag, so $F_{N,corr} = F_{N,eff}-W_{eng}/(L/D)$ (with $L/D = 21.6$).
- **Result**: a true optimum appears. There is a large penalty for fpr < 1.5, and huge fans may not fit under the wing or in freighters. Lower fpr is quieter.
- **fpr ≈ 1.5** matches current industry choices. The RB211, launched in 1971 at bpr 5 and fpr 1.5, grew from 44,000 to 60,000 lbf over its life by *raising* fpr and accepting lower $\eta_P$.

> [!tip] Exam angle
> "Explain how a greater bypass ratio affects fpr and fuel consumption" ([[SESA2023 Exam 2021-22 Solutions]] Q3(iii)).
> - At fixed OPR and core, a higher bpr needs a lower fpr, giving lower $V_j$, higher $\eta_P$ and lower bare sfc.
> - It also needs a larger fan, with more nacelle drag and weight, which offset part of the gain.
> - It needs more LPT work (more stages, or a gearbox).

## Links
- Parent: [[SESA2023 Propulsion Hub]] · Previous: [[SESA2023 W06 - Jet Engine Cycle Analysis - Brayton, Ramjet, Turbojet and Reheat]] · Next: [[SESA2023 W08 - Turbomachinery Principles - Euler Equation and Velocity Triangles]]
- Worked sheet: [[SESA2023 Problem Sheet 8 Turbofans Solutions]]
- Exams: [[SESA2023 Exam 2013-14 Solutions]] Q3 (M 2 turbofan), [[SESA2023 Exam 2020-21 Solutions]] Q4 (geared LPT stage count), [[SESA2023 Exam 2021-22 Solutions]] Q3, [[SESA2023 Exam 2023-24 Solutions]] Q3 (electric ducted fan, BLI)

## Sources
- Weeks 6–7 handout §7 and Lectures 20–21
