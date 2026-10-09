---
title: "MATH1054 M12 Solutions - Differential Equations II"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: tutorial
stream: "Block 3: Differential Equations"
tags:
  - math1054
  - tutorial-solutions
  - odes
  - first-order-odes
sheet: "Specimen Test 12 (booklet) + Module 12 work scheme: Examples 10.14, 10.16, 10.17; Exercises 18(b), 20(d), 21(b), 23(e), 24(d), 25(b), 31(c), 32(c), 33(c)"
theory_notes: ["[[MATH1054 M12 - Differential Equations II]]"]
key_concepts: ["[[Homogeneous First-Order ODEs]]", "[[Exact Differential Equations]]", "[[Integrating Factor Method]]"]
status: complete
sources: ["tmp/md/module_12_differential_equations_ii.md", "02 - Sources/Modern Engineering Mathematics.pdf (§10.5.2–10.5.4)"]
---

# MATH1054 M12 Solutions - Differential Equations II

> [!abstract] Sheet Info
> The Module 12 work scheme: the three remaining first-order methods. Every general solution and IVP was checked with SymPy `dsolve`, and the exact potentials were checked by differentiating back.
>
> **Notation** (James): the exact test is for equations of the form $f(x,t)\,\dot x+g(x,t)=0$.

## Theory Links
- [[MATH1054 M12 - Differential Equations II]] · [[Homogeneous First-Order ODEs]] · [[Exact Differential Equations]] · [[Integrating Factor Method]] · [[Separable First-Order ODEs]]

> [!tip] Which method?
> | Form | Test | Method |
> |---|---|---|
> | $\dot x=F(x/t)$ | the degree of every term is the same | $x=vt$, which makes it separable |
> | $f\dot x+g=0$ | $\partial f/\partial t=\partial g/\partial x$ | find $F$ with $F_x=f$, $F_t=g$; then $F=C$ |
> | $\dot x+P(t)x=Q(t)$ | linear in $x$ | IF $=e^{\int P\,\mathrm dt}$ |

---

# Part A: Worked examples

## Example 10.14: $t^2\dot x=x^2+xt$ (homogeneous type)
Divide by $t^2$: $\dot x=\big(\tfrac xt\big)^2+\tfrac xt$. This is a function of $x/t$ only. Put $x=vt$, so $\dot x=v+t\dot v$:
$$v+t\dot v=v^2+v\ \Rightarrow\ t\dot v=v^2\ \Rightarrow\ \int\frac{\mathrm dv}{v^2}=\int\frac{\mathrm dt}t\ \Rightarrow\ -\frac1v=\ln t+C$$
$$\boxed{x=\frac{t}{A-\ln t}}$$

## Example 10.16: $(\ln\sin t-3x^2)\dot x+x\cot t+4t=0$ (exact)
Here $f=\ln\sin t-3x^2$ and $g=x\cot t+4t$.

**Test**: $\dfrac{\partial f}{\partial t}=\cot t$ and $\dfrac{\partial g}{\partial x}=\cot t$. They are equal, so the equation is **exact** ✔.

**Find $F$** with $F_x=f$ and $F_t=g$:
- Integrate $f$ with respect to $x$: $F=x\ln\sin t-x^3+h(t)$.
- Then $F_t=x\cot t+h'(t)$. This must equal $x\cot t+4t$, so $h'=4t$ and $h=2t^2$.

$$\boxed{x\ln\sin t-x^3+2t^2=C}$$
The solution is left implicit, which is normal for exact equations.

## Example 10.17: $\dot x+tx=t$ (linear, integrating factor)
The integrating factor is $\mu=e^{\int t\,\mathrm dt}=e^{t^2/2}$. Multiplying through turns the left side into an exact derivative:
$$\frac{\mathrm d}{\mathrm dt}\big(xe^{t^2/2}\big)=te^{t^2/2}\ \Rightarrow\ xe^{t^2/2}=e^{t^2/2}+C$$
$$\boxed{x=1+Ce^{-t^2/2}}$$
Every solution decays to the equilibrium $x=1$. (The equation is also separable: $\dot x=t(1-x)$.)

---

# Part B: Assigned exercises

