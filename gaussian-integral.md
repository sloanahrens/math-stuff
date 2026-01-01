# The Gaussian Integral

One of the most important integrals in physics:

$$
\boxed{\int_{-\infty}^{\infty} e^{-ax^2} dx = \sqrt{\frac{\pi}{a}}}
$$

This appears in [quantum mechanics](quantum-mechanics.md), [statistical mechanics](statistical-mechanics.md), and [path integrals](path-integrals.md). The proof uses a beautiful trick: square the integral and convert to polar coordinates. This document requires [calculus](calculus-primer.md) and basic [vector calculus](vector-calculus.md).

## The Proof

### Step 1: Define the Integral

Let $I$ be the Gaussian integral with $a = 1$ (we'll generalize later):

$$
I = \int_{-\infty}^{\infty} e^{-x^2} dx
$$

This integral cannot be evaluated by finding an antiderivative—$e^{-x^2}$ has no elementary antiderivative. We need a trick.

### Step 2: Square the Integral

Consider $I^2$:

$$
I^2 = \left(\int_{-\infty}^{\infty} e^{-x^2} dx\right)\left(\int_{-\infty}^{\infty} e^{-y^2} dy\right)
$$

Since $x$ and $y$ are independent dummy variables, we can combine these into a double integral:

$$
I^2 = \int_{-\infty}^{\infty} \int_{-\infty}^{\infty} e^{-x^2} e^{-y^2} \, dx \, dy = \int_{-\infty}^{\infty} \int_{-\infty}^{\infty} e^{-(x^2 + y^2)} \, dx \, dy
$$

**What this means:** We've converted a hard 1D integral into an easier 2D integral. The key insight is that $x^2 + y^2 = r^2$ in polar coordinates—the integrand has circular symmetry!

### Step 3: Convert to Polar Coordinates

In polar coordinates:
- $x = r\cos\theta$, $y = r\sin\theta$
- $x^2 + y^2 = r^2$
- $dx \, dy = r \, dr \, d\theta$ (the Jacobian gives the factor of $r$)

The integration region (all of $\mathbb{R}^2$) becomes $r \in [0, \infty)$ and $\theta \in [0, 2\pi)$:

$$
I^2 = \int_0^{2\pi} \int_0^{\infty} e^{-r^2} \, r \, dr \, d\theta
$$

### Step 4: Evaluate the Integrals

The integrals separate:

$$
I^2 = \left(\int_0^{2\pi} d\theta\right) \left(\int_0^{\infty} r \, e^{-r^2} dr\right)
$$

**Angular integral:**
$$
\int_0^{2\pi} d\theta = 2\pi
$$

**Radial integral:** Use substitution $u = r^2$, so $du = 2r \, dr$:
$$
\int_0^{\infty} r \, e^{-r^2} dr = \frac{1}{2}\int_0^{\infty} e^{-u} du = \frac{1}{2}\left[-e^{-u}\right]_0^{\infty} = \frac{1}{2}(0 - (-1)) = \frac{1}{2}
$$

**Combining:**
$$
I^2 = 2\pi \cdot \frac{1}{2} = \pi
$$

### Step 5: Take the Square Root

Since the integrand $e^{-x^2}$ is positive, $I > 0$:

$$
\boxed{I = \int_{-\infty}^{\infty} e^{-x^2} dx = \sqrt{\pi}}
$$

## Generalization to Arbitrary $a$

For general $a > 0$, substitute $u = \sqrt{a} \, x$, so $du = \sqrt{a} \, dx$:

$$
\int_{-\infty}^{\infty} e^{-ax^2} dx = \int_{-\infty}^{\infty} e^{-u^2} \frac{du}{\sqrt{a}} = \frac{1}{\sqrt{a}} \sqrt{\pi} = \sqrt{\frac{\pi}{a}}
$$

$$
\boxed{\int_{-\infty}^{\infty} e^{-ax^2} dx = \sqrt{\frac{\pi}{a}}}
$$

## Useful Generalizations

### Shifted Gaussian

$$
\int_{-\infty}^{\infty} e^{-a(x-b)^2} dx = \sqrt{\frac{\pi}{a}}
$$

The shift $b$ doesn't change the value—we're still integrating over all of $\mathbb{R}$.

### Completing the Square

For integrals of the form $e^{-ax^2 + bx}$, complete the square:

$$
-ax^2 + bx = -a\left(x - \frac{b}{2a}\right)^2 + \frac{b^2}{4a}
$$

Therefore:

$$
\boxed{\int_{-\infty}^{\infty} e^{-ax^2 + bx} dx = \sqrt{\frac{\pi}{a}} \, e^{b^2/(4a)}}
$$

This is essential for [path integrals](path-integrals.md) and partition functions.

### Moments of the Gaussian

**Even moments:** For $n = 0, 1, 2, \ldots$:

$$
\int_{-\infty}^{\infty} x^{2n} e^{-ax^2} dx = \frac{(2n-1)!!}{(2a)^n} \sqrt{\frac{\pi}{a}}
$$

where $(2n-1)!! = (2n-1)(2n-3)\cdots 3 \cdot 1$ is the double factorial.

**Odd moments:** For $n = 1, 2, 3, \ldots$:

$$
\int_{-\infty}^{\infty} x^{2n-1} e^{-ax^2} dx = 0
$$

by symmetry (odd function integrated over symmetric interval).

**First few even moments:**

| $n$ | $\int x^{2n} e^{-ax^2} dx$ |
|-----|---------------------------|
| 0 | $\sqrt{\pi/a}$ |
| 1 | $\frac{1}{2a}\sqrt{\pi/a}$ |
| 2 | $\frac{3}{4a^2}\sqrt{\pi/a}$ |
| 3 | $\frac{15}{8a^3}\sqrt{\pi/a}$ |

### Differentiation Under the Integral Sign

The moments can also be obtained by differentiating with respect to $a$:

$$
\int_{-\infty}^{\infty} x^2 e^{-ax^2} dx = -\frac{\partial}{\partial a} \int_{-\infty}^{\infty} e^{-ax^2} dx = -\frac{\partial}{\partial a} \sqrt{\frac{\pi}{a}} = \frac{1}{2a}\sqrt{\frac{\pi}{a}}
$$

This technique, sometimes called "Feynman's trick," is very powerful.

## Multidimensional Gaussian

In $n$ dimensions with a positive definite matrix $A$:

$$
\int_{\mathbb{R}^n} e^{-\mathbf{x}^T A \mathbf{x}} d^n x = \sqrt{\frac{\pi^n}{\det A}}
$$

**What this means:** The determinant measures how much the quadratic form $\mathbf{x}^T A \mathbf{x}$ "squeezes" the Gaussian. Larger determinant means more squeezing, smaller integral.

For the special case of $A = aI$ (identity matrix times scalar):

$$
\int_{\mathbb{R}^n} e^{-a|\mathbf{x}|^2} d^n x = \left(\frac{\pi}{a}\right)^{n/2}
$$

## Complex Gaussian

For purely imaginary exponent (relevant to [quantum mechanics](quantum-mechanics.md)):

$$
\int_{-\infty}^{\infty} e^{iax^2} dx = \sqrt{\frac{\pi}{a}} \, e^{i\pi/4} = \sqrt{\frac{i\pi}{a}}
$$

This requires careful treatment of the contour and branch cuts. The result follows from analytic continuation of the real Gaussian.

## Physics Applications

### Normalization of Wave Functions

The ground state of the [quantum harmonic oscillator](harmonic-oscillator.md):

$$
\psi_0(x) = \left(\frac{m\omega}{\pi\hbar}\right)^{1/4} e^{-m\omega x^2/(2\hbar)}
$$

The normalization constant comes directly from the Gaussian integral.

### Partition Functions

In [statistical mechanics](statistical-mechanics.md), the canonical partition function for a free particle:

$$
Z = \int_{-\infty}^{\infty} e^{-\beta p^2/(2m)} dp = \sqrt{2\pi m k_B T}
$$

### Path Integrals

The [path integral](path-integrals.md) for a free particle is an infinite-dimensional Gaussian:

$$
\langle x_f | e^{-iHt/\hbar} | x_i \rangle = \sqrt{\frac{m}{2\pi i\hbar t}} \exp\left(\frac{im(x_f - x_i)^2}{2\hbar t}\right)
$$

### Error Function

The **error function** is defined as the integral of the Gaussian:

$$
\text{erf}(x) = \frac{2}{\sqrt{\pi}} \int_0^x e^{-t^2} dt
$$

It satisfies $\text{erf}(\infty) = 1$ and $\text{erf}(-x) = -\text{erf}(x)$.

## Summary

| Result | Formula |
|--------|---------|
| Basic Gaussian | $\int_{-\infty}^{\infty} e^{-ax^2} dx = \sqrt{\pi/a}$ |
| With linear term | $\int_{-\infty}^{\infty} e^{-ax^2 + bx} dx = \sqrt{\pi/a} \, e^{b^2/(4a)}$ |
| Second moment | $\int_{-\infty}^{\infty} x^2 e^{-ax^2} dx = \frac{1}{2a}\sqrt{\pi/a}$ |
| $n$-dimensional | $\int_{\mathbb{R}^n} e^{-\mathbf{x}^T A \mathbf{x}} d^n x = \sqrt{\pi^n/\det A}$ |
| Complex | $\int_{-\infty}^{\infty} e^{iax^2} dx = \sqrt{i\pi/a}$ |

**The essential insight:** The Gaussian integral is solvable because squaring it creates circular symmetry, allowing conversion to polar coordinates. This trick—converting a difficult 1D problem to an easier 2D problem—appears throughout physics. The ubiquity of Gaussian integrals in physics reflects the central limit theorem: sums of many random variables become Gaussian, and quadratic approximations to potentials give harmonic oscillators.
