---
title: "SESA2023 W10 - Rocket Performance, Staging and Power Cycles"
module: "SESA2023 Propulsion"
type: topic
stream: "Section 5: Rockets"
order: 10
tags:
  - sesa2023
  - rockets
  - specific-impulse
  - staging
  - power-cycles
aliases: ["Rockets I", "Rocket staging", "SESA2023 Week 10"]
date: 2026-09-24
status: lectured
coverage: "Week 10 (rockets introduction, staging, power cycles) and the 5 May staging review"
parent: ["[[SESA2023 Propulsion Hub]]"]
prerequisites: ["[[SESA2023 W03 - Compressible Flow, Normal Shocks and Nozzles]]", "[[SESA2023 W01 - Thrust, Efficiency, Range and the ISA]]"]
next_topics: ["[[SESA2023 W11 - Solid Propellants and Rocket Nozzle Design]]"]
key_concepts: ["[[Rocket Performance Parameters]]", "[[Tsiolkovsky Rocket Equation]]", "[[Rocket Staging]]", "[[Rocket Engine Power Cycles]]", "[[Critical Conditions and Choked Flow]]"]
tutorial_sheets: ["[[SESA2023 Problem Sheet 10 Rockets Solutions]]"]
sources: ["02 - Sources/Lectures/Week 10 - Rockets.pdf", "02 - Sources/Lectures/Week 10 - Rockets - Lecture Slides.pdf", "02 - Sources/Lectures/SESA2023 Lecture 25 - Rockets Introduction.txt", "02 - Sources/Lectures/SESA2023 Lecture 26 - Rocket staging.txt", "02 - Sources/Lectures/SESA2023 Lecture 30.txt", "02 - Sources/Lectures/SESA2023 Lecture 31.txt"]
---

# SESA2023 W10 - Rocket Performance, Staging and Power Cycles

> [!abstract] Summary
> A rocket carries all of its propellant, so the aim is the most impulse per kilogram, which means a hot, high-pressure chamber, light exhaust products and a well-expanded nozzle. Its performance is measured by the specific impulse $I_{sp}$ and effective exhaust velocity $c_e$ overall, the characteristic velocity $C^*$ for the combustion and the thrust coefficient $C_F$ for the nozzle, with $c_e=C^*C_F$. The Tsiolkovsky equation $\Delta V=c_e\ln(m_0/m_{bo})$ shows why staging is essential, and liquid engines' power cycles (pressure-fed, expander, gas generator, staged combustion) trade complexity for chamber pressure, while solid motors are simple but can't be controlled.

