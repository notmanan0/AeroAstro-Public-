---
title: "Rocket Mass Fractions"
module: "SESA1015 Intro to Aero & Astro"
type: concept
stream: "Astronautics"
aliases: ["Rocket Mass Bookkeeping", "Payload Fraction", "Structural Efficiency", "Structural Coefficient", "Mass Ratio"]
tags: [sesa1015, concept, astronautics, rocket]
status: complete
parent_lectures: ["[[SESA1015 A04 - Rocket Equation and Launch Performance]]", "[[SESA1015 A05 - Staging and Payload Fraction]]"]
related_concepts: ["[[Tsiolkovsky Rocket Equation]]", "[[Multistage Rocket Performance]]", "[[Rocket Staging]]"]
sources: ["02 - Sources/Astronautics/Astronautics - Part 3 - Launch Vehicles.pdf (pp. 22–27)"]
---

# Rocket Mass Fractions

A rocket stage's mass is split into payload $M_p$, structure $M_s$ and fuel $M_f$, and its performance depends only on two ratios of these, the payload fraction $p=M_p/M_0$ and the propellant tankage structural efficiency $s=M_s/M_f$, through the mass ratio $M_0/M_b=(1+s)/(p+s)$.

At lift-off and at burnout

$$
M_0=M_p+M_s+M_f,\qquad M_b=M_p+M_s ,
$$

because the structure stays attached until the fuel is gone. Dividing $M_0$ by $M_0$ and using $M_f=M_s/s$ gives $1=p+\frac{M_s}{M_0}\cdot\frac{1+s}{s}$, so

$$
\frac{M_s}{M_0}=\frac{s(1-p)}{1+s},
$$

and substituting into $M_0/M_b=1/(p+M_s/M_0)$,

$$
\frac{M_0}{M_b}=\frac{1+s}{p(1+s)+s(1-p)}=\frac{1+s}{p+s}.
$$

The rocket equation then reads $\Delta V_{ideal}=V_{ex}\ln\frac{1+s}{p+s}$ with no approximation. The full derivation is in [[SESA1015 A04 - Rocket Equation and Launch Performance#Deriving the mass ratio in terms of p and s|A04]].

The form makes the two limits plain. With no payload the mass ratio is $(1+s)/s$, so structure alone caps a single stage: $s=0.1$ gives 11 and $\Delta V\le V_{ex}\ln11=2.40V_{ex}$, which is why a single stage to orbit needs $V_{ex}\ge3.25$ km/s even with no payload and no losses. With no structure the mass ratio is $1/p$ and any $\Delta V$ is possible in principle. Solving for the payload,

$$
p=(1+s)e^{-\Delta V/V_{ex}}-s ,
$$

and a negative $p$ means the stage cannot deliver that $\Delta V$ at all.

For a stage of a multistage vehicle the payload $M_p$ is the whole stack above it, not the satellite; [[Multistage Rocket Performance]] uses this to build the overall payload fraction $P=\prod p_i$.

The symbols differ between sources, and the same letter can mean three different masses. In this course $M_f$ is fuel; in SESA2023 and most textbooks $m_p$ is propellant and $m_f$ or $m_{bo}$ is final (burnout) mass. Other ratios in use are the structural coefficient $\varepsilon=M_s/(M_s+M_f)=s/(1+s)$ and the SESA2023 structural ratio $\delta=M_s/M_0=s(1-p)/(1+s)$, with which the mass ratio is $1/(p+\delta)$. The SESA2023 payload ratio $\lambda=m_{pl}/m_0$ is the course's $p$.

## Related

- Topics: [[SESA1015 A04 - Rocket Equation and Launch Performance]] · [[SESA1015 A05 - Staging and Payload Fraction]] · [[SESA2023 W10 - Rocket Performance, Staging and Power Cycles]]
- Concepts: [[Tsiolkovsky Rocket Equation]] · [[Multistage Rocket Performance]] · [[Rocket Staging]] · [[Gravity and Drag Losses]]
- Sources: Astronautics Part 3, pp. 22–27.
