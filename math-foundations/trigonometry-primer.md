# Trigonometry Primer

This document covers the essential trigonometry needed for physics and [calculus](calculus-primer.md). Trigonometric functions describe periodic phenomena—oscillations, waves, rotations—which appear throughout physics from [harmonic oscillators](../classical-mechanics/harmonic-oscillator.md) to [quantum mechanics](../quantum-mechanics/quantum-mechanics.md).

## Angles and Their Measurement

### Degrees vs Radians

| Unit | Full circle | Right angle | Definition |
|------|-------------|-------------|------------|
| Degrees | 360° | 90° | Historical (Babylonian) |
| Radians | $2\pi$ | $\pi/2$ | Arc length / radius |

**Conversion:**
```math
\theta_{\text{rad}} = \frac{\pi}{180} \theta_{\text{deg}}, \qquad \theta_{\text{deg}} = \frac{180}{\pi} \theta_{\text{rad}}
```

**What this means:** Radians are the natural unit for calculus because they make derivatives simple: $(d/dx)\sin x = \cos x$ only works in radians. Physics always uses radians.

### Important Angles

| Degrees | Radians | Fraction of circle |
|---------|---------|-------------------|
| 0° | 0 | 0 |
| 30° | $\pi/6$ | 1/12 |
| 45° | $\pi/4$ | 1/8 |
| 60° | $\pi/3$ | 1/6 |
| 90° | $\pi/2$ | 1/4 |
| 180° | $\pi$ | 1/2 |
| 270° | $3\pi/2$ | 3/4 |
| 360° | $2\pi$ | 1 |

## The Trigonometric Functions

### Right Triangle Definitions

For a right triangle with angle $\theta$, opposite side $o$, adjacent side $a$, and hypotenuse $h$:

```math
\sin\theta = \frac{o}{h}, \qquad \cos\theta = \frac{a}{h}, \qquad \tan\theta = \frac{o}{a}
```

**Mnemonics:** SOH-CAH-TOA (Sine = Opposite/Hypotenuse, etc.)

### Unit Circle Definitions

For a point $(x, y)$ on the unit circle at angle $\theta$ from the positive x-axis:

```math
\cos\theta = x, \qquad \sin\theta = y, \qquad \tan\theta = \frac{y}{x}
```

**What this means:** The unit circle definition extends trig functions to all angles, not just acute angles in triangles. This is essential for physics.

### The Six Trigonometric Functions

| Function | Definition | Reciprocal |
|----------|------------|------------|
| $\sin\theta$ | opposite/hypotenuse | $\csc\theta = 1/\sin\theta$ |
| $\cos\theta$ | adjacent/hypotenuse | $\sec\theta = 1/\cos\theta$ |
| $\tan\theta$ | opposite/adjacent = $\sin\theta/\cos\theta$ | $\cot\theta = 1/\tan\theta$ |

### Special Values

| $\theta$ | $0$ | $\pi/6$ | $\pi/4$ | $\pi/3$ | $\pi/2$ |
|----------|-----|---------|---------|---------|---------|
| $\sin\theta$ | $0$ | $\frac{1}{2}$ | $\frac{\sqrt{2}}{2}$ | $\frac{\sqrt{3}}{2}$ | $1$ |
| $\cos\theta$ | $1$ | $\frac{\sqrt{3}}{2}$ | $\frac{\sqrt{2}}{2}$ | $\frac{1}{2}$ | $0$ |
| $\tan\theta$ | $0$ | $\frac{1}{\sqrt{3}}$ | $1$ | $\sqrt{3}$ | undefined |

**Memory trick:** For sine at $0, \pi/6, \pi/4, \pi/3, \pi/2$: $\frac{\sqrt{0}}{2}, \frac{\sqrt{1}}{2}, \frac{\sqrt{2}}{2}, \frac{\sqrt{3}}{2}, \frac{\sqrt{4}}{2}$.

## Fundamental Identities

### Pythagorean Identities

```math
\boxed{\sin^2\theta + \cos^2\theta = 1}
```

Dividing by $\cos^2\theta$ or $\sin^2\theta$:

```math
\tan^2\theta + 1 = \sec^2\theta, \qquad 1 + \cot^2\theta = \csc^2\theta
```

**What this means:** These follow directly from the unit circle: if $(\cos\theta, \sin\theta)$ is on the unit circle, then $\cos^2\theta + \sin^2\theta = 1$.

### Symmetry Identities

**Even/Odd:**
```math
\cos(-\theta) = \cos\theta \quad \text{(even)}, \qquad \sin(-\theta) = -\sin\theta \quad \text{(odd)}
```

**Periodicity:**
```math
\sin(\theta + 2\pi) = \sin\theta, \qquad \cos(\theta + 2\pi) = \cos\theta
```

**Shifts:**
```math
\sin(\theta + \pi/2) = \cos\theta, \qquad \cos(\theta + \pi/2) = -\sin\theta
```

```math
\sin(\theta + \pi) = -\sin\theta, \qquad \cos(\theta + \pi) = -\cos\theta
```

