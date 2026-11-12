---
title: "SESA1015 A05 - Staging and Payload Fraction"
module: "SESA1015 Intro to Aero & Astro"
type: topic
stream: "Astronautics"
order: 17
tags:
  - sesa1015
  - astronautics
  - staging
  - payload-fraction
aliases: ["SESA1015 Astronautics 5", "Rocket Staging (SESA1015)"]
date: 2026-09-27
status: lectured
coverage: "Astronautics Part 3 (Launch Vehicles) pp. 22–27: payload fraction p and structural efficiency s, why staging follows from the single-stage limit, the variation of Delta-V with number of stages, the multistage rocket equation and the overall payload fraction P. Optimal split between identical stages derived as an extension."
parent: ["[[SESA1015 Intro to Aero & Astro Hub]]"]
prerequisites: ["[[SESA1015 A04 - Rocket Equation and Launch Performance]]"]
next_topics: ["[[SESA1015 A06 - Launch Vehicles, Systems and Interfaces]]"]
key_concepts: ["[[Rocket Mass Fractions]]", "[[Multistage Rocket Performance]]", "[[Tsiolkovsky Rocket Equation]]"]
tutorial_sheets: []
sources: ["02 - Sources/Astronautics/Astronautics - Part 3 - Launch Vehicles.pdf (pp. 22–27)", "02 - Sources/Astronautics/Astronautics - Part 1 - Introduction.pdf (p. 15, Saturn V)"]
---

# SESA1015 A05 - Staging and Payload Fraction

> [!abstract] Summary
> A single stage must carry its empty tanks and engines all the way to orbit, which caps its mass ratio at $(1+s)/s$ and makes orbit out of reach with ordinary propellants. Staging drops each set of tanks once it is empty, and the velocity increments of the stages add: $\Delta V_{ideal}=\sum_i V_{ex,i}\ln\frac{1+s_i}{p_i+s_i}$, where each stage's payload is everything above it and the overall payload fraction is the product $P=p_1p_2p_3\cdots$. Adding stages gives diminishing returns: for identical stages $\Delta V/V_{ex}$ tends to $\ln(1/P)/(1+s)$, and the best split gives every stage the same payload ratio $P^{1/N}$.

