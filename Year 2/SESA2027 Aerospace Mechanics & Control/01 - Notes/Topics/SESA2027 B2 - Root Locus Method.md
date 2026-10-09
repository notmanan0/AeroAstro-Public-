---
title: "SESA2027 B2 - Root Locus Method"
module: "SESA2027 Aerospace Mechanics & Control"
type: topic
stream: "Part B: Control Systems"
order: 7
tags:
  - sesa2027
  - root-locus
  - control-design
aliases: ["Root Locus"]
date: 2026-09-23
status: complete
parent: ["[[SESA2027 Aerospace Mechanics & Control Hub]]"]
prerequisites: ["[[SESA2027 B1 - Control System Fundamentals and PID Control]]"]
next_topics: ["[[SESA2027 B3 - Frequency-Response PID Design and Ziegler-Nichols Tuning]]"]
key_concepts: ["[[Root Locus]]", "[[Poles and Zeros]]", "[[Damping Ratio and Natural Frequency]]"]
tutorial_sheets: ["[[SESA2027 Practice Problems 2 Solutions]]"]
sources: ["02 - Sources/Lectures/Lecture 2.04.pdf"]
---

# SESA2027 B2 - Root Locus Method

> [!abstract] Summary
> The **root locus** plots how the closed-loop poles, the roots of $1+KG(s) = 0$, move in the $s$-plane as one real parameter (usually the loop gain $K$) varies from 0 to $\infty$. Branches **start at the open-loop poles** and **end at the open-loop zeros or at infinity** along asymptotes. Pole position gives $\sigma$ (decay rate), $\omega$ (oscillation), $\omega_n$ (distance from the origin) and $\zeta = \cos\beta$ (angle). So the locus links gain directly to stability and transient response.

## Key Concepts
- [[Root Locus]] · [[Poles and Zeros]] · [[Damping Ratio and Natural Frequency]]

---

## 1. Stability revisited
The open-loop response is set by the roots of the characteristic polynomial:

| Root location | Response |
|---|---|
| Left half-plane, real | Exponential decay |
| Left half-plane, complex | Oscillatory decay |
| Imaginary axis | Sustained oscillation (marginal) |
| Right half-plane, real | Exponential growth |
| Right half-plane, complex | Oscillatory growth |

For $\lambda = \sigma\pm i\omega$:
- $\omega_n = \sqrt{\sigma^2+\omega^2}$ is the distance from the origin.
- $\zeta = -\sigma/\omega_n = \cos\beta$, where $\beta$ is the angle from the negative real axis.
- **Lines of constant $\zeta$** are rays from the origin: $\omega = \sqrt{\sigma^2/\zeta^2-\sigma^2}$.

## 2. Two instructive examples
Plant: double integrator $G = 1/s^2$.

**P controller**, $C = K_P$:

$$
\frac{X}{R} = \frac{K_P}{s^2+K_P},\qquad s = \pm i\sqrt{K_P}
$$

The roots move only along the imaginary axis. The response is a sustained oscillation, i.e. **marginally stable**.

**PD controller**, $C = K_D(s+K_P/K_D)$:

$$
s^2+K_Ds+K_D\frac{K_P}{K_D} = 0\quad\Rightarrow\quad s = \frac{-K_D\pm\sqrt{K_D^2-4K_D(K_P/K_D)}}{2}
$$

With $K_P/K_D = 1$:

| $K_D$ | Roots |
|---|---|
| 0 | $s_{1,2} = 0$ (repeated) |
| $0<K_D<4$ | Complex conjugate |
| $4$ | $s_{1,2} = -2$ (repeated) |
| $>4$ | Real, distinct: $s_1\to-\infty$, $s_2\to-1$ (the zero) |

The locus is a **circle** around the zero at $-1$. The system is now **stable**. The best damping on the circle is $\zeta\approx0.75$.

## 3. Six construction steps
1. Convert the open-loop TF to **zero-pole-gain** form.
2. Plot the **poles (×)** and **zeros (○)**. Branches start at the poles ($K=0$) and end at the zeros or infinity ($K\to\infty$).
3. **Real-axis segments**: a real-axis point is on the locus if the number of real poles plus zeros **to its right** is **odd**.
4. **Asymptotes**:
   - Number: $n-m$ (poles minus zeros).
   - Angles: $\theta_k = \dfrac{(2k+1)\pi}{n-m}$.
   - Centroid: $\sigma_a = \dfrac{\sum\text{poles}-\sum\text{zeros}}{n-m}$.
