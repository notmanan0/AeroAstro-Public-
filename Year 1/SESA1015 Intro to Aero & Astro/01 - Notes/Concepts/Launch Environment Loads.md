---
title: "Launch Environment Loads"
module: "SESA1015 Intro to Aero & Astro"
type: concept
stream: "Astronautics"
aliases: ["Launch Loads", "Launch environment", "Quasi-static load factor", "Static acceleration"]
tags: [sesa1015, concept, astronautics, launch, loads, vibration]
status: complete
parent_lectures: ["[[SESA1015 A03 - Launch Environment]]"]
related_concepts: ["[[Random Vibration and Acceleration PSD]]", "[[Sound Pressure Level]]", "[[Launch Vehicle Interfaces]]", "[[Space Environment Hazards]]"]
sources: ["Astronautics Part 2 (Environment), pp. 39–47"]
---

# Launch Environment Loads

The launch environment loads are the mechanical loads a spacecraft carries during ascent: a quasi-static (static) acceleration that changes slowly through each burn, broadband random vibration transmitted through the adapter, and an intense acoustic field over its surfaces. Together they are usually the most severe loads in a spacecraft's life and the main driver of its structural design.

The quasi-static load is set by the non-gravitational forces on the vehicle. Free-body diagrams of the launcher ($M\dot V=T-D-Mg\sin\gamma$) and of the payload ($m_p\dot V=F_i-m_pg\sin\gamma$) give an interface force $F_i=m_p(T-D)/M$, so the load factor is $n=(T-D)/(Mg_0)$ and gravity cancels: a coasting payload feels nothing. With constant thrust the load factor rises as propellant burns, $n=T/[g_0(M_0-\dot mt)]$, and peaks at burnout at $n_{bo}=n_0M_0/M_{bo}$. Peaks are about 4 g for Ariane 5 (4.4 g at solid-booster burnout) and 3 g for the Shuttle, which throttled its engines, $T=3Mg_0$, to hold that value; the 8 g given for Saturn on p. 39 is about twice what the Saturn V flew. A 3000 kg payload at 4.4 g loads its adapter with 129 kN.

The dynamic loads ride on top. Random vibration comes from machinery, combustion and the structure's response to the acoustic field, and is specified as an acceleration PSD envelope whose area is the mean-square acceleration; the Ariane envelope on p. 42 integrates to about 51 $g^2$, or 7.1 g RMS ([[Random Vibration and Acceleration PSD]]). The acoustic field comes from engine and aerodynamic noise, peaks at lift-off and at transonic speed (where max-q falls), and reaches about 140 dB overall under a fairing, about 240 Pa RMS ([[Sound Pressure Level]]). Compact equipment is loaded mainly by the vibration through its mountings; large light structures such as solar arrays and antenna reflectors are loaded mainly by the acoustics, because the force scales with area and the response with area over mass.

The loads are not interchangeable. A quasi-static load factor is a slowly varying force that sizes primary structure; a PSD describes a random signal whose effect depends on the structure's natural frequencies and damping, and whose peaks reach about $3g_{RMS}$; an SPL is a pressure spectrum. Each is verified by its own ground test (static or centrifuge, shaker, acoustic chamber), at qualification levels above the flight envelope on a test model and at lower acceptance levels on the flight model.

## Related

- Topic: [[SESA1015 A03 - Launch Environment]]
- Concepts: [[Random Vibration and Acceleration PSD]] · [[Sound Pressure Level]] · [[Launch Vehicle Interfaces]] · [[Space Environment Hazards]] · [[Newton's Laws of Motion]]
- Later: [[SESA2028 Aerospace Materials & Structures Hub]] · [[Natural Frequencies and Mode Shapes]]
- Sources: Astronautics Part 2, pp. 39–47
