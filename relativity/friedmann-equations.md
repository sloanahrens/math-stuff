# The Friedmann Equations

The Friedmann equations govern the expansion of the universe. They emerge from Einstein's field equations applied to a homogeneous, isotropic universe and describe everything from the Big Bang to the accelerating expansion we observe today. This document builds on [tensor calculus](../math-foundations/tensor-calculus.md) and [special relativity](special-relativity.md), connecting to [black hole thermodynamics](black-hole-thermodynamics.md) through horizons.

## The Cosmological Principle

### Assumptions

Modern cosmology rests on two assumptions:

1. **Homogeneity:** The universe looks the same at every point (on large scales)
2. **Isotropy:** The universe looks the same in every direction

Together, these form the **cosmological principle**.

**What this means:** There's no special place or direction in the universe. While locally we see galaxies, clusters, and voids, on scales $\gtrsim 100$ Mpc, the universe is remarkably uniform.

## The FLRW Metric

### The Line Element

The most general metric satisfying the cosmological principle is the **Friedmann-Lemaître-Robertson-Walker (FLRW) metric**:

```math
\boxed{ds^2 = -c^2dt^2 + a(t)^2\left[\frac{dr^2}{1 - kr^2} + r^2(d\theta^2 + \sin^2\theta \, d\phi^2)\right]}
```

where:
- $a(t)$ is the **scale factor** (dimensionless, normalized so $a(t_0) = 1$ today)
- $k$ is the **curvature parameter**: $k = +1, 0, -1$ for closed, flat, open universes
- $(r, \theta, \phi)$ are **comoving coordinates**

In [natural units](../math-foundations/natural-units.md) with $c = 1$:

```math
ds^2 = -dt^2 + a(t)^2\left[\frac{dr^2}{1 - kr^2} + r^2 d\Omega^2\right]
```

**What this means:** The scale factor $a(t)$ tells us how the universe stretches over time. Comoving coordinates expand with the universe—galaxies at fixed comoving positions move apart as $a$ increases.

### Alternative Curvature Form

Often written with curvature radius $R_0$:

```math
ds^2 = -dt^2 + a(t)^2\left[\frac{dr^2}{1 - r^2/R_0^2} + r^2 d\Omega^2\right]
```

or in terms of conformal time $\eta$ with $dt = a \, d\eta$:

```math
ds^2 = a(\eta)^2\left[-d\eta^2 + d\chi^2 + S_k^2(\chi) d\Omega^2\right]
```

where $S_k(\chi) = \sin\chi, \chi, \sinh\chi$ for $k = +1, 0, -1$.

## The Friedmann Equations

### Derivation from Einstein's Equations

Applying Einstein's field equations $G_{\mu\nu} + \Lambda g_{\mu\nu} = 8\pi G T_{\mu\nu}$ to the FLRW metric with a perfect fluid:

```math
T_{\mu\nu} = (\rho + P/c^2)u_\mu u_\nu + P g_{\mu\nu}
```

yields the Friedmann equations.

### First Friedmann Equation

```math
\boxed{\left(\frac{\dot{a}}{a}\right)^2 = \frac{8\pi G}{3}\rho - \frac{kc^2}{a^2} + \frac{\Lambda c^2}{3}}
```

In natural units ($G = c = 1$):

```math
H^2 = \frac{8\pi}{3}\rho - \frac{k}{a^2} + \frac{\Lambda}{3}
```

where $H = \dot{a}/a$ is the **Hubble parameter**.

**What this means:** This is energy conservation for the universe. Matter/energy density $\rho$ drives expansion; curvature $k$ and cosmological constant $\Lambda$ modify it.

### Second Friedmann Equation (Acceleration Equation)

```math
\boxed{\frac{\ddot{a}}{a} = -\frac{4\pi G}{3}\left(\rho + \frac{3P}{c^2}\right) + \frac{\Lambda c^2}{3}}
```

In natural units:

```math
\frac{\ddot{a}}{a} = -\frac{4\pi}{3}(\rho + 3P) + \frac{\Lambda}{3}
```

**What this means:** Ordinary matter ($\rho > 0, P \geq 0$) decelerates expansion. The cosmological constant ($\Lambda > 0$) accelerates it. The observation that $\ddot{a} > 0$ today was the discovery of dark energy.

### Fluid Equation

Energy conservation $\nabla_\mu T^{\mu\nu} = 0$ gives:

```math
\boxed{\dot{\rho} + 3H\left(\rho + \frac{P}{c^2}\right) = 0}
```

**What this means:** As the universe expands, energy density decreases. The rate depends on the equation of state—matter dilutes as $a^{-3}$ (volume), radiation as $a^{-4}$ (volume plus redshift).

## The Hubble Parameter

### Definition

```math
H(t) = \frac{\dot{a}}{a}
```

Present value: $H_0 \approx 70$ km/s/Mpc $\approx (14 \text{ billion years})^{-1}$.

