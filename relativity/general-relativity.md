# General Relativity

General relativity is Einstein's geometric theory of gravity, replacing Newton's action-at-a-distance with the curvature of spacetime. Mass and energy tell spacetime how to curve; curved spacetime tells matter how to move. This document covers the conceptual foundations and key equations. We use [natural units](../math-foundations/natural-units.md) where $G = c = 1$. Prerequisites: [special relativity](special-relativity.md), [tensor calculus](../math-foundations/tensor-calculus.md). For the full mathematical derivation, see [Einstein field equations](einstein-field-equations.md).

## The Equivalence Principle

### The Insight

Einstein's key insight: **gravity and acceleration are locally indistinguishable**.

An observer in a closed box cannot tell whether:
- The box is at rest on Earth's surface (gravity pulling down)
- The box is accelerating upward at $g$ in deep space (inertia pushing down)

This is the **equivalence principle**—the foundation of general relativity.

### Versions

| Version | Statement |
|---------|-----------|
| Weak | All objects fall with the same acceleration (Galileo) |
| Einstein | Local physics in a freely falling frame is special-relativistic |
| Strong | All laws of physics are the same in all local inertial frames |

**What this means:** If gravity and acceleration are equivalent, then gravity cannot be a force in the usual sense. Instead, freely falling objects follow the natural paths through spacetime—they're not being pushed or pulled. What we call "gravity" is the curvature of spacetime itself.

### Consequences

The equivalence principle immediately implies:

1. **Light bends in gravitational fields** — If light goes straight in an accelerating elevator (as seen from outside), it must curve downward inside. So light curves in gravity.

2. **Time dilates in gravitational fields** — Clocks at different heights in an accelerating rocket tick at different rates. So clocks run slower deeper in a gravitational field.

3. **Gravity affects all forms of energy** — Since $E = mc^2$, energy has inertia, so gravity must affect light, heat, and all energy.

## Curved Spacetime

### From Flat to Curved

In special relativity, spacetime is flat. The interval between events is:

```math
ds^2 = -dt^2 + dx^2 + dy^2 + dz^2 = \eta_{\mu\nu} dx^\mu dx^\nu
```

where $\eta_{\mu\nu} = \text{diag}(-1, 1, 1, 1)$ is the Minkowski metric.

In general relativity, spacetime can curve. The interval becomes:

```math
\boxed{ds^2 = g_{\mu\nu}(x) \, dx^\mu dx^\nu}
```

where $g_{\mu\nu}(x)$ is the **metric tensor**—a field that varies from point to point.

**What this means:** The metric tells you how to measure distances and times at each point in spacetime. Curvature means these measurements vary with position, encoding the effects of gravity.

### The Metric Tensor

The metric $g_{\mu\nu}$ is a symmetric $4 \times 4$ matrix (10 independent components) that:

- Defines distances: $ds^2 = g_{\mu\nu} dx^\mu dx^\nu$
- Defines angles: $\cos\theta = \frac{g_{\mu\nu} A^\mu B^\nu}{|A||B|}$
- Raises/lowers indices: $V_\mu = g_{\mu\nu} V^\nu$
- Determines causal structure: $ds^2 < 0$ (timelike), $ds^2 = 0$ (null), $ds^2 > 0$ (spacelike)

### Examples of Metrics

| Spacetime | Metric | Description |
|-----------|--------|-------------|
| Minkowski | $ds^2 = -dt^2 + dx^2 + dy^2 + dz^2$ | Flat spacetime |
| [Schwarzschild](schwarzschild-solution.md) | $ds^2 = -(1-\frac{2M}{r})dt^2 + (1-\frac{2M}{r})^{-1}dr^2 + r^2 d\Omega^2$ | Non-rotating black hole |
| [Kerr](kerr-metric.md) | See Kerr document | Rotating black hole |
| [FLRW](friedmann-equations.md) | $ds^2 = -dt^2 + a(t)^2 [dr^2/(1-kr^2) + r^2 d\Omega^2]$ | Expanding universe |

## Curvature

### The Riemann Tensor

Curvature is measured by the **Riemann curvature tensor** $R^\rho{}_{\sigma\mu\nu}$, which tells you how vectors change when parallel-transported around closed loops.

For a metric $g_{\mu\nu}$, first compute the Christoffel symbols:

```math
\Gamma^\rho_{\mu\nu} = \frac{1}{2} g^{\rho\sigma} \left( \partial_\mu g_{\nu\sigma} + \partial_\nu g_{\mu\sigma} - \partial_\sigma g_{\mu\nu} \right)
```

Then the Riemann tensor is:

