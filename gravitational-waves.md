# Gravitational Waves

Gravitational waves are ripples in spacetime that propagate at the speed of light, predicted by general relativity and directly detected by LIGO in 2015. This document uses [tensor calculus](tensor-calculus.md), [special relativity](special-relativity.md), and [natural units](natural-units.md) with $G = c = 1$.

## Overview

Just as accelerating charges produce electromagnetic waves, accelerating masses produce **gravitational waves**. These are oscillations in the metric tensor $g_{\mu\nu}$ that carry energy away from their source.

**What this means:** Spacetime itself can vibrate. When two black holes merge, they shake spacetime so violently that the ripples are detectable billions of light-years away—though the effect on Earth is incredibly tiny (less than a proton's width).

## Linearized Gravity

### Weak Field Approximation

For weak gravitational fields, write the metric as flat spacetime plus a small perturbation:

$$
g_{\mu\nu} = \eta_{\mu\nu} + h_{\mu\nu}, \qquad |h_{\mu\nu}| \ll 1
$$

where $\eta_{\mu\nu} = \text{diag}(-1, 1, 1, 1)$ is the Minkowski metric.

**What this means:** We're treating gravity as a small deviation from flat spacetime. This linearization is valid far from strong sources like black holes and neutron stars.

### The Trace-Reversed Perturbation

Define the **trace-reversed** perturbation:

$$
\bar{h}_{\mu\nu} = h_{\mu\nu} - \frac{1}{2} \eta_{\mu\nu} h
$$

where $h = \eta^{\mu\nu} h_{\mu\nu}$ is the trace.

**What this means:** This combination simplifies the equations. Note that $\bar{h} = -h$.

### Gauge Freedom

The perturbation $h_{\mu\nu}$ isn't unique—we can make coordinate changes (gauge transformations):

$$
h_{\mu\nu} \to h_{\mu\nu} - \partial_\mu \xi_\nu - \partial_\nu \xi_\mu
$$

We choose the **Lorenz gauge** (also called de Donder or harmonic gauge):

$$
\partial^\mu \bar{h}_{\mu\nu} = 0
$$

**What this means:** Just as in electromagnetism we can choose $\partial_\mu A^\mu = 0$, in gravity we can fix the gauge to simplify the equations. This is the gravitational analog of Lorenz gauge.

## The Wave Equation

In Lorenz gauge, the linearized Einstein equations become:

$$
\boxed{\Box \bar{h}_{\mu\nu} = -16\pi T_{\mu\nu}}
$$

where $\Box = -\partial_t^2 + \nabla^2$ is the d'Alembertian (wave operator).

**What this means:** This is a wave equation! In vacuum ($T_{\mu\nu} = 0$), gravitational perturbations propagate as waves at the speed of light (since $c = 1$ in our units).

### Vacuum Solutions

In vacuum:

$$
\Box \bar{h}_{\mu\nu} = 0
$$

Plane wave solutions:

$$
\bar{h}_{\mu\nu} = A_{\mu\nu} e^{ik_\alpha x^\alpha}
$$

where $k^\mu$ is the wave 4-vector satisfying $k_\mu k^\mu = 0$ (null—waves travel at light speed).

## Transverse-Traceless Gauge

We can further restrict the gauge to **transverse-traceless (TT) gauge**:

$$
h^{TT}_{0\mu} = 0, \qquad h^{TT}_{ii} = 0, \qquad \partial^j h^{TT}_{ij} = 0
$$

**What this means:**
- $h_{0\mu} = 0$: No time components (purely spatial)
- $h_{ii} = 0$: Traceless (no volume change)
- $\partial^j h_{ij} = 0$: Transverse (perpendicular to propagation)

This eliminates all gauge freedom, leaving only the physical degrees of freedom.

## Polarizations

For a wave traveling in the $z$-direction, the TT perturbation has only two independent components:

$$
h^{TT}_{ij} = \begin{pmatrix} h_+ & h_\times & 0 \\ h_\times & -h_+ & 0 \\ 0 & 0 & 0 \end{pmatrix} \cos(\omega t - kz)
$$

### Plus Polarization ($h_+$)

$$
h^+_{ij} = h_+ \begin{pmatrix} 1 & 0 & 0 \\ 0 & -1 & 0 \\ 0 & 0 & 0 \end{pmatrix}
$$

**What this means:** Alternately stretches space in the $x$-direction while compressing in $y$, then vice versa. A circle of test particles becomes an ellipse oscillating between horizontal and vertical orientations.

### Cross Polarization ($h_\times$)

$$
h^\times_{ij} = h_\times \begin{pmatrix} 0 & 1 & 0 \\ 1 & 0 & 0 \\ 0 & 0 & 0 \end{pmatrix}
$$

**What this means:** Same pattern but rotated 45°. A circle becomes an ellipse oscillating along the diagonal directions.

### Helicity

The two polarizations have **helicity** $\pm 2$:

$$
h_R = h_+ + i h_\times, \qquad h_L = h_+ - i h_\times
$$

**What this means:** Gravitational waves are spin-2 (helicity ±2), while electromagnetic waves are spin-1 (helicity ±1). This is why gravitons, if they exist, are spin-2 particles.

## Effect on Test Particles

### Geodesic Deviation

Two nearby freely-falling particles separated by $\xi^i$ experience relative acceleration:

$$
\frac{d^2 \xi^i}{dt^2} = \frac{1}{2} \frac{\partial^2 h^{TT}_{ij}}{\partial t^2} \xi^j
$$

**What this means:** Gravitational waves stretch and squeeze space. The relative distance between test particles oscillates as the wave passes.

### Strain

The **strain** $h$ is the fractional change in distance:

$$
h = \frac{\Delta L}{L}
$$

For LIGO's first detection (GW150914): $h \sim 10^{-21}$.

**What this means:** For LIGO's 4 km arms, this corresponds to a length change of about $4 \times 10^{-18}$ m—smaller than a proton!

## Energy and Momentum

### Gravitational Wave Energy

Gravitational waves carry energy. The **stress-energy pseudotensor** (averaged over wavelengths):

$$
t_{\mu\nu} = \frac{1}{32\pi} \langle \partial_\mu h^{TT}_{ij} \partial_\nu h^{TT}_{ij} \rangle
$$

**What this means:** "Pseudotensor" because it's not gauge-invariant locally—but the total energy radiated is well-defined. This is a subtle point unique to gravity.

### Energy Flux

The energy flux (power per unit area) for a wave traveling in the $z$-direction:

$$
F = \frac{1}{16\pi} \langle \dot{h}_+^2 + \dot{h}_\times^2 \rangle
$$

**What this means:** The energy carried by gravitational waves depends on the square of the time derivative of the strain, just as electromagnetic energy depends on $E^2 + B^2$.

## Gravitational Wave Sources

### Quadrupole Formula

The dominant gravitational wave emission comes from the time-varying **mass quadrupole**:

$$
Q_{ij} = \int \rho \left( x_i x_j - \frac{1}{3} \delta_{ij} r^2 \right) d^3x
$$

The radiated power (in natural units):

$$
\boxed{P = \frac{1}{5} \langle \dddot{Q}_{ij} \dddot{Q}_{ij} \rangle}
$$

**What this means:** You need a changing quadrupole moment to radiate gravitational waves. A spinning symmetric sphere doesn't radiate—but two orbiting masses do.

### Why Quadrupole?

| Multipole | Electromagnetic | Gravitational |
|-----------|-----------------|---------------|
| Monopole | Conserved (charge) | Conserved (mass-energy) |
| Dipole | Radiates | Conserved (momentum) |
| Quadrupole | Radiates | **Radiates** |

**What this means:** Conservation of mass-energy forbids monopole radiation, and conservation of momentum forbids dipole radiation. The leading-order gravitational radiation is quadrupole.

### Binary System

For two masses $m_1, m_2$ in circular orbit with separation $r$ and orbital angular frequency $\omega$:

$$
P = \frac{32}{5} \frac{\mu^2 M^3}{r^5}
$$

where $\mu = m_1 m_2 / M$ is the reduced mass and $M = m_1 + m_2$ is the total mass.

**What this means:** Tighter binaries radiate more powerfully ($\propto r^{-5}$). As energy is lost, the orbit shrinks, radiation increases, and the system spirals inward—the inspiral accelerates dramatically near merger.

### Converting to SI Units

To restore factors of $G$ and $c$ (see [natural units](natural-units.md)):

$$
P = \frac{32}{5} \frac{G^4}{c^5} \frac{\mu^2 M^3}{r^5}
$$

The factor $G^4/c^5 \approx 3.6 \times 10^{-53}$ W·m$^5$/kg$^5$ shows why gravitational waves are so weak.

## Inspiral and Merger

### Chirp Signal

As a binary inspirals, both amplitude and frequency increase—producing a characteristic **chirp**:

$$
f(t) \propto (t_c - t)^{-3/8}
$$

$$
h(t) \propto (t_c - t)^{-1/4}
$$

where $t_c$ is the coalescence time.

**What this means:** The waveform sweeps upward in frequency, getting louder and faster until merger. This distinctive pattern is how LIGO identifies binary mergers.

### Chirp Mass

The combination that determines the waveform during inspiral:

$$
\mathcal{M} = \frac{(m_1 m_2)^{3/5}}{(m_1 + m_2)^{1/5}} = \mu^{3/5} M^{2/5}
$$

**What this means:** The chirp mass is the best-measured parameter from gravitational wave observations. Individual masses $m_1, m_2$ are harder to determine.

### Post-Newtonian Corrections

The simple quadrupole formula breaks down near merger. Corrections are organized as an expansion in $v/c$:

$$
h = h_{\text{Newtonian}} \left( 1 + \text{1PN} + \text{1.5PN} + \text{2PN} + \cdots \right)
$$

where nPN means corrections of order $(v/c)^{2n}$.

**What this means:** Near merger, velocities approach the speed of light and the weak-field approximation fails. Full numerical relativity is needed to model the final plunge and merger.

## Detection: LIGO/Virgo

### Principle

LIGO uses **laser interferometry**:
- Two 4-km perpendicular arms
- Laser bounces between mirrors at arm ends
- Gravitational wave changes relative arm lengths
- Interference pattern shifts

**What this means:** A passing gravitational wave stretches one arm while compressing the other (for $h_+$), changing the interference pattern. By measuring this shift to extreme precision, we detect the wave.

### Sensitivity

| Noise Source | Frequency Range |
|--------------|-----------------|
| Seismic | $< 10$ Hz |
| Thermal | $10 - 100$ Hz |
| Quantum (shot noise) | $> 100$ Hz |

LIGO is most sensitive around 100–300 Hz, matching the frequency of stellar-mass binary mergers.

### First Detection: GW150914

On September 14, 2015, LIGO detected gravitational waves from two merging black holes:

| Parameter | Value |
|-----------|-------|
| Masses | $36 M_\odot + 29 M_\odot$ |
| Final mass | $62 M_\odot$ |
| Energy radiated | $3 M_\odot c^2$ |
| Distance | 1.3 billion light-years |
| Peak strain | $10^{-21}$ |
| Peak frequency | 150 Hz |

**What this means:** About 3 solar masses were converted to gravitational wave energy in a fraction of a second—more power than all the stars in the observable universe combined, briefly.

## Relationship to Other Topics

### Connection to Schwarzschild/Kerr

The [Schwarzschild](schwarzschild-solution.md) and [Kerr](kerr-metric.md) solutions describe *stationary* black holes. Gravitational waves are the *dynamical* aspect—what happens when black holes move, merge, or are perturbed.

### Connection to Tensor Calculus

Gravitational waves are perturbations of the metric tensor $g_{\mu\nu}$. The [tensor calculus](tensor-calculus.md) formalism—covariant derivatives, Christoffel symbols, Riemann curvature—underlies all the calculations.

### Connection to Differential Forms

The energy pseudotensor can be expressed using [differential forms](differential-forms.md), and the gauge structure of linearized gravity parallels gauge theories.

## Summary

| Concept | Expression | Meaning |
|---------|------------|---------|
| Metric perturbation | $g_{\mu\nu} = \eta_{\mu\nu} + h_{\mu\nu}$ | Weak gravity = flat + small correction |
| Wave equation | $\Box \bar{h}_{\mu\nu} = -16\pi T_{\mu\nu}$ | Gravitational waves propagate at $c$ |
| TT gauge | $h_{0\mu} = 0$, $h_{ii} = 0$ | Physical degrees of freedom only |
| Polarizations | $h_+$, $h_\times$ | Two independent wave modes (helicity ±2) |
| Quadrupole radiation | $P = \frac{1}{5} \langle \dddot{Q}_{ij}^2 \rangle$ | Leading-order emission |
| Strain | $h = \Delta L / L$ | Fractional length change |

**The essential insight:** Gravitational waves are ripples in spacetime's geometry, predicted by general relativity and confirmed by direct detection. They open a new window on the universe—letting us observe black hole mergers, neutron star collisions, and potentially the earliest moments after the Big Bang.
