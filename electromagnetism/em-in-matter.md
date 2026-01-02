# Electromagnetic Fields in Matter

When electromagnetic fields enter material media, they induce polarization and magnetization that modify the fields themselves. Understanding this interaction is essential for optics, electronics, and material science. This document builds on [electrostatics](electrostatics.md), [magnetostatics](magnetostatics.md), and [Maxwell's equations](maxwell-equations.md).

## Electric Fields in Dielectrics

### Polarization

When an electric field is applied to a dielectric material, charges shift slightly:
- Electrons displace relative to nuclei (electronic polarization)
- Polar molecules rotate to align (orientational polarization)
- Ions shift in crystals (ionic polarization)

The **polarization** $\mathbf{P}$ is the electric dipole moment per unit volume:

```math
\mathbf{P} = \frac{d\mathbf{p}}{dV}
```

### Bound Charges

Polarization creates effective charges:

**Volume charge density:**
```math
\rho_b = -\nabla \cdot \mathbf{P}
```

**Surface charge density:**
```math
\sigma_b = \mathbf{P} \cdot \hat{\mathbf{n}}
```

**What this means:** Where polarization varies (or at surfaces), there's a net bound charge. These bound charges produce electric fields that partially cancel the applied field inside the material.

### The Displacement Field D

We define the **electric displacement**:

```math
\boxed{\mathbf{D} = \epsilon_0 \mathbf{E} + \mathbf{P}}
```

Gauss's law in terms of free charges only:

```math
\nabla \cdot \mathbf{D} = \rho_f \qquad \oint \mathbf{D} \cdot d\mathbf{A} = Q_{f,\text{enc}}
```

### Linear Dielectrics

For most materials at moderate field strengths:

```math
\mathbf{P} = \epsilon_0 \chi_e \mathbf{E}
```

where $\chi_e$ is the **electric susceptibility**. Then:

```math
\mathbf{D} = \epsilon_0(1 + \chi_e)\mathbf{E} = \epsilon_0 \epsilon_r \mathbf{E} = \epsilon \mathbf{E}
```

| Quantity | Symbol | Meaning |
|----------|--------|---------|
| Susceptibility | $\chi_e$ | Response strength |
| Relative permittivity | $\epsilon_r = 1 + \chi_e$ | Dielectric constant |
| Permittivity | $\epsilon = \epsilon_0 \epsilon_r$ | Total permittivity |

### Typical Dielectric Constants

| Material | $\epsilon_r$ |
|----------|--------------|
| Vacuum | 1 |
| Air | 1.0006 |
| Glass | 4-10 |
| Water | 80 |
| Silicon | 12 |
| Barium titanate | 1000-10000 |

## Magnetic Fields in Materials

### Magnetization

In a magnetic field, atomic magnetic moments align, producing **magnetization**:

```math
\mathbf{M} = \frac{d\mathbf{m}}{dV}
```

### The H Field

The **magnetic field intensity**:

```math
\boxed{\mathbf{H} = \frac{\mathbf{B}}{\mu_0} - \mathbf{M}}
```

Ampere's law for free currents:

```math
\nabla \times \mathbf{H} = \mathbf{J}_f
```

### Linear Magnetic Materials

```math
\mathbf{M} = \chi_m \mathbf{H}
```

```math
\mathbf{B} = \mu_0(1 + \chi_m)\mathbf{H} = \mu_0 \mu_r \mathbf{H} = \mu \mathbf{H}
```

### Types of Magnetic Materials

| Type | $\chi_m$ | Mechanism | Examples |
|------|----------|-----------|----------|
| Diamagnetic | $\sim -10^{-5}$ | Induced opposing moment | Cu, Bi, H₂O |
| Paramagnetic | $\sim 10^{-5}$ | Alignment of permanent moments | Al, Pt, O₂ |
| Ferromagnetic | $10^2 - 10^5$ | Domain alignment | Fe, Co, Ni |
| Antiferromagnetic | $\sim 0$ | Opposing sublattice moments | MnO, Cr |
| Ferrimagnetic | Large | Unequal opposing moments | Ferrites |

## Boundary Conditions

### At a Dielectric Interface

**Normal component of D:**
```math
D_{1\perp} - D_{2\perp} = \sigma_f
```

If no free surface charge: $D_{1\perp} = D_{2\perp}$, so $\epsilon_1 E_{1\perp} = \epsilon_2 E_{2\perp}$.

**Tangential component of E:**
```math
E_{1\parallel} = E_{2\parallel}
```

### At a Magnetic Interface

**Normal component of B:**
```math
B_{1\perp} = B_{2\perp}
```

**Tangential component of H:**
```math
H_{1\parallel} - H_{2\parallel} = K_f
```

If no free surface current: $H_{1\parallel} = H_{2\parallel}$, so $B_{1\parallel}/\mu_1 = B_{2\parallel}/\mu_2$.

## Electromagnetic Waves in Matter

### Wave Equation in Media

In a linear, homogeneous, isotropic medium with no free charges or currents:

```math
\nabla^2 \mathbf{E} = \mu\epsilon \frac{\partial^2 \mathbf{E}}{\partial t^2}
```

The wave speed:

```math
v = \frac{1}{\sqrt{\mu\epsilon}} = \frac{c}{\sqrt{\mu_r \epsilon_r}} = \frac{c}{n}
```

where $n = \sqrt{\mu_r \epsilon_r} \approx \sqrt{\epsilon_r}$ is the **index of refraction** (for non-magnetic materials).

### Reflection and Refraction

At an interface between media with indices $n_1$ and $n_2$:

**Snell's Law:**
```math
\boxed{n_1 \sin\theta_1 = n_2 \sin\theta_2}
```

**Total Internal Reflection:** When $n_1 > n_2$ and $\theta_1 > \theta_c = \arcsin(n_2/n_1)$.

### Fresnel Equations

For the reflected and transmitted wave amplitudes:

**s-polarization (E perpendicular to plane of incidence):**
```math
r_s = \frac{n_1\cos\theta_1 - n_2\cos\theta_2}{n_1\cos\theta_1 + n_2\cos\theta_2}
```

```math
t_s = \frac{2n_1\cos\theta_1}{n_1\cos\theta_1 + n_2\cos\theta_2}
```

**p-polarization (E in plane of incidence):**
```math
r_p = \frac{n_2\cos\theta_1 - n_1\cos\theta_2}{n_2\cos\theta_1 + n_1\cos\theta_2}
```

```math
t_p = \frac{2n_1\cos\theta_1}{n_2\cos\theta_1 + n_1\cos\theta_2}
```

### Brewster's Angle

At the **Brewster angle**, $r_p = 0$ (no p-polarized reflection):

```math
\tan\theta_B = \frac{n_2}{n_1}
```

Light reflected at Brewster's angle is completely s-polarized.

### Reflectance and Transmittance

**Reflectance** (fraction of power reflected):
```math
R = |r|^2
```

**Transmittance** (fraction of power transmitted):
```math
T = \frac{n_2\cos\theta_2}{n_1\cos\theta_1}|t|^2
```

Energy conservation: $R + T = 1$.

**Normal incidence:**
```math
R = \left(\frac{n_1 - n_2}{n_1 + n_2}\right)^2
```

## Dispersion

### Frequency-Dependent Response

In reality, $\epsilon$ and $n$ depend on frequency—this is **dispersion**.

### The Lorentz Model

Model atoms as damped harmonic oscillators driven by the electric field:

```math
m\ddot{x} + m\gamma\dot{x} + m\omega_0^2 x = qE
```

This gives a complex dielectric function:

```math
\epsilon_r(\omega) = 1 + \frac{\omega_p^2}{\omega_0^2 - \omega^2 - i\gamma\omega}
```

where $\omega_p = \sqrt{Nq^2/m\epsilon_0}$ is the plasma frequency.

### Refractive Index

The complex refractive index:

```math
\tilde{n} = n + i\kappa
```

where $n$ is the real refractive index and $\kappa$ is the **extinction coefficient**.

The dielectric function: $\epsilon_r = \tilde{n}^2 = (n + i\kappa)^2$.

### Absorption

A wave propagating in an absorbing medium:

```math
E = E_0 e^{i(kx - \omega t)} e^{-\kappa\omega x/c}
```

The intensity decays as $I \propto e^{-\alpha x}$ where $\alpha = 2\kappa\omega/c$ is the **absorption coefficient**.

### Normal and Anomalous Dispersion

| Region | $dn/d\omega$ | $dn/d\lambda$ | Type |
|--------|--------------|---------------|------|
| Far from resonance | $> 0$ | $< 0$ | Normal |
| Near resonance | $< 0$ | $> 0$ | Anomalous |

**Normal dispersion:** Blue light bends more than red (prism).

**Anomalous dispersion:** Occurs near absorption lines.

### Group Velocity

For a wave packet:

```math
v_g = \frac{d\omega}{dk} = c\left(n + \omega\frac{dn}{d\omega}\right)^{-1}
```

In regions of anomalous dispersion, $v_g$ can exceed $c$—but this doesn't violate causality because information travels at the signal velocity.

## Conducting Media

### Complex Permittivity

For a conductor with conductivity $\sigma$:

```math
\tilde{\epsilon} = \epsilon + i\frac{\sigma}{\omega}
```

The wave equation has solutions that decay into the conductor.

### Skin Depth

The **skin depth** $\delta$ is the distance over which fields decay to $1/e$:

```math
\boxed{\delta = \sqrt{\frac{2}{\omega\mu\sigma}}}
```

For a good conductor ($\sigma \gg \omega\epsilon$):

```math
\delta \approx \sqrt{\frac{2}{\omega\mu\sigma}}
```

### Skin Depth Examples

| Material | $\sigma$ (S/m) | $\delta$ at 60 Hz | $\delta$ at 1 GHz |
|----------|----------------|-------------------|-------------------|
| Copper | $5.8 \times 10^7$ | 8.5 mm | 2.1 μm |
| Aluminum | $3.8 \times 10^7$ | 11 mm | 2.6 μm |
| Seawater | 4 | 33 m | 8 mm |

### Reflection from Conductors

For a perfect conductor, all incident energy is reflected. For real conductors, there's slight penetration (skin effect) and absorption.

## Metamaterials

### Negative Index Materials

If both $\epsilon$ and $\mu$ are negative:

```math
n = -\sqrt{\epsilon_r \mu_r}
```

**Consequences:**
- Phase and group velocity are antiparallel
- Snell's law gives negative refraction
- "Perfect lens" focusing below diffraction limit

### Plasmonics

At metal-dielectric interfaces, surface plasmon polaritons can be excited—electromagnetic waves coupled to electron oscillations, with wavelength shorter than free-space light.

## Summary

| Quantity | Vacuum | Linear Medium |
|----------|--------|---------------|
| $\mathbf{D}$ | $\epsilon_0\mathbf{E}$ | $\epsilon\mathbf{E}$ |
| $\mathbf{H}$ | $\mathbf{B}/\mu_0$ | $\mathbf{B}/\mu$ |
| Wave speed | $c$ | $c/n$ |
| Impedance | $\eta_0 = \sqrt{\mu_0/\epsilon_0}$ | $\eta = \sqrt{\mu/\epsilon}$ |

| Phenomenon | Key Formula | Application |
|------------|-------------|-------------|
| Snell's law | $n_1\sin\theta_1 = n_2\sin\theta_2$ | Lenses, prisms |
| Fresnel equations | $r_s$, $r_p$, $t_s$, $t_p$ | Coatings, polarizers |
| Brewster's angle | $\tan\theta_B = n_2/n_1$ | Polarization by reflection |
| Dispersion | $n(\omega)$ | Prism spectrometers |
| Skin depth | $\delta = \sqrt{2/\omega\mu\sigma}$ | Shielding, waveguides |

**The essential insight:** Matter responds to electromagnetic fields through polarization and magnetization, which modify the fields themselves. This self-consistent interaction determines wave propagation, reflection, refraction, and absorption. The frequency dependence (dispersion) leads to phenomena from rainbows to fiber optic communication. At boundaries, matching conditions on field components determine how waves reflect and transmit—the foundation of all optical and electronic device design.
