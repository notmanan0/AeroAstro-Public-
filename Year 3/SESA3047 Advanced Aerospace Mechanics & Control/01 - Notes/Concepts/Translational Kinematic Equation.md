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
sources: ["02 - Sources/Lectures/Chapter-3.pdf", "02 - Sources/Lectures/L8 - SESA3047.txt", "02 - Sources/Lectures/L9 - SESA3047.txt"]
---

# Translational Kinematic Equation

On a flat Earth, the centre-of-mass position $\mathbf p^{NED}_{cm/Q}=[x,y,z]^T$ (north, east and down from the local origin $Q$) evolves from the Earth-relative velocity in body axes $\mathbf v^{FRD}_{cm/e}=[u,v,w]^T$ as

$${}^e\dot{\mathbf p}^{NED}_{cm/Q}=\mathbf C^T_{FRD/NED}\,\mathbf v^{FRD}_{cm/e}\qquad(3.39)$$

Position on a map is naturally expressed in NED, and its Earth-frame derivative is the NED velocity (3.36). But the velocity is carried in FRD, because that's where aerodynamic and thrust forces are simplest (3.37). So the velocity has to be converted from FRD to NED with the inverse DCM, which is its transpose (3.38); the columns of $\mathbf C^T$ are the body axes written in NED. The full matrix form (3.40) and a worked example are in [[SESA3047 3.2 - Translational Kinematics and Accelerations in Moving Frames#5. The position state equation (§3.2.3, Eqs. 3.35–3.40)|3.2 §5]].

The order matters: rotate first, then integrate. Integrating $u,v,w$ directly goes wrong as soon as the aircraft turns, since constant $u$ with a constant yaw rate traces a circle, not a straight line. The equation is purely kinematic; the attitude only enters through $\mathbf C(\phi,\theta,\psi)$, which comes from the [[Rotational Kinematic Equation]]. Because NED $z$ points down, the climb rate is $-\dot z$. Wings level ($\phi=0$), $\dot z=-u\sin\theta+w\cos\theta$, so the flight-path angle is $\gamma=\theta-\alpha$.

For example, $\psi=60^\circ$, $\theta=10^\circ$, $\phi=0$ and $[u,v,w]=[150,0,5]$ m/s give $[\dot x,\dot y,\dot z]=[74.3,\ 128.7,\ -21.1]$ m/s: a 21 m/s climb on a 060° track, with $\gamma=8.09^\circ$.

## Related

- [[Direction Cosine Matrix]] · [[NED and FRD Coordinates]] · [[Flat-Earth Model]]
- [[Rotational Kinematic Equation]] · [[Rotational Dynamic Equation]] · [[Coriolis and Centripetal Acceleration]]
