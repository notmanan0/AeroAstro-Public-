---
title: "SESA2027 B2 - Root Locus Method"
module: "SESA2027 Aerospace Mechanics & Control"
type: topic
stream: "Part B: Control Systems"
order: 7
tags:
  - sesa2027
  - root-locus
  - control-design
aliases: ["Root Locus"]
date: 2026-09-23
status: lectured
coverage: "L2.04 (stability revisited, double-integrator examples, six construction steps, SPO pitch-rate locus)"
parent: ["[[SESA2027 Aerospace Mechanics & Control Hub]]"]
prerequisites: ["[[SESA2027 B1 - Control System Fundamentals and PID Control]]"]
next_topics: ["[[SESA2027 B3 - Frequency-Response PID Design and Ziegler-Nichols Tuning]]"]
key_concepts: ["[[Root Locus]]", "[[Poles and Zeros]]", "[[Damping Ratio and Natural Frequency]]"]
tutorial_sheets: ["[[SESA2027 Practice Problems 2 Solutions]]"]
sources: ["02 - Sources/Lectures/Lecture 2.04.pdf", "02 - Sources/Lectures/Lecture 2.04 recording.txt"]
---

# SESA2027 B2 - Root Locus Method

> [!abstract] Summary
> The root locus plots how the closed-loop poles, the roots of $1+KG(s) = 0$, move through the $s$-plane as one parameter, usually the loop gain $K$, goes from 0 to ∞. Branches start at the open-loop poles and end at the open-loop zeros or at infinity along asymptotes. Because a pole's position gives its decay rate, frequency, $\omega_n$ and $\zeta = \cos\beta$, the locus links the gain directly to stability and transient response.