## Exercise 18(b): $x^2\dot x=\dfrac{t^3+x^3}{t}$
Divide by $x^2$: $\dot x=\dfrac{t^2}{x^2}+\dfrac xt$. Every term depends only on $x/t$, so it is homogeneous. Put $x=vt$:
$$v+t\dot v=\frac1{v^2}+v\ \Rightarrow\ v^2\,\mathrm dv=\frac{\mathrm dt}t\ \Rightarrow\ \tfrac13v^3=\ln t+c$$
$$\boxed{x^3=t^3(3\ln t+C)}\quad\text{i.e. }x=t\,(3\ln t+C)^{1/3}$$

## Exercise 20(d): $t\dot x=x+t\tan(x/t)$
$\dot x=\frac xt+\tan\frac xt$. With $x=vt$:
$$t\dot v=\tan v\ \Rightarrow\ \int\cot v\,\mathrm dv=\int\frac{\mathrm dt}t\ \Rightarrow\ \ln|\sin v|=\ln t+c\ \Rightarrow\ \sin v=At$$
$$\boxed{x=t\sin^{-1}(At)}$$

## Exercise 21(b): $xt\dot x=2(x^2+t^2)$, $x(2)=-1$
$\dot x=\dfrac{2x}t+\dfrac{2t}x$. With $x=vt$:
$$t\dot v=v+\frac2v=\frac{v^2+2}v\ \Rightarrow\ \int\frac{v\,\mathrm dv}{v^2+2}=\int\frac{\mathrm dt}t\ \Rightarrow\ \tfrac12\ln(v^2+2)=\ln t+c\ \Rightarrow\ v^2+2=At^2$$
So $x^2=At^4-2t^2$. At $t=2$: $1=16A-8$, so $A=\frac9{16}$. Since $x(2)<0$, take the negative root:
$$\boxed{x=-t\sqrt{\tfrac{9}{16}t^2-2}=-\tfrac t4\sqrt{9t^2-32}}$$
This is valid for $t>\sqrt{32}/3\approx1.886$.

## Exercise 23(e): $(x-t)\dot x-x+t-1=0$
Here $f=x-t$ and $g=-x+t-1$.

**Test**: $\partial f/\partial t=-1=\partial g/\partial x$, so it is **exact** ✔.

**Find $F$**:
- $F_x=x-t$ gives $F=\tfrac12x^2-tx+h(t)$.
- $F_t=-x+h'(t)=-x+t-1$, so $h=\tfrac12t^2-t$.

So $F=\tfrac12x^2-tx+\tfrac12t^2-t=\tfrac12(x-t)^2-t$, and $F=C$ gives
$$\boxed{(x-t)^2=2t+A\quad\Leftrightarrow\quad x=t\pm\sqrt{2t+A}}$$

## Exercise 24(d): $\cos t\,\dot x-x\sin t+1=0$, $x(0)=2$
Here $f=\cos t$ and $g=-x\sin t+1$.

**Test**: $\partial f/\partial t=-\sin t=\partial g/\partial x$, so it is **exact** ✔. In fact the first two terms are $\frac{\mathrm d}{\mathrm dt}(x\cos t)$.

**Find $F$**: $F=x\cos t+h(t)$, with $h'=1$, so $F=x\cos t+t=C$. The initial condition gives $C=2$:
$$\boxed{x=\frac{2-t}{\cos t}}$$

## Exercise 25(b): $\sqrt t\,\dot x-xt=0$
Here $f=\sqrt t$ and $g=-xt$. Then $\partial f/\partial t=\dfrac1{2\sqrt t}$ but $\partial g/\partial x=-t$. These are not equal, so the equation is **not exact**.

(Although it is not exact, it can still be solved. It is separable: $\dfrac{\dot x}{x}=\sqrt t$, so $\ln x=\tfrac23t^{3/2}+c$, giving $x=Ae^{\frac23t^{3/2}}$. Multiplying by $\frac1{x\sqrt t}$, an integrating factor, would make it exact.)

