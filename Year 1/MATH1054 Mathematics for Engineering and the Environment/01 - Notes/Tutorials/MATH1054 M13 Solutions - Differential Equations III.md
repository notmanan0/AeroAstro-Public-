---
title: "MATH1054 M13 Solutions - Differential Equations III"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: tutorial
stream: "Block 3: Differential Equations"
tags:
  - math1054
  - tutorial-solutions
  - odes
  - constant-coefficients
sheet: "Specimen Test 13 (booklet) + Module 13 work scheme: Examples 10.23–10.45; Exercises 46(a), 49(c), 62(b), 63(a),(b),(h),(j), 66(b), 68(d), 21(a)"
theory_notes: ["[[MATH1054 M13 - Differential Equations III]]"]
key_concepts: ["[[Linear Differential Operators and Superposition]]", "[[Auxiliary Equation]]", "[[Method of Undetermined Coefficients]]", "[[Damping Ratio and Natural Frequency]]"]
status: complete
sources: ["tmp/md/module_13_differential_equations_iii.md", "02 - Sources/Modern Engineering Mathematics.pdf (§10.8–10.10)"]
---

# MATH1054 M13 Solutions - Differential Equations III

> [!abstract] Sheet Info
> The whole Module 13 work scheme. Every general solution was checked with SymPy `dsolve`. Particular integrals were also checked by substituting back.
>
> **Notation**: $\mathrm D=\frac{\mathrm d}{\mathrm dt}$, and $P(m)$ is the auxiliary (characteristic) polynomial. Standard damped form (James 10.50): $\ddot x+2\zeta\omega\dot x+\omega^2x=0$, where $\zeta$ is the **damping parameter** and $\omega$ the **natural frequency**.

## Theory Links
- [[MATH1054 M13 - Differential Equations III]] · [[Linear Differential Operators and Superposition]] · [[Auxiliary Equation]] · [[Method of Undetermined Coefficients]] · [[Damping Ratio and Natural Frequency]]

---

# Part A: Worked examples

## Examples 10.23–10.26: Operators
An **operator** maps functions to functions.

**Ex 10.23**, $\phi[f]=f^2$. Check the expansion:
$$(3t^2-2t+4)^2=9t^4-12t^3+(4+24)t^2-16t+16=9t^4-12t^3+28t^2-16t+16\ ✔$$
Note that this $\phi$ is **not linear**: $\phi[2f]=4f^2\neq2\phi[f]$.

**Ex 10.24**, $\phi[f]=tf^2-4f+t^2$:
- $\phi[g^2]=t(g^2)^2-4g^2+t^2=tg^4-4g^2+t^2$ ✔
- $\phi[e^t]=te^{2t}-4e^t+t^2$ ✔

**Ex 10.25**, $\phi=\frac{\mathrm d}{\mathrm dt}$. For example, $\phi[4t^3-\tan t]=12t^2-\sec^2t$. Differentiation **is** linear.

**Ex 10.26**, $\mathrm L=\mathrm D^2-(\sin t)\mathrm D+e^t$. The ODE $f''-(\sin t)f'+e^tf=t^4$ is simply $\mathrm L[f]=t^4$.

## Example 10.27: Show $\ddot x+4t\dot x-(\sin t)x=\cos t$ is linear
The operator is $\mathrm L=\mathrm D^2+4t\,\mathrm D-\sin t$. For constants $a,b$:
$$\mathrm L[ax_1+bx_2]=(ax_1+bx_2)''+4t(ax_1+bx_2)'-\sin t\,(ax_1+bx_2)$$
$$=a\big(x_1''+4tx_1'-\sin t\,x_1\big)+b\big(x_2''+4tx_2'-\sin t\,x_2\big)=a\mathrm L[x_1]+b\mathrm L[x_2]\ ✔$$
This works because differentiation is linear, and multiplication by a function of $t$ is linear. The variable coefficients do not spoil linearity.

