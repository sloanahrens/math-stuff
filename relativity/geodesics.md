# Geodesics and Motion in Curved Spacetime

Geodesics are the "straightest possible paths" in curved spacetime—the trajectories followed by freely falling objects. This document extends the [Schwarzschild](schwarzschild-solution.md) and [Kerr](kerr-metric.md) solutions to describe orbital motion, light bending, and other relativistic phenomena. It requires [calculus](../math-foundations/calculus-primer.md) (differential equations), builds on [tensor calculus](../math-foundations/tensor-calculus.md), and uses [natural units](../math-foundations/natural-units.md) where $G = c = 1$.

## What Is a Geodesic?

In flat space, the shortest path between two points is a straight line. In curved spacetime, the analog is a **geodesic**—a path that extremizes the spacetime interval.

```math
\delta \int ds = 0
```

**What this means:** Free-falling objects (no forces except gravity) follow geodesics. Gravity isn't a force in general relativity—it's the curvature of spacetime, and objects simply follow the straightest available paths.

## The Geodesic Equation

### Derivation

The geodesic equation can be derived from the Euler-Lagrange equations (see [Lagrangian mechanics](../classical-mechanics/lagrangian-mechanics.md)) with the Lagrangian:

```math
\mathcal{L} = g_{\mu\nu} \frac{dx^\mu}{d\lambda} \frac{dx^\nu}{d\lambda}
```

This gives:

```math
\boxed{\frac{d^2 x^\mu}{d\tau^2} + \Gamma^\mu_{\alpha\beta} \frac{dx^\alpha}{d\tau} \frac{dx^\beta}{d\tau} = 0}
```

where $\tau$ is proper time and $\Gamma^\mu_{\alpha\beta}$ are the Christoffel symbols.

**What this means:** This is the relativistic generalization of $\mathbf{F} = m\mathbf{a}$. The Christoffel symbols encode how the coordinate basis vectors change from point to point, causing what looks like acceleration in coordinates but is actually straight motion in curved spacetime.

### Alternative Form

Using the 4-velocity $U^\mu = dx^\mu/d\tau$:

```math
U^\nu \nabla_\nu U^\mu = 0
```

**What this means:** The 4-velocity is parallel-transported along itself. The object's "direction" in spacetime doesn't change—it's the straightest possible motion.

## Types of Geodesics

| Type | Condition | Physical Meaning |
|------|-----------|------------------|
| Timelike | $ds^2 < 0$ | Massive particles |
| Null (lightlike) | $ds^2 = 0$ | Light rays (photons) |
| Spacelike | $ds^2 > 0$ | Not physical trajectories |

For null geodesics, proper time $\tau$ is not defined, so we use an **affine parameter** $\lambda$.

## Geodesics in Schwarzschild Spacetime

### The Metric

```math
ds^2 = -\left(1 - \frac{2M}{r}\right)dt^2 + \left(1 - \frac{2M}{r}\right)^{-1}dr^2 + r^2(d\theta^2 + \sin^2\theta \, d\phi^2)
```

### Conserved Quantities

Due to the time translation and rotational symmetries (Killing vectors), there are conserved quantities:

**Energy per unit mass:**

```math
E = \left(1 - \frac{2M}{r}\right)\frac{dt}{d\tau}
```

**Angular momentum per unit mass:**

```math
L = r^2 \frac{d\phi}{d\tau}
```

**What this means:** Just as in Newtonian mechanics, symmetries imply conservation laws. An orbiting particle conserves energy and angular momentum, constrained to a plane (we can choose $\theta = \pi/2$).

### The Effective Potential

For motion in the equatorial plane ($\theta = \pi/2$), the radial equation becomes:

```math
\frac{1}{2}\left(\frac{dr}{d\tau}\right)^2 + V_{\text{eff}}(r) = \frac{1}{2}(E^2 - 1)
```

where the **effective potential** is:

