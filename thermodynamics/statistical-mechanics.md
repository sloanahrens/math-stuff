# Statistical Mechanics

Statistical mechanics bridges microscopic physics and macroscopic thermodynamics. It explains why ice melts, why gases expand, and why entropy increases—all from the statistics of many particles. This document requires [probability and statistics](../math-foundations/probability-statistics.md) (distributions, expectation values, entropy) and [calculus](../math-foundations/calculus-primer.md). It connects to [quantum mechanics](../quantum-mechanics/quantum-mechanics.md), [path integrals](../classical-mechanics/path-integrals.md), and [black hole thermodynamics](../relativity/black-hole-thermodynamics.md). For computational approaches, see [numerical methods](../math-foundations/numerical-methods.md) (especially Monte Carlo).

## The Central Idea

### From Micro to Macro

A macroscopic system (gas, solid, liquid) contains $\sim 10^{23}$ particles. We can't track each one, but we can:
1. Count the number of ways to arrange them (microstates)
2. Assign probabilities to each arrangement
3. Compute average properties (pressure, energy, entropy)

**What this means:** Statistical mechanics replaces impossible deterministic tracking with powerful probabilistic reasoning.

### Microstates and Macrostates

**Microstate:** Complete specification of all particle positions and momenta $(\mathbf{q}_i, \mathbf{p}_i)$, or quantum state $|n\rangle$.

**Macrostate:** Macroscopic observables like energy $E$, volume $V$, number $N$, pressure $P$, temperature $T$.

Many microstates correspond to the same macrostate.

## The Microcanonical Ensemble

### Isolated Systems

For an isolated system with fixed $E$, $V$, $N$:

**Fundamental postulate:** All accessible microstates are equally likely.

```math
P(\text{microstate}) = \frac{1}{\Omega(E, V, N)}
```

where $\Omega$ is the number of microstates with energy $E$.

### Boltzmann Entropy

```math
\boxed{S = k_B \ln \Omega}
```

where $k_B = 1.38 \times 10^{-23}$ J/K is Boltzmann's constant.

**What this means:** Entropy counts microstates. More microstates = more entropy = more disorder. This is engraved on Boltzmann's tombstone.

### Temperature from Entropy

```math
\frac{1}{T} = \frac{\partial S}{\partial E}\bigg|_{V,N} = k_B \frac{\partial \ln\Omega}{\partial E}
```

**What this means:** Temperature is defined by how entropy changes with energy. Systems at equilibrium have equal temperatures because this maximizes total entropy.

## The Canonical Ensemble

### Systems at Fixed Temperature

For a system in thermal contact with a heat bath at temperature $T$:

**Boltzmann distribution:**

```math
\boxed{P(n) = \frac{e^{-E_n/(k_B T)}}{Z}}
```

where the **partition function** is:

```math
\boxed{Z = \sum_n e^{-E_n/(k_B T)} = \sum_n e^{-\beta E_n}}
```

with $\beta = 1/(k_B T)$.

**What this means:** States with lower energy are exponentially more likely. The partition function normalizes probabilities and encodes all thermodynamic information.

### Why Boltzmann?

The Boltzmann factor $e^{-\beta E}$ arises from maximizing entropy subject to fixed average energy. It's the most random distribution consistent with the constraint.

### Thermodynamics from $Z$

**Helmholtz free energy:**
```math
F = -k_B T \ln Z
```

**Average energy:**
```math
\langle E \rangle = -\frac{\partial \ln Z}{\partial \beta} = k_B T^2 \frac{\partial \ln Z}{\partial T}
```

**Entropy:**
```math
S = k_B(\ln Z + \beta \langle E \rangle) = -\frac{\partial F}{\partial T}
```

**Pressure:**
```math
P = -\frac{\partial F}{\partial V}
```

**What this means:** Once you compute $Z$, all thermodynamics follows by differentiation. The partition function is the central object.

### Example: Ideal Gas

For $N$ non-interacting particles in volume $V$:

```math
Z = \frac{1}{N!}\left(\frac{V}{\lambda^3}\right)^N
```

where $\lambda = \sqrt{2\pi\hbar^2/(mk_BT)}$ is the thermal de Broglie wavelength.

This gives:
```math
PV = Nk_BT, \quad \langle E \rangle = \frac{3}{2}Nk_BT
```

—the ideal gas law and equipartition theorem.

## The Grand Canonical Ensemble

### Variable Particle Number

