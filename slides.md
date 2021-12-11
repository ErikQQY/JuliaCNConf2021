---
# try also 'default' to start simple
theme: seriph
# random image from a curated Unsplash collection by Anthony
# like them? see https://unsplash.com/collections/94734566/slidev
background: https://source.unsplash.com/collection/94734566/1920x1080
# apply any windi css classes to the current slide
class: 'text-center'
# https://sli.dev/custom/highlighters.html
highlighter: shiki
# show line numbers in code blocks
lineNumbers: false
# some information about the slides, markdown enabled
info: |
  ## SciFracX presentation
  
  Aiming at providing world class fractional computing techniques.

  Learn more at [SciFracX](https://github.com/SciFracX)
# persist drawings in exports and build
drawings:
  persist: false
---

# Fractional Order Computing with Julia

<br>
<br>
<br>

ErikQQY 

<br>

JuliaCN 2021


<div class="abs-br m-6 flex gap-1">
  <a href="https://github.com/SciFracX" target="_blank" alt="GitHub"
    class="text-xl icon-btn opacity-30 !border-none !hover:text-white">
    <carbon-logo-github />
  </a>
</div>

<!--
The last comment block of each slide will be treated as slide notes. It will be visible and editable in Presenter Mode along with the slide. [Read more in the docs](https://sli.dev/guide/syntax.html#notes)
-->

---
layout: default
---

# OutLine

1. SciFracX introduction

2. History of fractional calculus and fractional differential equations

3. Introduction to Fractional Calculus

4. Get hands on FractionalCalculus.jl

5. Introduction to Fractional Differential Equations

6. Get hands on FractionalDiffEq.jl

7. One more thing

---
layout: 'intro'
---


# What is SciFracX?

SciFracX is an orgnization aiming at deploying the advantages of Julia to fractional computing area.

*Scientific Fractional Order Computing*

<div grid="~ cols-2 gap-2" m="-t-2">

- There are huge gap between theoretical researches and applications in fractional scientific computing area. SciFracX is aiming at filling the gap and bridge the theoretical and application.

- No deadline, no pushing, just a labor of love.

<img border="rounded" src="/assets/favicon.ico" class="m-10 left-130 w-70 " />

</div>

<br>
<br>

<!--
You can have `style` tag in markdown to override the style for the current page.
Learn more: https://sli.dev/guide/syntax#embedded-styles
-->

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent; 
  -moz-text-fill-color: transparent;
}
</style>

---
layout: fact
background: https://source.unsplash.com/collection/94734566/1920x1080
class: 'text-center'
---

# Fractional Calculus


<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;

  -webkit-text-fill-color: transparent; 
  -moz-text-fill-color: transparent;
  font-size: 15em;
}
</style>


---
layout: default
---

# Classical Calculus
We already learned classical calculus

The derivative and integral has its geometric illustration and meaning.

$$
\frac{d}{dt}v = a
$$

$$
\int_{t_1}^{t_2} vdt = s
$$

<br>

<div grid="~ cols-3 gap-3" m="-t-3">
<img border="rounded" src="/assets/distance.png" class="m-0 left-130 w-70 " />
<img border="rounded" src="/assets/velocity.png" class="m-0 left-130 w-70 " />
<img border="rounded" src="/assets/acceleration.png" class="m-0 left-130 w-70 " />
</div>

---
layout: two-cols
---

# Meaning

Then what is the meaning of semi-order derivative or a quarter integral?🤔

<v-clicks>

Let's go back to three handreds years ago


