# Path Integrals in Quantum Mechanics

The path integral formulation, developed by Richard Feynman, provides an alternative to the Schrödinger equation that makes the connection to classical mechanics transparent. It sums over all possible paths, weighted by the exponential of the action—directly linking [quantum mechanics](quantum-mechanics.md) to [Lagrangian mechanics](lagrangian-mechanics.md).

## The Central Idea

In classical mechanics, a particle takes the path of least action. In quantum mechanics, **all paths contribute**, each weighted by a phase:

$$
e^{iS[x(t)]/\hbar}
$$

where $S[x(t)]$ is the action along the path $x(t)$.

**What this means:** The particle doesn't choose one path—it "explores" all paths simultaneously. Paths close to the classical path interfere constructively; far-from-classical paths interfere destructively. In the classical limit ($\hbar \to 0$), only the classical path survives.

## The Propagator

### Definition

The **propagator** (or kernel) $K(x_f, t_f; x_i, t_i)$ gives the amplitude for a particle to go from $(x_i, t_i)$ to $(x_f, t_f)$:

$$
\boxed{K(x_f, t_f; x_i, t_i) = \int \mathcal{D}[x(t)] \, e^{iS[x(t)]/\hbar}}
$$

The wave function evolves as:

$$
\psi(x_f, t_f) = \int_{-\infty}^{\infty} K(x_f, t_f; x_i, t_i) \, \psi(x_i, t_i) \, dx_i
$$

**What this means:** The propagator is the quantum analog of "how likely is this transition?" Every possible path from $(x_i, t_i)$ to $(x_f, t_f)$ contributes, weighted by $e^{iS/\hbar}$.

### Connection to Schrödinger

The propagator satisfies:

$$
\left(i\hbar\frac{\partial}{\partial t_f} - \hat{H}\right) K(x_f, t_f; x_i, t_i) = 0
$$

with initial condition:

$$
K(x_f, t_i; x_i, t_i) = \delta(x_f - x_i)
$$

**What this means:** The path integral and Schrödinger formulations are equivalent—they give the same physics. The path integral just organizes the calculation differently.

## Constructing the Path Integral

### Time-Slicing

Divide the time interval $[t_i, t_f]$ into $N$ slices of width $\epsilon = (t_f - t_i)/N$:

$$
t_i = t_0 < t_1 < t_2 < \cdots < t_N = t_f
$$

At each intermediate time $t_k$, insert a complete set of position states:

$$
K = \int dx_1 \, dx_2 \cdots dx_{N-1} \, K(x_N, t_N; x_{N-1}, t_{N-1}) \cdots K(x_1, t_1; x_0, t_0)
$$

### Infinitesimal Propagator

For small $\epsilon$, the propagator between adjacent times is:

$$
K(x_{k+1}, t_{k+1}; x_k, t_k) \approx \sqrt{\frac{m}{2\pi i\hbar\epsilon}} \exp\left[\frac{i}{\hbar}\epsilon L\left(\frac{x_{k+1} - x_k}{\epsilon}, \frac{x_{k+1} + x_k}{2}\right)\right]
$$

where $L$ is the Lagrangian.

### The Continuum Limit

Taking $N \to \infty$ (and $\epsilon \to 0$), the discrete sum becomes:

$$
S = \int_{t_i}^{t_f} L(\dot{x}, x) \, dt
$$

and the product of integrals becomes the functional integral:

$$
\int \mathcal{D}[x(t)] = \lim_{N \to \infty} \left(\frac{m}{2\pi i\hbar\epsilon}\right)^{N/2} \int dx_1 \cdots dx_{N-1}
$$

**What this means:** The path integral sums over all continuous paths $x(t)$, weighted by $e^{iS/\hbar}$. The measure $\mathcal{D}[x(t)]$ includes the normalization.

## The Free Particle

### Action

$$
S = \int_{t_i}^{t_f} \frac{1}{2}m\dot{x}^2 \, dt
$$

### Propagator

The path integral is Gaussian and can be evaluated exactly:

$$
\boxed{K_0(x_f, t_f; x_i, t_i) = \sqrt{\frac{m}{2\pi i\hbar(t_f - t_i)}} \exp\left[\frac{im(x_f - x_i)^2}{2\hbar(t_f - t_i)}\right]}
$$

**What this means:** The free particle propagator spreads out over time—a localized wave packet broadens. The phase depends on the classical action for the straight-line path.

### Verification

This matches the Schrödinger equation solution for a free particle and gives the correct momentum eigenstates.

## The Harmonic Oscillator

### Action

$$
S = \int_{t_i}^{t_f} \left(\frac{1}{2}m\dot{x}^2 - \frac{1}{2}m\omega^2 x^2\right) dt
$$

### Propagator

$$
K(x_f, t_f; x_i, t_i) = \sqrt{\frac{m\omega}{2\pi i\hbar\sin(\omega T)}} \exp\left[\frac{im\omega}{2\hbar\sin(\omega T)}\left((x_f^2 + x_i^2)\cos(\omega T) - 2x_f x_i\right)\right]
$$

where $T = t_f - t_i$.

**What this means:** The propagator oscillates with the natural frequency $\omega$. It becomes singular when $\omega T = n\pi$ (focusing points), reflecting the periodic nature of harmonic motion.

## The Classical Limit

### Stationary Phase Approximation

