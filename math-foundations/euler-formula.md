# Euler's Formula

Euler's formula is one of the most beautiful and useful results in mathematics, connecting exponentials, trigonometry, and complex numbers in a single elegant equation. It unifies seemingly disparate areas of mathematics and is essential throughout physics—from quantum mechanics to signal processing to electromagnetism. Prerequisites: [algebra](algebra-primer.md), [trigonometry](trigonometry-primer.md), [calculus](calculus-primer.md).

## The Formula

### Euler's Formula

```math
\boxed{e^{i\theta} = \cos\theta + i\sin\theta}
```

where $i = \sqrt{-1}$ is the imaginary unit and $\theta$ is a real number (angle in radians).

**What this means:** The complex exponential $e^{i\theta}$ traces out the unit circle in the complex plane as $\theta$ varies. At angle $\theta$, you're at the point $(\cos\theta, \sin\theta)$.

### Euler's Identity

Setting $\theta = \pi$:

```math
\boxed{e^{i\pi} + 1 = 0}
```

This single equation connects five fundamental constants:
- $e$ — the base of natural logarithms
- $i$ — the imaginary unit
- $\pi$ — the ratio of circumference to diameter
- $1$ — the multiplicative identity
- $0$ — the additive identity

**What this means:** This is often called "the most beautiful equation in mathematics." It shows that exponential growth, rotation, and the geometry of circles are all aspects of the same underlying structure.

## Derivations

### From Taylor Series

The most rigorous proof uses Taylor series. Recall:

```math
e^x = \sum_{n=0}^{\infty} \frac{x^n}{n!} = 1 + x + \frac{x^2}{2!} + \frac{x^3}{3!} + \cdots
```

Substituting $x = i\theta$:

```math
e^{i\theta} = \sum_{n=0}^{\infty} \frac{(i\theta)^n}{n!}
```

Using $i^0 = 1$, $i^1 = i$, $i^2 = -1$, $i^3 = -i$, $i^4 = 1$, ..., we can separate real and imaginary parts:

```math
e^{i\theta} = \left(1 - \frac{\theta^2}{2!} + \frac{\theta^4}{4!} - \cdots\right) + i\left(\theta - \frac{\theta^3}{3!} + \frac{\theta^5}{5!} - \cdots\right)
```

These are exactly the Taylor series for $\cos\theta$ and $\sin\theta$:

```math
\cos\theta = \sum_{n=0}^{\infty} \frac{(-1)^n \theta^{2n}}{(2n)!}, \quad \sin\theta = \sum_{n=0}^{\infty} \frac{(-1)^n \theta^{2n+1}}{(2n+1)!}
```

Therefore $e^{i\theta} = \cos\theta + i\sin\theta$.

### From Differential Equations

Define $f(\theta) = e^{i\theta}$. Then:

```math
\frac{df}{d\theta} = ie^{i\theta} = if(\theta)
```

Now define $g(\theta) = \cos\theta + i\sin\theta$. Then:

```math
\frac{dg}{d\theta} = -\sin\theta + i\cos\theta = i(\cos\theta + i\sin\theta) = ig(\theta)
```

Both $f$ and $g$ satisfy the same differential equation $y' = iy$ with the same initial condition $y(0) = 1$. By uniqueness of solutions, $f = g$.

### Geometric Intuition

Consider the derivative of $e^{i\theta}$:

```math
\frac{d}{d\theta}e^{i\theta} = ie^{i\theta}
```

Multiplying by $i$ rotates a complex number by $90°$ counterclockwise. So the velocity vector is always perpendicular to the position vector—this describes circular motion!

Starting at $e^{i \cdot 0} = 1$, the point moves counterclockwise around the unit circle at unit speed.

## Key Consequences

### Trigonometric Identities from Euler

Many trig identities become trivial using Euler's formula.

**Expressing trig functions as exponentials:**

```math
\boxed{\cos\theta = \frac{e^{i\theta} + e^{-i\theta}}{2}, \quad \sin\theta = \frac{e^{i\theta} - e^{-i\theta}}{2i}}
```

**Angle addition:**

```math
e^{i(\alpha + \beta)} = e^{i\alpha} e^{i\beta}
```

