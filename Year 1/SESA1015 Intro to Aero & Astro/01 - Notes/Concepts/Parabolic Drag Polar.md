---
title: "Parabolic Drag Polar"
module: "SESA1015 Intro to Aero & Astro"
type: concept
tags: [sesa1015, drag-polar, induced-drag]
aliases: ["Drag Polar", "C_D = C_D0 + k C_L^2"]
date: 2026-09-27
status: complete
parent: ["[[SESA1015 M03 - Aerodynamic Characteristics and the Drag Polar]]"]
sources: ["02 - Sources/Mechanics of Flight/Mechanics of Flight - Course Notes.pdf"]
---

# Parabolic Drag Polar

$$\boxed{C_D=C_{D0}+kC_L^2},\qquad k\approx\frac{1}{\pi eAR}.$$

$C_{D0}$ represents parasite/zero-lift drag; $kC_L^2$ represents lift-dependent induced drag.

Plot $C_D$ against $C_L^2$ to obtain a straight line:

- intercept $=C_{D0}$;
- slope $=k$.

Maximum lift-to-drag ratio occurs when

$$C_{D0}=kC_L^2.$$

Thus

$$C_{L,MD}=\sqrt{\frac{C_{D0}}k},\qquad \left(\frac LD\right)_{max}=\frac{1}{2\sqrt{kC_{D0}}}.$$

> [!warning] Model envelope
> The polar is configuration- and condition-specific. It is least reliable near stall and when compressibility or configuration change becomes important.

See [[Downwash and Induced Drag]] for the finite-wing origin of $k$.