### Cofunction Identities

```math
\sin(\pi/2 - \theta) = \cos\theta, \qquad \cos(\pi/2 - \theta) = \sin\theta
```

**What this means:** Sine and cosine are the same function, just shifted by 90°. This is why they appear together throughout physics.

## Addition and Subtraction Formulas

### Angle Sum/Difference

```math
\boxed{\sin(\alpha \pm \beta) = \sin\alpha\cos\beta \pm \cos\alpha\sin\beta}
```

```math
\boxed{\cos(\alpha \pm \beta) = \cos\alpha\cos\beta \mp \sin\alpha\sin\beta}
```

```math
\tan(\alpha \pm \beta) = \frac{\tan\alpha \pm \tan\beta}{1 \mp \tan\alpha\tan\beta}
```

**What this means:** These formulas are essential for analyzing combined oscillations, wave interference, and rotations. They connect to [complex exponentials](algebra-primer.md): $e^{i(\alpha+\beta)} = e^{i\alpha}e^{i\beta}$.

### Double Angle Formulas

```math
\sin(2\theta) = 2\sin\theta\cos\theta
```

```math
\cos(2\theta) = \cos^2\theta - \sin^2\theta = 2\cos^2\theta - 1 = 1 - 2\sin^2\theta
```

```math
\tan(2\theta) = \frac{2\tan\theta}{1 - \tan^2\theta}
```

### Half Angle Formulas

```math
\sin^2(\theta/2) = \frac{1 - \cos\theta}{2}, \qquad \cos^2(\theta/2) = \frac{1 + \cos\theta}{2}
```

**What this means:** Half-angle formulas are useful for integration and for finding exact values of trig functions at unusual angles.

### Power-Reducing Formulas

```math
\sin^2\theta = \frac{1 - \cos(2\theta)}{2}, \qquad \cos^2\theta = \frac{1 + \cos(2\theta)}{2}
```

**What this means:** These convert powers of trig functions into linear combinations, which is essential for integration in [calculus](calculus-primer.md).

## Product and Sum Formulas

### Product to Sum

```math
\sin\alpha\cos\beta = \frac{1}{2}[\sin(\alpha+\beta) + \sin(\alpha-\beta)]
```

```math
\cos\alpha\cos\beta = \frac{1}{2}[\cos(\alpha-\beta) + \cos(\alpha+\beta)]
```

```math
\sin\alpha\sin\beta = \frac{1}{2}[\cos(\alpha-\beta) - \cos(\alpha+\beta)]
```

### Sum to Product

```math
\sin\alpha + \sin\beta = 2\sin\left(\frac{\alpha+\beta}{2}\right)\cos\left(\frac{\alpha-\beta}{2}\right)
```

```math
\cos\alpha + \cos\beta = 2\cos\left(\frac{\alpha+\beta}{2}\right)\cos\left(\frac{\alpha-\beta}{2}\right)
```

**What this means:** These formulas explain beats in acoustics—when two similar frequencies combine, you hear the sum frequency modulated by the difference frequency.

## Inverse Trigonometric Functions

### Definitions

| Function | Domain | Range | Meaning |
|----------|--------|-------|---------|
| $\arcsin x$ or $\sin^{-1}x$ | $[-1, 1]$ | $[-\pi/2, \pi/2]$ | Angle whose sine is $x$ |
| $\arccos x$ or $\cos^{-1}x$ | $[-1, 1]$ | $[0, \pi]$ | Angle whose cosine is $x$ |
| $\arctan x$ or $\tan^{-1}x$ | $(-\infty, \infty)$ | $(-\pi/2, \pi/2)$ | Angle whose tangent is $x$ |

**What this means:** Inverse trig functions answer "what angle has this ratio?" The restricted ranges ensure a unique answer.

### Important Values

| $x$ | $\arcsin x$ | $\arccos x$ | $\arctan x$ |
|-----|-------------|-------------|-------------|
| $0$ | $0$ | $\pi/2$ | $0$ |
| $1/2$ | $\pi/6$ | $\pi/3$ | — |
| $\sqrt{2}/2$ | $\pi/4$ | $\pi/4$ | — |
| $\sqrt{3}/2$ | $\pi/3$ | $\pi/6$ | — |
| $1$ | $\pi/2$ | $0$ | $\pi/4$ |

### Key Identity

```math
\arctan x + \arctan(1/x) = \begin{cases} \pi/2 & \text{if } x > 0 \\ -\pi/2 & \text{if } x < 0 \end{cases}
```

### Derivatives (Preview)

These are crucial in [calculus](calculus-primer.md):

```math
\frac{d}{dx}\arcsin x = \frac{1}{\sqrt{1-x^2}}, \qquad \frac{d}{dx}\arctan x = \frac{1}{1+x^2}
```

## Euler's Formula

The most beautiful equation connecting trigonometry to exponentials:

```math
\boxed{e^{i\theta} = \cos\theta + i\sin\theta}
```

