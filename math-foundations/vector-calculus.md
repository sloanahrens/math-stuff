# Vector Calculus

Vector calculus extends [calculus](calculus-primer.md) to vector fields in 2D and 3D. It provides the language for electromagnetism, fluid dynamics, and classical mechanics. The operations here—gradient, divergence, and curl—are unified by [differential forms](../math-foundations/differential-forms.md), but this document presents the traditional 3D vector approach first.

## Vectors

### Basic Operations

A vector $\mathbf{v} = (v_x, v_y, v_z)$ has magnitude and direction:

```math
|\mathbf{v}| = \sqrt{v_x^2 + v_y^2 + v_z^2}
```

**Scalar multiplication:** $c\mathbf{v} = (cv_x, cv_y, cv_z)$

**Vector addition:** $\mathbf{u} + \mathbf{v} = (u_x + v_x, u_y + v_y, u_z + v_z)$

### Dot Product

```math
\mathbf{u} \cdot \mathbf{v} = u_x v_x + u_y v_y + u_z v_z = |\mathbf{u}||\mathbf{v}|\cos\theta
```

**What this means:** The dot product measures how much two vectors point in the same direction. It's zero for perpendicular vectors, positive for similar directions, negative for opposite.

### Cross Product

```math
\mathbf{u} \times \mathbf{v} = \begin{vmatrix} \mathbf{i} & \mathbf{j} & \mathbf{k} \\ u_x & u_y & u_z \\ v_x & v_y & v_z \end{vmatrix} = (u_y v_z - u_z v_y, u_z v_x - u_x v_z, u_x v_y - u_y v_x)
```

**Properties:**
- $|\mathbf{u} \times \mathbf{v}| = |\mathbf{u}||\mathbf{v}|\sin\theta$
- Result is perpendicular to both $\mathbf{u}$ and $\mathbf{v}$
- Antisymmetric: $\mathbf{u} \times \mathbf{v} = -\mathbf{v} \times \mathbf{u}$

**What this means:** The cross product gives a vector perpendicular to the plane of $\mathbf{u}$ and $\mathbf{v}$, with magnitude equal to the area of the parallelogram they span. It appears in angular momentum $\mathbf{L} = \mathbf{r} \times \mathbf{p}$ and the magnetic force $\mathbf{F} = q\mathbf{v} \times \mathbf{B}$.

## Scalar and Vector Fields

### Definitions

**Scalar field:** A function that assigns a number to each point in space.
- Examples: Temperature $T(x, y, z)$, electric potential $\phi(x, y, z)$, pressure $P(x, y, z)$

**Vector field:** A function that assigns a vector to each point in space.
- Examples: Velocity $\mathbf{v}(x, y, z)$, electric field $\mathbf{E}(x, y, z)$, gravitational field $\mathbf{g}(x, y, z)$

## The Del Operator

The **nabla** or **del** operator combines partial derivatives into a vector:

```math
\nabla = \left(\frac{\partial}{\partial x}, \frac{\partial}{\partial y}, \frac{\partial}{\partial z}\right)
```

This operator acts on fields to produce the three fundamental operations of vector calculus.

## Gradient

### Definition

The **gradient** of a scalar field $f$ is:

```math
\boxed{\nabla f = \left(\frac{\partial f}{\partial x}, \frac{\partial f}{\partial y}, \frac{\partial f}{\partial z}\right)}
```

**What this means:** The gradient points in the direction of steepest increase of $f$, with magnitude equal to that rate of increase. It's perpendicular to level surfaces of $f$.

### Properties

- $\nabla f$ points "uphill" in $f$
- $|\nabla f|$ is the rate of change in that direction
- $\nabla f = 0$ at maxima, minima, and saddle points
- $\nabla f \cdot d\mathbf{r} = df$ (change in $f$ along $d\mathbf{r}$)

### Physics Application

Force from potential energy:

```math
\mathbf{F} = -\nabla V
```

The force points downhill in potential energy. For gravity near Earth: $V = mgh$, so $\mathbf{F} = -mg\hat{z}$.

### Directional Derivative

The rate of change of $f$ in direction $\hat{n}$:

```math
\frac{\partial f}{\partial n} = \nabla f \cdot \hat{n}
```

## Divergence

### Definition

The **divergence** of a vector field $\mathbf{F} = (F_x, F_y, F_z)$ is:

```math
\boxed{\nabla \cdot \mathbf{F} = \frac{\partial F_x}{\partial x} + \frac{\partial F_y}{\partial y} + \frac{\partial F_z}{\partial z}}
```

**What this means:** Divergence measures how much a vector field "spreads out" from a point. Positive divergence means the field is a source (flowing outward); negative means it's a sink (flowing inward).

### Physical Interpretation

Imagine $\mathbf{F}$ is fluid velocity:
- $\nabla \cdot \mathbf{F} > 0$: fluid is being created (source)
- $\nabla \cdot \mathbf{F} < 0$: fluid is being destroyed (sink)
- $\nabla \cdot \mathbf{F} = 0$: incompressible flow