> [!summary]- Exam use: quick path
> - **Use it when:** given chamber conditions and a nozzle, find $V_j$, $C^*$, $C_F$, $I_{sp}$, throat and exit areas; given $\Delta V$, $I_{sp}$, payload and structural ratio, find propellant and stage masses; or compare power cycles.
> - **Assumptions:** perfect gas of combustion products with given $\gamma$, $R$ (or $c_p$); adiabatic isentropic nozzle, choked throat; fully expanded unless stated; for the rocket equation, constant $c_e$, no gravity or drag losses unless asked.
> - **Method:** 1. $V_j=\sqrt{2c_pT_{0c}[1-(p_e/p_{0c})^{(\gamma-1)/\gamma}]}$. 2. $\dot m=F/(g_0I_{sp})$; throat area from the choked mass flow; $A_e=A_t(A_e/A_t)$. 3. $C^*=p_cA_t/\dot m$, $C_F=F/(p_cA_t)$, check $c_e=C^*C_F$. 4. Rocket equation per stage: $\lambda=e^{-\Delta V/c_e}-\delta$, $m_0=m_{pl}/\lambda$. 5. Staging: the payload of stage $i$ is the whole stack above it; solve from the top stage down.
> - **Common mistakes:** treating stage 2's mass as separate from stage 1's payload (the most common error in the 2024-25 exam, 5 May, ll. 237–241); using $g$ at altitude instead of $g_0$ in $I_{sp}$.
> - **Practise:** [[#Worked example – the 2024-25 exam rocket question]] · [[SESA2023 Problem Sheet 10 Rockets Solutions]] Q10.1–Q10.3

A rocket produces thrust by ejecting propellant it carries. No air comes in, so there is no ram drag, and every kilogram leaving the nozzle at $V_j$ is pure thrust (LR1, ll. 13–24); the faster it leaves, the less propellant is needed. The chamber and the nozzle do separate jobs: hot, light gas at high pressure in the chamber has a lot of enthalpy, which the nozzle converts to speed, so $C^*$ measures the chamber and $C_F$ the nozzle.

Most of a rocket's mass is propellant. As it burns the rocket gets lighter, so the same thrust accelerates it more, and the result is logarithmic: doubling the speed needs the mass ratio squared. That is the case for staging. Once a stage's propellant is gone, its tanks and engines are dead weight, and dropping them means the next stage only has to accelerate what is still useful. Finally, a high chamber pressure needs powerful pumps, and the power cycle (pressurised tanks, heated fuel, a small burner or a pre-burner) is the choice of how they are driven.

---

## 1. Rocket thrust and the ideal jet velocity (rockets introduction)

From W01, with no inlet momentum:

$$
F = \dot mV_j+A_e(P_e-P_A)
$$

Unlike an air-breather, a rocket wants a small $\dot m$ and a large $V_j$: its whole propellant load has to be carried (LR1, ll. 13–24, 51–68). In a large turbofan the air outweighs the fuel about 500 : 1; in a rocket the oxidiser-to-fuel ratio is more like 4 : 1, and every kilogram of both is on board.

- The equation applies to a static test stand, or to a flying rocket if all the extra pressure and shear forces on the vehicle's sides are booked as drag: "this is our rocket thrust and the rest of it is rocket drag" (LR1, ll. 24–41).
- The module covers chemical rockets only. Electric propulsion (ionised propellant accelerated by an electric field) obeys the same thrust equation, but "we won't discuss that in this module" (LR1, ll. 44–50).

### Ideal jet velocity

Assume an adiabatic nozzle (so $T_{0c}=T_{0e}$, chamber to exit), isentropic flow and full expansion ($P_e=P_A$). The SFEE between the chamber (stagnant) and the exit, with no heat or work:

$$
\tfrac12V_e^2 = h_{0c}-h_e = c_p\left(T_{0c}-T_e\right)
$$

Use the isentropic relation $T_e/T_{0c}=(P_e/P_{0c})^{(\gamma-1)/\gamma}$:

$$
\boxed{V_j = \sqrt{2c_pT_{0c}\left[1-\left(\frac{P_e}{P_{0c}}\right)^{\frac{\gamma-1}{\gamma}}\right]}}
$$

To raise $V_j$:

- raise $T_{0c}$ (burning in oxygen, with no nitrogen to dilute it, gives about 3600 K, LR1, ll. 286–288);
- raise $P_{0c}/P_e$, though with diminishing returns as the bracket tends to 1;
- choose a light exhaust: $c_pT=\frac{\gamma}{\gamma-1}\frac{\bar R}{M}T$, so at a given temperature a lower molar mass $M$ gives more enthalpy per kilogram (hence hydrogen).

In practice the nozzle is a regenerative heat exchanger (fuel flows through cooling passages in its wall), so "adiabatic" is an approximation. The lecture lists the idealisations and how good they are (LR1, ll. 89–117): adiabatic (reasonable, since little of the flow touches the wall), uniform temperature and velocity (not true near the cooled wall), no viscous losses or separation (so isentropic), and a perfect gas, which is poor for a gas cooling by thousands of kelvin. They give the trends, not accurate numbers.

![[prop_rocket_nozzle.png|760]]

A supersonic exit decouples the chamber from the outside: everything upstream of the choked throat is independent of the back pressure (LR1, ll. 290–295; W01). At low altitude the jet is over-expanded, at its design altitude exactly expanded, and higher up under-expanded (W03 regimes 6–8).

## 2. Performance parameters

| Parameter | Definition | Measures |
|---|---|---|
| Total impulse | $I_T=\int_0^tF\,dt$ | |
| Specific impulse | $I_{sp}=\dfrac{I_T}{g_0m_p}=\dfrac{F}{g_0\dot m}$ (s) | the overall engine |
| Effective exhaust velocity | $c_e=\dfrac{F}{\dot m}=g_0I_{sp}$ | overall; includes pressure thrust and non-uniform exit flow |
| Characteristic velocity | $C^*=\dfrac{p_cA_t}{\dot m}$ | the combustor |
| Thrust coefficient | $C_F=\dfrac{F}{p_cA_t}$ | the nozzle expansion |

- Impulse is force integrated over time: a long gentle push (croquet) or a short hard hit (golf) can give the same change in momentum (LR1, ll. 195–203). Dividing by the propellant weight gives $I_{sp}$ in seconds.
- $g_0=9.81$ m/s², sea-level gravity, is used by convention even for rockets elsewhere; and $m_p$ is the whole propellant, oxidiser plus fuel (LR1, ll. 210–216).
- $c$ is for *celeritas*, speed (LR1, l. 229). With pressure thrust or a non-uniform exit, $c_e$ is a representative velocity, not the actual jet velocity.
- The throat is almost always choked, so it is a natural dividing line: $C^*$ for everything upstream (combustion), $C_F$ for everything downstream (nozzle) (LR1, ll. 236–276).

Multiply the last two; $p_cA_t$ cancels:

$$
C^*C_F = \frac{p_cA_t}{\dot m}\cdot\frac{F}{p_cA_t} = \frac{F}{\dot m} = c_e,\qquad I_{sp} = \frac{C^*C_F}{g_0}
$$

### Why the characteristic velocity measures only the combustor

The throat is choked, so (W03, compact form with $p_c=p_0$, $T_c=T_0$):

$$
\dot m = \frac{A_tp_c}{\sqrt{T_c}}\sqrt{\frac{\gamma}{R}}\left(\frac{2}{\gamma+1}\right)^{\frac{\gamma+1}{2(\gamma-1)}}
$$

Rearrange for $p_cA_t/\dot m$:

$$
\boxed{C^* = \sqrt{\frac{RT_c}{\gamma}}\left(\frac{\gamma+1}{2}\right)^{\frac{\gamma+1}{2(\gamma-1)}}}
$$

It depends only on the combustion products ($R$, $\gamma$, $T_c$), not on the diverging section. $C_F$ then carries the nozzle's expansion and the pressure thrust (W11).

> [!warning] $C^*$ is not the throat velocity (LR1, ll. 252–253)
> "The characteristic velocity C star is the flow velocity through the throat." It has units of velocity, but it is defined as $p_cA_t/\dot m$, not as the gas speed. The gas at a choked throat moves at the critical sound speed $a^*=\sqrt{\gamma RT^*}$. For the F-1 below, $T^*=3600\times2/2.24=3214$ K and $a^*=1193$ m/s, while $C^*=1727$ m/s.

> [!warning] Slide typo (LR1, l. 263)
> "That should say choked rather than cocked. Sorry, I apologise, not my slides."

### Worked example – the Saturn V F-1 engine

The lecture example (LR1, ll. 282–375): $T_c=3600$ K, $P_c=70$ bar, $A_e/A_t=16$, design altitude 24 km ($P_A=2.97$ kPa from the data book), $F=7.7$ MN, $I_{sp}=305$ s; $\gamma=1.24$, $R=356.8$, $c_p=1844$ J kg⁻¹ K⁻¹.

Ideal jet velocity at the design altitude:

$$
V_j = \sqrt{2\times1844\times3600\left[1-\left(\frac{2970}{7\times10^6}\right)^{0.1935}\right]} = 3213\ \mathrm{m/s}
$$

**Effective exhaust velocity and mass flow:**

$$
c_e = g_0I_{sp} = 9.81\times305 = 2992\ \mathrm{m/s},\qquad \dot m = \frac{F}{c_e} = \frac{7.7\times10^6}{2992} = 2573\ \mathrm{kg/s}
$$

$c_e<V_j$: the nozzle is cooled and has viscous losses, and, probably more important, the perfect-gas $V_j$ is very sensitive to the assumed $\gamma$ and $c_p$ (LR1, ll. 323–331).

Throat and exit (choked-flow formula from the data book, LR1, ll. 340–373):

$$
A_t = \frac{\dot m\sqrt{T_c}}{p_c\sqrt{\gamma/R}\,\big(2/(\gamma+1)\big)^{(\gamma+1)/[2(\gamma-1)]}} = 0.635\ \mathrm{m^2},\qquad D_t = 0.90\ \mathrm m
$$

$$
A_e = 16A_t = 10.16\ \mathrm{m^2},\qquad D_e = 3.6\ \mathrm m
$$

**Component parameters:** $C^*=1727$ m/s, so $C_F=c_e/C^*=1.73$.

> [!warning] Two problems with this example
> - **Transcript slips (LR1, ll. 298, 320, 367):** the thrust is read as "seven meganewtons" (slide 7.7 MN), and the mass flow as "about 2.3 tons per second" and then "2.5 kilograms per second". The computed value is 2.57 t/s; the real engine ran at about 2.6 t/s.
> - **Inconsistent design altitude.** An isentropic expansion through $A_e/A_t=16$ at $\gamma=1.24$ reaches only $M_e=3.76$ and $p_e=42$ kPa, a design altitude of about 7 km, not 24 km. The 3213 m/s is therefore an *upper bound* for this nozzle. (The real F-1 throat was about 0.78 m, LR1, l. 374.)

## 3. Mass ratios and the rocket equation

### Definitions

$$
m_0 = m_{pl}+m_p+m_{dw},\qquad m_{bo} = m_{pl}+m_{dw}
$$

with payload $m_{pl}$, propellant $m_p$ and dead (structural) weight $m_{dw}$. Define the payload and structural ratios and the mass ratio:

$$
\lambda = \frac{m_{pl}}{m_0},\qquad \delta = \frac{m_{dw}}{m_0},\qquad MR = \frac{m_0}{m_{bo}} = \frac{1}{\lambda+\delta}
$$

### Derivation of the Tsiolkovsky equation

"You don't need to remember the equation by heart, but you need to know how to derive it" (5 May, ll. 45–48). In the 2024-25 exam it was worth 6 marks, and only about a third of the cohort got it (ll. 106–113).

Fully expanded, so the thrust is $F=\dot mc_e$, with the propellant flow $\dot m=-dm/dt$ (the rocket's mass falls). Newton's second law, ignoring gravity and drag:

$$
m\frac{dV}{dt} = F = -c_e\frac{dm}{dt}
$$

Multiply by $dt$ and divide by $m$:

$$
dV = -c_e\frac{dm}{m}
$$

Integrate from the initial state ($V_1$, $m_0$) to burnout ($V_2$, $m_{bo}$); $c_e$ is constant:

$$
V_2-V_1 = -c_e\int_{m_0}^{m_{bo}}\frac{dm}{m} = -c_e\ln\frac{m_{bo}}{m_0}
$$

$$
\boxed{\Delta V_{ideal} = c_e\ln\frac{m_0}{m_{bo}} = c_e\ln\frac{1}{\lambda+\delta}}
$$

Keep the minus sign explicit (5 May, ll. 87–96): "one thing that we need to be careful… the mass is actually decreasing." Putting it in at $\dot m=-dm/dt$ saves worrying about which of $m_1$ and $m_2$ is larger.

### Losses

With gravity at flight-path angle $\psi$ from the horizontal and drag $D$:

$$
\Delta V = \Delta V_{ideal}-\int_0^tg\sin\psi\,dt-\int_0^t\frac{D}{m}\,dt
$$

- Drag $D=\tfrac12\rho V^2SC_D$ favours a slow, vertical climb out of the dense lower atmosphere.
- Gravity loss favours high acceleration (short burn) and a small $\psi$.
- The compromise: lift off vertically and slowly (the vehicle is heaviest then anyway), then pitch over in a gravity turn. In the limit, a rocket accelerating sideways just above the ground would have no gravity loss at all, since it is already in orbit; the gravity turn moves towards that once the air is thin (LR2, ll. 116–140).
- Drag goes with $V^2$, so it pays to reach a reasonable speed quickly and then moderate it in the dense air. A student asked why rockets throttle down on the way up: partly drag, and partly the structural loads near maximum dynamic pressure and through Mach 1 ("I'll research that one", LR2, ll. 143–154).

## 4. Staging (rocket staging)

### Relations

Each stage's "payload" is everything above it:

$$
(m_{pl})_i = (m_0)_{i+1}
$$

Apply the rocket equation to stage $i$ with its own $\delta_i$ and $c_{e,i}$:

$$
\frac{\Delta V_i}{c_{e,i}} = \ln\frac{1}{\lambda_i+\delta_i}\qquad\Longrightarrow\qquad \boxed{\lambda_i = \exp\!\left(-\frac{\Delta V_i}{c_{e,i}}\right)-\delta_i},\qquad (m_0)_i = \frac{(m_{pl})_i}{\lambda_i}
$$

Overall, because each stage's initial mass is the next stage's payload, the payload ratios multiply and the velocity increments add:

$$
\lambda_0 = \frac{m_{pl}}{(m_0)_1} = \prod_i\lambda_i,\qquad \Delta V_0 = \sum_i\Delta V_i
$$

**Work from the top stage down**: the payload is known only for the last stage. The biggest gain is from one to two stages; more give diminishing returns and add complexity ("just an accounting exercise", LR2, ll. 176, 194). Each extra stage needs its own engine, and several small tanks have more structure than one big one, so the total dead weight rises: an optimisation problem (ll. 289–298).

A second reason to stage (LR2, ll. 157–163): each engine is fully expanded at only one altitude. A first stage can be designed for 10–20 km; upper stages fire in near-vacuum and use much larger area ratios. Dropping the low-altitude engines lets each phase use a nozzle suited to it.

All the performance parameters, mass ratios, the rocket equation and the staging relation $(m_{pl})_i=(m_0)_{i+1}$ are printed in the data book, so "you don't need to memorise them" (LR2, ll. 7–10, 48–49, 189–193, 301–302). The 5 May review adds that you must still be able to derive the rocket equation.

![[prop_rocket_staging.png|640]]

> [!warning] The most common exam error (5 May, ll. 230–241, 389–399)
> "A very common mistake last year was to use first stage two, then stage one, and then making all the calculation wrong." In the *mission*, stage 1 fires first and is dropped. In the *calculation*, you start with stage 2 because that is where the payload is given. The link is always: payload of stage 1 = initial mass of stage 2.

### Worked example – Saturn V staging

Lecture example (LR2, ll. 197–264): payload 43.5 t.

| Stage | $m_0$ (t) | $\lambda$ | $\delta$ | $c_e$ (m/s) | $\Delta V$ (m/s) |
|---|---|---|---|---|---|
| 1 | 2942.5 | 0.218 | 0.0445 | 2991 | 3996 |
| 2 | 642.5 | 0.253 | 0.0560 | 4129 | 4850 |
| 3 | 162.5 | 0.268 | 0.0615 | 4129 | 4587 |

$\Delta V_0=13{,}433$ m/s (about 13 km/s, LR2, l. 264) and $\lambda_0=43.5/2942.5=0.0148$.

A single stage with the same $\lambda_0$ and $\delta_0=0.06$ reaches only 10,706 m/s. To reach 13,433 m/s it would need $m_0=5706$ t, nearly twice the actual 2942.5 t.

The first stage burns RP-1 (refined kerosene) with LOX, the upper two LH₂/LOX, hence the different $c_e$ (about 3000 against 4129 m/s). Propellant loads are about 2000, 400 and 100 t, all to lift about 43 t (LR2, ll. 197–216).

> [!check] Numerical checks
> - Stage 1: $2991\ln[1/(0.218+0.0445)]=4000$ m/s; the table's 3996 comes from the unrounded $\lambda$, $\delta$.
> - $\lambda_0=0.218\times0.253\times0.268=0.0148$ ✔.
> - Single-stage alternative: burnout mass = all dead weight + payload = $131+36+10+43.5\approx220$ t, so $m_0=220\,e^{13\,433/4129}=5707$ t and $\lambda=43.5/5707=0.76$ %.

> [!warning] Transcript slips in the Saturn V example (LR2, ll. 252, 280–287)
> - "About 13,000 kilometers per second": it is about 13 km/s (13,433 m/s), as the lecturer says at l. 264.
> - For the single-stage case the lecturer gives the payload ratio as "0.076 %… about 20 times worse… we can take two tonnes of payload". With the same 43.5 t payload and $m_0=5707$ t the payload ratio is 0.76 %, about half (not a twentieth) of the staged 1.48 %. The "two tonnes" figure would be 0.076 % of the *original* 2942 t, a different comparison.

### Worked example – the 2024-25 exam rocket question

Reviewed in full on 5 May (ll. 115–330): $\Delta V=5000$ m/s, payload 2000 kg, $I_{sp}=450$ s, $\delta=0.08$.

**Single stage.**

$$
c_e = 450\times9.81 = 4414.5\ \mathrm{m/s},\qquad MR = e^{5000/4414.5} = 3.104
$$

$$
\lambda = \frac{1}{MR}-\delta = 0.3222-0.08 = 0.2422,\qquad m_0 = \frac{2000}{0.2422} = 8258\ \mathrm{kg}
$$

$$
m_p = m_0\left(1-\frac{1}{MR}\right) = 8258\times0.6778 = 5598\ \mathrm{kg}
$$

Two identical stages, 2500 m/s each, same $\delta$ and $c_e$:

$$
MR_i = e^{2500/4414.5} = 1.762,\qquad \lambda_i = 0.5676-0.08 = 0.4876
$$

Top stage first:

$$
(m_0)_2 = \frac{2000}{0.4876} = 4102\ \mathrm{kg},\qquad (m_0)_1 = \frac{(m_0)_2}{0.4876} = 8412\ \mathrm{kg}
$$

Propellant in each:

$$
m_{p,2} = 4102\times(1-0.5676) = 1773\ \mathrm{kg},\qquad m_{p,1} = 8412\times0.4324 = 3637\ \mathrm{kg}
$$

Total 5411 kg, about 190 kg less than the single stage, with the same payload and $\Delta V$; the lecture quotes "8,411" for $(m_0)_1$ (l. 314). See [[SESA2023 Exam 2024-25 Solutions]] Q2.

> [!info] Marking (5 May, ll. 182–198)
> - Significant figures are not marked, and $g=9.8$ or even 10 is accepted (ll. 138–141, 198).
> - "If you write even the wrong number I tend to give the mark" when the procedure is right. If you notice a number makes no physical sense but you are sure of the method, write a note saying so: you lose perhaps one mark instead of more.

> [!warning] Transcript slips in the review (5 May, ll. 285, 317, 322)
> The lecturer reads $\lambda$ as "0.34… 0.487" (it is 0.4876), the stage-1 propellant as "3630" (3637 kg) and the single-stage propellant as "500,098 kg" (5598 kg).

Part (iv): does altitude change the propellant mass flow through a C–D nozzle? (5 May, ll. 334–387). The jet velocity is set inside the engine by the combustion process, not by the flight speed. Once the ambient pressure is below the critical value, the nozzle is choked and the mass flow is fixed by the chamber state and the throat area: climbing further changes the exhaust expansion (and the pressure thrust) but not $\dot m$. Only if the nozzle were unchoked (possible at sea level for some designs) would altitude change the flow.

## 5. Solid and liquid rockets (Lecture 30)

- **Solid**: fuel and oxidiser are premixed in a solid grain that is also the combustion chamber, so there is no feed system. Simple and storable. But it cannot be controlled or stopped once lit, so the thrust–time profile is designed into the grain shape (the burning area). Lower $I_{sp}$. See [[SESA2023 W11 - Solid Propellants and Rocket Nozzle Design]].
- **Liquid**: needs pumps or pressurised tanks, and injectors to mix. Complex, heavy, costly, harder to store (cryogenics). But it can be throttled and restarted, and has a higher $I_{sp}$. Fuels: LH₂, RP-1/kerosene; oxidisers: LOX, N₂O₄. Monopropellants (hydrogen peroxide, hydrazine) decompose without a separate oxidiser (L30, l. 41).

Propellant choices (L30, ll. 183–233). A comparison at 100 bar chamber pressure and area ratio 45 (roughly vacuum performance):

| Propellants | Ideal $c_e$ (m/s) | Notes |
|---|---|---|
| LOX / LH₂ | about 4500 | best; hydrogen is liquid only below about 20 K, boils off and embrittles metals; Shuttle main engines, Ariane upper stages |
| LOX / CH₄ | about 3650 | methane liquid below about 110 K; SpaceX |
| LOX / RP-1 (kerosene) | lower | kerosene is liquid at ambient; heavier hydrocarbons do slightly worse |
| N₂O₄ / hydrazine | almost as good as hydrocarbons | both storable at ambient and hypergolic (ignite on contact), so ideal for restarts after years in space; hydrazine is extremely toxic |

LOX is cryogenic (liquid below about 90 K at ambient pressure).

Above about 100 bar the reactants cannot be treated as perfect gases: nitrogen's critical pressure is about 34 bar, above which there is no distinct liquid and vapour, so real-fluid models are needed (L30, ll. 23–32). The injector plate is "a plate with a thousand tiny Bunsen burners" (ll. 234–240).

**Engine classes:**

| Class | Thrust | Burn time | Notes |
|---|---|---|---|
| Boosters (solid or liquid) | 3000–8000 kN | < 150 s | e.g. the Shuttle's two solid boosters (L30, l. 135) |
| Core engines | 1000–2000 kN | about 600 s | higher $I_{sp}$; also run as boosters at lift-off |
| Upper stages | 30–150 kN | 600–1100 s | need vacuum ignition |

## 6. Liquid-rocket power cycles (Lecture 30)

The job of the cycle is to raise the chamber pressure, which needs pump power.

| Cycle | Turbine drive | Pros | Cons | Examples |
|---|---|---|---|---|
| Pressure-fed | none: tanks pressurised (helium, or self-pressurisation) | simplest, light, cheap, no start-up | tank strength caps $P_c$, so low thrust; upper stages and thrusters | Aestus (hydrazine/N₂O₄, L30, ll. 263–265) |
| Expander | fuel heated in the nozzle/chamber jacket drives the turbine (closed; a *bleed* variant dumps the turbine fuel for a larger turbine pressure ratio) | simple; clean fuel on the turbine means little wear | turbine power is limited by the heat picked up (area ∝ size², volume ∝ size³), so size-limited; not self-starting | Vinci ($I_{sp}$ 465 s, 60.8 bar, L30, ll. 337–339), RL10 |
| Gas generator (GG) | a separate small combustor; its exhaust is dumped | high turbine power, high $P_c$; throttleable | complex; GG propellant is wasted (lower $I_{sp}$); hot-gas turbine wear | F-1, Merlin 1D (L30, l. 364), Vulcain 2 |
| Staged combustion (SC) | all the fuel (or oxidiser) through a pre-burner with a little of the other; the rich turbine exhaust goes into the main chamber | highest $P_c$ (SSME > 200 bar); nothing dumped | harshest turbine conditions; most complex | SSME (L30, l. 389), RD-253 |
| Full-flow SC (legacy exams) | fuel-rich and oxidiser-rich pre-burners drive separate pumps | all propellant through the turbines; cooler turbines; no inter-propellant seal | even more complex | RD-270, Raptor |

How each cycle works (L30, ll. 242–388):

- **Pressure-fed.** Each tank must be at least at chamber pressure (plus injector and pipe losses): 100 bar in the chamber means 100 bar in a cryogenic tank, which is thick and heavy. Pressurise by self-pressurisation (heat makes a cryogen boil) or a separate helium bottle. The Aestus upper-stage engine uses hypergolic hydrazine/N₂O₄ and is rated for about 20 starts.
- **Expander.** On the fuel side it is a small Brayton cycle: pump, heat (in the nozzle cooling coil), expand through a turbine, then inject. The fuel must leave the turbine still above chamber pressure, so the pump delivers several times the chamber pressure. Only one propellant (usually the fuel) is used, partly because sealing a shaft that carries both a fuel and an oxidiser turbine against leakage, at cryogenic temperatures, is a "massive engineering headache". Heat transfer through the wall limits the turbine power, and the engine needs another source to start the pumps.
- **Gas generator.** A small separate combustor burns a bleed of fuel and oxidiser to drive the turbine. Its exhaust leaves the turbine below chamber pressure, so it is dumped overboard or sent through a small separate nozzle: wasted propellant.
- **Staged combustion.** All the fuel goes through a pre-burner with only part of the oxidiser, giving fuel-rich, incomplete combustion: enough temperature to drive the turbine. The rich exhaust then enters the main chamber, where the rest of the oxidiser completes the reaction. Nothing is dumped, but the fuel pump must deliver well above chamber pressure. On the SSME, sparks at the nozzle ignite the propellant instantly at start-up so no explosive hydrogen–oxygen cloud forms; at sea level the plume is over-expanded and shows shock diamonds.

> [!warning] Expander pump pressure (L30, ll. 298–305)
> The lecturer says the pump outlet must be "five or 10 times the pressure of the combustion chamber. Instead of it being 100 or 200 bar, it needs to be 2000 bar", then "maybe 500 bar here… expand it down to 100 bar". The figures are illustrative and not consistent; the point is that the pump must deliver well above chamber pressure so the fuel can still be injected after the turbine.

> [!warning] Vulcain is a gas-generator engine
> The Week 10 notes also list Vulcain under staged combustion; the slides (and the engine) are gas-generator. Use GG.

The expander cycle is size-limited because the heat it picks up scales with the wall area (∝ size²) while the propellant flow, and so the pump power needed, scales with the volume (∝ size³). Big engines can't pick up enough heat to drive their pumps.

---

## 7. Problem-solving workflow

1. Write the thrust equation; decide whether the nozzle is fully expanded.
2. $V_j$ from the chamber state; $c_e=g_0I_{sp}$; $\dot m=F/c_e$.
3. Throat area from the choked mass flow (use the formula, not the $\gamma=1.4$ table, when $\gamma$ differs); exit area from the area ratio.
4. $C^*$ and $C_F$; check $C^*C_F=c_e$.
5. Rocket equation: $\lambda=e^{-\Delta V/c_e}-\delta$; staging from the top down with $(m_{pl})_i=(m_0)_{i+1}$.
6. Propellant per stage $m_p=m_0(1-1/MR)$; sanity-check that $\lambda>0$ (otherwise the stage cannot deliver that $\Delta V$).

## Terminology and alternative names

| Course term | Also called | Where the course uses it | Note |
|---|---|---|---|
| effective exhaust velocity $c_e$ | equivalent exhaust velocity, $c$ | Week 10 notes | $=g_0I_{sp}$. |
| characteristic velocity $C^*$ | c-star | Week 10 notes | |
| thrust coefficient $C_F$ | — | Week 10 notes | |
| dead weight $m_{dw}$ | structural mass, inert mass | Week 10 notes, 5 May | "date weight" in the transcript. |
| structural ratio $\delta$ | dead-weight ratio, structural coefficient | Week 10 notes | Some texts define $\epsilon=m_s/(m_s+m_p)$ instead. |
| payload ratio $\lambda$ | — | Week 10 notes | |
| Tsiolkovsky equation | rocket equation | 5 May, l. 46 | |
| gas generator cycle | open cycle | L30 | |
| staged combustion | closed cycle, pre-burner cycle | L30 | |

## Links

- Parent: [[SESA2023 Propulsion Hub]] · Previous: [[SESA2023 W09 - Turbomachinery Characteristics - Coefficients, Similarity and Maps]] · Next: [[SESA2023 W11 - Solid Propellants and Rocket Nozzle Design]]
- Rocket thrust and pressure thrust: [[SESA2023 W01 - Thrust, Efficiency, Range and the ISA#Rocket|W01]] · choked flow and nozzle regimes: [[SESA2023 W03 - Compressible Flow, Normal Shocks and Nozzles]] · combustion temperatures: [[SESA2023 W05 - Combustion, Stoichiometry and Chemical Equilibrium]]
- Worked sheet: [[SESA2023 Problem Sheet 10 Rockets Solutions]] (identical to the older Sheet 6) · Formula list: [[SESA2023 Formula Sheet]]
- Exams: [[SESA2023 Exam 2022-23 Solutions]] Q2, [[SESA2023 Exam 2024-25 Solutions]] Q2, [[SESA2023 Exam 2021-22 Solutions]] Q1 (nozzle as a rocket), plus legacy power-cycle and SSTO essays (2014-15 to 2018-19)

## Sources

- `Week 10 - Rockets.pdf` (notes: Peters, Grenga, Richardson) and `Week 10 - Rockets - Lecture Slides.pdf`; Sutton, *Rocket Propulsion Elements*; Hill & Peterson (1992). The notes number these Lectures 28–30.
- Transcripts (line numbers refer to these files): LR1 `SESA2023 Lecture 25 - Rockets Introduction.txt` (28 Apr, E. Richardson: thrust, parameters, F-1); LR2 `SESA2023 Lecture 26 - Rocket staging.txt` (28 Apr: rocket equation, staging, Saturn V); L30 `SESA2023 Lecture 30.txt` (1 May: solid vs liquid, power cycles); 5 May `SESA2023 Lecture 31.txt` (T. Grenga: the 2024-25 exam rocket question).

## Self-study tasks

Tasks marked *(set)* were set or explicitly pointed to in the Week 10 lectures; the rest are suggested, not lecturer-set. Attempt each closed-book, then check against the linked section.

### Core

- [ ] *(set)* Derive the Tsiolkovsky equation: "you need to know how to derive it" (5 May, ll. 45–48). → [[#Derivation of the Tsiolkovsky equation]]
- [ ] *(set)* 2024-25 exam Q2: single- and two-stage propellant masses (5 May, ll. 115–330). Targets 5598 kg and 5411 kg. → [[#Worked example – the 2024-25 exam rocket question]]
- [ ] *(set)* F-1 engine: $V_j$, $c_e$, $\dot m$, throat and exit diameters (LR1, ll. 282–375). Targets 3213 and 2992 m/s, 0.90 and 3.6 m. → [[#Worked example – the Saturn V F-1 engine]]
- [ ] *(set)* Saturn V staging (LR2, ll. 197–264), including the single-stage comparison. → [[#Worked example – Saturn V staging]]
- [ ] *(set)* Work [[SESA2023 Problem Sheet 10 Rockets Solutions|Problem Sheet 10]] and the past-paper rocket solutions on Blackboard (5 May, ll. 325–328, 404–407).

### Further practice

- [ ] Derive $V_j$ from the SFEE and the isentropic relation. → [[#Ideal jet velocity]]
- [ ] Derive $C^*$ from the choked mass flow and show $c_e=C^*C_F$. → [[#Why the characteristic velocity measures only the combustor]]
- [ ] Show that the F-1's area ratio of 16 implies a design altitude of about 7 km at $\gamma=1.24$. → [[#Worked example – the Saturn V F-1 engine]]
- [ ] Compare the four power cycles in a table from memory, with one engine each. → [[#6. Liquid-rocket power cycles (Lecture 30)]]
- [ ] Explain the gravity-turn compromise between drag and gravity losses. → [[#Losses]]
- [ ] *(2024-25 Q2(iv))* Explain whether altitude changes the propellant mass flow through a C–D nozzle. → [[#Worked example – the 2024-25 exam rocket question]]
- [ ] Compare LOX/LH₂, LOX/CH₄, LOX/RP-1 and N₂O₄/hydrazine on performance and storability. → [[#5. Solid and liquid rockets (Lecture 30)]]
- [ ] Give two reasons for staging besides shedding dead weight. → [[#Relations]]