where $i = \sqrt{-1}$. See [algebra primer](algebra-primer.md) for complex numbers and [Euler's formula](euler-formula.md) for full derivations and applications.

### Consequences

**Sine and cosine as exponentials:**
```math
\cos\theta = \frac{e^{i\theta} + e^{-i\theta}}{2}, \qquad \sin\theta = \frac{e^{i\theta} - e^{-i\theta}}{2i}
```

**Euler's identity:** Setting $\theta = \pi$:
```math
e^{i\pi} + 1 = 0
```

**What this means:** Euler's formula unifies trigonometry and exponentials. In [quantum mechanics](../quantum-mechanics/quantum-mechanics.md), wave functions are complex exponentials; their real and imaginary parts are the oscillating sine and cosine components.

### Why Euler's Formula Works

From Taylor series (see [calculus primer](calculus-primer.md)):

```math
e^{i\theta} = 1 + i\theta + \frac{(i\theta)^2}{2!} + \frac{(i\theta)^3}{3!} + \cdots
```

Since $i^2 = -1$, $i^3 = -i$, $i^4 = 1$, ..., the real and imaginary parts separate into the Taylor series for $\cos\theta$ and $\sin\theta$.

## Trigonometry in Physics

### Simple Harmonic Motion

The [harmonic oscillator](../classical-mechanics/harmonic-oscillator.md) has solution:

```math
x(t) = A\cos(\omega t + \phi)
```

where:
- $A$ = amplitude (maximum displacement)
- $\omega$ = angular frequency (radians per second)
- $\phi$ = phase (initial angle)

### Waves

A traveling wave:

```math
y(x, t) = A\sin(kx - \omega t)
```

where $k = 2\pi/\lambda$ is the wave number and $\lambda$ is wavelength.

### Rotations

In two dimensions, rotating a point $(x, y)$ by angle $\theta$:

```math
\begin{pmatrix} x' \\ y' \end{pmatrix} = \begin{pmatrix} \cos\theta & -\sin\theta \\ \sin\theta & \cos\theta \end{pmatrix} \begin{pmatrix} x \\ y \end{pmatrix}
```

See [linear algebra](linear-algebra.md) for matrix methods.

### Components of Vectors

A vector of magnitude $r$ at angle $\theta$:

```math
v_x = r\cos\theta, \qquad v_y = r\sin\theta
```

Conversely:

```math
r = \sqrt{v_x^2 + v_y^2}, \qquad \theta = \arctan(v_y/v_x)
```

## Small Angle Approximations

When $|\theta| \ll 1$ (in radians):

```math
\sin\theta \approx \theta, \qquad \cos\theta \approx 1 - \frac{\theta^2}{2}, \qquad \tan\theta \approx \theta
```

**What this means:** For small angles, the arc, chord, and tangent are nearly equal. This linearizes many physics problems—the simple pendulum equation $\ddot{\theta} = -(g/\ell)\sin\theta$ becomes $\ddot{\theta} = -(g/\ell)\theta$ for small oscillations.

## Law of Sines and Cosines

For any triangle with sides $a$, $b$, $c$ opposite angles $A$, $B$, $C$:

### Law of Sines

```math
\frac{a}{\sin A} = \frac{b}{\sin B} = \frac{c}{\sin C}
```

### Law of Cosines

```math
c^2 = a^2 + b^2 - 2ab\cos C
```

**What this means:** These generalize the Pythagorean theorem to non-right triangles. The law of cosines reduces to $c^2 = a^2 + b^2$ when $C = 90°$.

## Hyperbolic Functions

Related to trigonometric functions but using real exponentials:

```math
\sinh x = \frac{e^x - e^{-x}}{2}, \qquad \cosh x = \frac{e^x + e^{-x}}{2}
```

### Identities

```math
\cosh^2 x - \sinh^2 x = 1
```

Compare to $\cos^2\theta + \sin^2\theta = 1$—the sign difference is fundamental.

**What this means:** Hyperbolic functions describe hanging cables (catenaries), relativistic velocity addition, and appear in special relativity. The connection: $\cos(ix) = \cosh x$ and $\sin(ix) = i\sinh x$.

## Summary

| Concept | Key Formula | Where It's Used |
|---------|-------------|-----------------|
| Pythagorean identity | $\sin^2\theta + \cos^2\theta = 1$ | Everywhere |
| Angle addition | $\sin(\alpha+\beta) = \sin\alpha\cos\beta + \cos\alpha\sin\beta$ | Wave interference, rotations |
| Euler's formula | $e^{i\theta} = \cos\theta + i\sin\theta$ | Quantum mechanics, waves |
| Small angle | $\sin\theta \approx \theta$ for small $\theta$ | Pendulums, optics |
| Power reduction | $\sin^2\theta = (1-\cos 2\theta)/2$ | Integration |
| Inverse functions | $\arcsin, \arccos, \arctan$ | Solving for angles |

**The essential insight:** Trigonometric functions describe circles and oscillations—anything that repeats. Through Euler's formula, they connect to complex exponentials, unifying oscillations, rotations, and waves under a single framework. This is why trigonometry pervades physics from classical mechanics to quantum field theory.
