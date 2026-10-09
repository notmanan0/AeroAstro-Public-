---
title: "Loading Effect and Buffering"
module: "SESA2027 Aerospace Mechanics & Control"
type: concept
stream: "Part C: Sensing Systems"
aliases: ["loading effect", "impedance matching", "buffer amplifier", "voltage follower"]
tags: [sesa2027, concept, sensors, electronics]
status: complete
parent_lectures: ["[[SESA2027 C3 - Signal Conditioning, Digitisation and Digital Filtering]]"]
related_concepts: ["[[Measurement Chain]]", "[[ADC Quantisation and Resolution]]"]
sources: ["02 - Sources/Lectures/Lecture 3.07.pdf"]
---

# Loading Effect and Buffering

## Definition

> [!note] Definition
> Connecting a measuring device draws current from the sensor. The sensor's output impedance and the device's input impedance form a voltage divider:
> $$V_{meas} = V_{sensor}\frac{Z_{in}}{Z_{out}+Z_{in}},\qquad \varepsilon_{load} = \frac{Z_{out}}{Z_{out}+Z_{in}}$$
> An accurate measurement needs $Z_{in}\gg Z_{out}$.

## Explanation
- **The measurement must not disturb the thing measured.** Loading is a silent, systematic error: the data look clean but are low.
- It can vary with the sensor state or temperature (a changing $Z_{out}$), so calibrating it out is unreliable.
- **Buffer amplifier**: an op-amp voltage follower.
  - Its input impedance is very high ($Z_{in}\to\infty$), so it draws almost no current and $V_{meas}\approx V_{sensor}$.
  - Its low output impedance then drives the ADC.
- This is a **hardware** duty in the chain. Software cannot correct it without knowing the impedances.

## Examples
- Lecture: 10 kΩ into 100 kΩ loses 9.1 % of the signal.
- PS C Q9: 20 kΩ into 200 kΩ gives a ratio of 0.909, a 9.09 % error ([[SESA2027 Part C Problem Sheet Solutions]]).

## Related
- [[Measurement Chain]] · [[ADC Quantisation and Resolution]]
- Year 1: [[Potential Divider]] · [[Potentiometric Displacement Sensor]] · op-amp follower in [[Standard Op-Amp Configurations]]

## Sources
- Lecture 3.07
