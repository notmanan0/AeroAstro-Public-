---
title: "FEEG1002 Materials Tutorial 2 - Mechanical Properties and Strengthening Solutions"
module: "FEEG1002 Mechanics, Materials and Structures"
type: tutorial
stream: "Part C: Materials"
tags: [feeg1002, tutorial-solutions, materials, tensile-test, strengthening, annealing]
sheet: "Materials Tutorial Sheet 2"
theory_notes: ["[[FEEG1002 C4 - Mechanical Properties, Dislocations and Plastic Deformation]]", "[[FEEG1002 C5 - Strengthening Mechanisms and Annealing]]"]
key_concepts: ["[[Engineering Stress-Strain Properties]]", "[[Dislocations and Slip Systems]]", "[[Strengthening Mechanisms in Metals]]", "[[Annealing of Cold-Worked Metals]]"]
status: complete
sources: ["02 - Sources/Materials/Tutorials/Tutorial Sheet 02 - Plastic Deformation-Mechanical Properties Strengthening.pdf"]
---

# FEEG1002 Materials Tutorial 2 - Mechanical Properties and Strengthening Solutions

> [!abstract] Sheet Info
> Seven questions on elastic strain, graph-based tensile properties, dislocation obstacles, yield-point behaviour, cold work and Arrhenius recrystallisation kinetics. Graph readings are reported to appropriate precision.

## Theory Links
- [[FEEG1002 C4 - Mechanical Properties, Dislocations and Plastic Deformation]] · [[FEEG1002 C5 - Strengthening Mechanisms and Annealing]]

---

## Q1: Copper rod, $d=10$ mm, $L_0=305$ mm, $\sigma=276$ MPa
$$\varepsilon_z=\frac\sigma E=\frac{276}{110000}=2.509\times10^{-3}$$
$$\boxed{\Delta L=\varepsilon_zL_0=0.765\ \text{mm}}$$

The lateral strain is $\varepsilon_d=-\nu\varepsilon_z=-0.34(2.509\times10^{-3})=-8.531\times10^{-4}$:
$$\boxed{\Delta d=\varepsilon_dd=-0.00853\ \text{mm}}$$
The diameter decreases by 8.53 $\mu$m.

## Q2: Aluminium tensile curve, $d=12.8$ mm, $L_0=50.8$ mm
Readings from the supplied graph:

| Quantity | Result |
|---|---:|
| elastic modulus | $\boxed{E\approx60\ \text{GPa}}$ |
| 0.2% proof stress | $\boxed{\sigma_{0.2}\approx275\text{–}280\ \text{MPa}}$ |
| tensile strength | $\boxed{UTS\approx370\ \text{MPa}}$ |
| failure strain / elongation | $\boxed{\varepsilon_f\approx0.165\ (16.5\%)}$ |
| extension at failure | $0.165(50.8)=\boxed{8.38\ \text{mm}}$ |

Original area:
$$A_0=\frac{\pi d^2}{4}=\frac{\pi(12.8)^2}{4}=128.68\ \text{mm}^2$$
Maximum load:
$$\boxed{F_{max}=UTS\,A_0\approx370(128.68)=47.6\ \text{kN}}$$

At 340 MPa the graph gives total strain about $0.033$. On elastic unloading, recovered strain is
$$\varepsilon_e=\frac{340}{60000}=0.00567$$
so permanent strain is about $0.0273$ and
$$\boxed{\Delta L_{permanent}\approx0.0273(50.8)=1.39\ \text{mm}}$$

> [!note] These are graph readings; $E$ and the 340 MPa intersection dominate the last answer. Reporting extra digits would be misleading.

## Q3: Why obstacles hinder dislocations
1. **Solute atoms** distort the lattice; their stress fields bind/interact with dislocations.
2. **Other dislocations** have elastic stress fields, tangle and create forest barriers.
3. **Grain boundaries** interrupt the slip plane and change crystal orientation; pile-ups must generate enough local stress to start slip in the next grain.
4. **Precipitates** differ in structure/modulus and must be cut or bypassed by bowing, both requiring extra stress.

## Q4: Why steel shows upper and lower yield points
Interstitial C/N atoms gather around and pin dislocations (Cottrell atmospheres). A relatively high stress is needed for initial breakaway: the **upper yield point**. Once mobile dislocations propagate Lüders bands, deformation continues at the lower yield stress. Work hardening then raises the flow stress again.

## Q5: Effect of work hardening
- yield strength, UTS and hardness increase;
- ductility, percentage elongation and formability decrease;
- residual stress, anisotropy and dislocation density increase;
- Young's modulus is essentially unchanged.

## Q6: Restoring properties by heat treatment
Anneal the cold-worked material:
- recovery reduces residual stress and rearranges dislocations;
- recrystallisation replaces elongated, dislocation-rich grains with new equiaxed grains, restoring ductility and lowering strength;
- stop before excessive grain growth if strength/toughness are required.

## Q7: Aluminium crystal-growth velocity
Growth is diffusion controlled, so
$$v=Ae^{-Q/RT}\quad\Rightarrow\quad \ln v=\ln A-\frac QR\frac1T$$

A least-squares fit to the four supplied points (200–400°C) gives
$$Q\approx229\ \text{kJ mol}^{-1}$$
and setting $v=10^{-2}$ m/s gives
$$\boxed{T\approx797\ \text K\approx523^\circ\text C}$$

This is an extrapolation well beyond the data, so a graph should be quoted as roughly **520°C**.

## Sources
- Materials Tutorial Sheet 2; numerical graph readings independently checked from the rendered source page.

