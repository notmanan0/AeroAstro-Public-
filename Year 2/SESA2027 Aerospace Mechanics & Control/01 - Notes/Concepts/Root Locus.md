---
title: "Root Locus"
module: "SESA2027 Aerospace Mechanics & Control"
type: concept
stream: "Part B: Control Systems"
aliases: ["root locus method", "Evans root locus", "breakaway point", "asymptotes"]
tags: [sesa2027, concept, control]
status: complete
parent_lectures: ["[[SESA2027 B2 - Root Locus Method]]"]
related_concepts: ["[[Poles and Zeros]]", "[[Closed-Loop Transfer Function]]", "[[Damping Ratio and Natural Frequency]]"]
sources: ["02 - Sources/Lectures/Lecture 2.04.pdf"]
---

# Root Locus

## Definition

> [!note] Definition
> The path of the **closed-loop poles**, the roots of $1+KG(s) = 0$, as a gain $K$ goes from 0 to ∞. Branches **start at the open-loop poles** ($K = 0$) and **end at the open-loop zeros or at infinity** ($K\to\infty$).

## Explanation
**Construction rules**:
1. Write $G$ in ZPK form and plot the poles (×) and zeros (○).
2. **Real axis**: a point is on the locus if the number of real poles plus zeros **to its right** is **odd**.
3. **Asymptotes**:
   - $n-m$ of them;
   - angles $\theta_k = (2k+1)\pi/(n-m)$;
   - centroid $\sigma_a = \dfrac{\sum p-\sum z}{n-m}$.
4. **Break-away / break-in**: solve $dK/ds = 0$ with $K = -A(s)/B(s)$, keeping only roots that lie on the locus.
5. **Departure / arrival angles**: $\phi = \pi+\sum\angle(\text{zeros})-\sum\angle(\text{poles})$.
6. Sketch, then check numerically.

**Reading it**:
- the distance from the origin gives $\omega_n$;
- the angle from the negative real axis gives $\zeta = \cos\beta$;
- the real part gives the decay rate.

So you choose $K$ by where you want the poles.

**Adding a zero** (PD) pulls the locus left, adding phase lead and damping. **Adding a pole** (I) pushes it right.

## Examples
- $K/[s(s+4)]$: segment $[-4,0]$, asymptotes ±90° with centroid −2, break-away at −2 ($K = 4$). Stable for all $K>0$. With a PD zero at −1 the locus stays on the real axis ([[SESA2027 Practice Problems 2 Solutions]]).
- SPO pitch-rate plant: break-in at $s = -1.389$; $K<0$ is needed because the plant gain is negative ([[SESA2027 B2 - Root Locus Method]]).

![[amc_ps2_q6_root_locus.png|700]]

## Related
- [[Poles and Zeros]] · [[Closed-Loop Transfer Function]] · [[Damping Ratio and Natural Frequency]] · [[PID Controller]]

## Sources
- Lecture 2.04; Evans (1948); Franklin, Powell & Emami-Naeini, Ch. 5