### Hubble's Law

For nearby galaxies:

```math
v = H_0 d
```

**What this means:** Galaxies recede with velocity proportional to distance. This was the first evidence for cosmic expansion (Hubble, 1929).

### Hubble Time and Distance

**Hubble time:** $t_H = 1/H_0 \approx 14$ Gyr (rough estimate of cosmic age)

**Hubble distance:** $d_H = c/H_0 \approx 4.4$ Gpc (horizon scale)

## Density Parameters

### Critical Density

The density that makes the universe spatially flat ($k = 0$):

```math
\rho_c = \frac{3H^2}{8\pi G} \approx 9.5 \times 10^{-27} \text{ kg/m}^3
```

**What this means:** About 5 hydrogen atoms per cubic meter. The universe is remarkably dilute.

### Density Parameters

Define dimensionless ratios:

```math
\Omega_m = \frac{\rho_m}{\rho_c}, \quad \Omega_r = \frac{\rho_r}{\rho_c}, \quad \Omega_\Lambda = \frac{\Lambda c^2}{3H^2}, \quad \Omega_k = -\frac{kc^2}{a^2H^2}
```

The first Friedmann equation becomes:

```math
\boxed{\Omega_m + \Omega_r + \Omega_\Lambda + \Omega_k = 1}
```

### Measured Values (Today)

| Component | $\Omega$ | Meaning |
|-----------|----------|---------|
| Matter | 0.31 | Baryonic + dark matter |
| Radiation | $\sim 10^{-4}$ | Photons + neutrinos |
| Dark energy | 0.69 | Cosmological constant |
| Curvature | $\sim 0$ | Spatially flat |

**What this means:** The universe is dominated by dark energy (69%) and dark matter (26%). Ordinary atoms are only 5%. Radiation is negligible now but dominated early.

## Equations of State

### Perfect Fluid

```math
P = w\rho c^2
```

| Component | $w$ | $\rho \propto$ | Physical Reason |
|-----------|-----|----------------|-----------------|
| Matter (dust) | 0 | $a^{-3}$ | Dilution only |
| Radiation | 1/3 | $a^{-4}$ | Dilution + redshift |
| Cosmological constant | $-1$ | const | Vacuum energy |
| Curvature | $-1/3$ | $a^{-2}$ | (effective) |

### Matter-Dominated Era

For $P \approx 0$:

```math
a(t) \propto t^{2/3}, \quad H = \frac{2}{3t}
```

### Radiation-Dominated Era

For $P = \rho c^2/3$:

```math
a(t) \propto t^{1/2}, \quad H = \frac{1}{2t}
```

### Dark Energy-Dominated Era

For $P = -\rho c^2$ (cosmological constant):

```math
a(t) \propto e^{Ht}, \quad H = \text{const} = \sqrt{\Lambda/3}
```

**What this means:** The universe's expansion rate depends on what dominates. Early: radiation (decelerating). Middle: matter (decelerating slower). Late: dark energy (accelerating).

## Cosmological History

### Timeline

| Era | Time | Dominant | $a \propto$ |
|-----|------|----------|-------------|
| Planck | $< 10^{-43}$ s | Unknown | ? |
| Inflation | $10^{-43}$ - $10^{-32}$ s | Inflaton field | $e^{Ht}$ |
| Radiation | $10^{-32}$ s - 47,000 yr | Photons, neutrinos | $t^{1/2}$ |
| Matter | 47,000 yr - 9.8 Gyr | Dark + baryonic matter | $t^{2/3}$ |
| Dark energy | 9.8 Gyr - now | Cosmological constant | $e^{Ht}$ |

### Key Events

| Event | Time | Redshift $z$ | Temperature |
|-------|------|--------------|-------------|
| Big Bang | 0 | $\infty$ | $\infty$ |
| Nucleosynthesis | 3 min | $\sim 10^9$ | $10^9$ K |
| Matter-radiation equality | 47,000 yr | 3400 | 9500 K |
| Recombination (CMB) | 380,000 yr | 1100 | 3000 K |
| First stars | 100-400 Myr | 10-20 | — |
| Today | 13.8 Gyr | 0 | 2.7 K |

## Redshift

### Cosmological Redshift

Light emitted with wavelength $\lambda_e$ is observed with:

```math
\boxed{1 + z = \frac{\lambda_o}{\lambda_e} = \frac{a(t_o)}{a(t_e)} = \frac{1}{a(t_e)}}
```

**What this means:** Photons stretch with the universe. The CMB was emitted when the universe was 1/1100 its current size, so $z = 1100$.

### Redshift-Distance Relations

For small $z$:

```math
z \approx \frac{H_0 d}{c}
```

For larger $z$, the relationship depends on cosmological parameters and requires integration.

## Horizons

### Particle Horizon

The maximum distance light could have traveled since the Big Bang:

```math
d_p(t) = a(t) \int_0^t \frac{c \, dt'}{a(t')}
```

