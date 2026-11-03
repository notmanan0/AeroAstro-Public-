---
title: "SESA2027 Mock Questions"
module: "SESA2027 Aerospace Mechanics & Control"
type: tutorial
subtype: self-written-mock
lecturer_set: false
stream: "Parts A–C: Dynamic Systems, Control Systems, Sensing Systems"
tags: [sesa2027, tutorial-solutions, mock-questions, self-written, exam-prep]
sheet: "Self-written mock questions (not lecturer-set)"
theory_notes: ["[[SESA2027 A1 - Dynamic Systems and Aircraft Equations of Motion]]", "[[SESA2027 A2 - Longitudinal State-Space Model and Aerodynamic Derivatives]]", "[[SESA2027 A3 - Longitudinal Dynamic Modes - SPO and Phugoid]]", "[[SESA2027 A4 - Laplace Transforms, Transfer Functions and Step Response]]", "[[SESA2027 A5 - Frequency Response and Bode Plots]]", "[[SESA2027 B1 - Control System Fundamentals and PID Control]]", "[[SESA2027 B2 - Root Locus Method]]", "[[SESA2027 B3 - Frequency-Response PID Design and Ziegler-Nichols Tuning]]", "[[SESA2027 B4 - Robustness, Stability vs Manoeuvrability and Design Process]]", "[[SESA2027 C1 - Sensing Systems, Sensor Principles and Sensor Fusion]]", "[[SESA2027 C2 - Sensor Characteristics, Dynamics and Design]]", "[[SESA2027 C3 - Signal Conditioning, Digitisation and Digital Filtering]]"]
parent: ["[[SESA2027 Aerospace Mechanics & Control Hub]]"]
status: complete
coverage: "All lectured content, L1.01–L3.08"
date: 2026-10-28
sources: ["01 - Notes/Topics", "01 - Notes/SESA2027 Formula Sheet.md", "02 - Sources/Problem Sheets"]
---

# SESA2027 Mock Questions

> [!warning] Self-written mock questions, not lecturer-set
> **These questions were written from the lectured content of all three parts. They are not the real SESA2027 paper**, and the format, marks and timings are guesses.
>
> **What was checked first (28 Oct 2026):** `03 - Exams & Past Papers` is empty, so there is no past or specimen paper. The three lecturer sheets ([[SESA2027 Practice Problems 1 Solutions|PP1]], [[SESA2027 Practice Problems 2 Solutions|PP2]], [[SESA2027 Part C Problem Sheet Solutions|Part C]]) are already solved; every number here is different from them. The question styles follow what the lecturers said could be asked (collected on the [[SESA2027 Aerospace Mechanics & Control Hub|hub]]): stability from the real part, Routh–Hurwitz in words, the negligible derivatives, the final value of a step, a pole–zero map, GM and PM from a Bode plot, a full-marks root-locus sketch, ZN against other tuning methods.

> [!info] How to use this sheet
> - **Timing:** about **1.8 min per mark**, so each 10-mark question is about 18 minutes. The whole sheet is 120 marks (about 3.5 hours): do three or four questions per sitting.
> - Attempt each question closed-book, then open the collapsed solution. Each solution links to the section of the topic note it tests.
> - Conventions follow the lectures: body axes $x$ forward, $y$ starboard, $z$ down; $\mathbf R_{BE}=\mathbf R_x(\phi)\mathbf R_y(\theta)\mathbf R_z(\psi)$; $s=\sigma+i\omega$; overshoot as a percentage; settling time to 1 %.
> - Every number in a solution was recomputed in Python (numpy/scipy).

