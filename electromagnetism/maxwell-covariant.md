# Maxwell's Equations in Covariant Form

This document shows how the four Maxwell equations in three-dimensional space can be elegantly unified into a single tensor equation using the formalism of [special relativity](../relativity/special-relativity.md). We use [natural units](../math-foundations/natural-units.md) where $c = 1$ and the metric signature $(-,+,+,+)$. This requires familiarity with [vector calculus](../math-foundations/vector-calculus.md) (div, curl, gradient) and builds on [tensor calculus](../math-foundations/tensor-calculus.md). It connects to [differential forms](../math-foundations/differential-forms.md) for the most elegant formulation.

## Maxwell's Equations in 3-Space

The classical Maxwell equations in vacuum with sources are:

**Gauss's Law (electric):**
```math
\nabla \cdot \mathbf{E} = \rho
```

**Gauss's Law (magnetic):**
```math
\nabla \cdot \mathbf{B} = 0
```

**Faraday's Law:**
```math
\nabla \times \mathbf{E} = -\frac{\partial \mathbf{B}}{\partial t}
```

**Ampère-Maxwell Law:**
```math
\nabla \times \mathbf{B} = \mathbf{J} + \frac{\partial \mathbf{E}}{\partial t}
```

where $\mathbf{E}$ is the electric field, $\mathbf{B}$ is the magnetic field, $\rho$ is charge density, and $\mathbf{J}$ is current density.

## Building the 4-Vector Formalism

### Spacetime Coordinates

In special relativity, we combine space and time into a 4-vector:

```math
x^\mu = (t, x, y, z) = (x^0, x^1, x^2, x^3)
```

The Minkowski metric is:

```math
\eta_{\mu\nu} = \begin{pmatrix}
-1 & 0 & 0 & 0 \\
0 & 1 & 0 & 0 \\
0 & 0 & 1 & 0 \\
0 & 0 & 0 & 1
\end{pmatrix}
```

### The 4-Gradient

The partial derivative becomes a 4-vector operator:

```math
\partial_\mu = \frac{\partial}{\partial x^\mu} = \left(\frac{\partial}{\partial t}, \nabla\right) = \left(\frac{\partial}{\partial t}, \frac{\partial}{\partial x}, \frac{\partial}{\partial y}, \frac{\partial}{\partial z}\right)
```

With raised index:

```math
\partial^\mu = \eta^{\mu\nu} \partial_\nu = \left(-\frac{\partial}{\partial t}, \nabla\right)
```

### The 4-Current

Charge density $\rho$ and current density $\mathbf{J}$ combine into the **4-current**:

```math
J^\mu = (\rho, \mathbf{J}) = (\rho, J^x, J^y, J^z)
```

The continuity equation $\frac{\partial \rho}{\partial t} + \nabla \cdot \mathbf{J} = 0$ becomes:

```math
\partial_\mu J^\mu = 0
```

### The 4-Potential

The scalar potential $\phi$ and vector potential $\mathbf{A}$ combine into the **4-potential**:

```math
A^\mu = (\phi, \mathbf{A})
```

The fields are related to potentials by:

```math
\mathbf{E} = -\nabla\phi - \frac{\partial \mathbf{A}}{\partial t}, \quad \mathbf{B} = \nabla \times \mathbf{A}
```

## The Electromagnetic Field Tensor

### Definition

The **electromagnetic field tensor** (or Faraday tensor) is the antisymmetric rank-2 tensor:

```math
F_{\mu\nu} = \partial_\mu A_\nu - \partial_\nu A_\mu
```

### Components

Writing out the components explicitly in terms of $\mathbf{E}$ and $\mathbf{B}$:

```math
F_{\mu\nu} = \begin{pmatrix}
0 & E_x & E_y & E_z \\
-E_x & 0 & B_z & -B_y \\
-E_y & -B_z & 0 & B_x \\
-E_z & B_y & -B_x & 0
\end{pmatrix}
```

With raised indices:

```math
F^{\mu\nu} = \eta^{\mu\alpha} \eta^{\nu\beta} F_{\alpha\beta} = \begin{pmatrix}
0 & -E_x & -E_y & -E_z \\
E_x & 0 & B_z & -B_y \\
E_y & -B_z & 0 & B_x \\
E_z & B_y & -B_x & 0
\end{pmatrix}
```

### The Dual Tensor

The **Hodge dual** of $F^{\mu\nu}$ is defined using the Levi-Civita symbol:

```math
\tilde{F}^{\mu\nu} = \frac{1}{2} \epsilon^{\mu\nu\rho\sigma} F_{\rho\sigma}
```

