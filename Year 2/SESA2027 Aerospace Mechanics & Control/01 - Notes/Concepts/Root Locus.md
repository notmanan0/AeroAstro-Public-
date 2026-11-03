---
title: "Root Locus"
module: "SESA2027 Aerospace Mechanics & Control"
type: concept
stream: "Part B: Control Systems"
aliases: ["root locus method", "Evans root locus", "breakaway point", "asymptotes", "root-locus diagram"]
tags: [sesa2027, concept, control]
status: complete
parent_lectures: ["[[SESA2027 B2 - Root Locus Method]]"]
related_concepts: ["[[Poles and Zeros]]", "[[Closed-Loop Transfer Function]]", "[[Damping Ratio and Natural Frequency]]"]
sources: ["02 - Sources/Lectures/Lecture 2.04.pdf", "Evans (1948)", "Franklin, Powell & Emami-Naeini, Ch. 5"]
---

# Root Locus

The root locus is the path of the closed-loop poles, the roots of $1+KG(s) = 0$, as a gain $K$ goes from 0 to ∞. Branches start at the open-loop poles ($K = 0$) and end at the open-loop zeros or at infinity ($K\to\infty$).

The construction rules from L2.04 are:

1. Write $G$ in ZPK form and plot the poles (×) and zeros (○).
2. A point on the real axis is on the locus if the number of real poles plus zeros to its right is odd.
3. There are $n-m$ asymptotes, at angles $\theta_k = (2k+1)\pi/(n-m)$, meeting at the centroid $\sigma_a = (\sum p-\sum z)/(n-m)$.
4. Break-away and break-in points solve $dK/ds = 0$ with $K = -A(s)/B(s)$; keep only the roots that lie on the locus.
5. Departure and arrival angles are $\phi = \pi+\sum\angle(\text{zeros})-\sum\angle(\text{poles})$.
6. Sketch, then check numerically.

Reading a design off the locus uses the s-plane geometry: the distance from the origin gives $\omega_n$, the angle from the negative real axis gives $\zeta = \cos\beta$, and the real part gives the decay rate, so you choose $K$ by where you want the poles to sit. Adding a zero (PD control) pulls the locus to the left, adding phase lead and damping; adding a pole (integral action) pushes it to the right.

For $K/[s(s+4)]$ the locus covers $[-4,0]$ on the real axis, breaks away at −2 when $K = 4$ and follows asymptotes at ±90° through the centroid at −2, so the loop is stable for all $K>0$; adding a PD zero at −1 keeps the locus on the real axis ([[SESA2027 Practice Problems 2 Solutions]]). For the SPO pitch-rate plant the break-in is at $s = -1.389$, and $K<0$ is needed because the plant gain is negative ([[SESA2027 B2 - Root Locus Method]]).

![[amc_ps2_q6_root_locus.png|700]]

## Related

- The rules from the angle and magnitude conditions: [[SESA2027 B2 - Root Locus Method#Where the rules come from|B2]]
- [[Poles and Zeros]] · [[Closed-Loop Transfer Function]] · [[Damping Ratio and Natural Frequency]] · [[PID Controller]]
