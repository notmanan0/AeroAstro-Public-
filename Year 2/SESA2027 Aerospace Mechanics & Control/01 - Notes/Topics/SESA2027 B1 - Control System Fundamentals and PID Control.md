---
title: "SESA2027 B1 - Control System Fundamentals and PID Control"
module: "SESA2027 Aerospace Mechanics & Control"
type: topic
stream: "Part B: Control Systems"
order: 6
tags:
  - sesa2027
  - control-systems
  - pid
aliases: ["PID Control", "Control Fundamentals"]
date: 2026-09-23
status: lectured
coverage: "L2.01 (why control), L2.02 (classifications, SPO with elevator), L2.03 (PID actions, satellite demo)"
parent: ["[[SESA2027 Aerospace Mechanics & Control Hub]]"]
prerequisites: ["[[SESA2027 A5 - Frequency Response and Bode Plots]]"]
next_topics: ["[[SESA2027 B2 - Root Locus Method]]"]
key_concepts: ["[[Closed-Loop Transfer Function]]", "[[PID Controller]]", "[[Transfer Function]]"]
tutorial_sheets: ["[[SESA2027 Practice Problems 2 Solutions]]"]
sources: ["02 - Sources/Lectures/Lecture 2.01.pdf", "02 - Sources/Lectures/Lecture 2.02.pdf", "02 - Sources/Lectures/Lecture 2.03.pdf", "02 - Sources/Lectures/Lecture 2.01 recording.txt", "02 - Sources/Lectures/Lecture 2.02 recording.txt", "02 - Sources/Lectures/Lecture 2.03 recording.txt"]
---

# SESA2027 B1 - Control System Fundamentals and PID Control

> [!abstract] Summary
> A control system compares a reference $r$ with the measured output $y$, and the error $e = r-y$ drives a controller $C(s)$ that commands the plant $G(s)$. With unity feedback the closed loop is $GC/(1+GC)$, and its characteristic polynomial decides stability. The PID controller $C(s) = K_P+K_I/s+K_Ds$ acts on the present, accumulated and predicted error, and each term moves the closed-loop poles in a different way.

