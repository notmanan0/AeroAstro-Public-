---
title: "Thermal Barrier Coatings"
module: "SESA2028 Aerospace Materials & Structures"
type: concept
stream: "Materials"
tags: [sesa2028, materials, coatings, turbine-blade, high-temperature]
status: complete
parent: ["[[SESA2028 M8 - High Temperature Materials - Creep, Oxidation and Superalloys]]"]
related: ["[[Single Crystal Casting]]", "[[Oxidation Rate Laws]]", "[[Gamma Prime Strengthening]]", "[[Turbine Entry Temperature and Blade Cooling]]"]
---

# Thermal Barrier Coatings

A thermal barrier coating (TBC) is a low-conductivity ceramic layer on an internally cooled superalloy part. It produces a **large temperature drop** across the coating (about 100-150 °C). The metal then runs cooler, which slows creep and oxidation, or the gas can run hotter for better efficiency.

## The stack (from substrate outwards)

1. **Substrate**: a single-crystal Ni superalloy with internal cooling-air passages.
2. **Bond coat**: an intermetallic (Pt-)aluminide, deposited by CVD or pack aluminising, or an MCrAlY overlay. It supplies Al for the protective oxide and **grades the thermal-expansion mismatch** between metal and ceramic.
3. **Thermally grown oxide (TGO)**: a thin $\mathrm{Al_2O_3}$ layer grown on the bond coat in service. This is the real oxidation barrier. When it thickens too much it causes spallation.
4. **Top coat**: yttria-stabilised zirconia (YSZ), 100-400 µm. It has very low thermal conductivity and relatively high thermal expansion for a ceramic.
   - **EB-PVD**: columnar grains give **strain tolerance** for thermal cycling (aerofoils).
   - **APS / HVOF**: splat structure, cheaper, used for combustors and platforms. Line of sight only.

## Why it works with cooling

Heat flows from the hot gas, through the YSZ (large temperature drop), through the metal wall, into the cooling air. See [[Turbine Entry Temperature and Blade Cooling]] (SESA2023).

## Failure modes

TGO growth plus thermal-expansion mismatch on thermal cycling cause spallation. Also erosion, foreign-object damage, and CMAS (molten sand) attack.

## Exam phrasing

"What coatings would you use to reduce the temperature experienced by the alloy?" (2013-14 B3(v), 2014-15 B3(v)): **a YSZ TBC over an aluminide or MCrAlY bond coat**, with film cooling.
