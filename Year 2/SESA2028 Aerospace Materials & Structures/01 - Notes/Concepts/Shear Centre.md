---
title: "Shear Centre"
module: "SESA2028 Aerospace Materials & Structures"
type: concept
tags: [sesa2028, structures, shear-centre]
status: complete
---

# Shear Centre

The shear centre is the point through which a transverse force must act to produce bending without twist. It is a property of the section, not of the applied load magnitude.

Find the wall flow created by a convenient shear $V$, calculate its torque about a reference point O, and locate S from

$$
Ve=\int q(s)[y\,dz-z\,dy].
$$

Symmetry rules save time:

- one symmetry axis → S lies on it;
- two symmetry axes → S is the centroid;
- point symmetry can also force S to the centroid even when $I_{yz}\ne0$.

For open channels, S often lies outside the material. That is a physical result, not a warning sign.

If a force acts a distance $e$ away from S, analyse it as a force through S plus a torque $T=Ve$.

See [[SESA2028 S3 - Shear Flow and Shear Centre]].