In a letter to L'Hôpital in 1695<br>
Leibniz raised the question: <br>"Can the meaning of derivatives with integer order be generalized to derivatives with non-integer orders?"<br> <br>L`Hôpital was curious about that question and replied by another question: "What if the order will be $\frac{1}{2}$?" Leibniz in a letter dated September 30, 1695 — the exact birthday of the fractional calculus! — replied: <br>

<font color=#4EC5D4><strong>"It will lead to a paradox, from which one day useful consequences will be drawn."</strong></font>

</v-clicks>

::right::



<br>
<br>
<br>
<br>

<div grid="~ cols-2 gap-2" m="-t-2">

<div v-click>
<img border="rounded" src="/assets/Leibniz.jpg" class="m-0 left-130 w-50 " />
</div>

<div v-click>
<img border="rounded" src="/assets/LHopital.jpg" class="m-0 w-50" />
</div>

</div>

---
layout: default
---

# An outlook of Fractional Calculus

"Old history"

<v-clicks>


<img border="rounded" src="/assets/history.png" class="m-0 w-150 h-100" />





</v-clicks>


---
layout: default
---

# An outlook of Fractional Calculus

"Recent history"

<v-clicks>

<img border="rounded" src="/assets/recent.png" class="m-0 w-150 h-100" />

</v-clicks>

---
layout: default
---

# Basic introductioon

*Fractional Calculus* here means arbitrary order in fact, **fractions**, **complex**, **arbitrary**

<v-clicks>

We first think about how can we get the fractional derivative.

Suppose we want the fractional derivative of a power function: $f(x)=x^k$

The basic calculus we learned before is enough:

The first derivative:

$$
f'(x)=\frac{d}{dx}f(x)=kx^{k-1}
$$

And the second derivative:

$$
f''(x)=\frac{d^2}{dx^2}f(x)=k(k-1)x^{k-2}
$$

We can know the n-th derivative:

</v-clicks>

---

<v-clicks>

$$
f^{(n)}(x)=\frac{d^n}{dx^n}x^k=\frac{k!}{(k-n)!}x^{k-n}=\frac{\Gamma(k+1)}{\Gamma(k-n+1)}x^{k-n}
$$


So we replace **n** with $\frac{1}{2}$, we can get the semi-derivative of the power function:

$$
f^{(\frac{1}{2})}(x)=\frac{\Gamma(2)}{\Gamma(\frac{3}{2})}x^{\frac{1}{2}}=\frac{2}{\sqrt\pi}x^{\frac{1}{2}}
$$

Bingo🎉!! We get the semi-derivative of $f(x)=x$!

</v-clicks>


---
layout: default
---

## Then what's the geometric and physical meaning of fractional calculus?[^1]

<div class="grid grid-cols-2 gap-x-1">

<div>

<img src="/assets/shadow.png" class="m-0 w-150" />



Shadows on the wall



Three axis: $\tau$, $g(\tau)$, $f(\tau)$

</div>

<div>

$$
_0^{RL}Dt^{-\alpha}f(t)=\frac{1}{\Gamma(\alpha)}\int_0^t\frac{f(\tau)}{(t-\tau)^{(1-\alpha)}}d\tau
$$
$$
g(\tau)=\frac{1}{\Gamma(\alpha+1)}[t^\alpha-(t-\tau)^\alpha]
$$

$$
\downarrow
$$

$$
_0^{RL}D_t^{-\alpha}f(t)=\int_0^tf(\tau)d g(\tau)
$$


Shadow in $\tau$~$f(\tau)$ plane: **Classical Inetgral**

Shadow in $g(\tau)$~$f(\tau)$ plane: **Fractional Integral**

</div>

</div>

[^1]: [Geometric and Physical Interpretation of Fractional Integration and Fractional Differentiation](https://arxiv.org/abs/math/0110241)


<style>
.footnotes-sep {
  @apply mt-20 opacity-10;
}
.footnotes {
  @apply text-sm opacity-75;
}
.footnote-backref {
  display: none;
}
</style>

---
layout: default
---

# Three different grades of fractional calculus

<v-clicks>

### Constant non-integer order (CO)

$$
_aD^\alpha_t f(t)=\frac{1}{\Gamma(n-\alpha)}(\frac{d}{dt})^n\int_a^t\frac{f(\tau)d\tau}{(t-\tau)^{\alpha-n+1}},\quad (n-1\leq\alpha < n)
$$

### Variable order (VO)

$$
^C_0D^{\alpha(t)}_t=\frac{1}{\Gamma(n-\alpha(t))}\int_0^t\frac{f^{(n)}(\tau)d\tau}{(t-\tau)^{\alpha(t)-n+1}},\quad (n-1\leq\alpha(t) < n)
$$

### Distributed order (DO)

$$
_aD^{\phi(\alpha)}f(t)=\int_c^d\phi(\alpha){_aD_t^\alpha}f(t)d\alpha
$$

$$
\int_c^d\phi(\alpha)d\alpha=1
$$

</v-clicks>


---
layout: default
---

# Quick Start

<v-clicks>

Let's get start!!🥳

Install FractionalCalculus.jl in REPL package manager with entering <kbd>]</kbd>

```julia
Pkg> add FractionalCalculus
julia> using FractionalCalculus
```

Then if you want to calculuate the semi derivative of $f(x)=x^2$ at $x=1$:

```julia
julia> fracdiff(x->x^2, 0.5, 1, 0.001, RLDiff_Approx())
1.5044908143658473
```

Or a quarter integral of $f(x)=\sin x$ ay $x=1$? Not a problem!

```julia
julia> fracint(sin, 0.25, 3, 0.001, RLInt_Approx())
0.6197918550987523
```

</v-clicks>

---
layout: default
---

# Plots

Let's plot different order integral and derivative:

<div class="grid grid-cols-2 gap-x-4">


<v-clicks>

<div>

Different order integral of $f(x)=x$

<img src="/assets/different_order_x_integral.png" />

</div>

<div>

Different order derivative of $f(x)=\sin(x)$

<img src="/assets/different_order_sin_derivative.png" />

</div>

We can see the fractional calculus is quite different from classical calculus.

</v-clicks>


</div>

---

<v-clicks>

If we want to see different order derivative of $f(x)=\sin(x)$ in a more (With *tspan*, *order* and *value* axis):


<img src="/assets/3dexample.png" />

</v-clicks>


---
layout: default
---

# Different sense of fractional derivative and integral

Thanks to the hard work of pioneers, there are many sense of fractional derivative and integral.

The widely used fractional derivative sense are:

### Caputo Sense:

$$
^C_aD^\alpha_tf(t)=\frac{1}{\Gamma(n-\alpha)}\int_a^t\frac{f^{(n)}(\tau)d\tau}{(t-\tau)^{\alpha-n+1}},\quad(n-1\leq\alpha < n)
$$

### Riemann Liouville Sense:

$$
_aD^\alpha_tf(t)=\frac{1}{\Gamma(n-\alpha)}(\frac{d}{dt})^n\int_a^t\frac{f(\tau)d\tau}{(t-\tau)^{\alpha-n+1}}
$$

### Grunwald Letnikov Sense:

$$
D^\alpha f(t)=\displaystyle\lim_{h\leftarrow 0}h^{-\alpha}\displaystyle\sum_{k=0}^{\frac{t-a}{h}}(-1)^k{\alpha\choose n}f(t-kh)
$$

---
layout: default
---

# Different sense derivative in FractionalCalculus.jl

FractionalCalculus.jl has supports for many sense of fractional derivative and fractional integral:

<div grid="~ cols-2 gap-2" m="-t-2">

<div v-click>

## Fractional derivative

* Caputo fractional derivative

* Grunwald-Letnikov fractional derivative

* Riemann-Liouville fractional derivative

* Riesz fractional derivative

* Hadamard fractional derivative

</div>

<div v-click>

## Fractional integral

* Riemann-Liouville fractional integral


</div>

</div>




<style>
.more {
  transition: opacity 100ms ease;
}
</style>

---
layout: two-cols
---

# Current Algorithms

## Fractional Derivative

* Caputo_Piecewise
* Caputo_Diethelm
* GL_Multiplicative_Additive
* GL_Lagrange_Three_Point_Interp
* RLDiff_Approx
* RLDiff_Matrix
* Hadamard_LRect
* Hadamard_RRect
* Hadamard_Trap
* Riesz_Symmetric

::right::
<br>
<br>
<br>
<br>



## Fractional Integral

* RLDiff_Approx
* RL_Piecewise
* RL_LinearInterp
* RLInt_Approx
* RLInt_Matrix
* RLInt_Simpson
* RLInt_Trapezoidal
* RLInt_Rectangular
* RLInt_Cubic_Spline_Interp


---
layout: fact
---

## Fractional Differential Equations

<style>

h2 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;

  -webkit-text-fill-color: transparent; 
  -moz-text-fill-color: transparent;
  font-size: 15em;
}

</style>

---
layout: default
---

# Fractional Differential Equations

A generalization of differential equation

Fractional differential equation can be seen as the generalization of differential equations. In our daily life, models are usually better described in fractional differential equations.

Nowadays, fractional calculus and fractional differential equations are getting more and more attentions such as **Viscoelasticity**, **Memristor**. In **Control Theory**, fractional transfer function e.g. $G(s)=\frac{1}{s^{1.5}+s^{0.4}}$, and fractional differential equations are widely used when the usual modeling tools can't satisfy our need. Also need to mention there are fractional PID analogue---$PI^\lambda D^\mu$


---
layout: default
---

<img src="/assets/modeling.png" border="rounded" class="m-0 w-160 h-120" />



---
layout: two-cols
---

# Get started!

Let's learn how to use **FractionalDiffEq.jl** to easily solve an FDE

<v-clicks>

$$
D^{1.8}y(x)+y(x)=1
$$

$$
y(0)=0
$$

We can use the PECE(Predict-Evaluate-Correct-Evaluate) method:

```julia
using FractionalDiffEq, Plots, LaTeXStrings
s = "My first FDE solution"
fun(t, u)=1-u
prob = FODEProblem(fun, 1.8, 0, 5, 0.01)
sol = solve(prob, PECE())
plot(sol, linewidth=5, title="My first FDE solution!", 
    xaxis="Time (t)", yaxis="u(t)")
