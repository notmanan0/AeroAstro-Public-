---
title: "Multistage Rocket Performance"
module: "SESA1015 Intro to Aero & Astro"
type: concept
stream: "Astronautics"
aliases: ["Multistage Delta-v", "Multistage Rocket Equation", "Overall Payload Fraction"]
tags: [sesa1015, concept, astronautics, staging]
status: complete
parent_lectures: ["[[SESA1015 A05 - Staging and Payload Fraction]]"]
related_concepts: ["[[Rocket Mass Fractions]]", "[[Tsiolkovsky Rocket Equation]]", "[[Rocket Staging]]"]
sources: ["02 - Sources/Astronautics/Astronautics - Part 3 - Launch Vehicles.pdf (pp. 24–27)"]
---

# Multistage Rocket Performance

A multistage rocket is a stack of single-stage rockets fired in turn, each dropped once empty; its ideal velocity change is the sum of the stage increments, $\Delta V_{ideal}=\sum_iV_{ex,i}\ln\frac{1+s_i}{p_i+s_i}$, and its overall payload fraction is the product of the stage payload ratios, $P=\prod_ip_i$.

Each stage $i$ is treated as a rocket whose payload $M_{pi}$ is everything above it, so $M_{p1}=M_{02}$, $M_{p2}=M_{03}$, and the top stage's payload is the mass delivered to orbit. With $p_i=M_{pi}/M_{0i}$ and $s_i=M_{si}/M_{fi}$, each stage contributes $V_{ex,i}\ln(M_{0i}/M_{bi})=V_{ex,i}\ln\frac{1+s_i}{p_i+s_i}$ (see [[Rocket Mass Fractions]]), and the increments add because each stage starts from its predecessor's burnout speed. The product rule for $P$ follows by inserting the intermediate stack masses: $\frac{M_{p3}}{M_{01}}=\frac{M_{p3}}{M_{03}}\frac{M_{03}}{M_{02}}\frac{M_{02}}{M_{01}}=p_3p_2p_1$.

Staging works because it discards empty tanks and engines before they have to be accelerated further. A single stage is capped at $\Delta V\le V_{ex}\ln\frac{1+s}{s}$; a staged vehicle resets the mass ratio at every separation. For $N$ identical stages ($p_i=P^{1/N}$),

$$
\frac{\Delta V_{ideal}}{V_{ex}}=N\ln\frac{1+s}{P^{1/N}+s}\ \longrightarrow\ \frac{\ln(1/P)}{1+s}\quad\text{as } N\to\infty ,
$$

so the returns diminish quickly: two stages give the largest gain over one, three come close to the ceiling, and more than four are rarely worth their extra engines, separation systems and failure modes. For identical stages the best split gives each stage the same payload ratio, $p_i=P^{1/N}$; with different $V_{ex}$ and $s$ the optimum shifts, normally giving the upper stages high-$V_{ex}$ hydrogen engines.

A typical trap is to take the satellite alone as the payload of a lower stage; it is the whole wet upper stack. Gravity and drag losses ([[Gravity and Drag Losses]]) are subtracted from the ideal sum, not from each stage separately in the course model.

Worked numbers: for 1000 kg to LEO with $\Delta V=8.75$ km/s, $V_{ex}=3$ km/s and $s=0.1$, one stage is impossible, two equal stages need 41.2 t at lift-off and three need 31.7 t ([[SESA1015 A05 - Staging and Payload Fraction#Two identical stages to LEO|A05]]). The Saturn V had $P\approx4.3$ % to LEO.

## Related

- Topics: [[SESA1015 A05 - Staging and Payload Fraction]] · [[SESA1015 A04 - Rocket Equation and Launch Performance]] · [[SESA1015 A06 - Launch Vehicles, Systems and Interfaces]] · [[SESA2023 W10 - Rocket Performance, Staging and Power Cycles]]
- Concepts: [[Rocket Mass Fractions]] · [[Tsiolkovsky Rocket Equation]] · [[Rocket Staging]] · [[Gravity and Drag Losses]]
- Sources: Astronautics Part 3, pp. 24–27; Part 1, p. 15 (Saturn V).
