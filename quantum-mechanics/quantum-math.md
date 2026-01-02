# Quantum Mechanics: An Overview

This document covers the core mathematical framework of quantum mechanics and how different interpretations address the measurement problem. We use [natural units](../math-foundations/natural-units.md) where $\hbar = 1$. The formalism connects deeply to [Hamiltonian mechanics](../classical-mechanics/hamiltonian-mechanics.md) (Poisson brackets become commutators) and [Lie groups](../math-foundations/lie-groups.md) (symmetries determine particle types).

## The Wave Function

The **wave function** $\psi(x, t)$ is the fundamental object in quantum mechanics. It encodes everything knowable about a quantum system.

For a single particle in one dimension:

```math
\psi: \mathbb{R} \times \mathbb{R} \to \mathbb{C}
```

The wave function lives in a **Hilbert space** $\mathcal{H}$—a complex vector space with an inner product:

```math
\langle \phi | \psi \rangle = \int_{-\infty}^{\infty} \phi^*(x) \psi(x) \, dx
```

### Normalization

The wave function must be normalized:

```math
\langle \psi | \psi \rangle = \int_{-\infty}^{\infty} |\psi(x)|^2 \, dx = 1
```

### Born Rule

The probability of finding the particle between $x$ and $x + dx$ is:

```math
P(x) \, dx = |\psi(x)|^2 \, dx
```

This is the **Born rule**—the bridge between the mathematical formalism and experimental predictions.

## The Schrödinger Equation

The wave function evolves according to the **Schrödinger equation**:

```math
i \frac{\partial \psi}{\partial t} = \hat{H} \psi
```

where $\hat{H}$ is the Hamiltonian operator. For a non-relativistic particle in a potential $V(x)$:

```math
\hat{H} = -\frac{1}{2m} \frac{\partial^2}{\partial x^2} + V(x)
```

giving the full equation:

```math
i \frac{\partial \psi}{\partial t} = -\frac{1}{2m} \frac{\partial^2 \psi}{\partial x^2} + V(x) \psi
```

### Time-Independent Case

For stationary states with definite energy $E$:

```math
\psi(x, t) = \phi(x) e^{-iEt}
```

The spatial part satisfies:

```math
\hat{H} \phi = E \phi
```

This eigenvalue equation determines the allowed energy levels of the system.

### Key Properties

| Property | Mathematical Expression |
|----------|------------------------|
| Linearity | If $\psi_1$ and $\psi_2$ are solutions, so is $\alpha\psi_1 + \beta\psi_2$ |
| Unitarity | $\langle \psi(t) | \psi(t) \rangle = \langle \psi(0) | \psi(0) \rangle$ (probability conserved) |
| Determinism | Given $\psi(0)$, the equation uniquely determines $\psi(t)$ |

## Operators and Observables

Physical observables correspond to **Hermitian operators**:

| Observable | Operator |
|------------|----------|
| Position | $\hat{x} = x$ |
| Momentum | $\hat{p} = -i \frac{\partial}{\partial x}$ |
| Energy | $\hat{H} = \frac{\hat{p}^2}{2m} + V(\hat{x})$ |

### Expectation Values

The expected value of an observable $\hat{A}$:

```math
\langle A \rangle = \langle \psi | \hat{A} | \psi \rangle = \int \psi^* \hat{A} \psi \, dx
```

### Commutators

The **commutator** of two operators:

```math
[\hat{A}, \hat{B}] = \hat{A}\hat{B} - \hat{B}\hat{A}
```

The fundamental commutator of quantum mechanics:

```math
[\hat{x}, \hat{p}] = i
```

## The Heisenberg Uncertainty Principle

For any two observables $\hat{A}$ and $\hat{B}$, the **uncertainty principle** states:

```math
\Delta A \cdot \Delta B \geq \frac{1}{2} |\langle [\hat{A}, \hat{B}] \rangle|
```

where $\Delta A = \sqrt{\langle A^2 \rangle - \langle A \rangle^2}$ is the standard deviation.

For position and momentum:

```math
\boxed{\Delta x \cdot \Delta p \geq \frac{1}{2}}
```

(In SI units: $\Delta x \cdot \Delta p \geq \frac{\hbar}{2}$)

### What It Means

This is **not** about measurement disturbance. It's a fundamental property of waves:

- A wave localized in position requires many momentum components (Fourier transform)
- A wave with definite momentum extends infinitely in space

The uncertainty principle is a theorem about the wave function itself, not about our knowledge or instruments.

## Superposition

A quantum system can exist in a **superposition** of states:

```math
|\psi\rangle = \alpha |0\rangle + \beta |1\rangle
```

where $|\alpha|^2 + |\beta|^2 = 1$.

The system is not "secretly" in one state or the other—it genuinely exists in both simultaneously until measurement.

## Entanglement

When two particles interact, their wave functions can become **entangled**—they can no longer be described independently.

### Product vs. Entangled States

**Separable (product) state:**

```math
|\psi\rangle = |\phi_A\rangle \otimes |\phi_B\rangle
```

**Entangled state (Bell state):**

```math
|\Phi^+\rangle = \frac{1}{\sqrt{2}} \left( |0\rangle_A |0\rangle_B + |1\rangle_A |1\rangle_B \right)
```

In the Bell state, neither particle has a definite state of its own. Measuring particle A instantly determines the state of particle B, regardless of distance.

