# Probability and Statistics

Probability is essential for both [quantum mechanics](../quantum-mechanics/quantum-mechanics.md) and [statistical mechanics](../thermodynamics/statistical-mechanics.md). In quantum mechanics, probability is fundamental—outcomes are inherently random. In statistical mechanics, probability handles our ignorance of microscopic details. This primer covers the concepts needed for physics.

## Basic Probability

### Probability Axioms

A **probability** $P(A)$ for event $A$ satisfies:

1. $0 \leq P(A) \leq 1$
2. $P(\text{certain event}) = 1$
3. For mutually exclusive events: $P(A \text{ or } B) = P(A) + P(B)$

**What this means:** Probabilities are numbers between 0 and 1 that add up correctly when you combine independent possibilities.

### Conditional Probability

The probability of $A$ given that $B$ occurred:

```math
P(A|B) = \frac{P(A \text{ and } B)}{P(B)}
```

**What this means:** Knowing $B$ happened changes your estimate of $A$'s probability. This is how we update beliefs with new information.

### Bayes' Theorem

```math
P(A|B) = \frac{P(B|A)P(A)}{P(B)}
```

**What this means:** This relates "probability of $A$ given $B$" to "probability of $B$ given $A$"—they're not the same! Bayes' theorem is fundamental to inference and appears in quantum measurement theory.

### Independence

Events $A$ and $B$ are **independent** if:

```math
P(A \text{ and } B) = P(A) \cdot P(B)
```

Equivalently, $P(A|B) = P(A)$—knowing $B$ doesn't change your estimate of $A$.

## Random Variables

### Discrete Random Variables

A **discrete random variable** $X$ takes values $x_1, x_2, \ldots$ with probabilities $P(X = x_i) = p_i$.

**Normalization:**
```math
\sum_i p_i = 1
```

### Continuous Random Variables

A **continuous random variable** has a **probability density function (PDF)** $p(x)$:

```math
P(a \leq X \leq b) = \int_a^b p(x) \, dx
```

**Normalization:**
```math
\int_{-\infty}^{\infty} p(x) \, dx = 1
```

**What this means:** For continuous variables, $p(x)$ is not a probability—$p(x)dx$ is. The probability of any exact value is zero; only intervals have nonzero probability.

## Expectation Values

### Definition

The **expectation value** (mean) of a random variable:

**Discrete:**
```math
\langle X \rangle = \sum_i x_i p_i
```

**Continuous:**
```math
\langle X \rangle = \int_{-\infty}^{\infty} x \, p(x) \, dx
```

**What this means:** The expectation value is the average you'd get from many measurements. It's the "center of mass" of the probability distribution.

### Expectation of Functions

For any function $f(X)$:

```math
\langle f(X) \rangle = \sum_i f(x_i) p_i \quad \text{or} \quad \int f(x) p(x) \, dx
```

### Linearity

```math
\langle aX + bY \rangle = a\langle X \rangle + b\langle Y \rangle
```

This holds whether or not $X$ and $Y$ are independent.

## Variance and Standard Deviation

### Variance

The **variance** measures the spread of a distribution:

```math
\text{Var}(X) = \langle (X - \langle X \rangle)^2 \rangle = \langle X^2 \rangle - \langle X \rangle^2
```

### Standard Deviation

```math
\sigma_X = \sqrt{\text{Var}(X)}
```

**What this means:** The standard deviation has the same units as $X$ and gives a typical deviation from the mean. For a Gaussian, about 68% of values lie within one $\sigma$ of the mean.

### Properties

- $\text{Var}(aX) = a^2 \text{Var}(X)$
- $\text{Var}(X + Y) = \text{Var}(X) + \text{Var}(Y)$ if $X$, $Y$ independent

### Uncertainty Product

In [quantum mechanics](../quantum-mechanics/quantum-mechanics.md), the **uncertainty principle** bounds products of standard deviations:

```math
\sigma_x \sigma_p \geq \frac{\hbar}{2}
```

## Important Distributions

### Uniform Distribution

All outcomes equally likely:

**Discrete:** $P(X = x_i) = 1/n$ for $n$ outcomes

**Continuous:** $p(x) = 1/(b-a)$ for $x \in [a, b]$

### Binomial Distribution

For $n$ independent trials, each with success probability $p$:

```math
P(k \text{ successes}) = \binom{n}{k} p^k (1-p)^{n-k}
```

Mean: $\langle k \rangle = np$, Variance: $\sigma^2 = np(1-p)$

### Poisson Distribution

For rare events (small $p$, large $n$, moderate $\lambda = np$):

```math
P(k) = \frac{\lambda^k e^{-\lambda}}{k!}
```

Mean and variance both equal $\lambda$.

**What this means:** Poisson describes counts of random events—radioactive decays, photon arrivals, etc.

### Gaussian (Normal) Distribution

The most important continuous distribution:

```math
\boxed{p(x) = \frac{1}{\sqrt{2\pi\sigma^2}} e^{-(x-\mu)^2/(2\sigma^2)}}
```

Mean: $\mu$, Standard deviation: $\sigma$

**What this means:** The Gaussian appears everywhere due to the **central limit theorem**: sums of many independent random variables approach a Gaussian, regardless of the underlying distribution.

### Maxwell-Boltzmann Distribution

Speed distribution for classical gas molecules:

```math
p(v) = 4\pi n \left(\frac{m}{2\pi k_B T}\right)^{3/2} v^2 e^{-mv^2/(2k_BT)}
```

