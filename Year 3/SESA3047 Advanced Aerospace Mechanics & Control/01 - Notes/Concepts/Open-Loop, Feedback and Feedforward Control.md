---
title: "Open-Loop, Feedback and Feedforward Control"
module: "SESA3047 Advanced Aerospace Mechanics & Control"
type: concept
stream: "Chapter 1: Fundamental Concepts"
aliases: ["control arrangements", "feedback and feedforward"]
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

## Related

- [[Closed-Loop Transfer Function]] · [[Passive and Active Control]]

