# Quantum Information

Quantum information theory extends [classical information theory](../information-theory/information-theory.md) to quantum systems, revealing fundamentally new phenomena: entanglement, no-cloning, and quantum speedup. This document covers qubits, quantum gates, entanglement, and the foundations of quantum computing. Prerequisites: [quantum mechanics](quantum-mechanics.md), [spin](spin-angular-momentum.md), [linear algebra](../math-foundations/linear-algebra.md).

## Qubits

### Classical vs Quantum Bits

A classical bit is 0 or 1. A quantum bit (qubit) is a superposition:

```math
|\psi\rangle = \alpha|0\rangle + \beta|1\rangle
```

where $|\alpha|^2 + |\beta|^2 = 1$.

### The Bloch Sphere

Any pure qubit state can be written:

```math
|\psi\rangle = \cos\frac{\theta}{2}|0\rangle + e^{i\phi}\sin\frac{\theta}{2}|1\rangle
```

This maps to a point on the unit sphere (Bloch sphere):
- North pole: $|0\rangle$
- South pole: $|1\rangle$
- Equator: equal superpositions with various phases

### Physical Realizations

| System | $\|0\rangle$ | $\|1\rangle$ |
|--------|-------------|-------------|
| Photon polarization | Horizontal | Vertical |
| Electron spin | Spin up | Spin down |
| Ion | Ground state | Excited state |
| Superconducting | Ground | First excited |

## Quantum Gates

### Single-Qubit Gates

**Pauli Gates:**

```math
X = \begin{pmatrix} 0 & 1 \\ 1 & 0 \end{pmatrix}, \quad
Y = \begin{pmatrix} 0 & -i \\ i & 0 \end{pmatrix}, \quad
Z = \begin{pmatrix} 1 & 0 \\ 0 & -1 \end{pmatrix}
```

- $X$: bit flip ($|0\rangle \leftrightarrow |1\rangle$)
- $Z$: phase flip ($|1\rangle \to -|1\rangle$)
- $Y = iXZ$

**Hadamard Gate:**

```math
H = \frac{1}{\sqrt{2}}\begin{pmatrix} 1 & 1 \\ 1 & -1 \end{pmatrix}
```

Creates superpositions: $H|0\rangle = \frac{1}{\sqrt{2}}(|0\rangle + |1\rangle) \equiv |+\rangle$

**Phase Gates:**

```math
S = \begin{pmatrix} 1 & 0 \\ 0 & i \end{pmatrix}, \quad
T = \begin{pmatrix} 1 & 0 \\ 0 & e^{i\pi/4} \end{pmatrix}
```

**Rotation Gates:**

```math
R_x(\theta) = e^{-i\theta X/2}, \quad R_y(\theta) = e^{-i\theta Y/2}, \quad R_z(\theta) = e^{-i\theta Z/2}
```

### Two-Qubit Gates

**CNOT (Controlled-NOT):**

```math
\text{CNOT} = \begin{pmatrix} 1 & 0 & 0 & 0 \\ 0 & 1 & 0 & 0 \\ 0 & 0 & 0 & 1 \\ 0 & 0 & 1 & 0 \end{pmatrix}
```

Flips target qubit if control is $|1\rangle$.

**CZ (Controlled-Z):**

```math
\text{CZ} = \begin{pmatrix} 1 & 0 & 0 & 0 \\ 0 & 1 & 0 & 0 \\ 0 & 0 & 1 & 0 \\ 0 & 0 & 0 & -1 \end{pmatrix}
```

**SWAP:**

```math
\text{SWAP} = \begin{pmatrix} 1 & 0 & 0 & 0 \\ 0 & 0 & 1 & 0 \\ 0 & 1 & 0 & 0 \\ 0 & 0 & 0 & 1 \end{pmatrix}
```

### Universal Gate Sets

Any quantum computation can be decomposed into:
- $\{H, T, \text{CNOT}\}$ (discrete universal set)
- $\{R_y, R_z, \text{CNOT}\}$ (continuous universal set)

## Density Matrices

### Pure vs Mixed States

**Pure state:** A system in a definite quantum state $|\psi\rangle$.

**Mixed state:** Statistical ensemble of pure states. Described by the **density matrix**:

```math
\rho = \sum_i p_i |\psi_i\rangle\langle\psi_i|
```

where $p_i$ are classical probabilities.

### Properties

```math
\text{Tr}(\rho) = 1, \quad \rho = \rho^\dagger, \quad \rho \geq 0
```

**Pure state criterion:**

