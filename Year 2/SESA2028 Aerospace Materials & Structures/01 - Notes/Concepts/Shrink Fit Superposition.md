---
title: "Shrink Fit Superposition"
module: "SESA2028 Aerospace Materials & Structures"
type: concept
tags: [sesa2028, structures, shrink-fit]
status: complete
---

# Shrink Fit Superposition

A shrink fit creates a contact pressure before service loading. It puts the inner cylinder into hoop compression and the outer cylinder into hoop tension.

Find the contact pressure from radial-displacement compatibility at the junction. Then solve two Lamé problems:

1. inner tube under external pressure;
2. outer tube under internal pressure.

The resulting hoop stress jumps at the interface because the two materials occupy different sides of a traction boundary; radial stress remains continuous and equals the negative contact pressure.

Service pressure can then be superposed while the response remains elastic and the interface remains in contact.

![Shrink-fit residual stress](../Figures/structures_shrink_fit_residual_stress.png)

The design purpose is to replace dangerous tensile bore stress with beneficial residual compression.

See [[SESA2028 S10 - Thick Cylinders and Shrink Fits]].

