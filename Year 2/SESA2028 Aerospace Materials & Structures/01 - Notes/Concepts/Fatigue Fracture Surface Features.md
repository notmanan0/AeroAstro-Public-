---
title: "Fatigue Fracture Surface Features"
module: "SESA2028 Aerospace Materials & Structures"
type: concept
stream: "Materials"
tags: [sesa2028, materials, fatigue, fractography]
status: complete
parent: ["[[SESA2028 M2 - Fatigue - Fracture Surfaces, Mechanisms and Lifing]]"]
related: ["[[Paris Law]]", "[[Plane Strain Constraint]]", "[[Localised Corrosion]]"]
---

# Fatigue Fracture Surface Features

Read the surface **backwards**, from final failure to origin:

| Feature | Scale | Meaning |
|---|---|---|
| **Shear lips** | by eye | $45^\circ$ rim in plane stress, marking **final overload**. Easiest to find first |
| **Final fracture zone** | by eye | rough, fibrous or granular. **Area fraction ≈ $\sigma_{max}/\sigma_{UTS}$** (first-order), so a small zone means low nominal stress |
| **Fatigue zone** | by eye | smooth, flat, at $90^\circ$ to the opening stress; looks brittle but formed by local plasticity |
| **Beach marks** | by eye / low magnification | crack-front positions at **changes in loading** (stop-start, amplitude change, oxidation during pauses). Concentric and point back to the origin |
| **Ratchet marks** | by eye | steps between **multiple origins** on slightly different planes. Many ratchets mean high local stress or a severe stress concentration |
| **Striations** | **SEM only** | one per cycle; local spacing = $da/dN$. Clear in Al and stainless, often absent in mild steel, and hidden by corrosion. **Absence does not disprove fatigue** |
| **Origin(s)** | | at a stress concentration: fillet, keyway, spline root, weld toe, corrosion pit, scratch, inclusion |

**Beach marks vs striations** (a common exam part): beach marks are macroscopic, each covers many cycles, and they record changes in the loading history. Striations are microscopic and record **individual cycles**, so they need high-magnification electron microscopy.

## Loading mode from the pattern (Metals Handbook chart)

- **Tension / unidirectional bending**: origin(s) on one side and a crack front sweeping across. Bending looks like tension, so check the load path.
- **Reversed bending**: **two** opposed fatigue zones; final fracture a central band.
- **Rotating bending**: origins all round; final fracture **offset** (rotated) and lopsided or swirly; central under severe stress concentration.
- **Torsion**: $45^\circ$ helical growth; multiple origins give a stepped "spiral staircase" or star pattern.
- Higher nominal stress gives a larger final zone. More severe stress concentration gives more origins and ratchets.

Lecture example: an aluminium dinghy mast. Two opposed zones (reversed bending from rocking), multiple origins at corrosion pits, ratchets, beach marks, and a central final fracture with shear lips.
