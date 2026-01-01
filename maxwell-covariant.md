# Maxwell's Equations in Covariant Form

This document shows how the four Maxwell equations in three-dimensional space can be elegantly unified into a single tensor equation using the formalism of special relativity. We use natural units where $c = 1$ and the metric signature $(-,+,+,+)$.

## Maxwell's Equations in 3-Space

The classical Maxwell equations in vacuum with sources are:

**Gauss's Law (electric):**
$$
\nabla \cdot \mathbf{E} = \rho
$$

**Gauss's Law (magnetic):**
$$
\nabla \cdot \mathbf{B} = 0
$$

**Faraday's Law:**
$$
\nabla \times \mathbf{E} = -\frac{\partial \mathbf{B}}{\partial t}
$$

**Ampère-Maxwell Law:**
$$
\nabla \times \mathbf{B} = \mathbf{J} + \frac{\partial \mathbf{E}}{\partial t}
$$

where $\mathbf{E}$ is the electric field, $\mathbf{B}$ is the magnetic field, $\rho$ is charge density, and $\mathbf{J}$ is current density.

## Building the 4-Vector Formalism

### Spacetime Coordinates

In special relativity, we combine space and time into a 4-vector:

$$
x^\mu = (t, x, y, z) = (x^0, x^1, x^2, x^3)
$$

The Minkowski metric is:

$$
\eta_{\mu\nu} = \begin{pmatrix}
-1 & 0 & 0 & 0 \\
0 & 1 & 0 & 0 \\
0 & 0 & 1 & 0 \\
0 & 0 & 0 & 1
\end{pmatrix}
$$

### The 4-Gradient

The partial derivative becomes a 4-vector operator:

$$
\partial_\mu = \frac{\partial}{\partial x^\mu} = \left(\frac{\partial}{\partial t}, \nabla\right) = \left(\frac{\partial}{\partial t}, \frac{\partial}{\partial x}, \frac{\partial}{\partial y}, \frac{\partial}{\partial z}\right)
$$

With raised index:

$$
\partial^\mu = \eta^{\mu\nu} \partial_\nu = \left(-\frac{\partial}{\partial t}, \nabla\right)
$$

### The 4-Current

Charge density $\rho$ and current density $\mathbf{J}$ combine into the **4-current**:

$$
J^\mu = (\rho, \mathbf{J}) = (\rho, J^x, J^y, J^z)
$$

The continuity equation $\frac{\partial \rho}{\partial t} + \nabla \cdot \mathbf{J} = 0$ becomes:

$$
\partial_\mu J^\mu = 0
$$

### The 4-Potential

The scalar potential $\phi$ and vector potential $\mathbf{A}$ combine into the **4-potential**:

$$
A^\mu = (\phi, \mathbf{A})
$$

The fields are related to potentials by:

$$
\mathbf{E} = -\nabla\phi - \frac{\partial \mathbf{A}}{\partial t}, \quad \mathbf{B} = \nabla \times \mathbf{A}
$$

## The Electromagnetic Field Tensor

### Definition

The **electromagnetic field tensor** (or Faraday tensor) is the antisymmetric rank-2 tensor:

$$
F_{\mu\nu} = \partial_\mu A_\nu - \partial_\nu A_\mu
$$

### Components

Writing out the components explicitly in terms of $\mathbf{E}$ and $\mathbf{B}$:

$$
F_{\mu\nu} = \begin{pmatrix}
0 & E_x & E_y & E_z \\
-E_x & 0 & B_z & -B_y \\
-E_y & -B_z & 0 & B_x \\
-E_z & B_y & -B_x & 0
\end{pmatrix}
$$

With raised indices:

$$
F^{\mu\nu} = \eta^{\mu\alpha} \eta^{\nu\beta} F_{\alpha\beta} = \begin{pmatrix}
0 & -E_x & -E_y & -E_z \\
E_x & 0 & B_z & -B_y \\
E_y & -B_z & 0 & B_x \\
E_z & B_y & -B_x & 0
\end{pmatrix}
$$

### The Dual Tensor

The **Hodge dual** of $F^{\mu\nu}$ is defined using the Levi-Civita symbol:

$$
\tilde{F}^{\mu\nu} = \frac{1}{2} \epsilon^{\mu\nu\rho\sigma} F_{\rho\sigma}
$$

where $\epsilon^{0123} = +1$. The dual tensor swaps the roles of $\mathbf{E}$ and $\mathbf{B}$:

$$
\tilde{F}^{\mu\nu} = \begin{pmatrix}
0 & -B_x & -B_y & -B_z \\
B_x & 0 & -E_z & E_y \\
B_y & E_z & 0 & -E_x \\
B_z & -E_y & E_x & 0
\end{pmatrix}
$$

## Maxwell's Equations in Tensor Form

### The Inhomogeneous Equations

Gauss's law and the Ampère-Maxwell law combine into:

$$
\boxed{\partial_\mu F^{\mu\nu} = J^\nu}
$$

**Verification:**

For $\nu = 0$:
$$
\partial_\mu F^{\mu 0} = \partial_i F^{i0} = \partial_i E^i = \nabla \cdot \mathbf{E} = \rho = J^0 \quad \checkmark
$$

For $\nu = j$ (spatial):
$$
\partial_\mu F^{\mu j} = \partial_0 F^{0j} + \partial_i F^{ij} = -\frac{\partial E^j}{\partial t} + (\nabla \times \mathbf{B})^j = J^j \quad \checkmark
$$

### The Homogeneous Equations

Gauss's law for magnetism and Faraday's law combine into:

$$
\boxed{\partial_\mu \tilde{F}^{\mu\nu} = 0}
$$

Or equivalently, using the **Bianchi identity**:

$$
\boxed{\partial_\mu F_{\nu\rho} + \partial_\nu F_{\rho\mu} + \partial_\rho F_{\mu\nu} = 0}
$$

This can be written more compactly as:

$$
\partial_{[\mu} F_{\nu\rho]} = 0
$$

**Verification:**

For $\nu = 0$:
$$
\partial_\mu \tilde{F}^{\mu 0} = \partial_i B^i = \nabla \cdot \mathbf{B} = 0 \quad \checkmark
$$

For $\nu = j$ (spatial):
$$
\partial_\mu \tilde{F}^{\mu j} = \frac{\partial B^j}{\partial t} + (\nabla \times \mathbf{E})^j = 0 \quad \checkmark
$$

## Summary: From Four Equations to Two

| 3D Maxwell Equations | Covariant Form |
|---------------------|----------------|
| $\nabla \cdot \mathbf{E} = \rho$ | $\partial_\mu F^{\mu\nu} = J^\nu$ |
| $\nabla \times \mathbf{B} = \mathbf{J} + \frac{\partial \mathbf{E}}{\partial t}$ | (inhomogeneous) |
| $\nabla \cdot \mathbf{B} = 0$ | $\partial_\mu \tilde{F}^{\mu\nu} = 0$ |
| $\nabla \times \mathbf{E} = -\frac{\partial \mathbf{B}}{\partial t}$ | (homogeneous) |

## The Single Equation Form

Using differential forms, both equations can be written as a **single equation**. Define the 2-form:

$$
F = \frac{1}{2} F_{\mu\nu} \, dx^\mu \wedge dx^\nu
$$

and the 1-form current:

$$
J = J_\mu \, dx^\mu
$$

Then Maxwell's equations become:

$$
\boxed{dF = 0, \quad d{\star}F = {\star}J}
$$

where $d$ is the exterior derivative and $\star$ is the Hodge star operator.

In even more compact notation using the codifferential $\delta = \star d \star$:

$$
\boxed{dF = 0, \quad \delta F = J}
$$

Or, if we introduce the 4-potential 1-form $A = A_\mu dx^\mu$ with $F = dA$, the homogeneous equation is automatic ($d^2 = 0$), and we have:

$$
\boxed{\delta \, dA = J}
$$

This is the **single equation** that encapsulates all of Maxwell's electromagnetism.

## Lorentz Covariance

The beauty of this formulation is manifest **Lorentz covariance**. Under a Lorentz transformation $\Lambda^\mu{}_\nu$:

$$
F'^{\mu\nu} = \Lambda^\mu{}_\alpha \Lambda^\nu{}_\beta F^{\alpha\beta}
$$

The equations $\partial_\mu F^{\mu\nu} = J^\nu$ and $\partial_\mu \tilde{F}^{\mu\nu} = 0$ transform covariantly, automatically guaranteeing that Maxwell's equations have the same form in all inertial frames.

This was one of the key insights that led Einstein to special relativity: Maxwell's equations were already relativistically correct, while Newtonian mechanics needed modification.
