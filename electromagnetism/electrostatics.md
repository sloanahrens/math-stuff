# Electrostatics

Electrostatics describes electric fields and potentials when charges are stationary. It's the foundation for understanding [Maxwell's equations](maxwell-equations.md) and is essential for atomic physics, chemistry, and electronics. This document uses [vector calculus](../prerequisites/vector-calculus.md), particularly the divergence theorem.

## Coulomb's Law

### The Force Between Point Charges

Two point charges $q_1$ and $q_2$ separated by distance $r$ exert forces on each other:

$$
\boxed{\mathbf{F}_{12} = \frac{1}{4\pi\epsilon_0} \frac{q_1 q_2}{r^2} \hat{\mathbf{r}}_{12}}
$$

where $\hat{\mathbf{r}}_{12}$ points from charge 1 to charge 2.

| Constant | Value |
|----------|-------|
| $\epsilon_0$ | $8.85 \times 10^{-12}$ F/m |
| $k = 1/(4\pi\epsilon_0)$ | $8.99 \times 10^9$ N·m²/C² |

**What this means:** Like charges repel, opposite charges attract. The force is proportional to each charge and falls off as $1/r^2$—the same dependence as gravity, but vastly stronger.

### Superposition

For multiple charges, forces add vectorially:

$$
\mathbf{F} = \frac{q}{4\pi\epsilon_0} \sum_i \frac{q_i}{r_i^2} \hat{\mathbf{r}}_i
$$

**What this means:** Each charge exerts its force independently; you simply add them up. This linearity is fundamental.

## The Electric Field

### Definition

The electric field $\mathbf{E}$ at a point is the force per unit charge:

$$
\mathbf{E} = \frac{\mathbf{F}}{q} = \lim_{q \to 0} \frac{\mathbf{F}}{q}
$$

For a point charge $Q$:

$$
\boxed{\mathbf{E} = \frac{1}{4\pi\epsilon_0} \frac{Q}{r^2} \hat{\mathbf{r}}}
$$

**What this means:** The field exists in space whether or not a test charge is present. It tells you what force any charge would experience.

### Field from Continuous Distributions

