# Lagrangian Mechanics

Lagrangian mechanics reformulates Newton's laws using energy rather than forces. It's more powerful for constrained systems, reveals deep connections to symmetry, and leads naturally to [Hamiltonian mechanics](hamiltonian-mechanics.md), [quantum mechanics](../quantum-mechanics/quantum-mechanics.md), and [path integrals](path-integrals.md). In general relativity, the same principle gives [geodesics](../relativity/geodesics.md)—the paths of freely falling objects. This document uses [calculus](../math-foundations/calculus-primer.md) extensively, particularly partial derivatives and the chain rule.

## The Principle of Least Action

### The Central Idea

Nature chooses the path that **extremizes** (usually minimizes) the **action**:

```math
S = \int_{t_1}^{t_2} L(q, \dot{q}, t) \, dt
```

where:
- $q = (q_1, q_2, \ldots, q_n)$ are **generalized coordinates**
- $\dot{q} = dq/dt$ are **generalized velocities**
- $L$ is the **Lagrangian**

**What this means:** Instead of asking "what forces act at each instant?", we ask "what path makes the total action stationary?" This seemingly different question leads to the same physics—but reveals deeper structure.

### The Lagrangian

For most mechanical systems:

```math
L = T - V
```

where $T$ is kinetic energy and $V$ is potential energy.

**What this means:** The Lagrangian is the difference between kinetic and potential energy. This might seem arbitrary, but it's what makes the principle work. The equations of motion emerge from requiring the action to be stationary.

## The Euler-Lagrange Equations

Requiring $\delta S = 0$ (the action is stationary under small path variations) yields:

```math
\boxed{\frac{d}{dt} \frac{\partial L}{\partial \dot{q}_i} - \frac{\partial L}{\partial q_i} = 0}
```

This is the **Euler-Lagrange equation**—one equation for each generalized coordinate $q_i$.

**What this means:** This single equation replaces Newton's $\mathbf{F} = m\mathbf{a}$. It automatically handles constraints, curvilinear coordinates, and gives the equations of motion in whatever coordinates you choose.

### Derivation Sketch

Consider a path $q(t)$ and a small variation $q(t) + \epsilon \eta(t)$ with $\eta(t_1) = \eta(t_2) = 0$ (endpoints fixed):

```math
\delta S = \int_{t_1}^{t_2} \left( \frac{\partial L}{\partial q} \eta + \frac{\partial L}{\partial \dot{q}} \dot{\eta} \right) dt
```

Integration by parts on the second term:

```math
\delta S = \int_{t_1}^{t_2} \left( \frac{\partial L}{\partial q} - \frac{d}{dt} \frac{\partial L}{\partial \dot{q}} \right) \eta \, dt
```

For $\delta S = 0$ for all $\eta(t)$, the bracket must vanish—giving the Euler-Lagrange equation.

## Example: Simple Harmonic Oscillator

See [harmonic oscillator](harmonic-oscillator.md) for a comprehensive treatment. For a mass $m$ on a spring with spring constant $k$:

```math
T = \frac{1}{2} m \dot{x}^2, \qquad V = \frac{1}{2} k x^2
```

```math
L = \frac{1}{2} m \dot{x}^2 - \frac{1}{2} k x^2
```

Euler-Lagrange equation:

```math
\frac{d}{dt} (m \dot{x}) - (-kx) = 0 \quad \Rightarrow \quad m \ddot{x} + kx = 0
```

This is the familiar $\ddot{x} = -\omega^2 x$ with $\omega = \sqrt{k/m}$.

## Example: Pendulum

For a pendulum of length $\ell$ and mass $m$, using angle $\theta$ as the coordinate:

```math
T = \frac{1}{2} m \ell^2 \dot{\theta}^2, \qquad V = -mg\ell \cos\theta
```

```math
L = \frac{1}{2} m \ell^2 \dot{\theta}^2 + mg\ell \cos\theta
```

Euler-Lagrange equation:

```math
m\ell^2 \ddot{\theta} + mg\ell \sin\theta = 0 \quad \Rightarrow \quad \ddot{\theta} = -\frac{g}{\ell} \sin\theta
```

**What this means:** We never had to decompose forces into components or worry about tension. The constraint (fixed length) is automatically handled by choosing $\theta$ as our coordinate.

## Generalized Coordinates

### Freedom of Choice

Generalized coordinates $q_i$ can be any parameters that specify the system's configuration:
- Cartesian coordinates $(x, y, z)$
- Angles $(\theta, \phi)$
- Arc lengths along curves
- Any combination

**What this means:** You're free to choose coordinates that match the problem's symmetry or constraints. A pendulum naturally uses $\theta$; planetary motion naturally uses $(r, \theta)$.

### Constraints Reduce Degrees of Freedom

If a system has $N$ particles but $k$ constraints:

```math
\text{degrees of freedom} = 3N - k
```

**Example:** A particle constrained to a sphere ($x^2 + y^2 + z^2 = R^2$) has $3 - 1 = 2$ degrees of freedom, naturally parametrized by $(\theta, \phi)$.