Expanding both sides:

```math
\cos(\alpha+\beta) + i\sin(\alpha+\beta) = (\cos\alpha + i\sin\alpha)(\cos\beta + i\sin\beta)
```

Multiplying out and matching real/imaginary parts gives the addition formulas:

```math
\cos(\alpha+\beta) = \cos\alpha\cos\beta - \sin\alpha\sin\beta
```
```math
\sin(\alpha+\beta) = \sin\alpha\cos\beta + \cos\alpha\sin\beta
```

**What this means:** Euler's formula reveals that trig identities are just properties of exponentials in disguise. The angle addition formulas follow from $e^{a+b} = e^a e^b$.

### De Moivre's Theorem

```math
\boxed{(\cos\theta + i\sin\theta)^n = \cos(n\theta) + i\sin(n\theta)}
```

**Proof:** $(e^{i\theta})^n = e^{in\theta}$

This makes computing powers of complex numbers trivial and gives formulas for $\cos(n\theta)$ and $\sin(n\theta)$.

**Example:** Find $\cos(3\theta)$ in terms of $\cos\theta$.

```math
\cos(3\theta) + i\sin(3\theta) = (\cos\theta + i\sin\theta)^3
```

Expanding the right side using the binomial theorem:
```math
= \cos^3\theta + 3i\cos^2\theta\sin\theta - 3\cos\theta\sin^2\theta - i\sin^3\theta
```

Real part:
```math
\cos(3\theta) = \cos^3\theta - 3\cos\theta\sin^2\theta = 4\cos^3\theta - 3\cos\theta
```

### Roots of Unity

The $n$th roots of unity are the solutions to $z^n = 1$:

```math
z_k = e^{2\pi i k/n} = \cos\frac{2\pi k}{n} + i\sin\frac{2\pi k}{n}, \quad k = 0, 1, \ldots, n-1
```

These are $n$ points equally spaced around the unit circle.

**Sum of roots:**
```math
\sum_{k=0}^{n-1} e^{2\pi ik/n} = 0
```

This is a geometric series with ratio $e^{2\pi i/n} \neq 1$, so the sum is $\frac{1 - e^{2\pi i}}{1 - e^{2\pi i/n}} = \frac{1-1}{1-e^{2\pi i/n}} = 0$.

## The Complex Exponential

### General Complex Exponentials

For any complex number $z = x + iy$:

```math
e^z = e^{x+iy} = e^x \cdot e^{iy} = e^x(\cos y + i\sin y)
```

So $|e^z| = e^x$ (the modulus) and $\arg(e^z) = y$ (the argument).

### Periodicity

```math
e^{i(\theta + 2\pi)} = e^{i\theta}
```

The complex exponential is periodic with period $2\pi i$:

```math
e^{z + 2\pi i} = e^z
```

### Complex Logarithm

If $w = e^z$, then $z = \ln w$. But since $e^z$ is periodic, the logarithm is multi-valued:

```math
\ln w = \ln|w| + i(\arg(w) + 2\pi k), \quad k \in \mathbb{Z}
```

The **principal value** uses $-\pi < \arg(w) \leq \pi$.

## Applications in Physics

### Oscillations and Waves

Simple harmonic motion:
```math
x(t) = A\cos(\omega t + \phi)
```

can be written as the real part of a complex exponential:
```math
x(t) = \text{Re}\left[Ae^{i(\omega t + \phi)}\right] = \text{Re}\left[\tilde{A}e^{i\omega t}\right]
```

where $\tilde{A} = Ae^{i\phi}$ is a complex amplitude.

**What this means:** Complex exponentials simplify oscillation problems. Instead of tracking amplitude and phase separately, use a single complex number. See [harmonic oscillator](../classical-mechanics/harmonic-oscillator.md).

### AC Circuits

In electrical engineering, voltages and currents are written as:
```math
V(t) = V_0 e^{i\omega t}, \quad I(t) = I_0 e^{i\omega t}
```

Impedances become complex numbers:
- Resistor: $Z_R = R$
- Capacitor: $Z_C = 1/(i\omega C)$
- Inductor: $Z_L = i\omega L$

Circuit analysis reduces to complex algebra.