```math
R^\rho{}_{\sigma\mu\nu} = \partial_\mu \Gamma^\rho_{\nu\sigma} - \partial_\nu \Gamma^\rho_{\mu\sigma} + \Gamma^\rho_{\mu\lambda} \Gamma^\lambda_{\nu\sigma} - \Gamma^\rho_{\nu\lambda} \Gamma^\lambda_{\mu\sigma}
```

**What this means:** If $R^\rho{}_{\sigma\mu\nu} = 0$ everywhere, spacetime is flat (just Minkowski in disguise). Nonzero Riemann means genuine curvature—tidal forces, gravitational effects.

### Contractions

| Tensor | Definition | Components |
|--------|------------|------------|
| Riemann | $R^\rho{}_{\sigma\mu\nu}$ | 20 independent |
| Ricci tensor | $R_{\mu\nu} = R^\rho{}_{\mu\rho\nu}$ | 10 independent |
| Ricci scalar | $R = g^{\mu\nu} R_{\mu\nu}$ | 1 component |
| Einstein tensor | $G_{\mu\nu} = R_{\mu\nu} - \frac{1}{2} g_{\mu\nu} R$ | 10 independent |

The **Einstein tensor** $G_{\mu\nu}$ is special: it satisfies $\nabla_\mu G^{\mu\nu} = 0$ automatically (the Bianchi identity). This is crucial for consistency with energy conservation.

## The Einstein Field Equations

### The Equations

Einstein's field equations relate spacetime curvature to matter and energy:

```math
\boxed{G_{\mu\nu} = 8\pi T_{\mu\nu}}
```

or equivalently:

```math
R_{\mu\nu} - \frac{1}{2} g_{\mu\nu} R = 8\pi T_{\mu\nu}
```

**What this means:** The left side is pure geometry (curvature). The right side is matter and energy. Mass-energy curves spacetime; the curvature is proportional to the energy density.

### With Cosmological Constant

Including the cosmological constant $\Lambda$:

```math
\boxed{G_{\mu\nu} + \Lambda g_{\mu\nu} = 8\pi T_{\mu\nu}}
```

The $\Lambda$ term acts like a constant energy density of empty space—dark energy.

### Properties

| Property | Explanation |
|----------|-------------|
| 10 equations | Symmetric tensors have 10 components |
| 4 constraints | Bianchi identity $\nabla_\mu G^{\mu\nu} = 0$ gives 4 constraints |
| 6 physical DOF | 10 - 4 = 6 degrees of freedom (but 4 are gauge) |
| 2 true DOF | 2 physical gravitational degrees of freedom (gravitational waves have 2 polarizations) |

## The Stress-Energy Tensor

### Definition

The **stress-energy tensor** $T_{\mu\nu}$ describes the density and flux of energy and momentum:

```math
T_{\mu\nu} = \begin{pmatrix}
\text{energy density} & \text{energy flux} \\
\text{momentum density} & \text{stress (pressure, shear)}
\end{pmatrix}
```

### Components

| Component | Physical Meaning |
|-----------|------------------|
| $T_{00}$ | Energy density $\rho$ |
| $T_{0i}$ | Momentum density (energy flux) |
| $T_{i0}$ | Energy flux (= momentum density) |
| $T_{ij}$ | Stress tensor (pressure, shear) |

### Common Sources

**Perfect fluid:**
```math
T_{\mu\nu} = (\rho + p) u_\mu u_\nu + p \, g_{\mu\nu}
```

where $\rho$ is energy density, $p$ is pressure, and $u^\mu$ is 4-velocity.

| Matter Type | $\rho$ | $p$ | Equation of State |
|-------------|--------|-----|-------------------|
| Dust (matter) | $\rho$ | $0$ | $p = 0$ |
| Radiation | $\rho$ | $\rho/3$ | $p = \rho/3$ |
| Cosmological constant | $\rho_\Lambda$ | $-\rho_\Lambda$ | $p = -\rho$ |

**What this means:** Different types of matter curve spacetime differently. Pressure gravitates too—not just mass. Negative pressure (dark energy) causes accelerating expansion.

### Conservation

Energy-momentum is conserved:
```math
\nabla_\mu T^{\mu\nu} = 0
```

This follows automatically from $\nabla_\mu G^{\mu\nu} = 0$ and the field equations.

## Geodesics

### The Geodesic Equation

Free particles follow **geodesics**—the straightest possible paths in curved spacetime:

```math
\boxed{\frac{d^2 x^\mu}{d\tau^2} + \Gamma^\mu_{\rho\sigma} \frac{dx^\rho}{d\tau} \frac{dx^\sigma}{d\tau} = 0}
```

**What this means:** In flat spacetime, geodesics are straight lines. In curved spacetime, they curve—but they're still the "straightest" paths. What we perceive as gravitational attraction is just geodesic motion through curved spacetime.

