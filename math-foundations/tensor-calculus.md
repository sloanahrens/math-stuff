# Tensor Calculus: A Primer

This document introduces tensors—the mathematical objects that describe physical quantities in a coordinate-independent way. It builds on [linear algebra](linear-algebra.md) (matrices, transformations) and [calculus](calculus-primer.md) (partial derivatives). Tensors are essential for [differential forms](differential-forms.md), [special relativity](../relativity/special-relativity.md), [gravitational waves](../relativity/gravitational-waves.md), [geodesics](../relativity/geodesics.md), and general relativity ([Schwarzschild](../relativity/schwarzschild-solution.md), [Kerr](../relativity/kerr-metric.md)).

## Why Tensors?

Physics shouldn't depend on how we choose to describe it. If I measure a force, its magnitude is the same whether I use Cartesian or spherical coordinates. **Tensors** are objects that transform in a specific way under coordinate changes, ensuring physical laws remain invariant.

### The Problem with Vectors

In elementary physics, we write vectors as column matrices:

```math
\vec{v} = \begin{pmatrix} v_x \\ v_y \\ v_z \end{pmatrix}
```

But this depends on our coordinate choice. The *same* physical vector looks different in different coordinates. We need a formalism that captures the *intrinsic* object, not just its coordinate representation.

## Coordinate Transformations

Consider two coordinate systems $x^\mu$ and $x'^\mu$ (where $\mu = 0, 1, 2, 3$ for spacetime, or $\mu = 1, 2, 3$ for space). The transformation between them is:

```math
x'^\mu = x'^\mu(x^0, x^1, x^2, x^3)
```

The **Jacobian matrix** encodes how coordinates change:

```math
\frac{\partial x'^\mu}{\partial x^\nu}
```

This matrix tells us: if I move a small amount $dx^\nu$ in the old coordinates, how much do I move in the new coordinates?

## Index Notation

### Einstein Summation Convention

Repeated indices (one up, one down) are summed:

```math
A^\mu B_\mu \equiv \sum_{\mu=0}^{3} A^\mu B_\mu = A^0 B_0 + A^1 B_1 + A^2 B_2 + A^3 B_3
```

**What this means:** Writing $A^\mu B_\mu$ automatically implies summation. This keeps equations compact—no $\sum$ symbols cluttering everything.

### Upper vs. Lower Indices

- **Upper indices** ($A^\mu$): contravariant components
- **Lower indices** ($A_\mu$): covariant components

These transform *oppositely* under coordinate changes, which is why contracting one of each produces an invariant.

## Contravariant Vectors

A **contravariant vector** $V^\mu$ transforms like coordinate differentials:

```math
V'^\mu = \frac{\partial x'^\mu}{\partial x^\nu} V^\nu
```

**What this means:** Think of velocity $dx^\mu/d\tau$. If you stretch your coordinate grid (making coordinates larger), the numerical components of velocity get smaller—they transform "against" the coordinate change.

**Example:** A displacement vector $dx^\mu$ is contravariant. If you switch from meters to centimeters, the numbers get 100× larger.

## Covariant Vectors (1-Forms)

A **covariant vector** (or **1-form**) $\omega_\mu$ transforms with the inverse Jacobian:

```math
\omega'_\mu = \frac{\partial x^\nu}{\partial x'^\mu} \omega_\nu
```

**What this means:** Think of a gradient $\partial \phi / \partial x^\mu$. If you stretch coordinates, the rate of change per coordinate unit gets larger—it transforms "with" the coordinate change.

**Example:** The gradient of a scalar field $\partial_\mu \phi = \partial \phi / \partial x^\mu$ is covariant.

## The Metric Tensor

The **metric tensor** $g_{\mu\nu}$ defines distances and angles:

```math
ds^2 = g_{\mu\nu} \, dx^\mu \, dx^\nu
```

**What this means:** The metric tells you the "shape" of space(time). In flat Cartesian space, $g_{ij} = \delta_{ij}$ (identity matrix). In curved space or curvilinear coordinates, the metric encodes how distances work.

### Examples

**Minkowski spacetime** (special relativity):

```math
\eta_{\mu\nu} = \begin{pmatrix} -1 & 0 & 0 & 0 \\ 0 & 1 & 0 & 0 \\ 0 & 0 & 1 & 0 \\ 0 & 0 & 0 & 1 \end{pmatrix}
```

**Spherical coordinates** in flat 3D space:

```math
ds^2 = dr^2 + r^2 d\theta^2 + r^2 \sin^2\theta \, d\phi^2
```

```math
g_{ij} = \begin{pmatrix} 1 & 0 & 0 \\ 0 & r^2 & 0 \\ 0 & 0 & r^2 \sin^2\theta \end{pmatrix}
```

### Raising and Lowering Indices

The metric converts between contravariant and covariant:

```math
V_\mu = g_{\mu\nu} V^\nu \qquad V^\mu = g^{\mu\nu} V_\nu
```

where $g^{\mu\nu}$ is the inverse metric: $g^{\mu\alpha} g_{\alpha\nu} = \delta^\mu_\nu$.

**What this means:** The metric is like a "translator" between the two types of indices. This is crucial—it's how we compute dot products and magnitudes.

## General Tensors

A **tensor of type $(p, q)$** has $p$ contravariant and $q$ covariant indices:

```math
T^{\mu_1 \cdots \mu_p}{}_{\nu_1 \cdots \nu_q}
```

It transforms as:

```math
T'^{\mu_1 \cdots \mu_p}{}_{\nu_1 \cdots \nu_q} = \frac{\partial x'^{\mu_1}}{\partial x^{\alpha_1}} \cdots \frac{\partial x'^{\mu_p}}{\partial x^{\alpha_p}} \frac{\partial x^{\beta_1}}{\partial x'^{\nu_1}} \cdots \frac{\partial x^{\beta_q}}{\partial x'^{\nu_q}} T^{\alpha_1 \cdots \alpha_p}{}_{\beta_1 \cdots \beta_q}
```

