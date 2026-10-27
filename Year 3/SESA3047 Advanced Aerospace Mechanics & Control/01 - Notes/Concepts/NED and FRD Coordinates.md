---
title: "NED and FRD Coordinates"
module: "SESA3047 Advanced Aerospace Mechanics & Control"
type: concept
stream: "Chapter 1: Fundamental Concepts"
aliases: ["North-East-Down", "Forward-Right-Down", "body axes", "body-fixed axes", "Earth axes", "local-level frame", "local tangent-plane frame", "navigation frame"]
tags: [sesa3047, concept, coordinates]
status: complete
parent_lectures: ["[[SESA3047 1.2 - Dynamic Models, Frames and Earth Models]]"]
related_concepts: ["[[Reference Frames and Coordinate Systems]]", "[[Flat-Earth Model]]"]
sources: ["02 - Sources/Lectures/Chapter 1.pdf", "02 - Sources/Lectures/L3 - SESA3047.txt"]
---

# NED and FRD Coordinates

## NED

Local right-handed coordinates fixed to the tangent plane:

- $x$: north;
- $y$: east;
- $z$: down.

Convenient for local position, ground-relative velocity and gravity:

$$
\mathbf g^{NED}=\begin{bmatrix}0\\0\\g\end{bmatrix}.
$$

## FRD

Right-handed coordinates fixed to the vehicle:

- $x$: forward;
- $y$: right;
- $z$: down.

Convenient for aerodynamic and propulsive forces, body-velocity components and angular velocity.

Vehicle attitude is the orientation of FRD relative to NED.

## Other conventions

East-North-Up (ENU, robotics and GIS) and Forward-Left-Up (FLU, ROS) are **different** axis conventions, not other names for NED and FRD: gravity is $[0,0,-g]^T$ in ENU. SESA2027 and Cook call FRD the body axes and NED the Earth axes.

## Related

- [[Reference Frames and Coordinate Systems]] · [[Flat-Earth Model]]

