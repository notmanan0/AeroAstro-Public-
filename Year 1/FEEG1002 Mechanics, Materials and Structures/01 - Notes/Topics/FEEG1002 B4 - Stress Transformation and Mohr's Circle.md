---
title: "FEEG1002 B4 - Stress Transformation and Mohr's Circle"
module: "FEEG1002 Mechanics, Materials and Structures"
type: topic
stream: "Part B: Statics 2"
order: 13
tags: [feeg1002, statics-2, stress-transformation, mohrs-circle, principal-stresses]
aliases: ["Statics 2 Lecture 5", "Statics 2 Lecture 6", "Stress transformation", "Mohr's circle", "Principal stresses"]
date: 2026-09-25
status: complete
parent: ["[[FEEG1002 Mechanics, Materials and Structures Hub]]"]
prerequisites: ["[[FEEG1002 B1 - Stress in Multiple Dimensions and Thin-Walled Pressure Vessels]]"]
next_topics: ["[[FEEG1002 B5 - Strain Measurement and Strain Rosettes]]"]
key_concepts: ["[[Stress Transformation Equations]]", "[[Mohr's Circle]]", "[[Principal Stresses]]"]
tutorial_sheets: ["[[FEEG1002 Statics 2 Tutorial 4 - Stresses on Inclined Sections and Stress Transformation Solutions]]", "[[FEEG1002 Statics 2 Tutorial 5 - Mohr's Circle Solutions]]"]
sources: ["02 - Sources/Statics 2/Lectures/Lecture 05 - Stresses on Inclined Sections and Stress Transformation.pdf", "02 - Sources/Statics 2/Lectures/Lecture 06 - Mohr's Circle.pdf"]
---

# FEEG1002 B4 - Stress Transformation and Mohr's Circle

> [!abstract] Summary
> One stress state looks different on differently oriented planes. Equilibrium of a wedge gives the **transformation equations**:
>
> $$\sigma_{x'x'} = \frac{\sigma_{xx}+\sigma_{yy}}{2} + \frac{\sigma_{xx}-\sigma_{yy}}{2}\cos2\theta + \sigma_{xy}\sin2\theta,\qquad \sigma_{x'y'} = -\frac{\sigma_{xx}-\sigma_{yy}}{2}\sin2\theta + \sigma_{xy}\cos2\theta$$
>
> Eliminating $2\theta$ gives a **circle** in the ($\sigma$, $\tau$) plane, **Mohr's circle**, with centre $\sigma_{avg}$ and radius $R$. It shows at a glance:
> - the **principal stresses** $\sigma_{I,II} = \sigma_{avg}\pm R$, on planes with zero shear, 90° apart;
> - the **maximum in-plane shear** $R$, at 45° to the principal planes.