When $S \gg \hbar$, the integral is dominated by paths where the action is stationary:

$$
\frac{\delta S}{\delta x(t)} = 0
$$

This is exactly the classical equation of motion (Euler-Lagrange).

**What this means:** In the classical limit, the path integral reduces to the classical path. Quantum corrections come from fluctuations around this path.

### Semi-Classical Expansion

Expand around the classical path $x_{cl}(t)$:

$$
x(t) = x_{cl}(t) + y(t)
$$

The action becomes:

$$
S[x] = S[x_{cl}] + \frac{1}{2}\int dt_1 \, dt_2 \, y(t_1) \frac{\delta^2 S}{\delta x(t_1)\delta x(t_2)}\bigg|_{x_{cl}} y(t_2) + \cdots
$$

The leading term gives the classical phase; the Gaussian integral over $y$ gives quantum corrections.

## Euclidean Path Integrals

### Wick Rotation

Replacing $t \to -i\tau$ (imaginary time):

$$
e^{iS/\hbar} \to e^{-S_E/\hbar}
$$

where $S_E$ is the **Euclidean action**.

**What this means:** The oscillatory integral becomes exponentially damped, making it mathematically better-behaved. This is essential for statistical mechanics and quantum field theory.

### Connection to Statistical Mechanics

In [statistical mechanics](statistical-mechanics.md), the partition function is:

$$
Z = \text{Tr}(e^{-\beta H}) = \int \mathcal{D}[x(\tau)] \, e^{-S_E/\hbar}
$$

with periodic boundary conditions $x(0) = x(\beta\hbar)$.

**What this means:** Quantum statistical mechanics is equivalent to path integrals in imaginary time with periodic paths. Temperature corresponds to the period.

## Path Integrals in Phase Space

### Hamiltonian Form

The path integral can also be written in phase space:

$$
K = \int \mathcal{D}[x]\mathcal{D}[p] \, \exp\left[\frac{i}{\hbar}\int dt \left(p\dot{x} - H(x,p)\right)\right]
$$

**What this means:** This form directly connects to [Hamiltonian mechanics](hamiltonian-mechanics.md). Both position and momentum paths are integrated over.

### Gaussian Integration Over $p$

For Hamiltonians quadratic in $p$ (like $H = p^2/2m + V(x)$), the $p$ integral is Gaussian:

$$
\int \mathcal{D}[p] \exp\left[\frac{i}{\hbar}\int dt \left(p\dot{x} - \frac{p^2}{2m}\right)\right] \propto \exp\left[\frac{i}{\hbar}\int dt \, \frac{m\dot{x}^2}{2}\right]
$$

This recovers the Lagrangian form.

## Symmetries and Conserved Quantities

### Noether's Theorem in Path Integrals

If the action is invariant under a transformation $x \to x + \epsilon\delta x$:

$$
S[x + \epsilon\delta x] = S[x]
$$

then the corresponding current is conserved.

**What this means:** Path integrals make symmetries manifest. Time translation invariance gives energy conservation; space translation gives momentum conservation.

### Ward Identities

Symmetries in path integrals lead to **Ward identities**—constraints on correlation functions that are fundamental in quantum field theory.

## Applications

### Quantum Field Theory

The path integral extends naturally to fields $\phi(x,t)$:

$$
Z = \int \mathcal{D}[\phi] \, e^{iS[\phi]/\hbar}
$$

This is the foundation of modern particle physics.

### Gauge Theories

Path integrals handle gauge symmetries elegantly through Faddeev-Popov ghost fields.

### Instantons

Non-perturbative effects (like tunneling) are captured by **instantons**—classical solutions in imaginary time that contribute to the path integral.

### Numerical Methods

The Euclidean path integral enables **lattice Monte Carlo** simulations of quantum systems, crucial for QCD calculations.

## Comparison of Formulations

| Aspect | Schrödinger | Path Integral |
|--------|-------------|---------------|
| Central object | Wave function $\psi$ | Propagator $K$ |
| Equation | $i\hbar\partial_t\psi = H\psi$ | Sum over paths |
| Classical limit | Requires WKB | Stationary phase |
| Symmetries | Operators | Manifest in action |
| Field theory | Second quantization | Natural extension |
| Numerical methods | Time evolution | Monte Carlo |

**What this means:** The formulations are equivalent but suited to different problems. Path integrals excel for symmetries, gauge theories, and the classical limit.

## Summary

| Concept | Expression | Meaning |
|---------|------------|---------|
| Path integral | $K = \int \mathcal{D}[x] \, e^{iS/\hbar}$ | Sum over all paths |
| Action weight | $e^{iS[x]/\hbar}$ | Phase for each path |
| Classical limit | $\delta S = 0$ | Stationary phase gives classical path |
| Free propagator | $K_0 \propto e^{im(x_f-x_i)^2/2\hbar T}$ | Gaussian spreading |
| Euclidean | $t \to -i\tau$ | Connects to statistical mechanics |
| Phase space | $\int \mathcal{D}[x]\mathcal{D}[p]$ | Hamiltonian formulation |

**The essential insight:** The path integral reveals quantum mechanics as a sum over histories. Each path contributes a phase proportional to its action. Classical physics emerges when $\hbar$ is small—most paths cancel out, leaving only the classical trajectory. This formulation makes symmetries manifest, connects naturally to classical mechanics, and extends seamlessly to quantum field theory.