## Example 10.28: Superposition for $\ddot x+\lambda^2x=0$
$\mathrm L[\sin\lambda t]=0$ and $\mathrm L[\cos\lambda t]=0$. By linearity, $\mathrm L[A\sin\lambda t+B\cos\lambda t]=A\cdot0+B\cdot0=0$. So the general solution is $x=A\sin\lambda t+B\cos\lambda t$, with two constants for a second-order equation.

## Example 10.29: $x^{(4)}-\lambda^4x=0$
The auxiliary equation factorises as a difference of squares:
$$m^4-\lambda^4=(m^2-\lambda^2)(m^2+\lambda^2)=0\ \Rightarrow\ m=\pm\lambda,\ \pm\mathrm j\lambda$$
$$\boxed{x=Ae^{\lambda t}+Be^{-\lambda t}+C\cos\lambda t+D\sin\lambda t}$$
Equivalently, $x=A'\cosh\lambda t+B'\sinh\lambda t+C\cos\lambda t+D\sin\lambda t$. This is the beam-vibration equation.

## Example 10.30: $\dddot x-2\ddot x-\dot x+2x=0$
Factor by grouping:
$$m^3-2m^2-m+2=m^2(m-2)-(m-2)=(m-2)(m-1)(m+1)$$
$$\boxed{x=Ae^{2t}+Be^{t}+Ce^{-t}}$$

## Example 10.32: $\ddot x+\lambda^2x=4t^3$
- **CF**: $A\cos\lambda t+B\sin\lambda t$.
- **PI**: the forcing is a cubic, so try a full cubic $x_p=at^3+bt^2+ct+d$. Then $\ddot x_p=6at+2b$, and
$$6at+2b+\lambda^2(at^3+bt^2+ct+d)=4t^3$$
- Compare coefficients:
  - $t^3$: $a=4/\lambda^2$
  - $t^2$: $b=0$
  - $t$: $6a+\lambda^2c=0$, so $c=-24/\lambda^4$
  - constant: $d=0$

$$\boxed{x=A\cos\lambda t+B\sin\lambda t+\frac{4t^3}{\lambda^2}-\frac{24t}{\lambda^4}}$$

## Example 10.33: BVP $\ddot x-k^2x=\sin2t$, $x(0)=x(\frac\pi4)=0$
- **CF**: $A\cosh kt+B\sinh kt$.
- **PI**: try $C\sin2t$. Then $(-4-k^2)C=1$, so $C=-\dfrac1{k^2+4}$.
- $x(0)=A=0$.
- $x(\frac\pi4)=B\sinh\frac{k\pi}4-\dfrac{\sin\frac\pi2}{k^2+4}=0$, so $B=\dfrac{1}{(k^2+4)\sinh(k\pi/4)}$.

$$\boxed{x=\frac{1}{k^2+4}\left[\frac{\sinh kt}{\sinh(k\pi/4)}-\sin2t\right]}$$
The solution is unique, because $\sinh(k\pi/4)\neq0$ for $k>0$.

## Examples 10.34–10.36
These are repeated from Module 06. Full working is in [[MATH1054 M06 Solutions - Differential Equations I]].

| Ex | Auxiliary roots | Solution |
|---|---|---|
| 10.34 | $\frac{9\pm\sqrt{57}}2$ | $Ae^{\frac{9+\sqrt{57}}2t}+Be^{\frac{9-\sqrt{57}}2t}$ |
| 10.35 | $\frac34\pm\mathrm j\frac{\sqrt{31}}4$ | $e^{3t/4}\big(A\cos\frac{\sqrt{31}}4t+B\sin\frac{\sqrt{31}}4t\big)$ |
| 10.36 | $-3,-3$ | $(1+5t)e^{-3t}$ |

## Examples 10.40–10.43: $\ddot x+5\dot x-9x=f(t)$
These four share one CF. The auxiliary equation $m^2+5m-9=0$ gives $m_{1,2}=\dfrac{-5\pm\sqrt{61}}2$ ($\approx1.405$ and $-6.405$):
$$x_c=Ae^{m_1t}+Be^{m_2t}$$
None of the forcing terms clash with the CF.

