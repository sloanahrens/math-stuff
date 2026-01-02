# Newtonian Mechanics

Newton's laws form the foundation of classical mechanics. They describe how forces cause motion and establish the conservation laws that govern physical systems. This document introduces the concepts that are reformulated in [Lagrangian](lagrangian-mechanics.md) and [Hamiltonian](hamiltonian-mechanics.md) mechanics. Prerequisites: [calculus](../math-foundations/calculus-primer.md) and [vector calculus](../math-foundations/vector-calculus.md).

## Newton's Three Laws

### First Law (Inertia)

> An object remains at rest or in uniform motion unless acted upon by a net external force.

```math
\mathbf{F}_{\text{net}} = 0 \quad \Rightarrow \quad \mathbf{v} = \text{constant}
```

**What this means:** This defines **inertial reference frames**—frames where free particles move in straight lines at constant speed. Newton's laws only hold in inertial frames.

### Second Law (F = ma)

```math
\boxed{\mathbf{F} = m\mathbf{a} = m\frac{d\mathbf{v}}{dt} = \frac{d\mathbf{p}}{dt}}
```

where $\mathbf{p} = m\mathbf{v}$ is **momentum**.

**What this means:** Force causes acceleration, not velocity. The more massive an object, the more force needed for the same acceleration.

### Third Law (Action-Reaction)

> For every action, there is an equal and opposite reaction.

```math
\mathbf{F}_{12} = -\mathbf{F}_{21}
```

**What this means:** Forces come in pairs. When you push on a wall, it pushes back on you with equal force.

## Kinematics

### Position, Velocity, Acceleration

```math
\mathbf{v} = \frac{d\mathbf{r}}{dt}, \qquad \mathbf{a} = \frac{d\mathbf{v}}{dt} = \frac{d^2\mathbf{r}}{dt^2}
```

### Constant Acceleration

For constant $\mathbf{a}$:

```math
\mathbf{v}(t) = \mathbf{v}_0 + \mathbf{a}t
```

```math
\mathbf{r}(t) = \mathbf{r}_0 + \mathbf{v}_0 t + \frac{1}{2}\mathbf{a}t^2
```

```math
v^2 = v_0^2 + 2\mathbf{a} \cdot (\mathbf{r} - \mathbf{r}_0)
```

### Projectile Motion

Near Earth's surface with $\mathbf{g}$ downward:

```math
x(t) = v_0 \cos\theta \cdot t, \qquad y(t) = v_0 \sin\theta \cdot t - \frac{1}{2}gt^2
```

Range: $R = \frac{v_0^2 \sin(2\theta)}{g}$ (maximum at $\theta = 45°$)

## Common Forces

### Gravity (Near Earth)

```math
\mathbf{F} = m\mathbf{g}, \qquad g \approx 9.8 \text{ m/s}^2
```

### Universal Gravitation

```math
\mathbf{F} = -\frac{GMm}{r^2}\hat{\mathbf{r}}
```

See [central forces](central-forces.md) for orbital mechanics.

### Normal Force

Perpendicular to surface, adjusts to prevent interpenetration:

```math
N = mg\cos\theta \quad \text{(on incline)}
```

### Friction

**Static:** $f_s \leq \mu_s N$ (prevents sliding)

**Kinetic:** $f_k = \mu_k N$ (opposes sliding)

**What this means:** Static friction is whatever it needs to be up to a maximum. Kinetic friction is constant once sliding begins.

### Spring Force (Hooke's Law)

```math
F = -kx
```

This leads to the [harmonic oscillator](harmonic-oscillator.md)—one of the most important systems in physics.

### Tension

Force transmitted through strings, ropes, cables. For massless strings, tension is constant throughout.

### Drag

At low speed (Stokes): $F_d = -b\mathbf{v}$

At high speed: $F_d = -\frac{1}{2}C_d \rho A v^2$

## Work and Energy

### Work

```math
W = \int_C \mathbf{F} \cdot d\mathbf{r}
```

For constant force: $W = \mathbf{F} \cdot \Delta\mathbf{r} = F d \cos\theta$

**What this means:** Work is force times displacement in the direction of force. Work transfers energy.

### Kinetic Energy

```math
T = \frac{1}{2}mv^2
```

**Work-Energy Theorem:**

```math
W_{\text{net}} = \Delta T = T_f - T_i
```

### Conservative Forces and Potential Energy

A force is **conservative** if the work done is path-independent:

```math
\oint \mathbf{F} \cdot d\mathbf{r} = 0
```

Equivalently, $\mathbf{F} = -\nabla V$ for some potential energy $V$.

**Common potentials:**

| Force | Potential Energy |
|-------|------------------|
| Gravity (uniform) | $V = mgh$ |
| Gravity (universal) | $V = -GMm/r$ |
| Spring | $V = \frac{1}{2}kx^2$ |
| Electrostatic | $V = kq_1q_2/r$ |

### Conservation of Energy

For conservative forces:

```math
E = T + V = \text{constant}
```

**What this means:** Energy transforms between kinetic and potential but is never created or destroyed. This is one of the most powerful principles in physics.

## Momentum

### Linear Momentum

```math
\mathbf{p} = m\mathbf{v}
```

Newton's second law: $\mathbf{F} = \frac{d\mathbf{p}}{dt}$

### Conservation of Momentum

If $\mathbf{F}_{\text{ext}} = 0$:

```math
\mathbf{p}_{\text{total}} = \sum_i m_i \mathbf{v}_i = \text{constant}
```

**What this means:** In an isolated system, total momentum is conserved. This follows from Newton's third law.

### Impulse

