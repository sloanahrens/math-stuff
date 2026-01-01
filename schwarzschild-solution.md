# The Schwarzschild Solution

The Schwarzschild solution is the unique spherically symmetric vacuum solution to Einstein's field equations. It describes the spacetime geometry outside a non-rotating, uncharged, spherically symmetric mass.

## Einstein Field Equations

In vacuum (where the stress-energy tensor $T_{\mu\nu} = 0$), Einstein's field equations reduce to:

$$
R_{\mu\nu} = 0
$$

where $R_{\mu\nu}$ is the Ricci tensor. The full Einstein equations with matter are:

$$
R_{\mu\nu} - \frac{1}{2} R g_{\mu\nu} = 8\pi T_{\mu\nu}
$$

where $R$ is the Ricci scalar and $g_{\mu\nu}$ is the metric tensor. We use units where $G = c = 1$.

## The Schwarzschild Metric

In Schwarzschild coordinates $(t, r, \theta, \phi)$, the line element is:

$$
ds^2 = -\left(1 - \frac{2M}{r}\right) dt^2 + \left(1 - \frac{2M}{r}\right)^{-1} dr^2 + r^2 \left(d\theta^2 + \sin^2\theta \, d\phi^2\right)
$$

Or equivalently, the metric tensor components are:

$$
g_{\mu\nu} = \begin{pmatrix}
-\left(1 - \frac{2M}{r}\right) & 0 & 0 & 0 \\
0 & \left(1 - \frac{2M}{r}\right)^{-1} & 0 & 0 \\
0 & 0 & r^2 & 0 \\
0 & 0 & 0 & r^2 \sin^2\theta
\end{pmatrix}
$$

where $M$ is the mass of the central object.

## The Schwarzschild Radius

The **Schwarzschild radius** (or gravitational radius) is defined as:

$$
r_s = 2M
$$

In SI units, this is $r_s = \frac{2GM}{c^2}$. For reference:
- Sun: $r_s \approx 3 \text{ km}$
- Earth: $r_s \approx 9 \text{ mm}$

## Key Features

### Event Horizon

At $r = r_s = 2M$, the metric has a **coordinate singularity**:
- $g_{tt} \to 0$
- $g_{rr} \to \infty$

This defines the **event horizon** of a black hole. This singularity is removable by choosing different coordinates (e.g., Eddington-Finkelstein or Kruskal-Szekeres).

### True Singularity

At $r = 0$, there is a **physical singularity** where the curvature diverges. The Kretschmann scalar:

$$
K = R_{\mu\nu\rho\sigma} R^{\mu\nu\rho\sigma} = \frac{48 M^2}{r^6}
$$

diverges as $r \to 0$, indicating genuine spacetime curvature singularity.

### Asymptotic Flatness

As $r \to \infty$:

$$
ds^2 \to -dt^2 + dr^2 + r^2 d\Omega^2
$$

recovering flat Minkowski spacetime in spherical coordinates, where $d\Omega^2 = d\theta^2 + \sin^2\theta \, d\phi^2$.

## Christoffel Symbols

The non-vanishing Christoffel symbols $\Gamma^\alpha_{\beta\gamma}$ for the Schwarzschild metric are:

$$
\Gamma^t_{tr} = \Gamma^t_{rt} = \frac{M}{r(r - 2M)}
$$

$$
\Gamma^r_{tt} = \frac{M(r - 2M)}{r^3}, \quad \Gamma^r_{rr} = \frac{-M}{r(r - 2M)}
$$

$$
\Gamma^r_{\theta\theta} = -(r - 2M), \quad \Gamma^r_{\phi\phi} = -(r - 2M)\sin^2\theta
$$

$$
\Gamma^\theta_{r\theta} = \Gamma^\theta_{\theta r} = \frac{1}{r}, \quad \Gamma^\theta_{\phi\phi} = -\sin\theta \cos\theta
$$

$$
\Gamma^\phi_{r\phi} = \Gamma^\phi_{\phi r} = \frac{1}{r}, \quad \Gamma^\phi_{\theta\phi} = \Gamma^\phi_{\phi\theta} = \cot\theta
$$

## Geodesics

Test particles follow geodesics given by:

$$
\frac{d^2 x^\mu}{d\tau^2} + \Gamma^\mu_{\alpha\beta} \frac{dx^\alpha}{d\tau} \frac{dx^\beta}{d\tau} = 0
$$

Due to the symmetries (time translation and spherical symmetry), there are conserved quantities:

**Energy per unit mass:**
$$
E = \left(1 - \frac{2M}{r}\right) \frac{dt}{d\tau}
$$

**Angular momentum per unit mass:**
$$
L = r^2 \frac{d\phi}{d\tau}
$$

The effective potential for radial motion (in the equatorial plane $\theta = \pi/2$) is:

$$
V_{\text{eff}}(r) = \left(1 - \frac{2M}{r}\right)\left(1 + \frac{L^2}{r^2}\right)
$$

## Historical Note

Karl Schwarzschild derived this solution in 1916, just months after Einstein published his field equations, while serving in the German army during World War I. He died shortly thereafter. The solution was the first exact solution to the Einstein equations and remains one of the most important in general relativity.