**10.40**, $f=t^2$. Try $x_p=at^2+bt+c$:
$$2a+5(2at+b)-9(at^2+bt+c)=t^2$$
- $t^2$: $-9a=1$, so $a=-\frac19$.
- $t$: $10a-9b=0$, so $b=-\frac{10}{81}$.
- constant: $2a+5b-9c=0$, so $c=-\frac{68}{729}$.

$$x_p=-\tfrac19t^2-\tfrac{10}{81}t-\tfrac{68}{729}$$

**10.41**, $f=\cos2t$. Try $x_p=a\cos2t+b\sin2t$. Substituting gives $(-13a+10b)\cos2t+(-10a-13b)\sin2t$. So $-13a+10b=1$ and $10a+13b=0$, which give $a=-\frac{13}{269}$ and $b=\frac{10}{269}$:
$$x_p=\tfrac1{269}(10\sin2t-13\cos2t)$$

**10.42**, $f=e^{4t}$. Try $Ce^{4t}$: $P(4)C=(16+20-9)C=27C=1$, so
$$x_p=\tfrac1{27}e^{4t}$$

**10.43**, $f=e^{-2t}+2-t$. By **superposition**, add the PIs for each piece:
- $e^{-2t}$: $P(-2)=4-10-9=-15$, so $-\frac1{15}e^{-2t}$.
- $2-t$: try $at+b$. Then $5a-9(at+b)=2-t$, so $a=\frac19$ and $b=-\frac{13}{81}$.

$$x_p=-\tfrac1{15}e^{-2t}+\tfrac19t-\tfrac{13}{81}$$

In each case the general solution is $x=x_c+x_p$.

## Example 10.44: $\ddot x+\dot x-2x=e^{-2t}$ (a clash)
- $P(m)=m^2+m-2=(m+2)(m-1)$, so $x_c=Ae^t+Be^{-2t}$.
- The forcing $e^{-2t}$ **is** in the CF, so try $x_p=Cte^{-2t}$.
- For a simple root this gives $C=1/P'(-2)$, where $P'(m)=2m+1$. So $C=\frac1{-3}$.

$$\boxed{x=Ae^t+Be^{-2t}-\tfrac13te^{-2t}}$$
**Check**: with $x_p=Cte^{-2t}$, $\dot x_p=C(1-2t)e^{-2t}$ and $\ddot x_p=C(4t-4)e^{-2t}$. The sum $\ddot x_p+\dot x_p-2x_p=C(-3)e^{-2t}$, so $C=-\frac13$ ✔.

## Example 10.45: $x^{(4)}-2\dddot x+5\ddot x-8\dot x+4x=e^t$
$P(m)=m^4-2m^3+5m^2-8m+4$. Since $P(1)=0$ and $P'(1)=4-6+10-8=0$, $m=1$ is a **double** root. Dividing out gives
$$P(m)=(m-1)^2(m^2+4).$$
- **CF**: $(A+Bt)e^t+C\cos2t+D\sin2t$.
- **PI**: $e^t$ matches a double root, so try $Kt^2e^t$. The coefficient is $K=\dfrac{1}{P''(1)}$ with $P''(1)=2(1^2+4)=10$.

$$\boxed{x=(A+Bt)e^t+C\cos2t+D\sin2t+\tfrac1{10}t^2e^t}$$

---

# Part B: Assigned exercises

## Exercise 46(a): The operator for $\dot x+t^2x=0$
$$\boxed{\mathrm L=\frac{\mathrm d}{\mathrm dt}+t^2}$$

## Exercise 49(c): The operator for $\ddot x+(\sin t)\dot x=(t+\cos t)x$
Move everything to the left: $\ddot x+(\sin t)\dot x-(t+\cos t)x=0$. So
$$\boxed{\mathrm L=\frac{\mathrm d^2}{\mathrm dt^2}+(\sin t)\frac{\mathrm d}{\mathrm dt}-(t+\cos t)}$$