where $\epsilon^{0123} = +1$. The dual tensor swaps the roles of $\mathbf{E}$ and $\mathbf{B}$:

```math
\tilde{F}^{\mu\nu} = \begin{pmatrix}
0 & -B_x & -B_y & -B_z \\
B_x & 0 & -E_z & E_y \\
B_y & E_z & 0 & -E_x \\
B_z & -E_y & E_x & 0
\end{pmatrix}
```

## Maxwell's Equations in Tensor Form

### The Inhomogeneous Equations

Gauss's law and the Ampère-Maxwell law combine into:

```math
\boxed{\partial_\mu F^{\mu\nu} = J^\nu}
```

**Verification:**

For $\nu = 0$:
```math
\partial_\mu F^{\mu 0} = \partial_i F^{i0} = \partial_i E^i = \nabla \cdot \mathbf{E} = \rho = J^0 \quad \checkmark
```

For $\nu = j$ (spatial):
```math
\partial_\mu F^{\mu j} = \partial_0 F^{0j} + \partial_i F^{ij} = -\frac{\partial E^j}{\partial t} + (\nabla \times \mathbf{B})^j = J^j \quad \checkmark
```

### The Homogeneous Equations

Gauss's law for magnetism and Faraday's law combine into:

```math
\boxed{\partial_\mu \tilde{F}^{\mu\nu} = 0}
```

Or equivalently, using the **Bianchi identity**:

```math
\boxed{\partial_\mu F_{\nu\rho} + \partial_\nu F_{\rho\mu} + \partial_\rho F_{\mu\nu} = 0}
```

This can be written more compactly as:

```math
\partial_{[\mu} F_{\nu\rho]} = 0
```

**Verification:**

For $\nu = 0$:
```math
\partial_\mu \tilde{F}^{\mu 0} = \partial_i B^i = \nabla \cdot \mathbf{B} = 0 \quad \checkmark
```

For $\nu = j$ (spatial):
```math
\partial_\mu \tilde{F}^{\mu j} = \frac{\partial B^j}{\partial t} + (\nabla \times \mathbf{E})^j = 0 \quad \checkmark
```

## Summary: From Four Equations to Two

| 3D Maxwell Equations | Description | Covariant Form |
|---------------------|-------------|----------------|
| $\nabla \cdot \mathbf{E} = \rho$ | Electric charges produce electric field lines | $\partial_\mu F^{\mu\nu} = J^\nu$ |
| $\nabla \times \mathbf{B} = \mathbf{J} + \frac{\partial \mathbf{E}}{\partial t}$ | Currents and changing electric fields produce magnetic fields | (inhomogeneous) |
| $\nabla \cdot \mathbf{B} = 0$ | No magnetic monopoles exist; magnetic field lines always close | $\partial_\mu \tilde{F}^{\mu\nu} = 0$ |
| $\nabla \times \mathbf{E} = -\frac{\partial \mathbf{B}}{\partial t}$ | Changing magnetic fields induce electric fields | (homogeneous) |

## The Single Equation Form

Using differential forms, both equations can be written as a **single equation**. Define the 2-form:

```math
F = \frac{1}{2} F_{\mu\nu} \, dx^\mu \wedge dx^\nu
```

and the 1-form current:

```math
J = J_\mu \, dx^\mu
```

Then Maxwell's equations become:

```math
\boxed{dF = 0, \quad d{\star}F = {\star}J}
```

where $d$ is the exterior derivative and $\star$ is the Hodge star operator.

In even more compact notation using the codifferential $\delta = \star d \star$:

```math
\boxed{dF = 0, \quad \delta F = J}
```

Or, if we introduce the 4-potential 1-form $A = A_\mu dx^\mu$ with $F = dA$, the homogeneous equation is automatic ($d^2 = 0$), and we have:

```math
\boxed{\delta \, dA = J}
```

This is the **single equation** that encapsulates all of Maxwell's electromagnetism.

## Lorentz Covariance

The beauty of this formulation is manifest **Lorentz covariance**. Under a Lorentz transformation $\Lambda^\mu{}_\nu$:

```math
F'^{\mu\nu} = \Lambda^\mu{}_\alpha \Lambda^\nu{}_\beta F^{\alpha\beta}
```

The equations $\partial_\mu F^{\mu\nu} = J^\nu$ and $\partial_\mu \tilde{F}^{\mu\nu} = 0$ transform covariantly, automatically guaranteeing that Maxwell's equations have the same form in all inertial frames.

This was one of the key insights that led Einstein to special relativity: Maxwell's equations were already relativistically correct, while Newtonian mechanics needed modification.