For charge density $\rho(\mathbf{r}')$:

$$
\mathbf{E}(\mathbf{r}) = \frac{1}{4\pi\epsilon_0} \int \frac{\rho(\mathbf{r}')}{|\mathbf{r} - \mathbf{r}'|^2} \hat{\mathbf{r}} \, d^3r'
$$

For surface charge $\sigma$ or line charge $\lambda$, replace $\rho \, d^3r'$ with $\sigma \, dA'$ or $\lambda \, dl'$.

## Gauss's Law

### Statement

$$
\boxed{\oint_S \mathbf{E} \cdot d\mathbf{A} = \frac{Q_{\text{enc}}}{\epsilon_0}}
$$

The electric flux through any closed surface equals the enclosed charge divided by $\epsilon_0$.

### Differential Form

$$
\nabla \cdot \mathbf{E} = \frac{\rho}{\epsilon_0}
$$

**What this means:** Electric field lines originate from positive charges and terminate on negative charges. Gauss's law is one of Maxwell's equations.

### Using Gauss's Law

Gauss's law is useful when symmetry makes $\mathbf{E}$ constant over a convenient surface:

**Point charge / Sphere:**
$$
E = \frac{Q}{4\pi\epsilon_0 r^2}
$$

**Infinite line charge ($\lambda$ per unit length):**
$$
E = \frac{\lambda}{2\pi\epsilon_0 r}
$$

**Infinite plane ($\sigma$ per unit area):**
$$
E = \frac{\sigma}{2\epsilon_0}
$$

**What this means:** With high symmetry, one integral gives the field everywhere. Without symmetry, you need Coulomb's law directly.

## Electric Potential

### Definition

The electric potential $\phi$ is defined by:

$$
\mathbf{E} = -\nabla \phi
$$

Or equivalently, the work per unit charge to bring a test charge from infinity:

$$
\phi(\mathbf{r}) = -\int_\infty^{\mathbf{r}} \mathbf{E} \cdot d\mathbf{l}
$$

**What this means:** Potential is a scalar—easier to work with than a vector field. The field is the (negative) gradient of potential.

### Potential from Point Charge

$$
\phi = \frac{1}{4\pi\epsilon_0} \frac{Q}{r}
$$

### Potential from Distributions

$$
\phi(\mathbf{r}) = \frac{1}{4\pi\epsilon_0} \int \frac{\rho(\mathbf{r}')}{|\mathbf{r} - \mathbf{r}'|} \, d^3r'
$$

**What this means:** Potentials add as scalars (no vector addition needed), then take the gradient to get $\mathbf{E}$.

### Poisson's and Laplace's Equations

From $\nabla \cdot \mathbf{E} = \rho/\epsilon_0$ and $\mathbf{E} = -\nabla\phi$:

$$
\boxed{\nabla^2 \phi = -\frac{\rho}{\epsilon_0}} \quad \text{(Poisson's equation)}
$$

In charge-free regions:

$$
\nabla^2 \phi = 0 \quad \text{(Laplace's equation)}
$$

**What this means:** Given charge distribution and boundary conditions, solving these equations determines the potential everywhere.

## Electrostatic Energy

### Energy of Point Charges

For a collection of point charges:

$$
U = \frac{1}{4\pi\epsilon_0} \sum_{i<j} \frac{q_i q_j}{r_{ij}}
$$

Or equivalently:

$$
U = \frac{1}{2} \sum_i q_i \phi_i
$$

where $\phi_i$ is the potential at charge $i$ due to all other charges.

### Energy Density

The energy stored in an electric field:

$$
u = \frac{1}{2} \epsilon_0 E^2
$$

Total energy:

$$
U = \frac{\epsilon_0}{2} \int E^2 \, d^3r
$$

**What this means:** Energy is stored in the field itself, not just "between charges." This energy is real—it can do work.

### Energy of a Charged Sphere

A uniformly charged sphere of radius $R$ with total charge $Q$:

$$
U = \frac{3}{5} \frac{Q^2}{4\pi\epsilon_0 R}
$$

**What this means:** It takes energy to assemble charge against electrostatic repulsion. This "self-energy" diverges for point charges—a classical problem resolved by quantum electrodynamics.

## Conductors

### Properties

In electrostatic equilibrium:
- $\mathbf{E} = 0$ inside the conductor
- $\phi = \text{constant}$ throughout
- All excess charge resides on the surface
- $\mathbf{E}$ at surface is perpendicular: $E = \sigma/\epsilon_0$

**What this means:** Charges in a conductor are free to move and redistribute until the field inside vanishes.

### Capacitance

For two conductors with charges $\pm Q$ and potential difference $V$:

$$
C = \frac{Q}{V}
$$

**Parallel plate capacitor:**
$$
C = \frac{\epsilon_0 A}{d}
$$

**Spherical capacitor:**
$$
C = 4\pi\epsilon_0 \frac{ab}{b-a}
$$

**Isolated sphere:**
$$
C = 4\pi\epsilon_0 R
$$

### Energy in a Capacitor

$$
U = \frac{1}{2}CV^2 = \frac{Q^2}{2C} = \frac{1}{2}QV
$$

## Dielectrics

### Polarization

In a dielectric material, the electric field induces dipole moments. The **polarization** $\mathbf{P}$ is the dipole moment per unit volume.

For linear dielectrics:

$$
\mathbf{P} = \epsilon_0 \chi_e \mathbf{E}
$$

where $\chi_e$ is the electric susceptibility.

### Electric Displacement

$$
\mathbf{D} = \epsilon_0 \mathbf{E} + \mathbf{P} = \epsilon \mathbf{E}
$$

where $\epsilon = \epsilon_0(1 + \chi_e) = \epsilon_0 \epsilon_r$ is the permittivity.

Gauss's law becomes:

$$
\nabla \cdot \mathbf{D} = \rho_f
$$

where $\rho_f$ is the free (not bound) charge.

**What this means:** The dielectric reduces the field by a factor $\epsilon_r$ (the relative permittivity or dielectric constant).

### Capacitor with Dielectric

$$
C = \epsilon_r C_0 = \frac{\epsilon A}{d}
$$

**What this means:** Dielectrics increase capacitance. This is why capacitors use ceramic, plastic, or other dielectric materials.

## The Electric Dipole

### Definition

Two charges $+q$ and $-q$ separated by displacement $\mathbf{d}$:

$$
\mathbf{p} = q\mathbf{d}
$$

### Dipole Field

Far from the dipole ($r \gg d$):

$$
\phi = \frac{1}{4\pi\epsilon_0} \frac{\mathbf{p} \cdot \hat{\mathbf{r}}}{r^2}
$$

$$
\mathbf{E} = \frac{1}{4\pi\epsilon_0} \frac{1}{r^3} [3(\mathbf{p} \cdot \hat{\mathbf{r}})\hat{\mathbf{r}} - \mathbf{p}]
$$

**What this means:** The dipole field falls off as $1/r^3$ (faster than a monopole's $1/r^2$). The field has a characteristic "figure-8" pattern.

### Dipole in External Field

**Torque:** $\boldsymbol{\tau} = \mathbf{p} \times \mathbf{E}$

**Energy:** $U = -\mathbf{p} \cdot \mathbf{E}$

**Force in non-uniform field:** $\mathbf{F} = (\mathbf{p} \cdot \nabla)\mathbf{E}$

## Boundary Value Problems

### Uniqueness

Given boundary conditions (potential on conductors or asymptotic behavior), the solution to Laplace's/Poisson's equation is unique.

### Method of Images

Replace conductors with image charges that satisfy boundary conditions:

**Point charge near grounded plane:**
Image charge $-q$ at mirror position.

**Point charge near grounded sphere:**
Image charge $q' = -(R/d)q$ at position $R^2/d$ from center.

### Separation of Variables

For high-symmetry problems, write $\phi$ as products of single-variable functions:

**Cartesian:** $\phi = X(x)Y(y)Z(z)$

**Spherical:** $\phi = R(r)\Theta(\theta)\Phi(\phi)$

This yields Legendre polynomials, spherical harmonics, etc.

## Summary

| Concept | Formula | Meaning |
|---------|---------|---------|
| Coulomb's law | $F = kq_1q_2/r^2$ | Force between point charges |
| Electric field | $\mathbf{E} = \mathbf{F}/q$ | Force per unit charge |
| Gauss's law | $\oint \mathbf{E} \cdot d\mathbf{A} = Q/\epsilon_0$ | Flux = enclosed charge |
| Potential | $\mathbf{E} = -\nabla\phi$ | Field from scalar potential |
| Poisson | $\nabla^2\phi = -\rho/\epsilon_0$ | Potential from charge density |
| Energy density | $u = \frac{1}{2}\epsilon_0 E^2$ | Energy stored in field |
| Capacitance | $C = Q/V$ | Charge per unit voltage |

**The essential insight:** Electrostatics is the study of how stationary charges create electric fields and potentials. The key equations—Coulomb's law, Gauss's law, and Poisson's equation—are different ways of expressing the same physics. Mastering these prepares you for the full dynamics of [Maxwell's equations](maxwell-equations.md) and the quantum mechanics of charged particles.