**What this means:** Each upper index gets a Jacobian factor, each lower index gets an inverse Jacobian factor. The transformation rule is just the combination of the rules for vectors.

### Important Examples

| Tensor | Type | Description |
|--------|------|-------------|
| Scalar $\phi$ | $(0,0)$ | Invariant quantity (temperature, mass) |
| Vector $V^\mu$ | $(1,0)$ | Velocity, momentum direction |
| 1-form $\omega_\mu$ | $(0,1)$ | Gradient, wave covector |
| Metric $g_{\mu\nu}$ | $(0,2)$ | Distance/angle information |
| EM field tensor $F^{\mu\nu}$ | $(2,0)$ | Electromagnetic field |
| Riemann curvature $R^\rho{}_{\sigma\mu\nu}$ | $(1,3)$ | Spacetime curvature |

## Tensor Operations

### Contraction

Summing over a pair of indices (one up, one down) reduces the rank:

```math
T^\mu{}_\mu = T^0{}_0 + T^1{}_1 + T^2{}_2 + T^3{}_3
```

**What this means:** Contraction is the tensor generalization of the trace. It produces a quantity with two fewer indices.

**Example:** The Ricci tensor is a contraction of the Riemann tensor:

```math
R_{\mu\nu} = R^\rho{}_{\mu\rho\nu}
```

### Tensor Products

Multiplying tensors combines their indices:

```math
(A \otimes B)^{\mu\nu} = A^\mu B^\nu
```

**What this means:** You're building higher-rank tensors from lower-rank ones, like constructing a matrix from two vectors.

### Symmetry and Antisymmetry

A tensor is **symmetric** if swapping indices leaves it unchanged:

```math
T_{\mu\nu} = T_{\nu\mu}
```

A tensor is **antisymmetric** if swapping indices changes the sign:

```math
F_{\mu\nu} = -F_{\nu\mu}
```

**What this means:** Symmetric tensors (like the metric) describe "undirected" relationships. Antisymmetric tensors (like the EM field tensor) describe "oriented" relationships.

## The Covariant Derivative

Ordinary partial derivatives don't produce tensors in curved space. The **covariant derivative** $\nabla_\mu$ fixes this:

```math
\nabla_\mu V^\nu = \partial_\mu V^\nu + \Gamma^\nu_{\mu\rho} V^\rho
```

```math
\nabla_\mu \omega_\nu = \partial_\mu \omega_\nu - \Gamma^\rho_{\mu\nu} \omega_\rho
```

**What this means:** The $\Gamma$ terms (Christoffel symbols) compensate for how the coordinate basis vectors change from point to point. In flat space with Cartesian coordinates, $\Gamma = 0$ and $\nabla = \partial$.

### Christoffel Symbols

The Christoffel symbols are computed from the metric:

```math
\Gamma^\rho_{\mu\nu} = \frac{1}{2} g^{\rho\sigma} \left( \partial_\mu g_{\nu\sigma} + \partial_\nu g_{\mu\sigma} - \partial_\sigma g_{\mu\nu} \right)
```

**What this means:** The Christoffel symbols encode how much the coordinate basis "twists" as you move through space. They're not tensors themselves—they vanish in the right coordinates—but they're essential for computing covariant derivatives.

### Key Property

The covariant derivative of the metric vanishes:

```math
\nabla_\rho g_{\mu\nu} = 0
```

This is **metric compatibility**—the "length-measuring device" doesn't change under parallel transport.

## Curvature

The **Riemann curvature tensor** measures how much vectors change when parallel transported around loops:

```math
R^\rho{}_{\sigma\mu\nu} = \partial_\mu \Gamma^\rho_{\nu\sigma} - \partial_\nu \Gamma^\rho_{\mu\sigma} + \Gamma^\rho_{\mu\lambda} \Gamma^\lambda_{\nu\sigma} - \Gamma^\rho_{\nu\lambda} \Gamma^\lambda_{\mu\sigma}
```

**What this means:** If you parallel transport a vector around a small loop, it comes back rotated. The Riemann tensor quantifies this rotation—it's the intrinsic measure of curvature.

### Contractions of Riemann

**Ricci tensor** (contraction on first and third indices):

```math
R_{\mu\nu} = R^\rho{}_{\mu\rho\nu}
```

**Ricci scalar** (trace of Ricci tensor):

```math
R = g^{\mu\nu} R_{\mu\nu}
```

These appear in the Einstein field equations:

```math
R_{\mu\nu} - \frac{1}{2} R g_{\mu\nu} = 8\pi T_{\mu\nu}
```

(in [natural units](natural-units.md) with $G = c = 1$).

## Summary

| Concept | Symbol | Key Idea |
|---------|--------|----------|
| Contravariant vector | $V^\mu$ | Transforms like $dx^\mu$ |
| Covariant vector | $\omega_\mu$ | Transforms like $\partial/\partial x^\mu$ |
| Metric | $g_{\mu\nu}$ | Defines distances, raises/lowers indices |
| Covariant derivative | $\nabla_\mu$ | Derivative that produces tensors |
| Christoffel symbols | $\Gamma^\rho_{\mu\nu}$ | Connection coefficients (not a tensor) |
| Riemann tensor | $R^\rho{}_{\sigma\mu\nu}$ | Measures curvature |

**The essential insight:** Tensors transform in a well-defined way under coordinate changes, ensuring that physical equations written in tensor form are automatically valid in all coordinate systems. This is the mathematical foundation for relativity and modern physics.