## Exercise 62(b): $\ddot x-2\dot x-5x=t^2-2t$
- **CF**: $m^2-2m-5=0$ gives $m=1\pm\sqrt6$.
- **PI**: try $at^2+bt+c$. Then $2a-2(2at+b)-5(at^2+bt+c)=t^2-2t$:
  - $t^2$: $-5a=1$, so $a=-\frac15$.
  - $t$: $-4a-5b=-2$, so $b=\frac{14}{25}$.
  - constant: $2a-2b-5c=0$, so $c=-\frac{38}{125}$.

$$\boxed{x=Ae^{(1+\sqrt6)t}+Be^{(1-\sqrt6)t}-\tfrac15t^2+\tfrac{14}{25}t-\tfrac{38}{125}}$$

## Exercise 63
**(a)** $\ddot x-3\dot x+4x=\cos4t-2\sin4t$.
- **CF**: $m=\frac32\pm\mathrm j\frac{\sqrt7}2$, so $x_c=e^{3t/2}\big(A\cos\frac{\sqrt7}2t+B\sin\frac{\sqrt7}2t\big)$.
- **PI**: try $a\cos4t+b\sin4t$. Substituting gives $(-12a-12b)\cos4t+(12a-12b)\sin4t$.
- Matching: $-12a-12b=1$ and $12a-12b=-2$. So $b=\frac1{24}$ and $a=-\frac18$.

$$\boxed{x=x_c-\tfrac18\cos4t+\tfrac1{24}\sin4t}$$

**(b)** $9\ddot x-12\dot x+4x=e^{-3t}$.
- **CF**: $(3m-2)^2=0$, so $x_c=(A+Bt)e^{2t/3}$.
- **PI**: $P(-3)=81+36+4=121$, so $x_p=\frac1{121}e^{-3t}$.

$$\boxed{x=(A+Bt)e^{2t/3}+\tfrac1{121}e^{-3t}}$$

**(h)** $3\ddot x+3\dot x-x=t^2+e^{-2t}$.
- **CF**: $3m^2+3m-1=0$ gives $m=\dfrac{-3\pm\sqrt{21}}6$.
- **PI for $t^2$**: try $at^2+bt+c$. Then $6a+3(2at+b)-(at^2+bt+c)=t^2$, which gives $a=-1$, $b=-6$ and $c=6a+3b=-24$.
- **PI for $e^{-2t}$**: $P(-2)=12-6-1=5$, so $\frac15e^{-2t}$.

$$\boxed{x=Ae^{\frac{-3+\sqrt{21}}6t}+Be^{\frac{-3-\sqrt{21}}6t}-t^2-6t-24+\tfrac15e^{-2t}}$$

**(j)** $\ddot x+16x=1+2\sin4t$ (resonance).
- **CF**: $A\cos4t+B\sin4t$.
- **PI for 1**: $\frac1{16}$.
- **PI for $2\sin4t$**: this is at the natural frequency, so it clashes. Try $t(a\cos4t+b\sin4t)$. Substituting leaves only $8(b\cos4t-a\sin4t)=2\sin4t$, so $a=-\frac14$ and $b=0$.

$$\boxed{x=A\cos4t+B\sin4t+\tfrac1{16}-\tfrac14t\cos4t}$$
The amplitude grows linearly in $t$. This is **resonance** ([[Resonance]]).

## Exercise 66(b): $\ddot x+4\dot x+7x=0$
Compare with $\ddot x+2\zeta\omega\dot x+\omega^2x=0$:
- $\omega^2=7$, so $\boxed{\omega=\sqrt7\approx2.646}$ (natural frequency).
- $2\zeta\omega=4$, so $\boxed{\zeta=\dfrac{2}{\sqrt7}\approx0.756}$ (damping parameter). Since $\zeta<1$, the system is **under-damped**.

