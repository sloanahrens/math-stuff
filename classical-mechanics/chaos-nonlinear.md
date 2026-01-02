# Chaos and Nonlinear Dynamics

Most physical systems are nonlinear, and nonlinearity can produce chaos—sensitive dependence on initial conditions that makes long-term prediction impossible despite deterministic dynamics. This document covers phase space, stability, bifurcations, strange attractors, and the KAM theorem. Prerequisites: [Hamiltonian mechanics](hamiltonian-mechanics.md), [Lagrangian mechanics](lagrangian-mechanics.md), [calculus](../math-foundations/calculus-primer.md).

## Phase Space

### Definition

For a system with $n$ degrees of freedom, the **phase space** is the $2n$-dimensional space of coordinates and momenta $(q_1, \ldots, q_n, p_1, \ldots, p_n)$.

Each point represents a complete state; evolution traces a trajectory.

### Hamiltonian Flow

The equations of motion:

```math
\dot{q}_i = \frac{\partial H}{\partial p_i}, \quad \dot{p}_i = -\frac{\partial H}{\partial q_i}
```

define a vector field on phase space. Trajectories never cross (uniqueness of solutions).

### Liouville's Theorem

```math
\boxed{\frac{d\rho}{dt} = 0}
```

Phase space volume is conserved under Hamiltonian flow. This is equivalent to:

```math
\nabla \cdot \mathbf{v} = \sum_i \left(\frac{\partial \dot{q}_i}{\partial q_i} + \frac{\partial \dot{p}_i}{\partial p_i}\right) = 0
```

**What this means:** Hamiltonian systems are incompressible in phase space—volumes can stretch and fold but not shrink. Dissipative systems violate this.

## Fixed Points and Stability

### Finding Fixed Points

A fixed point $\mathbf{x}^*$ satisfies:

```math
\dot{\mathbf{x}} = \mathbf{f}(\mathbf{x}^*) = 0
```

### Linear Stability Analysis

Near a fixed point, linearize:

```math
\dot{\boldsymbol{\xi}} = J \boldsymbol{\xi}
```

where $\boldsymbol{\xi} = \mathbf{x} - \mathbf{x}^*$ and $J_{ij} = \partial f_i/\partial x_j$ is the Jacobian.

Stability is determined by eigenvalues $\lambda$ of $J$:

| Eigenvalues | Fixed Point Type |
|-------------|------------------|
| All $\text{Re}(\lambda) < 0$ | Stable (attractor) |
| All $\text{Re}(\lambda) > 0$ | Unstable (repeller) |
| Mixed signs | Saddle point |
| Pure imaginary | Center (neutrally stable) |

### Classification in 2D

For a 2D system with trace $\tau = \lambda_1 + \lambda_2$ and determinant $\Delta = \lambda_1\lambda_2$:

| Region | Type |
|--------|------|
| $\Delta < 0$ | Saddle |
| $\Delta > 0$, $\tau < 0$ | Stable node/spiral |
| $\Delta > 0$, $\tau > 0$ | Unstable node/spiral |
| $\Delta > 0$, $\tau = 0$ | Center |

Spiral if $\tau^2 < 4\Delta$ (complex eigenvalues).

## Bifurcations

### Definition

A **bifurcation** is a qualitative change in dynamics as a parameter varies.

### Saddle-Node Bifurcation

```math
\dot{x} = r + x^2
```

- $r < 0$: two fixed points (stable and unstable)
- $r = 0$: one fixed point (saddle-node)
- $r > 0$: no fixed points

### Transcritical Bifurcation

```math
\dot{x} = rx - x^2
```

Two fixed points exchange stability at $r = 0$.

### Pitchfork Bifurcation

**Supercritical:**

```math
\dot{x} = rx - x^3
```

- $r < 0$: one stable fixed point at $x = 0$
- $r > 0$: $x = 0$ unstable, two stable at $x = \pm\sqrt{r}$

**Subcritical:**

```math
\dot{x} = rx + x^3
```

Unstable branches exist for $r < 0$; system can jump discontinuously.

### Hopf Bifurcation

```math
\boxed{\text{A fixed point loses stability as eigenvalues cross the imaginary axis}}
```

Creates or destroys a limit cycle.

**Example:**

```math
\dot{r} = \mu r - r^3, \quad \dot{\theta} = \omega
```

