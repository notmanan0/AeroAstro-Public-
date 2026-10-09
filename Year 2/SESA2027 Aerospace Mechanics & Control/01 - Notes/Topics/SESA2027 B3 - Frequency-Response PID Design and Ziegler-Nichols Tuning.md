---
title: "SESA2027 B3 - Frequency-Response PID Design and Ziegler-Nichols Tuning"
module: "SESA2027 Aerospace Mechanics & Control"
type: topic
stream: "Part B: Control Systems"
order: 8
tags:
  - sesa2027
  - pid-tuning
  - frequency-response-design
  - ziegler-nichols
aliases: ["PID Tuning", "Frequency-Response Design"]
date: 2026-09-23
status: complete
parent: ["[[SESA2027 Aerospace Mechanics & Control Hub]]"]
prerequisites: ["[[SESA2027 B2 - Root Locus Method]]", "[[SESA2027 A5 - Frequency Response and Bode Plots]]"]
next_topics: ["[[SESA2027 B4 - Robustness, Stability vs Manoeuvrability and Design Process]]"]
key_concepts: ["[[Gain and Phase Margins]]", "[[PID Controller]]", "[[Ziegler-Nichols Tuning]]", "[[Bode Plot]]"]
tutorial_sheets: ["[[SESA2027 Practice Problems 2 Solutions]]"]
sources: ["02 - Sources/Lectures/Lecture 2.05.pdf", "02 - Sources/Lectures/Lecture 2.06.pdf"]
---

# SESA2027 B3 - Frequency-Response PID Design and Ziegler-Nichols Tuning

> [!abstract] Summary
> Frequency-response design shapes the **open-loop** Bode plot of $C(s)G(s)$:
> 1. Choose a gain crossover $\omega_{gc}$.
> 2. Use the D term to add the phase lead needed for a target **phase margin**.
> 3. Set $T_I$ well below $\omega_{gc}$ to remove steady-state error.
> 4. Set $K_p$ so that $|CG| = 1$ at $\omega_{gc}$.
>
> **Ziegler–Nichols** is an empirical alternative. Find the ultimate gain $K_u$ and period $T_u$ that give sustained oscillation, then read the gains off a table. It is quick but aggressive.

## Key Concepts
- [[Gain and Phase Margins]] · [[PID Controller]] · [[Ziegler-Nichols Tuning]]

---

## 1. Why frequency-response design (L2.05)

| Advantages | Disadvantages |
|---|---|
| Explicit control of phase and gain margins | Needs an accurate frequency-response model |
| Strong insight into robustness | More complex than simple tuning rules |
| Shows noise amplification and filtering | Time-domain behaviour is only inferred indirectly |
| Naturally suits PD/PID design | D action may amplify noise |
| Good for lightly damped or flexible systems | Less effective for nonlinear or saturated plants |
| Bandwidth and crossover tuned directly | Phase-lag-dominated systems can be hard to stabilise |

**Gain margin (GM)**: how much the open-loop gain can increase before the closed loop becomes unstable. It is measured at the **phase crossover frequency**, where the phase is −180°:

$$
GM = -|L(i\omega_{pc})|_{dB}
$$

**Phase margin (PM)**: the extra phase lag that would bring the loop to the verge of instability. It is measured at the **gain crossover frequency**, where $|L| = 0$ dB:

$$
PM = 180^\circ+\angle L(i\omega_{gc})
$$

![[amc_gain_phase_margins.png|600]]

## 2. PID in standard (time-constant) form

$$
C(s) = K_P+\frac{K_I}{s}+K_Ds = K_p\left[1+\frac{1}{T_Is}+T_Ds\right],\qquad T_I = \frac{K_p}{K_I},\quad T_D = \frac{K_D}{K_p}
$$

- **$T_I$** (integral, or reset, time): how fast the error integral accumulates. A smaller $T_I$ removes steady-state error faster but risks oscillation.
- **$T_D$** (derivative, or rate, time): how strongly the controller reacts to the error rate. A larger $T_D$ adds damping but is more sensitive to noise.

## 3. Eight-step frequency-response design
1. Plot the plant Bode diagram. Identify the current PM, the current $\omega_{gc}$, and where the phase is deficient.
2. **Choose $\omega_{gc}$**. Higher gives a faster response but less noise attenuation. Lower gives a slower, more robust response.
3. **Required phase lead**: $\phi_{PD} = \phi_{desired}-(180^\circ+\phi_{current})$, where $\phi_{current} = \angle G(i\omega_{gc})$.
4. **Controller type**: PD if phase lead is needed, adding I if steady-state error must be removed.
5. **Derivative time**: a PD controller $(1+T_Ds)$ contributes $\phi_{PD} = \tan^{-1}(\omega_{gc}T_D)$, so

$$
T_D = \frac{\tan\phi_{PD}}{\omega_{gc}}
$$

6. **Integral time**: $T_I = 3/\omega_{gc}$. This keeps the integrator's phase lag well below crossover.
7. **Gain**: set

