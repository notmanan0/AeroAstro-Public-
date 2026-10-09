---
title: "Castigliano Second Theorem"
module: "SESA2028 Aerospace Materials & Structures"
type: concept
stream: "Structures"
tags: [sesa2028, structures, castigliano]
status: complete
parent: ["[[SESA2028 S8 - Virtual Work and Castigliano Theorems]]"]
---

# Castigliano Second Theorem

**Statement.** For a linearly elastic structure, the partial derivative of the strain energy $U$ (written in terms of the applied loads) with respect to a load $P_i$ equals the displacement at, and in the direction of, that load:

$$
\delta_i=\frac{\partial U}{\partial P_i},\qquad \theta_i=\frac{\partial U}{\partial M_i}.
$$

## Why it works (sketch)

Strictly, the theorem is $\delta_i=\partial U^*/\partial P_i$, where $U^*$ is the **complementary energy**. For a linear elastic structure $U^*=U$ ([[Complementary Energy]]), so the strain energy can be used directly. Physically: add a small $dP_i$. The extra external work is $\delta_i\,dP_i$ (to first order), and that must equal the increase in stored energy, $dU$.

## Bending form

$$
\delta_i=\int\frac{M}{EI}\frac{\partial M}{\partial P_i}\,dx
\quad(+\text{axial and torsion terms}).
$$

Differentiate **under the integral before integrating**; it is much less work.

## Worked example: cantilever tip deflection

Cantilever of length $L$, tip load $P$, with $x$ measured from the tip. $M=-Px$ and $\partial M/\partial P=-x$:

$$
\delta_{tip}=\int_0^L\frac{(-Px)(-x)}{EI}dx=\frac{PL^3}{3EI}.
$$

**Dummy load:** for the slope at the tip, add a tip moment $M_0$. Then $M=-Px-M_0$ and $\partial M/\partial M_0=-1$:

$$
\theta_{tip}=\int_0^L\frac{(-Px-M_0)(-1)}{EI}dx\Big|_{M_0=0}=\frac{PL^2}{2EI}.
$$

Set the dummy load to zero **only after differentiating**.

The practical use of the theorem is in [[Castigliano Theorem]].
