---
title: "SESA2028 Materials Tutorial MT2 - Fatigue Lifing Solutions"
module: "SESA2028 Aerospace Materials & Structures"
type: tutorial-solution
stream: "Materials"
tags: [sesa2028, materials, tutorial, fatigue, paris-law, miners-rule]
status: complete
parent: ["[[SESA2028 Aerospace Materials & Structures Hub]]"]
topics: ["[[SESA2028 M2 - Fatigue - Fracture Surfaces, Mechanisms and Lifing]]", "[[SESA2028 M1 - Fracture, Toughness and Fracture Mechanics]]"]
sources: ["02 - Sources/SESA2028 green coursework book.pdf (MT2, p.27)"]
---

# SESA2028 Materials Tutorial MT2 - Fatigue Lifing Solutions

> These are independent worked solutions, not an official mark scheme. Q4 reproduces the lecturer's own worked example. Q2 is identical to 2018-19 A2(i), Q3 to 2014-15 B1, and Q5 to 2016-17 A2(iv) (with a different $A$).

**Conventions used throughout** ([[Paris Law]]):

$$
\Delta\sigma=\sigma_{max}-\max(\sigma_{min},0),\qquad
a_c=\frac1\pi\left(\frac{K_{Ic}}{Q\sigma_{max}}\right)^2,\qquad
N_f=\frac{a_c^{\,1-m/2}-a_i^{\,1-m/2}}{(1-\frac m2)\,A\,(Q\Delta\sigma\sqrt\pi)^m}.
$$

---

## Q1 - Total life (Miner) vs Paris law [5 marks]

**Total-life approach using Miner's rule**

- Start from S-N (HCF, Basquin) or $\varepsilon$-N (LCF, Coffin-Manson) curves measured on smooth specimens. They give $N_i$, the life at each stress or strain level.
- Break the service history into blocks (rainflow counting). Block $i$ has $n_i$ cycles and uses the fraction $n_i/N_i$ of the life.
- Failure is predicted when $\sum n_i/N_i=1$.
- It predicts **initiation + growth** in a nominally defect-free component, and is dominated by initiation. So it is very sensitive to surface finish, mean stress (Goodman) and environment, and effectively **designs against crack initiation**.
- Assumes linear, sequence-independent damage.

**Damage-tolerant approach using the Paris law**

- **Assumes a crack already exists** (found by NDT, or the largest that could be missed) and calculates how many cycles it takes to grow to the critical size.
- $da/dN=A(\Delta K)^m$ with $\Delta K=Q\Delta\sigma\sqrt{\pi a}$, integrated from $a_i$ to $a_c$ (from $K_{Ic}$).
- Needs $a_i$ (size and position), $\Delta\sigma$, $\sigma_{max}$, $K_{Ic}$, $A$, $m$ and $Q$.
- **Designs against growth**, and sets **inspection intervals** (typically at half the predicted life).

**Contrast:** Miner/S-N suits parts that must not crack, or cannot be inspected. Paris suits inspectable structures that tolerate defects (airframes, pressure vessels, discs). See [[Total Life vs Damage Tolerance]].

---

## Q2 - Gas-turbine blade: combined LCF and HCF [8 marks]

$N_{LCF}=150\,\Delta\varepsilon^{-1.5}$ and $N_{HCF}=7.5\times10^9\,\Delta\sigma^{-1.2}$ ($\Delta\sigma$ in MPa).

**Life used by the 550 stop-starts at $\Delta\varepsilon=0.23$:**

$$
N_{LCF}(0.23)=150\times0.23^{-1.5}=150\times9.066=1360\ \text{cycles},\qquad
\frac{550}{1360}=0.404.
$$

**Life used by $2.53\times10^6$ flutter cycles at $\Delta\sigma=320$ MPa:**

$$
N_{HCF}(320)=7.5\times10^9\times320^{-1.2}=7.5\times10^9\times9.859\times10^{-4}=7.39\times10^6,\qquad
\frac{2.53\times10^6}{7.39\times10^6}=0.342.
$$

**Total consumed (Miner):**

$$
\sum\frac{n_i}{N_i}=0.404+0.342=\boxed{0.747\ (74.7\,\%)}.
$$

**Remaining life at the new LCF level $\Delta\varepsilon=0.18$:**

$$
N_{LCF}(0.18)=150\times0.18^{-1.5}=1964,\qquad
n_{remaining}=(1-0.747)\times1964=\boxed{498\ \text{stop-starts}}.
$$

**Reasoning and recommendation.**

- Miner assumes each cycle type uses up life independently and linearly, and that order does not matter.
- Here high-strain LCF came first, which is usually *more* damaging than Miner predicts.
- The LCF and HCF laws are empirical fits, and flutter amplitude is uncertain.
- So apply a safety factor of 2: allow about **250 further stop-starts**, then inspect the blade root (NDT) or retire it.

![[Figures/materials_fatigue_miner_budget.png]]

---

## Q3 - Pressure-vessel plate [10 marks]