### Physics Applications

**Gauss's law (electrostatics):**
```math
\nabla \cdot \mathbf{E} = \frac{\rho}{\epsilon_0}
```

Charges are sources of electric field lines—see [Maxwell covariant](../electromagnetism/maxwell-covariant.md).

**Continuity equation:**
```math
\frac{\partial \rho}{\partial t} + \nabla \cdot \mathbf{J} = 0
```

Mass/charge is conserved: what flows out equals what's lost inside.

## Curl

### Definition

The **curl** of a vector field $\mathbf{F}$ is:

```math
\boxed{\nabla \times \mathbf{F} = \begin{vmatrix} \mathbf{i} & \mathbf{j} & \mathbf{k} \\ \frac{\partial}{\partial x} & \frac{\partial}{\partial y} & \frac{\partial}{\partial z} \\ F_x & F_y & F_z \end{vmatrix}}
```

Expanded:

```math
\nabla \times \mathbf{F} = \left(\frac{\partial F_z}{\partial y} - \frac{\partial F_y}{\partial z}, \frac{\partial F_x}{\partial z} - \frac{\partial F_z}{\partial x}, \frac{\partial F_y}{\partial x} - \frac{\partial F_x}{\partial y}\right)
```

**What this means:** Curl measures the rotation or "swirl" of a vector field around a point. If you placed a tiny paddle wheel in the flow, curl tells you how fast and in what direction it would spin.

### Physical Interpretation

- $\nabla \times \mathbf{F} = 0$: the field is irrotational (no swirl)
- $|\nabla \times \mathbf{F}|$ large: strong local rotation

### Physics Applications

**Faraday's law:**
```math
\nabla \times \mathbf{E} = -\frac{\partial \mathbf{B}}{\partial t}
```

Changing magnetic fields create circulating electric fields.

**Ampère's law:**
```math
\nabla \times \mathbf{B} = \mu_0\mathbf{J} + \mu_0\epsilon_0\frac{\partial \mathbf{E}}{\partial t}
```

Currents and changing electric fields create circulating magnetic fields.

## The Laplacian

### Definition

The **Laplacian** is divergence of gradient:

```math
\boxed{\nabla^2 f = \nabla \cdot (\nabla f) = \frac{\partial^2 f}{\partial x^2} + \frac{\partial^2 f}{\partial y^2} + \frac{\partial^2 f}{\partial z^2}}
```

**What this means:** The Laplacian measures how much $f$ at a point differs from its average in nearby regions. If $\nabla^2 f > 0$, the point is a local minimum compared to neighbors; if $\nabla^2 f < 0$, it's a local maximum.

### Physics Applications

**Laplace's equation** (no sources):
```math
\nabla^2 \phi = 0
```

**Poisson's equation** (with sources):
```math
\nabla^2 \phi = -\frac{\rho}{\epsilon_0}
```

**Schrödinger equation** contains $\nabla^2$:
```math
-\frac{\hbar^2}{2m}\nabla^2\psi + V\psi = E\psi
```

See [quantum mechanics](../quantum-mechanics/quantum-mechanics.md).

## Fundamental Identities

### Vector Identities

```math
\nabla \times (\nabla f) = 0 \quad \text{(curl of gradient is zero)}
```

```math
\nabla \cdot (\nabla \times \mathbf{F}) = 0 \quad \text{(divergence of curl is zero)}
```

**What this means:** These identities are why:
- Electrostatic fields ($\mathbf{E} = -\nabla\phi$) have no curl
- Magnetic fields ($\nabla \cdot \mathbf{B} = 0$) can be written as $\mathbf{B} = \nabla \times \mathbf{A}$

See [differential forms](../math-foundations/differential-forms.md) where both become $d^2 = 0$.

### Other Useful Identities

```math
\nabla(fg) = f\nabla g + g\nabla f
```

```math
\nabla \cdot (f\mathbf{F}) = f(\nabla \cdot \mathbf{F}) + \mathbf{F} \cdot \nabla f
```

```math
\nabla \times (f\mathbf{F}) = f(\nabla \times \mathbf{F}) + (\nabla f) \times \mathbf{F}
```

```math
\nabla \times (\nabla \times \mathbf{F}) = \nabla(\nabla \cdot \mathbf{F}) - \nabla^2\mathbf{F}
```

## Integral Theorems

### Line Integrals

The line integral of a vector field along a curve $C$:

```math
\int_C \mathbf{F} \cdot d\mathbf{r} = \int_C (F_x dx + F_y dy + F_z dz)
```

**What this means:** This computes work done by force $\mathbf{F}$ along path $C$, or circulation of a flow.

### Gradient Theorem (Fundamental Theorem for Line Integrals)

```math
\int_a^b \nabla f \cdot d\mathbf{r} = f(b) - f(a)
```

**What this means:** For conservative fields ($\mathbf{F} = \nabla f$), the line integral depends only on endpoints, not path. This is why potential energy is well-defined.