For $\mu > 0$: stable limit cycle with radius $\sqrt{\mu}$.

## Limit Cycles

### Definition

A **limit cycle** is an isolated closed trajectory in phase space.

- **Stable (attracting):** Nearby trajectories spiral in
- **Unstable (repelling):** Nearby trajectories spiral out
- **Semi-stable:** Attracting from one side

### Poincare-Bendixson Theorem

In 2D, if a trajectory stays in a bounded region without approaching a fixed point, it must approach a limit cycle.

**What this means:** Chaos requires at least 3 dimensions for continuous systems.

### Examples

- Van der Pol oscillator: self-sustained oscillations
- Predator-prey (Lotka-Volterra): population cycles
- Heart rhythms, neural oscillations

## Strange Attractors and Chaos

### Sensitive Dependence on Initial Conditions

**Chaos:** Nearby trajectories separate exponentially:

```math
|\delta\mathbf{x}(t)| \sim |\delta\mathbf{x}(0)| e^{\lambda t}
```

where $\lambda > 0$ is the Lyapunov exponent.

### Lyapunov Exponents

```math
\boxed{\lambda = \lim_{t \to \infty} \frac{1}{t} \ln\frac{|\delta\mathbf{x}(t)|}{|\delta\mathbf{x}(0)|}}
```

For an $n$-dimensional system, there are $n$ Lyapunov exponents $\lambda_1 \geq \lambda_2 \geq \cdots \geq \lambda_n$.

| System Type | Lyapunov Spectrum |
|-------------|-------------------|
| Fixed point | All $\lambda_i < 0$ |
| Limit cycle | One $\lambda = 0$, rest $< 0$ |
| Torus | Multiple $\lambda = 0$ |
| Strange attractor | At least one $\lambda > 0$ |

**What this means:** A positive Lyapunov exponent means chaos—the "butterfly effect" where small perturbations grow exponentially.

### Strange Attractors

A **strange attractor** is a fractal set in phase space that attracts trajectories.

Properties:
- Bounded in phase space
- Sensitive dependence (positive Lyapunov exponent)
- Fractal dimension (non-integer)
- Dense periodic orbits

### The Lorenz System

```math
\dot{x} = \sigma(y - x)
```

```math
\dot{y} = x(\rho - z) - y
```

```math
\dot{z} = xy - \beta z
```

For $\sigma = 10$, $\rho = 28$, $\beta = 8/3$: chaotic with strange attractor (the "Lorenz butterfly").

### The Rossler Attractor

```math
\dot{x} = -y - z, \quad \dot{y} = x + ay, \quad \dot{z} = b + z(x - c)
```

Simpler geometry than Lorenz; single-scroll attractor.

## Maps and Discrete Dynamics

### Poincare Sections

Reduce continuous flow to discrete map by recording intersections with a surface.

A limit cycle → fixed point of map
A torus → circle map
Strange attractor → strange set

### The Logistic Map

```math
\boxed{x_{n+1} = rx_n(1 - x_n)}
```

| $r$ Range | Behavior |
|-----------|----------|
| $0 < r < 1$ | Fixed point at 0 |
| $1 < r < 3$ | Stable fixed point $x^* = 1 - 1/r$ |
| $3 < r < 3.57$ | Period-doubling cascade |
| $r \approx 3.57$ | Onset of chaos |
| $r > 3.57$ | Chaos with periodic windows |

### Period-Doubling Route to Chaos

As parameter increases, stable fixed point → period-2 → period-4 → ... → chaos.

**Feigenbaum constant:**

```math
\delta = \lim_{n \to \infty} \frac{r_n - r_{n-1}}{r_{n+1} - r_n} \approx 4.669
```

This is universal for unimodal maps.

### The Henon Map

```math
x_{n+1} = 1 - ax_n^2 + y_n, \quad y_{n+1} = bx_n
```

For $a = 1.4$, $b = 0.3$: strange attractor with fractal structure.

## The KAM Theorem

### Integrable Systems

A Hamiltonian system with $n$ degrees of freedom is **integrable** if there exist $n$ independent constants of motion in involution.

Motion is confined to invariant tori in phase space.

### The KAM Theorem

```math
\boxed{\text{Most invariant tori survive small perturbations}}
```

More precisely: for a non-degenerate integrable Hamiltonian $H_0$ perturbed by $\epsilon H_1$:

- Tori with "sufficiently irrational" frequency ratios persist (deformed)
- Tori with rational frequency ratios break up
- For small $\epsilon$, most of phase space volume remains on tori

### Consequences

1. **Near-integrable systems are not ergodic:** Trajectories don't fill energy surface
2. **Arnold diffusion:** In 3+ dimensions, trajectories can slowly drift between surviving tori
3. **Stability of solar system:** KAM tori protect against secular instabilities

### Resonances

Tori break up when frequencies are commensurable:

```math
\mathbf{m} \cdot \boldsymbol{\omega} = 0
```

for integer vectors $\mathbf{m}$. This creates chains of islands and chaos.

## Fractal Dimensions

### Box-Counting Dimension

Cover the set with boxes of size $\epsilon$. If $N(\epsilon)$ is the number needed:

```math
\boxed{D_0 = \lim_{\epsilon \to 0} \frac{\ln N(\epsilon)}{\ln(1/\epsilon)}}
```

For strange attractors, $D_0$ is typically non-integer.

### Examples

| Set | Dimension |
|-----|-----------|
| Cantor set | $\ln 2/\ln 3 \approx 0.63$ |
| Koch curve | $\ln 4/\ln 3 \approx 1.26$ |
| Lorenz attractor | $\approx 2.06$ |
| Henon attractor | $\approx 1.26$ |

### Kaplan-Yorke Dimension

Relates dimension to Lyapunov exponents:

```math
D_{KY} = k + \frac{\sum_{i=1}^k \lambda_i}{|\lambda_{k+1}|}
```

where $k$ is largest integer such that $\sum_{i=1}^k \lambda_i \geq 0$.

## Physical Examples

### The Double Pendulum

Two coupled pendulums exhibit chaos for sufficient energy.

Equations of motion are coupled nonlinear ODEs with no closed-form solution.

Sensitive dependence: two nearly identical initial conditions diverge exponentially.

### Driven Damped Pendulum

```math
\ddot{\theta} + \gamma\dot{\theta} + \omega_0^2\sin\theta = f\cos(\omega t)
```

Shows period-doubling to chaos as driving amplitude increases.

### Three-Body Problem

Newton showed that 3 gravitating bodies generically exhibit chaotic motion.

This limits long-term solar system predictions (Lyapunov time ~5 million years).

### Turbulence

Fluid turbulence involves strange attractors in infinite-dimensional phase space.

The transition from laminar to turbulent flow often follows bifurcation sequences.

## Summary

| Concept | Description |
|---------|-------------|
| Phase space | $(q, p)$ space; trajectories don't cross |
| Fixed point | $\dot{\mathbf{x}} = 0$; stability from Jacobian eigenvalues |
| Bifurcation | Qualitative change as parameter varies |
| Limit cycle | Isolated closed orbit (stable or unstable) |
| Strange attractor | Fractal set with positive Lyapunov exponent |
| Lyapunov exponent | Rate of exponential separation of trajectories |
| KAM theorem | Most invariant tori survive small perturbations |

| Bifurcation Type | Normal Form |
|------------------|-------------|
| Saddle-node | $\dot{x} = r + x^2$ |
| Transcritical | $\dot{x} = rx - x^2$ |
| Pitchfork (super) | $\dot{x} = rx - x^3$ |
| Hopf | Complex eigenvalues cross imaginary axis |

| Chaotic System | Key Feature |
|----------------|-------------|
| Lorenz | Strange attractor, sensitive dependence |
| Logistic map | Period-doubling, Feigenbaum universality |
| Henon map | 2D strange attractor |
| Double pendulum | Mechanical chaos |

| Constant | Value |
|----------|-------|
| Feigenbaum $\delta$ | 4.669... |
| Feigenbaum $\alpha$ | 2.502... |

**The essential insight:** Determinism does not imply predictability. Nonlinear systems can exhibit sensitive dependence on initial conditions—the hallmark of chaos—where exponentially growing uncertainties make long-term prediction impossible. Strange attractors in phase space have fractal structure, and the route to chaos often follows universal patterns like period-doubling. Yet the KAM theorem shows that islands of regularity persist: most invariant tori of integrable systems survive perturbation. Understanding chaos is essential for weather prediction, turbulence, [celestial mechanics](central-forces.md), heart arrhythmias, and the foundations of [statistical mechanics](../thermodynamics/statistical-mechanics.md).
