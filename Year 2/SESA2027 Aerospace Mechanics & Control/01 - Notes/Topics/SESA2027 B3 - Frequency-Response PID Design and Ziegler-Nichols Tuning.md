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
status: lectured
coverage: "L2.05 (frequency-response PID design; corrected deck), L2.06 (PID tuning, Ziegler–Nichols)"
parent: ["[[SESA2027 Aerospace Mechanics & Control Hub]]"]
prerequisites: ["[[SESA2027 B2 - Root Locus Method]]", "[[SESA2027 A5 - Frequency Response and Bode Plots]]"]
next_topics: ["[[SESA2027 B4 - Robustness, Stability vs Manoeuvrability and Design Process]]"]
key_concepts: ["[[Gain and Phase Margins]]", "[[PID Controller]]", "[[Ziegler-Nichols Tuning]]", "[[Bode Plot]]"]
tutorial_sheets: ["[[SESA2027 Practice Problems 2 Solutions]]"]
sources: ["02 - Sources/Lectures/Lecture 2.05.pdf", "02 - Sources/Lectures/Lecture 2.06.pdf", "02 - Sources/Lectures/Lecture 2.05 recording.txt", "02 - Sources/Lectures/Lecture 2.06 recording.txt", "02 - Sources/Lectures/Lecture 2.07 recording.txt"]
---

# SESA2027 B3 - Frequency-Response PID Design and Ziegler-Nichols Tuning

> [!abstract] Summary
> Frequency-response design shapes the open-loop Bode plot of $C(s)G(s)$: choose a gain crossover $\omega_{gc}$, use the D term to add the phase lead needed for a target phase margin, place $T_I$ well below crossover to remove steady-state error, and set $K_p$ so that $|CG| = 1$ at $\omega_{gc}$. Ziegler–Nichols is the empirical alternative: find the ultimate gain $K_u$ and period $T_u$ that give sustained oscillation, then read the gains off a table. It is quick but aggressive.

