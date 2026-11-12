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

The static characteristics of a transducer describe how its steady output relates to a steady input, and they are the figures quoted on a sensor specification. They are static properties only; the dynamic ones (time constant, bandwidth) follow in SESA2027.

**Sensitivity** is the ratio $\Delta A_{out}/\Delta A_{in}$, in units such as mV/°C, and **linearity** is how constant that sensitivity stays over the range. Linearity is quoted as the maximum deviation from the best straight line, as a percentage of full scale. **Resolution** is the smallest increment the transducer can detect. **Precision** is the spread of readings caused by noise, non-linearity and hysteresis, while **accuracy** is how close the mean reading is to the true value. The error is the measured value minus the true value, and the uncertainty is the interval that contains the true value. Repeatability is the agreement between repeated readings of the same input, and drift is a change of output without any change of input.

Resolution is often overrated, because noise sets the useful limit. A 16-bit ADC on a 10 V range resolves 0.15 mV, but if the noise floor is 10 mV then the precision of the measurement is 10 mV, not 0.15 mV.

![[ee_e1_static_characteristics.png|700]]

## Related

- [[FEEG1004 E1 - Measurement Systems and Temperature Sensors]]
- [[Passive and Active Transducers]]
- Year 2: [[Accuracy and Precision]] · [[ADC Quantisation and Resolution]] · [[Measurement Chain]] · [[Sensor Dynamic Models]]
- Sources: Transducers lecture 1