```math
\text{Tr}(\rho^2) = 1 \quad \text{(pure)}, \quad \text{Tr}(\rho^2) < 1 \quad \text{(mixed)}
```

### Single Qubit Density Matrix

```math
\rho = \frac{1}{2}(I + \mathbf{r} \cdot \boldsymbol{\sigma})
```

where $\mathbf{r}$ is the Bloch vector ($|\mathbf{r}| \leq 1$) and $\boldsymbol{\sigma} = (X, Y, Z)$.

## Entanglement

### Definition

A state of multiple qubits is **entangled** if it cannot be written as a product:

```math
|\psi_{AB}\rangle \neq |\psi_A\rangle \otimes |\psi_B\rangle
```

### Bell States

The maximally entangled two-qubit states:

```math
|\Phi^+\rangle = \frac{1}{\sqrt{2}}(|00\rangle + |11\rangle)
```

```math
|\Phi^-\rangle = \frac{1}{\sqrt{2}}(|00\rangle - |11\rangle)
```

```math
|\Psi^+\rangle = \frac{1}{\sqrt{2}}(|01\rangle + |10\rangle)
```

```math
|\Psi^-\rangle = \frac{1}{\sqrt{2}}(|01\rangle - |10\rangle)
```

**What this means:** Measuring one qubit of a Bell pair instantly determines the other's state, regardless of separation. This is the basis of quantum nonlocality.

### Creating Entanglement

Bell state from $|00\rangle$:

```math
|00\rangle \xrightarrow{H \otimes I} \frac{1}{\sqrt{2}}(|0\rangle + |1\rangle)|0\rangle \xrightarrow{\text{CNOT}} \frac{1}{\sqrt{2}}(|00\rangle + |11\rangle)
```

### Entanglement Measures

**For pure states:**

```math
\boxed{E(\psi_{AB}) = S(\rho_A) = -\text{Tr}(\rho_A \log_2 \rho_A)}
```

where $\rho_A = \text{Tr}_B(|\psi\rangle\langle\psi|)$ is the reduced density matrix.

For Bell states: $E = 1$ ebit (maximum for two qubits).

## Bell Inequalities

### The CHSH Inequality

For local hidden variable theories:

```math
|\langle A_1 B_1\rangle + \langle A_1 B_2\rangle + \langle A_2 B_1\rangle - \langle A_2 B_2\rangle| \leq 2
```

where $A_i, B_j = \pm 1$ are measurement outcomes.

**Quantum mechanics violates this:**

```math
\boxed{|\langle CHSH\rangle_{\text{QM}}| \leq 2\sqrt{2} \approx 2.83}
```

The maximum is achieved by Bell states with optimal measurement angles.

**What this means:** Quantum correlations are stronger than any classical (local realistic) theory can produce. Experiments confirm the quantum prediction.

## No-Cloning Theorem

### Statement

```math
\boxed{\text{There is no unitary } U \text{ such that } U|\psi\rangle|0\rangle = |\psi\rangle|\psi\rangle \text{ for all } |\psi\rangle}
```

### Proof

Suppose such $U$ exists. For two states $|\psi\rangle$ and $|\phi\rangle$:

```math
U|\psi\rangle|0\rangle = |\psi\rangle|\psi\rangle, \quad U|\phi\rangle|0\rangle = |\phi\rangle|\phi\rangle
```

Taking inner product and using unitarity:

```math
\langle\psi|\phi\rangle = \langle\psi|\phi\rangle^2
```

This only holds if $\langle\psi|\phi\rangle = 0$ or $1$, so arbitrary states cannot be cloned.

**What this means:** Quantum information cannot be copied, enabling quantum cryptography (eavesdropping is detectable).

## Quantum Teleportation

### Protocol

To teleport unknown state $|\psi\rangle = \alpha|0\rangle + \beta|1\rangle$ from Alice to Bob:

1. Alice and Bob share a Bell pair $|\Phi^+\rangle_{AB}$
2. Alice performs Bell measurement on her qubit and the unknown state
3. Alice sends 2 classical bits to Bob (measurement result)
4. Bob applies correction ($I$, $X$, $Z$, or $XZ$) based on Alice's bits

**Result:** Bob's qubit becomes $|\psi\rangle$

### Key Points

- The original state is destroyed (no-cloning respected)
- Classical communication is required (no faster-than-light signaling)
- Entanglement is consumed (1 ebit per teleportation)

## Quantum Computing

### Quantum Parallelism

A register of $n$ qubits can be in superposition of all $2^n$ basis states:

```math
|\psi\rangle = \sum_{x=0}^{2^n-1} \alpha_x |x\rangle
```

A quantum gate acts on all $2^n$ components simultaneously.

