# Calculus Primer

This document covers the essential calculus needed for physics: derivatives, integrals, and their multivariable extensions. These tools underpin [Lagrangian mechanics](lagrangian-mechanics.md), [Hamiltonian mechanics](hamiltonian-mechanics.md), [quantum mechanics](quantum-mechanics.md), and virtually every physics document in this collection.

## Derivatives

### The Basic Idea

The **derivative** measures the instantaneous rate of change of a function:

$$
\frac{df}{dx} = \lim_{h \to 0} \frac{f(x+h) - f(x)}{h}
$$

**What this means:** If $f(x)$ is position, $df/dx$ is velocity. If $f(x)$ is potential energy, $-df/dx$ is force. Derivatives tell you how fast things change.

### Notation

| Notation | Meaning |
|----------|---------|
| $\frac{df}{dx}$ or $f'(x)$ | Derivative of $f$ with respect to $x$ |
| $\frac{d^2f}{dx^2}$ or $f''(x)$ | Second derivative |
| $\dot{x}$ | Time derivative $dx/dt$ (physics notation) |
| $\ddot{x}$ | Second time derivative $d^2x/dt^2$ |

### Essential Derivatives

| Function | Derivative |
|----------|------------|
| $x^n$ | $nx^{n-1}$ |
| $e^x$ | $e^x$ |
| $\ln x$ | $1/x$ |
| $\sin x$ | $\cos x$ |
| $\cos x$ | $-\sin x$ |
| $e^{ax}$ | $ae^{ax}$ |

### Rules

**Sum rule:**
$$
\frac{d}{dx}(f + g) = \frac{df}{dx} + \frac{dg}{dx}
$$

**Product rule:**
$$
\frac{d}{dx}(fg) = f\frac{dg}{dx} + g\frac{df}{dx}
$$

**Chain rule:**
$$
\frac{d}{dx}f(g(x)) = \frac{df}{dg}\frac{dg}{dx}
$$

**What this means:** The chain rule is essential for physics. If position depends on time, and energy depends on position, then energy's time dependence is $dE/dt = (dE/dx)(dx/dt)$.

### Example: Simple Harmonic Motion

For $x(t) = A\cos(\omega t)$:

$$
\dot{x} = -A\omega\sin(\omega t), \qquad \ddot{x} = -A\omega^2\cos(\omega t) = -\omega^2 x
$$

This gives $\ddot{x} = -\omega^2 x$, the equation of simple harmonic motion.

## Integrals

### The Basic Idea

The **integral** is the "reverse" of differentiation and computes accumulated quantities:

$$
\int_a^b f(x) \, dx = \text{area under } f(x) \text{ from } a \text{ to } b
$$

**What this means:** If velocity is $v(t)$, then $\int v \, dt$ is displacement. If force is $F(x)$, then $\int F \, dx$ is work.

### Fundamental Theorem of Calculus

$$
\int_a^b \frac{df}{dx} \, dx = f(b) - f(a)
$$

**What this means:** Integration and differentiation are inverses. This connects local rates of change to global accumulated effects.

### Essential Integrals

| Function | Integral |
|----------|----------|
| $x^n$ ($n \neq -1$) | $\frac{x^{n+1}}{n+1}$ |
| $1/x$ | $\ln|x|$ |
| $e^{ax}$ | $\frac{1}{a}e^{ax}$ |
| $\sin x$ | $-\cos x$ |
| $\cos x$ | $\sin x$ |

### Gaussian Integral

One of the most important integrals in physics:

$$
\boxed{\int_{-\infty}^{\infty} e^{-ax^2} dx = \sqrt{\frac{\pi}{a}}}
$$

This appears in [quantum mechanics](quantum-mechanics.md), [statistical mechanics](statistical-mechanics.md), and [path integrals](path-integrals.md). See [Gaussian integral](gaussian-integral.md) for the proof and generalizations.

### Integration by Parts

$$
\int u \, dv = uv - \int v \, du
$$

**What this means:** This is the integral version of the product rule. It's essential for deriving the [Euler-Lagrange equations](lagrangian-mechanics.md).

## Partial Derivatives

### Functions of Multiple Variables

For $f(x, y)$, the **partial derivative** with respect to $x$ treats $y$ as constant:

$$
\frac{\partial f}{\partial x} = \lim_{h \to 0} \frac{f(x+h, y) - f(x, y)}{h}
$$

**Notation:** $\partial f/\partial x$, $f_x$, or $\partial_x f$.

### Example

For $f(x, y) = x^2y + y^3$:

$$
\frac{\partial f}{\partial x} = 2xy, \qquad \frac{\partial f}{\partial y} = x^2 + 3y^2
$$

### The Total Derivative

If $f$ depends on $x$, $y$, and $t$, and $x$ and $y$ themselves depend on $t$:

$$
\frac{df}{dt} = \frac{\partial f}{\partial x}\frac{dx}{dt} + \frac{\partial f}{\partial y}\frac{dy}{dt} + \frac{\partial f}{\partial t}
$$

**What this means:** This is the multivariable chain rule. It appears throughout [Lagrangian](lagrangian-mechanics.md) and [Hamiltonian](hamiltonian-mechanics.md) mechanics.

### Mixed Partials

For well-behaved functions:

$$
\frac{\partial^2 f}{\partial x \partial y} = \frac{\partial^2 f}{\partial y \partial x}
$$