> [!summary]- Exam use: quick path
> - **Use it when:** a question asks for the closed-loop transfer function or characteristic polynomial for a given $C(s)$ and $G(s)$, the effect of P, I or D on rise time, overshoot, steady-state error and robustness, pros and cons of control classes, or gains that place the closed-loop poles at a target $\omega_n$, $\zeta$.
> - **Assumptions:** unity feedback with an ideal sensor ($H=1$) unless told otherwise; negative feedback with $e=r-y$; LTI plant $G=B/A$; stable closed loop before using the final-value theorem.
> - **Method:** 1. $X/R=GC/(1+GC)$. 2. Characteristic polynomial: numerator of $1+GC$ (e.g. $A+K_PB$ for P). 3. Steady-state error to a step: $e_\infty=\lim_{s\to0}1/(1+G(s)C(s))$. 4. For pole placement, match the characteristic polynomial to $s^2+2\zeta\omega_ns+\omega_n^2$ term by term. 5. Check the gain sign against the sign of $G(0)$.
> - **Common mistakes:** calling the numerator of $X/R$ the characteristic polynomial (it is the denominator, L2.03, l. 266); expecting P alone to remove steady-state error or D alone to change $\omega_n$.
> - **Practise:** [[#Worked example: P leaves an error, PI removes it]] · [[SESA2027 Mock Questions#Q6. Closed loop and PID actions|Mock Q6]] · [[SESA2027 Practice Problems 2 Solutions]] (Q4–Q5)

An open-loop command is a guess: deflect the elevator by a fixed amount and hope the aircraft does what the model said. Any gust, model error or change in weight shows up straight in the output. A closed loop instead measures the output, compares it with what was wanted, and acts on the difference. Errors are corrected as they appear, and the price is a sensor, some care with signs, and the risk of making the system unstable if you push too hard.

The PID controller is the simplest useful way to turn an error into an action. P pushes in proportion to the error now, so it acts first and does most of the work. I pushes in proportion to how long the error has persisted, so it keeps pushing until the error is exactly zero, but it is slow. D pushes against how fast the error is changing, so it brakes the response before it overshoots, but it also reacts to every bit of sensor noise. Each term moves the closed-loop poles in a different direction, which is what B2 and B3 make precise.

---

## 1. Why control? (L2.01)
Examples in the lecture:
- A kestrel hovering: feedback in nature.
- Watt's steam-engine governor.
- Chemical process plants.
- Multirotor attitude and position control.
- A wind-tunnel model whose controller fails.

The lecture defines a **control system** as "an arrangement of components in which a controller generates a control action by comparing a reference input with the system's feedback signal, i.e. the control error. The controller uses the control error to adjust the system so that its output achieves the specified performance or remains within desired bounds."

| Element | Meaning |
|---|---|
| Controller $C(s)$ | Processes the error and decides the action |
| Control action $u(t)$ | Command sent to the plant |
| Control error $e(t) = r(t)-y(t)$ | Difference between reference and measurement |
| Reference $r(t)$ | Desired or commanded output |
| Feedback $y(t)$ | Measured output (or estimated state) |

**General block diagram**:
- $R\to\Sigma\to E\to C(s)\to U_C\to\Sigma(+U_P\text{, process noise})\to U\to G(s)\to X$
- Feedback path: $X\to\Sigma(+X_N\text{, measurement noise})\to X_M\to H(s)\ (\text{sensor})\to Y\to$ back to the first $\Sigma$ with a minus sign

![[amc_feedback_loop_block_diagram.png|900]]

- Why "plant"? The name comes from the chemical process plants where control theory grew up (L2.01, ll. 289–292).
- Measurement noise $X_N$ covers both true random noise and offsets in the signal (L2.01, ll. 583–586).

The error is always reference minus measurement, $e = r-y$: "for us, we always say reference as positive because that's our baseline" (L2.01, ll. 512–522), although some books use the opposite sign. The feedback summing junction is the only one with a minus sign, because this is negative feedback (ll. 548–558). Part B also assumes an ideal sensor, $H = 1$, meaning "perfect accuracy, no delay, infinite bandwidth … and zero drift. How realistic is that? Zero" (ll. 707–712); Part C removes that assumption. Not every state can be measured either: most aircraft have no angle-of-attack sensor, so $\alpha$ (or $w$) has to be estimated (ll. 527–541).

> [!warning] Cautionary tales from the lecture (L2.01, ll. 420–486)
> - **Wind-tunnel rig, Bristol 7 ft × 5 ft tunnel**: while gains were being tuned, the wireless link to the model dropped. The controller received confusing data and the model departed, damaging its nose. "This is an example of when sensing goes wrong." The lab now asks people to switch off Wi-Fi during tests.
> - **A retrofitted system with a single sensor**: the lecturer alluded to the Boeing 737 MAX MCAS, where redundant sensing and a disagree warning were optional extras (ll. 453–460). Robustness and redundancy are design requirements, not options.
> - "There are things you don't know that you don't know. Those are the dangerous ones" (ll. 467–470).

### Control objectives
1. Stability (BIBO): every bounded input gives a bounded output.
2. **Regulation**: hold a variable at a constant set point despite disturbances.
3. **Tracking**: follow a time-varying reference.
4. **Disturbance rejection**: minimise the effect of external disturbances on the output.
5. **Performance management**: meet the rise-time, overshoot and settling specifications while limiting control effort.

## 2. Control classifications (L2.02)

| Type | Pros | Cons |
|---|---|---|
| Open-loop | Simple, cheap, no sensors | No error correction, sensitive to disturbances |
| Closed-loop | Error correction, robust, better stability | Needs sensing, costs more, needs careful tuning |
| Model-based | Predictable, has stability guarantees | Needs an accurate model |
| Model-free | No model needed, robust to modelling errors | Weaker guarantees, tuning-dependent |
| Linear | Simple analysis, well-established tools | Only valid near equilibrium |
| Nonlinear | Covers the full envelope | Complex, relies on model accuracy |
| Rule-based | Transparent logic | Limited adaptability |
| Learning-based (SL/RL) | Adapts to complex environments | Needs data, hard to interpret or validate |

Open-loop and closed-loop control are also called feed-forward and feedback, and the two can be combined (L2.02, ll. 102–116). A feed-forward block passes the reference straight to the control action through a simple model of what to expect. If 2° of elevator is known to give about 0.5° of pitch, for example, the feed-forward path supplies most of the deflection, and the feedback controller only has to correct the remaining, simpler dynamics.

> [!example] Learning-based control in practice (L2.02, ll. 161–175)
> In the lecturer's gimbal experiment, three reinforcement-learning controllers were trained: on a linear (SPO-type) model, on a model with gimbal friction, and with domain randomisation (the linear model's parameters varied in every simulation, so the agent "was seeing a different aircraft every time"). The randomised agent was the most robust. It coped with changes in inertia, a larger elevator area and an injected aileron fault that shifted the trim point.

**DAP2**: this module uses linear, rule-based, closed-loop control, namely PID (slide 9; L2.02, ll. 190–194).

> [!note] Is PID model-based?
> An earlier version of this note said "model-based". The slide does not, and the lecturer classes PID itself as model-free: its control law contains no plant model (L2.02, l. 125). In this module the PID gains are nevertheless chosen from a plant model (root locus, Bode design), which is why the model-based column of the table still matters.

> [!info] Possible exam question (L2.02, ll. 184–187)
> "Name a few of the cons for, let's say, model-based control": it needs an accurate model and is sensitive to model errors. For rule-based control: low adaptability, limited scalability, needs expert knowledge.

### SPO approximation with elevator input
Add $[\mathring Z_\eta,\ \mathring M_\eta]^T\eta$ to the SPO equations, giving $\dot{\mathbf x}_{SPO} = \mathbf A_{SPO}\mathbf x_{SPO}+\mathbf B_{SPO}\eta$ with $\mathbf x = [w,q]^T$. With $\mathbf C = [0,\ 1]$ (measure $q$):

$$
\left[\frac{q(s)}{\eta(s)}\right]_{SPO} = \frac{m_\eta s+(-m_\eta z_w+m_wz_\eta)}{s^2-(m_q+z_w)s+(z_wm_q-z_qm_w)},\qquad \left[\frac{\theta(s)}{\eta(s)}\right]_{SPO} = \frac1s\left[\frac{q(s)}{\eta(s)}\right]_{SPO}
$$

The lower-case letters are Cook's "concise" derivatives, i.e. the entries of $\mathbf A = \mathbf M^{-1}\mathbf A'$.

Derivation (done on the board in L2.02, ll. 263–453). Write the SPO model in concise form:

$$
\mathbf A = \begin{bmatrix}z_w&z_q\\m_w&m_q\end{bmatrix},\qquad \mathbf B = \begin{bmatrix}z_\eta\\m_\eta\end{bmatrix},\qquad \mathbf C = \begin{bmatrix}0&1\end{bmatrix},\qquad \mathbf D = 0
$$

Form $s\mathbf I-\mathbf A$:

$$
s\mathbf I-\mathbf A = \begin{bmatrix}s-z_w&-z_q\\-m_w&s-m_q\end{bmatrix}
$$

Its determinant (main diagonal minus off-diagonal):

$$
|s\mathbf I-\mathbf A| = (s-z_w)(s-m_q)-z_qm_w
$$

$$
|s\mathbf I-\mathbf A| = s^2-(m_q+z_w)s+(z_wm_q-z_qm_w)
$$

The adjoint of a $2\times2$ matrix swaps the diagonal and negates the off-diagonal:

$$
\mathrm{adj}(s\mathbf I-\mathbf A) = \begin{bmatrix}s-m_q&z_q\\m_w&s-z_w\end{bmatrix}
$$

Multiply by $\mathbf C$ ($1\times2$ times $2\times2$ gives $1\times2$):

$$
\mathbf C\,\mathrm{adj}(s\mathbf I-\mathbf A) = \begin{bmatrix}m_w&s-z_w\end{bmatrix}
$$

Multiply by $\mathbf B$ ($1\times2$ times $2\times1$ gives a scalar):

$$
\mathbf C\,\mathrm{adj}(s\mathbf I-\mathbf A)\,\mathbf B = m_wz_\eta+(s-z_w)m_\eta
$$

$$
\mathbf C\,\mathrm{adj}(s\mathbf I-\mathbf A)\,\mathbf B = m_\eta s+(m_wz_\eta-m_\eta z_w)
$$

Divide by the determinant to get $q/\eta$ above. The denominator is the SPO characteristic polynomial, so $-(m_q+z_w) = 2\zeta\omega_n$ and $z_wm_q-z_qm_w = \omega_n^2$ (ll. 346–352). The lecturer does not expect you to repeat this for $\theta/\eta$: just multiply by $1/s$ (ll. 457–463).

The lecture example used throughout Part B is

$$
G(s) = \frac{q}{\eta} = \frac{-1.39(s+0.306)}{s^2+0.805s+1.325}
$$

## 3. Closed-loop transfer function
With unity feedback ($H=1$) and no noise:

$$
X = GU,\quad U = CE,\quad E = R-X\quad\Rightarrow\quad\boxed{\frac{X(s)}{R(s)} = \frac{G(s)C(s)}{1+G(s)C(s)}}
$$

Writing $G = B/A$, the closed-loop characteristic equation is $A(s)+C(s)B(s) = 0$ (for a proportional $C$). See [[Closed-Loop Transfer Function]].

**General case with sensor, process noise and measurement noise.** The lecture skipped these steps and promised to upload them (L2.01, ll. 643–716). The block equations are:

$$
X = G(U_C+U_P),\qquad U_C = CE,\qquad E = R-Y,\qquad Y = HX_M,\qquad X_M = X+X_N
$$

Substitute $U_C$, then $E$, then $Y$ and $X_M$:

$$
X = GCE+GU_P
$$

$$
X = GC(R-HX-HX_N)+GU_P
$$

$$
X = GCR-GCHX-GCHX_N+GU_P
$$

Collect the $X$ terms on the left:

$$
X(1+GCH) = GCR+GU_P-GCHX_N
$$

$$
\boxed{X = \frac{GC\,R+G\,U_P-GCH\,X_N}{1+GCH}}
$$

With no process noise ($U_P = 0$) and no measurement noise ($X_N = 0$):

$$
\frac{X}{R} = \frac{GC}{1+GCH}
$$

and with an ideal sensor ($H = 1$) this is the boxed result above. The three terms reappear in L2.07 as the reference, disturbance and noise transfer functions ([[SESA2027 B4 - Robustness, Stability vs Manoeuvrability and Design Process#3. The three closed-loop transfer functions|B4 §3]]).

## 4. PID control (L2.03)

**History**:
- Float valves; Watt's fly-ball governor (1788).
- Airy (1840) and Maxwell (1868): first stability analyses.
- Routh (1877) and Lyapunov (1892): stability criteria.
- Feedback amplifiers: Nyquist (1932) and Bode (1945).
- PID formalised by Callender et al. (1936).
- Root locus: Evans (1948).

$$
u(t) = K_Pe(t)+K_I\int_0^te(\tau)d\tau+K_D\frac{de}{dt}\quad\xrightarrow{\ \mathcal L\ }\quad C(s) = K_P+\frac{K_I}{s}+K_Ds
$$

Each action is studied alone (DAP3), with $G = B/A$:

| Action | Closed loop $X/R$ | Characteristic polynomial | Effect |
|---|---|---|---|
| P | $\dfrac{K_PB}{A+K_PB}$ | $A+K_PB=0$ | Faster, reduces error. Higher gain gives oscillation. Steady-state error remains |
| I | $\dfrac{K_IB}{As+K_IB}$ | $As+K_IB=0$ | Removes steady-state error. Slower, can overshoot, integrator wind-up. Adds a pole at the origin (extra −90° phase) |
| D | $\dfrac{K_DBs}{A+K_DBs}$ | $A+K_DBs=0$ | Adds damping, predicts the error trend, reduces overshoot. Amplifies noise, needs filtering |

![[amc_pid_actions_comparison.png|620]]

Common variants are P, PD, PI and PID. Start simple and add terms as needed (DAP2). The gains must be chosen to guarantee stability.

**The three closed loops, line by line.** With $G=B/A$ and $C$ a single action, multiply the top and bottom of $GC/(1+GC)$ by $A$ (and by $s$ when $C$ contains $1/s$):

$$
\text{P: }\frac{(B/A)K_P}{1+(B/A)K_P}=\frac{K_PB}{A+K_PB}
$$

$$
\text{I: }\frac{(B/A)(K_I/s)}{1+(B/A)(K_I/s)}=\frac{K_IB}{As+K_IB}
$$

$$
\text{D: }\frac{(B/A)K_Ds}{1+(B/A)K_Ds}=\frac{K_DBs}{A+K_DBs}
$$

The I loop has one more power of $s$ in its denominator: integral action adds a closed-loop pole, so the order goes up by one.

Why P leaves a steady-state error and I does not (final-value theorem; assumes the closed loop is stable). The error is $E=R-X$, so

$$
\frac{E}{R}=1-\frac{GC}{1+GC}=\frac{1}{1+GC}
$$

For a unit step, $R=1/s$:

$$
e_\infty=\lim_{s\to0}s\cdot\frac1s\cdot\frac{1}{1+G(s)C(s)}=\frac{1}{1+G(0)C(0)}
$$

- **P:** $C(0)=K_P$, so $e_\infty=1/(1+K_PG(0))$. It shrinks as $K_PG(0)$ grows but is never zero for a finite gain.
- **I (or PI):** $C(s)$ contains $K_I/s$, so $C(0)\to\infty$ and $e_\infty=0$. The integrator keeps changing its output for as long as any error remains, so the only possible steady state is zero error.

### Worked example: P leaves an error, PI removes it

*(Suggested, not lecturer-set.)* Use the lecture plant $G(s)=q/\eta=-1.39(s+0.306)/(s^2+0.805s+1.325)$.

- Static gain: $G(0)=-1.39\times0.306/1.325=-0.321$. It is negative, so the gains must be negative too ([[SESA2027 B4 - Robustness, Stability vs Manoeuvrability and Design Process#1. Allowable gain signs (L2.07)|B4 §1]]).
- P with $K_P=-3$: $K_PG(0)=0.963$, so the closed-loop DC gain is $0.963/1.963=0.491$ and $e_\infty=0.509$: half the commanded pitch rate is missing.
- Its characteristic polynomial is $A+K_PB=s^2+(0.805+4.17)s+(1.325+1.276)=s^2+4.975s+2.601$, with real roots $-4.38$ and $-0.594$: stable and overdamped.
- PI with $K_P=-3$, $K_I=-1$: $C=(K_Ps+K_I)/s$, so the characteristic polynomial is $As+(K_Ps+K_I)B=s^3+4.975s^2+3.991s+0.425$, roots $-4.01$, $-0.844$, $-0.126$. All stable, and $e_\infty=0$.

![[amc_p_vs_pi_steady_state.png|760]]

> [!check] Numerical check (Python, `scipy.signal.step`)
> The P responses settle at 0.243, 0.491 and 0.762 for $K_P=-1,-3,-10$, exactly $K_PG(0)/(1+K_PG(0))$. ✓ The PI response reaches 1, but slowly: its slowest pole is at $-0.126$, a time constant of 8 s. That is the "I makes it sluggish" point from L2.03 (ll. 334–354). The early spike in every curve comes from the plant zero at $-0.306$.

> [!info] What each term does, in the lecturer's words (L2.03)
> - At time zero the error is largest, the integral has had no time to build up and the derivative starts from zero, so P does the early work (ll. 159–169).
> - P changes the closed-loop natural frequency, hence rise time and settling time, and a little of the damping. Push it too far and you excite oscillations (ll. 276–308).
> - I adds a closed-loop root at the origin. In the demo the response time-scale stretched from about 8 s (P) to 60 s (I), so it makes the system sluggish (ll. 334–354).
> - D alone does not move $\omega_n$ and does not remove steady-state error. Its job is to pull the phase away from −180° and damp oscillation (ll. 377–399). It is shown combined with a fixed $K_P = 3$ because D on its own is not useful.
> - As a rule of thumb, $K_P$ is usually the largest gain; $K_I$ and $K_D$ are typically one to two orders of magnitude smaller (ll. 359–363).
> - Integrator wind-up arises because a digital accumulator saturates, which can destabilise the loop (ll. 412–417).
> - PD or PI is often enough, and two gains are easier to tune than three. Start with P and add terms (ll. 422–436).

> [!example] Satellite 1-DoF attitude via a reaction wheel (L2.03 demo)
> Plant: $G(s) = \Psi/U = \dfrac{1}{I_{zz}s^2}$ (double integrator).
>
> The reaction-wheel torque is $\omega_z = -\dfrac{I_{zz-wh}}{I_{zz}}\omega_{z-wh}$, with controller $\omega_{z-wh}(s) = k_ds+k_p$ (PD). The closed loop is
>
> $$T(s) = \frac{-(I_{zz-wh}k_ds+I_{zz-wh}k_p)}{I_{zz}s^2-I_{zz-wh}k_ds-I_{zz-wh}k_p}$$
>
> A P controller alone only gives marginal stability (poles on the imaginary axis). The D term is essential. See [[SESA2027 B2 - Root Locus Method]].

Open loop (L2.03, ll. 480–497): a step in wheel speed makes the satellite spin the opposite way, so the yaw angle grows without bound. The double integrator has a −40 dB/decade magnitude and a constant −180° phase, so tracking is impossible without feedback.

Choosing $k_p$ and $k_d$ by matching a standard second-order system (the lecturer calls this loop shaping, ll. 505–517). Let $\rho = I_{zz-wh}/I_{zz}$. Divide the denominator of $T(s)$ by $I_{zz}$:

$$
s^2-\rho k_ds-\rho k_p
$$

Match it to $s^2+2\zeta\omega_ns+\omega_n^2$, term by term:

$$
-\rho k_d = 2\zeta\omega_n,\qquad -\rho k_p = \omega_n^2
$$

$$
k_d = -\frac{2\zeta\omega_n}{\rho},\qquad k_p = -\frac{\omega_n^2}{\rho}
$$

So $k_p$ sets the natural frequency and $k_d$ the damping. Both gains come out negative because the wheel's reaction turns the satellite the opposite way; a negative gain is correct when the plant's static gain is negative (see [[SESA2027 B4 - Robustness, Stability vs Manoeuvrability and Design Process#1. Allowable gain signs (L2.07)|B4 §1]]).

> [!check] Demo numbers (computed from the expressions above)
> The demo used $\rho = 0.05$, $\zeta = 1$ and $\omega_n = 1.8$ rad/s (ll. 478–479, 521–522). Then $k_p = -1.8^2/0.05 = -64.8$ and $k_d = -2\times1\times1.8/0.05 = -72$. Lowering $\zeta$ to 0.5 gives an oscillatory response with a resonant peak in the closed-loop Bode plot; $\zeta = 2.5$ gives an overdamped response (ll. 530–537).

## Lecturer emphasis and exam hints (transcripts)

> [!info] Exam scope and admin
> - "I'm not thinking of including any derivations on the exam" (L2.03, l. 6), referring to the closed-loop and SPO transfer-function derivations above.
> - Cons of model-based and rule-based control are a possible exam question (L2.02, ll. 184–187).
> - The closed-loop SPO transfer functions for $q$ and $\theta$ are the ones used for the rest of Part B and the second computer lab (L2.02, ll. 464–465, 483).
> - The satellite PD Jupyter notebook was put on Blackboard; it is based on Franklin et al. Example 2.3 (L2.03, ll. 439–464, 540).
> - CubeSat project: tracking a light is a tracking objective on top of stability (L2.01, ll. 609–612).

## Transcript slips

> [!warning] Speech-to-text and spoken slips, with the correct version
> | Where | Transcript says | Correct |
> |---|---|---|
> | L2.01, l. 226 | "a comfortable system is the Watt-stream engine" | a control system: Watt's steam engine |
> | L2.01, l. 535 | "vertical velocity on the poliaxis" | along the body $z$-axis |
> | L2.01, l. 562 | the controller "is going to take the error as an output" | takes the error as its input |
> | L2.01, l. 571 | "perturbations via ghosts" | gusts |
> | L2.01, l. 602 | "we want the system to become unstable" | we do not want it to become unstable |
> | L2.01, l. 604 | "a viable or bounded input, bounded output" | BIBO stability |
> | L2.02, ll. 165–167 | "domain analyzation", "domain-domain-dominalization" | domain randomisation |
> | L2.02, l. 172 | "deflecting one of the error runs" | one of the ailerons |
> | L2.02, l. 253 | "this should be X SPO" | slide correction: $\mathbf x_{SPO} = [w,\ q]^T$ |
> | L2.02, ll. 283, 312 | "adjoint of S I minus I", "the I joint" | $\mathrm{adj}(s\mathbf I-\mathbf A)$ |
> | L2.02, l. 323 | "S cubed SPO times minus M W SPO" | $(-z_q)(-m_w)$ |
> | L2.02, l. 368 | "the adjoint of matrix F is now the thing that F22 …" | $\mathrm{adj}\,\mathbf F = \begin{bmatrix}F_{22}&-F_{12}\\-F_{21}&F_{11}\end{bmatrix}$ |
> | L2.02, ll. 403–408 | "D of the SPO is Z, eta, and beta" | $\mathbf B_{SPO} = [z_\eta,\ m_\eta]^T$ |
> | L2.02, l. 472 | "this should have been theta, apologies. And this should have been s here" | slide correction in the $\theta$ closed-loop TF |
> | L2.03, l. 62 | "go to the nearest law" | the nearest loo (cistern float valve) |
> | L2.03, l. 97 | "Edward Ruth and Adolf Horwitz" | Edward Routh and Adolf Hurwitz |
> | L2.03, ll. 108–117 | "Bodhi … was actually working at NACA" | Hendrik Bode, who worked at Bell Telephone Laboratories, as did Nyquist |
> | L2.03, ll. 126–127 | "Calendar developed a method called the root locus" | Callender et al. (1936) formalised PID; the root locus is Evans's (1948), as the next slide says (l. 131) |
> | L2.03, l. 256 | "Kp E of s by 1 plus Kp E of s" | $K_PB(s)/[A(s)+K_PB(s)]$ |
> | L2.03, l. 266 | the characteristic polynomial "is the numerator of this equation" | the denominator |
> | L2.03, l. 350 | "that extra zero, sorry … that extra pull" | the extra pole at the origin |
> | L2.03, l. 377 | "this other pole that we are now injecting to the numerator" | the extra zero ($s$ in the numerator) |
> | L2.03, l. 414 | "integrator window" | integrator wind-up |
> | L2.03, ll. 489, 491 | "the jaw angle" | the yaw angle |
> | L2.03, l. 507 | "divide … by I set set" | by $I_{zz}$ |
> | L2.03, l. 536 | "about 1.5 … sorry, 1.8" | $\omega_n = 1.8$ rad/s |

## Terminology and alternative names

| Course term | Also called | Where the course uses it | Note |
|---|---|---|---|
| control error $e=r-y$ | error signal, tracking error | L2.01 | some texts define $e=y-r$; the course always uses reference minus measurement |
| control action $u$ | control input, command, actuator demand | L2.01 | |
| plant $G(s)$ | process, system | L2.01 | |
| process noise $U_P$ | disturbance, input disturbance (gusts) | L2.01 | |
| measurement noise $X_N$ | sensor noise, output noise | L2.01 | |
| closed-loop characteristic polynomial | closed-loop characteristic equation (when set to 0), $1+GC=0$ | L2.01–L2.03 | |
| P, I, D actions | proportional, integral (reset), derivative (rate) action | L2.03 | "reset" and "rate" are process-industry names |
| integrator wind-up | integral wind-up, reset wind-up | L2.03 | fixed by anti-wind-up (clamping) |
| model-free / rule-based control | heuristic control | L2.02 | PID itself is model-free (L2.02, l. 125) |
| BIBO stability | bounded-input bounded-output stability | L2.01 | |
| loop shaping (pole matching in the satellite demo) | pole placement, coefficient matching | L2.03, ll. 505–517 | strictly, "loop shaping" usually means shaping the open-loop Bode plot |
| concise derivatives ($z_w$, $m_q$, …) | normalised derivatives | L2.02 | entries of $\mathbf A=\mathbf M^{-1}\mathbf A'$ |

## Links
- Parent: [[SESA2027 Aerospace Mechanics & Control Hub]] · Previous: [[SESA2027 A5 - Frequency Response and Bode Plots]] · Next: [[SESA2027 B2 - Root Locus Method]]
- Concepts: [[Closed-Loop Transfer Function]] · [[PID Controller]] · [[Transfer Function]]
- Year 3: control architectures in [[SESA3047 1.1 - Dynamic Systems and Control Architectures]]; hub: [[SESA3047 Advanced Aerospace Mechanics & Control Hub|SESA3047 Advanced Aerospace Mechanics & Control]]

## Sources
- Lectures 2.01–2.03 (Dr S. Araujo-Estrada): slides `Lecture 2.01.pdf`–`Lecture 2.03.pdf`
- Transcripts (speech-to-text): `Lecture 2.01 recording.txt`, `Lecture 2.02 recording.txt`, `Lecture 2.03 recording.txt`
- Franklin, Powell & Emami-Naeini (2014) Ch. 1, 4; Brian Douglas, *Map of Control Theory*
- Figures: `01 - Notes/Figures/generate_amc_b1_figures.py`

## Self-study tasks

Three tasks were set in L2.01–L2.03 (marked lecturer-set). No derivations are planned for the exam (L2.03, l. 6); the cons of model-based and rule-based control were named as a possible question (L2.02, ll. 184–187).

### Core

- [ ] Lecturer-set (L2.01, ll. 671–687, working promised for upload): derive $X/R$ for the full loop with $H(s)$, process noise and measurement noise. → [[#3. Closed-loop transfer function]]
- [ ] Lecturer-set (L2.03, l. 539, "I'm going to let you play with this simulation"): in the satellite notebook, vary $\zeta$ and $\omega_n$ and relate the response to $k_p$ and $k_d$. → [[#4. PID control (L2.03)]]
- [ ] Give two cons each of model-based and rule-based control (possible exam question). → [[#2. Control classifications (L2.02)]]
- [ ] For $G = B/A$, write the closed-loop characteristic polynomials for P, I and D and say which specification each gain moves (suggested). → [[#4. PID control (L2.03)]]
- [ ] Find the steady-state error of the lecture plant under P and PI control (suggested). → [[#Worked example: P leaves an error, PI removes it]]
- [ ] PS2 Q4–Q5. → [[SESA2027 Practice Problems 2 Solutions]]
- [ ] Mock exam question. → [[SESA2027 Mock Questions#Q6. Closed loop and PID actions|Mock Q6]]

### Further practice

- [ ] Lecturer-set (L2.02, ll. 466–468, "if you follow the same procedure … for a 3×3 matrix, 4×4 matrix"): repeat the $\mathbf C\,\mathrm{adj}(s\mathbf I-\mathbf A)\mathbf B$ method for the $2\times2$ SPO, then try a $3\times3$. → [[#SPO approximation with elevator input]]
- [ ] Prove $e_\infty=1/(1+G(0)C(0))$ with the final-value theorem and show why an integrator forces it to zero (suggested). → [[#4. PID control (L2.03)]]
