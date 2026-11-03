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

Connecting a measuring device draws current from the sensor, and the sensor's output impedance and the device's input impedance then act as a voltage divider:

$$
V_{meas} = V_{sensor}\frac{Z_{in}}{Z_{out}+Z_{in}},\qquad \varepsilon_{load} = \frac{Z_{out}}{Z_{out}+Z_{in}} .
$$

An accurate measurement needs $Z_{in}\gg Z_{out}$. The lecture's example, a 10 kΩ sensor into a 100 kΩ input, loses 9.1 % of the signal; PS C Q9, 20 kΩ into 200 kΩ, gives a ratio of 0.909 and a 9.09 % error ([[SESA2027 Part C Problem Sheet Solutions]]).

Loading is a silent, systematic error: the data look clean but read low. It can also change with the sensor's state or temperature, because $Z_{out}$ changes, so calibrating it out is unreliable. The hardware fix is a buffer, an op-amp voltage follower. Its very high input impedance draws almost no current, so $V_{meas}\approx V_{sensor}$, and its low output impedance then drives the ADC. This is a job for the hardware in the measurement chain; software can't correct loading without knowing the impedances.

## Related

- The loading error line by line: [[SESA2027 C3 - Signal Conditioning, Digitisation and Digital Filtering#4. Loading effect and buffering|C3 §4]]
- [[Measurement Chain]] · [[ADC Quantisation and Resolution]]
- Year 1: [[Potential Divider]] · [[Potentiometric Displacement Sensor]] · the op-amp follower in [[Standard Op-Amp Configurations]]
