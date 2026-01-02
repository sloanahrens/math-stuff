# Introduction to Quantum Field Theory

Quantum field theory (QFT) unifies quantum mechanics with special relativity. It treats particles as excitations of underlying fields, naturally incorporating particle creation and annihilation. This document introduces the conceptual foundations and simplest calculations, building on [quantum mechanics](quantum-mechanics.md), [special relativity](../relativity/special-relativity.md), and the [harmonic oscillator](../classical-mechanics/harmonic-oscillator.md).

## Why Quantum Field Theory?

### Limitations of Relativistic Quantum Mechanics

The [Dirac equation](dirac-equation.md) successfully describes spin-1/2 particles relativistically, but problems remain:

1. **Negative energy solutions** suggest antiparticles, but how do they arise?
2. **Particle number** isn't conserved (pair creation from $E = mc^2$)
3. **Causality** issues with localized wave packets
4. **Multi-particle systems** are awkward in first-quantized formalism

### The QFT Solution

Instead of quantizing particles, quantize fields. Particles emerge as field excitations:

| First Quantization | Second Quantization |
|--------------------|---------------------|
| Wave function $\psi(x,t)$ | Field operator $\hat{\phi}(x,t)$ |
| Fixed particle number | Variable particle number |
| Particles fundamental | Fields fundamental |
| Nonrelativistic OK | Naturally relativistic |

## Canonical Quantization

### Classical Field Theory Review

A classical field $\phi(x,t)$ has Lagrangian density $\mathcal{L}(\phi, \partial_\mu\phi)$.

**Action:**
```math
S = \int \mathcal{L} \, d^4x
```

**Euler-Lagrange equation:**
```math
\partial_\mu\frac{\partial\mathcal{L}}{\partial(\partial_\mu\phi)} - \frac{\partial\mathcal{L}}{\partial\phi} = 0
```

**Conjugate momentum:**
```math
\pi = \frac{\partial\mathcal{L}}{\partial\dot{\phi}}
```

### Quantization Prescription

Promote fields to operators with equal-time commutation relations:

```math
\boxed{[\hat{\phi}(\mathbf{x},t), \hat{\pi}(\mathbf{x}',t)] = i\hbar\delta^3(\mathbf{x} - \mathbf{x}')}
```

```math
[\hat{\phi}(\mathbf{x},t), \hat{\phi}(\mathbf{x}',t)] = [\hat{\pi}(\mathbf{x},t), \hat{\pi}(\mathbf{x}',t)] = 0
```

This is the field-theoretic analog of $[\hat{x}, \hat{p}] = i\hbar$.

## The Free Scalar Field

### Klein-Gordon Field

The simplest relativistic field. Lagrangian density:

```math
\mathcal{L} = \frac{1}{2}(\partial_\mu\phi)(\partial^\mu\phi) - \frac{1}{2}m^2\phi^2
```

Equation of motion (Klein-Gordon):

```math
(\Box + m^2)\phi = 0
```

where $\Box = \partial_\mu\partial^\mu = \partial_t^2 - \nabla^2$ (in units $\hbar = c = 1$).

### Mode Expansion

The field operator:

```math
\hat{\phi}(x) = \int \frac{d^3p}{(2\pi)^3}\frac{1}{\sqrt{2\omega_p}}\left[\hat{a}_\mathbf{p}e^{-ip\cdot x} + \hat{a}_\mathbf{p}^\dagger e^{ip\cdot x}\right]
```

where $\omega_p = \sqrt{\mathbf{p}^2 + m^2}$ and $p \cdot x = \omega_p t - \mathbf{p}\cdot\mathbf{x}$.

### Creation and Annihilation Operators

```math
[\hat{a}_\mathbf{p}, \hat{a}_\mathbf{p'}^\dagger] = (2\pi)^3\delta^3(\mathbf{p} - \mathbf{p}')
```

```math
[\hat{a}_\mathbf{p}, \hat{a}_\mathbf{p'}] = [\hat{a}_\mathbf{p}^\dagger, \hat{a}_\mathbf{p'}^\dagger] = 0
```

**What this means:** Each momentum mode is an independent harmonic oscillator. $\hat{a}^\dagger_\mathbf{p}$ creates a particle with momentum $\mathbf{p}$; $\hat{a}_\mathbf{p}$ destroys one.

### The Fock Space

**Vacuum:** $|0\rangle$ satisfying $\hat{a}_\mathbf{p}|0\rangle = 0$ for all $\mathbf{p}$.

**One-particle states:** $|\mathbf{p}\rangle = \sqrt{2\omega_p}\hat{a}^\dagger_\mathbf{p}|0\rangle$