## Generalized Momentum

Define the **generalized (canonical) momentum** conjugate to $q_i$:

```math
p_i = \frac{\partial L}{\partial \dot{q}_i}
```

**What this means:** This generalizes the concept of momentum. For a free particle with $L = \frac{1}{2}m\dot{x}^2$, we get $p = m\dot{x}$ (ordinary momentum). But for other coordinates, $p_i$ might be angular momentum or something else entirely.

### Examples

| System | Coordinate | Lagrangian | Generalized Momentum |
|--------|------------|------------|---------------------|
| Free particle | $x$ | $\frac{1}{2}m\dot{x}^2$ | $p_x = m\dot{x}$ (linear momentum) |
| Rotating body | $\theta$ | $\frac{1}{2}I\dot{\theta}^2$ | $p_\theta = I\dot{\theta}$ (angular momentum) |
| Charged particle | $x$ | $\frac{1}{2}m\dot{x}^2 + qA_x\dot{x}$ | $p_x = m\dot{x} + qA_x$ (canonical momentum) |

## Noether's Theorem

**If the Lagrangian is invariant under a continuous symmetry, there is a corresponding conserved quantity.**

```math
\text{Symmetry} \longleftrightarrow \text{Conservation Law}
```

| Symmetry | Conserved Quantity |
|----------|-------------------|
| Time translation ($L$ doesn't depend on $t$) | Energy |
| Space translation ($L$ doesn't depend on $x$) | Linear momentum |
| Rotation ($L$ doesn't depend on $\theta$) | Angular momentum |

**What this means:** Conservation laws aren't accidents—they're consequences of symmetries in the Lagrangian. This is one of the deepest insights in physics, connecting the structure of spacetime to what quantities are conserved.

### Cyclic Coordinates

If $L$ doesn't depend on $q_i$ (but does depend on $\dot{q}_i$), then $q_i$ is **cyclic**:

```math
\frac{\partial L}{\partial q_i} = 0 \quad \Rightarrow \quad \frac{d}{dt} \frac{\partial L}{\partial \dot{q}_i} = 0 \quad \Rightarrow \quad p_i = \text{constant}
```

**What this means:** If a coordinate doesn't appear in the Lagrangian, its conjugate momentum is conserved. This is Noether's theorem in action.

## Energy Conservation

Define the **energy function**:

```math
h = \sum_i \dot{q}_i \frac{\partial L}{\partial \dot{q}_i} - L
```

If $L$ has no explicit time dependence ($\partial L / \partial t = 0$):

```math
\frac{dh}{dt} = 0
```

**What this means:** When the Lagrangian doesn't change with time, $h$ is conserved. For most systems, $h = T + V$ = total energy.

### When $h = E$

If the kinetic energy is a homogeneous quadratic function of velocities:

```math
T = \frac{1}{2} \sum_{ij} M_{ij}(q) \dot{q}_i \dot{q}_j
```

then $h = T + V = E$ (total mechanical energy).

## Lagrangian for Relativistic Systems

In special relativity, the free particle Lagrangian becomes:

```math
L = -m\sqrt{1 - v^2/c^2} \cdot c^2 = -mc^2\sqrt{1 - v^2/c^2}
```

In [natural units](../math-foundations/natural-units.md) with $c = 1$:

```math
L = -m\sqrt{1 - v^2}
```

The Euler-Lagrange equation gives:

```math
\frac{d}{dt} \frac{m v}{\sqrt{1 - v^2}} = 0
```

which is conservation of relativistic momentum $p = \gamma m v$.

## From Lagrangian to Hamiltonian

The Lagrangian formulation leads directly to the [Hamiltonian formulation](hamiltonian-mechanics.md) via the **Legendre transformation**:

```math
H(q, p, t) = \sum_i p_i \dot{q}_i - L(q, \dot{q}, t)
```

where $\dot{q}_i$ is expressed in terms of $p_i$ by inverting $p_i = \partial L / \partial \dot{q}_i$.

**What this means:** The Hamiltonian reformulates mechanics using position and momentum (rather than position and velocity). This is the natural framework for [quantum mechanics](../quantum-mechanics/quantum-mechanics.md), where position and momentum become operators.

## Summary

| Concept | Expression | Meaning |
|---------|------------|---------|
| Action | $S = \int L \, dt$ | Quantity nature extremizes |
| Lagrangian | $L = T - V$ | Kinetic minus potential energy |
| Euler-Lagrange | $\frac{d}{dt}\frac{\partial L}{\partial \dot{q}} = \frac{\partial L}{\partial q}$ | Equations of motion |
| Generalized momentum | $p_i = \frac{\partial L}{\partial \dot{q}_i}$ | Conjugate to coordinate $q_i$ |
| Noether's theorem | Symmetry ↔ Conservation | Deep structure of physics |

**The essential insight:** The principle of least action unifies mechanics under a single variational principle. It reveals conservation laws as consequences of symmetries and provides the foundation for all of modern theoretical physics.