See [statistical mechanics](../thermodynamics/statistical-mechanics.md).

### Boltzmann Distribution

Probability of energy state $E$ at temperature $T$:

```math
P(E) \propto e^{-E/(k_B T)}
```

This is the foundation of [statistical mechanics](../thermodynamics/statistical-mechanics.md).

## Probability in Quantum Mechanics

### Born Rule

In quantum mechanics, if a system is in state $|\psi\rangle$, the probability of measuring eigenvalue $a$ of observable $\hat{A}$ is:

```math
P(a) = |\langle a | \psi \rangle|^2
```

**What this means:** Probability amplitudes (complex numbers) are squared to get probabilities. This is why quantum mechanics uses [linear algebra](linear-algebra.md)—wave functions are vectors in Hilbert space.

### Normalization

```math
\sum_a P(a) = \sum_a |\langle a | \psi \rangle|^2 = \langle \psi | \psi \rangle = 1
```

### Expectation Values

```math
\langle \hat{A} \rangle = \langle \psi | \hat{A} | \psi \rangle = \sum_a a \, P(a)
```

See [quantum mechanics](../quantum-mechanics/quantum-mechanics.md) for details.

## Probability in Statistical Mechanics

### Ensembles

An **ensemble** is a probability distribution over microstates:

| Ensemble | Fixed | Distribution |
|----------|-------|--------------|
| Microcanonical | $E, V, N$ | All states equally likely |
| Canonical | $T, V, N$ | $P \propto e^{-E/(k_BT)}$ |
| Grand canonical | $T, V, \mu$ | $P \propto e^{-(E-\mu N)/(k_BT)}$ |

### Entropy and Probability

Boltzmann entropy:
```math
S = k_B \ln \Omega
```

Gibbs entropy:
```math
S = -k_B \sum_i p_i \ln p_i
```

**What this means:** Entropy measures the "amount of randomness" or "missing information" in a probability distribution. See [statistical mechanics](../thermodynamics/statistical-mechanics.md).

## Central Limit Theorem

### Statement

If $X_1, X_2, \ldots, X_n$ are independent random variables with the same distribution (mean $\mu$, variance $\sigma^2$), then for large $n$:

```math
\bar{X} = \frac{1}{n}\sum_{i=1}^n X_i \quad \text{is approximately Gaussian with mean } \mu \text{ and variance } \sigma^2/n
```

**What this means:** Averages of many measurements approach a Gaussian distribution. This is why the Gaussian is so ubiquitous—and why measurement errors are often Gaussian.

### Implications

- Fluctuations decrease as $1/\sqrt{n}$
- For $n \sim 10^{23}$ particles, relative fluctuations are $\sim 10^{-12}$—unmeasurable
- This is why thermodynamics works—fluctuations are negligible

## Correlation and Covariance

### Covariance

```math
\text{Cov}(X, Y) = \langle (X - \langle X \rangle)(Y - \langle Y \rangle) \rangle = \langle XY \rangle - \langle X \rangle \langle Y \rangle
```

### Correlation Coefficient

```math
\rho_{XY} = \frac{\text{Cov}(X, Y)}{\sigma_X \sigma_Y}
```

**Properties:**
- $-1 \leq \rho \leq 1$
- $\rho = 0$: uncorrelated
- $\rho = \pm 1$: perfectly (anti)correlated

**What this means:** Correlation measures how much two variables "move together." Independent variables are uncorrelated, but uncorrelated variables aren't necessarily independent.

### Quantum Correlations

Entangled quantum states can exhibit correlations that exceed classical limits (Bell inequalities). This is a deep feature of [quantum mechanics](../quantum-mechanics/quantum-mechanics.md).

## Combinatorics

### Counting Principles

**Permutations** (ordered arrangements of $k$ from $n$):
```math
P(n, k) = \frac{n!}{(n-k)!}
```

**Combinations** (unordered selections of $k$ from $n$):
```math
\binom{n}{k} = \frac{n!}{k!(n-k)!}
```

### Stirling's Approximation

For large $n$:
```math
\ln(n!) \approx n\ln n - n
```

Or more precisely:
```math
n! \approx \sqrt{2\pi n}\left(\frac{n}{e}\right)^n
```

**What this means:** This is essential for statistical mechanics, where we count microstates involving $\sim 10^{23}$ particles.

## Summary

| Concept | Definition | Physics Application |
|---------|------------|---------------------|
| Probability density | $p(x)$ with $\int p \, dx = 1$ | Wave function $|\psi|^2$ |
| Expectation value | $\langle X \rangle = \int x \, p(x) \, dx$ | Observable averages |
| Variance | $\sigma^2 = \langle X^2 \rangle - \langle X \rangle^2$ | Uncertainty |
| Gaussian | $p(x) \propto e^{-(x-\mu)^2/(2\sigma^2)}$ | Central limit theorem |
| Boltzmann | $P(E) \propto e^{-E/(k_BT)}$ | Thermal equilibrium |
| Central limit theorem | Sums approach Gaussian | Why thermo works |
| Entropy | $S = -k_B \sum p_i \ln p_i$ | Information/disorder |

**The essential insight:** Probability is unavoidable in physics. In quantum mechanics, it's fundamental—nature is probabilistic. In statistical mechanics, it handles complexity—we can't track $10^{23}$ particles, but we can predict their statistical behavior. The mathematics is the same; the interpretation differs.
