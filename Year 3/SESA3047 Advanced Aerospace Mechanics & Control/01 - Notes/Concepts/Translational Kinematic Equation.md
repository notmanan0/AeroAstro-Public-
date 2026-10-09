---
title: "Translational Kinematic Equation"
module: "SESA3047 Advanced Aerospace Mechanics & Control"
type: concept
stream: "Chapter 3: Kinematic Equations and Introduction to Dynamics"
aliases: ["position state equation", "navigation equation", "body velocity to NED velocity"]
tags: [sesa3047, concept, kinematics, navigation]
status: complete
parent_lectures: ["[[SESA3047 3.2 - Translational Kinematics and Accelerations in Moving Frames]]"]
related_concepts: ["[[Direction Cosine Matrix]]", "[[NED and FRD Coordinates]]", "[[Rotational Kinematic Equation]]", "[[Coriolis and Centripetal Acceleration]]"]
sources: ["02 - Sources/Lectures/Chapter-3.pdf"]
---

# Translational Kinematic Equation

## Statement

> [!note] Definition
> For the centre-of-mass position $\mathbf p^{NED}_{cm/Q}=[x,y,z]^T$ (north, east, down from the local origin $Q$) and the Earth-relative velocity in body axes $\mathbf v^{FRD}_{cm/e}=[u,v,w]^T$, on a flat Earth:
>
> $${}^e\dot{\mathbf p}^{NED}_{cm/Q}=\mathbf C^T_{FRD/NED}\,\mathbf v^{FRD}_{cm/e}\qquad(3.39)$$

## Why it has this form

1. Position on a map is naturally in **NED**; its Earth-frame derivative is the NED velocity (3.36).
2. The velocity is carried in **FRD**, because aerodynamic and thrust forces are simplest there (3.37).
3. Convert FRD to NED with the inverse DCM, which is the transpose (3.38). The columns of $\mathbf C^T$ are the body axes written in NED.

Full matrix (3.40) and worked example: [[SESA3047 3.2 - Translational Kinematics and Accelerations in Moving Frames#5. The position state equation (§3.2.3, Eqs. 3.35–3.40)|3.2 §5]].

## Key points

- **Rotate first, then integrate.** Integrating $u,v,w$ directly is wrong as soon as the aircraft turns: constant $u$ with a constant yaw rate is a circle, not a straight line.
- **Purely kinematic**; the attitude enters only through $\mathbf C(\phi,\theta,\psi)$, which comes from the [[Rotational Kinematic Equation]].
- Climb rate is $-\dot z$, because NED $z$ points **down**.
- Wings level ($\phi=0$): $\dot z=-u\sin\theta+w\cos\theta$, so the flight-path angle is $\gamma=\theta-\alpha$.

## Example

$\psi=60^\circ$, $\theta=10^\circ$, $\phi=0$, $[u,v,w]=[150,0,5]$ m/s gives $[\dot x,\dot y,\dot z]=[74.3,\ 128.7,\ -21.1]$ m/s: a 21 m/s climb on a 060° track, $\gamma=8.09^\circ$.

## Related

- [[Direction Cosine Matrix]] · [[NED and FRD Coordinates]] · [[Flat-Earth Model]]
- [[Rotational Kinematic Equation]] · [[Rotational Dynamic Equation]] · [[Coriolis and Centripetal Acceleration]]