$a_i=4$ mm, $\sigma_{min}=10$ MPa, $\sigma_{max}=150$ MPa, $K_{Ic}=65\ \mathrm{MPa\sqrt m}$, $A=1.58\times10^{-10}$, $m=3.5$, $Q=1.2$.

**Stress range** (all tensile): $\Delta\sigma=150-10=140$ MPa.

**Critical crack length** (fast fracture at the peak of the cycle):

$$
a_c=\frac1\pi\left(\frac{65}{1.2\times150}\right)^2=\frac1\pi(0.3611)^2=0.0415\ \text m=41.5\ \text{mm}.
$$

**Integrate the Paris law.** Here $1-m/2=-0.75$:

$$
a_c^{-0.75}=0.04151^{-0.75}=10.87,\qquad a_i^{-0.75}=0.004^{-0.75}=62.87,
$$

$$
(Q\Delta\sigma\sqrt\pi)^m=(1.2\times140\times1.7725)^{3.5}=297.8^{3.5}=4.556\times10^8,
$$

$$
N_f=\frac{10.87-62.87}{(-0.75)(1.58\times10^{-10})(4.556\times10^8)}=\frac{-52.00}{-0.05399}=\boxed{963\ \text{cycles}}.
$$

**Recommendation.** With a safety factor of 2, allow about **480 pressurisation cycles**, then re-inspect. Crack growth is fastest near $a_c$, so re-inspect well before the end of life.

**Assumptions to state:** $Q$ is constant as the crack deepens (in reality it changes as the crack approaches the back face; the plate thickness is not given, and $a_c=41.5$ mm may exceed it, so a leak or net-section yield could come first). $A$ and $m$ are from lab data. There is no environmental or temperature effect, and no Stage I growth.

---

## Q4 - Lecturer's worked example: large flat plate [10 marks]

+120/-30 MPa, $a_i=1.00$ mm, $K_{Ic}=45\ \mathrm{MPa\sqrt m}$, $A=2\times10^{-12}$, $m=3$, $Q=1$.

**Stress range.** A compressive stress closes the crack and does not drive growth, so only the tensile part counts:

$$
\Delta\sigma=120\ \text{MPa}\quad(\text{not }150).
$$

**Critical crack length:**

$$
a_c=\frac1\pi\left(\frac{45}{1\times120}\right)^2=0.0448\ \text m.
$$

**Integrate** with $1-m/2=-\tfrac12$:

$$
N_f=\frac{a_c^{-1/2}-a_i^{-1/2}}{(-\tfrac12)A(\Delta\sigma\sqrt\pi)^3}
=\frac{0.0448^{-1/2}-0.001^{-1/2}}{(-\tfrac12)(2\times10^{-12})(120\sqrt\pi)^3}
$$

$$
=\frac{4.727-31.623}{(-\tfrac12)(2\times10^{-12})(9.622\times10^6)}=\frac{-26.90}{-9.622\times10^{-6}}
=\boxed{2.80\times10^6\ \text{cycles}}.
$$

The lecturer quotes 2,801,904 cycles, from $a_c$ rounded to 0.0448 m. Carrying full precision gives 2,795,265; both are fine. **Recommend** re-inspection at about $1.4\times10^6$ cycles (SF 2).

---

## Q5 - Mixer shaft, once per revolution [10 marks]

$a_i=1.5$ mm, $\sigma_{min}=5$ MPa, $\sigma_{max}=300$ MPa, $K_{Ic}=55\ \mathrm{MPa\sqrt m}$, $m=2.5$, $Q=1.2$. The Green Book prints $A=2.67\times10^{-11}$; the 2016-17 exam version prints $A=2.67\times10^{-10}$. Both are worked below.

$$
\Delta\sigma=295\ \text{MPa},\qquad
a_c=\frac1\pi\left(\frac{55}{1.2\times300}\right)^2=\frac1\pi(0.1528)^2=7.43\ \text{mm}.
$$

With $1-m/2=-0.25$:

$$
a_c^{-0.25}=0.00743^{-0.25}=3.406,\qquad a_i^{-0.25}=0.0015^{-0.25}=5.081,
$$

$$
(1.2\times295\sqrt\pi)^{2.5}=627.4^{2.5}=9.862\times10^6.
$$

| $A$ | Denominator $(-0.25)A(9.862\times10^6)$ | $N_f$ | With SF 2 |
|---|---:|---:|---:|
| $2.67\times10^{-11}$ (Green Book) | $-6.583\times10^{-5}$ | **25,450 revolutions** | ~12,700 |
| $2.67\times10^{-10}$ (2016-17 exam) | $-6.583\times10^{-4}$ | **2,545 revolutions** | ~1,270 |

**Reasoning.** One major cycle per revolution, so the life in revolutions equals $N_f$. For a mixer running at, say, 60 rpm, 2,545 revolutions is only about 42 minutes. So in practice this shaft should be **replaced immediately**, and the cause fixed: the unbalanced blades (the source of the rotating-bending cycle), and the surface condition at the crack origin.

A factor of 10 in $A$ gives a factor of 10 in life, which shows how sensitive the prediction is to the measured Paris constants.
