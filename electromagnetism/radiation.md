# Electromagnetic Radiation

When charges accelerate, they radiate electromagnetic waves. This document develops the theory of radiation from first principles—retarded potentials, dipole radiation, the Larmor formula—connecting [Maxwell's equations](maxwell-equations.md) to [electromagnetic waves](electromagnetic-waves.md). These ideas extend directly to antenna theory, synchrotron radiation, and ultimately [gravitational waves](../relativity/gravitational-waves.md).

## Retarded Potentials

### The Problem

In electrodynamics, the potentials must account for the finite propagation speed of electromagnetic effects.

### Retarded Time

The field at position $\mathbf{r}$ and time $t$ depends on the source at position $\mathbf{r}'$ at the **retarded time**:

$$
\boxed{t_r = t - \frac{|\mathbf{r} - \mathbf{r}'|}{c}}
$$

This is the time at which a signal traveling at $c$ would need to leave $\mathbf{r}'$ to arrive at $\mathbf{r}$ at time $t$.

### Retarded Potentials

The solutions to the wave equations for potentials (in Lorenz gauge):

$$
\boxed{\phi(\mathbf{r}, t) = \frac{1}{4\pi\epsilon_0}\int\frac{\rho(\mathbf{r}', t_r)}{|\mathbf{r} - \mathbf{r}'|}d^3r'}
$$

$$
\boxed{\mathbf{A}(\mathbf{r}, t) = \frac{\mu_0}{4\pi}\int\frac{\mathbf{J}(\mathbf{r}', t_r)}{|\mathbf{r} - \mathbf{r}'|}d^3r'}
$$

**What this means:** The potentials at $(\mathbf{r}, t)$ depend on what the sources were doing at the retarded time—the time it takes light to travel from source to field point.

## Lienard-Wiechert Potentials

### Point Charge Potentials

For a point charge $q$ moving on trajectory $\mathbf{r}_q(t)$ with velocity $\mathbf{v}(t)$:

$$
\boxed{\phi(\mathbf{r}, t) = \frac{q}{4\pi\epsilon_0}\frac{1}{|\mathbf{R}| - \mathbf{R}\cdot\boldsymbol{\beta}}\bigg|_{t_r}}
$$

$$
\boxed{\mathbf{A}(\mathbf{r}, t) = \frac{\mu_0 q c}{4\pi}\frac{\boldsymbol{\beta}}{|\mathbf{R}| - \mathbf{R}\cdot\boldsymbol{\beta}}\bigg|_{t_r}}
$$

where:
- $\mathbf{R} = \mathbf{r} - \mathbf{r}_q(t_r)$ (vector from retarded position to field point)
- $\boldsymbol{\beta} = \mathbf{v}(t_r)/c$
- Everything is evaluated at the retarded time $t_r$

### The Retarded Time Equation

$t_r$ is defined implicitly by:

$$
c(t - t_r) = |\mathbf{r} - \mathbf{r}_q(t_r)|
$$

This must be solved for each field point.

### Fields from a Moving Charge

$$
\mathbf{E} = \frac{q}{4\pi\epsilon_0}\left[\frac{(1-\beta^2)(\hat{\mathbf{R}} - \boldsymbol{\beta})}{(1 - \hat{\mathbf{R}}\cdot\boldsymbol{\beta})^3 R^2} + \frac{\hat{\mathbf{R}} \times [(\hat{\mathbf{R}} - \boldsymbol{\beta}) \times \dot{\boldsymbol{\beta}}]}{c(1 - \hat{\mathbf{R}}\cdot\boldsymbol{\beta})^3 R}\right]_{t_r}
$$

**First term:** Velocity field—generalizes Coulomb field for moving charge, falls off as $1/R^2$.

**Second term:** Acceleration field—radiation field, falls off as $1/R$, dominates at large distances.

$$
\mathbf{B} = \frac{1}{c}\hat{\mathbf{R}} \times \mathbf{E}
$$

## Electric Dipole Radiation

### Oscillating Electric Dipole

A dipole oscillating as $\mathbf{p}(t) = \mathbf{p}_0 \cos(\omega t)$:

### The Radiation Fields

In the **radiation zone** ($r \gg \lambda$ and $r \gg$ source size):

$$
\boxed{\mathbf{E} = -\frac{\mu_0 c k^2}{4\pi}\frac{(\hat{\mathbf{r}} \times \mathbf{p}) \times \hat{\mathbf{r}}}{r}e^{i(kr-\omega t)}}
$$

$$
\boxed{\mathbf{B} = \frac{1}{c}\hat{\mathbf{r}} \times \mathbf{E}}
$$

where $k = \omega/c$.

**Key features:**
- Fields are perpendicular to $\hat{\mathbf{r}}$ (transverse wave)
- Amplitude falls as $1/r$
- Angular pattern: $|\mathbf{E}| \propto \sin\theta$ (zero along dipole axis)

### Radiation Pattern

The angular distribution of power:

$$
\frac{dP}{d\Omega} = \frac{\mu_0 c k^4 p_0^2}{32\pi^2}\sin^2\theta
$$

This is the famous "donut" pattern—maximum radiation perpendicular to the dipole axis.

### Total Radiated Power

$$
\boxed{P = \frac{\mu_0 c k^4 p_0^2}{12\pi} = \frac{\mu_0 p_0^2 \omega^4}{12\pi c}}
$$

The power scales as $\omega^4$—higher frequencies radiate much more efficiently.

## The Larmor Formula

### Power Radiated by an Accelerating Charge

For a non-relativistic accelerating charge:

$$
\boxed{P = \frac{\mu_0 q^2 a^2}{6\pi c} = \frac{q^2 a^2}{6\pi\epsilon_0 c^3}}
$$

**What this means:** Any accelerating charge radiates. The power depends on the square of acceleration—violent accelerations produce bright radiation.

### Derivation

The acceleration field at angle $\theta$ to the acceleration:

$$
|\mathbf{E}_{\text{rad}}| = \frac{qa\sin\theta}{4\pi\epsilon_0 c^2 r}
$$

The Poynting vector magnitude:

$$
S = \frac{1}{\mu_0 c}|E|^2 = \frac{q^2 a^2 \sin^2\theta}{16\pi^2\epsilon_0 c^3 r^2}
$$

Integrating over a sphere:

$$
P = \int S r^2 d\Omega = \frac{q^2 a^2}{6\pi\epsilon_0 c^3}
$$

### Relativistic Generalization

For a relativistic particle:

$$
P = \frac{\mu_0 q^2 c}{6\pi}\gamma^6\left[(\dot{\boldsymbol{\beta}})^2 - (\boldsymbol{\beta} \times \dot{\boldsymbol{\beta}})^2\right]
$$

**Linear acceleration:** $P \propto \gamma^6$ for given force.

**Circular motion:** $P \propto \gamma^4$ (synchrotron radiation).

## Magnetic Dipole Radiation

### Oscillating Magnetic Dipole

For a magnetic dipole $\mathbf{m}(t) = \mathbf{m}_0\cos(\omega t)$:

The radiation fields have the same structure as electric dipole but with $\mathbf{E}$ and $\mathbf{B}$ roles exchanged.

### Power Radiated

$$
P_m = \frac{\mu_0 m_0^2 \omega^4}{12\pi c^3}
$$

### Comparison

$$
\frac{P_m}{P_e} = \frac{m_0^2}{p_0^2 c^2}
$$

For atomic sources, $m_0 \sim p_0/c$, so magnetic dipole radiation is typically weaker by factor $(v/c)^2$.

## Electric Quadrupole Radiation

### The Quadrupole Moment

$$
Q_{ij} = \int (3r_i r_j - r^2\delta_{ij})\rho \, d^3r
$$

### Power Radiated

$$
P_Q = \frac{\mu_0 c k^6}{180\pi}\sum_{ij}|\ddot{Q}_{ij}|^2
$$

### Comparison with Dipole

$$
\frac{P_Q}{P_d} \sim (ka)^2 = \left(\frac{a}{\lambda}\right)^2
$$

where $a$ is the source size. For sources small compared to wavelength, quadrupole is suppressed.

## Radiation from Antennas

### Half-Wave Dipole

A center-fed antenna of length $L = \lambda/2$:

Current distribution: $I(z) = I_0\cos(kz)$

Radiation resistance: $R_{\text{rad}} \approx 73 \, \Omega$

Power radiated: $P = \frac{1}{2}I_0^2 R_{\text{rad}}$

### Antenna Arrays

Multiple antennas can be phased to create directional radiation patterns. The array factor determines beam shape.

### Antenna Gain

$$
G = \frac{\text{Peak intensity}}{\text{Isotropic intensity}} = \frac{4\pi}{P}\left(\frac{dP}{d\Omega}\right)_{\text{max}}
$$

Half-wave dipole: $G \approx 1.64$ (2.15 dBi).

## Synchrotron Radiation

### Circular Motion

A relativistic charged particle in circular motion radiates with:

$$
P = \frac{\mu_0 q^2 c}{6\pi}\gamma^4\left(\frac{v^2}{R^2}\right)
$$

where $R$ is the orbit radius.

### Characteristic Frequency

The radiation is concentrated in a narrow forward cone of angle $\sim 1/\gamma$.

Critical frequency:

$$
\omega_c = \frac{3\gamma^3 c}{2R}
$$

### Spectrum

The spectrum extends from low frequencies up to $\sim \omega_c$, with a broad peak.

### Applications

- **Synchrotron light sources:** Brilliant X-rays for materials science
- **Astrophysics:** Emission from relativistic jets, pulsars
- **Particle accelerators:** Energy loss mechanism

## Radiation Reaction

### The Abraham-Lorentz Force

A radiating charge experiences a self-force:

$$
\mathbf{F}_{\text{rad}} = \frac{\mu_0 q^2}{6\pi c}\dot{\mathbf{a}}
$$

This is a third-derivative "jerk" term.

### Problems

- Pre-acceleration (effect before cause)
- Runaway solutions

### Resolution

The full theory requires quantum electrodynamics; classical theory breaks down at scales $\sim$ classical electron radius.

## Summary

| Radiation Type | Power | Angular Pattern | Frequency Dependence |
|----------------|-------|-----------------|----------------------|
| Electric dipole | $\propto p^2\omega^4$ | $\sin^2\theta$ | $\omega^4$ |
| Magnetic dipole | $\propto m^2\omega^4$ | $\sin^2\theta$ | $\omega^4$ |
| Electric quadrupole | $\propto Q^2\omega^6$ | More complex | $\omega^6$ |
| Larmor (non-rel) | $\propto q^2 a^2$ | $\sin^2\theta$ | — |
| Synchrotron | $\propto \gamma^4 a^2$ | Forward cone | Broad spectrum |

| Formula | Expression | Application |
|---------|------------|-------------|
| Retarded time | $t_r = t - R/c$ | Causality in radiation |
| Larmor power | $P = \mu_0 q^2 a^2/6\pi c$ | Non-relativistic radiation |
| Dipole power | $P = \mu_0 p_0^2\omega^4/12\pi c$ | Atomic transitions |
| Radiation zone | $E \propto 1/r$, $E \perp \hat{r}$ | Far-field pattern |

**The essential insight:** Accelerating charges radiate—this is the fundamental mechanism behind all electromagnetic radiation from radio waves to gamma rays. The Larmor formula quantifies the power; the angular distribution shows the radiation pattern; the $\omega^4$ frequency dependence explains why the sky is blue (Rayleigh scattering). The mathematical structure—retarded potentials, multipole expansions—extends directly to [gravitational radiation](../relativity/gravitational-waves.md) in general relativity. Understanding radiation is understanding how energy and information propagate through the universe.
