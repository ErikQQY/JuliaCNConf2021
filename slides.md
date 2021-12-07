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

3. Get hands on FractionalCalculus.jl

4. Get hands on FractionalDiffEq.jl

5. One more thing

---
layout: 'intro'
---


# What is SciFracX?

SciFracX is an orgnization aiming at deploying the advantages of Julia to fractional computing area.

*Scientific Fractional Order Computing*

- There are huge gap between theoretical researches and applications in fractional scientific computing area. SciFracX is aiming at filling the gap and bridge the theoretical and application.

- No deadline, no pushing, just a labor of love.


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


<img border="rounded" src="/assets/history.png" class="m-0 w-150" />





</v-clicks>


---
layout: default
---

# An outlook of Fractional Calculus

"Recent history"

<v-clicks>

<img border="rounded" src="/assets/recent.png" class="m-0 w-150" />

</v-clicks>

---
layout: default
---

# Basic introductioon

*Fractional Calculus* here means arbitrary order in fact, **fractions**, **complex**, **arbitrary**

<v-clicks>

We first think about how the fractional derivative is being obtained.

Suppose we want the fractional derivative of a power function: $f(x)=x^k$

Using the basic calculus we have learned is enough:

The first derivative:

$$
f'(x)=\frac{d}{dx}f(x)=kx^{k-1}
$$

And the second:

$$
f''(x)=\frac{d^2}{dx^2}f(x)=k^2x^{k-2}
$$

We can know the n-th derivative:

$$
f^{(n)}(x)=\frac{d^n}{dx^n}x^k=\frac{k!}{(k-n)!}x^{k-n}=\frac{\Gamma(k+1)}{\Gamma(k-n+1)}x^{k-n}
$$

</v-clicks>

---

<v-clicks>

So we replace **n** with $\frac{1}{2}$, we can get the semi-derivative of the power function:

$$
f^{(\frac{1}{2})}(x)=\frac{\Gamma(2)}{\Gamma(\frac{3}{2})}x^{\frac{1}{2}}=\frac{2}{\sqrt\pi}x^{\frac{1}{2}}
$$

Bingo🎉!! You get the semi-derivative of $f(x)=x$!

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

<img src="/assets/different_order_x_integral.png" />


<img src="/assets/different_order_sin_derivative.png" />

</v-clicks>

</div>

---
layout: default
---

# Different sense of fractional derivative and integral

Thanks to the hard work of pioneers, there are many sense of fractional derivative and integral.

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



---
layout: two-cols
---

# Getting start!

Let's learn how to use **FractionalDiffEq.jl** to easily solve a FDE

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

<img border="rounded" src="/assets/ode_example.png" class="m-0 w-130 h-80" />


</v-clicks>


</div>


---
layout: default
---

# Current status

As a young organization and all of these packages are just version **0.1.***, all of the APIs and algorithms are under heavy development, all kinds of contributions are sincerely welcomed.

I believe power of community is great, a group of people with the same interest working together for the same goal.(We prepared contribution gifts for contributors~~)

# Road Map

-  Fractional Partial Differential Equations

-  More robust algorithms and better design

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

Auto Differentiation?  😔

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

The Complex Step Differentiation method also appeared in the [Deep Learning Book](https://www.deeplearningbook.org/contents/guidelines.html)


<img src="/assets/csd.png" class="m-20 w-150" />

With complex arithmetic computing built inside, Julia is absolutely a good choice!

---
layout: default
---

# Multi-Complex Step Differentiation

The generalization of **Single**complex to **Multi**complex

$$\mathbb{C_n}=\{\zeta_n=\zeta_{n-1,1}+\zeta_{n-1,2}\cdot i_n,\quad \zeta_{n-1,1},\zeta_{n-1,2}\in\mathbb{C_{n-1}}\}
$$

```julia
import Base: +, -, *, /
import Base: sin, cos, tan, cot
import Base: sinh, cosh, tanh

+(bi1::bicomplex, bi2::complex) = mat2bicomplex(mat(bi1) + mat(bi2))
-(bi1::bicomplex, bi2::complex) = mat2bicomplex(mat(bi1) - mat(bi2))
```

With fully utilizing multiple dispatch and operator overloading, we can achieve high order derivative computing.