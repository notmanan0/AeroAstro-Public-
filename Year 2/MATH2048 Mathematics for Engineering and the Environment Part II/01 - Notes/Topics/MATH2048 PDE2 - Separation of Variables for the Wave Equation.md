---
title: "MATH2048 PDE2 - Separation of Variables for the Wave Equation"
module: "MATH2048 Mathematics for Engineering and the Environment Part II"
type: topic
stream: "Block 4: Partial Differential Equations"
order: 11
tags:
  - math2048
  - pdes
  - wave-equation
  - separation-of-variables
aliases: ["MATH2048 Lecture 15", "MATH2048 Lecture 16", "Normal modes", "Six-step method"]
date: 2026-10-30
status: lectured
coverage: "Lecture 15 (30 Oct 2024): separation of variables for the wave equation with fixed ends, why the separated sides are constant, the three-case eigenvalue problem, the general solution and fitting initial data by half-range series. Lecture 16 (4 Nov 2024): the six-step method, x(1 - x) released from rest with Dirichlet ends, then the same problem with Neumann ends. Start of Lecture 17 (5 Nov 2024): the separated solution as left- and right-moving waves. All Ian Hawke."
parent: ["[[MATH2048 Mathematics for Engineering and the Environment Part II Hub]]"]
prerequisites: ["[[MATH2048 PDE1 - Classification of PDEs and the Wave Equation]]", "[[MATH2048 ODE3 - Boundary Value and Eigenvalue Problems]]", "[[MATH2048 FS2 - Even and Odd Functions, Half-Range Series and Convergence]]"]
next_topics: ["[[MATH2048 PDE3 - The Heat Equation]]"]
key_concepts: ["[[Separation of Variables]]", "[[Wave Equation]]", "[[ODE Eigenvalue Problems]]", "[[Half-Range Expansions]]"]
tutorial_sheets: ["[[MATH2048 Problem Sheets 6-7 Solutions - PDEs]]"]
sources: ["02 - Sources/Lectures/MATH2048 Lecture 15.txt", "02 - Sources/Lectures/MATH2048 Lecture 16.txt", "02 - Sources/Lectures/MATH2048 Lecture 17.txt", "02 - Sources/Lectures & Problem Sheets/PDEs/Lecture15_Hyperbolic2.pdf", "02 - Sources/Lectures & Problem Sheets/PDEs/Lecture16_Hyperbolic3.pdf"]
---

# MATH2048 PDE2 - Separation of Variables for the Wave Equation

> [!abstract] Summary
> Separation of variables guesses solutions of the form $y=X(x)T(t)$. Substituting into $y_{tt}=c^2y_{xx}$ and dividing by $XT$ leaves a function of $t$ equal to a function of $x$, so both equal a constant $\lambda$, and the PDE splits into two ODEs. The spatial ODE with the boundary conditions is an eigenvalue problem: fixed ends allow only $\lambda_n=-(n\pi/L)^2$ with modes $\sin\frac{n\pi x}L$, and free (Neumann) ends give $\cos\frac{n\pi x}L$ plus a constant mode at $\lambda=0$. Adding all the modes gives the general solution, and the initial displacement and velocity fix its coefficients through half-range Fourier series.

