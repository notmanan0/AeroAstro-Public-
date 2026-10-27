---
title: "Open-Loop, Feedback and Feedforward Control"
module: "SESA3047 Advanced Aerospace Mechanics & Control"
type: concept
stream: "Chapter 1: Fundamental Concepts"
aliases: ["control arrangements", "feedback and feedforward", "closed-loop control", "predetermined control", "programmed control", "preview control", "summing junction", "setpoint"]
tags: [sesa3047, concept, feedback, feedforward]
status: complete
parent_lectures: ["[[SESA3047 1.1 - Dynamic Systems and Control Architectures]]"]
related_concepts: ["[[Passive and Active Control]]", "[[Closed-Loop Transfer Function]]"]
sources: ["02 - Sources/Lectures/Chapter 1.pdf", "02 - Sources/Lectures/L2 - SESA3047.txt"]
---

# Open-Loop, Feedback and Feedforward Control

## Comparison

| Arrangement | Uses measured plant output? | Action |
|---|---:|---|
| Open loop | No | executes a command or schedule |
| Feedback | Yes | corrects measured error after it appears |
| Feedforward | Not necessarily | anticipates a known command or measured disturbance |
| Combined | Yes, plus preview/disturbance information | anticipates first, then corrects residual error |

For negative feedback,

$$
e=r-y_m.
$$

Feedback improves robustness but may destabilise a system when delay, noise, saturation or controller design is poor. Feedforward acts early but depends strongly on the accuracy of the disturbance measurement and model.

## In numbers

For a first-order plant $\tau\dot y+y=Ku+d$ under proportional feedback $u=k_p(r-y)$,

$$
\tau_{cl}=\frac{\tau}{1+Kk_p},\qquad
r-y_{ss}=\frac{r-d}{1+Kk_p}.
$$

The loop gain $1+Kk_p$ divides the time constant, the disturbance and the sensitivity to plant-gain error alike. Feedforward leaves $\tau$ unchanged. With $\tau=0.5$ s, $K=8$, $k_p=1.125$, $r=20$ °/s and a 5 °/s gust, the steady output is 25 (open loop), 18.5 (feedback) and 20 (feedforward + feedback). Worked in [[SESA3047 1.1 - Dynamic Systems and Control Architectures#9. Worked example: three architectures on one plant (suggested)|1.1 §9]] (suggested example, not lecturer-set).

## Related

- [[Closed-Loop Transfer Function]] · [[Passive and Active Control]]