$$
|K_pG(i\omega_{gc})(1+i\omega_{gc}T_D)| = 1\;\Rightarrow\;K_p = \frac{1}{|G(i\omega_{gc})|\sqrt{1+(\omega_{gc}T_D)^2}}
$$

   This ensures the crossover is exactly $\omega_{gc}$.
8. **Validate in the time domain**: check overshoot, settling time and damping, and that the actuator effort is acceptable.

> [!example] Lecture example: SPO pitch rate
> The plant is $G = \dfrac{-1.39(s+0.306)}{s^2+0.805s+1.325}$. The negative gain makes the low-frequency phase about $-180^\circ$. To simplify, invert the response by multiplying the gain by −1.
>
> 1. Current $\omega_{gc}\approx1.87$ rad/s. Desired $\omega_{gc} = 3$ rad/s.
> 2. The slide takes $\phi_{current} = -64.3^\circ$ and $\phi_{desired} = 70^\circ$, giving $\phi_{PD} = 70-(180-64.3) = -45.7^\circ$. The negative sign comes from the inversion, so use $|\phi_{PD}| = 45.7^\circ$.
> 3. $T_D = \tan(45.7^\circ)/3 = 0.342$ s.
> 4. $T_I = 3/\omega_{gc} = 1.0$ s.
> 5. $|G(3i)| = 0.519$ and $|1+3T_Di| = \sqrt{1+1.026^2} = 1.433$, so $K_p = \dfrac{1}{0.519\times1.433} = 1.345$.
>
> **Gains**: $K_p = 1.345$, $K_i = K_p/T_I = 1.345$, $K_d = K_pT_D = 0.46$.
>
> The PID removes the steady-state error that P and PD leave behind.

![[amc_pid_design_validation.png|620]]

> [!example] PS2 Q7: $|G(3i)| = 0.25$, $\angle G = -155^\circ$, target PM $=55^\circ$
> - $\phi_{PD} = 55-(180-155) = 30^\circ$
> - $T_D = \tan30^\circ/3 = 0.192$ s
> - $K_p = \dfrac{1}{0.25\times1.1547} = 3.46$

## 4. PID tuning algorithms (L2.06)

| Method | Key points | vs Ziegler–Nichols |
|---|---|---|
| Manual (trial and error) | Iterate $K_p$, $K_i$, $K_d$ by hand | Safer and flexible, but slow and inconsistent |
| **Ziegler–Nichols** | Empirical, based on sustained oscillation | Fast, aggressive, large overshoot; a good starting point |
| Tyreus–Luyben | Modified ZN | More robust, less overshoot, slower |
| Cohen–Coon | For first-order-plus-dead-time (FOPDT) processes | Better with delay, but needs a process model |
| Lambda ($\lambda$) | Choose the closed-loop time constant | Very robust and predictable, but slow if $\lambda$ is large |

### Ziegler–Nichols: quarter-decay (reaction-curve) method
Apply an open-loop step. The response must be S-shaped and overdamped, with no integrators. Measure the apparent delay $L$, the time constant $\tau$ and the slope $R = A/\tau$:

| Controller | $K_p$ | $T_I$ | $T_D$ |
|---|---|---|---|
| P | $1/(RL)$ | – | – |
| PI | $0.9/(RL)$ | $L/0.3$ | – |
| PID | $1.2/(RL)$ | $2L$ | $0.5L$ |

### Ziegler–Nichols: ultimate sensitivity method
1. Remove I and D (P only) and close the loop.
2. Increase $K_p$ until the output shows **sustained oscillation**. That gain is the ultimate gain $K_u$, and the oscillation period is $T_u$.
3. Apply the table:

| Controller | $K_p$ | $T_I$ | $T_D$ |
|---|---|---|---|
| P | $0.5K_u$ | – | – |
| PI | $0.45K_u$ | $T_u/1.2$ | – |
| PID | $0.6K_u$ | $0.5T_u$ | $0.125T_u$ |

> [!example] Lecture: DC servo $G = \dfrac{336}{s^3+34s^2+47s+336}$ (poles $-32.88$, $-0.56\pm3.15i$)
> The ultimate gain lies between 2.5 and 4. The experiment gives $K_u\approx3.7$ and $T_u\approx0.924$ s:
> - **P**: $K_p = 1.85$
> - **PI**: $K_p = 1.665$, $T_I = 0.77$ s
> - **PID**: $K_p = 2.22$, $T_I = 0.462$ s, $T_D = 0.1155$ s
>
> The slide prints $K_p = 1.22$ for the PID, but $0.6\times3.7 = 2.22$.

> [!warning] ZN is aggressive
> It targets quarter-amplitude decay, which means about 25% overshoot and low damping ($\zeta\approx0.2$). Aerospace systems need refinement because of handling-qualities limits (FAR/MIL), passenger comfort, actuator limits and robustness to uncertainty.

## Links
- Parent: [[SESA2027 Aerospace Mechanics & Control Hub]] · Previous: [[SESA2027 B2 - Root Locus Method]] · Next: [[SESA2027 B4 - Robustness, Stability vs Manoeuvrability and Design Process]]

## Sources
- Lectures 2.05–2.06; Franklin, Powell & Emami-Naeini (2014) Ch. 6.3–6.6