5. **Branch directions**:
   - Departure/arrival angle: $\phi = \pi+\sum\angle(\text{to zeros})-\sum\angle(\text{to poles})$.
   - **Break-in/away points** satisfy $\dfrac{dK}{ds} = 0$, with $K(s) = -A(s)/B(s)$.
6. **Sketch** the locus (then verify it numerically).

## 4. Worked example: SPO pitch-rate with a P controller

$$
G(s) = \frac{-1.39(s+0.306)}{s^2+0.805s+1.325},\qquad C = K,\qquad \frac{X}{R} = \frac{K[-1.39(s+0.306)]}{(s^2+0.805s+1.325)+K[-1.39(s+0.306)]}
$$

1. **ZPK form**: $G = \dfrac{-1.39(s+0.306)}{(s+0.4025-1.0784i)(s+0.4025+1.0784i)}$.
2. **Poles**: $-0.4025\pm1.0784i$. **Zero**: $-0.306$. Gain: $-1.39$. Two poles and one zero.
3. **Real axis**:
   - For $s<-0.306$, one object (the zero) is to the right, so the point is **on** the locus.
   - For $s>-0.306$, there are none, so it is off.
4. **Asymptotes**: $n-m=1$.
   - $\sigma_a = \dfrac{(-0.4025+1.0784i)+(-0.4025-1.0784i)-(-0.306)}{1} = -0.499$.
   - $\theta = 180^\circ$.
5. **Break-in point**: $K(s) = -\dfrac{s^2+0.805s+1.325}{-1.39(s+0.306)}$. Setting $dK/ds = 0$ gives $s^2+0.612s-1.07867 = 0$, so $s = 0.7767$ (reject: not on the locus) or $\boxed{s = -1.3887}$. The complex poles move left, meet at the break-in point, then one branch goes to the zero and the other to $-\infty$.
6. **Observations**:
   - Because the plant gain is negative, **negative $K$** is needed for stable, negative feedback.
   - The open loop has $\zeta\approx0.4$, and $\zeta$ increases with $|K|$.
   - At the break-in point the system becomes heavily overdamped.
   - P alone gives a good rise time but a **significant steady-state error**, which motivates adding I.

![[amc_spo_root_locus.png|620]]

> [!example] PS2 Q6: $G = K/[s(s+4)]$
> - Poles at $0$ and $-4$, no zeros.
> - Real-axis segment $[-4,0]$.
> - Two asymptotes at $\pm90^\circ$, centroid $-2$, breakaway at $s=-2$ ($K=4$).
> - $s^2+4s+K=0$ is **stable for all $K>0$**.
>
> Adding a PD zero at $-1$ gives $s^2+(4+K)s+K = 0$, so the locus stays on the real axis. There is a branch from 0 to −1, and from −4 to $-\infty$. The response is faster, non-oscillatory and well damped. See [[SESA2027 Practice Problems 2 Solutions]].

![[amc_ps2_q6_root_locus.png]]

## 5. Pros, cons and limitations

| Pros | Cons |
|---|---|
| Intuitive picture of how the poles move | Tedious by hand for high order |
| Links pole motion to stability, $\zeta$ and transient response | Handles only one parameter at a time |
| Good for choosing gains and designing lead/lag compensators | Graphical accuracy is limited |
| Shows where poles start and end | Misleading with delays, non-minimum phase or bad scaling |
| Works for any LTI rational TF | Does not show frequency-domain margins directly |
| Easy with software | Mainly SISO |

**Limitations**:
- It assumes a precise, known TF.
- It becomes unreliable with large, unstructured, nonlinear or time-varying uncertainty.
- It gives no robustness guarantees.

## Links
- Parent: [[SESA2027 Aerospace Mechanics & Control Hub]] · Previous: [[SESA2027 B1 - Control System Fundamentals and PID Control]] · Next: [[SESA2027 B3 - Frequency-Response PID Design and Ziegler-Nichols Tuning]]

## Sources
- Lecture 2.04; Franklin, Powell & Emami-Naeini (2014) Ch. 5.1–5.3
