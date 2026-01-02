# Entropy

Entropy is perhaps the most profound concept in physics. It connects the microscopic world of atoms to the macroscopic world of heat engines, and bridges physics to information theory. This document explores entropy from multiple perspectives and reveals why Boltzmann's $S = k_B \ln W$ and Shannon's $H = -\sum p_i \log p_i$ are fundamentally the same idea.

Prerequisites: [thermodynamics](thermodynamics.md), [statistical mechanics](statistical-mechanics.md), [probability](../math-foundations/probability-statistics.md). See [information theory](../information-theory/information-theory.md) for the full information-theoretic treatment.

## Historical Development

### Clausius: Entropy as Heat Flow

Clausius (1865) defined entropy change as:

```math
dS = \frac{\delta Q_{\text{rev}}}{T}
```

For a reversible process, the total entropy change is:

```math
\Delta S = \int \frac{\delta Q_{\text{rev}}}{T}
```

**What this means:** Entropy measures the "dispersal" of energy. When heat flows from hot to cold, total entropy increases.

**The Clausius inequality:** For any cyclic process:
```math
\oint \frac{\delta Q}{T} \leq 0
```

with equality only for reversible cycles.

### Boltzmann: Entropy as Counting States

Boltzmann (1877) provided the microscopic interpretation:

```math
\boxed{S = k_B \ln W}
```

where:
- $k_B = 1.38 \times 10^{-23}$ J/K is Boltzmann's constant
- $W$ is the number of microstates consistent with the macrostate

**What this means:** Entropy counts possibilities. A system with more ways to arrange its microscopic components has higher entropy.

**Example:** Consider $N$ coins. The macrostate "all heads" has $W = 1$. The macrostate "half heads, half tails" has $W = \binom{N}{N/2} \approx 2^N/\sqrt{N}$ for large $N$. The second has enormously higher entropy.

### Gibbs: The General Formula

Gibbs generalized to arbitrary probability distributions:

```math
\boxed{S = -k_B \sum_i p_i \ln p_i}
```

where $p_i$ is the probability of microstate $i$.

**What this means:** This reduces to Boltzmann's formula when all $W$ microstates are equally probable ($p_i = 1/W$):
```math
S = -k_B \sum_{i=1}^W \frac{1}{W} \ln \frac{1}{W} = k_B \ln W
```

## Shannon Entropy: Information Theory

### Definition

Shannon (1948) defined information entropy:

```math
\boxed{H = -\sum_i p_i \log_2 p_i}
```

measured in **bits**.

**What this means:** $H$ measures uncertainty or information content. It answers: "How many yes/no questions do I need to ask, on average, to determine the outcome?"

### Key Properties

**Maximum entropy:** $H$ is maximized when all outcomes are equally likely:
```math
H_{\max} = \log_2 N
```

for $N$ outcomes.

**Zero entropy:** $H = 0$ when one outcome has probability 1 (complete certainty).

**Additivity:** For independent systems:
```math
H(A, B) = H(A) + H(B)
```

### Examples

**Fair coin:** $p_H = p_T = 1/2$
```math
H = -\frac{1}{2}\log_2\frac{1}{2} - \frac{1}{2}\log_2\frac{1}{2} = 1 \text{ bit}
```

**Biased coin:** $p_H = 0.9$, $p_T = 0.1$
```math
H = -0.9\log_2(0.9) - 0.1\log_2(0.1) \approx 0.47 \text{ bits}
```

**What this means:** A biased coin carries less uncertainty—you can often guess correctly.

## The Deep Connection

### Same Formula, Different Units

Boltzmann and Shannon entropy are mathematically identical:

| Boltzmann | Shannon |
|-----------|---------|
| $S = -k_B \sum p_i \ln p_i$ | $H = -\sum p_i \log_2 p_i$ |
| Units: J/K | Units: bits |
| Constant: $k_B$ | Constant: 1 |
| Natural log | Log base 2 |

**The conversion:**
```math
S = k_B \ln(2) \cdot H
```

or numerically:
```math
1 \text{ bit} = k_B \ln 2 \approx 10^{-23} \text{ J/K}
```

### Why Are They the Same?

Both measure the same thing: **missing information** about the microstate.

**Physical entropy:** You know macroscopic variables (temperature, pressure) but not the exact positions and velocities of $10^{23}$ particles. $S$ measures this missing information.

**Information entropy:** You know the probability distribution but not which specific outcome will occur. $H$ measures this missing information.

**The Landauer principle** makes this connection physical:

```math
\boxed{\text{Erasing 1 bit of information requires at least } k_B T \ln 2 \text{ of energy}}
```

**What this means:** Information is physical. Deleting data generates heat. This resolves Maxwell's demon paradox.

### Maxwell's Demon

**The paradox:** Imagine a demon that opens a door to let fast molecules through one way and slow molecules the other, creating a temperature difference without doing work—violating the second law.

**The resolution:** The demon must store information about each molecule. When its memory fills, it must erase bits, generating entropy $\geq k_B \ln 2$ per bit—exactly compensating the entropy decrease from sorting.

## Entropy in Statistical Mechanics

### The Microcanonical Ensemble

For an isolated system with fixed energy $E$:
```math
S(E) = k_B \ln \Omega(E)
```

where $\Omega(E)$ is the number of states with energy $E$.

Temperature emerges from:
```math
\frac{1}{T} = \frac{\partial S}{\partial E}
```