**What this means:** We can only see objects within our particle horizon. The observable universe has a finite size, even if the universe is infinite.

### Event Horizon

The maximum distance light emitted now can ever reach:

```math
d_e(t) = a(t) \int_t^\infty \frac{c \, dt'}{a(t')}
```

In a dark-energy-dominated universe, this is finite—there are galaxies we will never receive signals from.

### Hubble Horizon

```math
d_H = \frac{c}{H}
```

Objects beyond $d_H$ recede faster than light (in coordinate terms—this doesn't violate relativity).

## The Cosmological Constant

### Einstein's Blunder?

Einstein introduced $\Lambda$ to allow a static universe. After expansion was discovered, he called it his "biggest blunder." But in 1998, $\Lambda$ returned.

### Dark Energy

The accelerating expansion requires something with $w < -1/3$. The simplest option is $\Lambda$ with $w = -1$.

**Problems:**
- **Fine-tuning:** $\rho_\Lambda \approx 10^{-120}$ in Planck units—why so small?
- **Coincidence:** Why is $\Omega_\Lambda \sim \Omega_m$ today, when they scale differently?

### Alternatives

Other dark energy models:
- Quintessence: scalar field with $-1 < w < -1/3$
- Phantom energy: $w < -1$ (leads to "Big Rip")
- Modified gravity: $f(R)$ theories, etc.

## The Big Bang

### Not an Explosion

The Big Bang is not an explosion in space—it's the expansion of space itself. There's no center; every point expands away from every other point.

### Initial Singularity

Running the Friedmann equations backward: as $a \to 0$, $\rho \to \infty$, $T \to \infty$. This is the **Big Bang singularity**.

**What this means:** Classical GR predicts its own breakdown. Near the singularity, quantum gravity effects (unknown) become important.

### Inflation

A period of exponential expansion ($a \propto e^{Ht}$) in the early universe solves:
- **Horizon problem:** Why is the CMB so uniform?
- **Flatness problem:** Why is $\Omega \approx 1$?
- **Monopole problem:** Where are the topological defects?

Inflation stretches a tiny causally-connected region to cosmic scales.

## Solutions for Specific Cases

### Flat, Matter-Dominated (Einstein-de Sitter)

```math
a(t) = \left(\frac{t}{t_0}\right)^{2/3}, \quad t_0 = \frac{2}{3H_0}
```

### Flat, $\Lambda$-Dominated (de Sitter)

```math
a(t) = e^{H(t-t_0)}, \quad H = \sqrt{\Lambda/3}
```

### Flat, Matter + $\Lambda$ (ΛCDM)

```math
H(a) = H_0\sqrt{\Omega_m a^{-3} + \Omega_\Lambda}
```

The integral for $t(a)$ or $a(t)$ requires elliptic functions.

### Empty Universe (Milne)

For $\Omega = 0$:

```math
a(t) = H_0 t
```

(This is actually flat Minkowski space in unusual coordinates.)

## Observational Tests

### CMB

The cosmic microwave background:
- Confirms Big Bang (thermal spectrum at 2.725 K)
- Measures cosmological parameters from anisotropies
- Shows flatness ($\Omega_k \approx 0$) from acoustic peak positions

### Type Ia Supernovae

Standard candles that measure luminosity distance vs. redshift:
- Discovered acceleration (1998)
- Measures $\Omega_\Lambda$

### Baryon Acoustic Oscillations

Sound waves in the early universe leave imprints:
- Standard ruler (150 Mpc)
- Measures $H(z)$ and angular diameter distance

### Big Bang Nucleosynthesis

Light element abundances (H, He, Li):
- Confirms hot, dense early universe
- Measures baryon density $\Omega_b$

## Summary

| Equation | Formula | Meaning |
|----------|---------|---------|
| Friedmann I | $H^2 = \frac{8\pi G}{3}\rho - \frac{k}{a^2} + \frac{\Lambda}{3}$ | Expansion rate |
| Friedmann II | $\frac{\ddot{a}}{a} = -\frac{4\pi G}{3}(\rho + 3P) + \frac{\Lambda}{3}$ | Acceleration |
| Fluid | $\dot{\rho} + 3H(\rho + P) = 0$ | Energy conservation |
| Closure | $\Omega_m + \Omega_r + \Omega_\Lambda + \Omega_k = 1$ | Density constraint |

| Era | Dominant | $a(t)$ | $H$ |
|-----|----------|--------|-----|
| Radiation | Photons | $t^{1/2}$ | $1/(2t)$ |
| Matter | Dust | $t^{2/3}$ | $2/(3t)$ |
| $\Lambda$ | Dark energy | $e^{Ht}$ | const |

**The essential insight:** The Friedmann equations describe a universe that began hot and dense, expanded and cooled, and is now accelerating due to dark energy. The ΛCDM model—with cold dark matter and cosmological constant—fits observations remarkably well, despite leaving 95% of the universe's content unexplained.