> [!warning] L2.05 was delivered from an uncorrected deck: follow the slides
> The frequency-response design example was taught on Thursday 5 March 2026 from a version of the slides that left out the sign inversion. The lecturer re-issued the deck the next day: "on Friday, I made an announcement. I realized I made some omissions on this slide, so I made some updates in there … download the newer version of the slides" (L2.07, ll. 43–46). The filed `Lecture 2.05.pdf` is that corrected version (created Friday 6 March 2026, 13:58). These notes follow the corrected slides. What differs is listed in [[#What was said in L2.05 vs the corrected slides]].

> [!summary]- Exam use: quick path
> - **Use it when:** a question gives a Bode plot and asks for GM and PM (±5 % tolerance, L2.05, ll. 183–188); gives $\lvert G(i\omega_{gc})\rvert$, $\angle G(i\omega_{gc})$ and a target PM and asks for $T_D$, $T_I$, $K_p$; or gives $K_u$, $T_u$ (or a reaction curve) and asks for ZN gains or a comparison of tuning methods.
> - **Assumptions:** margins are read on the open-loop $L=CG$; standard PID form $K_p[1+1/(T_Is)+T_Ds]$; a negative-gain plant is inverted for the design and the sign restored on $K_p$ at the end; ZN needs a plant that can be driven to sustained oscillation (ultimate method) or an S-shaped open-loop step (reaction curve).
> - **Method:** 1. $\phi_{PD}=\phi_{desired}-(180°+\phi_{current})$. 2. $T_D=\tan\phi_{PD}/\omega_{gc}$. 3. $T_I=3/\omega_{gc}$. 4. $K_p=1/\left(\lvert G(i\omega_{gc})\rvert\sqrt{1+(\omega_{gc}T_D)^2}\right)$. 5. Validate the step response and the control effort. (ZN instead: $K_p=0.6K_u$, $T_I=0.5T_u$, $T_D=0.125T_u$.)
> - **Common mistakes:** reading PM at the phase crossover or GM at the gain crossover (swap them); forgetting to restore the negative sign of $K_p$ for the real SPO plant.
> - **Practise:** [[#3. Eight-step frequency-response design]] (lecture example) · [[SESA2027 Mock Questions#Q8. Margins and PD design|Mock Q8]] · [[SESA2027 Practice Problems 2 Solutions]] (Q7–Q8)

A feedback loop goes unstable when a signal can travel round it and come back the same size and upside down: then it reinforces itself forever. On a Bode plot of the open loop $CG$, "the same size" is the 0 dB line and "upside down" is −180°. The gain margin says how much louder the loop could be before the −180° frequency reaches 0 dB; the phase margin says how much extra lag the loop could take before the 0 dB frequency reaches −180°. Margins are a safety factor against everything the model got wrong.

Frequency-response design picks the frequency at which the loop should cross 0 dB (that sets how fast the closed loop responds), uses the derivative term to buy back phase there (that sets the margin, hence the damping), parks the integral term at a lower frequency where its phase lag does little harm, and finally scales the gain so the crossover lands where intended. Ziegler–Nichols skips the model: push the gain until the loop just oscillates, measure that gain and period, and back off by rule-of-thumb factors.

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

**Gain margin (GM)**: how much the open-loop gain can increase before the closed loop becomes unstable. It is measured at the phase crossover frequency, where the phase is −180°:

$$
GM = -|L(i\omega_{pc})|_{dB}
$$

**Phase margin (PM)**: the extra phase lag that would bring the loop to the verge of instability. It is measured at the gain crossover frequency, where $|L| = 0$ dB:

$$
PM = 180^\circ+\angle L(i\omega_{gc})
$$

![[amc_gain_phase_margins.png|600]]

**Why these two numbers measure the distance to instability.** The closed-loop poles are the roots of $1+L(s)=0$. A pole on the imaginary axis, $s=i\omega$, means

$$
L(i\omega)=-1\quad\Leftrightarrow\quad\lvert L(i\omega)\rvert=1\ \text{(0 dB)}\ \text{and}\ \angle L(i\omega)=-180°
$$

both at the same frequency. At $\omega_{pc}$ the phase condition already holds, so multiplying the gain by $1/\lvert L(i\omega_{pc})\rvert$ would satisfy the magnitude condition too. In dB that factor is $-\lvert L(i\omega_{pc})\rvert_{dB}$, the GM. At $\omega_{gc}$ the magnitude condition holds, so adding a pure lag of $180°+\angle L(i\omega_{gc})$ would satisfy the phase condition, the PM. (This assumes the open loop is stable and the plot crosses 0 dB once, as for every plant in this module.)

> [!info] Exam use of the margins (L2.05)
> - "If an exam or in the quiz I was to tell you I have this graph, and tell me what is the phase margin or … the gain margin": read them off the Bode plot. Draw a vertical line from the −180° crossing up to the magnitude plot for GM, and from the 0 dB crossing down to the phase plot for PM. A tolerance of about ±5 % will be allowed (ll. 157–188).
> - If the phase never reaches −180°, the phase-crossover frequency is infinite and GM is infinite. "That would be a nice exam question" (ll. 466–476, corrected at ll. 498–504).

The lecturer prefers this method to the root locus (L2.05, ll. 83–114). It lets you tune more than one gain at a time, shows the controller's effect on steady-state error before you simulate, and works even if the model is only approximately right, as long as it captures the main dynamics: "if you have the opportunity to build a transfer function model, this would be my method of choice." The Bode plot can also be measured, by exciting the system at increasing frequencies with small amplitudes (a CubeSat on a tether, a gimbal), or with a chirp, doublet or 3-2-1-1 input as in aircraft flight testing. The amplitude is kept small so as not to excite unstable dynamics or break the rig (ll. 1–73).

> [!note] Flight-test inputs (L2.05, ll. 52–64)
> Nobody wants to ride in an aircraft that is oscillating continuously, so aircraft are identified with short elevator inputs:
> - **Pulse**: deflect the elevator once, then return it to trim.
> - **Doublet**: deflect one way, then the other way, then back to trim. It is the simplest and "very, very effective".
> - **3-2-1-1**: like a doublet, but with alternating segments lasting 3, 2, 1 and 1 time units.
>
> The different inputs put their energy in different frequency bands.

## 2. PID in standard (time-constant) form

$$
C(s) = K_P+\frac{K_I}{s}+K_Ds = K_p\left[1+\frac{1}{T_Is}+T_Ds\right],\qquad T_I = \frac{K_p}{K_I},\quad T_D = \frac{K_D}{K_p}
$$

- $T_I$ (integral, or reset, time): how fast the error integral accumulates. A smaller $T_I$ removes steady-state error faster but risks oscillation.
- $T_D$ (derivative, or rate, time): how strongly the controller reacts to the error rate. A larger $T_D$ adds damping but is more sensitive to noise.

**From parallel to standard form, line by line.** Factor $K_p$ out of the parallel form (assumes $K_p\neq0$):

$$
C(s) = K_p+\frac{K_I}{s}+K_Ds
$$

$$
C(s) = K_p\left[1+\frac{K_I}{K_p}\frac1s+\frac{K_D}{K_p}s\right]
$$

$$
C(s) = K_p\left[1+\frac{1}{T_Is}+T_Ds\right],\qquad T_I = \frac{K_p}{K_I},\quad T_D = \frac{K_D}{K_p}
$$

"I'm collecting terms, so that I only have one gain … that controls everything" (L2.05, ll. 214–218). The lecturer said this form is needed for both the frequency-response method and Ziegler–Nichols, and that the slide should say so (ll. 200–215); the filed slide 5 still mentions only Ziegler–Nichols.

The lecture describes $T_I$ and $T_D$ as times you can picture, unlike $K_I$ and $K_D$ (L2.05, ll. 222–247). More precisely, for a constant error $e_0$ the integral term $K_pe_0t/T_I$ equals the proportional term $K_pe_0$ after $t = T_I$, the reset time, and for a ramp error the derivative term equals the change in the proportional term over $T_D$, a look-ahead time. $T_I$ sits in the denominator of $1/(T_Is)$, so a smaller $T_I$ means stronger integral action. Noisy gimbal loops are usually a $T_D$ problem, fixed by filtering the error derivative (ll. 248–253).

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

**Where steps 5–7 come from.** The PID bracket factorises approximately as a PD factor times an integral factor (exact if the cross term $T_D/T_I$ is neglected):

$$
1+\frac{1}{T_Is}+T_Ds\approx(1+T_Ds)\left(1+\frac{1}{T_Is}\right)
$$

- **Step 5.** At $s=i\omega$ the PD factor is $1+i\omega T_D$, a complex number with real part 1 and imaginary part $\omega T_D$. Its phase is $\tan^{-1}(\omega T_D)$. Setting that equal to $\phi_{PD}$ at $\omega_{gc}$ and solving gives $T_D=\tan\phi_{PD}/\omega_{gc}$.
- **Step 6.** The integral factor is $1+1/(i\omega T_I)=1-i/(\omega T_I)$, with phase $-\tan^{-1}\left(1/(\omega T_I)\right)$. With $T_I=3/\omega_{gc}$ its phase at crossover is $-\tan^{-1}(1/3)=-18.4°$. That is the price of zero steady-state error, and it is why the final margin differs from the target unless step 3 allows for it.
- **Step 7.** At crossover $\lvert CG\rvert=1$. The PD factor has magnitude $\sqrt{1+(\omega_{gc}T_D)^2}$, so $K_p\lvert G(i\omega_{gc})\rvert\sqrt{1+(\omega_{gc}T_D)^2}=1$. The integral factor's magnitude at crossover, $\sqrt{1+1/9}=1.054$, is neglected, which is one reason the realised crossover moves (the check below).

![[amc_pid_factor_phase.png|760]]

> [!info] Practical points from the lecture (L2.05)
> - Step 2: move $\omega_{gc}$ in small increments. If the plant crosses over at about 1 rad/s, "you cannot go crazy and go, well, I want to go at 10" (ll. 294–304).
> - Step 3: the target phase margin comes from the client, the user or the exam question (ll. 266–268).
> - Step 6: $T_I = 3/\omega_{gc}$ is a rule of thumb. A higher crossover means a smaller $T_I$ (ll. 323–330).
> - Step 8: look at the control action, not just the output. At $t = 0$ the largest contributions come from P, then D (the lecturer first said D, then corrected himself, ll. 554–557). Gains that demand control rates of hundreds per second are not achievable by a real actuator (ll. 356–368, 549–565).

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
>
> Where $\phi_{current}$ is read (slides 14–15): at the plant's current gain crossover, 1.87 rad/s. The inverted plant $G_+ = 1.39(s+0.306)/(s^2+0.805s+1.325)$ has $\angle G_+(1.87i) = -64.6^\circ$ (computed), which the slide rounds to $-64.3^\circ$. This is a phase, not a phase margin: the inverted plant's phase margin is $180^\circ-64.3^\circ = 115.7^\circ$, already above the 70° target, which is why the formula returns a negative number.
>
> **Sign of the implemented gains.** The gains above are for the inverted plant $G_+$. The real plant is $-G_+$, so the controller actually implemented on the aircraft has $K_p = -1.345$ (and therefore $K_i = -1.345$, $K_d = -0.46$), with $T_I = 1.0$ s and $T_D = 0.342$ s unchanged and positive. The closed loop is identical, because $(-C)(-G_+) = CG_+$. This is the "change the sign again of the gains" step the lecturer described (L2.05, ll. 407–413), and it matches the sign rules in [[SESA2027 B4 - Robustness, Stability vs Manoeuvrability and Design Process#1. Allowable gain signs (L2.07)|B4 §1]].

> [!check] What the designed loop actually achieves (computed)
> - $\vert G_+(3i)\vert = 0.521$ (slide: 0.519) and $\angle G_+(3i) = -78.4^\circ$.
> - $K_p = 1/(0.519\times1.433) = 1.345$ ✓.
> - Step 7 sizes $K_p$ with the PD factor only. With the integral factor included as well, the open loop $C(s)G_+(s)$ crosses 0 dB at about 2.42 rad/s (not exactly 3) with a phase margin of about 129°. This is why step 8, validating in the time domain, is part of the method.

![[amc_pid_design_validation.png|620]]

### What was said in L2.05 vs the corrected slides

> [!warning] Lecture as delivered (L2.05, Thursday 5 March 2026) vs corrected deck (Friday 6 March 2026)
> | Point | Said in the lecture | Corrected slides (follow these) |
> |---|---|---|
> | Plant used | Presented the example directly with a positive numerator, $1.39(s+0.306)/(s^2+0.805s+1.325)$, explaining that the sign had been removed to simplify the analysis; "the gain would be simply 1.39" (ll. 371–432) | Slides 11–12 first show the true plant with gain −1.39, its step response and its Bode plot, with the note that the low-frequency phase is about −180° because of the negative gain. Slide 13 then inverts it explicitly ("multiplying the gain by −1") and shows that only the sign of the step response changes |
> | Phase margin of the plant | "You have an infinite phase margin for this system … That would be a nice exam question" (ll. 466–476). Retracted: "The infinite value wouldn't be the phase margin. It would be the phase crossover frequency" (ll. 498–504) | Phase crossover at infinity (the phase of $G_+$ never reaches −180°) |
> | $\phi_{current}$ | "About 65 degrees for phase margin" (ll. 505–508) | $\phi_{current} = -64.3^\circ$, the open-loop phase at $\omega_{gc} = 1.87$ rad/s (slide 15). The inverted plant's PM is $115.7^\circ$ |
> | Required phase lead | "Desired minus 180 plus phi current, which would be 45.7 degrees" (ll. 510–512) | $\phi_{PD} = 70-(180-64.3) = -45.7^\circ$; "this negative result is due to the system's response inversion … we need to change the sign of this result" (slide 15) |
> | Sign of the final gains | "Remove the sign, do the analysis, and then at the end, you change the sign again of the gains" (ll. 407–413) | Slide 17 lists the gains for the inverted plant ($K_p = 1.345$). For the real aircraft, use $K_p<0$ (see the sign note in the example above and L2.07 slide 5) |
> | Which methods need the standard PID form | Both frequency-response design and Ziegler–Nichols; "I'll make a change on the slides" (ll. 200–215) | Slide 5 still says only Ziegler–Nichols; treat it as applying to both |
>
> Unchanged between the two: the eight steps, $\omega_{gc}$ from 1.87 to 3 rad/s, $\phi_{desired} = 70^\circ$, $T_D = 0.342$ s, $T_I = 1.0$ s, $K_p = 1.345$, $K_i = 1.345$, $K_d = 0.46$, and the step-response comparison.
>
> **Why it matters in an exam.** A negative plant gain puts the low-frequency phase at −180°, so a margin read straight off its Bode plot looks absurd ("phase margins that are minus 225 degrees", ll. 414–419). Use the corrected recipe: invert the plant and note it; read $\phi_{current}$ as the phase at the crossover; apply $\phi_{PD} = \phi_{desired}-(180^\circ+\phi_{current})$; if the result is negative only because of the inversion, take its magnitude; then restore the sign of $K_p$ for the real plant.

> [!example] PS2 Q7: $|G(3i)| = 0.25$, $\angle G = -155^\circ$, target PM $=55^\circ$
> - $\phi_{PD} = 55-(180-155) = 30^\circ$
> - $T_D = \tan30^\circ/3 = 0.192$ s
> - $K_p = \dfrac{1}{0.25\times1.1547} = 3.46$

## 4. PID tuning algorithms (L2.06)

| Method | Key points | vs Ziegler–Nichols |
|---|---|---|
| Manual (trial and error) | Iterate $K_p$, $K_i$, $K_d$ by hand; needs experience, and was normally used only on plants that were already stable (L2.06, ll. 22–27) | Safer and flexible, but slow and inconsistent |
| Ziegler–Nichols | Empirical, based on sustained oscillation | Fast, aggressive, large overshoot; a good starting point |
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
2. Increase $K_p$ until the output shows sustained oscillation. That gain is the ultimate gain $K_u$, and the oscillation period is $T_u$.
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
>
> Refined gains (slide 13): $K_p = 2.66$, $T_I = 0.462$ s, $T_D = 0.289$ s, i.e. $K_i = K_p/T_I = 5.76$ and $K_d = K_pT_D = 0.769$. The lecturer kept $T_I$ from the ZN table and hand-tuned only $K_p$ and $T_D$ (L2.06, ll. 298–305). The result reaches the reference in about 2 s with a rise time under 0.5 s, almost no overshoot and a peak control action under 25 (ll. 288–297).
>
> What the three ZN controllers did (ll. 277–297): P alone stays oscillatory; PI tracks the reference but with large overshoot and undershoot; PID (refined) is well behaved.

> [!check] Ultimate gain from Routh–Hurwitz (computed)
> With $C = K$ the closed-loop characteristic polynomial is $s^3+34s^2+47s+336(1+K)$. For a cubic $s^3+a_2s^2+a_1s+a_0$, marginal stability occurs at $a_2a_1 = a_0$:
>
> $$34\times47 = 336(1+K_u)\;\Rightarrow\;K_u = \frac{1598}{336}-1 = 3.76$$
>
> The oscillation is then at $\omega_u = \sqrt{a_1} = \sqrt{47} = 6.86$ rad/s, so $T_u = 2\pi/6.86 = 0.917$ s. The simulated "experiment" gave $K_u\approx3.7$ and $T_u\approx0.924$ s, a good match. The poles quoted on the slide check out: $-32.88$ and $-0.56\pm3.15i$.

> [!info] Lecturer's practical advice on ZN (L2.06)
> - Ultimate-gain tests are risky: "don't be on board an aircraft when someone is tuning a PID using this method". Large gains can push the aircraft out of its linear range, even into a stall. Start with small amplitudes (ll. 113–142).
> - Measure $T_u$ over several cycles, not one, for a robust estimate (ll. 166–170).
> - Sample fast enough when logging. Nyquist requires at least twice the signal frequency; in practice sample at about 10 times the characteristic frequency (ll. 84–90). This returns in Part C.
> - Real hardware oscillates more readily than a clean simulation, because of backlash, nonlinearities and delays. That is why the example uses a made-up servo model, and quiz systems will be similarly simplified (ll. 177–209).
> - The servo model is third order because voltage → current → speed → angle. Its numerator equals the constant term of the denominator, so the DC gain is 1 and the open loop reaches the reference (ll. 184–204).
> - The reaction-curve method needs a plant that is open-loop stable and overdamped, with an S-shaped step response and no integrators (ll. 98–110).

> [!warning] ZN is aggressive
> It targets a quarter-decay ratio: each overshoot peak is a quarter of the one before (L2.06, ll. 64–65). For a dominant second-order pair that means $\zeta\approx0.22$ and a first overshoot of about 50 % (derived below). An earlier version of this note said "about 25 % overshoot"; that confuses the decay ratio with the overshoot, and the slides do not give a figure. Aerospace systems need refinement because of handling-qualities limits (FAR/MIL), passenger comfort, actuator limits and robustness to uncertainty.

**What quarter decay implies.** For an underdamped second-order step response the overshoot peaks occur at $\omega_dt=\pi,3\pi,5\pi,\dots$ and the envelope is $e^{-\zeta\omega_nt}$. One full period separates the first and second overshoot peaks, so their ratio is

$$
\frac{C}{A}=e^{-\zeta\omega_n\cdot2\pi/\omega_d}=e^{-2\pi\zeta/\sqrt{1-\zeta^2}}=\frac14
$$

Take logs: $2\pi\zeta/\sqrt{1-\zeta^2}=\ln4$. Square and solve for $\zeta$:

$$
\zeta=\frac{\ln4}{\sqrt{4\pi^2+(\ln4)^2}}=\frac{1.386}{6.437}=0.215
$$

The first overshoot is $A=e^{-\pi\zeta/\sqrt{1-\zeta^2}}=\sqrt{C/A}=\sqrt{1/4}=0.50$.

![[amc_quarter_decay.png|720]]

## Lecturer emphasis and exam hints (transcripts)

> [!info] Exam and quiz signals
> - Read GM and PM off a given Bode plot, with about ±5 % tolerance (L2.05, ll. 183–188).
> - Infinite phase-crossover frequency (hence infinite GM) for a plant whose phase never reaches −180°: "a nice exam question" (L2.05, l. 476).
> - Compare tuning methods: "What are the advantages of this method against this method? Or … of Ziegler–Nichols over all of these methods?" is "a really nice quiz question" (L2.06, ll. 52–59).
> - Quiz plants will be simplified, like the made-up servo (L2.06, ll. 206–209).
> - Further reading: Franklin et al. Ch. 6.3–6.6 (L2.05, l. 574) and Ch. 4 (L2.06, l. 320).

## Transcript slips

> [!warning] Speech-to-text and spoken slips, with the correct version
> The content differences between the L2.05 delivery and the corrected slides are in [[#What was said in L2.05 vs the corrected slides]]. Smaller slips:
>
> | Where | Transcript says | Correct |
> |---|---|---|
> | L2.05, ll. 4, 117 | "body plot" | Bode plot |
> | L2.05, ll. 7, 13 | "the SPL", "the fuboid", "fugoid" | SPO, phugoid |
> | L2.05, l. 39 | "then it starts athenoid" | starts to attenuate |
> | L2.05, ll. 48–49 | "Arrinos … flood point unit … true flows" | Arduinos have no floating-point unit, so they handle floats slowly |
> | L2.05, l. 55 | "a unilet" | a single pulse (one elevator deflection and back) |
> | L2.05, l. 87 | "cotter frequency" | cut-off frequency |
> | L2.05, l. 112 | "phase-like dominated systems" | phase-lag-dominated systems |
> | L2.05, ll. 136–137 | "every time we increase the integrator part, so third order system" | every extra pole adds −20 dB/decade |
> | L2.05, l. 140 | "from minus 40 to 60" | a 60 dB drop over that decade |
> | L2.05, l. 202 | "the Ziegler-Nickel-Spinning method" | the Ziegler–Nichols tuning method |
> | L2.05, ll. 233–234 | "the smaller Ti, because it's on the numerator in here, the bigger this term" | $T_I$ is in the denominator of $1/(T_Is)$, which is why a smaller $T_I$ gives a bigger integral term |
> | L2.05, l. 277 | "the integral time EI" | $T_I$ |
> | L2.05, l. 297 | "one region per second" | 1 rad/s |
> | L2.05, l. 302 | "not be automating the noise" | not attenuating the noise |
> | L2.05, ll. 344–346 | the gain "crossover frequency in close loop" | the open-loop gain crossover $\omega_{gc}$ of $CG$ |
> | L2.05, ll. 398–399 | "deflected in a negative sense, that produces a positive deflection" | a negative elevator deflection produces a positive (nose-up) pitch |
> | L2.05, ll. 474, 505, 512 | "infinite phase margin", "65 degrees for phase margin", "+45.7°" | see the comparison table above |
> | L2.05, ll. 554–557 | "first, the derivative, and then second … sorry. First, the proportional" | P first, then D (self-corrected) |
> | L2.06, ll. 3, 55, 95, 211, 268, 301 | "Siegler-Nichols", "Siegel-Nichols", "Seager-Nichols", "Siegler, Nicol, Steiner", "Siegel and EcoTuner" | Ziegler–Nichols |
> | L2.06, l. 30 | "Tyreus-Lubin" | Tyreus–Luyben |
> | L2.06, l. 34 | "Cohen-Kuhn" | Cohen–Coon |
> | L2.06, ll. 64–69 | the quarter decay is described on the open-loop process curve: "in this case it's not oscillatory. Continuously decaying … so that the decay is 0.25" | the open-loop reaction curve is indeed not oscillatory. The 0.25 is the decay ratio between successive peaks of the closed-loop response that the tuned gains produce (derived in §4) |
> | L2.06, l. 98 | "quarter-decade ratio" | quarter-decay ratio |
> | L2.06, l. 105 | "you cannot have pulse at zero" | no poles at zero (no integrators) |
> | L2.06, l. 131 | (student) "the system becomes more unstable" | sustained oscillation means marginally stable (l. 136) |
> | L2.06, l. 134 | "either unstable or unstable" | either stable or unstable |
> | L2.06, ll. 213–215 | "in the slides I have Sn, it should be Zn" | slide 7 reads "Apply SN Ultimate sensitivity method": read ZN. The filed deck (dated 3 March) still has the typo |
> | L2.06, l. 265 | $T_u$ "about 0.9 seconds … I forgot to include the units" | $T_u = 0.924$ s |

## Terminology and alternative names

| Course term | Also called | Where the course uses it | Note |
|---|---|---|---|
| gain margin (GM) | gain safety factor; also quoted as a ratio rather than in dB | L2.05 | the course quotes dB |
| phase margin (PM) | phase safety margin | L2.05 | |
| gain crossover frequency $\omega_{gc}$ | crossover frequency, 0 dB crossing | L2.05 | measured on the open loop |
| phase crossover frequency $\omega_{pc}$ | −180° crossing | L2.05 | can be infinite |
| standard (time-constant) PID form | ideal / ISA form, non-interacting form | L2.05 slide 5 | parallel form uses $K_P,K_I,K_D$ |
| integral time $T_I$ | reset time | L2.05 | |
| derivative time $T_D$ | rate time | L2.05 | |
| frequency-response design | loop shaping, Bode design | L2.05 | |
| ultimate gain $K_u$, ultimate period $T_u$ | critical gain $K_{cr}$, critical period $P_{cr}$ | L2.06 | |
| quarter-decay ratio method (reaction curve) | process reaction curve method, open-loop ZN | L2.06 | the slides use "quarter decay ratio" for this method |
| ultimate sensitivity method | closed-loop ZN, continuous-cycling method | L2.06 | slide 7 typo "SN" |
| Tyreus–Luyben, Cohen–Coon, lambda tuning | IMC tuning (lambda) | L2.06 | |
| chirp, doublet, 3-2-1-1 input | frequency sweep, system-identification inputs | L2.05 | |

## Links
- Parent: [[SESA2027 Aerospace Mechanics & Control Hub]] · Previous: [[SESA2027 B2 - Root Locus Method]] · Next: [[SESA2027 B4 - Robustness, Stability vs Manoeuvrability and Design Process]]
- Concepts: [[Gain and Phase Margins]] · [[PID Controller]] · [[Ziegler-Nichols Tuning]] · [[Bode Plot]]

## Sources
- Lectures 2.05–2.06 (Dr S. Araujo-Estrada): slides `Lecture 2.05.pdf` (corrected version, created 6 March 2026) and `Lecture 2.06.pdf`
- Transcripts (speech-to-text): `Lecture 2.05 recording.txt`, `Lecture 2.06 recording.txt`; the correction announcement is in `Lecture 2.07 recording.txt`, ll. 39–46
- Franklin, Powell & Emami-Naeini (2014) Ch. 4 and 6.3–6.6
- Figures: `01 - Notes/Figures/generate_amc_b3_figures.py`

## Self-study tasks

Two tasks were set (marked lecturer-set). Reading GM and PM off a Bode plot, the infinite phase crossover and comparing tuning methods with ZN were all named as exam or quiz questions (L2.05, ll. 183–188, 476; L2.06, ll. 52–59).

### Core

- [ ] Lecturer-set (L2.05, ll. 546–548): take the frequency-response gains, "modify them slightly, and then just evaluate" the step response and the control action. → [[#3. Eight-step frequency-response design]], step 8
- [ ] Read GM and PM off a Bode plot, including a plant whose phase never reaches −180° (exam question). → [[#1. Why frequency-response design (L2.05)]]
- [ ] Redo the SPO design starting from the true plant $-1.39(s+0.306)/(\dots)$, inverting it explicitly, and give the gains to implement (suggested). → [[#What was said in L2.05 vs the corrected slides]]
- [ ] Find $K_u$ and $T_u$ for the servo by Routh–Hurwitz and apply the ZN table (suggested). → [[#Ziegler–Nichols: ultimate sensitivity method]]
- [ ] Give one advantage of ZN over each other tuning method, and one disadvantage (quiz question). → [[#4. PID tuning algorithms (L2.06)]]
- [ ] PS2 Q7 and the ZN question. → [[SESA2027 Practice Problems 2 Solutions]]
- [ ] Mock exam question. → [[SESA2027 Mock Questions#Q8. Margins and PD design|Mock Q8]]

### Further practice

- [ ] Lecturer-set (L2.06, ll. 309–310): "if you think this is not complicated enough for me, look at the other ones" (Tyreus–Luyben, Cohen–Coon, lambda). → [[#4. PID tuning algorithms (L2.06)]]
- [ ] Show that $T_I=3/\omega_{gc}$ costs 18.4° of phase at crossover, and explain why the realised crossover and PM differ from the targets (suggested). → [[#3. Eight-step frequency-response design]]
- [ ] Derive $\zeta=0.215$ and the 50 % first overshoot from the quarter-decay ratio (suggested). → [[#Ziegler–Nichols: ultimate sensitivity method]]
