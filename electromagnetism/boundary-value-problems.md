# Boundary Value Problems in Electromagnetism

Solving electromagnetic problems often means finding potentials that satisfy Laplace's or Poisson's equation with specific boundary conditions. This document develops the systematic methods—separation of variables, multipole expansion, and [Green's functions](../math-foundations/greens-functions.md)—that appear throughout physics. Prerequisites: [electrostatics](electrostatics.md), [vector calculus](../math-foundations/vector-calculus.md), [special functions](../math-foundations/special-functions.md).

## The Problems

### Laplace's Equation

In charge-free regions:

```math
\nabla^2 \phi = 0
```

### Poisson's Equation

With charge density $\rho$:

```math
\nabla^2 \phi = -\frac{\rho}{\epsilon_0}
```

### Boundary Conditions

| Type | Condition | Physical Meaning |
|------|-----------|------------------|
| Dirichlet | $\phi = f$ on boundary | Potential specified |
| Neumann | $\partial\phi/\partial n = g$ on boundary | Normal E-field specified |
| Mixed | Combination | Conductor + charge |

### Uniqueness Theorem

If $\phi$ satisfies Poisson's equation in a region $V$ and either Dirichlet or Neumann conditions on the boundary $S$, the solution is unique (up to a constant for pure Neumann).

**What this means:** Once we find *any* solution satisfying the boundary conditions, we've found *the* solution.

## Separation of Variables

### The Method

Assume the solution factors: $\phi(x, y, z) = X(x)Y(y)Z(z)$ (or appropriate coordinates).

Substituting into Laplace's equation separates it into ODEs for each factor.

### Cartesian Coordinates

```math
\nabla^2\phi = \frac{\partial^2\phi}{\partial x^2} + \frac{\partial^2\phi}{\partial y^2} + \frac{\partial^2\phi}{\partial z^2} = 0
```

Assume $\phi = X(x)Y(y)Z(z)$:

```math
\frac{X''}{X} + \frac{Y''}{Y} + \frac{Z''}{Z} = 0
```

Each term must be constant: $X'' = -k_x^2 X$, etc., with $k_x^2 + k_y^2 + k_z^2 = 0$.

**Solutions:**
- Oscillatory: $\sin(kx)$, $\cos(kx)$
- Exponential: $e^{\pm kx}$, $\sinh(kx)$, $\cosh(kx)$

### Example: Rectangular Box

For a box with $\phi = 0$ on all faces except $z = c$ where $\phi = V_0$:

```math
\phi(x,y,z) = \sum_{n,m=1}^{\infty} A_{nm} \sin\frac{n\pi x}{a}\sin\frac{m\pi y}{b}\frac{\sinh(\gamma_{nm}z)}{\sinh(\gamma_{nm}c)}
```

where $\gamma_{nm} = \sqrt{(n\pi/a)^2 + (m\pi/b)^2}$.

The coefficients $A_{nm}$ are determined by the boundary condition at $z = c$ via Fourier series.

### Cylindrical Coordinates

```math
\nabla^2\phi = \frac{1}{s}\frac{\partial}{\partial s}\left(s\frac{\partial\phi}{\partial s}\right) + \frac{1}{s^2}\frac{\partial^2\phi}{\partial\phi^2} + \frac{\partial^2\phi}{\partial z^2} = 0
```

Assume $\phi = R(s)\Phi(\phi)Z(z)$:

```math
\frac{s}{R}\frac{d}{ds}\left(s\frac{dR}{ds}\right) + \frac{1}{\Phi}\frac{d^2\Phi}{d\phi^2} + s^2\frac{Z''}{Z} = 0
```

**Angular part:** $\Phi'' = -m^2\Phi$ gives $\Phi = e^{\pm im\phi}$. Single-valuedness requires integer $m$.

**Radial part:** Bessel's equation—solutions are $J_m(ks)$, $N_m(ks)$ (or $I_m$, $K_m$ for modified).

**Axial part:** Exponentials $e^{\pm kz}$.

### Example: Cylinder with Potential on Ends

For a cylinder of radius $a$ with $\phi = 0$ on the curved surface and $\phi = V_0$ on one end:

```math
\phi(s,z) = \sum_{n=1}^{\infty} A_n J_0\left(\frac{x_{0n}s}{a}\right)\frac{\sinh(x_{0n}z/a)}{\sinh(x_{0n}L/a)}
```

where $x_{0n}$ are zeros of $J_0$.

### Spherical Coordinates

```math
\nabla^2\phi = \frac{1}{r^2}\frac{\partial}{\partial r}\left(r^2\frac{\partial\phi}{\partial r}\right) + \frac{1}{r^2\sin\theta}\frac{\partial}{\partial\theta}\left(\sin\theta\frac{\partial\phi}{\partial\theta}\right) + \frac{1}{r^2\sin^2\theta}\frac{\partial^2\phi}{\partial\phi^2} = 0
```

**Azimuthal symmetry** ($\phi$-independent): The general solution is

```math
\boxed{\phi(r,\theta) = \sum_{\ell=0}^{\infty}\left(A_\ell r^\ell + \frac{B_\ell}{r^{\ell+1}}\right)P_\ell(\cos\theta)}
```

where $P_\ell$ are [Legendre polynomials](../math-foundations/special-functions.md).

**Full angular dependence:** Solutions involve [spherical harmonics](../math-foundations/special-functions.md) $Y_\ell^m(\theta, \phi)$.

### Example: Sphere in Uniform Field

A conducting sphere of radius $R$ in uniform field $E_0\hat{z}$:

Boundary conditions:
- $\phi \to -E_0 z = -E_0 r\cos\theta$ as $r \to \infty$
- $\phi = 0$ on sphere (constant on conductor)

Solution:

```math
\phi(r,\theta) = -E_0\left(r - \frac{R^3}{r^2}\right)\cos\theta
```

The induced surface charge:

```math
\sigma = -\epsilon_0\frac{\partial\phi}{\partial r}\bigg|_{r=R} = 3\epsilon_0 E_0 \cos\theta
```

## The Method of Images

### The Idea

Replace conducting boundaries with fictitious "image" charges placed outside the physical region such that boundary conditions are satisfied.

### Point Charge Near a Conducting Plane

For charge $q$ at distance $d$ from an infinite grounded plane:

**Image:** Charge $-q$ at distance $d$ on the other side.

```math
\phi(\mathbf{r}) = \frac{q}{4\pi\epsilon_0}\left(\frac{1}{|\mathbf{r} - \mathbf{r}_q|} - \frac{1}{|\mathbf{r} - \mathbf{r}_{\text{image}}|}\right)
```

**Induced charge:** $\sigma = -\epsilon_0 \partial\phi/\partial z|_{z=0} = -\frac{qd}{2\pi(x^2+y^2+d^2)^{3/2}}$

**Total induced charge:** $\int \sigma \, dA = -q$

**Force on charge:** $F = \frac{q^2}{4\pi\epsilon_0(2d)^2}$ (attractive)

### Point Charge Near a Conducting Sphere

For charge $q$ at distance $p$ from center of grounded sphere of radius $R$:

**Image:** Charge $q' = -qR/p$ at distance $p' = R^2/p$ from center (inside sphere).

### Dielectric Interfaces

For charge $q$ near a planar interface between media $\epsilon_1$ and $\epsilon_2$:

**In medium 1:** Add image charge $q' = q\frac{\epsilon_1 - \epsilon_2}{\epsilon_1 + \epsilon_2}$ at mirror position.

**In medium 2:** Replace $q$ with $q'' = q\frac{2\epsilon_2}{\epsilon_1 + \epsilon_2}$ at original position.

## Multipole Expansion

### The Potential of a Charge Distribution

For a localized charge distribution, at large $r$:

```math
\boxed{\phi(\mathbf{r}) = \frac{1}{4\pi\epsilon_0}\sum_{\ell=0}^{\infty}\frac{1}{r^{\ell+1}}\sum_{m=-\ell}^{\ell}q_{\ell m}Y_\ell^m(\theta,\phi)}
```

where the **multipole moments** are:

```math
q_{\ell m} = \int r'^\ell Y_\ell^{m*}(\theta',\phi')\rho(\mathbf{r}')d^3r'
```

### First Few Multipoles

**Monopole ($\ell = 0$):**
```math
q_{00} = \frac{1}{\sqrt{4\pi}}Q, \quad \phi_0 = \frac{Q}{4\pi\epsilon_0 r}
```

**Dipole ($\ell = 1$):**
```math
\phi_1 = \frac{1}{4\pi\epsilon_0}\frac{\mathbf{p}\cdot\hat{\mathbf{r}}}{r^2}
```

where $\mathbf{p} = \int \mathbf{r}'\rho(\mathbf{r}')d^3r'$ is the dipole moment.

