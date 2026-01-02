# Scattering Theory

Scattering experiments probe the structure of matter: Rutherford discovered the nucleus, particle accelerators reveal fundamental particles. This document develops quantum scattering from first principles—partial waves, phase shifts, Born approximation—connecting to [perturbation theory](perturbation-theory.md) and [central forces](../classical-mechanics/central-forces.md). The formalism extends directly to nuclear, particle, and condensed matter physics.

## The Scattering Problem

### Setup

A beam of particles with momentum $\hbar\mathbf{k}$ (energy $E = \hbar^2k^2/2m$) impinges on a target with potential $V(\mathbf{r})$ (localized: $V \to 0$ as $r \to \infty$).

We want: the probability of scattering into solid angle $d\Omega$ at angles $(\theta, \phi)$.

### Asymptotic Wave Function

Far from the target:

```math
\psi(\mathbf{r}) \xrightarrow{r \to \infty} e^{i\mathbf{k}\cdot\mathbf{r}} + f(\theta, \phi)\frac{e^{ikr}}{r}
```

- First term: incident plane wave
- Second term: outgoing spherical wave
- $f(\theta, \phi)$: **scattering amplitude**

### Differential Cross-Section

```math
\boxed{\frac{d\sigma}{d\Omega} = |f(\theta, \phi)|^2}
```

The differential cross-section is the effective area for scattering into angle $(\theta, \phi)$.

### Total Cross-Section

```math
\sigma = \int \frac{d\sigma}{d\Omega} d\Omega = \int |f(\theta, \phi)|^2 d\Omega
```

## Partial Wave Analysis

### Expansion in Angular Momentum

For a central potential $V(r)$, angular momentum is conserved. Expand in spherical waves:

```math
\psi = \sum_{\ell=0}^{\infty} (2\ell+1) i^\ell R_\ell(r) P_\ell(\cos\theta)
```

where $P_\ell$ are [Legendre polynomials](../math-foundations/special-functions.md).

### The Radial Equation

Each partial wave satisfies:

```math
\frac{d^2 u_\ell}{dr^2} + \left[k^2 - \frac{\ell(\ell+1)}{r^2} - \frac{2m}{\hbar^2}V(r)\right]u_\ell = 0
```

where $u_\ell = r R_\ell$.

### Asymptotic Behavior

At large $r$ (where $V = 0$):

```math
u_\ell(r) \xrightarrow{r \to \infty} A_\ell \sin\left(kr - \frac{\ell\pi}{2} + \delta_\ell\right)
```

The **phase shift** $\delta_\ell$ encodes all effects of the potential on the $\ell$-th partial wave.

### Scattering Amplitude

```math
\boxed{f(\theta) = \frac{1}{k}\sum_{\ell=0}^{\infty}(2\ell+1)e^{i\delta_\ell}\sin\delta_\ell \, P_\ell(\cos\theta)}
```

or equivalently:

```math
f(\theta) = \sum_{\ell=0}^{\infty}(2\ell+1)f_\ell P_\ell(\cos\theta)
```

where the **partial wave amplitude**:

```math
f_\ell = \frac{e^{2i\delta_\ell} - 1}{2ik} = \frac{e^{i\delta_\ell}\sin\delta_\ell}{k}
```

### Total Cross-Section

```math
\boxed{\sigma = \frac{4\pi}{k^2}\sum_{\ell=0}^{\infty}(2\ell+1)\sin^2\delta_\ell}
```

### The Optical Theorem

```math
\boxed{\sigma = \frac{4\pi}{k}\text{Im}[f(0)]}
```

**What this means:** The total cross-section equals the imaginary part of the forward scattering amplitude. This connects elastic scattering to total absorption and is exact.

## Phase Shift Analysis

### Low-Energy Scattering

At low energies ($ka \ll 1$ where $a$ is the potential range), only $\ell = 0$ (s-wave) contributes significantly:

```math
f \approx f_0 = \frac{e^{i\delta_0}\sin\delta_0}{k} \approx -a_s
```

where $a_s$ is the **scattering length**.

```math
\sigma \approx 4\pi a_s^2
```

### Hard Sphere Scattering

For a hard sphere of radius $a$:

```math
\tan\delta_\ell = \frac{j_\ell(ka)}{n_\ell(ka)}
```

At low energy: $\delta_0 \approx -ka$, so $a_s = a$.

### Resonance Scattering

Near a resonance (quasi-bound state), the phase shift passes through $\pi/2$:

```math
\delta_\ell(E) = \arctan\left(\frac{\Gamma/2}{E_r - E}\right)
```

where $E_r$ is the resonance energy and $\Gamma$ is the width.

**Breit-Wigner formula:**
```math
\sigma_\ell = \frac{4\pi(2\ell+1)}{k^2}\frac{(\Gamma/2)^2}{(E - E_r)^2 + (\Gamma/2)^2}
```

### Levinson's Theorem

The total phase shift at zero energy is related to the number of bound states $n$:

```math
\delta(0) = n\pi
```

## The Born Approximation

### First Born Approximation

For weak potentials (perturbative scattering):

```math
\boxed{f(\mathbf{q}) = -\frac{m}{2\pi\hbar^2}\int V(\mathbf{r}')e^{-i\mathbf{q}\cdot\mathbf{r}'}d^3r'}
```

where $\mathbf{q} = \mathbf{k}_f - \mathbf{k}_i$ is the momentum transfer.