```

Then plot the solution!!

</v-clicks>


::right::

<v-clicks>

![Example](/assets/example.png)

</v-clicks>

---
layout: default
---

## Bagley Torvik Equation

<div grid="~ cols-2 gap-2" m="-t-2">

$$
Ay''(t)+BD_t^\frac{3}{2}y(t)+Cy(t)=f(t)
$$

<div>

<div grid="~ cols-2 gap-0" m="-t-3">

<img src="/assets/bagleytorvikexample.png" class="m-0 w-30 h-40" />

Damped object in Newtonian fluid

</div>


</div>

</div>

<div grid="~ cols-2 gap-2" m="-t-2">

```julia
using FractionalDiffEq
using Plots, LaTeXStrings

s="\$Bagley\\ Torvik\\ Equation\$"

T=30
h=0.05
tspan = collect(0:h:T)
result = bagleytorvik(1, 1, 1, 1, T, h)

plot(tspan, result, title=s, legend=:bottomright)
```

<img src="/assets/bagleytorvik.png" />

</div>


---

Or multi-term FDE?   **No problem**!

<v-clicks>

$$

y'''(t)+\frac{1}{16}{^C_0D^{2.5}_t}y(t)+\frac{4}{5}y''(t)+\frac{3}{2}y'(t)+\frac{1}{25}{^C_0D^{0.5}_ty(t)}+\frac{6}{5}y(t)=\frac{172}{125}\cos(\frac{4t}{5})

$$

```julia
system = D(30, 3, h)+1/16*D(30, 2.5, h)+4/5*D(30, 2, h)+3/2*D(30, 1, h)+1/25*D(30, 0.5, h)+6/5*D(30, 1, h);
rightfun = 172/125*cos(4/5*x)
result = solve(system, rightfun, 3, 0.05, 30, FODEMatrixDiscrete())
```

<img border="rounded" src="/assets/complicated_example.png" class="m-0 w-130 h-80" />

</v-clicks>

---

<div grid="~ cols-2 gap-2" m="-t-2">

<v-clicks>

Or solve Ordinary Differential Equations? Just do it~

$$
y''(x)+y'(x)=\sin(x)\\
y(0)=0
$$



</v-clicks>

</div>

<div grid="~ cols-2 gap-2" m="-t-2">

<v-clicks>

```julia
using FractionalDiffEq
using Plots, LaTeXStrings

