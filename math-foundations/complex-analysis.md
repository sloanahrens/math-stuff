# Complex Analysis

Complex analysis is the study of functions of complex variables. It provides powerful techniques for evaluating integrals, solving differential equations, and understanding analytic structure. This document builds on [algebra](algebra-primer.md) and [Euler's formula](euler-formula.md), and is essential for [Green's functions](greens-functions.md), [quantum mechanics](../quantum-mechanics/quantum-mechanics.md), and [electromagnetism](../electromagnetism/electrostatics.md).

## Complex Functions

### Functions of a Complex Variable

A complex function $f: \mathbb{C} \to \mathbb{C}$ maps complex numbers to complex numbers. Writing $z = x + iy$ and $f(z) = u(x,y) + iv(x,y)$:

```math
f(z) = u(x, y) + iv(x, y)
```

where $u$ and $v$ are real-valued functions of two real variables.

**Examples:**

| Function | $u(x,y)$ | $v(x,y)$ |
|----------|----------|----------|
| $f(z) = z^2$ | $x^2 - y^2$ | $2xy$ |
| $f(z) = e^z$ | $e^x \cos y$ | $e^x \sin y$ |
| $f(z) = 1/z$ | $x/(x^2+y^2)$ | $-y/(x^2+y^2)$ |

### Analyticity and the Cauchy-Riemann Equations

A function is **analytic** (or holomorphic) at a point if it has a complex derivative there. For $f(z) = u + iv$ to be analytic, it must satisfy the **Cauchy-Riemann equations**:

```math
\boxed{\frac{\partial u}{\partial x} = \frac{\partial v}{\partial y}, \qquad \frac{\partial u}{\partial y} = -\frac{\partial v}{\partial x}}
```

**What this means:** These conditions ensure the derivative is the same regardless of the direction of approach in the complex plane. They're remarkably restrictive—analytic functions are infinitely differentiable and equal their Taylor series.

### Harmonic Functions

If $f = u + iv$ is analytic, then both $u$ and $v$ satisfy Laplace's equation:

```math
\nabla^2 u = \frac{\partial^2 u}{\partial x^2} + \frac{\partial^2 u}{\partial y^2} = 0
```

Functions satisfying Laplace's equation are called **harmonic**. The real and imaginary parts of any analytic function are harmonic conjugates.

**What this means:** This connects complex analysis to [electrostatics](../electromagnetism/electrostatics.md)—the real part of an analytic function can represent an electrostatic potential in 2D.

## Contour Integration

### Line Integrals in the Complex Plane

A **contour** $C$ is a piecewise smooth curve in $\mathbb{C}$. The contour integral is:

```math
\int_C f(z) \, dz = \int_a^b f(z(t)) z'(t) \, dt
```

where $z(t)$ parametrizes the contour from $t = a$ to $t = b$.

### Cauchy's Theorem

If $f(z)$ is analytic inside and on a simple closed contour $C$:

```math
\boxed{\oint_C f(z) \, dz = 0}
```

**What this means:** The integral around any closed loop is zero if the function is analytic everywhere inside. This is the complex analog of a conservative vector field.

### Cauchy's Integral Formula

If $f(z)$ is analytic inside and on a simple closed contour $C$, and $z_0$ is inside $C$:

```math
\boxed{f(z_0) = \frac{1}{2\pi i} \oint_C \frac{f(z)}{z - z_0} \, dz}
```

For derivatives:

```math
f^{(n)}(z_0) = \frac{n!}{2\pi i} \oint_C \frac{f(z)}{(z - z_0)^{n+1}} \, dz
```

**What this means:** The value of an analytic function inside a region is completely determined by its values on the boundary. This is extraordinarily powerful—knowing the boundary determines everything inside.

## Singularities and Residues

### Types of Singularities

A point $z_0$ where $f(z)$ is not analytic is a **singularity**:

| Type | Behavior | Example |
|------|----------|---------|
| Removable | Limit exists, can be "filled in" | $\frac{\sin z}{z}$ at $z=0$ |
| Pole of order $n$ | $(z-z_0)^n f(z)$ is analytic | $\frac{1}{z^2}$ at $z=0$ (order 2) |
| Essential | Neither of the above | $e^{1/z}$ at $z=0$ |

### Laurent Series

Near an isolated singularity $z_0$, a function can be expanded as:

```math
f(z) = \sum_{n=-\infty}^{\infty} a_n (z - z_0)^n
```

The **principal part** consists of terms with $n < 0$. For a pole of order $m$, the series starts at $n = -m$.

### The Residue

The **residue** of $f(z)$ at $z_0$ is the coefficient $a_{-1}$ in the Laurent series:

```math
\text{Res}(f, z_0) = a_{-1} = \frac{1}{2\pi i} \oint_C f(z) \, dz
```

where $C$ is a small circle around $z_0$.

**For a simple pole** ($m = 1$):

```math
\text{Res}(f, z_0) = \lim_{z \to z_0} (z - z_0) f(z)
```

**For a pole of order $m$**:

```math
\text{Res}(f, z_0) = \frac{1}{(m-1)!} \lim_{z \to z_0} \frac{d^{m-1}}{dz^{m-1}} \left[ (z - z_0)^m f(z) \right]
```

## The Residue Theorem

### Statement

If $f(z)$ is analytic inside and on a simple closed contour $C$ except for isolated singularities $z_1, z_2, \ldots, z_n$ inside $C$:

```math
\boxed{\oint_C f(z) \, dz = 2\pi i \sum_{k=1}^{n} \text{Res}(f, z_k)}
```

**What this means:** Any contour integral reduces to summing residues. This transforms difficult integrals into algebraic calculations.

### Example: Evaluating $\oint \frac{e^z}{z^2} dz$

Around a circle containing $z = 0$:

The function has a pole of order 2 at $z = 0$. Using the formula:

```math
\text{Res}\left(\frac{e^z}{z^2}, 0\right) = \lim_{z \to 0} \frac{d}{dz}\left[z^2 \cdot \frac{e^z}{z^2}\right] = \lim_{z \to 0} e^z = 1
```

Therefore:
```math
\oint \frac{e^z}{z^2} dz = 2\pi i \cdot 1 = 2\pi i
```

## Evaluating Real Integrals

### Integrals of Rational Functions

For $\int_{-\infty}^{\infty} R(x) \, dx$ where $R(x) = P(x)/Q(x)$ with $\deg Q \geq \deg P + 2$:

1. Close the contour with a semicircle in the upper (or lower) half-plane
2. The semicircular arc contributes zero as radius $\to \infty$
3. Sum residues in the chosen half-plane

**Example:** $\displaystyle\int_{-\infty}^{\infty} \frac{dx}{1 + x^2}$

The integrand is $\frac{1}{(x+i)(x-i)}$. Closing in the upper half-plane, the only pole inside is $z = i$:

```math
\text{Res}\left(\frac{1}{1+z^2}, i\right) = \frac{1}{2i}
```

Therefore:
```math
\int_{-\infty}^{\infty} \frac{dx}{1 + x^2} = 2\pi i \cdot \frac{1}{2i} = \pi
```

### Integrals with Trigonometric Functions

For $\int_0^{2\pi} R(\cos\theta, \sin\theta) \, d\theta$:

Substitute $z = e^{i\theta}$, so $\cos\theta = \frac{z + z^{-1}}{2}$, $\sin\theta = \frac{z - z^{-1}}{2i}$, $d\theta = \frac{dz}{iz}$:

```math
\int_0^{2\pi} R(\cos\theta, \sin\theta) \, d\theta = \oint_{|z|=1} R\left(\frac{z+z^{-1}}{2}, \frac{z-z^{-1}}{2i}\right) \frac{dz}{iz}
```

### Integrals with Exponentials

For $\int_{-\infty}^{\infty} f(x) e^{iax} \, dx$ with $a > 0$:

- Close in the upper half-plane (where $e^{iaz} \to 0$ as $\text{Im}(z) \to \infty$)
- Apply Jordan's lemma: the semicircular arc contributes zero

**Example:** $\displaystyle\int_{-\infty}^{\infty} \frac{e^{ix}}{1 + x^2} dx$

Pole at $z = i$ in the upper half-plane:

```math
\text{Res}\left(\frac{e^{iz}}{1+z^2}, i\right) = \frac{e^{-1}}{2i}
```

Therefore:
```math
\int_{-\infty}^{\infty} \frac{e^{ix}}{1 + x^2} dx = 2\pi i \cdot \frac{e^{-1}}{2i} = \frac{\pi}{e}
```

## Branch Cuts and Multi-Valued Functions

### The Problem

Functions like $\sqrt{z}$, $\ln z$, and $z^{1/n}$ are multi-valued. Going around the origin once changes the value:

```math
\sqrt{re^{i\theta}} = \sqrt{r} e^{i\theta/2} \quad \text{becomes} \quad \sqrt{r} e^{i(\theta + 2\pi)/2} = -\sqrt{r} e^{i\theta/2}
```

### Branch Cuts

A **branch cut** is a curve we agree not to cross, making the function single-valued. Common choices:

| Function | Standard Branch Cut | Principal Value Range |
|----------|--------------------|-----------------------|
| $\ln z$ | Negative real axis | $-\pi < \arg(z) \leq \pi$ |
| $\sqrt{z}$ | Negative real axis | $-\pi/2 < \arg(\sqrt{z}) \leq \pi/2$ |
| $z^a$ (general) | Negative real axis | Defined via $e^{a \ln z}$ |

**What this means:** Branch cuts are necessary bookkeeping. When integrating, contours must not cross branch cuts, or you must account for the discontinuity.

### Example: $\int_0^\infty \frac{x^{a-1}}{1+x} dx$ for $0 < a < 1$

Use a keyhole contour avoiding the branch cut on the positive real axis:

```math
\int_0^\infty \frac{x^{a-1}}{1+x} dx = \frac{\pi}{\sin(\pi a)}
```

This is related to the [Gamma function](special-functions.md).

## Conformal Mapping

### Definition

A **conformal map** preserves angles between curves. Any analytic function with $f'(z) \neq 0$ is conformal.

### Key Mappings

| Map | Effect |
|-----|--------|
| $w = z + c$ | Translation |
| $w = e^{i\theta} z$ | Rotation by $\theta$ |
| $w = az$ ($a > 0$) | Scaling |
| $w = 1/z$ | Inversion + reflection |
| $w = z^2$ | Doubles angles at origin |
| $w = e^z$ | Maps strips to sectors |
| $w = \ln z$ | Maps sectors to strips |

### Mobius Transformations

The general form:

```math
w = \frac{az + b}{cz + d}, \qquad ad - bc \neq 0
```

maps circles and lines to circles and lines. Three points determine the transformation uniquely.

### Applications

Conformal mapping transforms complicated boundary shapes to simpler ones:
- Fluid flow around obstacles
- Electrostatic problems in 2D
- Heat conduction

**What this means:** A difficult problem in a complicated geometry can be mapped to an equivalent problem in a simple geometry, solved there, then mapped back.

## Analytic Continuation

### The Idea

If two analytic functions agree on a region, they must agree everywhere they're both defined. This lets us extend functions beyond their original domain.

### Example: The Gamma Function

The integral $\Gamma(z) = \int_0^\infty t^{z-1} e^{-t} dt$ converges only for $\text{Re}(z) > 0$.

Using $\Gamma(z+1) = z\Gamma(z)$, we can extend to all $z$ except non-positive integers:

```math
\Gamma(z) = \frac{\Gamma(z+1)}{z} = \frac{\Gamma(z+2)}{z(z+1)} = \cdots
```

### Example: The Riemann Zeta Function

$\zeta(s) = \sum_{n=1}^\infty n^{-s}$ converges for $\text{Re}(s) > 1$.

Analytic continuation extends it to all $s \neq 1$, revealing the famous zeros relevant to the Riemann hypothesis.

## Applications in Physics

### Quantum Mechanics

- **Propagators** are boundary values of analytic functions
- **S-matrix** analyticity constrains scattering amplitudes
- **Bound states** appear as poles in the complex energy plane

### Statistical Mechanics

- **Partition functions** have singularities at phase transitions
- **Lee-Yang theorem** locates zeros in the complex fugacity plane

### Electromagnetism

- **Response functions** (permittivity, conductivity) are analytic in the upper half-plane
- **Kramers-Kronig relations** connect real and imaginary parts

### Signal Processing

- **Laplace and Fourier transforms** use complex frequency
- **Transfer functions** have poles and zeros determining system behavior

## Summary

| Concept | Key Result | Application |
|---------|------------|-------------|
| Cauchy-Riemann | $\partial_x u = \partial_y v$, $\partial_y u = -\partial_x v$ | Test for analyticity |
| Cauchy's theorem | $\oint f \, dz = 0$ (analytic inside) | Path independence |
| Cauchy integral formula | $f(z_0) = \frac{1}{2\pi i} \oint \frac{f(z)}{z-z_0} dz$ | Values from boundary |
| Residue theorem | $\oint f \, dz = 2\pi i \sum \text{Res}$ | Evaluate any contour integral |
| Branch cuts | Make multi-valued functions single-valued | $\ln z$, $z^a$, $\sqrt{z}$ |
| Conformal maps | Preserve angles, transform geometries | 2D potential problems |

**The essential insight:** Analytic functions are remarkably rigid—knowing them on a boundary determines them everywhere, and their integrals reduce to algebraic residue calculations. This transforms difficult integrals and differential equations into tractable problems. The techniques appear throughout physics: from evaluating [Fourier transforms](fourier-analysis.md) to understanding the analytic structure of scattering amplitudes in [quantum field theory](../quantum-mechanics/qft-introduction.md).
