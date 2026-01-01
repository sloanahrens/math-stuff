# Green's Functions

Green's functions are the fundamental solutions to linear differential equations with source terms. They encode the response of a system to a point impulse, allowing general solutions to be built by superposition. This is essential for [electrostatics](../electromagnetism/electrostatics.md), [quantum mechanics](../quantum-mechanics/quantum-mechanics.md) (propagators), and wave phenomena. Prerequisites: [calculus](calculus-primer.md), [vector calculus](vector-calculus.md), [Fourier analysis](fourier-analysis.md).

## The Central Idea

### What is a Green's Function?

For a linear differential operator $\mathcal{L}$ and source function $\rho(\mathbf{r})$, we want to solve:

$$
\mathcal{L} u(\mathbf{r}) = \rho(\mathbf{r})
$$

The **Green's function** $G(\mathbf{r}, \mathbf{r}')$ is the response to a point source:

$$
\boxed{\mathcal{L} G(\mathbf{r}, \mathbf{r}') = \delta(\mathbf{r} - \mathbf{r}')}
$$

Once we have $G$, the solution for any source is:

$$
\boxed{u(\mathbf{r}) = \int G(\mathbf{r}, \mathbf{r}') \rho(\mathbf{r}') d^3r'}
$$

**What this means:** The Green's function is the system's "impulse response." Any source can be viewed as a sum of point sources, and the response is the corresponding sum of impulse responses.

### Physical Interpretation

| System | Green's Function Meaning |
|--------|--------------------------|
| Electrostatics | Potential of a point charge |
| Heat conduction | Temperature from a heat impulse |
| Wave equation | Response to a sudden disturbance |
| Quantum mechanics | Probability amplitude to propagate |

## Green's Function for the Laplacian

### Poisson's Equation

$$
\nabla^2 \phi = -\frac{\rho}{\epsilon_0}
$$

The Green's function satisfies:

$$
\nabla^2 G(\mathbf{r}, \mathbf{r}') = \delta(\mathbf{r} - \mathbf{r}')
$$

### Free-Space Green's Function (3D)

$$
\boxed{G(\mathbf{r}, \mathbf{r}') = -\frac{1}{4\pi|\mathbf{r} - \mathbf{r}'|}}
$$

**Derivation:** By spherical symmetry, $G$ depends only on $R = |\mathbf{r} - \mathbf{r}'|$. For $R \neq 0$:

$$
\nabla^2 G = \frac{1}{R^2}\frac{d}{dR}\left(R^2 \frac{dG}{dR}\right) = 0 \quad \Rightarrow \quad G = \frac{A}{R}
$$

The constant comes from integrating over a small sphere around $\mathbf{r}'$:

$$
\int \nabla^2 G \, d^3r = \int \nabla G \cdot d\mathbf{S} = 4\pi R^2 \cdot \frac{A}{R^2}(-1) = -4\pi A = 1
$$

So $A = -1/(4\pi)$.

### Solution to Poisson's Equation

$$
\phi(\mathbf{r}) = \frac{1}{4\pi\epsilon_0} \int \frac{\rho(\mathbf{r}')}{|\mathbf{r} - \mathbf{r}'|} d^3r'
$$

This is exactly the formula for the electrostatic potential from [electrostatics](../electromagnetism/electrostatics.md).

### Green's Functions in Other Dimensions

| Dimension | $\nabla^2 G = \delta$ | Solution |
|-----------|------------------------|----------|
| 1D | $G'' = \delta(x-x')$ | $G = -\frac{1}{2}|x-x'|$ |
| 2D | $\nabla^2 G = \delta^{(2)}$ | $G = \frac{1}{2\pi}\ln|\mathbf{r}-\mathbf{r}'|$ |
| 3D | $\nabla^2 G = \delta^{(3)}$ | $G = -\frac{1}{4\pi|\mathbf{r}-\mathbf{r}'|}$ |

## Boundary Conditions

### The Role of Boundaries

The free-space Green's function must be modified when boundaries are present. We need:

$$
\mathcal{L} G = \delta \quad \text{plus boundary conditions on } G
$$

### Dirichlet Boundary Conditions

$G(\mathbf{r}, \mathbf{r}') = 0$ when $\mathbf{r}$ is on the boundary.

The solution then satisfies $u = 0$ on the boundary.

### Neumann Boundary Conditions

$\nabla G \cdot \hat{n} = 0$ on the boundary (normal derivative vanishes).

The solution has zero normal derivative on the boundary.

### Uniqueness

For well-posed problems, the Green's function satisfying given boundary conditions is unique.

## Method of Images

### The Idea

For problems with simple boundary geometry, the Green's function can be constructed by adding "image" sources outside the physical region.

### Example: Conducting Plane

For a point charge $q$ at distance $d$ from an infinite grounded conducting plane:

Place an image charge $-q$ at distance $d$ on the other side of the plane.

The Green's function:

$$
G(\mathbf{r}, \mathbf{r}') = -\frac{1}{4\pi|\mathbf{r} - \mathbf{r}'|} + \frac{1}{4\pi|\mathbf{r} - \mathbf{r}''|}
$$

where $\mathbf{r}'' = \mathbf{r}'$ reflected across the plane.

**What this means:** The image charge ensures $G = 0$ on the conducting surface. The actual field exists only in the physical region.

### Example: Conducting Sphere

For a grounded sphere of radius $a$ centered at the origin and point charge at $\mathbf{r}'$:

Image charge: $q' = -q(a/r')$ at position $\mathbf{r}'' = (a^2/r'^2)\mathbf{r}'$.

The Green's function satisfies $G = 0$ on the sphere.

## The Helmholtz Equation

### Definition

$$
(\nabla^2 + k^2) G = \delta(\mathbf{r} - \mathbf{r}')
$$

This arises from time-harmonic wave equations.

### Free-Space Green's Function (3D)

$$
\boxed{G(\mathbf{r}, \mathbf{r}') = -\frac{e^{ik|\mathbf{r}-\mathbf{r}'|}}{4\pi|\mathbf{r}-\mathbf{r}'|}}
$$

This is the **outgoing wave** (or retarded) Green's function.

The **incoming wave** Green's function has $e^{-ik|\mathbf{r}-\mathbf{r}'|}$.

**What this means:** The outgoing Green's function represents spherical waves radiating from the source—the physical solution for radiation problems.

### Connection to Laplacian

As $k \to 0$, the Helmholtz Green's function approaches the Laplacian Green's function.

## Green's Functions for the Wave Equation

### The Wave Equation

$$
\left(\nabla^2 - \frac{1}{c^2}\frac{\partial^2}{\partial t^2}\right) G = \delta(\mathbf{r} - \mathbf{r}')\delta(t - t')
$$

### Retarded Green's Function

$$
\boxed{G_{\text{ret}}(\mathbf{r}, t; \mathbf{r}', t') = \frac{\delta(t - t' - |\mathbf{r}-\mathbf{r}'|/c)}{4\pi|\mathbf{r}-\mathbf{r}'|}}
$$

**What this means:** The response at $(\mathbf{r}, t)$ depends on the source at $(\mathbf{r}', t')$ only if a signal traveling at speed $c$ could connect them. This is **causality**.

### Advanced Green's Function

$$
G_{\text{adv}}(\mathbf{r}, t; \mathbf{r}', t') = \frac{\delta(t - t' + |\mathbf{r}-\mathbf{r}'|/c)}{4\pi|\mathbf{r}-\mathbf{r}'|}
$$

This has the source in the future of the effect—unphysical for radiation, but mathematically valid.

### Solution to Inhomogeneous Wave Equation

For source $\rho(\mathbf{r}, t)$:

$$
\phi(\mathbf{r}, t) = \int \frac{\rho(\mathbf{r}', t_{\text{ret}})}{4\pi|\mathbf{r}-\mathbf{r}'|} d^3r'
$$

where $t_{\text{ret}} = t - |\mathbf{r}-\mathbf{r}'|/c$ is the **retarded time**.

This is the basis for **Jefimenko's equations** and radiation from accelerating charges.

## Green's Functions via Eigenfunction Expansion

### The Method

If $\mathcal{L}$ has eigenfunctions $\psi_n$ with eigenvalues $\lambda_n$:

$$
\mathcal{L}\psi_n = \lambda_n \psi_n
$$

and the eigenfunctions are orthonormal, then:

$$
\boxed{G(\mathbf{r}, \mathbf{r}') = \sum_n \frac{\psi_n(\mathbf{r})\psi_n^*(\mathbf{r}')}{\lambda_n}}
$$

### Example: 1D Box

For $-d^2/dx^2$ with $u(0) = u(L) = 0$:

Eigenfunctions: $\psi_n = \sqrt{2/L}\sin(n\pi x/L)$, eigenvalues: $\lambda_n = (n\pi/L)^2$

$$
G(x, x') = \frac{2}{L}\sum_{n=1}^{\infty} \frac{\sin(n\pi x/L)\sin(n\pi x'/L)}{(n\pi/L)^2}
$$

This can be summed to give:

$$
G(x, x') = \begin{cases}
\frac{x(L-x')}{L} & x < x' \\
\frac{x'(L-x)}{L} & x > x'
\end{cases}
$$

### Continuous Spectrum

For unbounded regions, sums become integrals:

$$
G(\mathbf{r}, \mathbf{r}') = \int \frac{\psi_k(\mathbf{r})\psi_k^*(\mathbf{r}')}{\lambda(k)} dk
$$

## Green's Functions in Quantum Mechanics

### The Propagator

The **quantum propagator** $K(\mathbf{r}, t; \mathbf{r}', t')$ is the probability amplitude for a particle at $(\mathbf{r}', t')$ to be found at $(\mathbf{r}, t)$:

$$
\psi(\mathbf{r}, t) = \int K(\mathbf{r}, t; \mathbf{r}', t') \psi(\mathbf{r}', t') d^3r'
$$

### Free Particle Propagator

For a free particle with $H = -\frac{\hbar^2}{2m}\nabla^2$:

$$
K_0(\mathbf{r}, t; \mathbf{r}', 0) = \left(\frac{m}{2\pi i\hbar t}\right)^{3/2} \exp\left(\frac{im|\mathbf{r}-\mathbf{r}'|^2}{2\hbar t}\right)
$$

### Energy-Domain Green's Function

Taking Fourier transform in time:

$$
G(\mathbf{r}, \mathbf{r}'; E) = \int_0^\infty K(\mathbf{r}, t; \mathbf{r}', 0) e^{iEt/\hbar} dt
$$

The **retarded** Green's function has poles just below the real axis; the **advanced** has poles above.

**What this means:** Bound states appear as poles of the Green's function at negative energies. Scattering states form the continuous spectrum along the positive real axis.

### Connection to Scattering

The Lippmann-Schwinger equation:

$$
|\psi\rangle = |\phi\rangle + G_0 V |\psi\rangle
$$

relates the full scattering wave function to the incident wave via the free Green's function.

## Green's Function for the Diffusion Equation

### The Heat Kernel

$$
\left(\nabla^2 - \frac{1}{\kappa}\frac{\partial}{\partial t}\right) G = \delta(\mathbf{r} - \mathbf{r}')\delta(t - t')
$$

Solution (for $t > t'$):

$$
G(\mathbf{r}, t; \mathbf{r}', t') = \frac{1}{[4\pi\kappa(t-t')]^{3/2}} \exp\left(-\frac{|\mathbf{r}-\mathbf{r}'|^2}{4\kappa(t-t')}\right)
$$

**What this means:** This is a Gaussian that spreads with time—heat (or probability in the random walk interpretation) diffuses away from the source.

## Dyadic Green's Functions

### Vector Wave Equations

For electromagnetic fields, the Green's function becomes a tensor (dyadic):

$$
\nabla \times \nabla \times \mathbf{G} - k^2 \mathbf{G} = \mathbf{I}\delta(\mathbf{r} - \mathbf{r}')
$$

The electric field from a current distribution:

$$
\mathbf{E}(\mathbf{r}) = i\omega\mu_0 \int \mathbf{G}(\mathbf{r}, \mathbf{r}') \cdot \mathbf{J}(\mathbf{r}') d^3r'
$$

## Summary

| Equation | Green's Function | Application |
|----------|------------------|-------------|
| $\nabla^2 G = \delta$ | $-\frac{1}{4\pi r}$ | Electrostatics |
| $(\nabla^2 + k^2)G = \delta$ | $-\frac{e^{ikr}}{4\pi r}$ | Helmholtz, radiation |
| $(\nabla^2 - \frac{1}{c^2}\partial_t^2)G = \delta$ | $\frac{\delta(t-r/c)}{4\pi r}$ | Retarded waves |
| $(\nabla^2 - \frac{1}{\kappa}\partial_t)G = \delta$ | Gaussian in $r$, spreading in $t$ | Heat diffusion |
| $(\hat{H} - E)G = \delta$ | Poles at bound states | Quantum propagator |

| Method | When to Use |
|--------|-------------|
| Direct solution | Simple geometries |
| Method of images | Planar, spherical, cylindrical boundaries |
| Eigenfunction expansion | Bounded regions with known eigenfunctions |
| Fourier transform | Unbounded, homogeneous media |

**The essential insight:** Green's functions convert differential equations into integrals. The differential operator encodes the physics (wave propagation, diffusion, electrostatics); the Green's function encodes the response to a unit impulse. Any source is a superposition of impulses, so any solution is a superposition of Green's function responses. This divide-and-conquer strategy underlies perturbation theory, scattering theory, and path integrals throughout physics.