### Types of Geodesics

| Type | Condition | Example |
|------|-----------|---------|
| Timelike | $ds^2 < 0$ | Massive particles |
| Null | $ds^2 = 0$ | Light rays |
| Spacelike | $ds^2 > 0$ | Tachyons (hypothetical) |

See [geodesics](geodesics.md) for orbital motion, light bending, and the ISCO.

## Newtonian Limit

### Recovering Newton

For weak fields and slow motion, GR reduces to Newtonian gravity.

In the weak-field limit:
```math
g_{00} \approx -(1 + 2\Phi)
```

where $\Phi$ is the Newtonian gravitational potential. The geodesic equation becomes:

```math
\frac{d^2 \vec{x}}{dt^2} = -\nabla \Phi
```

And the field equation becomes Poisson's equation:
```math
\nabla^2 \Phi = 4\pi \rho
```

**What this means:** Newton's theory isn't wrong—it's the weak-field, slow-motion limit of GR. Einstein's theory extends it to strong fields and relativistic speeds.

## Key Predictions

### Confirmed Predictions

| Prediction | Test | Precision |
|------------|------|-----------|
| Light bending | Solar eclipses, radio sources | ~0.01% |
| Gravitational redshift | Pound-Rebka, GPS satellites | ~0.01% |
| Perihelion precession | Mercury's orbit | ~0.1% |
| Gravitational time dilation | Atomic clocks at altitude | ~10⁻¹⁵ |
| Gravitational waves | LIGO/Virgo detections | Direct observation |
| Black holes | Event Horizon Telescope | Direct imaging |
| Frame dragging | Gravity Probe B | ~19% |

### The Role of Each Prediction

- **Perihelion precession** tests strong-field static geometry
- **Light bending** tests null geodesics in curved spacetime
- **Gravitational waves** test dynamical spacetime (see [gravitational waves](gravitational-waves.md))
- **Black holes** test extreme curvature (see [Schwarzschild](schwarzschild-solution.md), [Kerr](kerr-metric.md))

## Solutions of the Field Equations

### Exact Solutions

Finding metrics that satisfy $G_{\mu\nu} = 8\pi T_{\mu\nu}$ is difficult. Key exact solutions:

| Solution | Source | Features |
|----------|--------|----------|
| [Schwarzschild](schwarzschild-solution.md) | Point mass | Non-rotating black hole |
| [Kerr](kerr-metric.md) | Rotating mass | Rotating black hole, ergosphere |
| [Reissner-Nordström](schwarzschild-solution.md) | Charged mass | Charged black hole |
| Kerr-Newman | Rotating charged mass | Most general black hole |
| [FLRW](friedmann-equations.md) | Homogeneous matter | Cosmology |
| de Sitter | $\Lambda > 0$ only | Accelerating expansion |

### The Uniqueness Theorems

Remarkably, black holes in GR are simple:

**No-hair theorem:** A stationary black hole is completely characterized by just three parameters: mass $M$, angular momentum $J$, and charge $Q$.

All other information about what formed the black hole is lost—black holes have "no hair."

## Summary

| Concept | Key Equation | Meaning |
|---------|--------------|---------|
| Equivalence principle | — | Gravity = acceleration locally |
| Metric | $ds^2 = g_{\mu\nu} dx^\mu dx^\nu$ | Geometry of spacetime |
| Curvature | $R^\rho{}_{\sigma\mu\nu}$ | Tidal forces, geometry |
| Einstein equations | $G_{\mu\nu} = 8\pi T_{\mu\nu}$ | Matter curves spacetime |
| Geodesics | $\ddot{x}^\mu + \Gamma^\mu_{\rho\sigma} \dot{x}^\rho \dot{x}^\sigma = 0$ | Free fall is geodesic motion |
| Newtonian limit | $g_{00} \approx -(1 + 2\Phi)$ | GR contains Newton |

| From SR to GR | Change |
|---------------|--------|
| Flat spacetime | → Curved spacetime |
| $\eta_{\mu\nu}$ (constant) | → $g_{\mu\nu}(x)$ (field) |
| Inertial frames (global) | → Local inertial frames only |
| No gravity | → Gravity = curvature |

**The essential insight:** General relativity geometrizes gravity. The equivalence principle tells us that gravity and acceleration are the same thing locally. This means gravity cannot be a force—it must be a property of spacetime itself. The metric tensor $g_{\mu\nu}$ encodes this geometry, and Einstein's field equations tell us how matter and energy determine that geometry. Objects in free fall aren't being pushed or pulled; they're following the straightest possible paths through a curved spacetime. This simple, beautiful idea explains everything from Mercury's orbit to gravitational waves to the expansion of the universe.