```math
\boxed{V_{\text{eff}}(r) = -\frac{M}{r} + \frac{L^2}{2r^2} - \frac{ML^2}{r^3}}
```

**What this means:** The first term is Newtonian gravity. The second is the centrifugal barrier. The third—the **relativistic correction**—is unique to GR and causes perihelion precession.

### Comparison with Newtonian Potential

| Feature | Newtonian | Relativistic |
|---------|-----------|--------------|
| Potential | $-M/r + L^2/(2r^2)$ | $-M/r + L^2/(2r^2) - ML^2/r^3$ |
| ISCO | None (any orbit stable) | $r = 6M$ |
| Precession | None | Yes |

## Circular Orbits

### Conditions

For circular orbits, $dr/d\tau = 0$ and $d^2r/d\tau^2 = 0$:

```math
\frac{dV_{\text{eff}}}{dr} = 0
```

This gives the orbital angular momentum:

```math
L^2 = \frac{Mr^2}{r - 3M}
```

### Orbital Velocity

The coordinate angular velocity:

```math
\Omega = \frac{d\phi}{dt} = \sqrt{\frac{M}{r^3}}
```

**What this means:** This is the same as Kepler's third law! The coordinate angular velocity matches the Newtonian prediction, though proper times differ.

### Innermost Stable Circular Orbit (ISCO)

The stability condition $d^2V_{\text{eff}}/dr^2 < 0$ fails at:

```math
\boxed{r_{\text{ISCO}} = 6M}
```

**What this means:** Inside $r = 6M$, no stable circular orbits exist. Matter spiraling into a black hole plunges inward from the ISCO, releasing energy as it falls. This is crucial for accretion disk physics.

For the Schwarzschild radius $r_s = 2M$, so ISCO $= 3r_s$.

### Photon Sphere

For light ($L \to \infty$ with fixed impact parameter $b = L/E$), the unstable circular orbit is at:

```math
\boxed{r_{\text{photon}} = 3M}
```

**What this means:** Light can orbit a black hole at $r = 3M$, but unstably—any perturbation sends it spiraling in or escaping to infinity. This creates the "photon ring" seen in black hole images.

## Perihelion Precession

### The Effect

In Newtonian gravity, bound orbits are closed ellipses. In GR, the ellipse precesses:

```math
\boxed{\Delta\phi = \frac{6\pi M}{a(1-e^2)}}
```

per orbit, where $a$ is the semi-major axis and $e$ is the eccentricity.

**What this means:** The orbit traces a rosette pattern instead of a closed ellipse. For Mercury, this gives 43 arcseconds per century—matching the observed anomaly that Newtonian gravity couldn't explain.

### Mercury's Precession

| Contribution | Arcseconds/century |
|--------------|-------------------|
| Other planets | 531 |
| Sun's oblateness | 0.03 |
| General relativity | 43 |
| **Total predicted** | **574** |
| **Observed** | **574** |

This was one of the first confirmations of general relativity.

## Light Deflection

### Null Geodesics

For light, the effective "potential" becomes:

```math
\left(\frac{dr}{d\lambda}\right)^2 = E^2 - \left(1 - \frac{2M}{r}\right)\frac{L^2}{r^2}
```

### Deflection Angle

For light passing at closest approach $r_0$ from a mass $M$:

```math
\boxed{\Delta\phi = \frac{4M}{r_0}}
```

**What this means:** Light bends toward massive objects. For light grazing the Sun, $\Delta\phi \approx 1.75$ arcseconds. This was confirmed in the 1919 eclipse expedition that made Einstein famous.

### Gravitational Lensing

Strong gravitational fields can create multiple images of background sources, arc-like distortions, and even complete Einstein rings when source, lens, and observer align perfectly.

## Radial Infall

### From Rest at Infinity

A particle falling from rest at infinity ($E = 1$, $L = 0$):

```math
\frac{dr}{d\tau} = -\sqrt{\frac{2M}{r}}
```

Integrating:

```math
\tau = \frac{2}{3}\sqrt{\frac{r^3}{2M}}
```

