---
title: "SESA2028 S6 - Imperfect Columns, Beam-Columns and Plate Buckling"
module: "SESA2028 Aerospace Materials & Structures"
type: topic
stream: "Structures"
order: 6
tags: [sesa2028, structures, beam-column, plate-buckling]
status: complete
parent: ["[[SESA2028 Aerospace Materials & Structures Hub]]"]
prerequisites: ["[[SESA2028 S5 - Euler Buckling and Effective Length]]"]
next_topics: ["[[SESA2028 S7 - Strain Energy and Conservation of Energy]]"]
key_concepts: ["[[Secant Formula]]", "[[Beam-Column]]", "[[Plate Buckling]]"]
tutorial_sheets: ["[[SESA2028 Structures Tutorial 4 - Buckling Solutions]]"]
sources: ["02 - Sources/Structures Lectures/SL7 buckling of beams with imperfection.pdf", "02 - Sources/Structures Lectures/SL12 Buckling 4 - Lateral Loading.pdf", "02 - Sources/Structures Lectures/SL13 Buckling 5 - Plate Buckling.pdf"]
---

# SESA2028 S6 - Imperfect Columns, Beam-Columns and Plate Buckling

> [!abstract] Summary
> Real columns bend before they reach the Euler load. Eccentricity, initial crookedness and transverse loading create a first-order moment which is amplified by the axial force. Plate buckling follows the same stability logic but selects both a longitudinal and a transverse half-wave pattern.

## 1. Eccentrically loaded pinned column

For a constant eccentricity $e$,

$$
EI v''+P(v+e)=0,\qquad \mu^2=\frac{P}{EI}.
$$

With $v(0)=v(L)=0$, the midspan deflection magnitude is

$$
v_{max}=e\left[\sec\left(\frac{\mu L}{2}\right)-1\right].
$$

The maximum moment is

$$
M_{max}=P(e+v_{max})=Pe\sec\left(\frac{\mu L}{2}\right),
$$

and the most compressed fibre reaches

$$
\sigma_{max}=-\frac PA-\frac{M_{max}c}{I}.
$$

This is the [[Secant Formula]]. The response becomes unbounded as $P\to P_E$.

![[Figures/structures_beam_column_amplification.png]]

## 2. Initially crooked column

For an initial imperfection

$$
v_0=a_0\sin\frac{\pi x}{L},
$$

the additional deflection has the same mode shape and the total maximum deflection is

$$
v_{tot,max}=\frac{a_0}{1-P/P_E}.
$$

The added displacement is $a_0[P/P_E]/[1-P/P_E]$. The precise factor differs from the secant formula because the assumed imperfection shape differs from a constant eccentricity, but both show the same instability as $P/P_E\to1$.

## 3. Column with lateral loading

The beam-column equation is

$$
EI v''+Pv=M_0(x),
$$

where $M_0$ is the first-order bending moment from transverse loads. The axial load magnifies curvature and moment. For a symmetric midspan point load $W$ on a pin-ended column,

$$
v_{max}=\frac{W}{2P}\left[\frac1\mu\tan\left(\frac{\mu L}{2}\right)-\frac L2\right],
$$

$$
M_{max}=\frac{W}{2\mu}\tan\left(\frac{\mu L}{2}\right).
$$

The no-axial-load limit of the first expression is $WL^3/(48EI)$, which is an essential check.

## 4. Plate buckling

For a simply supported rectangular plate of dimensions $a\times b$ under uniform compression in the $a$ direction,

$$
N_{x,cr}=k\frac{\pi^2D}{b^2},\qquad
D=\frac{Et^3}{12(1-\nu^2)},
$$

with

$$
k=\left(\frac{m}{a/b}+\frac{a/b}{m}\right)^2
$$

for one transverse half-wave and integer $m$ longitudinal half-waves. The plate chooses the integer $m$ giving the lowest $k$.

![[Figures/structures_plate_buckling_mode_envelope.png]]

## 5. Column versus plate buckling

| Column | Plate |
|---|---|
| one centreline displacement | two-dimensional deflection field $w(x,y)$ |
| stiffness $EI$ | flexural rigidity $D$ |
| end restraint enters through $K$ | edge restraint enters through $k$ |
| global mode | local panel mode possible within an otherwise straight member |

## 6. Design message

Keeping $P/P_E$ modest is more important than merely staying below one. Near the Euler load, small uncertainties in eccentricity, initial curvature, modulus or restraint create large changes in stress and deflection.

## Year 1 foundation
- [[FEEG1002 A7 - Euler Buckling of Struts]]: the ideal (perfectly straight) Euler strut that imperfection and eccentricity analyses start from.