**n-particle states:** $|\mathbf{p}_1, \mathbf{p}_2, \ldots, \mathbf{p}_n\rangle = \sqrt{2\omega_1}\cdots\sqrt{2\omega_n}\hat{a}^\dagger_{\mathbf{p}_1}\cdots\hat{a}^\dagger_{\mathbf{p}_n}|0\rangle$

The complete Hilbert space (Fock space) is the direct sum of n-particle spaces.

### The Hamiltonian

```math
\hat{H} = \int \frac{d^3p}{(2\pi)^3}\omega_p\hat{a}^\dagger_\mathbf{p}\hat{a}_\mathbf{p} + E_0
```

where $E_0$ is an (infinite) vacuum energy—typically subtracted by normal ordering.

## The Dirac Field

### Lagrangian

```math
\mathcal{L} = \bar{\psi}(i\gamma^\mu\partial_\mu - m)\psi
```

where $\bar{\psi} = \psi^\dagger\gamma^0$.

### Anticommutation Relations

For fermions, we need anticommutators:

```math
\boxed{\{\hat{\psi}_\alpha(\mathbf{x},t), \hat{\psi}^\dagger_\beta(\mathbf{x}',t)\} = \delta_{\alpha\beta}\delta^3(\mathbf{x}-\mathbf{x}')}
```

This ensures the Pauli exclusion principle and the spin-statistics theorem.

### Mode Expansion

```math
\hat{\psi}(x) = \int \frac{d^3p}{(2\pi)^3}\frac{1}{\sqrt{2\omega_p}}\sum_{s=1,2}\left[\hat{a}^s_\mathbf{p}u^s(\mathbf{p})e^{-ip\cdot x} + \hat{b}^{s\dagger}_\mathbf{p}v^s(\mathbf{p})e^{ip\cdot x}\right]
```

- $\hat{a}^s_\mathbf{p}$: annihilates particle (electron) with spin $s$
- $\hat{b}^{s\dagger}_\mathbf{p}$: creates antiparticle (positron) with spin $s$
- $u^s, v^s$: Dirac spinors

**What this means:** The Dirac field naturally contains both particles and antiparticles. Negative energy solutions of the Dirac equation correspond to positrons.

## The Electromagnetic Field

### Lagrangian

```math
\mathcal{L} = -\frac{1}{4}F_{\mu\nu}F^{\mu\nu}
```

where $F_{\mu\nu} = \partial_\mu A_\nu - \partial_\nu A_\mu$.

### Gauge Freedom and Quantization

Quantizing requires fixing a gauge (e.g., Coulomb: $\nabla\cdot\mathbf{A} = 0$).

The photon field:

```math
\hat{A}^\mu(x) = \int \frac{d^3k}{(2\pi)^3}\frac{1}{\sqrt{2\omega_k}}\sum_{\lambda=1,2}\left[\epsilon^\mu_\lambda(\mathbf{k})\hat{a}_{\mathbf{k},\lambda}e^{-ik\cdot x} + \text{h.c.}\right]
```

where $\epsilon^\mu_\lambda$ are polarization vectors.

### Photons

- Massless: $\omega_k = |\mathbf{k}|$
- Spin-1 with two polarizations
- $\hat{a}^\dagger_{\mathbf{k},\lambda}$ creates photon with momentum $\mathbf{k}$, polarization $\lambda$

## Interactions and QED

### Quantum Electrodynamics

The QED Lagrangian:

```math
\mathcal{L}_{\text{QED}} = \bar{\psi}(i\gamma^\mu D_\mu - m)\psi - \frac{1}{4}F_{\mu\nu}F^{\mu\nu}
```

where $D_\mu = \partial_\mu + ieA_\mu$ is the covariant derivative.

Interaction term:

```math
\mathcal{L}_{\text{int}} = -e\bar{\psi}\gamma^\mu\psi A_\mu = -ej^\mu A_\mu
```

**What this means:** Electrons couple to photons through the current $j^\mu = \bar{\psi}\gamma^\mu\psi$. This is the vertex of Feynman diagrams.

### Perturbation Theory

Expand in powers of the coupling $e$:

```math
\langle f | \hat{S} | i \rangle = \langle f | T\exp\left(-i\int\hat{H}_{\text{int}}d^4x\right) | i \rangle
```

Each term corresponds to Feynman diagrams with increasing numbers of vertices.

## Feynman Diagrams

### The Rules (QED)