## Key Concepts
- [[Stress Transformation Equations]] · [[Mohr's Circle]] · [[Principal Stresses]]

---

## 1. A bar in tension, cut obliquely (L5a)
- Cut at angle $\theta$: the same force $F$ acts on the larger area $A/\cos\theta$.
- Split it into normal $F\cos\theta$ and shear $F\sin\theta$:

$$\sigma_{x'x'} = \sigma_{xx}\cos^2\theta,\qquad \sigma_{x'y'} = -\sigma_{xx}\sin\theta\cos\theta$$

  The minus sign comes from the positive-shear convention.
- The normal stress peaks on the cross-section ($\theta = 0$). The **shear peaks at ±45°**, with value $\sigma_{xx}/2$.
- So even a purely tensile load can fail in **shear**, if the shear strength is less than half the tensile strength:
  - ductile metals slip on 45° planes;
  - a **scarf** or finger joint loads the glue in shear over a larger area than a butt joint.

![[s2_inclined_section_uniaxial.png|640]]

## 2. General plane-stress transformation (L5b)
Force balance on a wedge with faces $A$, $A\tan\theta$ and $A/\cos\theta$ gives, with $\theta$ positive **anticlockwise**:

$$
\sigma_{x'x'} = \sigma_{xx}\cos^2\theta + \sigma_{yy}\sin^2\theta + 2\sigma_{xy}\sin\theta\cos\theta
$$

$$
\sigma_{x'y'} = -(\sigma_{xx}-\sigma_{yy})\sin\theta\cos\theta + \sigma_{xy}(\cos^2\theta - \sin^2\theta)
$$

- $\sigma_{y'y'}$ follows by replacing $\theta$ with $\theta + 90^\circ$.
- $\sigma_{x'x'} + \sigma_{y'y'} = \sigma_{xx} + \sigma_{yy}$ is **invariant**: it does not depend on orientation.
- The same equations hold in **plane strain**, because $\sigma_{zz}$ does not enter the in-plane equilibrium.
- Uses:
  - normal and shear stress on a weld or glue line;
  - resolved shear stress on a crystal slip plane ([[FEEG1002 C4 - Mechanical Properties, Dislocations and Plastic Deformation]]);
  - stress along the grain of wood or the fibres of a composite.

> [!example] Tutorial 4: helical weld at 60° to the axis of a pressure vessel ($D = 1.2$ m, $t = 7$ mm, $p = 2$ MPa)
> - $\sigma_{xx} = pR/2t = 85.7$ MPa and $\sigma_{yy} = 171.4$ MPa.
> - The weld plane's normal is at $\theta = 90 - 60 = 30^\circ$ to the axis.
> - Normal stress: $\sigma_n = 85.7\cos^230^\circ + 171.4\sin^230^\circ = 107$ MPa.
> - Shear stress: $\tau = (171.4 - 85.7)\sin30^\circ\cos30^\circ = 37.1$ MPa.

## 3. Mohr's circle (L6a)
Using double-angle identities and eliminating $2\theta$:

$$
\left(\sigma_{x'x'} - \sigma_{avg}\right)^2 + \sigma_{x'y'}^2 = R^2,\qquad \sigma_{avg} = \frac{\sigma_{xx}+\sigma_{yy}}{2},\qquad R = \sqrt{\left(\frac{\sigma_{xx}-\sigma_{yy}}{2}\right)^2 + \sigma_{xy}^2}
$$

**Construction (FEEG1002 convention):**
1. Normal stress to the right; **shear stress positive DOWNWARDS**. With this choice, rotating the element by $\theta$ corresponds to rotating by $2\theta$ **in the same sense** on the circle.
2. Mark $\sigma_{xx}$ and $\sigma_{yy}$ on the horizontal axis. The centre $\sigma_{avg}$ is midway between them.
3. Plot the $x$-face point $(\sigma_{xx}, \sigma_{xy})$; this is $\theta = 0$. The $y$-face point $(\sigma_{yy}, -\sigma_{xy})$ is diametrically opposite.
4. Draw the circle through them.

## 4. Principal stresses and maximum shear (L6b)
- The circle always cuts the horizontal axis twice: two perpendicular orientations with **zero shear**, the **principal directions**.

$$
\sigma_I = \sigma_{avg} + R,\qquad \sigma_{II} = \sigma_{avg} - R,\qquad \tan2\theta_p = \frac{2\sigma_{xy}}{\sigma_{xx}-\sigma_{yy}}
$$

- **Maximum in-plane shear** $= R = (\sigma_I - \sigma_{II})/2$. It occurs at the top and bottom of the circle, 45° from the principal axes, where the normal stress is $\sigma_{avg}$ on **both** faces.
- Special circles:
  - **uniaxial**: the circle passes through the origin, and $\tau_{max} = \sigma/2$ at 45°;
  - **pure shear** (torsion): centred on the origin, so $\sigma_{I,II} = \pm\tau$ at 45°. That explains the helical fracture of chalk in torsion;
  - **equibiaxial** ($\sigma_{xx} = \sigma_{yy}$, $\sigma_{xy} = 0$): the circle shrinks to a point, with no shear on any plane. This is the spherical vessel.

![[s2_mohr_t5_sail.png|940]]

![[s2_mohr_pure_shear.png|940]]

> [!warning] Two double-angle traps
> - An angle on the circle is **twice** the physical angle. The $x$ and $y$ faces, 90° apart physically, are 180° apart on the circle.
> - Get the sign of $\sigma_{xy}$ from the **element**: a shear arrow pointing in $-x$ on a face with a $+y$ normal means $\sigma_{xy} < 0$. In the sail (Tutorial 5) $\sigma_{xy} = -1$ MPa, so the $x$-face point sits **above** the axis and the principal rotation is **clockwise**, $\theta_p = -16.8^\circ$.

## 5. 3D note
In 3D there are three principal stresses and three Mohr's circles. The absolute maximum shear is $\tfrac12\max|\sigma_i - \sigma_j|$. In plane stress one principal stress is $\sigma_{III} = 0$, which matters for the Tresca criterion ([[FEEG1002 B6 - Yield Criteria]]).

## Year 2 bridge
- **Principal axes of a section**: [[SESA2028 S1 - Section Properties and Unsymmetrical Bending]] uses the *same* transformation, and the same Mohr's circle, for $I_{yy}$, $I_{zz}$, $I_{yz}$ ([[Principal Axes of a Section]], [[Principal Second Moments of Area]]). Only the symbols change.
- **Principal stresses feed failure criteria**:
  - von Mises and Tresca ([[Von Mises and Tresca Yield Criteria]]), which every SESA2029 FE contour plot reports ([[SESA2029 B2 - Linear Elastic FE Analysis - Procedure, Boundary Conditions and Yield]]);
  - maximum principal stress for brittle materials and crack opening ([[Stress Intensity Factor]]).
- **Tensor rotation** generalises to $\boldsymbol\sigma' = \mathbf R\boldsymbol\sigma\mathbf R^T$. It is the same rotation-matrix algebra as aircraft axes in [[Euler Angles and Rotation Matrices]] ([[SESA2027 A1 - Dynamic Systems and Aircraft Equations of Motion]]).
- Principal directions are the **eigenvectors** of the stress tensor and principal stresses its **eigenvalues**. That is the same eigenproblem as modal analysis ([[Characteristic Equation and Eigenvalues]]).

## Links
- Previous: [[FEEG1002 B3 - Generalised Hooke's Law]] · Next: [[FEEG1002 B5 - Strain Measurement and Strain Rosettes]]
- Worked problems: [[FEEG1002 Statics 2 Tutorial 4 - Stresses on Inclined Sections and Stress Transformation Solutions]] · [[FEEG1002 Statics 2 Tutorial 5 - Mohr's Circle Solutions]] · [[FEEG1002 Statics 2 Tutorial 8 - Revision Problems Solutions]]

## Sources
- Statics 2 Lectures 5a–b (inclined sections; plane-stress transformation) and 6a–b (Mohr's circle; principal stresses)