**What this means:** The infalling observer reaches the singularity in finite proper time. For a solar-mass black hole, roughly 10 microseconds from the horizon to the singularity.

### Coordinate Time

In Schwarzschild coordinates:

```math
\frac{dr}{dt} = -\left(1 - \frac{2M}{r}\right)\sqrt{\frac{2M}{r}}
```

As $r \to 2M$, $dr/dt \to 0$. The crossing takes infinite coordinate time.

**What this means:** A distant observer never sees anything cross the horizon—objects appear frozen, increasingly redshifted. But the infalling observer crosses in finite proper time. This is a coordinate artifact, not physical.

## Geodesics in Kerr Spacetime

The [Kerr metric](kerr-metric.md) adds complexity due to rotation.

### Additional Conserved Quantity

Besides $E$ and $L_z$ (angular momentum about the spin axis), there's the **Carter constant** $Q$:

```math
Q = p_\theta^2 + \cos^2\theta\left(a^2(m^2 - E^2) + \frac{L_z^2}{\sin^2\theta}\right)
```

**What this means:** The Carter constant is a "hidden" symmetry not obvious from the metric. Its existence makes Kerr geodesics integrable—we can solve them exactly.

### Frame Dragging Effects

In Kerr spacetime:
- Orbits can be prograde or retrograde relative to the black hole spin
- Prograde ISCO is closer to the horizon than retrograde
- The ergosphere allows energy extraction (Penrose process)

### ISCO in Kerr

For prograde orbits around a maximally spinning black hole ($a = M$):

```math
r_{\text{ISCO}} = M \quad \text{(prograde, } a = M \text{)}
```

For retrograde:

```math
r_{\text{ISCO}} = 9M \quad \text{(retrograde, } a = M \text{)}
```

**What this means:** Frame dragging pulls prograde orbits closer, allowing particles to get much nearer to rapidly spinning black holes.

## Gravitational Redshift

A photon emitted at radius $r$ from a Schwarzschild black hole has its frequency shifted:

```math
\frac{\nu_{\infty}}{\nu_{\text{emit}}} = \sqrt{1 - \frac{2M}{r}}
```

**What this means:** Light climbing out of a gravitational well loses energy (redshifts). At the horizon ($r = 2M$), the redshift becomes infinite—no photon escapes.

## Shapiro Time Delay

Light passing near a massive object takes longer than in flat space:

```math
\Delta t = 4M\left(1 + \ln\frac{4r_1 r_2}{r_0^2}\right)
```

where $r_1, r_2$ are distances from the mass to the source and observer, and $r_0$ is the closest approach.

**What this means:** Radar signals to planets are delayed when they pass near the Sun. This has been measured with spacecraft, confirming GR to high precision.

## Summary

| Phenomenon | Formula | Meaning |
|------------|---------|---------|
| Geodesic equation | $\ddot{x}^\mu + \Gamma^\mu_{\alpha\beta}\dot{x}^\alpha\dot{x}^\beta = 0$ | Free-fall trajectories |
| Effective potential | $V_{\text{eff}} = -M/r + L^2/(2r^2) - ML^2/r^3$ | Radial motion |
| ISCO | $r = 6M$ (Schwarzschild) | Innermost stable orbit |
| Photon sphere | $r = 3M$ | Unstable light orbits |
| Perihelion precession | $\Delta\phi = 6\pi M/[a(1-e^2)]$ | Orbit rotation per cycle |
| Light deflection | $\Delta\phi = 4M/r_0$ | Bending angle |
| Gravitational redshift | $\nu_\infty/\nu_{\text{emit}} = \sqrt{1-2M/r}$ | Frequency shift |

**The essential insight:** In general relativity, gravity is geometry. Objects follow geodesics—the straightest possible paths through curved spacetime. The Schwarzschild and Kerr solutions allow exact calculations of orbits, light paths, and time delays, all confirming Einstein's theory with extraordinary precision.