**Quadrupole ($\ell = 2$):**
```math
\phi_2 = \frac{1}{4\pi\epsilon_0}\frac{1}{2r^3}\sum_{ij}Q_{ij}\hat{r}_i\hat{r}_j
```

where the quadrupole tensor is:
```math
Q_{ij} = \int (3r'_i r'_j - r'^2\delta_{ij})\rho(\mathbf{r}')d^3r'
```

### Physical Interpretation

| Multipole | Depends on | Falls off as | Example |
|-----------|------------|--------------|---------|
| Monopole | Total charge | $1/r$ | Point charge |
| Dipole | Charge separation | $1/r^2$ | CO molecule |
| Quadrupole | Charge distribution shape | $1/r^3$ | CO₂ molecule |

### Multipoles for Symmetric Distributions

**Azimuthally symmetric:** Only $m = 0$ terms (Legendre polynomials).

**Spherically symmetric:** Only monopole.

**Inversion symmetric:** Only even $\ell$.

**Point charges:** If total charge is zero, dominant term is dipole. If dipole is zero, dominant is quadrupole.

## Green's Functions for Electrostatics

### Dirichlet Green's Function

The Green's function satisfies:

```math
\nabla^2 G(\mathbf{r}, \mathbf{r}') = \delta(\mathbf{r} - \mathbf{r}')
```