**What this means:** The scattering amplitude is proportional to the Fourier transform of the potential.

### Momentum Transfer

For elastic scattering ($|k_f| = |k_i| = k$):

```math
q = 2k\sin(\theta/2)
```

### Example: Yukawa Potential

```math
V(r) = V_0 \frac{e^{-\mu r}}{r}
```

Born approximation:

```math
f(\theta) = -\frac{2mV_0}{\hbar^2(q^2 + \mu^2)}
```

```math
\frac{d\sigma}{d\Omega} = \left(\frac{2mV_0}{\hbar^2}\right)^2 \frac{1}{(q^2 + \mu^2)^2}
```

### Example: Coulomb Scattering

The Born approximation for Coulomb ($V = Ze^2/4\pi\epsilon_0 r$) gives the **Rutherford formula**:

```math
\boxed{\frac{d\sigma}{d\Omega} = \left(\frac{Ze^2}{16\pi\epsilon_0 E}\right)^2 \frac{1}{\sin^4(\theta/2)}}
```

Remarkably, this Born approximation result is exact for Coulomb.

### Validity of Born Approximation

Valid when the potential is weak:

```math
\left|\frac{mV_0}{\hbar^2 k}\right| \ll 1
```

or when energy is high enough that the particle "barely feels" the potential.

## The Lippmann-Schwinger Equation

### Integral Equation for Scattering

The full scattering state satisfies:

```math
|\psi\rangle = |\phi\rangle + \hat{G}_0(E) \hat{V} |\psi\rangle
```

where:
- $|\phi\rangle$ is the incident plane wave
- $\hat{G}_0(E) = (E - \hat{H}_0 + i\epsilon)^{-1}$ is the free Green's operator

### Born Series

Iterating:

```math
|\psi\rangle = |\phi\rangle + \hat{G}_0\hat{V}|\phi\rangle + \hat{G}_0\hat{V}\hat{G}_0\hat{V}|\phi\rangle + \cdots
```

First Born: keep only first correction.
Second Born: include second term, etc.

### The T-Matrix

Define the **transition matrix**:

```math
\hat{T} = \hat{V} + \hat{V}\hat{G}_0\hat{T}
```

Then:

```math
f = -\frac{m}{2\pi\hbar^2}\langle\mathbf{k}_f|\hat{T}|\mathbf{k}_i\rangle
```

## Identical Particles

### Symmetry Requirements

For identical bosons: $f(\theta) \to f(\theta) + f(\pi - \theta)$

For identical fermions: $f(\theta) \to f(\theta) - f(\pi - \theta)$

### Cross-Section Modifications

**Bosons:**
```math
\frac{d\sigma}{d\Omega} = |f(\theta) + f(\pi-\theta)|^2
```

**Fermions:**
```math
\frac{d\sigma}{d\Omega} = |f(\theta) - f(\pi-\theta)|^2
```

At $\theta = 90°$: bosons show enhancement, fermions show suppression.

## The S-Matrix

### Definition

The **scattering matrix** relates incoming to outgoing states:

```math
|\text{out}\rangle = \hat{S}|\text{in}\rangle
```

For a single partial wave:

```math
S_\ell = e^{2i\delta_\ell}
```

### Properties

**Unitarity:** $\hat{S}^\dagger\hat{S} = \hat{I}$ (probability conservation)

For single channel: $|S_\ell| = 1$

**Time-reversal:** $S_{fi} = S_{if}$

### Analytic Structure

$S(E)$ as a function of complex energy:
- Bound states: poles on negative real axis
- Resonances: poles in lower half-plane
- Branch cuts from thresholds

## Summary

| Quantity | Formula | Physical Meaning |
|----------|---------|------------------|
| Scattering amplitude | $f(\theta)$ | Amplitude of scattered wave |
| Differential cross-section | $d\sigma/d\Omega = |f|^2$ | Angular distribution |
| Phase shift | $\delta_\ell$ | Potential effect on partial wave |
| S-matrix | $S_\ell = e^{2i\delta_\ell}$ | In/out state relation |
| T-matrix | $\hat{T} = \hat{V} + \hat{V}\hat{G}_0\hat{T}$ | Full scattering amplitude |

| Approximation | Valid When | Key Result |
|---------------|------------|------------|
| Low-energy (s-wave) | $ka \ll 1$ | $\sigma = 4\pi a_s^2$ |
| Born | Weak $V$ or high $E$ | $f \propto \tilde{V}(\mathbf{q})$ (Fourier transform) |
| Partial waves | Central $V$ | Expand in $\delta_\ell$, $P_\ell(\cos\theta)$ |

| Result | Formula |
|--------|---------|
| Optical theorem | $\sigma = \frac{4\pi}{k}\text{Im}[f(0)]$ |
| Breit-Wigner | $\sigma \propto \frac{1}{(E-E_r)^2 + \Gamma^2/4}$ |
| Levinson | $\delta(0) = n\pi$ (n = # bound states) |

**The essential insight:** Scattering experiments probe the potential through the phase shifts—how much each partial wave is delayed by interaction with the target. At low energies, only s-waves matter (scattering length). At high energies or weak potentials, Born approximation gives the scattering amplitude as the Fourier transform of the potential. Resonances appear as rapid phase changes. The optical theorem connects forward scattering to total cross-section. These concepts extend to particle physics, where the "potential" becomes the exchange of force-carrying particles in [quantum field theory](qft-introduction.md).