### Divergence Theorem (Gauss's Theorem)

```math
\boxed{\iiint_V (\nabla \cdot \mathbf{F}) \, dV = \oiint_S \mathbf{F} \cdot d\mathbf{A}}
```

**What this means:** The total "outflow" from a volume equals the flux through its boundary. This converts [Maxwell's equations](../electromagnetism/maxwell-covariant.md) between differential and integral forms.

### Stokes' Theorem

```math
\boxed{\iint_S (\nabla \times \mathbf{F}) \cdot d\mathbf{A} = \oint_C \mathbf{F} \cdot d\mathbf{r}}
```

**What this means:** The total curl through a surface equals the circulation around its boundary. This relates Faraday's law in differential and integral forms.

### Connection to Differential Forms

All three theorems are special cases of the generalized Stokes' theorem:

```math
\int_M d\omega = \int_{\partial M} \omega
```

See [differential forms](../math-foundations/differential-forms.md) for the unified treatment.

## Curvilinear Coordinates

### Why Different Coordinates?

Cartesian coordinates $(x, y, z)$ are natural for boxes, but many physical systems have other symmetries:
- Cylinders, wires: cylindrical coordinates
- Spheres, atoms: spherical coordinates

### Cylindrical Coordinates $(r, \phi, z)$

```math
x = r\cos\phi, \quad y = r\sin\phi, \quad z = z
```

**Gradient:**
```math
\nabla f = \frac{\partial f}{\partial r}\hat{r} + \frac{1}{r}\frac{\partial f}{\partial \phi}\hat{\phi} + \frac{\partial f}{\partial z}\hat{z}
```

**Divergence:**
```math
\nabla \cdot \mathbf{F} = \frac{1}{r}\frac{\partial(rF_r)}{\partial r} + \frac{1}{r}\frac{\partial F_\phi}{\partial \phi} + \frac{\partial F_z}{\partial z}
```

**Laplacian:**
```math
\nabla^2 f = \frac{1}{r}\frac{\partial}{\partial r}\left(r\frac{\partial f}{\partial r}\right) + \frac{1}{r^2}\frac{\partial^2 f}{\partial \phi^2} + \frac{\partial^2 f}{\partial z^2}
```

### Spherical Coordinates $(r, \theta, \phi)$

```math
x = r\sin\theta\cos\phi, \quad y = r\sin\theta\sin\phi, \quad z = r\cos\theta
```

**Gradient:**
```math
\nabla f = \frac{\partial f}{\partial r}\hat{r} + \frac{1}{r}\frac{\partial f}{\partial \theta}\hat{\theta} + \frac{1}{r\sin\theta}\frac{\partial f}{\partial \phi}\hat{\phi}
```

**Divergence:**
```math
\nabla \cdot \mathbf{F} = \frac{1}{r^2}\frac{\partial(r^2 F_r)}{\partial r} + \frac{1}{r\sin\theta}\frac{\partial(\sin\theta F_\theta)}{\partial \theta} + \frac{1}{r\sin\theta}\frac{\partial F_\phi}{\partial \phi}
```

**Laplacian:**
```math
\nabla^2 f = \frac{1}{r^2}\frac{\partial}{\partial r}\left(r^2\frac{\partial f}{\partial r}\right) + \frac{1}{r^2\sin\theta}\frac{\partial}{\partial \theta}\left(\sin\theta\frac{\partial f}{\partial \theta}\right) + \frac{1}{r^2\sin^2\theta}\frac{\partial^2 f}{\partial \phi^2}
```

**What this means:** The [hydrogen atom](../quantum-mechanics/hydrogen-atom.md) is solved in spherical coordinates because the Coulomb potential $V = -1/r$ has spherical symmetry.

## Summary

| Operation | Symbol | Type → Type | Physical Meaning |
|-----------|--------|-------------|------------------|
| Gradient | $\nabla f$ | Scalar → Vector | Direction of steepest increase |
| Divergence | $\nabla \cdot \mathbf{F}$ | Vector → Scalar | Source strength |
| Curl | $\nabla \times \mathbf{F}$ | Vector → Vector | Rotation/circulation |
| Laplacian | $\nabla^2 f$ | Scalar → Scalar | Deviation from average |

| Theorem | Statement | Meaning |
|---------|-----------|---------|
| Gradient | $\int_a^b \nabla f \cdot d\mathbf{r} = f(b) - f(a)$ | Path independence |
| Divergence | $\iiint (\nabla \cdot \mathbf{F}) dV = \oiint \mathbf{F} \cdot d\mathbf{A}$ | Outflow = boundary flux |
| Stokes | $\iint (\nabla \times \mathbf{F}) \cdot d\mathbf{A} = \oint \mathbf{F} \cdot d\mathbf{r}$ | Curl flux = circulation |

**The essential insight:** Vector calculus describes how fields vary in space. Gradient, divergence, and curl measure different aspects of this variation. The integral theorems connect local (differential) properties to global (integral) behavior, which is why Maxwell's equations can be written in both forms.
