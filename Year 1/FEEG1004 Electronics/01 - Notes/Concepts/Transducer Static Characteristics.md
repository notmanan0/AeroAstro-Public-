---
title: "Transducer Static Characteristics"
module: "FEEG1004 Electronics"
type: concept
stream: "Part E: Transducers and Measurement"
aliases: ["sensitivity", "linearity", "resolution", "uncertainty", "repeatability", "drift", "sensor specifications"]
tags: [feeg1004, concept, transducers, measurement]
status: complete
parent_lectures: ["[[FEEG1004 E1 - Measurement Systems and Temperature Sensors]]"]
related_concepts: ["[[Accuracy and Precision]]", "[[ADC Quantisation and Resolution]]", "[[Passive and Active Transducers]]"]
sources: ["02 - Sources/S2 Transducers/S2-W26-31 Transducers 01 - Measurement Systems - Lecture Slides.pdf"]
---

# Transducer Static Characteristics

## Definition

> [!note] Definition
> - **Sensitivity** $= \Delta A_{out}/\Delta A_{in}$ (e.g. mV/°C).
> - **Linearity**: constancy of the sensitivity over the range.
> - **Resolution**: the smallest detectable increment.
> - **Precision**: spread from noise, non-linearity and hysteresis.
> - **Accuracy**: closeness of the mean to the truth.
> - **Uncertainty**: the interval containing the true value.
> - **Repeatability**, **drift** (output change without input change) and **error** (measured − true).

## Explanation
- Resolution is often overrated. A 16-bit ADC on 10 V resolves 0.15 mV, but a 10 mV noise floor means the **precision** is 10 mV.
- Linearity is quoted as the maximum deviation from the best straight line, in % of full scale.
- These are *static* properties; SESA2027 adds the dynamic ones (time constant, bandwidth).

![[ee_e1_static_characteristics.png|700]]

## Related
- Topic notes: [[FEEG1004 E1 - Measurement Systems and Temperature Sensors]]
- Year 2: [[Accuracy and Precision]] · [[ADC Quantisation and Resolution]] · [[Measurement Chain]] · [[Sensor Dynamic Models]]

## Sources
- Transducers lecture 1
