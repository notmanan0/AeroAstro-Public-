---
title: "Stress Transformation Equations"
module: "FEEG1002 Mechanics, Materials and Structures"
type: concept
stream: "Part B: Statics 2"
aliases: ["plane stress transformation", "stress on an inclined plane", "strain transformation", "transformation equations"]
tags: [feeg1002, concept, statics-2, stress-transformation]
status: complete
parent_lectures: ["[[FEEG1002 B4 - Stress Transformation and Mohr's Circle]]", "[[FEEG1002 B5 - Strain Measurement and Strain Rosettes]]"]
related_concepts: ["[[Mohr's Circle]]", "[[Principal Stresses]]", "[[Stress Tensor and Stress Element]]", "[[Strain Gauge Rosettes]]"]
sources: ["02 - Sources/Statics 2/Lectures/Lecture 05 - Stresses on Inclined Sections and Stress Transformation.pdf", "02 - Sources/Statics 2/Lectures/Lecture 07 - Strain Measurement.pdf"]
---

# Stress Transformation Equations

The stress transformation equations give the normal and shear stresses on an element rotated anticlockwise by $\theta$ from the $xy$ axes, in terms of $\sigma_{xx}$, $\sigma_{yy}$ and $\sigma_{xy}$:

$$
\sigma_{x'x'}=\sigma_{xx}\cos^2\theta+\sigma_{yy}\sin^2\theta+2\sigma_{xy}\sin\theta\cos\theta
$$

$$
\sigma_{x'y'}=-(\sigma_{xx}-\sigma_{yy})\sin\theta\cos\theta+\sigma_{xy}\left(\cos^2\theta-\sin^2\theta\right)
$$

They come from force equilibrium of a wedge whose faces have areas $A$, $A\tan\theta$ and $A/\cos\theta$, resolving forces along and across the inclined face. Each new stress depends on all three old ones; one factor of the angle comes from resolving forces and the other from the change of area, which is why no stress transforms by a single cosine. No material law is involved, so the equations hold for any material, and since $\sigma_{zz}$ does not enter the in-plane equilibrium they hold for plane strain as well as plane stress. The normal stress on the other face follows from $\theta+90^\circ$, and $\sigma_{x'x'}+\sigma_{y'y'}=\sigma_{xx}+\sigma_{yy}$ for every $\theta$.

With double-angle identities the equations become $\sigma_{x'x'}=\sigma_{average}+\frac{\sigma_{xx}-\sigma_{yy}}{2}\cos2\theta+\sigma_{xy}\sin2\theta$ and $\sigma_{x'y'}=-\frac{\sigma_{xx}-\sigma_{yy}}{2}\sin2\theta+\sigma_{xy}\cos2\theta$, and eliminating $2\theta$ gives [[Mohr's Circle]]. Since $d\sigma_{x'x'}/d\theta=2\sigma_{x'y'}$, the normal stress is largest and smallest exactly where the shear stress is zero, at the [[Principal Stresses]].

For a bar in tension the equations reduce to $\sigma_{x'x'}=\sigma_{xx}\cos^2\theta$ and $\sigma_{x'y'}=-\sigma_{xx}\sin\theta\cos\theta$, so the shear stress peaks at $\sigma_{xx}/2$ on planes at 45°. Strains transform by the same equations with the tensor shear strain $\varepsilon_{xy}=\gamma_{xy}/2$ in place of $\sigma_{xy}$; this follows from the geometry of a stretched line element and is the basis of strain gauge rosettes. In practice the hard part is the angle: $\theta$ is measured from $x$ to the normal of the surface of interest, not to the surface itself.

![[s2_wedge_equilibrium.png|800]]

## Related

- [[FEEG1002 B4 - Stress Transformation and Mohr's Circle#2. Plane-stress transformation|wedge derivation in B4]] · [[FEEG1002 B4 - Stress Transformation and Mohr's Circle#1. Stresses on an inclined section of a bar|inclined section of a bar]] · [[FEEG1002 B4 - Stress Transformation and Mohr's Circle#Worked example - helical weld in a pressure vessel|helical weld]] · [[FEEG1002 B5 - Strain Measurement and Strain Rosettes#3. Strain transformation|strain transformation in B5]]
- [[Mohr's Circle]] · [[Principal Stresses]] · [[Stress Tensor and Stress Element]] · [[Strain Gauge Rosettes]]
- Year 2: the same algebra for second moments of area in [[Principal Axes of a Section]] · tensor rotation as in [[Euler Angles and Rotation Matrices]]
