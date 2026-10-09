---
title: "Shrink Fit"
module: "SESA2028 Aerospace Materials & Structures"
type: concept
stream: "Structures"
tags: [sesa2028, structures, shrink-fit]
status: complete
parent: ["[[SESA2028 S10 - Thick Cylinders and Shrink Fits]]"]
---

# Shrink Fit

**What it is:** an outer tube whose bore (radius $c-\delta_o$) is slightly smaller than the outside radius of an inner tube (radius $c+\delta_i$) is heated, slid on and allowed to cool. The **radial interference** $\delta=\delta_i+\delta_o$ is taken up elastically, and a **contact pressure** $p$ develops at $r=c$.

## Compatibility

The interference equals the outward displacement of the outer bore minus the (negative) displacement of the inner surface:

$$
\delta=u_{outer}(c)-u_{inner}(c),\qquad u=\frac cE(\sigma_\theta-\nu\sigma_r-\nu\sigma_z).
$$

Using Lamé at $r=c$, with inner tube $a\to c$ and outer tube $c\to b$:

$$
\sigma_{\theta,inner}(c)=-p\,\frac{c^2+a^2}{c^2-a^2},\qquad
\sigma_{\theta,outer}(c)=+p\,\frac{b^2+c^2}{b^2-c^2}.
$$

For **identical materials** the $\nu$ terms cancel (both sides have $\sigma_r=-p$), giving

$$
\boxed{\delta=\frac{pc}{E}\left[\frac{b^2+c^2}{b^2-c^2}+\frac{c^2+a^2}{c^2-a^2}\right]=\frac{2pc^3(b^2-a^2)}{E(c^2-a^2)(b^2-c^2)}.}
$$

For **different materials**, keep separate $E$ and $\nu$ for each tube (the $\nu p$ terms no longer cancel).

## Worked check (2014-15 A2)

$a=25$, $c=50$, $b=75$ mm, $\delta=0.01$ mm, $E=208$ GPa. Then $\delta=1.0256\times10^{-3}\,p$, so $p=9.75$ MPa. See [[FEEG2005 Exam 2014-15 Solutions]].

## Traps

- Is $\delta$ given on the **radius** or the **diameter**? Diametral interference is $2\delta$.
- The inner tube may be **solid** (a shaft on a hub): then $a=0$ and $\sigma_{\theta,inner}=-p$ everywhere in the shaft.
- The result is residual **compression in the inner tube** and **tension in the outer tube**. Superpose the service loads afterwards ([[Shrink Fit Superposition]]).

**Related (SESA2028 materials):** [[Shot Peening]] (plastically induced residual stress, same self-equilibrium idea)
