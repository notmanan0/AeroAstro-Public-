---
title: "Confidence Intervals and Hypothesis Tests for the Mean"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: concept
stream: "Block 5: Series and Statistics"
aliases: ["Confidence interval", "Hypothesis test", "Significance level", "One-tailed test", "Two-tailed test", "Standard error"]
tags: [math1054, concept, statistics]
status: complete
parent_lectures: ["[[MATH1054 M25 - Statistics II]]"]
related_concepts: ["[[Normal Distribution and Standardisation]]", "[[Accuracy and Precision]]"]
sources: ["MATH1054 Module Booklet, Module 25 (items 6–10)"]
---

# Confidence Intervals and Hypothesis Tests for the Mean

A **confidence interval** for a population mean $\mu$ is the range $\bar x\pm z\,\sigma/\sqrt n$ built from a sample so that a stated proportion of such intervals (95% with $z=1.96$) contain $\mu$. A **hypothesis test** decides whether a sample mean is consistent with a claimed value $\mu_0$ using the statistic $Z=(\bar x-\mu_0)/(\sigma/\sqrt n)$.

Both rest on the sampling distribution of the mean. Averaging $n$ independent observations keeps the mean at $\mu$ and divides the variance by $n$, so $\bar X$ has standard deviation $\sigma/\sqrt n$, the **standard error**. $\bar X$ is normal when the parent is normal, and approximately normal for any parent when $n\ge30$ (central limit theorem); with $n\ge30$ an unknown $\sigma$ may be replaced by the sample standard deviation $s$. Then $(\bar X-\mu)/(\sigma/\sqrt n)\sim N(0,1)$, and

$$
P\Big(-1.96\le\frac{\bar X-\mu}{\sigma/\sqrt n}\le1.96\Big)=0.95 .
$$

Rearranging each inequality to isolate $\mu$ gives $P\big(\bar X-1.96\,\sigma/\sqrt n\le\mu\le\bar X+1.96\,\sigma/\sqrt n\big)=0.95$, which is the 95% interval. The other levels use $1.645$ (90%) and $2.58$ (99%). The interval narrows as $1/\sqrt n$, so a margin $E$ needs $n\ge(z\sigma/E)^2$.

A test states $H_0:\mu=\mu_0$ and an alternative: one-tailed ($\mu>\mu_0$ or $\mu<\mu_0$, for wording like "improvement" or "greater than") or two-tailed ($\mu\ne\mu_0$, for "different from"). $H_0$ is rejected when $Z$ falls in the rejection region, whose probability under $H_0$ is the significance level $\alpha$. At 5% that region is $Z>1.645$ one-tailed and $|Z|>1.96$ two-tailed; at 1% two-tailed it is $|Z|>2.58$. Rejecting a true $H_0$ is a **type I error**, with probability $\alpha$ by construction; accepting a false $H_0$ is a **type II error**. A two-tailed test at 5% accepts $\mu_0$ exactly when $\mu_0$ lies inside the 95% confidence interval, so the two methods always agree.

For example, steel wire from an existing process has $\mu=1250$, $\sigma=150$, and a new process gives $\bar x=1312$ from 25 measurements. Testing for an improvement, $H_1:\mu>1250$ is one-tailed and

$$
Z=\frac{1312-1250}{150/\sqrt{25}}=\frac{62}{30}=2.07>1.645,
$$

so $H_0$ is rejected at 5% ($p=0.019$). Two-tailed, phosphorus analyses with $n=64$, $\bar x=3.3\%$ and $s=0.8\%$ give $Z=0.3/0.1=3.0>1.96$ against $\mu_0=3\%$, a significant difference even at 1%. For intervals, cartons with $\sigma=6$ ml, $n=30$ and $\bar x=570$ ml give the 95% interval $570\pm1.96(1.095)=(567.9,\ 572.1)$ ml and the 90% interval $(568.2,\ 571.8)$ ml.

The common traps are choosing the tail from the result instead of the question's wording ($Z=1.80$ is significant one-tailed but not two-tailed), and dividing by $n$ instead of $\sqrt n$. For small samples ($n<30$) with $\sigma$ unknown, $1.96$ is too small: the correct multiplier comes from the $t$-distribution ($2.045$ for $n=30$, $2.776$ for $n=5$), which is beyond this module.

## Related

- Topics: [[MATH1054 M25 - Statistics II#7. Confidence intervals for the mean (booklet item 8)|MATH1054 M25 - Statistics II §7]] · [[MATH1054 M25 - Statistics II#8. Hypothesis tests for the mean (booklet item 10)|§8]]
- Concepts: [[Normal Distribution and Standardisation]] · [[Binomial Distribution]] · [[Accuracy and Precision]]
- Later use: the $\pm2\sigma$ uncertainty interval of a measurement in [[FEEG1004 E1 - Measurement Systems and Temperature Sensors]]; stochastic model updating in [[Model Updating]]
- Sources: MATH1054 Module Booklet, Module 25, items 6–10 (Examples A–F, Exercises C–F, Specimen Test 25 Q3–Q5); this material is not in James, *Modern Engineering Mathematics* (6th ed.), beyond the central limit theorem of §13.5.4.
