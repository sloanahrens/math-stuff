# The Schwarzschild Solution

The Schwarzschild solution is the unique spherically symmetric vacuum solution to Einstein's field equations. It describes the spacetime geometry outside a non-rotating, uncharged, spherically symmetric mass. This document requires understanding of [general relativity](general-relativity.md) and uses [tensor calculus](../math-foundations/tensor-calculus.md) notation. For motion in this spacetime, see [geodesics](geodesics.md); for thermodynamic properties, see [black hole thermodynamics](black-hole-thermodynamics.md); for dynamical aspects, see [gravitational waves](gravitational-waves.md).

## Einstein Field Equations

In vacuum (where the stress-energy tensor $T_{\mu\nu} = 0$), Einstein's field equations reduce to:

$$
R_{\mu\nu} = 0
$$

where $R_{\mu\nu}$ is the Ricci tensor. The full Einstein equations with matter are:

$$
R_{\mu\nu} - \frac{1}{2} R g_{\mu\nu} = 8\pi T_{\mu\nu}
$$

where $R$ is the Ricci scalar and $g_{\mu\nu}$ is the metric tensor. We use [natural units](../math-foundations/natural-units.md) where $G = c = 1$.

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

## Worked Examples

### Example 1: Orbital Period of a Circular Orbit

**Problem:** Find the orbital period of a test particle in a circular orbit at radius $r$ around a mass $M$.

**Solution:** For a circular orbit, we need $dV_{\text{eff}}/dr = 0$. For the effective potential:

$$
V_{\text{eff}} = \left(1 - \frac{2M}{r}\right)\left(1 + \frac{L^2}{r^2}\right)
$$

Taking the derivative and setting to zero (for circular orbits with $r \gg 2M$):

$$
\frac{L^2}{r^2} = \frac{M}{r - 3M} \approx \frac{M}{r}
$$

The angular velocity is $\omega = d\phi/dt = (d\phi/d\tau)(d\tau/dt)$. Using the conserved quantities:

$$
\omega = \frac{L/r^2}{E/(1 - 2M/r)} = \frac{L(1 - 2M/r)}{Er^2}
$$

For nearly Newtonian orbits ($r \gg 2M$), this gives $\omega^2 = M/r^3$, so:

$$
\boxed{T = 2\pi\sqrt{\frac{r^3}{M}} = 2\pi\sqrt{\frac{r^3}{GM}} \text{ (in SI units)}}
$$

This is Kepler's third law, valid for $r \gg r_s$.

---

### Example 2: Perihelion Precession of Mercury

**Problem:** Calculate the perihelion precession per orbit for a planet with semi-major axis $a$ and eccentricity $e$.

**Solution:** The orbital equation for a test particle, derived from the geodesic equations, is:

$$
\frac{d^2 u}{d\phi^2} + u = \frac{M}{L^2} + 3Mu^2
$$

where $u = 1/r$. The last term is the relativistic correction.

Using perturbation theory, the precession per orbit is:

$$
\Delta\phi = \frac{6\pi M}{L^2/M} = \frac{6\pi M}{a(1-e^2)}
$$

In SI units:

$$
\boxed{\Delta\phi = \frac{6\pi GM}{c^2 a(1-e^2)} \text{ radians per orbit}}
$$

**For Mercury:** $a = 5.79 \times 10^{10}$ m, $e = 0.206$, $M = M_\odot$:

$$
\Delta\phi = \frac{6\pi (6.67 \times 10^{-11})(2 \times 10^{30})}{(3 \times 10^8)^2 (5.79 \times 10^{10})(1 - 0.042)} \approx 5 \times 10^{-7} \text{ rad/orbit}
$$

Over 100 years (~415 orbits): $\Delta\phi_{\text{total}} \approx 43''$ (arcseconds per century), matching observations.

---

### Example 3: Gravitational Redshift

**Problem:** A photon is emitted at radius $r_1$ and observed at radius $r_2 > r_1$. Find the redshift.

**Solution:** For a stationary emitter and observer, the photon's conserved energy is:

$$
E = \left(1 - \frac{2M}{r}\right) \frac{dt}{d\lambda}
$$

where $\lambda$ is an affine parameter. The energy measured by a stationary observer at radius $r$ is proportional to $E/\sqrt{-g_{tt}} = E/\sqrt{1 - 2M/r}$.

The ratio of observed to emitted frequencies:

$$
\frac{\nu_2}{\nu_1} = \frac{\sqrt{1 - 2M/r_1}}{\sqrt{1 - 2M/r_2}}
$$

The gravitational redshift is:

$$
\boxed{z = \frac{\nu_1 - \nu_2}{\nu_2} = \sqrt{\frac{1 - 2M/r_1}{1 - 2M/r_2}} - 1}
$$

For weak fields ($r \gg 2M$), this becomes:

$$
z \approx \frac{M}{r_1} - \frac{M}{r_2} = \frac{GM}{c^2}\left(\frac{1}{r_1} - \frac{1}{r_2}\right)
$$

**Example:** Photon from Sun's surface to Earth: $z \approx GM_\odot/(c^2 R_\odot) \approx 2 \times 10^{-6}$.

## Historical Note

Karl Schwarzschild derived this solution in 1916, just months after Einstein published his field equations, while serving in the German army during World War I. He died shortly thereafter. The solution was the first exact solution to the Einstein equations and remains one of the most important in general relativity.
