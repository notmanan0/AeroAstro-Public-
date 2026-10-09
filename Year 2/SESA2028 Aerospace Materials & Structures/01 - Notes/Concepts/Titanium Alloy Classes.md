---
title: "Titanium Alloy Classes"
module: "SESA2028 Aerospace Materials & Structures"
type: concept
stream: "Materials"
tags: [sesa2028, materials, titanium, alloy-design, phase-transformations]
status: complete
parent: ["[[SESA2028 M6 - Light Alloys - Aluminium, Magnesium, Beryllium and Titanium]]"]
related: ["[[Precipitation Hardening]]", "[[Martensite]]", "[[Specific Stiffness and Strength]]"]
---

# Titanium Alloy Classes

Ti is HCP ($\alpha$) at low temperature and BCC ($\beta$) above the $\beta$-transus (about 882 °C for pure Ti). Alloying moves the transus:

- **$\alpha$ stabilisers** (raise it): **Al**, **O**, N, C, Ga, Ge.
- **$\beta$ stabilisers** (lower it): **V**, **Mo**, Nb, Ta, Fe, Cr, Mn, Co, Ni, Cu, Si.

Rapid cooling from $\beta$ can give **$\alpha'$ martensite**: diffusionless shear to a metastable HCP phase supersaturated in $\beta$ stabilisers. It is much less hard than steel martensite because it is not strengthened by trapped interstitial carbon. It is a fine metastable structure that is later aged or decomposed.

## The classes

| Class | Example | Phases and strengthening | Heat treatment | Key properties | Uses |
|---|---|---|---|---|---|
| CP Ti | Grade 1-4 (Ti-O) | $\alpha$; interstitial O solid solution | anneal | ductile, best corrosion, low strength (~414 MPa yield) | chemical and marine plant, shrouds, airframe skins |
| $\alpha$ | Ti-5Al-2.5Sn | $\alpha$; substitutional solid solution (Al, Sn) | anneal | **thermally stable (no precipitates), good creep**, weldable, poor formability | engine casings and rings to ~480 °C |
| Near-$\alpha$ | Ti-6242 | $\alpha$ + a little $\beta$ | thermomechanical + age | creep + strength | forged compressor discs and blades |
| $\alpha+\beta$ | **Ti-6Al-4V** | $\alpha$ + $\beta$ (+ $\alpha'$); microstructure set by heat treatment | anneal or STA | best all-round; tailorable fatigue | fan blades, airframe, implants |
| Metastable $\beta$ | Ti-10V-2Fe-3Al | $\beta$ + fine $\alpha$ precipitates | **solution treat + quench + age** | **highest strength** (~1150 MPa yield), formable in the solution-treated BCC state; 7-10 % denser, segregation-prone, not thermally stable | high-strength airframe forgings, landing gear |

## Ti-6Al-4V microstructures and fatigue

- **Slow cool from $\beta$**: $\alpha$ laths in a **basket-weave** pattern. The crack path is tortuous, so it **resists crack growth** and is tough and damage tolerant.
- **Anneal in the $\alpha+\beta$ field**: **equiaxed $\alpha$** + transformed $\beta$. Fine grains confine slip, so it **resists initiation** (best HCF).
- A bimodal structure combines both. That is why $\alpha+\beta$ alloys offer the **best fatigue resistance**: the microstructure can be tuned for both initiation and propagation.

## Choosing a matrix for a 550 °C MMC blade (2022-23 MQ2(ii))

**Ti-5Al-2.5Sn** or near-$\alpha$ ($\alpha$ alloys are thermally stable, with good creep and oxidation resistance at 550 °C). The fibres supply the strength, so the matrix mainly needs temperature stability and compatibility. Ti-6Al-4V is the practical alternative but loses creep strength above about 400-450 °C. $\beta$ alloys are unstable at temperature (their precipitates coarsen).
