---
title: "Fracture Toughness and LEFM Validity"
module: "SESA2028 Aerospace Materials & Structures"
type: concept
stream: "Materials"
aliases: ["KIc", "Fracture toughness", "LEFM"]
tags: [sesa2028, materials, fracture-mechanics, toughness, lefm]
status: lectured
parent: ["[[SESA2028 M1 - Fracture, Toughness and Fracture Mechanics]]"]
related: ["[[Stress Intensity Factor]]", "[[Plane Strain Constraint]]", "[[Ductile-Brittle Transition]]"]
---

# Fracture Toughness and LEFM Validity

Fracture toughness $K_{Ic}$ is the critical stress intensity factor at which a crack runs unstably under mode I (opening) loading in plane strain; it is a material property in MPa√m, and fast fracture occurs when $Q\sigma\sqrt{\pi a}=K_{Ic}$.

Toughness in general is a material's resistance to fracture in the presence of a notch or defect. Charpy impact energy measures it in a way that ranks materials but cannot be used for design. $K_{Ic}$ can, because it ties stress and defect size together. Mode I is used because most brittle failures follow the path of maximum opening stress. Plane strain is used because the critical value measured on thin specimens is higher and depends on thickness; only the thick-section plateau is a constant ([[Plane Strain Constraint]]).

Linear elastic fracture mechanics (LEFM) assumes stress proportional to strain, yet nearly every structural metal yields at a crack tip. It still works as long as the plastic zone and the transition region round it are small, so that the elastic $K$ field still surrounds and loads the process zone. The lecture's rule of thumb is that the plastic zone should be about 1/50 of the crack length, of the uncracked ligament and of the thickness. A very tough, low-strength material or a small section can break this rule, and then $K$ no longer describes the tip; in a lifing answer it is worth saying that the critical crack size could instead be set by net-section yield.

Typical values give a sense of scale: engineering ceramics about 2.5–5 MPa√m, 7xxx aluminium alloys 25–45, Ti-6Al-4V 55–75, structural and HSLA steels 50–150, nickel disc alloys about 90–125. Toughness is raised by ductility (a working plastic zone redistributes stress and absorbs work), fine grains, clean steel with few brittle particles or grain-boundary segregants, a temperature above the [[Ductile-Brittle Transition]] and slow loading. High strength generally lowers it.

## Related

- Topic: [[SESA2028 M1 - Fracture, Toughness and Fracture Mechanics|M1]]
- Concepts: [[Stress Intensity Factor]] · [[Plane Strain Constraint]] · [[Ductile-Brittle Transition]] · [[Griffith Energy Balance]]
