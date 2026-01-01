# Magnetostatics

Magnetostatics describes magnetic fields produced by steady currents. Just as [electrostatics](electrostatics.md) deals with charges at rest, magnetostatics deals with currents that don't change in time. The theory parallels electrostatics but with crucial differences—there are no magnetic monopoles, and the fundamental sources are current loops rather than point charges. Prerequisites: [vector calculus](../math-foundations/vector-calculus.md), [electrostatics](electrostatics.md).

## Magnetic Fields from Currents

### The Biot-Savart Law

The magnetic field $\mathbf{B}$ produced by a steady current $I$ flowing through a wire:

$$
\boxed{\mathbf{B}(\mathbf{r}) = \frac{\mu_0 I}{4\pi} \int \frac{d\mathbf{l}' \times (\mathbf{r} - \mathbf{r}')}{|\mathbf{r} - \mathbf{r}'|^3}}
$$

where $d\mathbf{l}'$ is an infinitesimal element of the wire at position $\mathbf{r}'$.

For a volume current density $\mathbf{J}$:

$$
\mathbf{B}(\mathbf{r}) = \frac{\mu_0}{4\pi} \int \frac{\mathbf{J}(\mathbf{r}') \times (\mathbf{r} - \mathbf{r}')}{|\mathbf{r} - \mathbf{r}'|^3} d^3r'
$$

**What this means:** The Biot-Savart law is the magnetic analog of Coulomb's law. But while electric fields point radially from charges, magnetic fields curl around currents.

### Example: Infinite Straight Wire

For current $I$ along the $z$-axis, at distance $s$:

$$
\mathbf{B} = \frac{\mu_0 I}{2\pi s} \hat{\boldsymbol{\phi}}
$$

The field circles the wire with magnitude decreasing as $1/s$.

### Example: Circular Loop on Axis

For a loop of radius $R$ carrying current $I$, on the axis at distance $z$:

$$
B_z = \frac{\mu_0 I R^2}{2(R^2 + z^2)^{3/2}}
$$

At the center ($z = 0$): $B = \mu_0 I / 2R$.

Far away ($z \gg R$): $B \approx \mu_0 I R^2 / 2z^3$ (dipole field).

## Ampere's Law

### Integral Form

$$
\boxed{\oint_C \mathbf{B} \cdot d\mathbf{l} = \mu_0 I_{\text{enc}}}
$$

where $I_{\text{enc}}$ is the current passing through any surface bounded by the closed loop $C$.

### Differential Form

$$
\boxed{\nabla \times \mathbf{B} = \mu_0 \mathbf{J}}
$$

**What this means:** Currents are sources of curl for the magnetic field. This is the magnetic analog of Gauss's law, but with curl instead of divergence.

### Symmetry Applications

Ampere's law simplifies calculations when symmetry makes $\mathbf{B}$ constant along an Amperian loop:

| Configuration | Amperian Loop | Result |
|---------------|---------------|--------|
| Infinite wire | Circle around wire | $B = \mu_0 I / 2\pi s$ |
| Solenoid | Rectangle through coil | $B = \mu_0 n I$ inside |
| Toroid | Circle inside torus | $B = \mu_0 N I / 2\pi r$ |
| Infinite sheet | Rectangle through sheet | $B = \mu_0 K / 2$ |

where $n$ = turns per length, $N$ = total turns, $K$ = surface current density.

## The Magnetic Vector Potential

### Definition

Since $\nabla \cdot \mathbf{B} = 0$ (no magnetic monopoles), we can write:

$$
\boxed{\mathbf{B} = \nabla \times \mathbf{A}}
$$

where $\mathbf{A}$ is the **magnetic vector potential**.

### Finding the Vector Potential

In the Coulomb gauge ($\nabla \cdot \mathbf{A} = 0$):

$$
\nabla^2 \mathbf{A} = -\mu_0 \mathbf{J}
$$

Solution (compare to electrostatic potential):

$$
\mathbf{A}(\mathbf{r}) = \frac{\mu_0}{4\pi} \int \frac{\mathbf{J}(\mathbf{r}')}{|\mathbf{r} - \mathbf{r}'|} d^3r'
$$

For a line current:

$$
\mathbf{A}(\mathbf{r}) = \frac{\mu_0 I}{4\pi} \oint \frac{d\mathbf{l}'}{|\mathbf{r} - \mathbf{r}'|}
$$

**What this means:** The vector potential is to magnetostatics what the scalar potential is to electrostatics. While $\mathbf{A}$ itself isn't directly measurable classically, it has profound significance in quantum mechanics (Aharonov-Bohm effect).

### Gauge Freedom

The transformation $\mathbf{A} \to \mathbf{A} + \nabla \chi$ leaves $\mathbf{B}$ unchanged for any scalar $\chi$. The Coulomb gauge ($\nabla \cdot \mathbf{A} = 0$) is the most common choice in magnetostatics.

## Magnetic Dipoles

### The Magnetic Dipole Moment

For a current loop with area $A$ carrying current $I$:

$$
\boxed{\mathbf{m} = I \mathbf{A} = I A \hat{\mathbf{n}}}
$$

where $\hat{\mathbf{n}}$ is the normal to the loop (right-hand rule).

### Dipole Field

Far from the loop ($r \gg$ loop size):

$$
\mathbf{B} = \frac{\mu_0}{4\pi} \left[ \frac{3(\mathbf{m} \cdot \hat{\mathbf{r}})\hat{\mathbf{r}} - \mathbf{m}}{r^3} \right]
$$

This has exactly the same form as the electric dipole field.

### Vector Potential of a Dipole

$$
\mathbf{A} = \frac{\mu_0}{4\pi} \frac{\mathbf{m} \times \hat{\mathbf{r}}}{r^2}
$$

### Torque and Energy in External Field

A dipole in a uniform external field $\mathbf{B}$:

**Torque:**
$$
\boldsymbol{\tau} = \mathbf{m} \times \mathbf{B}
$$

**Potential energy:**
$$
U = -\mathbf{m} \cdot \mathbf{B}
$$

**What this means:** A magnetic dipole tends to align with the external field, minimizing energy when $\mathbf{m} \parallel \mathbf{B}$.

## Magnetization

### Magnetic Materials

When a material is placed in a magnetic field, atomic current loops align, producing a net **magnetization**:

$$
\mathbf{M} = \frac{d\mathbf{m}}{dV} = \text{magnetic dipole moment per unit volume}
$$

### Bound Currents

Magnetization produces effective currents:

**Volume current density:**
$$
\mathbf{J}_b = \nabla \times \mathbf{M}
$$

**Surface current density:**
$$
\mathbf{K}_b = \mathbf{M} \times \hat{\mathbf{n}}
$$

These bound currents contribute to the total magnetic field.

### The Auxiliary Field H

We define:

$$
\boxed{\mathbf{H} = \frac{\mathbf{B}}{\mu_0} - \mathbf{M}}
$$

Ampere's law in terms of free currents only:

$$
\nabla \times \mathbf{H} = \mathbf{J}_f \qquad \oint \mathbf{H} \cdot d\mathbf{l} = I_{f,\text{enc}}
$$

**What this means:** $\mathbf{H}$ responds only to free currents (the ones we control), while $\mathbf{B}$ includes contributions from bound currents in the material.

### Linear Materials

For linear magnetic materials:

$$
\mathbf{M} = \chi_m \mathbf{H}
$$

$$
\mathbf{B} = \mu_0(1 + \chi_m)\mathbf{H} = \mu_0 \mu_r \mathbf{H} = \mu \mathbf{H}
$$

where $\chi_m$ is magnetic susceptibility, $\mu_r = 1 + \chi_m$ is relative permeability.

| Material Type | $\chi_m$ | Behavior |
|---------------|----------|----------|
| Diamagnetic | $\sim -10^{-5}$ | Weakly opposes field |
| Paramagnetic | $\sim 10^{-5}$ | Weakly enhances field |
| Ferromagnetic | $\gg 1$ | Strongly enhances, hysteresis |

## Boundary Conditions

### At an Interface

For a boundary between two magnetic media:

**Normal component:**
$$
B_{1\perp} = B_{2\perp}
$$

**Tangential component:**
$$
H_{1\parallel} - H_{2\parallel} = K_f
$$

where $K_f$ is the free surface current density.

If no free surface currents:
$$
\frac{B_{1\parallel}}{\mu_1} = \frac{B_{2\parallel}}{\mu_2}
$$

## Inductance

### Self-Inductance

When current $I$ flows through a circuit, it creates a magnetic flux $\Phi_B$ through the circuit itself:

$$
\Phi_B = LI
$$

where $L$ is the **self-inductance**. The induced EMF opposes changes:

$$
\mathcal{E} = -L \frac{dI}{dt}
$$

### Calculating Inductance

**From flux:**
$$
L = \frac{\Phi_B}{I} = \frac{N\Phi_B}{I} \quad \text{(N turns)}
$$

**From energy:**
$$
L = \frac{2U_B}{I^2}
$$

### Common Inductances

| Configuration | Inductance |
|---------------|------------|
| Solenoid (length $\ell$, area $A$, $n$ turns/length) | $L = \mu_0 n^2 A \ell$ |
| Toroid ($N$ turns, radius $R$, cross-section $A$) | $L = \mu_0 N^2 A / 2\pi R$ |
| Coaxial cable (inner $a$, outer $b$, length $\ell$) | $L = \frac{\mu_0 \ell}{2\pi} \ln(b/a)$ |

### Mutual Inductance

For two circuits:

$$
\Phi_{12} = M_{12} I_2
$$

where $\Phi_{12}$ is flux through circuit 1 due to current in circuit 2.

**Neumann formula:**
$$
M_{12} = \frac{\mu_0}{4\pi} \oint \oint \frac{d\mathbf{l}_1 \cdot d\mathbf{l}_2}{|\mathbf{r}_1 - \mathbf{r}_2|}
$$

Note: $M_{12} = M_{21} = M$.

## Magnetic Energy

### Energy in a Magnetic Field

$$
\boxed{U_B = \frac{1}{2\mu_0} \int B^2 \, d^3r}
$$

In terms of $\mathbf{H}$:
$$
U_B = \frac{1}{2} \int \mathbf{B} \cdot \mathbf{H} \, d^3r
$$

### Energy in an Inductor

$$
U = \frac{1}{2} L I^2
$$

### Energy Density

$$
u_B = \frac{B^2}{2\mu_0} = \frac{1}{2}\mathbf{B} \cdot \mathbf{H}
$$

Compare to electric energy density: $u_E = \frac{1}{2}\epsilon_0 E^2$.

## Comparison with Electrostatics

| Electrostatics | Magnetostatics |
|----------------|----------------|
| Source: charge $\rho$ | Source: current $\mathbf{J}$ |
| $\nabla \cdot \mathbf{E} = \rho/\epsilon_0$ | $\nabla \times \mathbf{B} = \mu_0 \mathbf{J}$ |
| $\nabla \times \mathbf{E} = 0$ | $\nabla \cdot \mathbf{B} = 0$ |
| Scalar potential $\phi$ | Vector potential $\mathbf{A}$ |
| $\mathbf{E} = -\nabla \phi$ | $\mathbf{B} = \nabla \times \mathbf{A}$ |
| Electric dipole $\mathbf{p} = q\mathbf{d}$ | Magnetic dipole $\mathbf{m} = I\mathbf{A}$ |
| Polarization $\mathbf{P}$ | Magnetization $\mathbf{M}$ |
| $\mathbf{D} = \epsilon_0\mathbf{E} + \mathbf{P}$ | $\mathbf{H} = \mathbf{B}/\mu_0 - \mathbf{M}$ |

## Summary

| Concept | Key Formula | Application |
|---------|-------------|-------------|
| Biot-Savart | $\mathbf{B} = \frac{\mu_0 I}{4\pi}\int\frac{d\mathbf{l}'\times\hat{\mathbf{r}}}{r^2}$ | Field from any current |
| Ampere's law | $\oint\mathbf{B}\cdot d\mathbf{l} = \mu_0 I_{\text{enc}}$ | Symmetric configurations |
| Vector potential | $\mathbf{B} = \nabla\times\mathbf{A}$ | Gauge theory, QM |
| Dipole moment | $\mathbf{m} = IA\hat{\mathbf{n}}$ | Magnetic materials |
| Inductance | $\Phi = LI$ | Energy storage, circuits |
| Energy | $U = B^2/2\mu_0$ | Field energy density |

**The essential insight:** Magnetostatics mirrors electrostatics with currents replacing charges, but the curl structure (rather than divergence) means magnetic fields wrap around their sources instead of pointing toward them. There are no magnetic monopoles—all magnetic fields ultimately come from moving charges. The vector potential $\mathbf{A}$ may seem like just a mathematical convenience, but it takes center stage in [quantum mechanics](../quantum-mechanics/quantum-mechanics.md) and gauge theory. Combined with electrostatics, these static fields form the foundation for the full dynamics in [Maxwell's equations](maxwell-equations.md).
