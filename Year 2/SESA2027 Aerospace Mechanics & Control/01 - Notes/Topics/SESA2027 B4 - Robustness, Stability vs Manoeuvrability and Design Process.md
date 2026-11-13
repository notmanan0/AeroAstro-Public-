---
title: "SESA2027 B4 - Robustness, Stability vs Manoeuvrability and Design Process"
module: "SESA2027 Aerospace Mechanics & Control"
type: topic
stream: "Part B: Control Systems"
order: 9
tags:
  - sesa2027
  - robustness
  - handling-qualities
  - control-design-process
aliases: ["Robust Control Design", "Stability vs Manoeuvrability"]
date: 2026-09-23
status: lectured
coverage: "L2.07 (gain signs, robustness, three closed-loop TFs), L2.08 (stability vs manoeuvrability), L2.09 (design process revision)"
parent: ["[[SESA2027 Aerospace Mechanics & Control Hub]]"]
prerequisites: ["[[SESA2027 B3 - Frequency-Response PID Design and Ziegler-Nichols Tuning]]"]
next_topics: ["[[SESA2027 C1 - Sensing Systems, Sensor Principles and Sensor Fusion]]"]
key_concepts: ["[[Gain and Phase Margins]]", "[[Stability vs Manoeuvrability]]", "[[Closed-Loop Transfer Function]]"]
tutorial_sheets: ["[[SESA2027 Practice Problems 2 Solutions]]"]
sources: ["02 - Sources/Lectures/Lecture 2.07.pdf", "02 - Sources/Lectures/Lecture 2.08.pdf", "02 - Sources/Lectures/lecture_2.09.pdf", "02 - Sources/Lectures/Lecture 2.07 recording.txt", "02 - Sources/Lectures/Lecture 2.08 recording.txt", "02 - Sources/Lectures/Lecture 2.09 recording.txt"]
---

# SESA2027 B4 - Robustness, Stability vs Manoeuvrability and Design Process

> [!abstract] Summary
> A PID must always give negative feedback: $T_D>0$, $T_I>0$ and the sign of $K_p$ matched to the plant. A robust controller stays stable and meets its specifications despite model uncertainty, disturbances and measurement noise, and splitting the closed-loop output into reference, disturbance and noise transfer functions shows the trade: high loop gain rejects disturbances but passes noise. In handling-quality terms the same trade appears as stability (high $\zeta$, low $\omega_n$) against manoeuvrability (high $\omega_n$ and bandwidth), and the design process ties these checks together.

