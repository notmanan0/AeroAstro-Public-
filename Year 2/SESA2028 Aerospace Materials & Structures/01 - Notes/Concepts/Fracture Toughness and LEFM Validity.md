---
title: "Fracture Toughness and LEFM Validity"
module: "SESA2028 Aerospace Materials & Structures"
type: concept
stream: "Materials"
tags: [sesa2028, materials, fracture-mechanics, toughness, lefm]
status: complete
parent: ["[[SESA2028 M1 - Fracture, Toughness and Fracture Mechanics]]"]
related: ["[[Stress Intensity Factor]]", "[[Plane Strain Constraint]]", "[[Ductile-Brittle Transition]]"]
---

# Fracture Toughness and LEFM Validity

**Fracture toughness** $K_{Ic}$ is the critical stress intensity at which a crack runs unstably in **mode I** (opening) under **plane-strain** conditions. It is a material property; units are $\mathrm{MPa\sqrt m}$.

$$
\text{fast fracture when}\quad Q\sigma\sqrt{\pi a}=K_{Ic}.
$$

## Why mode I and plane strain?

- Most brittle failures follow the **maximum opening stress**, so mode I is the worst case.
- $K_{crit}$ measured on thin specimens is higher (plane stress lets shear lips form) and falls to a **plateau** as thickness increases. Only the plateau is thickness-independent, so **only the plane-strain value is a true material constant** ([[Plane Strain Constraint]]).

## When is linear elastic fracture mechanics (LEFM) valid?

$K$ assumes linear elasticity, but real crack tips yield. LEFM still works if the **$K$-dominated field surrounds a small plastic zone**. The lecture's rule of thumb: plastic zone ≲ **1/50** of the crack length, the uncracked ligament **and** the thickness.

If that fails (very tough, low-strength material, or small sections), $K$ no longer describes the crack tip. Elastic-plastic methods (J-integral, CTOD) or net-section yield are needed. In lifing questions, "$a_c$ could also be set by net-section yield or a deflection limit" is a good limitation to state.

## Typical values ($\mathrm{MPa\sqrt m}$)

| Material | $K_{Ic}$ |
|---|---:|
| Ceramics ($\mathrm{Al_2O_3}$, SiC) | 2.5-5 |
| 7xxx Al | 25-45 |
| Ti-6Al-4V | 55-75 |
| Structural and HSLA steels | 50-150 |
| Ni disc alloys | 90-125 |

## What raises toughness

Ductility (a plastic zone absorbs work), fine grains, clean steel (few brittle particles and no grain-boundary segregants), temperature above the DBT, slow loading. High strength usually **lowers** it.

Charpy energy ranks toughness but cannot be used in design, because it has no stress-defect relationship.