> [!summary]- Exam use: quick path
> - **Use it when:** a question gives stage masses (payload, structure, fuel) or ratios $p_i$, $s_i$ with exhaust velocities and asks for the total $\Delta V$, the lift-off mass for a payload, or why staging helps.
> - **Assumptions:** serial stages, each burnt to empty and dropped before the next ignites; constant $V_{ex,i}$; losses handled separately as in A04; $M_f$ is fuel mass.
> - **Method:** 1. Draw the stack and list $M_{pi}$, $M_{si}$, $M_{fi}$ for each stage, with $M_{pi}=M_{0,i+1}$. 2. Form $M_{0i}$ from the top down. 3. Compute $p_i=M_{pi}/M_{0i}$ and $s_i=M_{si}/M_{fi}$, or the burnout mass $M_{0i}-M_{fi}$ directly. 4. Sum $V_{ex,i}\ln(M_{0i}/M_{bi})$. 5. $P=M_{p,\text{top}}/M_{01}$; check it equals $\prod p_i$.
> - **Common mistakes:** taking a lower stage's payload as the satellite only, instead of the whole upper stack; dropping the stage's own structure from its burnout mass.
> - **Practise:** [[#Two identical stages to LEO]] · [[#A three-stage vehicle]]

A single-stage rocket wastes effort. By the end of its burn most of what it is accelerating is empty tank and engine, mass that has finished its job but still has to be pushed to orbital speed. The consequence ([[SESA1015 A04 - Rocket Equation and Launch Performance|A04]]): with a structure as light as $s=0.1$ and no payload at all, a single stage needs an exhaust velocity of 3.25 km/s just to reach 7.8 km/s, and more once gravity and drag losses are counted.

Staging removes the dead mass in steps. The vehicle is built as a stack of rockets, each sitting on top of the one below. The bottom stage lifts the whole stack, burns its fuel, and is dropped; the next stage then starts with a much smaller vehicle, so the same exhaust velocity buys a fresh logarithmic increment from a fresh mass ratio. The velocity increments add, while the mass that has to be carried shrinks at every separation.

Each stage must carry everything above it as its payload. A kilogram added at the top needs more fuel in the top stage, which needs more fuel in every stage below, so the payload fraction of the whole vehicle is the product of the stage payload ratios and is always small. The design choices are therefore the number of stages and the share of the work each one does.

---

## 1. Mass fractions for one stage

A stage plus its load splits into payload $M_p$, structure $M_s$ (tanks, engines, interstage, everything that is neither payload nor propellant) and fuel $M_f$ (Part 3, pp. 22 and 25):

$$
M_0=M_p+M_s+M_f,\qquad M_b=M_p+M_s .
$$

The burnout mass $M_b$ keeps the structure, because the stage is only dropped after it has burnt out. The two ratios are

$$
p=\frac{M_p}{M_0}\ \text{(payload fraction)},\qquad s=\frac{M_s}{M_f}\ \text{(propellant tankage structural efficiency)} .
$$

The exact result ([[SESA1015 A04 - Rocket Equation and Launch Performance#Deriving the mass ratio in terms of p and s|A04]]) is

$$
\frac{M_0}{M_b}=\frac{1+s}{p+s},\qquad \Delta V_{ideal}=V_{ex}\ln\frac{M_p+M_s+M_f}{M_p+M_s}=V_{ex}\ln\frac{1+s}{p+s}.
$$

With no payload, $p=0$, the mass ratio is $(1+s)/s$, set by the structure alone: $s=0.1$ gives 11, so $\Delta V/V_{ex}\le\ln11=2.40$. With no structure, $s=0$, the mass ratio is $1/p$ and any $\Delta V$ is possible given a small enough payload. Structure, not propellant, is what limits a single stage.

> [!warning] Two meanings of f
> Here $M_f$ is **fuel** mass and $M_b$ is the burnout (final) mass. Many textbooks, and [[SESA2023 W10 - Rocket Performance, Staging and Power Cycles|SESA2023]], use $m_f$ or $m_{bo}$ for final mass and $m_p$ for propellant, so the same letter can mean payload, propellant or final mass depending on the source. Check the definitions before substituting.

## 2. Why staging is needed

The single-stage-to-orbit result (Part 3, p. 23) says that even under ideal conditions, with no payload and no losses, a single stage reaches orbit only with high-energy propellants. The propellant tankage is a large mass, and once its contents are burnt it contributes nothing but inertia. Shedding it progressively on the way up gives large performance benefits: this is **staging**.

The benefit is easiest to see by comparing a staged vehicle with a single stage made of the same parts. Take the three-stage vehicle of [[#A three-stage vehicle]], with 46 t of fuel and 4.7 t of structure in total. Staged, it gives an ideal 11.0 km/s. If the same fuel were burnt at the first-stage exhaust velocity with all 4.7 t of structure kept to the end, the mass ratio would be $51.7/(51.7-46.0)=9.07$ and the ideal $\Delta V$ only $2.9\ln9.07=6.4$ km/s. Dropping the empty structure, and using better engines on the upper stages, makes the difference.

## 3. The multistage rocket equation

### Stage bookkeeping

Consider a three-stage vehicle (Part 3, pp. 26–27). Stage 1 is jettisoned at the end of its burn, then stage 2, then stage 3, and what remains is the mass delivered to orbit. For each stage $i$, $M_{0i}$ is its initial mass (the whole vehicle at its ignition), $M_{fi}$ its fuel, $M_{si}$ its structure, and $M_{pi}$ its payload, which is everything above it:

$$
M_{p1}=M_{02},\qquad M_{p2}=M_{03},\qquad M_{p3}=\text{mass delivered to orbit}.
$$

![[astro_a05_stage_masses.png|900]]

Each stage, seen with its payload, is a single-stage rocket:

$$
M_{0i}=M_{pi}+M_{si}+M_{fi},\qquad M_{bi}=M_{pi}+M_{si},
$$

$$
p_i=\frac{M_{pi}}{M_{0i}},\qquad s_i=\frac{M_{si}}{M_{fi}} .
$$

### Adding the stages

Stage $i$ starts from the speed at which stage $i-1$ burnt out, and the rocket equation gives the increment it adds:

$$
\Delta V_i=V_{ex,i}\ln\frac{M_{0i}}{M_{bi}}=V_{ex,i}\ln\frac{1+s_i}{p_i+s_i}.
$$

The total is the sum of the increments (p. 27):

$$
\boxed{\Delta V_{ideal}=\sum_{i=1}^{3}V_{ex,i}\ln\frac{1+s_i}{p_i+s_i}}
$$

Gravity and drag losses are then subtracted from $\Delta V_{ideal}$ exactly as for one stage, [[SESA1015 A04 - Rocket Equation and Launch Performance#5. Gravity loss and drag loss|A04 equation (3.3)]].

### The overall payload fraction

The **overall payload fraction** is the mass delivered to orbit over the lift-off mass:

$$
P=\frac{M_{p3}}{M_{01}}.
$$

Insert the intermediate stack masses, each of which appears once on top and once underneath:

$$
P=\frac{M_{p3}}{M_{03}}\cdot\frac{M_{03}}{M_{02}}\cdot\frac{M_{02}}{M_{01}}.
$$

Since $M_{03}=M_{p2}$ and $M_{02}=M_{p1}$,

$$
P=\frac{M_{p3}}{M_{03}}\cdot\frac{M_{p2}}{M_{02}}\cdot\frac{M_{p1}}{M_{01}}=p_3\,p_2\,p_1,
$$

$$
\boxed{P=\prod_i p_i} .
$$

Stage payload ratios of 0.2–0.3 are typical, so a three-stage vehicle has $P$ of order 1–2 %. The Saturn V put about 129,300 kg into orbit from a lift-off mass of about 3,039,000 kg, $P=4.3$ % (Part 1, p. 15).

## 4. Diminishing returns with the number of stages

### Identical stages

The effect of the number of stages $N$ is clearest when every stage has the same $V_{ex}$ and $s$ and the same payload ratio. The payload ratios then multiply to the overall fraction, $p_i^N=P$, so

$$
p_i=P^{1/N},
$$

and the $N$ equal increments add to

$$
\frac{\Delta V_{ideal}}{V_{ex}}=N\ln\frac{1+s}{P^{1/N}+s}.
$$

With no payload, $P=0$, this is $N\ln\frac{1+s}{s}$, a straight line: each extra stage adds the full no-payload increment. With a payload the curve bends over.

### The limit of infinitely many stages

As $N\to\infty$, $1/N\to0$. Write $P^{1/N}=e^{(\ln P)/N}$ and expand the exponential for small $(\ln P)/N$:

$$
P^{1/N}\approx1+\frac{\ln P}{N}.
$$

Then

$$
\frac{1+s}{P^{1/N}+s}\approx\frac{1+s}{1+s+(\ln P)/N}=\frac{1}{1+\dfrac{\ln P}{N(1+s)}} .
$$

Taking the logarithm with $\ln\frac{1}{1+x}\approx-x$ for small $x$,

$$
\ln\frac{1+s}{P^{1/N}+s}\approx-\frac{\ln P}{N(1+s)}.
$$

Multiplying by $N$,

$$
\boxed{\lim_{N\to\infty}\frac{\Delta V_{ideal}}{V_{ex}}=\frac{\ln(1/P)}{1+s}}
$$

The ceiling is finite: an infinite number of stages, each carrying its own structure, still cannot beat $\ln(1/P)/(1+s)$.

![[astro_a05_stages_curve.png|900]]

The figure is the variation of velocity increment with number of stages (Part 3, p. 24). The original chart leaves $s$ unstated; the curves here use $s=0.15$, which reproduces its asymptotes of 2, 4 and 6 for $P=0.1$, $0.01$ and $0.001$ (since $\ln10/1.15=2.00$). Going from one to two stages gives the largest gain, three stages get close to the ceiling, and beyond four the gain is a few per cent per stage. Real vehicles lie near the $P=0.01$ curve: the Shuttle to LEO and Ariane to GTO both sit on it in the original chart. Each stage also brings engines, separation hardware, avionics and failure modes, so the practical number is two or three, sometimes with strap-on boosters.

## 5. Sharing the work between stages

Identical stages should have equal payload ratios, as the curves above assume (the proof below is not part of Part 3).

Take two stages with the same $V_{ex}$ and $s$, and a fixed overall payload fraction $P=p_1p_2$, so $p_2=P/p_1$. The ideal velocity is

$$
\frac{\Delta V}{V_{ex}}=f(p_1)=\ln(1+s)-\ln(p_1+s)+\ln(1+s)-\ln\!\left(\frac{P}{p_1}+s\right).
$$

Differentiate with respect to $p_1$:

$$
f'(p_1)=-\frac{1}{p_1+s}-\frac{-P/p_1^2}{P/p_1+s}=-\frac{1}{p_1+s}+\frac{P/p_1^2}{P/p_1+s}.
$$

Set $f'(p_1)=0$:

$$
\frac{P/p_1^2}{P/p_1+s}=\frac{1}{p_1+s}.
$$

Cross-multiply:

$$
\frac{P}{p_1^2}(p_1+s)=\frac{P}{p_1}+s .
$$

Expand the left side:

$$
\frac{P}{p_1}+\frac{Ps}{p_1^2}=\frac{P}{p_1}+s .
$$

Cancel $P/p_1$:

$$
\frac{Ps}{p_1^2}=s .
$$

$$
p_1^2=P,\qquad p_1=\sqrt P=p_2 .
$$

At $p_1=\sqrt P$ the derivative changes from positive to negative (the figure shows the single peak), so this is a maximum: for identical stages the best split gives both stages the same payload ratio, and since they share $s$ and $V_{ex}$, the same $\Delta V$. The same argument applied to any pair of adjacent stages extends the result to $N$ identical stages, $p_i=P^{1/N}$.

![[astro_a05_two_stage_split.png|850]]

The optimum is flat: $p_1$ can be off by a factor of two either way at a cost of only a few per cent in $\Delta V$, which leaves room for other considerations. Real stages are not identical. A first stage works in the atmosphere, needs high thrust, and can use dense propellant with a lower $V_{ex}$; an upper stage works in vacuum where high-$V_{ex}$ hydrogen pays off. Unequal $V_{ex}$ and $s$ move the optimum ([[SESA2023 W10 - Rocket Performance, Staging and Power Cycles]]).

## Worked examples

### Two identical stages to LEO

Put 1000 kg into LEO, needing $\Delta V_{ideal}=8.75$ km/s including losses (A04), with stages of $V_{ex}=3$ km/s and $s=0.1$.

A single stage cannot do it: its maximum is $3\ln11=7.19$ km/s, and solving $3\ln\frac{1.1}{p+0.1}=8.75$ gives $p=1.1e^{-2.917}-0.1=-0.040$.

With two equal stages each supplies $8.75/2=4.375$ km/s:

$$
\ln\frac{1.1}{p_i+0.1}=\frac{4.375}{3}=1.4583,\qquad \frac{1.1}{p_i+0.1}=e^{1.4583}=4.299,
$$

$$
p_i=\frac{1.1}{4.299}-0.1=0.2559-0.1=0.1559 .
$$

$$
P=p_i^2=0.02430,\qquad M_{01}=\frac{1000}{0.02430}=41\,150\ \mathrm{kg}.
$$

The stage masses follow from the top down. Stage 2 has $M_{02}=1000/0.1559=6415$ kg, so $M_{s2}+M_{f2}=5415$ kg; with $M_{s2}=0.1M_{f2}$, $M_{f2}=5415/1.1=4923$ kg and $M_{s2}=492$ kg. Stage 1 has $M_{s1}+M_{f1}=41\,151-6415=34\,736$ kg, so $M_{f1}=31\,579$ kg and $M_{s1}=3158$ kg.

> [!check] Numerical check
> Stage 2: $3\ln\frac{6415}{1000+492}=3\ln4.2997=4.375$ km/s. Stage 1: $3\ln\frac{41\,151}{6415+3158}=3\ln4.2987=4.375$ km/s. Total 8.75 km/s ✓.

Repeating for more equal stages:

| Stages $N$ | $p_i$ | $P$ | Lift-off mass $M_{01}$ |
|---|---|---|---|
| 1 | $-0.040$ | impossible | — |
| 2 | 0.1559 | 0.0243 | 41.2 t |
| 3 | 0.3161 | 0.0316 | 31.7 t |
| 4 | 0.4305 | 0.0344 | 29.1 t |
| 5 | 0.5138 | 0.0358 | 27.9 t |

![[astro_a05_lift_off_mass.png|750]]

The third stage saves 9.5 t of lift-off mass; the fourth saves only 2.6 t, and the fifth 1.2 t.

### A three-stage vehicle

A vehicle carries $M_{p3}=1000$ kg. Its stages have fuel $M_{f1}=36\,000$ kg, $M_{f2}=8000$ kg, $M_{f3}=2000$ kg; structural efficiencies $s_1=s_2=0.10$, $s_3=0.15$; and exhaust velocities 2.9, 3.2 and 4.4 km/s (the third stage burns hydrogen, whose bulky tanks give the larger $s$). Find the ideal $\Delta V$ and $P$.

Structure: $M_{s1}=3600$ kg, $M_{s2}=800$ kg, $M_{s3}=300$ kg. Build the stack from the top:

$$
M_{03}=1000+300+2000=3300\ \mathrm{kg},
$$

$$
M_{02}=3300+800+8000=12\,100\ \mathrm{kg},
$$

$$
M_{01}=12\,100+3600+36\,000=51\,700\ \mathrm{kg}.
$$

Each stage's burnout mass is its initial mass less its fuel:

| Stage | $M_{0i}$ (kg) | $M_{bi}$ (kg) | $M_{0i}/M_{bi}$ | $p_i$ | $\Delta V_i$ (km/s) |
|---|---|---|---|---|---|
| 1 | 51,700 | 15,700 | 3.293 | 0.234 | $2.9\ln3.293=3.456$ |
| 2 | 12,100 | 4,100 | 2.951 | 0.273 | $3.2\ln2.951=3.463$ |
| 3 | 3,300 | 1,300 | 2.538 | 0.303 | $4.4\ln2.538=4.099$ |

$$
\Delta V_{ideal}=3.456+3.463+4.099=11.02\ \mathrm{km/s},\qquad P=\frac{1000}{51\,700}=0.0193 .
$$

The product $p_1p_2p_3=0.234\times0.273\times0.303=0.0193$ agrees. After 0.75–1.8 km/s of losses this is enough for LEO with a large margin, or for a transfer orbit beyond it. The same fuel and structure as one stage at $V_{ex}=2.9$ km/s would give only 6.4 km/s ([[#2. Why staging is needed]]).

> [!check] Numerical check
> Stage 1 by the $p$, $s$ form: $2.9\ln\frac{1.1}{0.234+0.1}=2.9\ln3.293=3.456$ km/s, the same as the direct mass ratio, as it must be since $(1+s)/(p+s)=M_0/M_b$ exactly.

## Terminology and alternative names

| Course term | Also called | Note |
|---|---|---|
| payload fraction $p=M_p/M_0$ | payload ratio $\lambda$ (SESA2023, Sutton) | Curtis defines $\lambda=M_p/(M_s+M_f)$, a different ratio |
| propellant tankage structural efficiency $s=M_s/M_f$ | structural ratio | per kilogram of propellant |
| (no course symbol) | structural coefficient $\varepsilon=M_s/(M_s+M_f)=s/(1+s)$ | Curtis; $s=0.1$ is $\varepsilon=0.091$ |
| (no course symbol) | dead-weight or structural ratio $\delta=M_s/M_0$ | SESA2023; $\delta=s(1-p)/(1+s)$ and $1/(p+\delta)=(1+s)/(p+s)$ |
| fuel mass $M_f$ | propellant mass $m_p$ | $m_f$ elsewhere often means final mass |
| overall payload fraction $P$ | $\lambda_0$, overall payload ratio | $P=\prod p_i$ in every convention that uses $M_p/M_0$ |

## Links

- Parent: [[SESA1015 Intro to Aero & Astro Hub]]
- Previous: [[SESA1015 A04 - Rocket Equation and Launch Performance]] · Next: [[SESA1015 A06 - Launch Vehicles, Systems and Interfaces]]
- Concepts: [[Rocket Mass Fractions]] · [[Multistage Rocket Performance]] · [[Tsiolkovsky Rocket Equation]] · [[Gravity and Drag Losses]]
- Later in the degree: [[SESA2023 W10 - Rocket Performance, Staging and Power Cycles]] (staging solved from the top down with $\lambda_i=e^{-\Delta V_i/c_e}-\delta_i$, the Saturn V example) · [[Rocket Staging]] (SESA2023 concept) · [[SESA2024 01 - Systems Engineering and Spacecraft Design]] (mass budgets and margins).

## Sources

- Astronautics Part 3, Launch Vehicles: pp. 22–23 (payload fraction, structural efficiency, single stage to orbit), p. 24 (variation of velocity increment with number of stages), pp. 25–27 (multistage vehicle, stage masses, $\Delta V_{ideal}$ sum, overall payload fraction).
- Astronautics Part 1, Introduction: p. 15 (Saturn V payload mass fraction).
- Sections 4 (the limit of infinitely many stages) and 5 (the optimal split) are derived here; the slides give only the chart.
- Figures: `01 - Notes/Figures/generate_astro_a05_figures.py`.

## Self-study tasks

There are no exercises set in the Part 3 deck; the tasks below rework the slide material, plus three suggested problems.

### Core

- [ ] Derive the multistage $\Delta V_{ideal}$ sum and show that $P=p_1p_2p_3$ for the three-stage vehicle of Part 3, p. 27. → [[#3. The multistage rocket equation]]
- [ ] Explain, using the single-stage limit, why staging is needed (Part 3, p. 23). → [[#2. Why staging is needed]]
- [ ] Reproduce the curves of Part 3, p. 24 for identical stages and show the limit as $N\to\infty$. → [[#4. Diminishing returns with the number of stages]]

### Further practice

- [ ] Suggested, not lecturer-set: 1000 kg to LEO with $\Delta V=8.75$ km/s, $V_{ex}=3$ km/s, $s=0.1$: show one stage is impossible and size two equal stages. → [[#Two identical stages to LEO]]
- [ ] Suggested, not lecturer-set: find $\Delta V_{ideal}$ and $P$ for the three-stage vehicle with fuel 36, 8 and 2 t. → [[#A three-stage vehicle]]
- [ ] Suggested, not lecturer-set: show that two identical stages with fixed $P$ do best with $p_1=p_2=\sqrt P$. → [[#5. Sharing the work between stages]]
