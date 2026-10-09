---
title: "Principal Axes of a Section"
module: "SESA2028 Aerospace Materials & Structures"
type: concept
stream: "Structures"
tags: [sesa2028, structures, section-properties]
status: complete
parent: ["[[SESA2028 S1 - Section Properties and Unsymmetrical Bending]]"]
---

# Principal Axes of a Section

**What they are:** the pair of perpendicular centroidal axes about which the **product of inertia vanishes**. Bending about either principal axis produces curvature *only* about that axis: no coupling.

## Rotating the axes

Let axes $y',z'$ be rotated by $\theta$ from $y,z$, measured from the $y$-axis towards the $z$-axis ($y'=y\cos\theta+z\sin\theta$, $z'=-y\sin\theta+z\cos\theta$). With $I_y=\int z^2dA$, $I_z=\int y^2dA$ and $I_{yz}=\int yz\,dA$:

$$
I_{y'}=\frac{I_y+I_z}{2}+\frac{I_y-I_z}{2}\cos2\theta-I_{yz}\sin2\theta,
$$

$$
I_{z'}=\frac{I_y+I_z}{2}-\frac{I_y-I_z}{2}\cos2\theta+I_{yz}\sin2\theta,
$$

$$
I_{y'z'}=\frac{I_y-I_z}{2}\sin2\theta+I_{yz}\cos2\theta.
$$

Setting $I_{y'z'}=0$:

$$
\tan2\theta_p=\frac{2I_{yz}}{I_z-I_y}\quad(\theta\text{ measured from }y\text{ towards }z).
$$

The formula sheet and S1 quote $\tan2\theta_p=2I_{yz}/(I_y-I_z)$. That is the same result with $\theta$ measured the **other way** (or $I_{yz}$ defined with the opposite sign). **Whichever form you use, substitute back and confirm $I_{y'z'}=0$**, and state your direction of rotation on the sketch.

## Which axis is which?

$\tan2\theta$ has two solutions $90^\circ$ apart in $\theta$. Evaluate $I_{y'}$ at your $\theta_p$: if it equals $I_{max}$, that axis is the major principal axis. Or use Mohr's circle ([[Principal Second Moments of Area]]).

## Shortcuts

- An axis of **symmetry** is always a principal axis ($I_{yz}=0$).
- Equal-leg angle: principal axes at $45^\circ$ to the legs.
- If $I_y=I_z$ and $I_{yz}=0$ (square, circle), **every** centroidal axis is principal.