For systems exchanging particles with a reservoir:

**Grand partition function:**

```math
\boxed{\mathcal{Z} = \sum_N e^{\beta\mu N} Z_N = \sum_{N,n} e^{-\beta(E_{N,n} - \mu N)}}
```

where $\mu$ is the **chemical potential**.

**Grand potential:**
```math
\Phi = -k_B T \ln \mathcal{Z}
```

**Average particle number:**
```math
\langle N \rangle = k_B T \frac{\partial \ln \mathcal{Z}}{\partial \mu}
```

**What this means:** The grand canonical ensemble describes open systems (gases in containers with holes, electrons in metals). The chemical potential controls average particle number.

## Quantum Statistics

### Indistinguishable Particles

In [quantum mechanics](../quantum-mechanics/quantum-mechanics.md), identical particles are truly indistinguishable. This leads to two types:

| Type | Spin | Statistics | Examples |
|------|------|------------|----------|
| Bosons | Integer (0, 1, 2, ...) | Bose-Einstein | Photons, He-4, W/Z bosons |
| Fermions | Half-integer (1/2, 3/2, ...) | Fermi-Dirac | Electrons, protons, neutrons |

### Fermi-Dirac Distribution

For fermions, no two particles can occupy the same state (Pauli exclusion):

```math
\boxed{\langle n_i \rangle = \frac{1}{e^{\beta(E_i - \mu)} + 1}}
```

At $T = 0$: states below the **Fermi energy** $E_F = \mu(T=0)$ are filled; above are empty.

**What this means:** Electrons in metals fill energy levels from the bottom up. Even at absolute zero, they have kinetic energy—this is the "Fermi sea."

### Bose-Einstein Distribution

For bosons, any number can share a state:

```math
\boxed{\langle n_i \rangle = \frac{1}{e^{\beta(E_i - \mu)} - 1}}
```

At low temperatures, bosons can macroscopically occupy the ground state: **Bose-Einstein condensation**.

**What this means:** Lasers (photons), superfluidity (He-4), and ultracold atomic gases are Bose-Einstein condensates—quantum effects at macroscopic scales.

### Classical Limit

When $e^{\beta(\mu - E_i)} \ll 1$ (low density, high temperature), both reduce to:

```math
\langle n_i \rangle \approx e^{-\beta(E_i - \mu)}
```

—the Maxwell-Boltzmann distribution.

## Blackbody Radiation

### The Problem

A cavity in thermal equilibrium contains electromagnetic radiation. What's the spectrum?

### Photon Gas