**What this means:** The order of differentiation doesn't matter. This symmetry is used extensively in thermodynamics and mechanics.

## Taylor Series

### Expanding Functions

Any smooth function can be approximated near a point $a$:

$$
f(x) = f(a) + f'(a)(x-a) + \frac{f''(a)}{2!}(x-a)^2 + \frac{f'''(a)}{3!}(x-a)^3 + \cdots
$$

**What this means:** Taylor series let us approximate complicated functions with polynomials. This is how we derive small-angle approximations, perturbation expansions, and semiclassical limits.

### Important Expansions (around $x = 0$)

$$
e^x = 1 + x + \frac{x^2}{2!} + \frac{x^3}{3!} + \cdots
$$

$$
\sin x = x - \frac{x^3}{3!} + \frac{x^5}{5!} - \cdots
$$

$$
\cos x = 1 - \frac{x^2}{2!} + \frac{x^4}{4!} - \cdots
$$

$$
(1+x)^n \approx 1 + nx + \frac{n(n-1)}{2}x^2 + \cdots \quad \text{for } |x| \ll 1
$$

$$
\frac{1}{1-x} = 1 + x + x^2 + x^3 + \cdots \quad \text{for } |x| < 1
$$

### Physics Application

For small velocities $v \ll c$, the relativistic gamma factor:

$$
\gamma = \frac{1}{\sqrt{1-v^2/c^2}} \approx 1 + \frac{1}{2}\frac{v^2}{c^2} + \cdots
$$

This shows how relativistic energy $\gamma mc^2$ reduces to rest energy plus classical kinetic energy.

## Differential Equations

### Ordinary Differential Equations (ODEs)

An ODE relates a function to its derivatives. The order is the highest derivative present.

**First-order, separable:**
$$
\frac{dy}{dx} = f(x)g(y) \quad \Rightarrow \quad \int \frac{dy}{g(y)} = \int f(x) \, dx
$$

**Second-order, constant coefficients:**
$$
\frac{d^2y}{dx^2} + \omega^2 y = 0 \quad \Rightarrow \quad y = A\cos(\omega x) + B\sin(\omega x)
$$

**What this means:** Most physics equations are differential equations. Newton's second law, the Schrödinger equation, and Maxwell's equations are all differential equations.

### The Harmonic Oscillator Equation

$$
\ddot{x} + \omega^2 x = 0
$$

Solutions: $x(t) = A\cos(\omega t + \phi)$ or equivalently $x(t) = Ce^{i\omega t} + De^{-i\omega t}$.

**What this means:** This equation appears everywhere—springs, pendulums, circuits, quantum wells, field modes. Understanding it is essential for physics.

### Exponential Growth and Decay

$$
\frac{dy}{dt} = \pm ky \quad \Rightarrow \quad y(t) = y_0 e^{\pm kt}
$$

This describes radioactive decay, population growth, and thermal equilibration.

## Multivariable Integration

### Double and Triple Integrals

For functions of multiple variables:

$$
\iint_R f(x,y) \, dA, \qquad \iiint_V f(x,y,z) \, dV
$$

**What this means:** These compute volumes, masses, charges, and other accumulated quantities over regions.

### Jacobians and Coordinate Changes

When changing variables from $(x, y)$ to $(u, v)$:

$$
dA = dx \, dy = \left|\frac{\partial(x,y)}{\partial(u,v)}\right| du \, dv
$$

The **Jacobian** is the determinant:

$$
\frac{\partial(x,y)}{\partial(u,v)} = \begin{vmatrix} \frac{\partial x}{\partial u} & \frac{\partial x}{\partial v} \\ \frac{\partial y}{\partial u} & \frac{\partial y}{\partial v} \end{vmatrix}
$$

### Common Coordinate Systems

**Polar coordinates** ($x = r\cos\theta$, $y = r\sin\theta$):
$$
dA = r \, dr \, d\theta
$$

**Spherical coordinates** ($x = r\sin\theta\cos\phi$, etc.):
$$
dV = r^2 \sin\theta \, dr \, d\theta \, d\phi
$$

**What this means:** Choosing coordinates that match a problem's symmetry simplifies integrals enormously. The [hydrogen atom](hydrogen-atom.md) is solvable because of spherical symmetry.

## Summary

| Concept | Key Formula | Where It's Used |
|---------|-------------|-----------------|
| Derivative | $df/dx = \lim_{h\to 0}(f(x+h)-f(x))/h$ | Everywhere |
| Chain rule | $df/dx = (df/dg)(dg/dx)$ | Lagrangian, Hamiltonian |
| Integral | $\int_a^b f \, dx$ = area | Action, work, probability |
| Gaussian | $\int e^{-ax^2} = \sqrt{\pi/a}$ | QM, stat mech, path integrals |
| Partial derivative | $\partial f/\partial x$ (hold $y$ fixed) | Multivariable physics |
| Taylor series | $f(x) \approx f(a) + f'(a)(x-a) + \cdots$ | Approximations |
| Harmonic oscillator | $\ddot{x} + \omega^2 x = 0$ | Fundamental to all physics |

**The essential insight:** Calculus is the language of change. Derivatives describe instantaneous rates; integrals accumulate effects over time or space. Physics is fundamentally about how things change, which is why calculus pervades every topic.