| Q | Topic | Marks | Time |
|---|---|---:|---:|
| 1 | Body axes, rotation and linearisation | 10 | 18 min |
| 2 | Gravity and derivatives in the longitudinal model | 10 | 18 min |
| 3 | Modes from a factorised quartic | 10 | 18 min |
| 4 | Step response of a second-order system | 10 | 18 min |
| 5 | Bode magnitude and phase | 10 | 18 min |
| 6 | Closed loop and PID actions | 10 | 18 min |
| 7 | Root locus sketch and stable gain range | 10 | 18 min |
| 8 | Margins and PD design | 10 | 18 min |
| 9 | Robustness and the three closed-loop transfer functions | 10 | 18 min |
| 10 | Strain gauge bridge and complementary filter | 10 | 18 min |
| 11 | Second-order sensor design | 10 | 18 min |
| 12 | Range mapping, ADC and aliasing | 10 | 18 min |

---

## Q1. Body axes, rotation and linearisation

**[10 marks, ≈18 min]** · Tests [[SESA2027 A1 - Dynamic Systems and Aircraft Equations of Motion|A1]]

(a) Sketch a side view of an aircraft with its body axes. Mark the positive directions of $U$, $W$, $q$ and $M$. **[2]**

(b) An aircraft flies due east at 200 m/s in level flight, so $\mathbf v_E=(0,200,0)$ m/s in Earth axes, with attitude $\psi=90°$, $\theta=10°$, $\phi=0$. Find $\mathbf v_B$ and the angle of attack. **[3]**

(c) Find the body-axis components of gravity for $\theta=10°$, $\phi=20°$. **[2]**

(d) Linearise $Y=m(\dot V+rU-pW)$ about trim in stability axes. Explain physically why one product term survives. **[3]**