### Fourier Analysis

Any periodic function can be decomposed into complex exponentials:

```math
f(x) = \sum_{n=-\infty}^{\infty} c_n e^{inx}
```

where the Fourier coefficients are:
```math
c_n = \frac{1}{2\pi} \int_{-\pi}^{\pi} f(x) e^{-inx} dx
```

This is cleaner than using separate sine and cosine terms. See [electromagnetic waves](../electromagnetism/electromagnetic-waves.md).

### Quantum Mechanics

In quantum mechanics, wave functions are complex:

```math
\psi(x,t) = Ae^{i(kx - \omega t)}
```

The time evolution operator is:
```math
e^{-iHt/\hbar}
```

where $H$ is the Hamiltonian. Euler's formula is everywhere in QM. See [quantum mechanics](../quantum-mechanics/quantum-mechanics.md).

### Rotation in the Complex Plane

Multiplication by $e^{i\theta}$ rotates a complex number by angle $\theta$:

```math
z' = e^{i\theta} z
```

If $z = re^{i\phi}$, then $z' = re^{i(\phi+\theta)}$.

This extends to rotation matrices in physics and computer graphics.

## Special Values

| $\theta$ | $e^{i\theta}$ | Decimal |
|----------|---------------|---------|
| $0$ | $1$ | $1$ |
| $\pi/6$ | $\frac{\sqrt{3}}{2} + \frac{i}{2}$ | $0.866 + 0.5i$ |
| $\pi/4$ | $\frac{1}{\sqrt{2}} + \frac{i}{\sqrt{2}}$ | $0.707 + 0.707i$ |
| $\pi/3$ | $\frac{1}{2} + \frac{i\sqrt{3}}{2}$ | $0.5 + 0.866i$ |
| $\pi/2$ | $i$ | $i$ |
| $\pi$ | $-1$ | $-1$ |
| $3\pi/2$ | $-i$ | $-i$ |
| $2\pi$ | $1$ | $1$ |

## Related Formulas

### Hyperbolic Functions

Just as $e^{i\theta}$ relates to circular functions, $e^x$ relates to hyperbolic functions:

```math
\cosh x = \frac{e^x + e^{-x}}{2}, \quad \sinh x = \frac{e^x - e^{-x}}{2}
```

The connection:
```math
\cos(ix) = \cosh x, \quad \sin(ix) = i\sinh x
```

### The General Exponential

For any complex $a$ and $b$:
```math
a^b = e^{b \ln a}
```

This requires choosing a branch of the logarithm, making $a^b$ multi-valued in general.

**Example:** What is $i^i$?
```math
i^i = e^{i \ln i} = e^{i \cdot i\pi/2} = e^{-\pi/2} \approx 0.208
```

Remarkably, $i^i$ is a real number!

## Summary

| Formula | Statement | Significance |
|---------|-----------|--------------|
| Euler's formula | $e^{i\theta} = \cos\theta + i\sin\theta$ | Connects exponentials and trig |
| Euler's identity | $e^{i\pi} + 1 = 0$ | Five fundamental constants |
| Inverse formulas | $\cos\theta = \frac{e^{i\theta}+e^{-i\theta}}{2}$ | Trig as exponentials |
| De Moivre | $(e^{i\theta})^n = e^{in\theta}$ | Powers and roots |
| Periodicity | $e^{i(\theta+2\pi)} = e^{i\theta}$ | $2\pi i$ is the period |

| Application | How Euler's Formula Helps |
|-------------|---------------------------|
| Trig identities | Become exponential algebra |
| Oscillations | Complex amplitude encodes phase |
| Fourier analysis | Clean basis of $e^{inx}$ |
| Quantum mechanics | Wave functions are complex |
| Rotations | Multiply by $e^{i\theta}$ |

**The essential insight:** Euler's formula reveals that exponentials, trigonometry, and complex numbers are three perspectives on the same mathematical structure. The exponential $e^{i\theta}$ moves around the unit circle, with $\cos\theta$ and $\sin\theta$ as its coordinates. This unification simplifies countless calculations—from proving trig identities to solving differential equations to understanding quantum mechanics. When you see oscillations, waves, or rotations, think $e^{i\theta}$.
