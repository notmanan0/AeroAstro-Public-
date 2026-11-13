---
title: "MATH2048 ODE2 - Euler Equations and Inhomogeneous ODEs"
module: "MATH2048 Mathematics for Engineering and the Environment Part II"
type: topic
stream: "Block 1: Ordinary Differential Equations"
order: 2
tags:
  - math2048
  - odes
  - euler-equation
  - undetermined-coefficients
aliases: ["MATH2048 Lecture 2", "Euler equations", "Undetermined coefficients"]
date: 2026-10-30
status: lectured
coverage: "Lecture 2 (1 Oct 2024, Ian Hawke): Euler equations and the pulsating-star example, the t = ln x substitution, the method of undetermined coefficients and clashes with the complementary function; the correction at the start of Lecture 3. The resonance slide (L3 slide 18) was on the slides but not talked through."
parent: ["[[MATH2048 Mathematics for Engineering and the Environment Part II Hub]]"]
prerequisites: ["[[MATH2048 ODE1 - Second-Order Linear ODEs with Constant Coefficients]]"]
next_topics: ["[[MATH2048 ODE3 - Boundary Value and Eigenvalue Problems]]"]
key_concepts: ["[[Euler-Cauchy Equation]]", "[[Method of Undetermined Coefficients]]", "[[Resonance]]", "[[Auxiliary Equation]]"]
tutorial_sheets: ["[[MATH2048 Problem Sheets 1-2 Solutions - ODEs]]"]
sources: ["02 - Sources/Lectures/MATH2048 Lecture 2.txt", "02 - Sources/Lectures/MATH2048 Lecture 3.txt (ll. 1-18)", "02 - Sources/Lectures & Problem Sheets/ODEs/Lecture2_ODE.pdf", "02 - Sources/Lectures & Problem Sheets/ODEs/Lecture3_ODE.pdf (slide 18)", "02 - Sources/Lectures & Problem Sheets/ODEs/Appendix_Lecture1-2_(ODEs).pdf", "02 - Sources/Lectures & Problem Sheets/LectureNotesMATH2048.pdf (§1.1.1-1.1.2)"]
---

# MATH2048 ODE2 - Euler Equations and Inhomogeneous ODEs

> [!abstract] Summary
> Euler equations $ax^2y''+bxy'+cy=0$ have each derivative multiplied by the matching power of $x$, so the guess $y=x^n$ gives the quadratic $an^2+(b-a)n+c=0$; for repeated or complex roots the substitution $t=\ln x$ turns them into constant-coefficient ODEs, which is why repeated roots bring in $\ln x$. Inhomogeneous ODEs are solved as complementary function plus particular integral, with the particular integral found by the method of undetermined coefficients, multiplying the guess by $x$ whenever it clashes with the complementary function.

