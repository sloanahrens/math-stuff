# Perturbation Theory

Most quantum systems cannot be solved exactly. Perturbation theory provides systematic approximations when the Hamiltonian is "close" to a solvable one. This is the workhorse of practical quantum mechanics, enabling calculations of atomic spectra, molecular properties, and transition rates. Prerequisites: [quantum mechanics](quantum-mechanics.md), [linear algebra](../math-foundations/linear-algebra.md).

## The Setup

### The Problem

We have a Hamiltonian:

```math
\hat{H} = \hat{H}_0 + \lambda \hat{H}'
```

where:
- $\hat{H}_0$ is the **unperturbed Hamiltonian** (exactly solvable)
- $\hat{H}'$ is the **perturbation**
- $\lambda$ is a small parameter (often set to 1 at the end)

We know the eigenstates and eigenvalues of $\hat{H}_0$:

```math
\hat{H}_0 |n^{(0)}\rangle = E_n^{(0)} |n^{(0)}\rangle
```

We want to find the eigenstates and eigenvalues of the full $\hat{H}$.

### Expansion

Assume the solutions can be expanded in powers of $\lambda$:

```math
|n\rangle = |n^{(0)}\rangle + \lambda|n^{(1)}\rangle + \lambda^2|n^{(2)}\rangle + \cdots
```

```math
E_n = E_n^{(0)} + \lambda E_n^{(1)} + \lambda^2 E_n^{(2)} + \cdots
```

## Time-Independent Perturbation Theory

### Non-Degenerate Case

When $E_n^{(0)}$ is not equal to any other unperturbed energy:

**First-order energy:**
```math
\boxed{E_n^{(1)} = \langle n^{(0)} | \hat{H}' | n^{(0)} \rangle}
```

The first-order correction is just the expectation value of the perturbation.

**First-order state:**
```math
\boxed{|n^{(1)}\rangle = \sum_{m \neq n} \frac{\langle m^{(0)} | \hat{H}' | n^{(0)} \rangle}{E_n^{(0)} - E_m^{(0)}} |m^{(0)}\rangle}
```

The perturbed state mixes in other unperturbed states, weighted by matrix elements divided by energy differences.

**Second-order energy:**
```math
\boxed{E_n^{(2)} = \sum_{m \neq n} \frac{|\langle m^{(0)} | \hat{H}' | n^{(0)} \rangle|^2}{E_n^{(0)} - E_m^{(0)}}}
```

**What this means:** Second-order corrections are always negative for the ground state (all denominators are negative) and typically positive for excited states. States are pushed apart by perturbations.

### Example: Anharmonic Oscillator

For harmonic oscillator with perturbation $\hat{H}' = \alpha x^4$:

First-order: $E_n^{(1)} = \alpha\langle n | x^4 | n \rangle = \frac{3\alpha\hbar^2}{4m^2\omega^2}(2n^2 + 2n + 1)$

### Degenerate Perturbation Theory

When multiple unperturbed states share the same energy, the non-degenerate formulas fail (division by zero in state correction).

**Method:** Within the degenerate subspace, diagonalize the matrix:

```math
W_{ij} = \langle i^{(0)} | \hat{H}' | j^{(0)} \rangle
```

The eigenvalues of $W$ give the first-order energy corrections. The eigenvectors give the correct zeroth-order states.

### Example: Stark Effect in Hydrogen

The electric field perturbation $\hat{H}' = eEz$ lifts degeneracy of hydrogen $n = 2$ states:

The $2s$ and $2p_0$ states mix. The $2p_{\pm 1}$ states don't couple (selection rule).

Linear Stark splitting: $\Delta E = \pm 3eEa_0$

## Time-Dependent Perturbation Theory

### The Problem

A system in eigenstate of $\hat{H}_0$ is subjected to a time-dependent perturbation $\hat{H}'(t)$.

```math
\hat{H}(t) = \hat{H}_0 + \hat{H}'(t)
```

We want the transition probability to other states.

### Transition Amplitude

Starting in state $|i\rangle$ at $t = 0$, the amplitude to be in state $|f\rangle$ at time $t$:

```math
c_f(t) = -\frac{i}{\hbar}\int_0^t \langle f | \hat{H}'(t') | i \rangle e^{i\omega_{fi}t'} dt'
```

where $\omega_{fi} = (E_f - E_i)/\hbar$.

### Transition Probability

```math
P_{i \to f}(t) = |c_f(t)|^2
```

### Sinusoidal Perturbation

For $\hat{H}'(t) = \hat{V}e^{-i\omega t} + \hat{V}^\dagger e^{i\omega t}$:

```math
c_f(t) = -\frac{i}{\hbar}V_{fi}\frac{e^{i(\omega_{fi} - \omega)t} - 1}{\omega_{fi} - \omega}
```

The probability is sharply peaked when $\omega \approx \omega_{fi}$—resonance.

## Fermi's Golden Rule

### Statement

For a perturbation turned on at $t = 0$, the transition rate to a continuum of final states:

```math
\boxed{\Gamma_{i \to f} = \frac{2\pi}{\hbar}|\langle f | \hat{H}' | i \rangle|^2 \rho(E_f)}
```

where $\rho(E_f)$ is the density of final states at energy $E_f = E_i$ (energy conservation).

**What this means:** The transition rate depends on:
1. The matrix element squared (coupling strength)
2. The density of available final states

### Applications

- **Atomic transitions:** Emission and absorption rates
- **Scattering:** Cross-sections
- **Decay:** Lifetime of excited states
- **Photoelectric effect:** Electron ejection rates