Photons are bosons with $\mu = 0$ (photon number isn't conserved). The energy density per frequency:

```math
\boxed{u(\nu, T) = \frac{8\pi h\nu^3}{c^3}\frac{1}{e^{h\nu/(k_BT)} - 1}}
```

This is **Planck's law**.

### Limiting Cases

**Low frequency (Rayleigh-Jeans):**
```math
u \approx \frac{8\pi \nu^2}{c^3} k_B T
```

**High frequency (Wien):**
```math
u \approx \frac{8\pi h\nu^3}{c^3} e^{-h\nu/(k_BT)}
```

### Stefan-Boltzmann Law

Total energy density:

```math
u = \frac{\pi^2 k_B^4}{15\hbar^3 c^3} T^4 = a T^4
```

Total power radiated per area:

```math
P = \sigma T^4, \quad \sigma = \frac{2\pi^5 k_B^4}{15h^3c^2} = 5.67 \times 10^{-8} \text{ W/(m}^2\text{K}^4)
```

**What this means:** Hot objects radiate more (∝ $T^4$). The CMB at 2.7 K is a near-perfect blackbody from the early universe.

## Entropy and the Second Law

### The Second Law

**Statement:** The total entropy of an isolated system never decreases:

```math
\Delta S \geq 0
```

### Statistical Interpretation

Entropy increases because:
1. Systems evolve toward more probable macrostates
2. More probable = more microstates = higher entropy
3. The most probable state is overwhelmingly likely ($10^{10^{23}}$ more microstates)

**What this means:** The second law is statistical, not absolute. Decreases in entropy are possible but astronomically unlikely for macroscopic systems.

### Fluctuations

For a system of $N$ particles, typical fluctuations scale as:

```math
\frac{\Delta X}{\langle X \rangle} \sim \frac{1}{\sqrt{N}}
```

For $N \sim 10^{23}$, this is $\sim 10^{-12}$—utterly undetectable.

## Phase Transitions

### Order Parameters

Phase transitions are characterized by **order parameters**:
- Liquid-gas: density difference
- Ferromagnet: magnetization
- Superconductor: Cooper pair condensate

### Classification

| Order | Discontinuity | Examples |
|-------|--------------|----------|
| First | Order parameter | Boiling, melting |
| Second | Derivative of order parameter | Ferromagnet, superconductor |

### Critical Phenomena

Near second-order transitions, systems show **critical phenomena**:
- Diverging correlation length
- Power-law behavior
- Universal critical exponents

**What this means:** Near critical points, microscopic details don't matter—only symmetry and dimensionality. This universality is one of the deep insights of statistical mechanics.

## Connection to Path Integrals

### Imaginary Time

The canonical partition function can be written as (see [path integrals](../classical-mechanics/path-integrals.md)):

```math
Z = \text{Tr}(e^{-\beta H}) = \int \mathcal{D}[x(\tau)] \, e^{-S_E/\hbar}
```

where $S_E$ is the Euclidean action and paths are periodic with period $\beta\hbar$.

**What this means:** Quantum statistical mechanics is equivalent to Euclidean path integrals. Temperature is imaginary time periodicity. This connects quantum mechanics, statistical mechanics, and field theory.

### Wick Rotation

The connection:
```math
e^{-iHt/\hbar} \xrightarrow{t \to -i\beta\hbar} e^{-\beta H}
```

Time evolution becomes the Boltzmann operator.

## Thermodynamic Potentials

### Summary Table

| Potential | Natural Variables | Differential |
|-----------|-------------------|--------------|
| $E$ (internal energy) | $S, V, N$ | $dE = TdS - PdV + \mu dN$ |
| $F$ (Helmholtz) | $T, V, N$ | $dF = -SdT - PdV + \mu dN$ |
| $G$ (Gibbs) | $T, P, N$ | $dG = -SdT + VdP + \mu dN$ |
| $\Phi$ (grand) | $T, V, \mu$ | $d\Phi = -SdT - PdV - Nd\mu$ |
| $H$ (enthalpy) | $S, P, N$ | $dH = TdS + VdP + \mu dN$ |

### Legendre Transforms

These potentials are related by Legendre transforms:
```math
F = E - TS, \quad G = F + PV, \quad \Phi = F - \mu N
```

**What this means:** Different potentials are useful for different experimental conditions (constant $T$ vs constant $E$, etc.).

## Information Theory Connection

### Shannon Entropy

The information-theoretic entropy:

```math
S = -k_B \sum_n P_n \ln P_n
```

is maximized by the Boltzmann distribution subject to $\langle E \rangle = $ const.

**What this means:** Statistical mechanics is Bayesian inference. The Boltzmann distribution is the least-biased (maximum entropy) guess consistent with knowing the average energy.

### Gibbs Entropy

More generally:

```math
S = -k_B \text{Tr}(\rho \ln \rho)
```

where $\rho$ is the density matrix—this works for quantum systems and reduces to the above for thermal states.

## Summary

| Ensemble | Fixed | Partition Function | Key Formula |
|----------|-------|-------------------|-------------|
| Microcanonical | $E, V, N$ | $\Omega$ | $S = k_B \ln \Omega$ |
| Canonical | $T, V, N$ | $Z = \sum e^{-\beta E_n}$ | $F = -k_BT \ln Z$ |
| Grand canonical | $T, V, \mu$ | $\mathcal{Z} = \sum e^{-\beta(E-\mu N)}$ | $\Phi = -k_BT \ln \mathcal{Z}$ |

| Distribution | Formula | Applies To |
|--------------|---------|------------|
| Maxwell-Boltzmann | $P \propto e^{-\beta E}$ | Classical particles |
| Fermi-Dirac | $\langle n \rangle = (e^{\beta(E-\mu)}+1)^{-1}$ | Fermions |
| Bose-Einstein | $\langle n \rangle = (e^{\beta(E-\mu)}-1)^{-1}$ | Bosons |
| Planck | $u(\nu) \propto \nu^3/(e^{\beta h\nu}-1)$ | Photons |

**The essential insight:** Statistical mechanics shows that macroscopic properties emerge from microscopic randomness. Temperature is average kinetic energy; pressure is momentum transfer; entropy counts possibilities. The partition function encodes everything, and quantum statistics explains why electrons don't collapse into atoms and why stars shine.