> [!summary]- Exam use: quick path
> - **Use it when:** an ODE has $x^2y''$, $xy'$ and $y$ terms (Euler, often from polar or spherical coordinates), or has a polynomial, exponential or sine/cosine source.
> - **Assumptions:** Euler equations on $x>0$ (so $x^n$ and $\ln x$ are real); undetermined coefficients needs constant coefficients and a source made of polynomials, exponentials and sines/cosines.
> - **Method:** 1. Solve the homogeneous problem (ODE1 table, or the Euler table in §1). 2. Guess the particular integral from the source (table in §2). 3. If any term of the guess is in the complementary function, multiply by $x$ until it isn't. 4. Substitute and match coefficients. 5. Add complementary function and particular integral, then apply any conditions.
> - **Common mistakes:** writing $bn$ instead of $(b-a)n$ in the Euler auxiliary equation; trying $Ce^{kx}$ when $e^{kx}$ is already a complementary function, which can never balance.
> - **Practise:** [[#Clashes with the complementary function]] · [[MATH2048 Problem Sheets 1-2 Solutions - ODEs#Q3: Undetermined coefficients|PS1 Q3]]

The reason for studying Euler equations is dimensions. In $ay''+by'+cy=0$, if $y$ is a temperature and $x$ a length, the three terms have units of temperature per length squared, per length, and temperature, so either $a$, $b$ and $c$ carry units or the equation has been non-dimensionalised. The other way to make the units agree is to multiply each derivative by the matching power of the length itself: $x^2y''$, $xy'$ and $y$ all have the same units, and that is an Euler equation. Cartesian problems tend to give constant-coefficient equations, and cylindrical or spherical ones tend to give Euler equations (or Bessel's), because the radius is the natural length scale.

Because each $x$-derivative of $x^n$ loses one power of $x$, and the equation hands it straight back, a power of $x$ plays the role the exponential played in ODE1. The connection is exact: with $x=e^t$, a power $x^n$ is the exponential $e^{nt}$, so an Euler equation in $x$ is a constant-coefficient equation in $t=\ln x$ in disguise. That one substitution explains both the guess and what to do when the roots repeat.

For a source on the right-hand side, any particular integral will do (ODE1). The method of undetermined coefficients is the quick way to find one: guess a function of the same shape as the source, with unknown coefficients, and let the equation fix them. It covers the sources that turn up in practice, and when it fails, stop and use variation of parameters or computer algebra.

---

## 1. Euler equations

The general Euler equation is

$$
ax^2y''+bxy'+cy=0\qquad(x>0,\ a,b,c\ \text{constant}).
$$

Guess a power:

$$
y=x^n.
$$

Each derivative lowers the power by one:

$$
y'=nx^{n-1},\qquad y''=n(n-1)x^{n-2}.
$$

Substitute; the $x^2$ and $x$ in the equation restore the lost powers:

$$
an(n-1)x^n+bnx^n+cx^n=0
$$

$$
\big[an^2+(b-a)n+c\big]x^n=0.
$$

For $x>0$, $x^n\neq0$, so

$$
an^2+(b-a)n+c=0.
$$

This is the Euler auxiliary equation. Compared with the constant-coefficient one, the $n^2$ and constant terms are the same and only the linear coefficient changes, from $b$ to $b-a$. Writing $n(n-1)$ out explicitly before collecting terms is the safest way not to drop the $-a$.

| Roots of $an^2+(b-a)n+c=0$ | General solution |
|---|---|
| real, distinct $n_1\neq n_2$ | $c_1x^{n_1}+c_2x^{n_2}$ |
| real, repeated $n$ | $x^n(c_1+c_2\ln x)$ |
| complex, $\alpha\pm j\beta$ | $x^\alpha\big[c_1\cos(\beta\ln x)+c_2\sin(\beta\ln x)\big]$ |

### The pulsating star

The worked example is a model for radial pulsations of a star. A spherically symmetric fluid body under its own gravity, pulsing in and out as $e^{j\ell t}$, has a spatial part $X(r)$ satisfying

$$
\frac1r\frac{d^2}{dr^2}\big[rX\big]-\frac{\ell(\ell+1)}{r^2}X=0.
$$

Multiply through by $r^2$:

$$
r\frac{d^2}{dr^2}\big[rX\big]-\ell(\ell+1)X=0.
$$

Expand $(rX)''$ with the product rule twice. Once:

$$
(rX)'=X+rX'.
$$

Twice:

$$
(rX)''=X'+X'+rX''=rX''+2X'.
$$

So

$$
r^2X''+2rX'-\ell(\ell+1)X=0,
$$

an Euler equation in $r$ with $a=1$, $b=2$ and $c=-\ell(\ell+1)$. With $X=r^n$ the auxiliary equation is

$$
n^2+(2-1)n-\ell(\ell+1)=0
$$

$$
n^2+n-\ell(\ell+1)=0
$$

$$
(n-\ell)(n+\ell+1)=0,
$$

so $n=\ell$ or $n=-(\ell+1)$, two distinct real roots, and

$$
X(r)=c_1r^\ell+\frac{c_2}{r^{\ell+1}}.
$$

> [!check] The quadrupole case, $\ell=2$
> The powers are $r^2$ and $r^{-3}$. For $X=r^{-3}$: $X'=-3r^{-4}$, $X''=12r^{-5}$, so $r^2X''+2rX'-6X=12r^{-3}-6r^{-3}-6r^{-3}=0$. For $X=r^2$: $2r^2+4r^2-6r^2=0$.

Physical conditions can kill whole solutions without any boundary value being given, as they do throughout the PDE block. For a star, $r$ runs down to the centre and $X$ must stay finite there, so $c_2=0$. For the field of a charged particle, valid out to $r\to\infty$, it is $c_1$ that must vanish instead. The same pair of powers reappears for Laplace's equation in polar coordinates.

### Repeated or complex roots: the substitution t = ln x

$x^n$ with a complex $n$ is awkward, and it isn't obvious what replaces "multiply by $x$" for a repeated root. Changing the independent variable removes both difficulties. Let

$$
t=\ln x,\qquad x=e^t,\qquad \frac{dt}{dx}=\frac1x,
$$

and write a dot for $d/dt$. The first derivative, by the chain rule:

$$
y'=\frac{dy}{dt}\frac{dt}{dx}=\frac1x\,\dot y,
$$

so

$$
xy'=\dot y.
$$

The second derivative, by the product rule on $\frac1x\cdot\dot y$, remembering that $\dot y$ depends on $x$ through $t$:

$$
y''=\frac{d}{dx}\Big(\frac1x\,\dot y\Big)
$$

$$
=-\frac1{x^2}\dot y+\frac1x\frac{d\dot y}{dt}\frac{dt}{dx}
$$

$$
=-\frac1{x^2}\dot y+\frac1{x^2}\ddot y,
$$

so

$$
x^2y''=\ddot y-\dot y.
$$

Substitute into $ax^2y''+bxy'+cy=0$:

$$
a(\ddot y-\dot y)+b\dot y+cy=0
$$

$$
a\ddot y+(b-a)\dot y+cy=0.
$$

This is a constant-coefficient ODE in $t$, and its auxiliary equation $a\lambda^2+(b-a)\lambda+c=0$ is the Euler auxiliary equation with $\lambda=n$. Solve in $t$ with the ODE1 table and convert back: $e^{nt}=x^n$, $te^{nt}=x^n\ln x$ and $e^{\alpha t}\cos\beta t=x^\alpha\cos(\beta\ln x)$. That is where the Euler table comes from, and it is also why the guess $x^n$ works at all. The final answer has to be in $x$; stopping at $y(t)$ loses marks.

In practice the auxiliary equation is tried first, with $\ln x$ rather than $x$ multiplying the second solution for a repeated root, since almost every engineering and mathematical physics problem gives real roots, distinct or repeated. Only complex roots force the full substitution.

### Two worked Euler equations

A repeated root arises in $x^2y''+3xy'+y=0$, which gives

$$
n(n-1)+3n+1=n^2+2n+1=(n+1)^2=0,
$$

so $n=-1$ twice. In $t$ the equation is $\ddot y+2\dot y+y=0$, with solution $(c_1+c_2t)e^{-t}$, and converting back,

$$
y=\frac{c_1+c_2\ln x}{x}.
$$

*(Suggested, not lecturer-set.)* For complex roots, take $x^2y''+xy'+4y=0$. The auxiliary equation is $n(n-1)+n+4=n^2+4=0$, so $n=\pm2j$, with $\alpha=0$ and $\beta=2$. In $t$ it is $\ddot y+4y=0$, so $y=c_1\cos2t+c_2\sin2t$, and in $x$

$$
y=c_1\cos(2\ln x)+c_2\sin(2\ln x).
$$

> [!check] Checking $y_1=\cos(2\ln x)$ directly
> $y_1'=-\frac2x\sin(2\ln x)$ and $y_1''=\frac2{x^2}\sin(2\ln x)-\frac4{x^2}\cos(2\ln x)$, so $x^2y_1''+xy_1'+4y_1=(2\sin-4\cos)-2\sin+4\cos=0$. SymPy's `dsolve` gives the same general solution for both examples.

### Problem Sheet 1, Q2: one Euler equation of each kind

PS1 Q2(a) is $x^2y''-6y=0$, so $a=1$, $b=0$, $c=-6$:

$$
n(n-1)-6=n^2-n-6=(n-3)(n+2)=0,
$$

giving $n=3$ and $n=-2$, two distinct real roots, and $y=c_1x^3+c_2x^{-2}$.

PS1 Q2(b) is $x^2y''+3xy'+10y=0$:

$$
n(n-1)+3n+10=n^2+2n+10=0
$$

$$
n=\frac{-2\pm\sqrt{4-40}}{2}=-1\pm3j .
$$

In $t=\ln x$ the equation is $\ddot y+2\dot y+10y=0$, with solution $e^{-t}(c_1\cos3t+c_2\sin3t)$. Convert back with $e^{-t}=x^{-1}$:

$$
y=\frac1x\big[c_1\cos(3\ln x)+c_2\sin(3\ln x)\big].
$$

PS1 Q2(c) is $x^2y''+5xy'+4y=0$:

$$
n(n-1)+5n+4=n^2+4n+4=(n+2)^2=0,
$$

so $n=-2$ twice and $y=x^{-2}(c_1+c_2\ln x)$. All three agree with SymPy's `dsolve`.

## 2. Inhomogeneous ODEs: complementary function plus particular integral

For $y''+py'+qy=r(x)$ the procedure has three steps:

1. Ignore the source and solve the homogeneous equation for the **complementary functions** $y_1$, $y_2$.
2. Find any **particular integral** $y_P$ that satisfies the full equation.
3. The general solution is $y=c_1y_1+c_2y_2+y_P$; only then apply initial or boundary conditions.

As in ODE1, $y-y_P$ satisfies the homogeneous equation, so every solution has this form and none is missed. It also follows that it doesn't matter which particular integral you find: two of them differ by a solution of the homogeneous equation, which the constants $c_1$, $c_2$ absorb.

### The method of undetermined coefficients

Guess a particular integral of the same form as the source, with unknown coefficients, substitute, and match terms. The logic is balancing: a guess $Ax+B$ against a source $4x$ works because differentiating a polynomial gives lower powers, so the $Ax$ can balance the $4x$ and the $B$ can absorb the constant that differentiation produces, whereas a guess $x^2$ would leave an $x^2$ term with nothing on the right to balance it. An exponential differentiates into itself, so $Ce^{kx}$ balances $e^{kx}$.

| Source $r(x)$ | Guess for $y_P$ |
|---|---|
| polynomial of degree $n$ | general polynomial of degree $n$, $A_nx^n+\dots+A_0$ |
| $e^{kx}$ | $Ce^{kx}$ |
| $\sin\omega x$ or $\cos\omega x$ | $C\sin\omega x+D\cos\omega x$ (always both) |
| $e^{kx}\sin\omega x$ or $e^{kx}\cos\omega x$ | $e^{kx}(C\sin\omega x+D\cos\omega x)$ |
| $x^ne^{kx}$ | $(A_nx^n+\dots+A_0)e^{kx}$ |
| a sum of the above | the sum of the guesses |

Sensible guesses exist only for polynomials, exponentials and simple trigonometric functions, the last being exponentials in disguise through Euler's formula. For logarithms, fractional powers and the like there is no sensible guess, and the method should be abandoned.

### Worked example: matching coefficients

Solve $y''+4y'+4y=4x+25e^{3x}$.

The complementary functions come from $\lambda^2+4\lambda+4=(\lambda+2)^2=0$, a repeated root $\lambda=-2$:

$$
y_1=e^{-2x},\qquad y_2=xe^{-2x}.
$$

The source is a first-degree polynomial plus $e^{3x}$, neither of which appears in the complementary function, so guess

$$
y_P=Ax+B+Ce^{3x}.
$$

Differentiate:

$$
y_P'=A+3Ce^{3x},\qquad y_P''=9Ce^{3x}.
$$

Substitute:

$$
y_P''+4y_P'+4y_P=9Ce^{3x}+4(A+3Ce^{3x})+4(Ax+B+Ce^{3x})
$$

$$
=4Ax+4(A+B)+(9+12+4)Ce^{3x}
$$

$$
=4Ax+4(A+B)+25Ce^{3x}.
$$

Match to $4x+0+25e^{3x}$ term by term. From $x^0$: $4(A+B)=0$, so $B=-A$. From $x^1$: $4A=4$, so $A=1$ and $B=-1$. From $e^{3x}$: $25C=25$, so $C=1$. Hence

$$
y_P=x-1+e^{3x},
$$

and the general solution is

$$
y=(c_1+c_2x)e^{-2x}+x-1+e^{3x}.
$$

The answer can sometimes be spotted by inspection, but matching term by term works when it cannot. SymPy confirms that $y_P$ reproduces $4x+25e^{3x}$ exactly.

### Clashes with the complementary function

The complementary function is found first because it decides the guess. If the natural guess is already a complementary function, substituting it gives zero, so it can never balance the source; the fix is to multiply the guess by successive powers of $x$. With the same left-hand side as above, whose complementary functions are $e^{-2x}$ and $xe^{-2x}$, two clashing sources are $e^{-2x}$ and $xe^{-2x}$.

For $r=e^{-2x}$, both $Ce^{-2x}$ and $Cxe^{-2x}$ are complementary functions, so the first guess worth trying is $y_P=Cx^2e^{-2x}$. Differentiate:

$$
y_P'=C(2x-2x^2)e^{-2x},
$$

$$
y_P''=C(2-4x-4x+4x^2)e^{-2x}=C(2-8x+4x^2)e^{-2x}.
$$

Substitute:

$$
y_P''+4y_P'+4y_P=C\big[(2-8x+4x^2)+(8x-8x^2)+4x^2\big]e^{-2x}
$$

$$
=2Ce^{-2x},
$$

so $2C=1$, $C=\tfrac12$ and $y_P=\tfrac12x^2e^{-2x}$.

For $r=xe^{-2x}$, the natural guess is $(Ax+B)e^{-2x}$, and multiplying by $x^2$ removes the clash: $y_P=(Ax^3+Bx^2)e^{-2x}$. A guess $Cx^2e^{-2x}$ alone can only produce $2Ce^{-2x}$, as the calculation above shows, and $Cx^3e^{-2x}$ is the first power that works. Writing $y_P=u(x)e^{-2x}$ with $u=Ax^3+Bx^2$, the left-hand side reduces to $u''e^{-2x}$ (derived in [[#Why the powers of x work]]), so

$$
u''=6Ax+2B,
$$

and matching $u''e^{-2x}$ to $xe^{-2x}$ term by term gives

$$
6A=1,\qquad 2B=0,
$$

so $A=\tfrac16$, $B=0$ and $y_P=\tfrac16x^3e^{-2x}$. The general solution is $y=(c_1+c_2x+\tfrac16x^3)e^{-2x}$, which SymPy's `dsolve` returns in exactly this form.

A source such as $\log(\sin x^{3/4})$ has no sensible guess, and undetermined coefficients doesn't apply. Variation of parameters, $y_P=v_1y_1+v_2y_2$ with $v_1'=-ry_2/W$ and $v_2'=ry_1/W$, works for any $r$ but is long and not examinable.

A practical rule is to give up after two failed guesses: a second-order equation needs at most $x^2$ times the guess, and checking each one by hand takes long, so computer algebra is quicker beyond that.

### Why the powers of x work

*(Suggested, not lectured; it explains the clash rule.)* In $y''+by'+cy$ let $y=u(x)e^{kx}$. Differentiate:

$$
y'=(u'+ku)e^{kx},
$$

$$
y''=(u''+2ku'+k^2u)e^{kx}.
$$

Substitute and collect:

$$
y''+by'+cy=\big[u''+(2k+b)u'+(k^2+bk+c)u\big]e^{kx}.
$$

The coefficient of $u$ is the auxiliary polynomial evaluated at $k$, which vanishes when $k$ is a root, so a constant $u$ (a plain $Ce^{kx}$) gives zero. The coefficient of $u'$ is that polynomial's derivative at $k$, which also vanishes when $k$ is a repeated root, leaving just $u''$. For $y''+4y'+4y$ with $k=-2$ both vanish, so the equation for $u$ is just $u''=$ (source $\times e^{2x}$). For $r=e^{-2x}$ that is $u''=1$, giving $u=\tfrac12x^2$; for $r=xe^{-2x}$ it is $u''=x$, giving $u=\tfrac16x^3$. That is why $x^2e^{-2x}$ fails for the second source: it gives $2e^{-2x}$, not anything proportional to $xe^{-2x}$.

### Problem Sheet 1, Q3: a clash hidden in a sine

PS1 Q3(b) is $y''-2y'+2y=4e^x\sin x$. The auxiliary equation $\lambda^2-2\lambda+2=0$ has roots

$$
\lambda=\frac{2\pm\sqrt{4-8}}{2}=1\pm j,
$$

so the complementary functions are $e^x\cos x$ and $e^x\sin x$. The table's guess $e^x(C\sin x+D\cos x)$ is exactly the complementary function and would give zero. Use the substitution above with $k=1$, $b=-2$, $c=2$: the coefficient of $u'$ is $2k+b=0$ and the coefficient of $u$ is $k^2+bk+c=1$, so $y=ue^x$ turns the equation into

$$
u''+u=4\sin x .
$$

This is the undamped oscillator forced at its own frequency, the resonance problem treated in [[#Resonance]], so the guess for $u$ must carry a factor $x$:

$$
u=x(C\cos x+D\sin x),
$$

$$
u''=2(-C\sin x+D\cos x)-x(C\cos x+D\sin x),
$$

$$
u''+u=-2C\sin x+2D\cos x .
$$

Matching to $4\sin x$ gives $C=-2$ and $D=0$, so $u=-2x\cos x$ and

$$
y_P=-2xe^x\cos x,\qquad y=e^x(c_1\cos x+c_2\sin x)-2xe^x\cos x .
$$

The same substitution handles PS1 Q3(a), $y''-2y'+y=4e^x$: with $k=1$ the root is repeated, both coefficients vanish, $u''=4$, $u=2x^2$ and $y_P=2x^2e^x$. SymPy's `dsolve` gives both general solutions.

### Resonance

The 1940 Tacoma Narrows bridge collapse is the classic motivating case. An undamped oscillator driven at frequency $\omega_s$ obeys

$$
\ddot y+\omega_0^2y=\cos\omega_st,
$$

with complementary function $c_1\cos\omega_0t+c_2\sin\omega_0t$. If $\omega_s\neq\omega_0$ there is no clash, and the guess $y_P=A\cos\omega_st$ (no sine is needed because there is no $\dot y$ term) gives

$$
\ddot y_P+\omega_0^2y_P=A(\omega_0^2-\omega_s^2)\cos\omega_st,
$$

so $A=1/(\omega_0^2-\omega_s^2)$: a bounded response that grows as the forcing approaches the natural frequency. At $\omega_s=\omega_0$ the guess clashes, so multiply by $t$:

$$
y_P=t(A\cos\omega_0t+B\sin\omega_0t).
$$

Differentiate:

$$
\dot y_P=(A\cos\omega_0t+B\sin\omega_0t)+t\omega_0(-A\sin\omega_0t+B\cos\omega_0t),
$$

$$
\ddot y_P=2\omega_0(-A\sin\omega_0t+B\cos\omega_0t)-t\omega_0^2(A\cos\omega_0t+B\sin\omega_0t).
$$

The $t$ terms cancel against $\omega_0^2y_P$, leaving

$$
\ddot y_P+\omega_0^2y_P=2\omega_0(-A\sin\omega_0t+B\cos\omega_0t)=\cos\omega_0t,
$$

so $A=0$, $B=1/(2\omega_0)$ and

$$
y_P=\frac{t}{2\omega_0}\sin\omega_0t.
$$

The amplitude grows linearly in time, which is resonance.

The two cases join up once initial conditions are applied. Starting from rest, $y(0)=\dot y(0)=0$, with $\omega_s\neq\omega_0$, the general solution is

$$
y=c_1\cos\omega_0t+c_2\sin\omega_0t+\frac{\cos\omega_st}{\omega_0^2-\omega_s^2}.
$$

$\dot y(0)=\omega_0c_2=0$ gives $c_2=0$, and $y(0)=c_1+1/(\omega_0^2-\omega_s^2)=0$ gives $c_1=-1/(\omega_0^2-\omega_s^2)$, so

$$
y=\frac{\cos\omega_st-\cos\omega_0t}{\omega_0^2-\omega_s^2}.
$$

As $\omega_s\to\omega_0$ both numerator and denominator vanish. Treat $\omega_s$ as the variable and apply L'Hôpital's rule:

$$
\lim_{\omega_s\to\omega_0}\frac{\cos\omega_st-\cos\omega_0t}{\omega_0^2-\omega_s^2}=\lim_{\omega_s\to\omega_0}\frac{-t\sin\omega_st}{-2\omega_s}=\frac{t}{2\omega_0}\sin\omega_0t,
$$

which is the resonant particular integral, and it already satisfies both initial conditions. Near resonance the response is a beat: the product form $\cos\omega_st-\cos\omega_0t=2\sin\frac{(\omega_0+\omega_s)t}{2}\sin\frac{(\omega_0-\omega_s)t}{2}$ shows a fast oscillation inside a slow envelope of period $4\pi/|\omega_0-\omega_s|$, and that envelope's peak, $2/|\omega_0^2-\omega_s^2|$, grows without limit as the frequencies approach each other.

> [!check] Beats against the resonant limit
> With $\omega_0=2$ and $\omega_s=1.9$, at $t=10$ the beat formula gives $(\cos19-\cos20)/0.39=1.489$, while the resonant formula gives $\tfrac{10}{4}\sin20=2.282$. The two agree only while $t\ll2\pi/|\omega_0-\omega_s|\approx63$, after which the beat turns back; SymPy's `dsolve` and `limit` reproduce both expressions.

![[m2048_ode_resonance.png|640]]

A real bridge has damping, so the amplitude saturates instead of growing for ever, but at the level $1/(2c\omega_0/m)$ rather than $1/(\omega_0^2-\omega_s^2)$, which for light damping is enormous.

## Links

- Parent: [[MATH2048 Mathematics for Engineering and the Environment Part II Hub]] · Previous: [[MATH2048 ODE1 - Second-Order Linear ODEs with Constant Coefficients]] · Next: [[MATH2048 ODE3 - Boundary Value and Eigenvalue Problems]]
- The particular-integral idea for PDEs: [[MATH2048 PDE4 - Inhomogeneous PDEs and Inhomogeneous Boundary Conditions]]
- Concepts: [[Euler-Cauchy Equation]] · [[Method of Undetermined Coefficients]] · [[Resonance]] · [[Auxiliary Equation]]

## Sources

- Lecture 2 recording, 1 Oct 2024 (Ian Hawke): `MATH2048 Lecture 2.txt`; correction at the start of Lecture 3 (`MATH2048 Lecture 3.txt`, ll. 1–18)
- Slides `Lecture2_ODE.pdf`; `Lecture3_ODE.pdf` slide 18 (resonance)
- Appendix to Lectures 1–2; lecture notes §1.1.1–1.1.2
- Problem Sheet 1 Q2–Q3; worked solutions in [[MATH2048 Problem Sheets 1-2 Solutions - ODEs]]

## Self-study tasks

Lecture 2 set the Tacoma Narrows challenge on its last slide and otherwise pointed to Problem Sheet 1 and the STACK practice quizzes.

### Core

- [ ] Derive $x^2y''=\ddot y-\dot y$ and $xy'=\dot y$ for $t=\ln x$, and hence the constant-coefficient form $a\ddot y+(b-a)\dot y+cy=0$ (L2, ll. 183–203). → [[#Repeated or complex roots: the substitution t = ln x]]
- [ ] PS1 Q2(a)–(c), one Euler equation of each root type. Answers: $c_1x^3+c_2x^{-2}$; $x^{-1}[c_1\cos(3\ln x)+c_2\sin(3\ln x)]$; $x^{-2}(c_1+c_2\ln x)$. → [[#Problem Sheet 1, Q2: one Euler equation of each kind]]
- [ ] PS1 Q3(a)–(c), undetermined coefficients with clashes. Answers: $y_P=2x^2e^x$; $y_P=-2xe^x\cos x$; $y_P=\tfrac16x^3e^{2x}$. → [[#Problem Sheet 1, Q3: a clash hidden in a sine]] · [[MATH2048 Problem Sheets 1-2 Solutions - ODEs#Q3: Undetermined coefficients]]

### Further practice

- [ ] Lecturer-set challenge (L2 slide 16): explain the Tacoma Narrows collapse, then derive $y_P=\frac{t}{2\omega_0}\sin\omega_0t$ both directly and as the limit of the beat solution. → [[#Resonance]]
- [ ] Find $y_P$ for $y''+4y'+4y=xe^{-2x}$ and show why $Cx^2e^{-2x}$ fails (suggested, not lecturer-set). → [[#Why the powers of x work]]
- [ ] Solve the pulsating-star equation and say which constant vanishes for a star and which for a point charge (L2, ll. 154–170). → [[#The pulsating star]]

## Transcript and slide slips

### Transcript slips

> [!warning] Lecture 2 slips
> | Where | Transcript says | Correct |
> |---|---|---|
> | L2, ll. 113–121 | expands $r(rX)''$ wrongly, then patches it on the slide | $r^2X''+2rX'-\ell(\ell+1)X=0$; the lecturer redid the product rule at the start of L3 (ll. 1–18) |
> | L2, l. 149 | roots "L or alternatively minus L plus 1" | $n=\ell$ or $n=-(\ell+1)$; the slide writes $c_2/r^{\ell+1}$ |
> | L2, l. 278 | "y double prime plus 4y prime plus 4y prime" | $y''+4y'+4y=0$ |
> | L2, ll. 401–402 | for the source $xe^{-2x}$, $x^2e^{-2x}$ "vanishes again on the left hand side but I'm not 100% sure" | it gives $2e^{-2x}$, not zero; it fails because it can't produce an $x e^{-2x}$ term |
