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

**NED** is a local right-handed system fixed to the tangent plane, with $x$ pointing north, $y$ east and $z$ down. It's the natural choice for local position, ground-relative velocity and gravity, which is simply

$$
\mathbf g^{NED}=\begin{bmatrix}0\\0\\g\end{bmatrix}.
$$

**FRD** is a right-handed system fixed to the vehicle, with $x$ forward, $y$ to the right and $z$ down. It's the natural choice for aerodynamic and propulsive forces, body-velocity components and angular velocity. The vehicle's attitude is the orientation of FRD relative to NED.

East-North-Up (ENU, used in robotics and GIS) and Forward-Left-Up (FLU, used in ROS) are different axis conventions, not other names for NED and FRD; gravity in ENU is $[0,0,-g]^T$. SESA2027 and Cook call FRD the body axes and NED the Earth axes.

## Related

- [[Reference Frames and Coordinate Systems]] · [[Flat-Earth Model]]
