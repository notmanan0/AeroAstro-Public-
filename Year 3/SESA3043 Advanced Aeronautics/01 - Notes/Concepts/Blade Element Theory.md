---
title: "Blade Element Theory"
module: "SESA3043 Advanced Aeronautics"
type: concept
stream: "Chapter 4: Rotor Aerodynamics"
aliases: ["BET", "blade element method", "blade-element theory", "rotor torque", "profile power", "collective pitch", "inflow angle", "rotor solidity"]
tags: [sesa3043, concept, rotor, hover, blade-element]
status: complete
parent_lectures: ["[[SESA3043 4.1 - Rotor in Hover]]"]
related_concepts: ["[[Rotor Thrust and Power Coefficients]]", "[[Figure of Merit]]", "[[Blade Twist and Annulus Theory]]", "[[Hover Induced Velocity and Disc Loading]]"]
sources: ["02 - Sources/Lectures/CH4 Rotor Aerodynamics.pdf"]
---

# Blade Element Theory

Blade element theory (BET) divides each rotor blade into spanwise segments, treats each as a 2-D aerofoil section in the local relative flow, and sums the lift and drag of all segments on all blades to give the rotor thrust, torque and power.

A segment of span $\mathrm dr$ at radius $r$ meets the air at $U_T=r\Omega$ in the plane of rotation and $U_P=v_i$ down through it, so the inflow angle is $\phi=\tan^{-1}(v_i/r\Omega)$ and the angle of attack is $\alpha=\theta-\phi$, where $\theta$ is the blade pitch. Lift is tilted back by $\phi$, so $\mathrm dT=\mathrm dL\cos\phi-\mathrm dD\sin\phi$ and the in-plane force is $\mathrm d\hat H=\mathrm dL\sin\phi+\mathrm dD\cos\phi$, giving torque $\mathrm dQ=r\,\mathrm d\hat H$. With small $\phi$ (true except near the root), $C_L=a\alpha$, constant chord, blades to the centre, collective pitch $\theta_0$ and uniform $v_i$, the integrals give ([[SESA3043 4.1 - Rotor in Hover#10. Blade element theory|4.1 §10]])

$$
T=\tfrac12\rho V_T^2NcRa\left(\frac{\theta_0}{3}-\frac{\lambda_i}{2}\right),\qquad P=Q\Omega=Tv_i+\tfrac18\rho V_T^3NcRC_D.
$$

The first part of the power is exactly the momentum-theory induced power, recovered here from the tilt of the lift vector; the second is the profile power, set by the blade area $NcR$ rather than the disc area. In coefficient form, with the solidity $s=Nc/\pi R$, $C_T/sa=\theta_0/3-\lambda_i/2$ and $C_P=C_T\lambda_i+sC_{D0}/4$. Combining the BET thrust with the momentum result $\lambda_i=\sqrt{C_T}/2$ gives the collective pitch needed to hover: about $10^\circ$ for a Lynx-sized rotor with $s=0.08$.

BET captures what actuator disc theory cannot: blade number, aerofoil lift and drag, and twist. In its basic form it still assumes uniform downwash; [[Blade Twist and Annulus Theory]] relaxes that.

## Related

- Parent lecture: [[SESA3043 4.1 - Rotor in Hover]]
- Related concepts: [[Rotor Thrust and Power Coefficients]] · [[Figure of Merit]] · [[Blade Twist and Annulus Theory]] · [[Hover Induced Velocity and Disc Loading]] · [[Actuator Disk Theory]] (SESA2023, propeller blade elements)
