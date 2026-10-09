---
title: "Beam-Column"
module: "SESA2028 Aerospace Materials & Structures"
type: concept
stream: "Structures"
tags: [sesa2028, structures, buckling, beam-column]
status: complete
parent: ["[[SESA2028 S6 - Imperfect Columns, Beam-Columns and Plate Buckling]]"]
---

# Beam-Column

**What it is:** a member carrying axial compression $P$ **and** bending (transverse load, end moments or eccentricity). The axial load acts through the lateral deflection $v$, adding a **second-order moment** $Pv$ (the "P-delta" effect):

$$
M_{total}(x)=M_0(x)+Pv(x).
$$

Deflection increases the moment, which increases the deflection. Ordinary superposition of "column" and "beam" answers **underestimates** both.

## Governing equation

With $\mu^2=P/EI$ and the module's sign convention (as in the 2013-14 eccentric strut):

$$
EI\,v''+Pv=-M_0(x)\qquad\Longrightarrow\qquad v''+\mu^2v=-\frac{M_0}{EI}.
$$

General solution: $v=A\cos\mu x+B\sin\mu x+v_p(x)$. Find $A$ and $B$ from the end conditions.

## Eccentric load (pin-ended, eccentricity $e$)

Here $M_0=Pe$, so $v_p=-e$. With $v(0)=v(L)=0$:

$$
v_{max}=e\left[\sec\frac{\mu L}{2}-1\right],\qquad
M_{max}=Pe\sec\frac{\mu L}{2},
$$

which gives the [[Secant Formula]].

## Transverse load or initial crookedness

For a sinusoidal shape (or approximately for a UDL), the lateral deflection and moment are amplified by

$$
\frac{1}{1-P/P_E}
$$

([[Beam-Column Amplification]]).

## Exam checks

- Always compare $P$ with $P_E$ first. If $P\ge P_E$ the member is unstable, whatever the bending (2024-25 SQ2).
- Stress check: $\sigma_{max}=\dfrac PA+\dfrac{M_{max}c}{I}$ at the compression face.
- Use the correct plane: bending and buckling must be in the same plane for the amplification to apply.
