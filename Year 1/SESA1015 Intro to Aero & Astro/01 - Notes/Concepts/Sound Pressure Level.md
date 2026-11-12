---
title: "Sound Pressure Level"
module: "SESA1015 Intro to Aero & Astro"
type: concept
stream: "Astronautics"
aliases: ["SPL", "OASPL", "Overall sound pressure level", "Acoustic environment"]
tags: [sesa1015, concept, astronautics, launch, acoustics]
status: complete
parent_lectures: ["[[SESA1015 A03 - Launch Environment]]"]
related_concepts: ["[[Decibels]]", "[[Launch Environment Loads]]", "[[Random Vibration and Acceleration PSD]]"]
sources: ["Astronautics Part 2 (Environment), pp. 43–45"]
---

# Sound Pressure Level

The sound pressure level is the RMS acoustic pressure on a decibel scale, $L_p=20\log_{10}(p_{rms}/p_{ref})$, with reference $p_{ref}=2\times10^{-5}$ Pa (0 dB), the nominal threshold of hearing.

The decibel compares powers, and acoustic power goes as pressure squared, so $L_p=10\log_{10}(p_{rms}^2/p_{ref}^2)$, which is the factor of 20 on the pressure ratio ([[Decibels]]). Inverting, $p_{rms}=p_{ref}10^{L_p/20}$: 120 dB is 20 Pa, 140 dB is 200 Pa, and every 20 dB is a factor of ten in pressure. Spectra are given in frequency bands, usually octaves. Pressures in different bands are uncorrelated, so their mean squares add, and the overall level is $\text{OASPL}=10\log_{10}\sum_i10^{L_i/10}$; two equal bands give 3 dB more than one.

Under the Ariane fairing (p. 43) the octave bands from 31.5 Hz to 8 kHz read about 114, 127, 132, 136, 137, 134, 128, 122 and 120 dB, which sum to about 142 dB overall, an RMS pressure near 240 Pa. The launch acoustic field comes from engine noise (exhaust mixing, strongest at lift-off when it reflects off the pad, which flame trenches and water deluge reduce) and from aerodynamic noise (strongest at transonic speed, near max-q). The load on a surface scales with its area and the response with area over mass: a 2 m², 10 kg panel in a 137 dB band (142 Pa) carries about 280 N RMS, roughly 2.9 g, which is why solar arrays and antenna reflectors are tested in reverberant acoustic chambers.

The usual mistake is adding decibels arithmetically. Levels must be converted to mean-square pressures, added, and converted back.

## Related

- Topic: [[SESA1015 A03 - Launch Environment]] (§4)
- Concepts: [[Decibels]] · [[Launch Environment Loads]] · [[Random Vibration and Acceleration PSD]]
- Sources: Astronautics Part 2, pp. 43–45
