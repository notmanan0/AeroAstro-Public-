---
title: "Passive and Active Transducers"
module: "FEEG1004 Electronics"
type: concept
stream: "Part E: Transducers and Measurement"
aliases: ["passive transducer", "active transducer", "self-generating sensor", "excitation"]
tags: [feeg1004, concept, transducers]
status: complete
parent_lectures: ["[[FEEG1004 E1 - Measurement Systems and Temperature Sensors]]"]
related_concepts: ["[[Transducer Static Characteristics]]", "[[RTDs and Thermistors]]", "[[Thermocouples and Cold-Junction Compensation]]"]
sources: ["02 - Sources/S2 Transducers/S2-W26-31 Transducers 01 - Measurement Systems - Lecture Slides.pdf", "Transducers lecture 1"]
---

# Passive and Active Transducers

A **passive** transducer responds to the measurand by changing a circuit parameter, and needs an external **excitation** supply to turn that change into a signal. An **active** transducer uses a material effect (thermoelectric, piezoelectric or electromagnetic) to generate a voltage or current without external power.

The parameter a passive transducer changes is a resistance, a capacitance or an inductance:

$$
R = \frac{\rho L}{A},\qquad C = \frac{\varepsilon A}{d},\qquad L = \frac{N^2}{\mathcal R}
$$

The RTD, thermistor, potentiometer, strain gauge, capacitive sensor and LVDT (which is AC-excited) are all passive. The thermocouple, piezoelectric accelerometer, tachogenerator and photovoltaic cell are active. Optical sensors, fibre and laser, form a third family.

Because a passive sensor's output scales with its excitation, any drift in the supply appears directly in the reading. The strain-gauge bridge output $V = NEG\varepsilon/4$, for example, is proportional to the excitation voltage $E$.

## Related

- [[FEEG1004 E1 - Measurement Systems and Temperature Sensors]] · [[FEEG1004 E2 - Displacement Sensors - Potentiometric, Capacitive and Inductive]]
- [[Transducer Static Characteristics]] · [[RTDs and Thermistors]] · [[Thermocouples and Cold-Junction Compensation]] · [[Gauge Factor]]
- Sources: Transducers lecture 1
