# Electromagnetic Waves

Electromagnetic waves are oscillating electric and magnetic fields that propagate through space at the speed of light. They emerge naturally from [Maxwell's equations](maxwell-equations.md) and include light, radio waves, X-rays, and all other forms of electromagnetic radiation. This document uses [vector calculus](../prerequisites/vector-calculus.md) and connects to [special relativity](../relativity/special-relativity.md).

## The Wave Equation

### Derivation from Maxwell's Equations

In free space (no charges or currents), Maxwell's equations are:

$$
\nabla \cdot \mathbf{E} = 0, \quad \nabla \cdot \mathbf{B} = 0, \quad \nabla \times \mathbf{E} = -\frac{\partial \mathbf{B}}{\partial t}, \quad \nabla \times \mathbf{B} = \mu_0 \epsilon_0 \frac{\partial \mathbf{E}}{\partial t}
$$

Taking the curl of Faraday's law:

$$
\nabla \times (\nabla \times \mathbf{E}) = -\frac{\partial}{\partial t}(\nabla \times \mathbf{B}) = -\mu_0 \epsilon_0 \frac{\partial^2 \mathbf{E}}{\partial t^2}
$$

Using the vector identity $\nabla \times (\nabla \times \mathbf{E}) = \nabla(\nabla \cdot \mathbf{E}) - \nabla^2 \mathbf{E}$ and $\nabla \cdot \mathbf{E} = 0$:

$$
\boxed{\nabla^2 \mathbf{E} = \mu_0 \epsilon_0 \frac{\partial^2 \mathbf{E}}{\partial t^2}}
$$

Similarly for $\mathbf{B}$:

$$
\boxed{\nabla^2 \mathbf{B} = \mu_0 \epsilon_0 \frac{\partial^2 \mathbf{B}}{\partial t^2}}
$$

**What this means:** Both $\mathbf{E}$ and $\mathbf{B}$ satisfy the wave equation with wave speed:

$$
c = \frac{1}{\sqrt{\mu_0 \epsilon_0}} = 3 \times 10^8 \text{ m/s}
$$

This is the speed of light—Maxwell's great discovery.

## Plane Wave Solutions

### The Simplest Solution

A plane wave propagating in the $+z$ direction:

$$
\mathbf{E} = E_0 \cos(kz - \omega t) \, \hat{\mathbf{x}}
$$

$$
\mathbf{B} = B_0 \cos(kz - \omega t) \, \hat{\mathbf{y}}
$$

where:
- $k = 2\pi/\lambda$ is the wave number
- $\omega = 2\pi f$ is the angular frequency
- $\lambda$ is wavelength, $f$ is frequency

### Dispersion Relation

Substituting into the wave equation:

$$
\omega = ck \quad \Leftrightarrow \quad f\lambda = c
$$

**What this means:** All electromagnetic waves in vacuum travel at the same speed $c$, regardless of frequency. There is no dispersion.

### Complex Notation

It's convenient to write:

$$
\mathbf{E} = E_0 \, e^{i(kz - \omega t)} \, \hat{\mathbf{x}}, \qquad \mathbf{B} = B_0 \, e^{i(kz - \omega t)} \, \hat{\mathbf{y}}
$$

with the understanding that physical fields are the real parts.

### General Plane Wave

For propagation in direction $\hat{\mathbf{k}}$:

$$
\mathbf{E} = \mathbf{E}_0 \, e^{i(\mathbf{k} \cdot \mathbf{r} - \omega t)}, \qquad \mathbf{B} = \mathbf{B}_0 \, e^{i(\mathbf{k} \cdot \mathbf{r} - \omega t)}
$$

## Properties of EM Waves

### Transverse Waves

From $\nabla \cdot \mathbf{E} = 0$:
$$
\mathbf{k} \cdot \mathbf{E}_0 = 0
$$

From $\nabla \cdot \mathbf{B} = 0$:
$$
\mathbf{k} \cdot \mathbf{B}_0 = 0
$$

**What this means:** Both $\mathbf{E}$ and $\mathbf{B}$ are perpendicular to the direction of propagation. EM waves are transverse, not longitudinal.

### E and B are Perpendicular

From Faraday's law:
$$
\mathbf{B}_0 = \frac{1}{\omega} \mathbf{k} \times \mathbf{E}_0 = \frac{1}{c} \hat{\mathbf{k}} \times \mathbf{E}_0
$$

**What this means:** $\mathbf{E}$, $\mathbf{B}$, and $\hat{\mathbf{k}}$ form a right-handed orthogonal triad.

### Amplitude Relationship

$$
B_0 = \frac{E_0}{c}
$$

**What this means:** The magnetic field amplitude is smaller than the electric field by a factor of $c$. In SI units, if $E_0 = 1$ V/m, then $B_0 = 3.3 \times 10^{-9}$ T.

## Energy in EM Waves

### Energy Density

$$
u = \frac{1}{2}\epsilon_0 E^2 + \frac{1}{2\mu_0} B^2
$$

For a plane wave with $B = E/c$:

$$
\frac{1}{2\mu_0}B^2 = \frac{1}{2\mu_0}\frac{E^2}{c^2} = \frac{1}{2}\epsilon_0 E^2
$$

**What this means:** Electric and magnetic energy densities are equal in an EM wave.

$$
u = \epsilon_0 E^2 = \frac{B^2}{\mu_0}
$$

### Poynting Vector

The energy flux (power per unit area):

$$
\mathbf{S} = \frac{1}{\mu_0} \mathbf{E} \times \mathbf{B}
$$

For a plane wave:

$$
S = \frac{E_0 B_0}{\mu_0} \cos^2(kz - \omega t) = \frac{E_0^2}{\mu_0 c} \cos^2(kz - \omega t)
$$

### Intensity

The time-averaged power per unit area:

$$
I = \langle S \rangle = \frac{1}{2} \frac{E_0^2}{\mu_0 c} = \frac{1}{2} \epsilon_0 c E_0^2 = \frac{c}{2\mu_0} B_0^2
$$

**What this means:** Intensity is proportional to the square of the amplitude. Doubling the field amplitude quadruples the intensity.

### Radiation Pressure

EM waves carry momentum density $\mathbf{g} = \mathbf{S}/c^2$. When absorbed, they exert pressure:

$$
P_{\text{abs}} = \frac{I}{c}
$$

When perfectly reflected:

$$
P_{\text{ref}} = \frac{2I}{c}
$$

**What this means:** Light exerts pressure. For sunlight ($I \approx 1400$ W/m²), the pressure is about $5 \times 10^{-6}$ Pa—tiny, but measurable and important for spacecraft and dust particles.

## Polarization

### Linear Polarization

The electric field oscillates along a fixed direction:

$$
\mathbf{E} = E_0 \cos(kz - \omega t) \, \hat{\mathbf{x}}
$$

### Circular Polarization

The electric field vector rotates:

$$
\mathbf{E} = E_0 [\cos(kz - \omega t) \, \hat{\mathbf{x}} + \sin(kz - \omega t) \, \hat{\mathbf{y}}]
$$

- **Right circular:** $\mathbf{E}$ rotates clockwise when viewed from the receiver
- **Left circular:** $\mathbf{E}$ rotates counterclockwise

**What this means:** Circular polarization carries angular momentum. Photons have spin $\pm\hbar$ corresponding to left/right circular polarization.

### Elliptical Polarization

The general case—$\mathbf{E}$ traces an ellipse:

$$
\mathbf{E} = E_x \cos(kz - \omega t) \, \hat{\mathbf{x}} + E_y \cos(kz - \omega t + \phi) \, \hat{\mathbf{y}}
$$

Linear and circular are special cases.

## The Electromagnetic Spectrum

| Type | Wavelength | Frequency | Typical Source |
|------|------------|-----------|----------------|
| Radio | > 1 m | < 300 MHz | Antennas, electronics |
| Microwave | 1 mm – 1 m | 300 MHz – 300 GHz | Klystrons, cosmic background |
| Infrared | 700 nm – 1 mm | 300 GHz – 430 THz | Thermal radiation |
| Visible | 400 – 700 nm | 430 – 750 THz | Hot objects, lasers |
| Ultraviolet | 10 – 400 nm | 750 THz – 30 PHz | Sun, discharge lamps |
| X-ray | 0.01 – 10 nm | 30 PHz – 30 EHz | Electron transitions, synchrotrons |
| Gamma ray | < 0.01 nm | > 30 EHz | Nuclear transitions, cosmic |

**What this means:** All these are the same phenomenon—oscillating EM fields—differing only in frequency/wavelength.

## Waves in Matter

### Dielectric Media

In a linear dielectric with permittivity $\epsilon$ and permeability $\mu$:

$$
v = \frac{1}{\sqrt{\mu \epsilon}} = \frac{c}{n}
$$

where $n = \sqrt{\mu_r \epsilon_r}$ is the **refractive index**.

### Dispersion

In real materials, $\epsilon$ (and hence $n$) depends on frequency:

$$
n = n(\omega)
$$

This causes different frequencies to travel at different speeds, spreading pulses.

**Phase velocity:** $v_p = \omega/k = c/n$

**Group velocity:** $v_g = d\omega/dk$ (speed of wave packets)

### Absorption

In conducting media or materials with loss:

$$
\mathbf{E} = \mathbf{E}_0 \, e^{-\alpha z} e^{i(kz - \omega t)}
$$

where $\alpha$ is the absorption coefficient (field decays exponentially).

## Reflection and Refraction

### Snell's Law

At an interface between media with indices $n_1$ and $n_2$:

$$
n_1 \sin\theta_1 = n_2 \sin\theta_2
$$

### Fresnel Equations

For incidence from medium 1 to 2:

**s-polarization** (E perpendicular to plane of incidence):
$$
r_s = \frac{n_1 \cos\theta_1 - n_2 \cos\theta_2}{n_1 \cos\theta_1 + n_2 \cos\theta_2}
$$

**p-polarization** (E in plane of incidence):
$$
r_p = \frac{n_2 \cos\theta_1 - n_1 \cos\theta_2}{n_2 \cos\theta_1 + n_1 \cos\theta_2}
$$

### Brewster's Angle

At this angle, $r_p = 0$ (no p-polarized reflection):

$$
\tan\theta_B = \frac{n_2}{n_1}
$$

### Total Internal Reflection

When $n_1 > n_2$ and $\theta_1 > \theta_c$:

$$
\sin\theta_c = \frac{n_2}{n_1}
$$

All light is reflected—basis of fiber optics.

## Connection to Photons

In [quantum mechanics](../quantum-mechanics/quantum-mechanics.md), electromagnetic waves are quantized into photons with:

- Energy: $E = \hbar\omega = hf$
- Momentum: $p = \hbar k = h/\lambda$
- Spin: $\pm\hbar$ (circular polarization states)

**What this means:** The wave and particle descriptions are complementary. Intensity determines the probability of finding photons; polarization determines their spin states.

## Summary

| Property | Formula | Meaning |
|----------|---------|---------|
| Wave speed | $c = 1/\sqrt{\mu_0\epsilon_0}$ | All EM waves travel at light speed in vacuum |
| Dispersion relation | $\omega = ck$ | No dispersion in vacuum |
| Transverse | $\mathbf{E} \perp \mathbf{k}$, $\mathbf{B} \perp \mathbf{k}$ | Fields perpendicular to propagation |
| E-B relation | $B_0 = E_0/c$ | Magnetic amplitude smaller by factor $c$ |
| Energy density | $u = \epsilon_0 E^2$ | Equal electric and magnetic contributions |
| Intensity | $I = \frac{1}{2}\epsilon_0 c E_0^2$ | Time-averaged power per area |
| Radiation pressure | $P = I/c$ (absorbed) | Light carries momentum |

**The essential insight:** Electromagnetic waves are self-sustaining oscillations where changing E creates B and changing B creates E. They carry energy, momentum, and angular momentum through empty space at the universal speed limit $c$, connecting electromagnetism to the structure of spacetime itself.