| Element | Meaning | Factor |
|---------|---------|--------|
| External electron line | Incoming/outgoing electron | $u(\mathbf{p})$ / $\bar{u}(\mathbf{p})$ |
| External positron line | Incoming/outgoing positron | $\bar{v}(\mathbf{p})$ / $v(\mathbf{p})$ |
| External photon line | Incoming/outgoing photon | $\epsilon_\mu(\mathbf{k})$ / $\epsilon_\mu^*(\mathbf{k})$ |
| Internal electron | Propagator | $\frac{i(\gamma^\mu p_\mu + m)}{p^2 - m^2 + i\epsilon}$ |
| Internal photon | Propagator | $\frac{-ig_{\mu\nu}}{k^2 + i\epsilon}$ |
| Vertex | Electron-photon coupling | $-ie\gamma^\mu$ |

### Example: Electron-Electron Scattering

Møller scattering at tree level: one photon exchange.

Amplitude:
```math
i\mathcal{M} = (-ie)^2\bar{u}(p_3)\gamma^\mu u(p_1)\frac{-ig_{\mu\nu}}{q^2}\bar{u}(p_4)\gamma^\nu u(p_2)
```

where $q = p_1 - p_3$ is the momentum transfer.

### Loop Diagrams and Renormalization

Higher orders include loops—integrals over internal momenta.

These often diverge! **Renormalization** absorbs infinities into redefinitions of mass, charge, and field normalizations.

**Running coupling:** The effective charge depends on energy scale:

```math
\alpha(Q^2) = \frac{\alpha(0)}{1 - \frac{\alpha(0)}{3\pi}\ln(Q^2/m_e^2)}
```

At higher energies, the electromagnetic coupling grows.

## The Standard Model (Overview)

### Particle Content

| Fermions | Gauge Bosons | Scalars |
|----------|--------------|---------|
| Quarks (6 flavors, 3 colors) | Photon (EM) | Higgs |
| Leptons (e, μ, τ + neutrinos) | W±, Z (weak) | |
| | Gluons (8) (strong) | |

### Gauge Groups

```math
SU(3)_C \times SU(2)_L \times U(1)_Y
```

- $SU(3)_C$: Quantum chromodynamics (strong force)
- $SU(2)_L \times U(1)_Y$: Electroweak (breaks to $U(1)_{\text{EM}}$)

### Key Features

- **Gauge invariance:** Forces arise from local symmetry
- **Spontaneous symmetry breaking:** Higgs mechanism gives masses
- **Asymptotic freedom:** QCD coupling weakens at high energy
- **Confinement:** Quarks bound into hadrons

## Vacuum Fluctuations

### The Casimir Effect

Between parallel conducting plates, vacuum fluctuations create a force:

```math
\frac{F}{A} = -\frac{\pi^2\hbar c}{240a^4}
```

where $a$ is plate separation. This has been measured!

### Virtual Particles

The vacuum is not empty—it's a sea of virtual particle-antiparticle pairs. These contribute to:
- Lamb shift in hydrogen
- Anomalous magnetic moment of the electron
- Hawking radiation from [black holes](../relativity/black-hole-thermodynamics.md)

## Summary

| Concept | Description |
|---------|-------------|
| Second quantization | Fields become operators, particles are excitations |
| Fock space | Hilbert space with variable particle number |
| Creation/annihilation | $\hat{a}^\dagger$, $\hat{a}$ add/remove particles |
| Spin-statistics | Bosons commute, fermions anticommute |
| Propagator | Amplitude for particle to travel from x to y |
| Vertex | Coupling between fields (interaction) |
| Feynman diagrams | Pictorial perturbation theory |
| Renormalization | Handling infinities, running couplings |

| Field | Particles | Statistics | Spin |
|-------|-----------|------------|------|
| Scalar (Klein-Gordon) | Spin-0 bosons | Bose-Einstein | 0 |
| Dirac | Electrons, positrons | Fermi-Dirac | 1/2 |
| Electromagnetic | Photons | Bose-Einstein | 1 |

**The essential insight:** Quantum field theory is the framework that unifies quantum mechanics and special relativity. Particles are no longer fundamental—they're ripples in underlying quantum fields that fill all of spacetime. This explains antiparticles, particle creation and annihilation, and the forces between particles as field interactions. The remarkable success of QED—agreement with experiment to 12 decimal places—and the Standard Model's predictions establish QFT as our deepest understanding of nature at fundamental scales. The same framework describes [statistical mechanics](../thermodynamics/statistical-mechanics.md) at finite temperature and connects to [gravitational radiation](../relativity/gravitational-waves.md) through the linearized gravity limit of general relativity.