with $G = 0$ on the boundary.

The solution to Poisson's equation with $\phi = f$ on boundary:

```math
\phi(\mathbf{r}) = \frac{1}{\epsilon_0}\int_V G(\mathbf{r}, \mathbf{r}')\rho(\mathbf{r}')d^3r' - \oint_S f\frac{\partial G}{\partial n'}dA'
```

### Free-Space Green's Function

```math
G_0(\mathbf{r}, \mathbf{r}') = -\frac{1}{4\pi|\mathbf{r} - \mathbf{r}'|}
```

### Green's Function for a Sphere

For Dirichlet conditions on a sphere of radius $a$:

```math
G(\mathbf{r}, \mathbf{r}') = -\frac{1}{4\pi|\mathbf{r} - \mathbf{r}'|} + \frac{a}{4\pi r'|\mathbf{r} - (a^2/r'^2)\mathbf{r}'|}
```

This is the method of images in Green's function language.

### Expansion in Eigenfunctions

```math
G(\mathbf{r}, \mathbf{r}') = \sum_n \frac{\psi_n(\mathbf{r})\psi_n^*(\mathbf{r}')}{\lambda_n}
```

where $\psi_n$ are eigenfunctions of the Laplacian with the given boundary conditions.

## Numerical Methods

### Finite Difference Method

Discretize on a grid. Approximate:

```math
\nabla^2\phi \approx \frac{\phi_{i+1} + \phi_{i-1} + \phi_{j+1} + \phi_{j-1} - 4\phi_{ij}}{h^2}
```

Set equal to $-\rho/\epsilon_0$ and solve the linear system.

### Relaxation Methods

**Jacobi:** Update all points using old values.

**Gauss-Seidel:** Update using most recent values (faster convergence).

**Successive Over-Relaxation (SOR):** Accelerated Gauss-Seidel.

### Finite Element Method

Divide domain into elements, approximate $\phi$ by polynomials on each, minimize energy functional.

### Boundary Element Method

Discretize only the boundary; use Green's functions to propagate to interior. Efficient for complex 3D geometries.

## Summary

| Method | Best For | Key Idea |
|--------|----------|----------|
| Separation of variables | High-symmetry geometries | Factor solution, use orthogonality |
| Method of images | Simple boundaries (planes, spheres) | Add fictitious charges to satisfy BC |
| Multipole expansion | Far-field of localized sources | Expand in $1/r$ powers |
| Green's functions | General problems, point sources | Superposition of impulse responses |
| Numerical methods | Complex geometries | Discretize and solve linear system |

| Geometry | Coordinate System | Special Functions |
|----------|-------------------|-------------------|
| Rectangular | Cartesian | $\sin$, $\cos$, $\sinh$, $\cosh$ |
| Cylindrical | Cylindrical | Bessel $J_m$, $N_m$, $I_m$, $K_m$ |
| Spherical | Spherical | Legendre $P_\ell$, spherical harmonics $Y_\ell^m$ |

**The essential insight:** Boundary value problems in electrostatics reduce to finding the right superposition of solutions to Laplace's equation that match the boundary conditions. Each coordinate system has its natural solutions—trigonometric for Cartesian, Bessel for cylindrical, Legendre and spherical harmonics for spherical. The method of images provides exact solutions for simple boundaries; multipole expansions characterize fields far from sources; Green's functions encode everything about a geometry. These same mathematical techniques appear throughout physics: heat conduction, wave equations, [quantum mechanics](../quantum-mechanics/quantum-mechanics.md)—wherever boundary conditions constrain solutions to linear PDEs.