> [!summary]- Exam use: quick path
> - **Use it when:** a linear homogeneous PDE on a finite interval has homogeneous boundary conditions; exam question A2 every year (2025/26: a damped wave equation).
> - **Assumptions:** linear and homogeneous PDE and boundary conditions; constant coefficients; initial data that can be expanded in the eigenfunctions.
> - **Method:** 1. Substitute $y=X(x)T(t)$, divide by $XT$, set both sides to $\lambda$. 2. Turn the boundary conditions on $y$ into conditions on $X$. 3. Solve the eigenvalue problem in the three cases $\lambda=0$, $\lambda>0$, $\lambda<0$. 4. Solve for $T_n$ with each allowed $\lambda_n$, then superpose $\sum X_nT_n$. 5. Fit the initial data with Fourier series.
> - **Common mistakes:** skipping the $\lambda=0$ case, which is a real mode with Neumann ends; multiplying $X_n$ by a $T_m$ with a different index.
> - **Practise:** [[#Guitar string with fixed ends (L16)]] · [[#4. The 2025-26 exam, question A2]] · [[MATH2048 Problem Sheets 6-7 Solutions - PDEs|PS6]]

PDE1 showed that the wave equation splits a pulse into left- and right-moving waves. The aim now is a method that works for any initial data and copes with boundaries, where waves bounce off walls (L15, ll. 11–14). Separation of variables is that method, and the lecturer called it "absolutely central to this unit". It follows the ODE strategy from [[MATH2048 ODE1 - Second-Order Linear ODEs with Constant Coefficients|ODE1]]: guess a form of solution, find which guesses work, and add them all up, because the equation is linear (ll. 16–21). Only the guess is more elaborate.

Everything earlier in the module comes back. The separated spatial problem is an eigenvalue problem from [[MATH2048 ODE3 - Boundary Value and Eigenvalue Problems|ODE3]], its solutions are the sines and cosines of Fourier series, and fitting the initial data is a half-range expansion from [[MATH2048 FS2 - Even and Odd Functions, Half-Range Series and Convergence|FS2]].

---

## 1. Separating the wave equation (L15)

Solve $y_{tt}=c^2y_{xx}$ on $0<x<L$. The guess is that interesting solutions are products of a function of space alone and a function of time alone (ll. 22–33):

$$
y(x,t)=X(x)\,T(t).
$$

Each partial derivative acts on only one factor. Using dots for time derivatives and primes for space derivatives,

$$
y_{tt}=X\ddot T,\qquad y_{xx}=X''T .
$$

Move $c^2$ to the left of the wave equation and substitute:

$$
\frac1{c^2}X\ddot T=X''T .
$$

Now the step that looks pointless (ll. 44–61): divide by $y=XT$.

$$
\frac1{c^2}\frac{\ddot T}{T}=\frac{X''}{X}.
$$

The left side depends only on $t$ and the right side only on $x$.

### Why the two sides must be constant

Call the left side $F(t)$ and the right side $G(x)$, so $F(t)=G(x)$ for all $x$ and $t$ (ll. 62–90). Fix $t=\tau$. Along that line, $F(\tau)$ is a single number, yet it equals $G(x)$ for every $x$, so $G$ is constant. Fixing $x$ instead shows that $F$ is constant. A function of one independent variable can equal a function of another only if both are the same constant, the separation constant $\lambda$:

$$
\frac1{c^2}\frac{\ddot T}{T}=\lambda=\frac{X''}{X}.
$$

This gives two ODEs (ll. 91–109):

$$
X''-\lambda X=0,\qquad\ddot T-\lambda c^2T=0 .
$$

They are coupled through $\lambda$, which is not yet known. The wave speed is put with $T$ on purpose, so that the spatial problem has as few parameters as possible and looks the same for every PDE with $\partial_x^2$ in it (L17, ll. 214–215).

### Boundary conditions on X

With fixed (Dirichlet) ends, $y(0,t)=0$ for all $t$, so $X(0)T(t)=0$ (ll. 110–126). A product is zero only if a factor is. $T\equiv0$ would make $y\equiv0$, which is no use, so $X(0)=0$. Likewise $X(L)=0$. The spatial problem is

$$
X''-\lambda X=0,\qquad X(0)=X(L)=0,
$$

exactly the eigenvalue problem of ODE3: it has non-zero solutions only for special values of $\lambda$ (ll. 127–136).

### Solving the eigenvalue problem: three cases

The auxiliary equation is $m^2-\lambda=0$, so $m=\pm\sqrt\lambda$, and the sign of $\lambda$ is unknown (ll. 137–148).

**$\lambda=0$.** $X''=0$ gives $X=A+Bx$. Then $X(0)=A=0$, and $X(L)=BL=0$ gives $B=0$. Only the zero solution, so ignore it (ll. 149–171).

**$\lambda=k^2>0$.** $X=Ce^{kx}+De^{-kx}$. $X(0)=C+D=0$ gives $D=-C$. Then (ll. 177–198)

$$
X(L)=C\big(e^{kL}-e^{-kL}\big)=0 .
$$

With $k>0$ and $L>0$, $e^{kL}>1>e^{-kL}$, so the bracket is positive and $C=0$. Only the zero solution again.

**$\lambda=-k^2<0$.** The roots are $\pm jk$, so $X=E\cos kx+F\sin kx$ (ll. 200–253). $X(0)=E=0$. Then $X(L)=F\sin kL=0$. $F=0$ is the zero solution, so instead $\sin kL=0$. Sine vanishes only at integer multiples of $\pi$, so

$$
k=\frac{n\pi}L,\qquad\lambda_n=-\Big(\frac{n\pi}L\Big)^2,\qquad X_n=\sin\frac{n\pi x}L,\qquad n=1,2,3,\dots
$$

Negative $n$ give the same functions up to sign, and $n=0$ gives zero. Each mode is a sine wave that fits exactly into the string: half a wavelength for $n=1$, a whole one for $n=2$, and so on.

### Solving for T and adding up the modes

Only the allowed $\lambda_n$ matter, so solve the $T$ equation just for those (ll. 255–278). With $\lambda_n=-(n\pi/L)^2$ the two minus signs cancel:

$$
\ddot T_n+\Big(\frac{n\pi c}L\Big)^2T_n=0 .
$$

The roots are $m=\pm j\frac{n\pi c}L$, so

$$
T_n=C_n\cos\frac{n\pi ct}L+D_n\sin\frac{n\pi ct}L .
$$

Each product $y_n=X_nT_n$ satisfies the PDE and the boundary conditions. The indices must match, because $X_n$ and $T_n$ are tied by the same $\lambda_n$ (ll. 279–299). The wave equation is linear, so any sum of solutions is a solution, and adding all of them gives the general solution (ll. 306–322):

$$
y(x,t)=\sum_{n=1}^\infty\sin\frac{n\pi x}L\Big[C_n\cos\frac{n\pi ct}L+D_n\sin\frac{n\pi ct}L\Big].
$$

Mode $n$ oscillates at angular frequency $n\pi c/L$, an integer multiple of the fundamental: this is why a guitar string has harmonics. $c$ and $L$ are just numbers you can change freely, but changing the boundary conditions changes the eigenfunctions, and the whole procedure has to be redone (ll. 324–328).

### Fitting the initial data

Given the initial displacement $y(x,0)=f(x)$ and velocity $y_t(x,0)=g(x)$, set $t=0$ (ll. 334–352). $\cos0=1$ and $\sin0=0$, so

$$
f(x)=\sum_{n=1}^\infty C_n\sin\frac{n\pi x}L .
$$

This is the Fourier sine series of $f$, so the half-range formula gives

$$
C_n=\frac2L\int_0^Lf(x)\sin\frac{n\pi x}L\,dx .
$$

For the velocity, differentiate the general solution in $t$ term by term and set $t=0$ (ll. 353–373):

$$
g(x)=\sum_{n=1}^\infty\frac{n\pi c}L\,D_n\sin\frac{n\pi x}L,\qquad\frac{n\pi c}LD_n=\frac2L\int_0^Lg(x)\sin\frac{n\pi x}L\,dx .
$$

Every constant is now fixed.

## 2. The six-step method (L16)

Lecture 16 set the procedure out as six steps that work for most linear homogeneous second-order PDEs in one space dimension (ll. 7–27). In higher dimensions there is one function per variable and the steps get longer but no harder.

1. Substitute $y=X(x)T(t)$ into the PDE and separate into ODEs with a constant $\lambda$.
2. Turn the spatial boundary conditions on $y$ into conditions on $X$.
3. Solve the eigenvalue problem for $X$, case by case.
4. Solve the $T$ equation for each allowed $\lambda_n$.
5. Superpose $\sum X_nT_n$ to get the general solution.
6. Fix the coefficients from the initial conditions.

Step 1 depends only on the PDE, and step 2 only on the boundary conditions, which is what lets you see what changes between problems (ll. 349–359).

### Guitar string with fixed ends (L16)

Solve $y_{tt}=c^2y_{xx}$ on $0<x<1$ with $y(0,t)=y(1,t)=0$, $y(x,0)=x(1-x)$ and $y_t(x,0)=0$, a string pulled into a parabola and released from rest (ll. 28–38). The initial data happen to satisfy the boundary conditions. That isn't required, since the boundary conditions apply only for $t>0$, but it makes the solution better behaved (ll. 34–36).

Steps 1–5 are Lecture 15 with $L=1$ (ll. 39–207): $\lambda_n=-(n\pi)^2$, $X_n=\sin n\pi x$, and

$$
y=\sum_{n=1}^\infty\big[A_n\cos n\pi ct+B_n\sin n\pi ct\big]\sin n\pi x .
$$

For step 6 take the easier condition first, the zero velocity (ll. 216–254):

$$
y_t(x,0)=\sum_{n=1}^\infty n\pi c\,B_n\sin n\pi x=0 .
$$

This is a sine series for the zero function. A function's Fourier coefficients are unique, so if a guess matches both sides it is the answer, with no integrals needed: $B_n=0$ for every $n$. The same shortcut works whenever the data is already a finite sum of modes, so $y_t(x,0)=\sin3\pi x$ would make every coefficient zero except the one multiplying $\sin3\pi x$ (ll. 248–252).

The displacement gives the sine series of $x(1-x)$ (ll. 255–274):

$$
A_n=2\int_0^1x(1-x)\sin n\pi x\,dx .
$$

Integrate by parts, differentiating the polynomial:

$$
A_n=2\left(\left[-x(1-x)\frac{\cos n\pi x}{n\pi}\right]_0^1+\int_0^1(1-2x)\frac{\cos n\pi x}{n\pi}\,dx\right).
$$

The bracket vanishes because $x(1-x)$ is zero at both ends. Integrate by parts again:

$$
A_n=2\left(\left[(1-2x)\frac{\sin n\pi x}{(n\pi)^2}\right]_0^1+\int_0^1\frac{2\sin n\pi x}{(n\pi)^2}\,dx\right).
$$

The bracket vanishes because $\sin n\pi=0$. The last integral gives (ll. 298–305)

$$
A_n=-\frac{4}{(n\pi)^3}\Big[\cos n\pi x\Big]_0^1=\frac{4}{(n\pi)^3}\big(1-(-1)^n\big).
$$

So $A_n=\frac8{(n\pi)^3}$ for odd $n$ and zero for even $n$, and

$$
y(x,t)=\sum_{n=1}^\infty\frac{4\big(1-(-1)^n\big)}{(n\pi)^3}\cos n\pi ct\,\sin n\pi x .
$$

> [!check] SymPy
> The coefficients are $\frac8{\pi^3}$, $0$, $\frac8{27\pi^3}$ for $n=1,2,3$, and 200 terms of the series at $t=0$, $x=0.3$ give $0.21000$, matching $0.3\times0.7$. The even modes vanish because $x(1-x)$ is symmetric about the middle of the string, while $\sin n\pi x$ for even $n$ is antisymmetric about it.

The process is long but mechanical (ll. 323–329): it works for any initial data, many boundary conditions and many linear PDEs, provided the spatial part with its boundary conditions gives an eigenvalue problem you can solve.

### Changing to Neumann ends (L16)

Now keep everything except the boundary conditions, which become $y_x(0,t)=y_x(1,t)=0$ (ll. 331–433). For a string this means ends free to slide vertically, and for sound in a pipe, open ends.

Step 1 is unchanged, since it depends only on the PDE. In step 2, $y_x=X'T$, so the conditions become $X'(0)=X'(1)=0$. In step 3 the general solutions in each case are the same, because the ODE is the same, but the boundary conditions now pick out different solutions (ll. 360–406).

**$\lambda=0$.** $X=A+Bx$ gives $X'=B$, and $X'(0)=X'(1)=0$ only says $B=0$. $A$ is free, so $\lambda_0=0$ with $X_0=$ constant is a genuine mode. With fixed ends there was nothing here.

**$\lambda>0$.** As before, only the zero solution; checking this was left as an exercise (l. 392). With $X=Ce^{kx}+De^{-kx}$, $X'(0)=k(C-D)=0$ gives $D=C$, then $X'(1)=kC(e^k-e^{-k})=0$ forces $C=0$.

**$\lambda=-k^2<0$.** $X=E\cos kx+F\sin kx$, so $X'=k(-E\sin kx+F\cos kx)$. $X'(0)=kF=0$ gives $F=0$, and $X'(1)=-kE\sin k=0$ gives $k=n\pi$ again. The eigenvalues are the same as before, but now the cosine survives: $X_n=\cos n\pi x$.

Step 4 for $n\geq1$ is unchanged, since it depends only on the PDE and $\lambda_n$. The new $\lambda_0=0$ mode has $\ddot T_0=0$, so $T_0=Gt+H$, a linear function of time (ll. 407–416). The general solution is

$$
y=Gt+H+\sum_{n=1}^\infty\big[C_n\cos n\pi ct+D_n\sin n\pi ct\big]\cos n\pi x .
$$

The $Gt$ term is the whole string drifting sideways at a steady speed, which free ends allow. Zero initial velocity gives $G=0$ and every $D_n=0$ by uniqueness (ll. 426–428). The displacement gives the cosine series of $x(1-x)$, where the constant term needs care: with the usual $\frac12a_0$ convention, $H=\frac12a_0$ (ll. 429–433). The integrals are the ones worked in [[MATH2048 PDE3 - The Heat Equation|PDE3]]:

$$
H=\int_0^1x(1-x)\,dx=\frac16,\qquad C_n=2\int_0^1x(1-x)\cos n\pi x\,dx=-\frac{2\big(1+(-1)^n\big)}{(n\pi)^2}.
$$

So

$$
y=\frac16-\sum_{n=1}^\infty\frac{2\big(1+(-1)^n\big)}{(n\pi)^2}\cos n\pi ct\,\cos n\pi x,
$$

in which only even $n$ survive. The constant $\frac16$ is the mean displacement, which stays put. Forgetting the $\lambda=0$ case loses it.

![[m2048_pde_wave_modes.png|900]]

> [!check] SymPy
> $C_2=-\frac1{\pi^2}$, $C_4=-\frac1{4\pi^2}$, odd $C_n=0$, and 200 terms of the cosine series at $x=0.3$ give $0.21001$.

## 3. Standing waves are travelling waves (L17)

The start of Lecture 17 links the separated solution back to waves moving at speed $c$ (ll. 6–28). By the product-to-sum formula,

$$
\cos n\pi x\cos n\pi ct=\tfrac12\Big[\cos n\pi(x-ct)+\cos n\pi(x+ct)\Big].
$$

The first term is constant along lines $x-ct=$ const, which move right at speed $c$, and the second along $x+ct=$ const, which move left. Each standing mode is two equal waves travelling in opposite directions. The same identity works with fixed ends, $\sin n\pi x\cos n\pi ct=\frac12[\sin n\pi(x-ct)+\sin n\pi(x+ct)]$. The difference is what happens at the ends: a fixed end reflects a wave upside down and a free end reflects it the right way up, so in both cases the left- and right-moving waves keep turning into each other.

The plucked string of PS6 Q1 shows this clearly. The triangle splits into two half-height triangles moving apart at speed $c$; what you see is a flat top whose corners run outwards, reflect inverted off the fixed ends, and reassemble as an upside-down triangle at $t=L/c$. After $t=2L/c$, one full period of the fundamental, the string is back where it started.

![[m2048_pde_plucked_string.png|720]]

## 4. The 2025-26 exam, question A2

The exam's A2 is this method applied to a variant of the lectured PDE; the solutions note "damped term not seen in classes". Solve

$$
u_{tt}+2\gamma u_t=u_{xx},\qquad0<x<\pi,\quad0<\gamma<1,
$$

with $u(t,0)=u(t,\pi)=0$, $u_t(0,x)=0$ and $u(0,x)=\sin x$. The exam writes $u(t,x)$, time first.

Substituting $u=X(x)T(t)$ and dividing by $XT$:

$$
\frac{\ddot T}{T}+2\gamma\frac{\dot T}{T}=\frac{X''}{X}=\lambda ,
$$

so $X''-\lambda X=0$ and $\ddot T+2\gamma\dot T-\lambda T=0$. The damping only touches the $T$ equation, so the eigenvalue problem is the fixed-end one with $L=\pi$: $\lambda_n=-n^2$ and $X_n=\sin nx$.

For $T_n$, the auxiliary equation is $m^2+2\gamma m+n^2=0$, so

$$
m=-\gamma\pm j\sqrt{n^2-\gamma^2},
$$

complex because $n\geq1>\gamma$. Write $\omega_n=\sqrt{n^2-\gamma^2}$, so $T_n=e^{-\gamma t}(P\sin\omega_nt+Q\cos\omega_nt)$. Zero initial velocity needs $\dot T_n(0)=P\omega_n-\gamma Q=0$, so $Q=P\omega_n/\gamma$, and $\omega_n/\gamma=\sqrt{(n/\gamma)^2-1}$:

$$
u=\sum_{n=1}^\infty C_n\sin nx\,e^{-\gamma t}\Big[\sin\omega_nt+\sqrt{(n/\gamma)^2-1}\,\cos\omega_nt\Big].
$$

At $t=0$ the bracket is $\sqrt{(n/\gamma)^2-1}$, so matching $u(0,x)=\sin x$ by uniqueness gives $C_n=0$ for $n\geq2$ and

$$
C_1\sqrt{\frac1{\gamma^2}-1}=1\quad\Longrightarrow\quad C_1=\frac{\gamma}{\sqrt{1-\gamma^2}} .
$$

> [!check] SymPy
> $T_n$ satisfies $\ddot T_n+2\gamma\dot T_n+n^2T_n=0$ with $\dot T_n(0)=0$ exactly.

## Transcript slips

> [!warning] Lectures 15–17
> | Where | Transcript says | Correct |
> |---|---|---|
> | L15, l. 31 | $y_{tt}$ "is equal to x" times $\ddot T$ | $X(x)\ddot T$, big $X$ |
> | L15, l. 117 | "separation ANZAT" (and "ANZATS" elsewhere) | ansatz, the assumed form |
> | L15, l. 372 | $D_n\frac{n\pi c}L=\frac2L\int_0^Lg\sin\frac{n\pi c}Lx\,dx$ | $\sin\frac{n\pi x}L$, no $c$ inside the sine |
> | L16, l. 66 | $\ddot T-c^2T=0$, "I missed off the lambda" | $\ddot T-\lambda c^2T=0$ |
> | L16, l. 144 | "T goes as e to the mx" | $e^{mt}$ |
> | L16, l. 252 | "match up left and wrong" | left and right |
> | L16, l. 387 | "Richelieu boundary conditions" | Dirichlet |
> | L17, ll. 22–28 | homogeneous Neumann conditions "precisely correspond" to left- and right-moving waves, and with Dirichlet conditions "it wouldn't work" | both decompose into travelling waves; the ends differ in reflecting waves inverted (fixed) or upright (free); see §3 |

## Links

- Parent: [[MATH2048 Mathematics for Engineering and the Environment Part II Hub]] · Previous: [[MATH2048 PDE1 - Classification of PDEs and the Wave Equation]] · Next: [[MATH2048 PDE3 - The Heat Equation]]
- Concepts: [[Separation of Variables]] · [[Wave Equation]] · [[ODE Eigenvalue Problems]] · [[Half-Range Expansions]] · [[Fourier Series]]
- Practice: [[MATH2048 Problem Sheets 6-7 Solutions - PDEs]] · [[MATH2048 Past Paper Solutions]]

## Sources

- Lecture 15 (30 Oct 2024), Lecture 16 (4 Nov 2024) and the start of Lecture 17 (5 Nov 2024), Ian Hawke: `MATH2048 Lecture 15.txt`, `MATH2048 Lecture 16.txt`, `MATH2048 Lecture 17.txt`
- Slides `Lecture15_Hyperbolic2.pdf`, `Lecture16_Hyperbolic3.pdf`; lecture notes §5.4
- Problem Sheet 6; 2025/26 exam question A2 and its published solutions

## Self-study tasks

Lecture 16 left the $\lambda>0$ case with Neumann ends to "check for yourself" (l. 392) and the Neumann coefficient calculation to the slides (l. 433). Lecture 15 promised "many more examples" (l. 382), which are Problem Sheet 6.

### Core

- [ ] Lecturer-set (L16, l. 392): show that $\lambda>0$ gives only the zero solution with Neumann ends. → [[#Changing to Neumann ends (L16)]]
- [ ] Lecturer-set (L16, l. 433): compute $H$ and $C_n$ for the Neumann problem. Answers: $\frac16$ and $-\frac{2(1+(-1)^n)}{(n\pi)^2}$. → [[#Changing to Neumann ends (L16)]]
- [ ] PS6 Q1: a string plucked into a triangle of height $h$ at $L/2$, released from rest, $c=1$. Answer: $y=\frac{8h}{\pi^2}\sum_{n\text{ odd}}\frac{(-1)^{(n-1)/2}}{n^2}\sin\frac{n\pi x}L\cos\frac{n\pi t}L$. → [[MATH2048 Problem Sheets 6-7 Solutions - PDEs]]
- [ ] 2025/26 A2: the damped wave equation, all four parts. → [[#4. The 2025-26 exam, question A2]]

### Further practice

- [ ] PS6 Q2: an antisymmetric "Z" displacement released from rest. Answer: only even modes, $y=\sum_k\frac{2\alpha}{k\pi}(-1)^{k+1}\sin\frac{2k\pi x}L\cos\frac{2k\pi ct}L$. → [[MATH2048 Problem Sheets 6-7 Solutions - PDEs]]
- [ ] Redo the fixed-end example with $y(x,0)=0$ and $y_t(x,0)=\sin3\pi x$, using the uniqueness shortcut. Answer: $y=\frac{1}{3\pi c}\sin3\pi ct\,\sin3\pi x$ (suggested, not lecturer-set). → [[#Guitar string with fixed ends (L16)]]