> [!example]- Solution
> **(a)** $x$ forward along the fuselage, $z$ down, $y$ out of the page in a nose-right side view (starboard side). $U$ along $+x$, $W$ along $+z$ (down), $q$ and $M$ positive **nose up** by the right-hand rule about $y$. See [[SESA2027 A1 - Dynamic Systems and Aircraft Equations of Motion#Body axes and notation|A1 body axes]]. *[1 for axes, 1 for signs]*
>
> **(b)** $\mathbf R_z(90°)$ turns east into body $x$: $\mathbf R_z\mathbf v_E=(200,0,0)$. Then $\mathbf R_y(10°)$:
>
> $$\mathbf v_B=\begin{pmatrix}\cos10°&0&-\sin10°\\0&1&0\\\sin10°&0&\cos10°\end{pmatrix}\begin{pmatrix}200\\0\\0\end{pmatrix}=\begin{pmatrix}197.0\\0\\34.7\end{pmatrix}\ \text{m/s}$$
>
> $\alpha=\tan^{-1}(34.7/197.0)=10.0°$: in level flight the angle of attack equals the pitch attitude. *[2 + 1]*
>
> **(c)** Third column of $\mathbf R_{BE}$: $\mathbf g_B=9.81(-\sin10°,\ \sin20°\cos10°,\ \cos20°\cos10°)=(-1.70,\ 3.30,\ 9.08)$ m/s². Check: magnitude 9.81. *[2]*
>
> **(d)** Substitute $U=U_\infty+u$, $V=v$, $W=w$: $Y=m(\dot v+rU_\infty+ru-pw)$. Drop the products of perturbations $ru$, $pw$: $\Delta Y=m(\dot v+rU_\infty)$. The term $rU_\infty$ survives because $U_\infty$ is large: yawing at rate $r$ swings the big forward velocity sideways in body axes, which needs a side force (the lateral analogue of the pull-up $qU_\infty$ term, [[SESA2027 A1 - Dynamic Systems and Aircraft Equations of Motion#Simplifications|A1 §3]]). *[2 + 1]*

---

## Q2. Gravity and derivatives in the longitudinal model

**[10 marks, ≈18 min]** · Tests [[SESA2027 A2 - Longitudinal State-Space Model and Aerodynamic Derivatives|A2]]

(a) In a $3°$ climb, express $\Delta X_g$ and $\Delta Z_g$ for a small pitch perturbation $\theta$. **[2]**

(b) At $\rho=1.0$ kg/m³, $U_\infty=150$ m/s, $S=30$ m², $\bar c=3$ m, convert $Z_w=-4.5$, $M_w=-0.5$, $M_q=-8.0$ and $M_{\dot w}=-3.0$ to dimensional form, with units. **[3]**

(c) Given the full Taylor expansion of $\Delta X_a$, $\Delta Z_a$, $\Delta M_a$ in $u,w,q,\dot w$, which derivatives can be neglected, and why? **[2]**

(d) For $\mathbf A=\begin{bmatrix}-1.2&150\\-0.03&-1.5\end{bmatrix}$, $\mathbf B=\begin{bmatrix}-0.1\\-6\end{bmatrix}$, $\mathbf C=[0\ 1]$, find $q(s)/\eta(s)$ and its poles. **[3]**

> [!example]- Solution
> **(a)** $\Delta X_g=-mg\theta\cos3°=-0.9986\,mg\theta$, $\Delta Z_g=-mg\theta\sin3°=-0.0523\,mg\theta$. *[1 + 1]* ([[SESA2027 A2 - Longitudinal State-Space Model and Aerodynamic Derivatives#1. Gravitational contributions (L1.04)|A2 §1]])
>
> **(b)** $\tfrac12\rho U_\infty S=2250$ kg/s.
> - $\mathring Z_w=-4.5\times2250=-10\,125$ N s/m.
> - $\mathring M_w=-0.5\times2250\times3=-3375$ N s.
> - $\mathring M_q=-8.0\times2250\times9=-162\,000$ N m s.
> - $\mathring M_{\dot w}=-3.0\times\tfrac12\times1.0\times30\times9=-405$ N s².
>
> *[2 for values, 1 for units]* ([[SESA2027 A2 - Longitudinal State-Space Model and Aerodynamic Derivatives#Dimensional vs dimensionless derivatives|A2 table]])
>
> **(c)** $\mathring X_q$ and $\mathring X_{\dot w}$: pitch rate and normal acceleration barely change the drag. At low Mach also $\mathring M_u$. This is the stated exam answer (L1.04, ll. 166–169). *[2]*
>
> **(d)** $\lvert s\mathbf I-\mathbf A\rvert=(s+1.2)(s+1.5)+150\times0.03=s^2+2.7s+6.3$. The second row of the adjoint is $[-0.03,\ s+1.2]$, so $\mathbf C\,\mathrm{adj}\,\mathbf B=0.003-6(s+1.2)=-6s-7.197$:
>
> $$\frac{q}{\eta}=\frac{-6(s+1.1995)}{s^2+2.7s+6.3}$$
>
> Poles $-1.35\pm2.116i$: $\omega_n=2.51$ rad/s, $\zeta=0.54$, stable. *[2 + 1]* ([[SESA2027 A2 - Longitudinal State-Space Model and Aerodynamic Derivatives#Worked example: SPO state space to transfer function (PS2 Q3)|A2 worked example]])

---

## Q3. Modes from a factorised quartic

**[10 marks, ≈18 min]** · Tests [[SESA2027 A3 - Longitudinal Dynamic Modes - SPO and Phugoid|A3]]

An aircraft's longitudinal stability quartic factorises as

$$
(\lambda^2+1.6\lambda+6.4)(\lambda^2-0.004\lambda+0.0049)=0
$$

(a) Find the four roots and sketch them on the complex plane. **[2]**

(b) For each mode give $\omega_n$, $\zeta$, the period, and the half-life or time to double. **[4]**

(c) Identify each mode and comment on its stability. Is this acceptable? **[2]**

(d) State the Routh–Hurwitz criterion in words and say what it predicts here without calculation. **[2]**

> [!example]- Solution
> **(a)** $\lambda_{1,2}=-0.8\pm2.4i$; $\lambda_{3,4}=+0.002\pm0.070i$. Sketch: one pair well into the left half-plane, the other just right of the imaginary axis, close to the origin. *[1 + 1]*
>
> **(b)** Mode 1: $\omega_n=\sqrt{6.4}=2.53$ rad/s, $\zeta=1.6/(2\times2.53)=0.316$, $T=2\pi/2.4=2.62$ s, $t_{1/2}=\ln2/0.8=0.87$ s. Mode 2: $\omega_n=\sqrt{0.0049}=0.070$ rad/s, $\zeta=-0.004/(2\times0.07)=-0.029$, $T=2\pi/0.070=89.8$ s; unstable, so no half-life: $t_2=\ln2/0.002=347$ s. *[2 + 2]* ([[SESA2027 A3 - Longitudinal Dynamic Modes - SPO and Phugoid#2. Damping factor and natural frequency|A3 §2]])
>
> **(c)** Mode 1 (larger $\omega_n$) is the **short-period oscillation**: stable and reasonably damped. Mode 2 is the **phugoid**: slightly unstable, $\zeta<0$ because $\sigma>0$. The amplitude doubles only every 347 s, about 4 cycles, which a pilot easily corrects; CS-25 allows a lightly damped (even mildly unstable) phugoid. *[1 + 1]*
>
> **(d)** All coefficients of the quartic positive **and** the Routh discriminant positive. Here multiplying out gives $\lambda^4+1.596\lambda^3+6.3985\lambda^2-0.0178\lambda+0.0314$: the $\lambda$ coefficient is negative, so the test fails at the first condition, consistent with the unstable phugoid. *[1 + 1]* ([[SESA2027 A3 - Longitudinal Dynamic Modes - SPO and Phugoid#1. General solution (L1.05)|A3 §1]])

---

## Q4. Step response of a second-order system

**[10 marks, ≈18 min]** · Tests [[SESA2027 A4 - Laplace Transforms, Transfer Functions and Step Response|A4]]

$$
G(s)=\frac{12}{s^2+2.4s+9}
$$

(a) Find $\omega_n$, $\zeta$ and the poles. **[2]**

(b) A step of size 2 is applied. Find the final value with the final-value theorem. **[2]**

(c) Find $t_r$, $t_p$, $OS$ (%) and $t_s$ (1 %). **[4]**

(d) Sketch the response, marking the four quantities. **[2]**

> [!example]- Solution
> **(a)** $\omega_n=3$ rad/s, $2\zeta\omega_n=2.4\Rightarrow\zeta=0.4$. Poles $-1.2\pm2.75i$. *[2]*
>
> **(b)** $\lim_{s\to0}s\cdot\dfrac{2}{s}\cdot\dfrac{12}{s^2+2.4s+9}=\dfrac{24}{9}=2.667$. *[2]* ([[SESA2027 A4 - Laplace Transforms, Transfer Functions and Step Response#3. SPO step response|A4 §3]])
>
> **(c)** $t_r\approx1.8/3=0.60$ s; $t_p=\pi/(3\sqrt{1-0.16})=1.143$ s; $OS=e^{-0.4\pi/\sqrt{0.84}}=25.4\,\%$ (keep the square root); $t_s\approx4.6/1.2=3.83$ s. *[1 each]*
>
> **(d)** Starts at 0 with zero slope, crosses the final value 2.667, peaks at $2.667\times1.254=3.34$ at 1.14 s, one undershoot, inside ±1 % after about 3.8 s. *[2]*
>
> > [!check] Simulation: peak 3.344 at $t=1.143$ s. ✓

---

## Q5. Bode magnitude and phase

**[10 marks, ≈18 min]** · Tests [[SESA2027 A5 - Frequency Response and Bode Plots|A5]] and [[SESA2027 B3 - Frequency-Response PID Design and Ziegler-Nichols Tuning|B3]]

$$
L(s)=\frac{50}{(s+1)(s+10)}
$$

(a) Find $\lvert L(i\omega)\rvert$ in dB and $\angle L(i\omega)$ at $\omega=0.1,\ 1,\ 10,\ 100$ rad/s. **[4]**

(b) Sketch the asymptotic Bode plot, labelling the corner frequencies and slopes. **[2]**

(c) Find the gain crossover frequency and the phase margin. What is the gain margin? **[4]**

> [!example]- Solution
> **(a)**
>
> | $\omega$ | 0.1 | 1 | 10 | 100 |
> |---|---|---|---|---|
> | $\lvert L\rvert$ (dB) | 13.94 | 10.93 | −9.07 | −46.06 |
> | $\angle L$ | −6.3° | −50.7° | −129.3° | −173.7° |
>
> e.g. at $\omega=1$: $\lvert L\rvert=50/(\sqrt2\sqrt{101})=3.518$; $\angle L=-45°-5.7°$. *[4]*
>
> **(b)** Flat at $20\log_{10}5=13.98$ dB to the corner at 1 rad/s, then −20 dB/dec to the corner at 10 rad/s, then −40 dB/dec. Phase 0 → −90° around 1 rad/s and another −90° around 10 rad/s, tending to −180°. *[2]*
>
> **(c)** $\lvert L\rvert=1$: $(\omega^2+1)(\omega^2+100)=2500\Rightarrow\omega^4+101\omega^2-2400=0\Rightarrow\omega^2=19.86$, $\omega_{gc}=4.46$ rad/s. $\angle L=-\tan^{-1}4.46-\tan^{-1}0.446=-101.4°$, so $PM=78.6°$. The phase only tends to −180°, so the phase crossover is at infinity and **GM is infinite** (the stated exam case, L2.05, l. 476). *[2 + 1 + 1]* ([[SESA2027 B3 - Frequency-Response PID Design and Ziegler-Nichols Tuning#1. Why frequency-response design (L2.05)|B3 §1]])

---

## Q6. Closed loop and PID actions

**[10 marks, ≈18 min]** · Tests [[SESA2027 B1 - Control System Fundamentals and PID Control|B1]]

Plant $G(s)=\dfrac{2}{(s+1)(s+4)}$, unity feedback.

(a) With $C=K_P$, write the closed-loop transfer function and characteristic polynomial. **[2]**

(b) Find $K_P$ for closed-loop $\zeta=0.5$, then the closed-loop poles and overshoot. **[3]**

(c) Find the steady-state error to a unit step at that gain. **[2]**

(d) What does adding integral action change, and what does it cost? Give one con of model-based control. **[3]**

> [!example]- Solution
> **(a)** $\dfrac{X}{R}=\dfrac{2K_P}{s^2+5s+4+2K_P}$; characteristic polynomial $s^2+5s+(4+2K_P)$. *[2]*
>
> **(b)** $2\zeta\omega_n=5$ with $\zeta=0.5\Rightarrow\omega_n=5$, so $4+2K_P=25$, $K_P=10.5$. Poles $-2.5\pm4.33i$; $OS=e^{-0.5\pi/\sqrt{0.75}}=16.3\,\%$. *[1 + 1 + 1]*
>
> **(c)** $e_\infty=1/(1+K_PG(0))=1/(1+10.5\times0.5)=0.16$. *[2]* ([[SESA2027 B1 - Control System Fundamentals and PID Control#4. PID control (L2.03)|B1 §4]])
>
> **(d)** An integrator makes $C(0)\to\infty$, so $e_\infty=0$. It adds a closed-loop pole (and $-90°$ of phase at low frequency), so the response becomes slower and can overshoot more, with a risk of integrator wind-up. Model-based control needs an accurate model and is sensitive to model error (L2.02, ll. 184–187). *[2 + 1]*

---

## Q7. Root locus sketch and stable gain range

**[10 marks, ≈18 min]** · Tests [[SESA2027 B2 - Root Locus Method|B2]]

$$
KG(s)=\frac{K(s+3)}{s(s+1)(s+5)},\qquad K>0
$$

(a) Mark the poles and zeros and the real-axis segments. **[2]**

(b) Find the number, angles and centroid of the asymptotes. **[2]**

(c) Find the breakaway point and the gain there. **[3]**

(d) Is the closed loop stable for all $K>0$? Use Routh–Hurwitz. Sketch the locus. **[3]**

> [!example]- Solution
> **(a)** Poles $0,-1,-5$; zero $-3$. Segments: $[-1,0]$ (one to the right) and $[-5,-3]$ (three to the right). *[2]*
>
> **(b)** $n-m=2$ asymptotes at $\pm90°$ from $\sigma_a=(0-1-5-(-3))/2=-1.5$. *[2]*
>
> **(c)** $A=s^3+6s^2+5s$, $B=s+3$: $A'B-AB'=(3s^2+12s+5)(s+3)-(s^3+6s^2+5s)=2s^3+15s^2+36s+15=0$. The only real root is $s=-0.522$, on $[-1,0]$. $K=-A/B=0.451$ there. *[2 + 1]*
>
> **(d)** Characteristic polynomial $s^3+6s^2+(5+K)s+3K$. Routh needs $6(5+K)>3K$, i.e. $30+3K>0$: true for all $K>0$. So the loop is **stable for every positive gain**: the zero pulls the asymptotes to $\sigma=-1.5$, in the left half-plane. Sketch: branches from 0 and −1 meet at −0.522, break away and approach the vertical asymptotes at $-1.5$; the branch from −5 goes to the zero at −3. *[2 + 1]* ([[SESA2027 B2 - Root Locus Method#Worked example: three poles, three asymptotes|B2]] for the contrast without a zero)
>
> > [!check] `np.roots` at $K=1,10,100$: complex pair real parts $-0.55$, $-0.94$, $-1.44$, approaching $-1.5$. ✓

---

## Q8. Margins and PD design

**[10 marks, ≈18 min]** · Tests [[SESA2027 B3 - Frequency-Response PID Design and Ziegler-Nichols Tuning|B3]]

(a) A Bode plot shows the phase crossing −180° at 5 rad/s, where the magnitude is −8 dB. What is the gain margin, and what does it mean? **[2]**

(b) A plant has $\lvert G(2i)\rvert=0.4$ and $\angle G(2i)=-160°$. Design a PID in standard form for $\omega_{gc}=2$ rad/s and $PM=50°$, using $T_I=3/\omega_{gc}$. Give $K_p$, $T_I$, $T_D$, $K_i$, $K_d$. **[5]**

(c) The same plant oscillates steadily under P control at $K_u=6$ with $T_u=1.2$ s. Give the ZN PID gains and one reason to refine them. **[3]**

> [!example]- Solution
> **(a)** $GM=-(-8)=8$ dB: the loop gain could rise by a factor $10^{8/20}=2.5$ before the closed loop goes unstable. *[2]*
>
> **(b)** $\phi_{PD}=50-(180-160)=30°$. $T_D=\tan30°/2=0.289$ s. $T_I=3/2=1.5$ s. $K_p=1/\left(0.4\sqrt{1+(2\times0.289)^2}\right)=1/(0.4\times1.155)=2.165$. $K_i=K_p/T_I=1.443$, $K_d=K_pT_D=0.625$. *[1 each for $\phi_{PD}$, $T_D$, $T_I$, $K_p$, and the parallel gains]* ([[SESA2027 B3 - Frequency-Response PID Design and Ziegler-Nichols Tuning#3. Eight-step frequency-response design|B3 §3]])
>
> **(c)** $K_p=0.6\times6=3.6$, $T_I=0.5\times1.2=0.6$ s, $T_D=0.125\times1.2=0.15$ s. ZN aims at a quarter-decay ratio, about $\zeta\approx0.22$ and roughly 50 % overshoot for a dominant pair: too aggressive for handling-quality and comfort limits. *[2 + 1]*

---

## Q9. Robustness and the three closed-loop transfer functions

**[10 marks, ≈18 min]** · Tests [[SESA2027 B4 - Robustness, Stability vs Manoeuvrability and Design Process|B4]]

$G(s)=\dfrac{K(s+z)}{s^2+2\zeta\omega_ns+\omega_n^2}$ with $K=-2$, $z=0.5$, $\omega_n=2$ rad/s, $\zeta=0.3$; P control $K_p=-1.5$.

(a) Why is a negative $K_p$ correct here? Why must $T_I$ and $T_D$ always be positive? **[2]**

(b) Find the closed-loop characteristic polynomial and show the loop is stable. **[3]**

(c) If the zero were at $z=-0.5$ instead, by how much could $\omega_n$ be over-estimated before the loop goes unstable? **[3]**

(d) Write the disturbance and noise transfer functions and explain why one controller cannot make both small at the same frequency. **[2]**

> [!example]- Solution
> **(a)** The plant's static gain $Kz/\omega_n^2$ is negative, so a negative $K_p$ restores **negative** feedback ($KK_p>0$). Negative $T_D$ gives anti-damping and negative $T_I$ integrates the wrong way and diverges (L2.07). *[1 + 1]*
>
> **(b)** $s^2+(KK_p+2\zeta\omega_n)s+(\omega_n^2+KK_pz)=s^2+4.2s+5.5$. Both coefficients positive, so stable (Routh for $n=2$). *[2 + 1]*
>
> **(c)** $c=\omega_n^2+KK_pz=\omega_n^2-1.5$. Stable while $\omega_n^2>1.5$, i.e. $\omega_n>1.225$ rad/s. The true $\omega_n$ may be up to $1-1.225/2=39\,\%$ lower than the modelled 2 rad/s. *[2 + 1]* ([[SESA2027 B4 - Robustness, Stability vs Manoeuvrability and Design Process#Worked example: how much model error can a design take?|B4 worked example]])
>
> **(d)** Disturbance: $G/(1+GC)=G\,S$. Noise: $-GC/(1+GC)=-T$. Since $S+T=1$, making $S$ small (good gust rejection) makes $\lvert T\rvert\approx1$ (noise passes). Separate them in frequency: high loop gain at low frequency, low loop gain at high frequency. *[2]*

---

## Q10. Strain gauge bridge and complementary filter

**[10 marks, ≈18 min]** · Tests [[SESA2027 C1 - Sensing Systems, Sensor Principles and Sensor Fusion|C1]]

(a) Two gauges ($G=2.1$) are bonded top and bottom of a bending cantilever and wired in adjacent arms of a bridge with $V_s=10$ V. The output is 3.15 mV. Find the strain. What strain would you wrongly report with the quarter-bridge formula? **[3]**

(b) Why does this arrangement cancel temperature effects? **[2]**

(c) A complementary filter runs at $\Delta t=5$ ms with time constant $\tau=0.25$ s. Find $\alpha$ and write the update equation. **[2]**

(d) The gyro has a bias of $0.2\ °/\text{s}$. Find the steady attitude error of the filter, and compare with integrating the gyro alone for 2 minutes. **[3]**

> [!example]- Solution
> **(a)** Half bridge: $V_G=(V_s/2)G\varepsilon\Rightarrow\varepsilon=2\times3.15\times10^{-3}/(10\times2.1)=3.0\times10^{-4}=300\ \mu\varepsilon$. The quarter-bridge formula $4V_G/(V_sG)$ gives 600 µε, double. *[2 + 1]*
>
> **(b)** A temperature change raises both gauge resistances equally. In adjacent arms they appear as a ratio, $\Delta R_T$ cancels from the numerator, and only a negligible change of scale remains ([[SESA2027 C1 - Sensing Systems, Sensor Principles and Sensor Fusion#4.1 Resistive: strain gauges and the Wheatstone bridge|C1 §4.1]]). *[2]*
>
> **(c)** $\alpha=\tau/(\tau+\Delta t)=0.25/0.255=0.980$. $\hat\theta_k=0.980(\hat\theta_{k-1}+\omega_k\Delta t)+0.020\,\theta_{acc,k}$. *[1 + 1]*
>
> **(d)** Steady error $\tau b=0.25\times0.2=0.05°$ (check: $\alpha b\Delta t/(1-\alpha)=0.05°$). The gyro alone drifts $0.2\times120=24°$. *[2 + 1]* ([[SESA2027 C1 - Sensing Systems, Sensor Principles and Sensor Fusion#Complementary filter|C1 §5]])

---

## Q11. Second-order sensor design

**[10 marks, ≈18 min]** · Tests [[SESA2027 C2 - Sensor Characteristics, Dynamics and Design|C2]]

(a) A thermocouple ($\tau=2$ s) is plunged from 20 °C into a 220 °C gas stream. Find its reading after 2 s and 3 s, and the time to read within 1 %. **[3]**

(b) An accelerometer has $f_n=50$ Hz and $\zeta=0.7$. Find the amplitude ratio, phase and time delay when it measures a 15 Hz vibration. **[4]**

(c) Repeat the amplitude ratio for $\zeta=0.2$ and explain which you would choose. **[3]**

> [!example]- Solution
> **(a)** $T=20+200(1-e^{-t/2})$: 146.4 °C at 2 s (63.2 % of the step), 175.4 °C at 3 s. Within 1 % after $4.6\tau=9.2$ s. *[1 + 1 + 1]*
>
> **(b)** $r=15/50=0.3$. $\lvert G\rvert/K=1/\sqrt{(1-0.09)^2+(2\times0.7\times0.3)^2}=1/\sqrt{0.8281+0.1764}=0.998$. Phase $-\tan^{-1}(0.42/0.91)=-24.8°$, a delay of $24.8/(360\times15)=4.6$ ms ($\approx2\zeta/\omega_n=4.5$ ms). *[2 + 1 + 1]*
>
> **(c)** $\zeta=0.2$: $1/\sqrt{0.8281+0.0144}=1.090$, a 9 % over-reading (closer to resonance). Choose $\zeta=0.7$: flat magnitude to within 0.2 % and a nearly constant delay, so the waveform is not distorted ([[SESA2027 C2 - Sensor Characteristics, Dynamics and Design#Optimal damping for second-order sensors|C2 §3]]). *[2 + 1]*

---

## Q12. Range mapping, ADC and aliasing

**[10 marks, ≈18 min]** · Tests [[SESA2027 C3 - Signal Conditioning, Digitisation and Digital Filtering|C3]]

A pressure sensor outputs ±25 mV. It feeds a 10-bit, 0–3.3 V ADC sampling at 200 Hz.

(a) Find the conditioning gain and offset. What happens to a 30 mV transient? **[3]**

(b) Find the ADC resolution, referred to the sensor. **[2]**

(c) A 330 Hz pump vibration reaches the sensor. At what frequency does it appear in the data? Size a first-order anti-alias filter. **[3]**

(d) The total latency is 30 ms and the pressure loop crosses over at 5 rad/s. How much phase margin is lost? An 8-sample moving average is added: how much extra delay? **[2]**

> [!example]- Solution
> **(a)** $A_v=3.3/0.05=66$; $V_{os}=0-66\times(-0.025)=1.65$ V. A 30 mV transient gives $66\times0.03+1.65=3.63$ V $>3.3$ V: **clipped**, and the peak is lost for good. *[1 + 1 + 1]*
>
> **(b)** $Q=3.3/1024=3.22$ mV at the ADC, $3.22/66=48.8$ µV at the sensor. *[2]*
>
> **(c)** $f_N=100$ Hz. $\lvert330-2\times200\rvert=70$ Hz lies in $[0,100]$, so the vibration appears at 70 Hz. Anti-alias RC: $f_c\le100$ Hz, so $\tau\ge1/(\pi\times200)=1.59$ ms (and in practice lower $f_c$, since a first-order filter attenuates only 3 dB at $f_c$). *[2 + 1]*
>
> **(d)** $\Delta PM=-5\times0.030=-0.15$ rad $=-8.6°$. Moving average: $(8-1)/2\times5$ ms $=17.5$ ms more. *[1 + 1]* ([[SESA2027 C3 - Signal Conditioning, Digitisation and Digital Filtering#6. Latency|C3 §6]])

---

## Links

- Parent: [[SESA2027 Aerospace Mechanics & Control Hub]]
- Formula sheet: [[SESA2027 Formula Sheet]]
- Lecturer sheets: [[SESA2027 Practice Problems 1 Solutions]] · [[SESA2027 Practice Problems 2 Solutions]] · [[SESA2027 Part C Problem Sheet Solutions]]