### Selection Rules

Transitions are forbidden when $\langle f | \hat{H}' | i \rangle = 0$.

For electric dipole transitions ($\hat{H}' \propto \mathbf{r}$):

| Rule | Constraint |
|------|------------|
| $\Delta \ell$ | $\pm 1$ |
| $\Delta m$ | $0, \pm 1$ |
| Parity | Must change |

## The Variational Method

### The Principle

For any trial wave function $|\psi_{\text{trial}}\rangle$:

```math
\boxed{E_{\text{ground}} \leq \frac{\langle \psi_{\text{trial}} | \hat{H} | \psi_{\text{trial}} \rangle}{\langle \psi_{\text{trial}} | \psi_{\text{trial}} \rangle}}
```

The expectation value of $\hat{H}$ in any state is an upper bound to the ground state energy.

**What this means:** Guess a wave function with adjustable parameters, minimize the energy expectation value. The result bounds the true ground state energy.

### Example: Helium Ground State

Trial function: $\psi = e^{-Z_{\text{eff}}(r_1 + r_2)/a_0}$

Minimizing over $Z_{\text{eff}}$: optimal $Z_{\text{eff}} = 27/16 \approx 1.69$

Result: $E \approx -77.5$ eV (experiment: $-79.0$ eV, error ~2%)

### Variational Parameters

Common choices:
- Effective nuclear charge (screening)
- Orbital exponents
- Linear combinations of basis functions

## The WKB Approximation

### Idea

For slowly varying potentials, the wave function is approximately:

```math
\psi(x) \approx \frac{C}{\sqrt{p(x)}} \exp\left(\pm\frac{i}{\hbar}\int p(x) dx\right)
```

where $p(x) = \sqrt{2m(E - V(x))}$ is the classical momentum.

### Validity

Valid when the wavelength changes slowly:

```math
\left|\frac{d\lambda}{dx}\right| \ll 1 \quad \Rightarrow \quad \left|\frac{\hbar}{p^2}\frac{dp}{dx}\right| \ll 1
```

Breaks down at classical turning points where $E = V(x)$.

### Connection Formulas

At turning points, WKB solutions in classically allowed and forbidden regions must be matched using Airy functions:

```math
\frac{1}{\sqrt{|p|}}\exp\left(-\frac{1}{\hbar}\int |p| dx\right) \leftrightarrow \frac{2}{\sqrt{p}}\cos\left(\frac{1}{\hbar}\int p\, dx - \frac{\pi}{4}\right)
```

### WKB Quantization

For bound states between turning points $x_1$ and $x_2$:

```math
\boxed{\int_{x_1}^{x_2} p(x) dx = \left(n + \frac{1}{2}\right)\pi\hbar}
```

This reproduces exact results for harmonic oscillator and gives good approximations for others.

### Tunneling

The tunneling probability through a barrier:

```math
T \approx \exp\left(-\frac{2}{\hbar}\int_{x_1}^{x_2} |p(x)| dx\right)
```

where the integral is over the classically forbidden region.

## Sudden and Adiabatic Approximations

### Sudden Approximation

When a perturbation is applied instantaneously (faster than any system timescale):

The wave function doesn't change; it's suddenly an eigenstate superposition of the new Hamiltonian.

```math
P_{n \to m} = |\langle m_{\text{new}} | n_{\text{old}} \rangle|^2
```

### Adiabatic Approximation

When a perturbation is applied infinitely slowly:

The system remains in the corresponding eigenstate of the instantaneous Hamiltonian.

```math
|n(t)\rangle = e^{i\gamma_n(t)}|n(t)\rangle_{\text{inst}}
```

where $\gamma_n$ is the **geometric (Berry) phase**.

### Adiabatic Condition

```math
\left|\frac{\langle m | \dot{\hat{H}} | n \rangle}{(E_m - E_n)^2}\right| \ll 1
```

The rate of change must be small compared to energy gaps.

## Summary

| Method | When to Use | Key Formula |
|--------|-------------|-------------|
| Non-degenerate PT | Distinct energy levels | $E_n^{(1)} = \langle n|\hat{H}'|n\rangle$ |
| Degenerate PT | Degenerate levels | Diagonalize $W_{ij}$ in subspace |
| Time-dependent PT | Perturbation varies in time | $c_f = -\frac{i}{\hbar}\int\langle f|\hat{H}'|i\rangle e^{i\omega_{fi}t}dt$ |
| Fermi's Golden Rule | Transitions to continuum | $\Gamma = \frac{2\pi}{\hbar}|V_{fi}|^2\rho(E)$ |
| Variational | Ground state bounds | $E_0 \leq \langle\psi|\hat{H}|\psi\rangle$ |
| WKB | Slowly varying potentials | $\psi \propto p^{-1/2}e^{\pm i\int p\,dx/\hbar}$ |
| Sudden | Fast changes | $P = |\langle m_{\text{new}}|n_{\text{old}}\rangle|^2$ |
| Adiabatic | Slow changes | Stay in instantaneous eigenstate |

**The essential insight:** Perturbation theory is the bridge between exactly solvable toy models and real physical systems. By treating deviations from ideal cases as small corrections, we can calculate atomic spectra, transition rates, tunneling probabilities, and much more. The hierarchy of approximations—first-order, second-order, Fermi's Golden Rule—corresponds to increasing precision and effort. These same methods extend to [quantum field theory](qft-introduction.md) where "perturbation theory" means Feynman diagrams and loop corrections.