```math
\mathbf{J} = \int \mathbf{F} \, dt = \Delta\mathbf{p}
```

### Collisions

**Elastic:** Both momentum and kinetic energy conserved

**Inelastic:** Only momentum conserved; some kinetic energy lost

**Perfectly inelastic:** Objects stick together; maximum kinetic energy loss

## Angular Motion

### Angular Momentum

```math
\mathbf{L} = \mathbf{r} \times \mathbf{p}
```

### Torque

```math
\boldsymbol{\tau} = \mathbf{r} \times \mathbf{F} = \frac{d\mathbf{L}}{dt}
```

### Conservation of Angular Momentum

If $\boldsymbol{\tau}_{\text{ext}} = 0$:

```math
\mathbf{L} = \text{constant}
```

**What this means:** Angular momentum is conserved in the absence of external torques. This explains why planets orbit in planes, ice skaters spin faster when they pull in their arms, and gyroscopes maintain orientation.

## Rotational Motion

### Moment of Inertia

```math
I = \sum_i m_i r_i^2 = \int r^2 \, dm
```

| Object | Moment of Inertia |
|--------|-------------------|
| Point mass | $mr^2$ |
| Rod (center) | $\frac{1}{12}ML^2$ |
| Rod (end) | $\frac{1}{3}ML^2$ |
| Disk/cylinder | $\frac{1}{2}MR^2$ |
| Sphere (solid) | $\frac{2}{5}MR^2$ |
| Sphere (hollow) | $\frac{2}{3}MR^2$ |

### Rotational Dynamics

```math
\tau = I\alpha
```

where $\alpha = d\omega/dt$ is angular acceleration.

### Rotational Kinetic Energy

```math
T_{\text{rot}} = \frac{1}{2}I\omega^2
```

**Rolling without slipping:** $v = \omega R$, total energy $T = \frac{1}{2}mv^2 + \frac{1}{2}I\omega^2$

## Center of Mass

### Definition

```math
\mathbf{R}_{\text{cm}} = \frac{1}{M}\sum_i m_i \mathbf{r}_i = \frac{1}{M}\int \mathbf{r} \, dm
```

### Motion of Center of Mass

```math
M\mathbf{a}_{\text{cm}} = \mathbf{F}_{\text{ext}}
```

**What this means:** The center of mass moves as if all mass were concentrated there with all external forces applied to it. Internal forces don't affect CM motion.

## Non-Inertial Frames

### Accelerating Frame

In a frame accelerating at $\mathbf{a}_0$, add a **pseudo-force**:

```math
\mathbf{F}_{\text{pseudo}} = -m\mathbf{a}_0
```

### Rotating Frame

In a frame rotating at $\boldsymbol{\omega}$:

**Centrifugal force:** $\mathbf{F}_{\text{cf}} = m\omega^2 \mathbf{r}_\perp$ (outward)

**Coriolis force:** $\mathbf{F}_{\text{Cor}} = -2m\boldsymbol{\omega} \times \mathbf{v}$

**What this means:** These aren't "real" forces—they arise from the non-inertial reference frame. But for observers in that frame, they're indistinguishable from real forces.

## Limitations of Newtonian Mechanics

| Regime | Replacement |
|--------|-------------|
| High speeds ($v \sim c$) | [Special relativity](../relativity/special-relativity.md) |
| Strong gravity | General relativity |
| Small scales ($\sim \hbar$) | [Quantum mechanics](../quantum-mechanics/quantum-mechanics.md) |

**What this means:** Newtonian mechanics is an approximation valid for everyday speeds, weak gravity, and macroscopic objects. It remains extremely useful and is the foundation for the more advanced formulations.

## Connection to Advanced Formulations

### Why Reformulate?

Newton's laws work well but have limitations:
- Forces must be known explicitly
- Constraints are handled awkwardly
- No direct connection to symmetries and conservation laws

### Lagrangian Approach

[Lagrangian mechanics](lagrangian-mechanics.md) uses $L = T - V$ and extremizes the action:

```math
\delta \int L \, dt = 0
```

**Advantages:** Handles constraints naturally, works in any coordinates, connects symmetries to conservation laws (Noether's theorem).

### Hamiltonian Approach

[Hamiltonian mechanics](hamiltonian-mechanics.md) uses $H = T + V$ in phase space $(q, p)$:

```math
\dot{q} = \frac{\partial H}{\partial p}, \qquad \dot{p} = -\frac{\partial H}{\partial q}
```

**Advantages:** Natural framework for quantum mechanics, reveals geometric structure, powerful for statistical mechanics.

## Summary

| Concept | Formula | Meaning |
|---------|---------|---------|
| Newton's 2nd law | $\mathbf{F} = m\mathbf{a}$ | Force causes acceleration |
| Momentum | $\mathbf{p} = m\mathbf{v}$ | "Quantity of motion" |
| Kinetic energy | $T = \frac{1}{2}mv^2$ | Energy of motion |
| Work | $W = \int \mathbf{F} \cdot d\mathbf{r}$ | Force times displacement |
| Conservative force | $\mathbf{F} = -\nabla V$ | Derivable from potential |
| Angular momentum | $\mathbf{L} = \mathbf{r} \times \mathbf{p}$ | Rotational momentum |
| Torque | $\boldsymbol{\tau} = \mathbf{r} \times \mathbf{F}$ | Rotational force |

**The essential insight:** Newton's laws provide a complete framework for classical mechanics: force determines acceleration, and conservation of energy, momentum, and angular momentum constrain motion. These concepts—reformulated in the Lagrangian and Hamiltonian frameworks—extend to quantum mechanics and field theory, making Newtonian mechanics the essential starting point for all of theoretical physics.