## Exercise 68(d): $\frac1\eta\ddot x+40\dot x+25\eta x=0$
Multiply by $\eta$ to get standard form: $\ddot x+40\eta\dot x+25\eta^2x=0$.
- $\omega^2=25\eta^2$, so $\boxed{\omega=5\eta}$.
- $2\zeta\omega=40\eta$, so $\zeta=\dfrac{40\eta}{10\eta}=\boxed{4}$. This is **over-damped**, whatever the value of $\eta$.

## Exercise 21(a): $\ddot x+2\dot x+5x=1$, $x(0)=\dot x(0)=0$
- **CF**: $m=-1\pm2\mathrm j$. **PI**: $x_p=\frac15$.
- So $x=\frac15+e^{-t}(A\cos2t+B\sin2t)$.
- $x(0)=0$ gives $A=-\frac15$.
- $\dot x(0)=-A+2B=0$ gives $B=-\frac1{10}$.

$$\boxed{x=\tfrac15-e^{-t}\Big(\tfrac15\cos2t+\tfrac1{10}\sin2t\Big)}$$
This is the classic under-damped **step response**. It overshoots, then settles to the steady state $\frac15$ ([[Step Response Specifications]]).

![[m1054_step_response_21a.png|600]]

---

# Part C: Specimen Test 13

> [!note] Source
> Transcribed from the MATH1054 Module Booklet (the final page of Module 13), then solved and checked with SymPy, NumPy or SciPy.

## Q1: The operator
$$\boxed{\mathrm L=\frac{\mathrm d^2}{\mathrm dt^2}+3\frac{\mathrm d}{\mathrm dt}+4}$$

## Q2: $\ddot x+5\dot x+6x=f(t)$
**(i)** $m^2+5m+6=(m+2)(m+3)=0$ gives $m=-2,-3$. So $x_c=Ae^{-3t}+Be^{-2t}$ ✔.

**(ii)** Particular integrals, with $P(m)=m^2+5m+6$:
- **(a)** $f=\cos t$. Try $a\cos t+b\sin t$. Substituting gives $(5a+5b)\cos t+(5b-5a)\sin t=\cos t$, so $a=b=\frac1{10}$:
$$x_p=\tfrac1{10}(\cos t+\sin t)$$
- **(b)** $f=e^{-2t}$. This is in the CF (a simple root), so try $Cte^{-2t}$. Then $C=\frac1{P'(-2)}=\frac1{-4+5}=1$:
$$x_p=te^{-2t}$$
- **(c)** $f=1-6t$. Try $at+b$. Then $5a+6(at+b)=1-6t$, so $a=-1$ and $b=1$:
$$x_p=1-t$$

**(iii)** The general solution is $x=Ae^{-3t}+Be^{-2t}+te^{-2t}$. Then:
- $x(0)=A+B=\frac14$
- $\dot x(0)=-3A-2B+1=0$

Solving gives $A=\frac12$ and $B=-\frac14$:
$$\boxed{x=\tfrac12e^{-3t}-\tfrac14e^{-2t}+te^{-2t}}$$

## Q3: $\ddot x+6\alpha\dot x+16x=0$ with $\alpha>0$
**(i)** Compare with $\ddot x+2\zeta\omega\dot x+\omega^2x=0$:
- $\omega^2=16$, so the natural frequency is $\boxed{\omega=4}$.
- $2\zeta\omega=6\alpha$, so the damping parameter is $\boxed{\zeta=\tfrac{3\alpha}4}$.

**(ii)**
- **(a)** Under-damped when $\zeta<1$: $\boxed{0<\alpha<\tfrac43}$.
- **(b)** Critically damped when $\zeta=1$: $\boxed{\alpha=\tfrac43}$.

**(iii)** In general, the **complementary function** (which decays when $\zeta>0$) is the **transient**, and the **particular integral** is the **steady state**. This equation is unforced, so there is no PI: the whole solution is transient, and the steady state is $x=0$.

## Sources
- Transcribed problem statements: `tmp/md/module_13_differential_equations_iii.md`
- James, *Modern Engineering Mathematics* (6th ed.) §10.8–10.10; MATH1054 Module Booklet, Module 13