### Quantum Algorithms

**Deutsch-Jozsa:** Determines if function is constant or balanced with 1 query (classically needs $2^{n-1} + 1$).

**Grover's Search:** Finds item in unsorted database of $N$ items in $O(\sqrt{N})$ queries (classically $O(N)$).

**Shor's Algorithm:** Factors $n$-bit integer in polynomial time (classically believed exponential). Threatens RSA cryptography.

### Quantum Speedup

| Problem | Classical | Quantum |
|---------|-----------|---------|
| Unstructured search | $O(N)$ | $O(\sqrt{N})$ |
| Factoring | $\exp(n^{1/3})$ | $O(n^3)$ |
| Simulation of quantum systems | $\exp(n)$ | $O(n)$ |

## Quantum Error Correction

### The Challenge

Quantum states are fragile:
- Decoherence from environment
- Gate errors
- Measurement errors

Classical error correction (redundancy) fails due to no-cloning.

### Quantum Error Correcting Codes

Encode 1 logical qubit in multiple physical qubits.

**3-qubit bit-flip code:**

```math
|0\rangle_L = |000\rangle, \quad |1\rangle_L = |111\rangle
```

Corrects single bit-flip ($X$) errors.

**Shor's 9-qubit code:** Corrects arbitrary single-qubit errors.

**Surface codes:** Leading candidate for fault-tolerant quantum computing.

### The Threshold Theorem

```math
\boxed{\text{If error rate } < p_{\text{th}}, \text{ arbitrarily long quantum computation is possible}}
```

Current estimates: $p_{\text{th}} \sim 1\%$ for surface codes.

## Quantum Entropy

### Von Neumann Entropy

```math
\boxed{S(\rho) = -\text{Tr}(\rho \log_2 \rho) = -\sum_i \lambda_i \log_2 \lambda_i}
```

where $\lambda_i$ are eigenvalues of $\rho$.

Properties:
- $S(\rho) = 0$ for pure states
- $S(\rho) \leq \log_2 d$ for $d$-dimensional system
- Subadditivity: $S(\rho_{AB}) \leq S(\rho_A) + S(\rho_B)$

### Quantum Mutual Information

```math
I(A:B) = S(\rho_A) + S(\rho_B) - S(\rho_{AB})
```

For entangled states, $I(A:B) > 0$ even when $S(\rho_{AB}) = 0$.

### Connection to Classical Entropy

For diagonal density matrices (classical probability distributions), von Neumann entropy reduces to [Shannon entropy](../information-theory/information-theory.md).

## Summary

| Concept | Description |
|---------|-------------|
| Qubit | $\alpha\|0\rangle + \beta\|1\rangle$ with $\|\alpha\|^2 + \|\beta\|^2 = 1$ |
| Bloch sphere | Geometric representation of qubit states |
| Quantum gates | Unitary operations on qubits |
| Density matrix | $\rho = \sum_i p_i \|\psi_i\rangle\langle\psi_i\|$ for mixed states |
| Entanglement | Non-separable multi-qubit states |
| Bell states | Maximally entangled two-qubit states |
| No-cloning | Arbitrary quantum states cannot be copied |
| Teleportation | State transfer using entanglement + classical bits |

| Inequality/Theorem | Statement |
|-------------------|-----------|
| CHSH (classical) | $\|S\| \leq 2$ |
| CHSH (quantum) | $\|S\| \leq 2\sqrt{2}$ |
| No-cloning | $\nexists U: U\|\psi\rangle\|0\rangle = \|\psi\rangle\|\psi\rangle$ for all $\|\psi\rangle$ |
| Threshold | Error rate $< p_{\text{th}}$ enables fault tolerance |

| Algorithm | Speedup |
|-----------|---------|
| Grover (search) | $O(N) \to O(\sqrt{N})$ |
| Shor (factoring) | Exponential to polynomial |
| Quantum simulation | Exponential to polynomial |

**The essential insight:** Quantum information exploits superposition and entanglement to process information in fundamentally new ways. Entanglement enables correlations stronger than any classical theory (Bell inequality violations), while the no-cloning theorem ensures quantum information cannot be copied—enabling secure quantum cryptography. Quantum computers exploit parallelism across exponentially many states, but extracting useful information requires clever algorithms like Grover's and Shor's. Error correction is possible despite no-cloning, with fault-tolerant computation achievable below error thresholds. These concepts connect deeply to [thermodynamic entropy](../thermodynamics/entropy.md) through von Neumann entropy and to the foundations of [quantum mechanics](quantum-mechanics.md) through measurement and decoherence.