> [!summary]- Exam use: quick path
> - **Use it when:** a question gives an open-loop transfer function in ZPK form (it will be given, L2.04, l. 412) and asks for a root-locus sketch, the effect of a P or PD controller, the range of stable gain, or the gain for a target $\zeta$.
> - **Assumptions:** unity negative feedback, characteristic equation $1+KG(s)=0$; $K$ from 0 to $+\infty$ (for a negative-gain plant such as the SPO, run $K$ from 0 to $-\infty$ or absorb the sign into $G$); start from the open-loop TF.
> - **Method:** 1. Mark poles (×) and zeros (○). 2. Real-axis segments: odd number of poles + zeros to the right. 3. $n-m$ asymptotes at $(2k+1)180°/(n-m)$ from $\sigma_a=(\Sigma p-\Sigma z)/(n-m)$. 4. Break-in/away from $A'B-AB'=0$; imaginary-axis crossing from Routh or $s=i\omega$. 5. Sketch symmetrically, label everything (the marking scheme, ll. 533–557).
> - **Common mistakes:** drawing the locus from the closed-loop TF; forgetting that a negative plant gain flips the locus, so positive $K$ gives the complementary (unstable) locus.
> - **Practise:** [[#Worked example: three poles, three asymptotes]] · [[SESA2027 Mock Questions#Q7. Root locus sketch and stable gain range|Mock Q7]] · [[SESA2027 Practice Problems 2 Solutions]] (Q6)

Closing a loop around a plant moves its poles. Turn the controller gain up from zero and every closed-loop pole slides through the $s$-plane: at zero gain they sit on the open-loop poles, at very high gain they are pulled into the open-loop zeros or flung off to infinity. The root locus is the map of those paths. Because the pole position fixes the response (distance from the origin = $\omega_n$, angle = $\zeta$, real part = decay rate, crossing the imaginary axis = instability), the locus shows at a glance which gains give a well-damped, fast, stable loop and which do not.

Zeros attract branches; poles repel them. That is why adding a derivative term (a zero) to the double integrator bends its branches off the imaginary axis into the stable left half-plane, and why a plant with several poles and no zeros will always go unstable at high enough gain.

---

## 1. Stability revisited
The open-loop response is set by the roots of the characteristic polynomial:

| Root location | Response |
|---|---|
| Left half-plane, real | Exponential decay |
| Left half-plane, complex | Oscillatory decay |
| Imaginary axis | Sustained oscillation (marginal) |
| Right half-plane, real | Exponential growth |
| Right half-plane, complex | Oscillatory growth |

For $\lambda = \sigma\pm i\omega$:
- $\omega_n = \sqrt{\sigma^2+\omega^2}$ is the distance from the origin.
- $\zeta = -\sigma/\omega_n = \cos\beta$, where $\beta$ is the angle from the negative real axis.
- Lines of constant $\zeta$ are rays from the origin: $\omega = \sqrt{\sigma^2/\zeta^2-\sigma^2}$.

Constant-$\zeta$ line, line by line (L2.04, ll. 92–116). Start from $\zeta = -\sigma/\omega_n$ with $\sigma<0$:

$$
\omega_n = -\frac{\sigma}{\zeta}
$$

Substitute $\omega_n^2 = \sigma^2+\omega^2$:

$$
\sigma^2+\omega^2 = \frac{\sigma^2}{\zeta^2}
$$

$$
\omega = \sqrt{\frac{\sigma^2}{\zeta^2}-\sigma^2} = |\sigma|\frac{\sqrt{1-\zeta^2}}{\zeta}
$$

So $\omega/|\sigma|$ is fixed for a given $\zeta$: the line is a ray from the origin.

The rays of constant damping are what make the s-plane useful for design (L2.04, ll. 121–142). To guarantee, say, $\zeta\ge0.5$, place the closed-loop poles on or inside the $\zeta = 0.5$ ray. Moving a pole only along its ray changes $\omega_n$ but not $\zeta$; to add damping you have to change the ratio of the imaginary part to the real part.

> [!note] Marginal stability is mostly a textbook case (L2.04, ll. 53–71)
> Poles exactly on the imaginary axis are rare in real hardware, which is always slightly damped or slightly unstable because of imperfections and flexibility. A controller can, however, put closed-loop poles there, as the P-controlled double integrator below shows.

## 2. Two instructive examples
Plant: double integrator $G = 1/s^2$.

P controller, $C = K_P$:

$$
\frac{X}{R} = \frac{K_P}{s^2+K_P},\qquad s = \pm i\sqrt{K_P}
$$

The roots move only along the imaginary axis. The response is a sustained oscillation, i.e. marginally stable.

> [!info] Stated exam answer (L2.04, ll. 258–265)
> "If I was to ask what is the effect of a proportional controller on the exam, and you were to tell me it increases the natural frequency, and then you show me this, and then you mention again the root locus for this system, I would be very happy." Raising $K_P$ raises $\omega_n = \sqrt{K_P}$, so the oscillation gets faster but never decays. This is also why a CubeSat attitude loop cannot be stabilised with P alone (ll. 216–236).

PD controller, $C = K_D(s+K_P/K_D)$:

$$
s^2+K_Ds+K_D\frac{K_P}{K_D} = 0\quad\Rightarrow\quad s = \frac{-K_D\pm\sqrt{K_D^2-4K_D(K_P/K_D)}}{2}
$$

With $K_P/K_D = 1$:

| $K_D$ | Roots |
|---|---|
| 0 | $s_{1,2} = 0$ (repeated) |
| $0<K_D<4$ | Complex conjugate |
| $4$ | $s_{1,2} = -2$ (repeated) |
| $>4$ | Real, distinct: $s_1\to-\infty$, $s_2\to-1$ (the zero) |

The locus is a circle around the zero at $-1$. The system is now stable. Along the circle $\zeta$ rises from 0 (at $K_D = 0$) to 1 (at the break-in point, $K_D = 4$).

> [!warning] Correction: what the $\zeta = 0.75$ line means
> An earlier version of this note said "the best damping on the circle is $\zeta\approx0.75$". That is not what the lecture said. The $\zeta = 0.75$ ray was added to the updated slides as a design target: inside it the system is already heavily damped, so the question becomes whether extra control effort is worth it (L2.04, ll. 386–392). On this circle $\zeta = \sqrt{K_D/4}$, so $\zeta = 0.75$ is reached at $K_D = 2.25$, with roots $-1.125\pm0.992i$ (computed). From the step responses for $K = 1, 2, 4, 8$, the lecturer would choose about $K_D = 4$, the edge of the complex region, because beyond it the gains in performance are minimal (ll. 394–406).

Changing the ratio $K_P/K_D$ ("wink … that might be something that could come in the exam", L2.04, ll. 307–317). With $K_P/K_D = r$ the characteristic equation is $s^2+K_Ds+rK_D = 0$, so

$$
s = \frac{-K_D\pm\sqrt{K_D^2-4rK_D}}{2}
$$

The discriminant is zero when $K_D^2 = 4rK_D$, i.e. $K_D = 4r$. There the roots are repeated at $s = -K_D/2 = -2r$. The zero is at $-r$, the locus is a circle of radius $r$ centred on the zero, and $\zeta = \sqrt{K_D/(4r)}$ on the circle.

| $r = K_P/K_D$ | Zero | Break-in point | $K_D$ at break-in | $K_D$ for $\zeta = 0.75$ |
|---|---|---|---|---|
| 1 | −1 | −2 | 4 | 2.25 |
| 2 | −2 | −4 | 8 | 4.5 |
| 4 | −4 | −8 | 16 | 9 |

(Checked numerically with `numpy.roots`.)

## 3. Six construction steps
1. Convert the open-loop TF to zero-pole-gain form.
2. Plot the poles (×) and zeros (○). Branches start at the poles ($K=0$) and end at the zeros or infinity ($K\to\infty$).
3. **Real-axis segments**: a real-axis point is on the locus if the number of real poles plus zeros to its right is odd.
4. **Asymptotes**:
   - Number: $n-m$ (poles minus zeros).
   - Angles: $\theta_k = \dfrac{(2k+1)\pi}{n-m}$.
   - Centroid: $\sigma_a = \dfrac{\sum\text{poles}-\sum\text{zeros}}{n-m}$.
5. **Branch directions**:
   - Departure/arrival angle: $\phi = \pi+\sum\angle(\text{to zeros})-\sum\angle(\text{to poles})$.
   - Break-in/away points satisfy $\dfrac{dK}{ds} = 0$, with $K(s) = -A(s)/B(s)$.
6. Sketch the locus (then verify it numerically).

**Break-in/away condition, line by line.** On the locus $1+KG = 0$ with $G = B/A$, so $K(s) = -A(s)/B(s)$. Differentiate with the quotient rule:

$$
\frac{dK}{ds} = -\frac{A'(s)B(s)-A(s)B'(s)}{B(s)^2}
$$

This is zero when the numerator is zero; the denominator only matters if it is zero, which would make $dK/ds$ infinite (L2.04, ll. 510–525):

$$
A'(s)B(s)-A(s)B'(s) = 0
$$

Keep only the roots that lie on a real-axis segment of the locus. The slide's version of this formula had a sign/order slip, which the lecturer corrected aloud (ll. 515–516).

### Where the rules come from

The slides state the six steps. They all follow from one equation. On the locus

$$
1+KG(s)=0\quad\Rightarrow\quad KG(s)=-1
$$

A complex number equals $-1$ only if its magnitude is 1 and its angle is an odd multiple of $180°$. For $K>0$:

$$
\lvert KG(s)\rvert=1\quad\text{(magnitude condition: fixes } K\text{ at a point)}
$$

$$
\angle G(s)=(2k+1)\,180°\quad\text{(angle condition: fixes the shape)}
$$

With $G=k_0\prod(s-z_i)/\prod(s-p_j)$ and $k_0>0$, the angle of a product is the sum of angles:

$$
\angle G(s)=\sum_i\angle(s-z_i)-\sum_j\angle(s-p_j)
$$

where $\angle(s-p_j)$ is the angle of the arrow from the pole $p_j$ to the test point $s$.

- **Start and end points.** Write the condition as $A(s)+KB(s)=0$. At $K=0$ it is $A=0$: the open-loop poles. As $K\to\infty$ divide by $K$: $B=0$, the zeros. With $n>m$, the remaining $n-m$ branches go to infinity.
- **Real-axis rule.** Take a test point on the real axis. A complex-conjugate pair contributes angles $+\theta$ and $-\theta$, which cancel. A real pole or zero to the left contributes $0°$; one to the right contributes $180°$. So the total is $180°\times(\text{number to the right})$, which is an odd multiple of $180°$ only if that number is odd.
- **Asymptote angles.** Far from the origin every arrow points in nearly the same direction $\theta$, so $\angle G\approx(m-n)\theta$. Setting $(m-n)\theta=(2k+1)180°$ and taking magnitudes gives $\theta_k=(2k+1)180°/(n-m)$ (the sign does not matter because the set of angles is symmetric).
- **Centroid.** Expand both polynomials: $A=s^n-(\Sigma p)s^{n-1}+\dots$ and $B=s^m-(\Sigma z)s^{m-1}+\dots$. Long division gives $A/B=s^{n-m}-(\Sigma p-\Sigma z)s^{n-m-1}+\dots$. Compare with $(s-\sigma_a)^{n-m}=s^{n-m}-(n-m)\sigma_as^{n-m-1}+\dots$: the far-field locus looks like $n-m$ straight lines from $\sigma_a=(\Sigma p-\Sigma z)/(n-m)$.
- **Departure angle.** Apply the angle condition at a test point a tiny distance from a complex pole $p_d$. All other arrows are as if drawn to $p_d$ itself; the one unknown is the departure angle $\phi$: $\sum\angle(\text{to zeros})-\sum_{j\ne d}\angle(\text{to poles})-\phi=180°$, which rearranges to the slide formula.

> [!warning] Negative gain: the complementary locus
> If $K<0$ (or the plant's gain $k_0<0$, as for the SPO), $KG=-1$ needs $\angle G=0°+k\,360°$. Every rule above flips: real-axis segments have an even number to the right, asymptotes sit at $k\,360°/(n-m)$. This is why the SPO pitch-rate locus must be drawn for $K$ from 0 to $-\infty$ (L2.04, ll. 152–157, 573–579).

### Worked example: three poles, three asymptotes

*(The lecture promised an example with asymptotes for upload, L2.04, l. 420; this one is suggested, not lecturer-set.)* $KG(s)=K/[s(s+2)(s+4)]$, $K>0$.

1. Poles $0$, $-2$, $-4$; no zeros. $n-m=3$.
2. Real axis: $[-2,0]$ (one pole to the right) and $(-\infty,-4]$ (three to the right). Not $(-4,-2)$ (two).
3. Asymptotes: $\theta_k=60°,180°,300°$ from $\sigma_a=(0-2-4)/3=-2$.
4. Breakaway: $A=s^3+6s^2+8s$, $B=1$, so $A'B-AB'=3s^2+12s+8=0$, giving $s=-0.845$ or $-3.155$. Only $-0.845$ lies on a segment. The gain there is $K=-A(-0.845)=3.08$.
5. Imaginary-axis crossing: the closed-loop polynomial is $s^3+6s^2+8s+K$. Routh's $s^1$ row is $(6\times8-K)/6$, which is positive only for $K<48$. At $K=48$ the $s^2$ row gives the auxiliary equation $6s^2+48=0$, so $s=\pm i\sqrt8=\pm2.83i$.

![[amc_root_locus_three_poles.png|680]]

> [!check] Numerical check (`numpy.roots`)
> At $K=48$ the roots of $s^3+6s^2+8s+48$ are $-6$ and $\pm2.828i$. ✓ The stable range is $0<K<48$. Unlike the two-pole PS2 Q6 plant, which is stable for every $K>0$, three poles with no zeros always go unstable at high gain: two asymptotes point into the right half-plane.

> [!info] Construction tips from the lecture (L2.04)
> - Always start from the open-loop TF, never the closed loop (ll. 424–426).
> - In the exam the ZPK form will be given; in the lab you must factor it yourself (ll. 412–413).
> - Asymptote angles are measured anticlockwise from the positive real axis, and $k$ is numbered from 0 "like in Python" (ll. 500–506).
> - The complex parts of conjugate poles cancel in the centroid, so only real parts matter (ll. 494–497).
> - The marking scheme for a sketch: straight, labelled axes; a symmetric locus; poles and zeros placed and labelled; branches drawn; break point, pole and zero values and asymptote annotated. "If you have all of these elements, you get full marks. If you miss one, then you start losing marks" (ll. 533–557).

## 4. Worked example: SPO pitch-rate with a P controller

$$
G(s) = \frac{-1.39(s+0.306)}{s^2+0.805s+1.325},\qquad C = K,\qquad \frac{X}{R} = \frac{K[-1.39(s+0.306)]}{(s^2+0.805s+1.325)+K[-1.39(s+0.306)]}
$$

1. **ZPK form**: $G = \dfrac{-1.39(s+0.306)}{(s+0.4025-1.0784i)(s+0.4025+1.0784i)}$.
2. **Poles**: $-0.4025\pm1.0784i$. Zero: $-0.306$. Gain: $-1.39$. Two poles and one zero.
3. **Real axis**:
   - For $s<-0.306$, one object (the zero) is to the right, so the point is on the locus.
   - For $s>-0.306$, there are none, so it is off.
4. **Asymptotes**: $n-m=1$.
   - $\sigma_a = \dfrac{(-0.4025+1.0784i)+(-0.4025-1.0784i)-(-0.306)}{1} = -0.499$.
   - $\theta = 180^\circ$.
5. **Break-in point**: $K(s) = -\dfrac{s^2+0.805s+1.325}{-1.39(s+0.306)}$. Setting $dK/ds = 0$ gives $s^2+0.612s-1.07867 = 0$, so $s = 0.7767$ (reject: not on the locus) or $\boxed{s = -1.3887}$. The complex poles move left, meet at the break-in point, then one branch goes to the zero and the other to $-\infty$.

   The algebra, with $A=s^2+0.805s+1.325$ and $B=-1.39(s+0.306)$:

   $$A'B-AB'=(2s+0.805)(-1.39)(s+0.306)-(s^2+0.805s+1.325)(-1.39)$$

   $$=-1.39\left[(2s+0.805)(s+0.306)-(s^2+0.805s+1.325)\right]$$

   $$=-1.39\left[2s^2+1.417s+0.2463-s^2-0.805s-1.325\right]=-1.39\left[s^2+0.612s-1.0787\right]$$

   The roots are $s=\left(-0.612\pm\sqrt{0.3745+4.3147}\right)/2=(-0.612\pm2.1655)/2$. At $s=-1.3887$: $A=2.1356$ and $B=1.5050$, so $K=-A/B=-1.419$.
6. **Observations**:
   - Because the plant gain is negative, negative $K$ is needed for stable, negative feedback.
   - The open loop has $\zeta\approx0.4$ (exactly $0.805/(2\sqrt{1.325}) = 0.35$), and $\zeta$ increases with $|K|$.
   - At the break-in point $\zeta = 1$ (critically damped, reached at $K = -1.42$); beyond it, with larger $|K|$, the system is overdamped. The lecture's "highly overdamped" at the break point (L2.04, l. 585) refers to the branches beyond it.
   - P alone gives a good rise time but a significant steady-state error, which motivates adding I.

> [!check] Steady-state value under P control (computed)
> The closed-loop final value is $KB(0)/[A(0)+KB(0)]$ with $A(0) = 1.325$ and $B(0) = -0.4253$. For $K = -1$ it is 0.24, for $K = -5$ it is 0.62, and for $K = -30$ it is 0.91. Even the "really big gain" of −30 that the lecturer showed (L2.04, ll. 586–594) leaves a 9 % steady-state error.

> [!warning] Why $K$ must be negative here (L2.04, ll. 152–157, 573–579)
> The root-locus rules assume $K$ goes from 0 to $+\infty$. The SPO plant has a negative gain (negative elevator gives positive pitch), so the analysis must run $K$ from 0 to $-\infty$. With positive $K$ you draw the complementary locus and get an unstable loop.

![[amc_spo_root_locus.png|620]]

> [!example] PS2 Q6: $G = K/[s(s+4)]$
> - Poles at $0$ and $-4$, no zeros.
> - Real-axis segment $[-4,0]$.
> - Two asymptotes at $\pm90^\circ$, centroid $-2$, breakaway at $s=-2$ ($K=4$).
> - $s^2+4s+K=0$ is stable for all $K>0$.
>
> Adding a PD zero at $-1$ gives $s^2+(4+K)s+K = 0$, so the locus stays on the real axis. There is a branch from 0 to −1, and from −4 to $-\infty$. The response is faster, non-oscillatory and well damped. See [[SESA2027 Practice Problems 2 Solutions]].

![[amc_ps2_q6_root_locus.png]]

## 5. Pros, cons and limitations

| Pros | Cons |
|---|---|
| Intuitive picture of how the poles move | Tedious by hand for high order |
| Links pole motion to stability, $\zeta$ and transient response | Handles only one parameter at a time |
| Good for choosing gains and designing lead/lag compensators | Graphical accuracy is limited |
| Shows where poles start and end | Misleading with delays, non-minimum phase or bad scaling |
| Works for any LTI rational TF | Does not show frequency-domain margins directly |
| Easy with software | Mainly SISO |

**Limitations**:
- It assumes a precise, known TF.
- It becomes unreliable with large, unstructured, nonlinear or time-varying uncertainty.
- It gives no robustness guarantees.

## Lecturer emphasis and exam hints (transcripts)

> [!info] Exam signals in L2.04
> - Hand construction "might be handy for exam" (l. 14); the ZPK form will be given (l. 412).
> - Effect of a P controller, illustrated with the $1/s^2$ root locus (ll. 264–265).
> - Redo the PD design with a different $K_P/K_D$ ratio (ll. 307–317).
> - Sketch marking scheme (ll. 533–557).
> - Admin: the root-locus program comes with the computer lab after the quiz week (ll. 560–562). An example with asymptotes was promised for upload (l. 420). The slides were re-uploaded with the $\zeta = 0.75$ line (l. 386).
> - Further reading: Franklin et al., sections 5.1–5.3 (ll. 604–605).

## Transcript slips

> [!warning] Speech-to-text and spoken slips, with the correct version
> | Where | Transcript says | Correct |
> |---|---|---|
> | L2.04, l. 43 | "about 20 seconds, two seconds, sorry" | about 2 s |
> | L2.04, l. 47 | "five times one to the minus, one to the seven" | $5\times10^7$ |
> | L2.04, l. 223 | "the one over z squared" | $1/s^2$ |
> | L2.04, l. 259 | P's main effect is "to increase the rise time" | P reduces rise time (it speeds the response up) by raising $\omega_n$ |
> | L2.04, l. 341 | the roots "meet at 2" | at $-2$ (self-corrected, l. 343) |
> | L2.04, ll. 346–347 | slide: one root "tends towards … that's a typo" | towards $-\infty$ |
> | L2.04, l. 401 | "value tops 4" | about $K_D = 4$ |
> | L2.04, ll. 433, 486 | number to the right "is off", "is solved" | is odd |
> | L2.04, l. 454 | break-away "so basically the inflection point" | a stationary point of $K(s)$ on the real axis ($dK/ds = 0$), not an inflection point |
> | L2.04, l. 468 | "the rule of diagram" | the root-locus diagram |
> | L2.04, l. 483 | "real axis assessments" | real-axis segments |
> | L2.04, l. 487 | "anything on the right hand side of the pole" | of the zero |
> | L2.04, l. 491 | "anything that is a bigger magnitude than the zero will not be on the locus" | points left of the zero ($s<-0.306$, larger magnitude) are on the locus, as l. 492 says |
> | L2.04, ll. 515–516 | "the derivative of a … times b … divided by the square of the numerator" | $(A'B-AB')/B^2$, divided by the square of the denominator |
> | L2.04, l. 585 | "highly overdumped" at the break point | $\zeta = 1$ at the break point; overdamped beyond |
> | L2.04, l. 600 | "it becomes an effective" | it becomes ineffective |

## Terminology and alternative names

| Course term | Also called | Where the course uses it | Note |
|---|---|---|---|
| root locus | Evans root locus, root-locus diagram | L2.04 | |
| zero-pole-gain (ZPK) form | factored form, $k\prod(s-z)/\prod(s-p)$ | L2.04 step 1 | given in the exam |
| real-axis segments | real-axis rule | L2.04 step 3 | |
| asymptote centroid $\sigma_a$ | centre of asymptotes, asymptote intercept | L2.04 step 4 | |
| break-in / break-away point | breakaway point, arrival/departure point on the real axis | L2.04 step 5 | a stationary point of $K(s)$, not an inflection point (l. 454 slip) |
| departure / arrival angle | angle of departure (from a pole) / arrival (at a zero) | L2.04 step 5 | |
| complementary root locus | negative-gain root locus, $0°$ locus | L2.04, ll. 152–157 (by implication) | needed for the SPO plant |
| lines of constant $\zeta$ | damping-ratio rays, constant-damping lines | L2.04, ll. 92–142 | |
| marginal stability | neutral stability, critical stability | L2.04 | poles on the imaginary axis |

## Links
- Parent: [[SESA2027 Aerospace Mechanics & Control Hub]] · Previous: [[SESA2027 B1 - Control System Fundamentals and PID Control]] · Next: [[SESA2027 B3 - Frequency-Response PID Design and Ziegler-Nichols Tuning]]
- Concepts: [[Root Locus]] · [[Poles and Zeros]] · [[Damping Ratio and Natural Frequency]] · [[Routh-Hurwitz Stability Criterion]]
- Pole geometry and specifications: [[SESA2027 A4 - Laplace Transforms, Transfer Functions and Step Response#Deriving the specifications|A4]]

## Sources
- Lecture 2.04 (Dr S. Araujo-Estrada): slides `Lecture 2.04.pdf`; transcript `Lecture 2.04 recording.txt` (speech-to-text)
- Franklin, Powell & Emami-Naeini (2014) Ch. 5.1–5.3
- Figures: `01 - Notes/Figures/generate_amc_b2_figures.py`

## Self-study tasks

Two tasks were set in L2.04 (marked lecturer-set). The effect of P on the $1/s^2$ locus, a PD locus for another ratio and a full-marks sketch were all named as exam material (ll. 258–265, 307–317, 533–557).

### Core

- [ ] Lecturer-set (L2.04, ll. 310–317): redo the double-integrator PD root locus with $K_P/K_D = 2$ and $4$. → [[#2. Two instructive examples]]
- [ ] Lecturer-set (L2.04, ll. 591–594, "bear this in mind … when you're doing your computer lab"): show that P control of the SPO pitch rate leaves a steady-state error at any gain. → [[#4. Worked example: SPO pitch-rate with a P controller]]
- [ ] Explain the effect of a P controller using the $1/s^2$ root locus (stated exam answer). → [[#2. Two instructive examples]]
- [ ] Sketch the locus of $K/[s(s+2)(s+4)]$ with every element of the marking scheme, and find the stable range of $K$. → [[#Worked example: three poles, three asymptotes]]
- [ ] PS2 Q6. → [[SESA2027 Practice Problems 2 Solutions]]
- [ ] Mock exam question. → [[SESA2027 Mock Questions#Q7. Root locus sketch and stable gain range|Mock Q7]]

### Further practice

- [ ] Find the SPO break-in point from $A'B-AB' = 0$ and the gain there (suggested). → [[#4. Worked example: SPO pitch-rate with a P controller]]
- [ ] Derive the real-axis rule, asymptote angles and centroid from the angle condition (suggested). → [[#Where the rules come from]]