### The Canonical Ensemble

For a system at temperature $T$:
```math
S = -k_B \sum_i p_i \ln p_i = \frac{\langle E \rangle - F}{T}
```

where $F = -k_B T \ln Z$ is the Helmholtz free energy.

### Maximum Entropy Principle

The equilibrium distribution **maximizes entropy** subject to constraints.

**Example:** Maximizing $S = -k_B \sum p_i \ln p_i$ with constraint $\sum p_i E_i = \langle E \rangle$ gives the Boltzmann distribution:
```math
p_i = \frac{e^{-E_i/k_B T}}{Z}
```

**What this means:** Equilibrium isn't special—it's just the overwhelmingly most probable state. The second law follows from statistics, not dynamics.

## Why Does Entropy Increase?

### The Statistical Argument

Consider a gas confined to one half of a box. When the partition is removed:
- Initial state: $W_i = $ (ways to fit $N$ molecules in half the box)
- Final state: $W_f = $ (ways to fit $N$ molecules in the whole box)

The ratio:
```math
\frac{W_f}{W_i} = 2^N
```

For $N \sim 10^{23}$, this is $2^{10^{23}}$—an incomprehensibly huge number.

**What this means:** The gas doesn't "want" to expand. It's just overwhelmingly more likely to be spread out. The second law is not dynamical—it's combinatorial.

### The Arrow of Time

**Why doesn't entropy decrease?** The fundamental laws of physics are time-reversible. Yet macroscopic processes have a preferred direction.

**Resolution:** The second law is statistical, not absolute. Entropy *can* decrease—it's just fantastically unlikely. For $10^{23}$ particles, a spontaneous entropy decrease large enough to notice would take longer than the age of the universe.

**The past hypothesis:** The universe started in a low-entropy state (the Big Bang). The arrow of time—why we remember the past but not the future—ultimately traces to this cosmological initial condition.

## Relative Entropy (Kullback-Leibler Divergence)

The "distance" between two probability distributions:

```math
D_{KL}(P \| Q) = \sum_i p_i \log \frac{p_i}{q_i}
```

**Properties:**
- $D_{KL} \geq 0$ (Gibbs' inequality)
- $D_{KL} = 0$ if and only if $P = Q$
- Not symmetric: $D_{KL}(P \| Q) \neq D_{KL}(Q \| P)$

**What this means:** $D_{KL}$ measures the information lost when using $Q$ to approximate $P$.

**In physics:** The entropy production in an irreversible process equals the KL divergence between the actual distribution and equilibrium.

## Entropy in Different Contexts

### Thermodynamic Entropy

```math
S = \int \frac{\delta Q_{\text{rev}}}{T}
```

Measures heat dispersal. Units: J/K.

### Statistical Entropy

```math
S = -k_B \sum p_i \ln p_i
```

Counts microstates. Units: J/K.

### Information Entropy

```math
H = -\sum p_i \log_2 p_i
```

Measures uncertainty. Units: bits.

### Von Neumann Entropy (Quantum)

```math
S = -\text{Tr}(\rho \ln \rho)
```

where $\rho$ is the density matrix. Measures quantum uncertainty and entanglement. See [quantum mechanics](../quantum-mechanics/quantum-mechanics.md).

### Black Hole Entropy

```math
S_{BH} = \frac{k_B c^3 A}{4 G \hbar}
```

Proportional to horizon area, not volume. The largest entropy objects in the universe. See [black hole thermodynamics](../relativity/black-hole-thermodynamics.md).

## Applications

### Data Compression

Shannon entropy sets the fundamental limit:

```math
\text{Average bits per symbol} \geq H
```

You cannot compress below the entropy. See [data compression](../information-theory/data-compression.md).

### Machine Learning

**Cross-entropy loss:**
```math
L = -\sum_i y_i \log \hat{y}_i
```

Used to train neural networks. Minimizing cross-entropy is equivalent to minimizing KL divergence from the true distribution.

**Maximum entropy models:** When you don't know the distribution, assume maximum entropy consistent with known constraints. This is the "least biased" assumption.

### Thermodynamic Computing

Landauer's principle sets the minimum energy cost of computation. Modern research explores "reversible computing" to reduce this limit and "thermodynamic computing" that exploits fluctuations.

## Summary

| Formulation | Formula | Measures |
|-------------|---------|----------|
| Clausius | $dS = \delta Q_{\text{rev}}/T$ | Heat dispersal |
| Boltzmann | $S = k_B \ln W$ | Microstate count |
| Gibbs | $S = -k_B \sum p_i \ln p_i$ | Statistical uncertainty |
| Shannon | $H = -\sum p_i \log_2 p_i$ | Information content |
| Von Neumann | $S = -\text{Tr}(\rho \ln \rho)$ | Quantum uncertainty |

| Connection | Equation |
|------------|----------|
| Boltzmann ↔ Shannon | $S = k_B \ln(2) \cdot H$ |
| Information ↔ Energy | Erasing 1 bit costs $\geq k_B T \ln 2$ |
| Entropy ↔ Probability | $S$ maximized at equilibrium |

**The essential insight:** Entropy is not "disorder"—it's missing information. Whether counting microstates in a gas or bits in a message, we're measuring the same thing: how much we don't know. This deep unity connects thermodynamics to information theory, explains the arrow of time, and reveals that information itself is physical. As Landauer said: "Information is physical."