s="\$ODE\\ Example\$"

T = 30
h=0.05
tspan = collect(0.05:h:T)

f(x)=1/2*(-exp(-x)-sin(x)-cos(x)+2)
target=f.(tspan)

eq = D(600, 2, h)+D(600, 1, h)
rightfun(x) = sin(x)
result = solve(eq, rightfun, 2, h, T, FODEMatrixDiscrete())

plot(tspan, result, title=s, legend=:bottomright, label="ODE Numerical Solution!")

plot!(tspan, target, lw=3,ls=:dash,label="ODE Analytical Solution!")
```

<img border="rounded" src="/assets/ode_example.png" />


</v-clicks>


</div>


---
layout: default
---

# Current status

As a young organization and all of these packages are just version **0.1.***, all of the APIs and algorithms are under heavy development, all kinds of contributions are sincerely welcomed.

I believe power of community is great, a group of people with the same interest working together for the same goal.

# Road Map

-  Fractional Partial Differential Equations.

-  More robust algorithms and better design.

- There are still some interesting ideas~

### Welcome to join our community!!

<style>
h3 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent; 
  -moz-text-fill-color: transparent;
}
</style>


---
layout: center
class: text-center
---

# One more thing!

---
layout: default
---

## How can we get derivative??

<v-clicks>

Finite Difference? $f'(x)=\frac{f(x+h)-f(x-h)}{2h}$ Round Off Error 😔

Symbolic Difference? Large Computation Cost 😔

### Complex Step Differentiation!!🙌

$$
f'(x)=\frac{\mathcal{Im}(f(x+ih))}{h}
$$

Very pleased to bring **ComplexDiff.jl** !!

The complex step differentiation thoughts comes from **Cleve Moler**.

</v-clicks>

<div class="abs-br m-6 flex gap-1">
  <a href="https://github.com/ErikQQY/ComplexDiff.jl" target="_blank" alt="GitHub"
    class="text-xl icon-btn opacity-30 !border-none !hover:text-white">
    <carbon-logo-github />
  </a>
</div>

---
layout: default
---

# JuliaCon talk on Complex Step Differentiation

It is amazing!!!

<Youtube id="Q9OLOqEhc64" width="700px" height="420px" />

---

Compasion with finite difference:

<img src="/assets/csderror.png" class="m-0 w-120 h-90" />

We can see the [round off error](https://en.wikipedia.org/wiki/Round-off_error) in Complex Step Differentiation is getting smaller and smaller when **h** becomes extremely small, while the error of finite difference is getting bigger and bigger.

---
layout: default
---

#### The Complex Step Differentiation method also appeared in the [Deep Learning Book](https://www.deeplearningbook.org/contents/guidelines.html)(Page 434)!!

<br>

<div grid="~ cols-2 gap-2" m="-t-2">

<div>



> If one has access to numerical computation on complex numbers, then there is
a very eﬃcient way to numerically estimate the gradient by using complex numbers
as input to the function (*Squire and Trapp, 1998*). The method is based on the
observation that
  $$
  f(x+i\epsilon)=f(x)+i\epsilon f'(x)+O(\epsilon^2)
  $$
  $$
  real(f(x+i\epsilon))=f(x)+O(\epsilon^2)
  $$
  $$
  imag(\frac{f(x+i\epsilon)}{\epsilon})=f'(x)+O(\epsilon^2)
  $$

> where $i=\sqrt{-1}$. Unlike in the real-valued case above, there is no cancellation
eﬀect because we take the diﬀerence between the value of $f$ at diﬀerent points. This allows the use of tiny values of $\epsilon$, like $\epsilon=10^{-150}$, which make the $O(\epsilon^2)$ error
insigniﬁcant for all practical purposes.


</div>

<div>


<img src="/assets/csd.png" class="m-10 w-120" />

With complex arithmetic computing built inside, Julia is absolutely a good choice!

</div>

</div>


<style>
h4 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent; 
  -moz-text-fill-color: transparent;
}
</style>

---
layout: default
---

# Multi-Complex Step Differentiation

The generalization of **Single**complex to **Multi**complex

$$
\mathbb{C_n}=\{\zeta_n=\zeta_{n-1,1}+\zeta_{n-1,2}\cdot i_n,\quad \zeta_{n-1,1},\ \zeta_{n-1,2}\in\mathbb{C_{n-1}}\}
$$

$$
f^{(n)}=\frac{imag[f(x+i_1h+i_2h+\cdots+i_nh)]}{h^n}+O(h^2)
$$

```julia
import Base: +, -, *, /
import Base: sin, cos, tan, cot
import Base: sinh, cosh, tanh

+(bi1::bicomplex, bi2::complex) = mat2bicomplex(mat(bi1) + mat(bi2))
-(bi1::bicomplex, bi2::complex) = mat2bicomplex(mat(bi1) - mat(bi2))
sin(bi::bicomplex) = bicomplex(cosh(i2)*sin(i1), sinh(i2)*cos(i1))
# Extend basic math operations and functions to multicomplex space
```

With fully utilizing multiple dispatch and operator overloading, we can achieve high order derivative computing.