## Exercise 31(c): $\dot x+2x=e^{-4t}$
The integrating factor is $e^{2t}$:
$$\frac{\mathrm d}{\mathrm dt}\big(xe^{2t}\big)=e^{-2t}\ \Rightarrow\ xe^{2t}=-\tfrac12e^{-2t}+C$$
$$\boxed{x=Ce^{-2t}-\tfrac12e^{-4t}}$$
**Check**: with $x_p=-\frac12e^{-4t}$, $\dot x_p+2x_p=2e^{-4t}-e^{-4t}=e^{-4t}$ ✔.

## Exercise 32(c): $\dot x-\dfrac xt=t^2-3$, $x(1)=-1$
The integrating factor is $e^{-\int\mathrm dt/t}=e^{-\ln t}=\frac1t$:
$$\frac{\mathrm d}{\mathrm dt}\Big(\frac xt\Big)=t-\frac3t\ \Rightarrow\ \frac xt=\tfrac12t^2-3\ln t+C$$
At $t=1$: $-1=\frac12+C$, so $C=-\frac32$.
$$\boxed{x=\tfrac12t^3-3t\ln t-\tfrac32t}$$

## Exercise 33(c): $\dot x+\dfrac{2x}{t}=\cos t$
The integrating factor is $e^{\int2/t\,\mathrm dt}=t^2$:
$$\frac{\mathrm d}{\mathrm dt}(t^2x)=t^2\cos t$$
By parts twice, $\int t^2\cos t\,\mathrm dt=t^2\sin t+2t\cos t-2\sin t$. So
$$\boxed{x=\sin t+\frac{2\cos t}{t}-\frac{2\sin t}{t^2}+\frac{C}{t^2}}$$

---

# Part C: Specimen Test 12

> [!note] Source
> Transcribed from the MATH1054 Module Booklet (the final page of Module 12), then solved and checked with SymPy, NumPy or SciPy.

## Q1: Classify $t\dot x+x=t^3$
Rewrite it as $\dot x=t^2-\frac xt$.

| Heading | Verdict | Reason |
|---|---|---|
| Separable | ✘ | $t^2-x/t$ cannot be written as $f(t)g(x)$ |
| $\dot x=f(x/t)$ | ✘ | the $t^2$ term is not a function of $x/t$ |
| **Exact** | ✔ | In the form $p\dot x+q=0$: $p=t$ and $q=x-t^3$, so $\partial p/\partial t=1=\partial q/\partial x$. In fact $t\dot x+x=\frac{\mathrm d}{\mathrm dt}(tx)$. |
| **Linear** | ✔ | $\dot x+\frac1tx=t^2$ |

## Q2: $\dot x+\frac2tx=t$, $x(1)=\frac14$
The integrating factor is $e^{\int2/t}=t^2$:
$$(t^2x)'=t^3\ \Rightarrow\ t^2x=\tfrac14t^4+C$$
At $t=1$: $\frac14=\frac14+C$, so $C=0$:
$$\boxed{x=\tfrac14t^2}$$

## Q3: $t^2\dot x=tx+x^2$ with $x=yt$
$\dot x=\frac xt+\big(\frac xt\big)^2$. With $x=yt$, $\dot x=y+t\dot y$:
$$y+t\dot y=y+y^2\ \Rightarrow\ \int\frac{\mathrm dy}{y^2}=\int\frac{\mathrm dt}t\ \Rightarrow\ -\frac1y=\ln t+c$$
$$\boxed{x=\frac{t}{C-\ln t}}$$
This is the same equation as Example 10.14.

## Q4: Exactness
The condition for $p(x,t)\dot x+q(x,t)=0$ to be exact is $\dfrac{\partial p}{\partial t}=\dfrac{\partial q}{\partial x}$.

For $(t+e^x)\dot x+2\cos t+x=0$: $\partial_t(t+e^x)=1$ and $\partial_x(2\cos t+x)=1$, so it is **exact** ✔.
- $F_x=t+e^x$ gives $F=tx+e^x+h(t)$.
- $F_t=x+h'(t)=2\cos t+x$ gives $h=2\sin t$.

$$\boxed{tx+e^x+2\sin t=C}$$

## Sources
- Transcribed problem statements: `tmp/md/module_12_differential_equations_ii.md`
- James, *Modern Engineering Mathematics* (6th ed.) §10.5.2–10.5.4; MATH1054 Module Booklet, Module 12