> [!summary]- Exam use: quick path
> - **Use it when:** a question asks which PID gain signs are allowed, whether a loop stays stable when plant parameters are wrong, how a controller rejects disturbances or amplifies noise, how to trade stability against manoeuvrability, or to outline the design process.
> - **Assumptions:** the standard feedback block diagram ($C$, $G$, $H$, process noise $U_P$, measurement noise $X_N$); $H=1$ for the parameter-sensitivity analysis; second-order plant $G=K(s+z)/(s^2+2\zeta\omega_ns+\omega_n^2)$ with P control; open loop stable.
> - **Method:** 1. $T_I>0$, $T_D>0$ always; sign of $K_p$ = sign of the plant's static gain. 2. Write the closed-loop quadratic $s^2+bs+c$; stable iff $b>0$ and $c>0$. 3. Check which parameter errors can push $b$ or $c$ through zero. 4. Disturbance TF $G/(1+GC)$, noise TF $-GCH/(1+GCH)$: high loop gain helps the first and hurts the second. 5. Fix the failing specification with the gain that controls it ($K_p\to\omega_n$, $T_D\to\zeta$, $T_I\to$ steady state).
> - **Common mistakes:** concluding that a negative $K_p$ is always positive feedback (it restores negative feedback when the plant gain is negative); treating Levels 1–3 as pilot-skill levels.
> - **Practise:** [[#Worked example: how much model error can a design take?]] · [[SESA2027 Mock Questions#Q9. Robustness and the three closed-loop transfer functions|Mock Q9]]

A controller is designed on a model, but it flies on an aircraft. The real aircraft is heavier or lighter, its derivatives change with Mach and altitude, gusts push it about, and every sensor adds noise. Robustness is the ability to stay stable and keep performing when all of that differs from the model.

Splitting the closed-loop output into three parts shows what feedback can and cannot do. Commands arrive through $GC/(1+GC)$, gusts through $G/(1+GC)$, sensor noise through $GC/(1+GC)$ with a minus sign. A high loop gain $GC$ makes the command term close to 1 and crushes the gust term, which is good. But the noise term is the same size as the command term: the loop cannot tell a real pitch rate from a noisy reading of one. High loop gain is therefore wanted at low frequency, where commands and gusts live, and low loop gain at high frequency, where noise lives. Stability versus manoeuvrability is the same trade in handling-qualities language: more bandwidth and less damping make the aircraft agile, but leave less margin for error.

---

## 1. Allowable gain signs
With $C(s) = K_p\left(1+T_Ds+\dfrac{1}{T_Is}\right)$, each gain has a sign it must not take. A negative $T_D$ turns damping into anti-damping: it injects energy at high frequency, amplifies noise and can destabilise the loop. A negative $T_I$ gives the integral action the wrong sign, so wind-up runs in the wrong direction and the loop diverges. A negative $K_p$ flips the control action into positive feedback, which is usually unstable. However, if the plant gain is negative (e.g. elevator-up gives a nose-up moment, so $q/\eta<0$), a negative $K_p$ restores negative feedback, and that is the case in the SPO examples.

The rule is therefore to choose $T_D>0$ and $T_I>0$ every time; if a design produces negative values, the controller structure is wrong. Only $K_p$ takes its sign from the plant.

What a negative $K_p$ does to the parallel gains. Expand the standard form:

$$
K_p\left(1+\frac{1}{T_Is}+T_Ds\right) = K_p+\frac{K_p/T_I}{s}+K_pT_Ds
$$

$$
K_I = \frac{K_p}{T_I},\qquad K_D = K_pT_D
$$

With $T_I>0$ and $T_D>0$, a negative $K_p$ makes $K_I$ and $K_D$ negative too. That is acceptable, provided $T_I$ and $T_D$ themselves stay positive.

The frequency-response design in B3 flips the sign of the SPO transfer function and restores it on $K_p$ at the end. With the SPO's negative static gain, a negative $K_p$ is fine in the quiz, the practice problems and the control lab. See [[SESA2027 B3 - Frequency-Response PID Design and Ziegler-Nichols Tuning#L2.05 as delivered versus the corrected slides|B3: sign handling for a negative plant gain]].

In a digital controller a negative $T_I$ is worse still: the integrator accumulates error in the wrong direction, the error grows, and the integrator state runs away until it or the actuator saturates, which compounds the divergence.

## 2. Robustness in aerospace
A control system is **robust** if it remains stable under parameter variations and maintains its performance ($t_r$, overshoot, bandwidth, disturbance rejection) under model uncertainty. A system that does not perform as expected in real life was not robust. Robustness matters in aerospace for five reasons:
- safety-critical systems;
- regulations: CS/FAR-25 and MIL-F-8785C margin requirements;
- passenger comfort;
- operational variability (mass, CG, fuel, Mach, altitude);
- environmental uncertainty (gusts, icing, sensor noise, actuator dynamics, flexibility).

The real aircraft deviates from its design model in three ways. Model uncertainty comes from derivatives that vary with $h$, $M$ and $Re$, CG shifts, unmodelled sensor and actuator dynamics, and flexible modes. External disturbances include turbulence (Dryden or von Kármán spectra), gust loads (CS 25.341), thrust variations and updrafts. Measurement noise covers gyro drift, accelerometer bias, air-data noise, quantisation and surface-position feedback noise.

Several of these have concrete forms. An airliner may fly full or 20 % full, so mass, cg and fuel vary widely; modern systems let the crew enter mass, cg position and fuel load, and the controller parameters are adjusted in real time (gain scheduling; not examined in detail). Actuators wear: the servo at the end of a test campaign is not the servo at the start, so its transfer function drifts, which also affects second-year projects using servos and motors. The Dryden turbulence model was developed mainly for fighters and airliners; its length and time scales do not suit small UAVs, and it is used for them only because nothing better is available. Air-data sensors (pitot tube, AoA vane) measure pressure differences, so fast manoeuvres and flight near the stall add sensor dynamics and give erroneous readings. A low-cost IMU not rated for the motion saturates and returns meaningless readings, and dropping significant figures costs resolution through quantisation.

FAA/EASA do not specify numerical stability margins; the relevant requirements are CS 25.672 (SAS), 25.173/175 (static longitudinal stability), 25.253 (high speed) and AC 25.629-1C (aeroelastic). MIL-F-9490D does give numbers: GM ≥ 4.5 dB and PM ≥ 30° typical, up to GM 6 dB and PM 45° depending on mode frequency and airspeed. It is used with MIL-STD-1797A (flying qualities), and it is the guideline to cite in a lab report that needs a margin.

Control lab 2 tests robustness directly: vary the plant parameters by about ±5 % (the 20 % scaling of $\omega_n$ in §5 is too much), check stability first and then performance, and inject a gust. Noise is simulated in lab 3. The lab aircraft parameters (JetStar, Boeing 747, F-4C) were interpolated from historical data over Mach and altitude, which is itself a source of model uncertainty.

## 3. The three closed-loop transfer functions
Using the general block diagram (controller $C$, plant $G$, sensor $H$, process noise $U_P$, measurement noise $X_N$):

$$
X(s) = \underbrace{\frac{GC}{1+GCH}}_{\text{reference}}R+\underbrace{\frac{G}{1+GCH}}_{\text{disturbance}}U_P-\underbrace{\frac{GCH}{1+GCH}}_{\text{noise}}X_N
$$

(The derivation of this line from the block equations is in [[SESA2027 B1 - Control System Fundamentals and PID Control#3. Closed-loop transfer function|B1 §3]].)

![[amc_three_closed_loop_tfs.png|820]]

Disturbance rejection and noise rejection work against each other. With $H=1$ write $L=GC$ and define the **sensitivity** $S=1/(1+L)$ and the **complementary sensitivity** $T=L/(1+L)$. Then

$$
S+T=\frac{1}{1+L}+\frac{L}{1+L}=\frac{1+L}{1+L}=1
$$

at every frequency. The reference TF is $T$, the noise TF is $-T$, and the disturbance TF is $G\,S$. Making $S$ small (rejecting gusts, tracking well) forces $T\to1$, which passes noise straight through. Both can be had only by separating them in frequency: $\lvert L\rvert\gg1$ where gusts and commands are, $\lvert L\rvert\ll1$ where noise is.

> [!check] Numbers behind the figure (computed)
> At 0.1 rad/s the PID loop has $\lvert S\rvert=0.20$, so the gust response falls from $-9.4$ dB (no control) to $-23.4$ dB, five times smaller. At DC the integrator makes $S\to0$. At high frequency the ideal derivative keeps $\lvert GC\rvert\to\lvert-1.39\times K_pT_D\rvert=0.64$, so $T$ levels off at $-8$ dB instead of rolling off: noise above the bandwidth is not attenuated. This is the quantitative reason the D term needs a low-pass filter ([[SESA2027 C3 - Signal Conditioning, Digitisation and Digital Filtering#Derivatives: noise amplifiers|C3]]). $\lvert S+T-1\rvert<10^{-15}$ at every frequency. ✓

### (a) Sensitivity to model parameters
Take $U_P = X_N = 0$ and $H = 1$. For $G = \dfrac{K(s+z)}{s^2+2\zeta\omega_ns+\omega_n^2}$ with $C = K_p$:

$$
\frac{X}{R} = \frac{K(s+z)K_p}{s^2+(KK_p+2\zeta\omega_n)s+(\omega_n^2+KK_pz)}
$$

Line by line: $GC/(1+GC)$ with $GC=KK_p(s+z)/(s^2+2\zeta\omega_ns+\omega_n^2)$. Multiply top and bottom by the plant denominator:

$$
\frac{X}{R}=\frac{KK_p(s+z)}{s^2+2\zeta\omega_ns+\omega_n^2+KK_p(s+z)}
$$

Collect powers of $s$ in the denominator: the $s$ terms give $2\zeta\omega_n+KK_p$ and the constants give $\omega_n^2+KK_pz$, which is the line above.

For a quadratic $s^2+bs+c$, the conditions $b>0$ and $c>0$ are the whole stability test. The roots have sum $-b$ and product $c$. Both roots in the left half-plane means their sum is negative ($b>0$) and their product positive ($c>0$); for a complex pair the product is $\lvert s\rvert^2>0$ automatically and the sum is twice the real part. Conversely, $b>0$, $c>0$ rules out a right-half-plane root. (This is Routh–Hurwitz for $n=2$.)

The closed-loop characteristic polynomial is a quadratic $as^2+bs+c$ with $a=1$, $b = KK_p+2\zeta\omega_n$ and $c = \omega_n^2+KK_pz$, so it is stable iff $b>0$ and $c>0$. An open-loop-stable plant has $\zeta>0$ and $\omega_n>0$, while the zero $z$ may have either sign. $K_p$ is given the same sign as the plant's static gain (§1); for the SPO, $K<0$ and $z>0$, so $K_p<0$ and therefore $KK_p>0$. Hence $b = KK_p+2\zeta\omega_n>0$ always. The constant term $c = \omega_n^2+KK_pz$ is positive when $z>0$. If the zero is in the right half-plane ($z<0$), $c>0$ requires $\omega_n^2>KK_p|z|$, so stability depends on the sizes of $\omega_n$ and $z$.

> [!warning] Matching signs
> $K$ and $K_p$ do not have opposite signs. Matching the sign of $K_p$ to the plant gain makes $KK_p>0$, which restores negative feedback. Only $c$ can be pushed negative by parameter errors.

Errors in the estimated parameters move $b$ and $c$: errors in $z$ affect $c$, errors in $\omega_n$ affect $b$ and $c$, and errors in $\zeta$ affect $b$. A design with little margin can become unstable. In the parabola picture of the polynomial, a negative $b$ shifts the parabola right, and a negative $c$ lowers it below the axis.

### Worked example: how much model error can a design take?

*(Suggested, not lecturer-set.)* Plant: $K=-1.39$, $z=0.306$, $\omega_n^2=1.325$, $2\zeta\omega_n=0.805$, with $K_p=-3$.

- $KK_p=4.17$, so $b=4.17+0.805=4.975$ and $c=1.325+4.17\times0.306=2.601$. Both positive.
- Because $z>0$ and $KK_p>0$, both terms of $b$ and both terms of $c$ are positive. No error in $\zeta$, $\omega_n$ or $z$ (as long as their signs are right) can destabilise this loop.
- With the zero in the right half-plane instead, $z=-0.306$ (a non-minimum-phase plant), $c=1.325-1.276=0.049$. Stability needs $\omega_n^2>1.276$, i.e. the true $\omega_n^2$ can be at most $3.7\,\%$ lower than modelled, or $\omega_n$ about $1.9\,\%$ lower, before $c<0$ and a real pole crosses into the right half-plane.

> [!check] Numerical check
> `np.roots([1, 4.975, 2.601])` gives $-4.381$ and $-0.594$ (stable). With the right-half-plane zero, `np.roots([1, 4.975, 0.049])` gives $-4.965$ and $-0.0099$: a pole sitting almost on the imaginary axis, which a 2 % error in $\omega_n$ pushes across. The sign of $z$ decides whether the design is robust or fragile.

### (b) Disturbance rejection
With $R = X_N = 0$:

$$
X = \frac{G}{1+GC}U_P
$$

Gusts enter through $\mathbf B'$ via $u_g$ and $w_g$. A typical model is the 1-cosine gust, $\alpha_g(t) = \frac{A_g}{2}[1-\cos(2\pi t/T_g)]$. The controller appears only in the denominator, so it cannot shape the disturbance directly and can only react through feedback. Higher low-frequency loop gain and bandwidth give better rejection.

### (c) Measurement noise
With $R = U_P = 0$:

$$
X = -\frac{GCH}{1+GCH}X_N
$$

Noise enters through the feedback path and is subtracted at the summing junction. High controller gain at high frequency amplifies it, so the bandwidth must be chosen carefully; one remedy is a band-pass filter on the measurements, cutting both low and high frequencies. Sampling adds a further limit. Nyquist–Shannon requires $f_s>2f_{max}$, and in practice about $10f_{max}$ is used. Noise above Nyquist aliases into the loop, so anti-alias filters go before the ADC. See [[Nyquist Sampling and Aliasing]].

### Controller adjustments for robustness

| Problem | Solution |
|---|---|
| Poor stability margin due to uncertainty | Add lead or damping, reduce gain |
| Poor gust rejection | Increase low-frequency gain |
| Noise amplification | Reduce bandwidth, add low-pass filtering |
| Sensitivity to $C_{m_\alpha}$ | Add pitch-rate feedback |

Other strategies:
- Reduce the crossover frequency to improve noise tolerance.
- Use washout filters.
- Limit actuator bandwidth so structural modes are not excited.

Beyond single-loop SISO design, the options are:
- Lead-lag compensators.
- Nested (cascaded) loops, e.g. ArduCopter and Crazyflie: position → velocity → attitude → rate PID loops.
- Gain scheduling across the flight envelope.

## 4. Stability vs manoeuvrability
Static stability in pitch means $C_{m_\alpha}<0$; dynamic stability means the oscillations (SPO and phugoid) decay. **Manoeuvrability** is the ability to change the flight path quickly on command, measured by $\left|\dfrac{\partial q}{\partial\eta}\right|_{max}$. High manoeuvrability means a large DC gain, high bandwidth and lower (but still stable) damping. The **DC gain** is the gain at zero frequency, the left-hand end of the Bode magnitude plot, named by analogy with direct current as a constant signal; for a transfer function it is $G(0)$.

In **fly-by-wire** the pilot's stick commands a computer and servomotors, which move the control surfaces; the pilot does not move them directly. It is needed for relaxed-stability fighters, and because hinge moments on large or supersonic aircraft are too big for a pilot to apply.

Uncrewed aircraft can switch sides of the trade-off. With nobody on board, a UAV can be flown stable in one phase and deliberately agile, even unstable, in another. For example, a delivery drone that cruises stably from A to B, then brakes hard, drops the parcel and leaves.

| Highly stable aircraft | Highly manoeuvrable aircraft |
|---|---|
| Large negative $C_{m_\alpha}$ | Small or positive $C_{m_\alpha}$ (relaxed stability) |
| High damping $\zeta$ | Lower damping, faster response |
| Sluggish, smooth response | Quick, agile response |
| Low control effort | High control power required |
| Transport aircraft (B777, A350), gliders | Fighters (F-16, Typhoon: unstable, fly-by-wire) |

On the SPO, more stability means $\zeta$ up and/or $\omega_n$ down. Raising $\zeta$ at fixed $\omega_n$ swings the poles towards the negative real axis, so the oscillation is better damped; lowering $\omega_n$ at fixed $\zeta$ slides them along their constant-$\zeta$ ray towards the origin, since the real part is $-\zeta\omega_n$, so the response is slower. More manoeuvrability means $\omega_n$ up and $\zeta$ down: the poles move out along the ray and towards the imaginary axis, and the response is faster but less damped. When $\zeta$ and $\omega_n$ change together, the real part $-\zeta\omega_n$ moves left or right according to whether $\zeta\omega_n$ grows or shrinks. The trade-off is visible directly in bandwidth $\propto\omega_n$ and overshoot $\propto e^{-\zeta\pi/\sqrt{1-\zeta^2}}$.

Handling qualities are rated on the Cooper–Harper scale (1–10) and graded as Levels 1–3 of flying qualities. Cook Table 10.4 gives the short-period damping limits; for Level 1:

| Category | $\zeta_{min}$ | $\zeta_{max}$ |
|---|---|---|
| A | 0.35 | 1.30 |
| B | 0.30 | 2.00 |
| C | 0.50 | 1.30 |

The thumbprint plot of $\omega_n$ against $\zeta$ (Etkin) shows the satisfactory region.

The pilot assessment loop is entered at the bottom left of the Cooper–Harper decision tree. If the aircraft is not controllable and stable, there are major deficiencies and it is redesigned. If the performance is not adequate without excessive corrections, it is redesigned again. If it is not satisfactory without improvement, the loop goes round again. The loop ends only when the pilot rates it good to fly.

> [!example] Shifting a design between stability and manoeuvrability
> Start from an SPO PID design that meets OS < 10 %: steady-state error removed within about 6–7 s and a rise time to 90 % of about 0.8 s. To make it more agile, relax the overshoot target to about 20 % and keep the steady-state behaviour:
> - increase $K_p$ (raises $\omega_n$ and bandwidth);
> - decrease the derivative action (less damping, so more overshoot);
> - keep $T_I$ (the steady-state response was already good).
>
> The rise time drops to about a third of the original, with higher overshoot, and the system stays stable. More bandwidth also means more sensitivity to noise and uncertainty.

Fighter aerodynamic databases are bigger for the same reason. Airliner databases typically span about −3° to 20° angle of attack and ±10° sideslip, while fighter databases span about −40° to 60°, because a less stable, more manoeuvrable aircraft has to be modelled far outside the linear range. Rate derivatives are measured on rotary-balance rigs (NASA, TsAGI).

Controller design strikes the balance differently by aircraft type. Passenger aircraft (more stable) use pitch-rate feedback for damping, low-pass filters, and lead–lag compensation for margins. Fighters (more manoeuvrable) use a reduced static margin, high-bandwidth fly-by-wire, state feedback (LQR) and command shaping. Modern aircraft do not rely only on natural stability; the control system provides synthetic stability. See [[Stability vs Manoeuvrability]].

## 5. The control system design process
The design process has seven steps: modelling → stability analysis → time- and frequency-domain analysis → controller design → robustness check → implementation constraints (sensing, sampling, actuator limits; Part C) → certification and validation by the authorities. The first five are grouped as below. Robustness analysis is needed because every model is wrong to some degree (DAP1).

1. Model the aircraft dynamics: EOM, then linearise about trim, then state space, then extract the mode (SPO), then a second-order model $G = \dfrac{K(s+z)}{s^2+2\zeta\omega_ns+\omega_n^2}$. The model hierarchy runs PDEs → nonlinear ODEs → linear ODEs → LTV → LTI.
2. Analyse the dynamics: time response ($\omega_n$, $\zeta$, $t_r$, $t_s$, OS) and frequency response (Bode, crossovers, bandwidth, margins).
3. Select and design a controller: root locus (pole placement), frequency response (margin shaping), or ZN (crude on its own). Example specifications: stable, $t_r<1.0$ s, $t_s(5\%)<6.0$ s, $OS<20\%$.
4. Evaluate robustness: vary the model, e.g. $\Delta\omega_n = 0.8$, $1.0$, $1.2$.
   - With $K_p = -1.75$, $T_D = 5\times10^{-2}$, $T_I = 2.5\times10^{-1}$, the OS specification is violated under uncertainty.
   - Retuning to $T_D = 1.5\times10^{-1}$ meets all specifications.
5. Interpret the results: check that the margins are adequate, the handling-qualities goals are met, the sensitivity is acceptable, the behaviour is consistent across the envelope, and the bandwidth is neither too high (noise) nor too low (sluggish), with safety, regulations, handling qualities and comfort kept in view throughout.

With $\omega_n$ scaled by 0.8, 1.0 and 1.2, the 0.8 case breaks the overshoot specification (above 20 %) while still meeting stability, rise time and settling time. $K_p$ mainly moves $\omega_n$ and the rise time, and $T_I$ is not the problem because the steady state was already good, so the gain to retune is $T_D$, which adds damping. Raising $T_D$ from $5\times10^{-2}$ until the overshoot just touches 20 % restores the specification. A 20 % change in $\omega_n$ is large, and the lab work uses about ±5 % (§2).

When the specifications conflict, the priority order is: safety first (the system has to be stable even when it must be manoeuvrable), then the regulations that encode it, then performance and handling qualities, and comfort last: comfort can be sacrificed, safety cannot.

The SPO transfer function carries a negative gain. A second-order system with no zero has a phase that runs from 0° to −180°. The SPO's negative numerator gain adds −180° and its left-half-plane zero adds up to +90°, so the phase starts at −180° and ends at −270° (rising to about −142° on the way, where the zero's lead acts), and the step response is negative. The same sign issue is handled in the frequency-response design by inverting the plant ([[SESA2027 B3 - Frequency-Response PID Design and Ziegler-Nichols Tuning#L2.05 as delivered versus the corrected slides|B3]]).

## Exam scope

- Negative $K_p$ is acceptable in the quiz, practice problems and control lab when the plant's static gain is negative.
- The robustness checks asked for in lab 2: stability under ±5 % parameter changes, then performance; gust rejection.
- Use MIL-F-9490D for margin guidelines and Cook Ch. 10 handling-qualities tables in the lab report.
- The final revision lecture adds no new concepts; it maps the material for the exam.
- The same process can be applied to the phugoid or Dutch-roll approximations in Cook.

## Terminology and alternative names

| Course term | Also called | Where the course uses it | Note |
|---|---|---|---|
| robustness | robust stability + robust performance | L2.07 slide 6 | the course's definition covers both |
| model uncertainty | parametric uncertainty, unmodelled dynamics | L2.07 | |
| reference / disturbance / noise transfer functions | complementary sensitivity $T$ / load-disturbance sensitivity $GS$ / $-T$ | L2.07 slides 12–20 | $S=1/(1+GC)$ is the sensitivity function |
| process noise $U_P$ | load disturbance, input disturbance | L2.07 | |
| 1-cosine gust | discrete gust ("1-cos"), CS 25.341 gust | L2.07 | |
| Dryden / von Kármán spectra | continuous turbulence models | L2.07 | |
| relaxed static stability | reduced static margin, RSS | L2.08 | |
| flying-qualities Levels 1–3 | handling-qualities levels | L2.08, Cook Ch. 10 | not pilot-skill levels |
| flight-phase Categories A, B, C | (A: non-terminal, rapid manoeuvring; B: non-terminal, gradual; C: terminal — take-off, approach, landing) | L2.08 | |
| thumbprint plot | short-period $\omega_n$–$\zeta$ requirement chart | L2.08 | |
| Cooper–Harper scale | pilot rating scale | L2.08 | |
| nested (cascaded) loops | inner/outer loops | L2.07 | |
| gain scheduling | scheduled gains over the envelope | L2.07 | |

## Links
- Parent: [[SESA2027 Aerospace Mechanics & Control Hub]] · Previous: [[SESA2027 B3 - Frequency-Response PID Design and Ziegler-Nichols Tuning]] · Next: [[SESA2027 C1 - Sensing Systems, Sensor Principles and Sensor Fusion]]
- Concepts: [[Gain and Phase Margins]] · [[Stability vs Manoeuvrability]] · [[Closed-Loop Transfer Function]]
- Static margin link: [[SESA2022 T6 - Aircraft Aerodynamics and Static Stability]]
- Year 3: [[SESA3047 Advanced Aerospace Mechanics & Control Hub|SESA3047 Advanced Aerospace Mechanics & Control]]

## Sources
- Lectures 2.07–2.09 (Dr S. Araujo-Estrada): slides `Lecture 2.07.pdf`, `Lecture 2.08.pdf`, `lecture_2.09.pdf`
- Transcripts (speech-to-text): `Lecture 2.07 recording.txt`, `Lecture 2.08 recording.txt`, `Lecture 2.09 recording.txt`
- Cook (2007) Ch. 10; Etkin (2000); MIL-F-9490D, MIL-STD-1797A
- Figures: `01 - Notes/Figures/generate_amc_b4_figures.py`

## Self-study tasks

Two in-class questions were set (marked lecturer-set). L2.09 is the revision map for Part B (l. 8). Negative $K_p$ is acceptable in the quiz, practice problems and control lab (L2.07, ll. 114–115).

### Core

- [ ] Lecturer-set (L2.08, ll. 464–480, asked in class): to make the SPO design more manoeuvrable with the same $\omega_n$ target and steady state, which gains do you change, and how? → [[#4. Stability vs manoeuvrability]]
- [ ] Lecturer-set (L2.09, ll. 175–199, asked in class): with $\omega_n$ 20 % low the overshoot exceeds 20 %; which gain do you retune? → [[#5. The control system design process]]
- [ ] Write $K_I$ and $K_D$ for $K_p = -1.75$, $T_I = 0.25$ s, $T_D = 0.15$ s and explain why the negative values are acceptable (suggested). → [[#1. Allowable gain signs]]
- [ ] For $G = K(s+z)/(s^2+2\zeta\omega_ns+\omega_n^2)$ with P control, find the condition on $z$ that keeps the loop stable for any parameter error (suggested). → [[#Worked example: how much model error can a design take?]]
- [ ] Mock exam question. → [[SESA2027 Mock Questions#Q9. Robustness and the three closed-loop transfer functions|Mock Q9]]

### Further practice

- [ ] Show $S+T=1$ and use it to explain why disturbance rejection and noise rejection cannot both be improved at the same frequency (suggested). → [[#3. The three closed-loop transfer functions]]
- [ ] Explain from the high-frequency limit of $\lvert GC\rvert$ why an unfiltered derivative passes sensor noise (suggested). → [[#3. The three closed-loop transfer functions]]

## Transcript and slide slips

> [!warning] Slide 5's elevator example is worded the wrong way round
> Where: [[#1. Allowable gain signs]].
>
> Slide 5 and the lecture (l. 112) say "elevator-up causes nose-down moment". With the course convention ($\eta>0$ is trailing edge down), trailing-edge-down elevator gives a nose-down moment and elevator-up gives a nose-up moment. Either way $q/\eta<0$, which is the point of the slide.

### Transcript slips

> [!warning] Speech-to-text and spoken slips, with the correct version
> | Where | Transcript says | Correct |
> |---|---|---|
> | L2.07, l. 50 | "a negative Ti would basically mean that you are reversing the sign of the derivative term" | a negative $T_D$ reverses the derivative term (anti-damping); a negative $T_I$ would reverse the integral term (§1) |
> | L2.07, l. 60 | "classical PAD control" | classical PID control |
> | L2.07, l. 107 | "if the plan has a negative static gain" | the plant |
> | L2.07, l. 112 | "elevator up causes a nose down moment" | elevator up gives nose up; the point is that $q/\eta<0$ |
> | L2.07, l. 168 | "our elasticity, it's a killer" | aeroelasticity |
> | L2.07, l. 193 | "the JetStart" | Lockheed JetStar |
> | L2.07, l. 204 | SPO depends on "MW, MQ, and ETA" | $M_w$, $M_q$ and $M_\eta$ |
> | L2.07, l. 220 | "because of the where" | because of wear |
> | L2.07, l. 227 | "on steady aerodynamics" | unsteady aerodynamics |
> | L2.07, l. 235 | "the four-Karman Spectra model" | the von Kármán spectrum |
> | L2.07, ll. 237–252 | "UABs" | UAVs |
> | L2.07, l. 329 | stability "is determined by the numerator of this transfer function" | by the denominator |
> | L2.07, ll. 363, 366–369 | "omega n and seth"; "zeta is going to affect C … Sorry, zero" | errors in $z$ affect $c$, in $\omega_n$ affect $b$ and $c$, in $\zeta$ affect $b$ (self-corrected) |
> | L2.07, l. 408 | "Nyquist-Sharon sampling theorem" | Nyquist–Shannon |
> | L2.07, l. 425 | "I need that compensator" | lead–lag compensator |
> | L2.07, l. 428 | "ArduPilot and the crazyfly" | ArduPilot and Crazyflie |
> | L2.07, l. 430 | "wider flight emperors" | wider flight envelopes |
> | L2.07, l. 437 | "the PLF controller" | the PID controller |
> | L2.08, l. 12 | "Earthcraft stability … CSAT 2022" | aircraft stability, SESA2022 |
> | L2.08, l. 22 | "return to train condition" | return to the trim condition |
> | L2.08, l. 183 | "Boeing 777, sorry, Airbus A350" | both are examples on the slide |
> | L2.08, l. 208 | "the F-22, the Aerofighter Type 1" | F-22, Eurofighter Typhoon |
> | L2.08, ll. 331–362 | Levels 1–3 as pilot-skill levels | flying-qualities levels (see the warning in §4) |
> | L2.08, ll. 334, 412, 419 | "dumping ratio", "dumping derivatives" | damping |
> | L2.08, l. 410 | "put the aircraft on a steam … make it spin" | on a rotary-balance rig |
> | L2.08, l. 414 | "Sagi in Russia" | TsAGI |
> | L2.08, l. 426 | "flabberg wire controllers" | fly-by-wire |
> | L2.08, ll. 466, 478 | the question asks to "hold my natural frequency the same", but the answer "increased the natural frequency" | the worked change in [[#4. Stability vs manoeuvrability]] raises $\omega_n$ through $K_p$; it holds the steady state, not $\omega_n$ |
> | L2.08, l. 478 | "a more mineral aircraft by changing the value of KB" | a more manoeuvrable aircraft, by changing $K_p$ |
> | L2.09, l. 37 | "The fugoid" | the phugoid |
> | L2.09, l. 58 | "the time to double if the system is stable" | if the system is unstable |
> | L2.09, l. 337 | "the authorities in this case are going to be in the army" | probably a mis-transcription of the certifying authority (EASA, or the FAA); military aircraft are certified by the military airworthiness authority |
> | L2.09, ll. 193, 197 | "I want to add more dumping … reduced that dumping" | add more damping, until the overshoot was reduced |
> | L2.09, l. 199 | "my cost loop characteristics" | closed-loop characteristics |

> [!warning] Transcript slip: levels are flying-qualities levels, not pilot-skill levels (L2.08, ll. 331–362)
> Where: [[#4. Stability vs manoeuvrability]].
>
> The lecture described Level 1 as "pilots with less experience, lower skills" and Level 3 as "pilots with a lot of skill", and said the damping limit drops "as the pilot becomes more of an expert" (L2.08, ll. 331–362). That is a slip. In MIL-F-8785C and Cook Ch. 10, Level 1 means flying qualities clearly adequate for the mission, Level 2 adequate but with increased pilot workload or degraded effectiveness, and Level 3 controllable but with excessive workload. The lower $\zeta$ limits at Levels 2–3 describe a more degraded aircraft that demands more of the pilot, which is the lecturer's underlying point (ll. 361–364). The category reasoning is right: Category C (take-off, approach, landing) has the highest $\zeta_{min} = 0.50$ because these are the most critical phases (ll. 348–354).