### Bell's Theorem

Bell (1964) proved that no **local hidden variable theory** can reproduce all quantum predictions. Experiments confirm quantum mechanics—nature is genuinely nonlocal in this sense, though no information travels faster than light.

### Quantifying Entanglement

For a pure state, entanglement can be measured by the **von Neumann entropy** of the reduced density matrix:

```math
S(\rho_A) = -\text{Tr}(\rho_A \log \rho_A)
```

where $\rho_A = \text{Tr}_B(|\psi\rangle\langle\psi|)$.

For separable states: $S = 0$. For maximally entangled states: $S = \log 2$.

## The Measurement Problem

The Schrödinger equation is **deterministic** and **linear**. But measurements appear to:

1. Give random outcomes (probabilistic)
2. "Collapse" the wave function (nonlinear)

How does the smooth, deterministic wave function produce definite outcomes?

### The Collapse Postulate

The standard (Copenhagen) approach adds a separate rule:

> Upon measurement of observable $\hat{A}$, the wave function collapses to an eigenstate $|a_n\rangle$ with probability $|\langle a_n | \psi \rangle|^2$.

This works empirically but raises questions:
- What counts as a "measurement"?
- When exactly does collapse occur?
- Why is measurement different from other interactions?

## Decoherence

**Decoherence** explains why we don't see quantum superpositions at macroscopic scales—without solving the full measurement problem.

### How It Works

A quantum system interacting with its environment becomes entangled with it:

```math
\left( \alpha |0\rangle + \beta |1\rangle \right) |E_0\rangle \to \alpha |0\rangle |E_0\rangle + \beta |1\rangle |E_1\rangle
```

where $|E_0\rangle$ and $|E_1\rangle$ are environment states.

If we ignore (trace out) the environment, the system's **reduced density matrix** becomes:

```math
\rho_{\text{system}} = |\alpha|^2 |0\rangle\langle 0| + |\beta|^2 |1\rangle\langle 1| + \underbrace{\alpha\beta^* |0\rangle\langle 1| + \alpha^*\beta |1\rangle\langle 0|}_{\text{off-diagonal terms}}
```

The off-diagonal "coherence" terms decay exponentially fast:

```math
\rho_{01}(t) \propto e^{-t/\tau_D}
```

where $\tau_D$ is the **decoherence time** (often $< 10^{-20}$ seconds for macroscopic objects).

### What Decoherence Explains

- Why macroscopic superpositions are never observed
- Why certain bases (position, not momentum) are preferred
- Why the world looks classical

### What Decoherence Doesn't Explain

Decoherence gives a **diagonal** density matrix—a classical probability distribution—but doesn't explain why we see one outcome rather than all of them. The full wave function still contains all branches.

## The Many-Worlds Interpretation

The **Many-Worlds Interpretation** (MWI), proposed by Hugh Everett (1957), resolves the measurement problem by taking the Schrödinger equation literally—always and everywhere.

### Core Claims

1. **Universal Wave Function**: There's one wave function for the entire universe, evolving unitarily
2. **No Collapse**: The wave function never collapses—all branches are equally real
3. **Branching**: What looks like "measurement" is entanglement with the environment, causing the wave function to branch

### How Measurement Works

Before measurement:

```math
|\text{observer}\rangle \otimes \left( \alpha |0\rangle + \beta |1\rangle \right)
```

After interaction:

```math
\alpha |\text{observer sees 0}\rangle |0\rangle + \beta |\text{observer sees 1}\rangle |1\rangle
```

Both terms exist. There are now two "branches" of the observer, each experiencing a definite outcome.

### The Role of Decoherence

Decoherence explains why branches don't interfere:

```math
|\psi\rangle = \alpha |0\rangle |E_0\rangle + \beta |1\rangle |E_1\rangle
```

If $\langle E_0 | E_1 \rangle \approx 0$, the branches evolve independently—they can't "see" each other.

Decoherence doesn't create branches, but it makes them **effectively separate** and explains the **preferred basis** (why we branch into position states, not momentum states).

### Probability in Many-Worlds

The Born rule ($P = |\alpha|^2$) is harder to justify if all outcomes occur. Approaches include:

- **Decision theory**: Rational agents should act as if the Born rule holds
- **Self-locating uncertainty**: Before looking, you're uncertain which branch you're in
- **Measure**: Branches have different "weights" proportional to amplitude squared

### The Many-Worlds Picture

| Aspect | Copenhagen | Many-Worlds |
|--------|------------|-------------|
| Wave function | Epistemic (knowledge) | Ontic (real) |
| Collapse | Physical process | Apparent (branching + decoherence) |
| Outcomes | One is real | All are real |
| Randomness | Fundamental | Apparent (self-location) |
| Nonlocality | Explicit in collapse | Hidden in entanglement |

## Summary: Tying It Together

1. **Wave function** describes quantum systems in Hilbert space
2. **Schrödinger equation** governs deterministic, unitary evolution
3. **Uncertainty principle** is a fundamental property of waves, not measurement
4. **Entanglement** creates correlations that can't be explained classically
5. **Decoherence** explains why we don't see macroscopic superpositions
6. **Many-worlds** says: take the math literally—all branches exist, decoherence explains why we only experience one

The interpretations don't differ on predictions—they differ on what the formalism *means*. Many-worlds is arguably the most parsimonious: it adds nothing to the math, just takes it seriously.
