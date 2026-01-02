# Information Theory

Information theory, founded by Claude Shannon in 1948, provides a mathematical framework for quantifying, storing, and communicating information. It answers fundamental questions: How much can data be compressed? How fast can we communicate reliably over a noisy channel? The theory has deep connections to physics through [entropy](../thermodynamics/entropy.md) and underpins modern communications, cryptography, and machine learning.

Prerequisites: [probability](../math-foundations/probability-statistics.md), [logarithms](../math-foundations/algebra-primer.md).

## Fundamental Concepts

### Information Content

The information content (or "surprisal") of an event with probability $p$ is:

```math
I = -\log_2 p = \log_2 \frac{1}{p}
```

measured in **bits**.

**What this means:** Rare events carry more information. Learning something unlikely happened tells you more than learning something expected happened.

**Examples:**
- Fair coin lands heads: $I = -\log_2(1/2) = 1$ bit
- Rolling a 6 on a fair die: $I = -\log_2(1/6) \approx 2.58$ bits
- Certain event ($p = 1$): $I = 0$ bits

### Shannon Entropy

The **entropy** of a random variable $X$ with distribution $\{p_i\}$ is:

```math
\boxed{H(X) = -\sum_i p_i \log_2 p_i = \mathbb{E}[I(X)]}
```

**What this means:** Entropy is the average information content—the expected number of bits needed to describe an outcome.

**Properties:**
- $H(X) \geq 0$
- $H(X) = 0$ if and only if one outcome is certain
- $H(X)$ is maximized when all outcomes are equally likely: $H_{\max} = \log_2 n$

### Binary Entropy Function

For a binary variable with $P(X=1) = p$:

```math
H_2(p) = -p\log_2 p - (1-p)\log_2(1-p)
```

This function peaks at $p = 1/2$ where $H_2 = 1$ bit.

## Joint and Conditional Entropy

### Joint Entropy

For two random variables $X$ and $Y$:

```math
H(X, Y) = -\sum_{x,y} p(x,y) \log_2 p(x,y)
```

**Chain rule:**
```math
H(X, Y) = H(X) + H(Y|X) = H(Y) + H(X|Y)
```

### Conditional Entropy

The entropy of $Y$ given knowledge of $X$:

```math
H(Y|X) = \sum_x p(x) H(Y|X=x) = -\sum_{x,y} p(x,y) \log_2 p(y|x)
```

**What this means:** How much uncertainty remains about $Y$ after learning $X$.

**Key inequality:**
```math
H(Y|X) \leq H(Y)
```

Conditioning reduces entropy (or leaves it unchanged if $X$ and $Y$ are independent).

## Mutual Information

### Definition

The mutual information between $X$ and $Y$:

```math
\boxed{I(X;Y) = H(X) + H(Y) - H(X,Y) = H(X) - H(X|Y) = H(Y) - H(Y|X)}
```

**What this means:** How much knowing $X$ tells you about $Y$ (and vice versa). It's the reduction in uncertainty about one variable given knowledge of the other.

### Properties

- $I(X;Y) \geq 0$
- $I(X;Y) = 0$ if and only if $X$ and $Y$ are independent
- $I(X;Y) = I(Y;X)$ (symmetric)
- $I(X;X) = H(X)$ (self-information)

### Venn Diagram Interpretation

```
        ┌─────────────────────────────────────┐
        │              H(X,Y)                 │
        │  ┌──────────┐     ┌──────────┐     │
        │  │          │     │          │     │
        │  │   H(X|Y) │I(X;Y)│  H(Y|X) │     │
        │  │          │     │          │     │
        │  └──────────┘     └──────────┘     │
        │     ◄──── H(X) ────►               │
        │              ◄──── H(Y) ────►      │
        └─────────────────────────────────────┘
```

## Kullback-Leibler Divergence

### Definition

The KL divergence (or relative entropy) from $Q$ to $P$:

```math
\boxed{D_{KL}(P \| Q) = \sum_i p_i \log_2 \frac{p_i}{q_i}}
```

**What this means:** The extra bits needed to encode data from $P$ using a code optimized for $Q$. It measures how "far" $Q$ is from $P$.

### Properties

- $D_{KL}(P \| Q) \geq 0$ (Gibbs' inequality)
- $D_{KL}(P \| Q) = 0$ if and only if $P = Q$
- **Not symmetric:** $D_{KL}(P \| Q) \neq D_{KL}(Q \| P)$
- **Not a metric:** Doesn't satisfy triangle inequality

### Cross-Entropy

```math
H(P, Q) = -\sum_i p_i \log_2 q_i = H(P) + D_{KL}(P \| Q)
```

**What this means:** The average bits needed to encode data from $P$ using a code optimized for $Q$. Minimizing cross-entropy is equivalent to minimizing KL divergence.

## Source Coding

### The Source Coding Theorem

**Shannon's first theorem:** Data from a source with entropy $H$ can be compressed to an average of $H$ bits per symbol, but no fewer.

```math
\boxed{\text{Minimum average code length} = H(X)}
```

**What this means:** Entropy is the fundamental limit of lossless compression. See [data compression](data-compression.md) for algorithms that approach this limit.

### Codes

A **prefix-free code** (no codeword is a prefix of another) allows unambiguous decoding. The Kraft inequality states that codeword lengths $\ell_i$ must satisfy:

```math
\sum_i 2^{-\ell_i} \leq 1
```

**Optimal code lengths:** For minimum average length, choose $\ell_i \approx -\log_2 p_i$. This gives average length $\approx H(X)$.

## Channel Capacity

### Noisy Channels

A communication channel adds noise. Given input $X$, the output $Y$ follows some conditional distribution $p(y|x)$.

**Channel capacity:**
```math
\boxed{C = \max_{p(x)} I(X;Y)}
```

The maximum is over all input distributions.

**What this means:** $C$ is the maximum rate (bits per channel use) at which information can be transmitted reliably.

### Shannon's Channel Coding Theorem

**Shannon's second theorem:** For any rate $R < C$, there exist codes that achieve arbitrarily low error probability. For $R > C$, errors are unavoidable.

**What this means:** Reliable communication is possible up to capacity $C$—a remarkable result that seemed impossible before Shannon proved it.

### Binary Symmetric Channel

The simplest noisy channel: each bit is flipped with probability $p$.

```math
C_{BSC} = 1 - H_2(p)
```

At $p = 0$ (no noise): $C = 1$ bit per transmission.
At $p = 0.5$ (pure noise): $C = 0$ bits.

### Gaussian Channel

For additive white Gaussian noise with power $N$ and signal power $S$:

```math
C = \frac{1}{2}\log_2\left(1 + \frac{S}{N}\right) \text{ bits per sample}
```

Or in bandwidth $W$:

```math
C = W\log_2\left(1 + \frac{S}{N}\right) \text{ bits per second}
```

**What this means:** This is the Shannon-Hartley theorem—the theoretical limit for WiFi, cellular, and all communication systems.

## Connections to Physics

### Thermodynamic Entropy

The Gibbs entropy:
```math
S = -k_B \sum_i p_i \ln p_i
```

is Shannon entropy times $k_B \ln 2$:
```math
S = k_B \ln(2) \cdot H
```

See [entropy](../thermodynamics/entropy.md) for the deep connections.

### Landauer's Principle

Erasing one bit of information requires at least:
```math
E_{\min} = k_B T \ln 2
```

of energy, dissipated as heat. Information is physical.

### Maxwell's Demon

The demon that sorts molecules must store information. Erasing this information produces enough entropy to satisfy the second law. Information theory resolves the paradox.

### Quantum Information

In quantum mechanics, the von Neumann entropy replaces Shannon entropy:
```math
S = -\text{Tr}(\rho \log_2 \rho)
```

Quantum information theory studies qubits, entanglement, and quantum error correction. Quantum computers can solve certain problems exponentially faster by exploiting superposition.

## Applications

### Data Compression

- **Huffman coding:** Optimal prefix-free codes
- **Arithmetic coding:** Approaches entropy more closely
- **Lempel-Ziv:** Dictionary-based compression (used in ZIP, PNG)

See [data compression](data-compression.md).

### Error Correction

- **Hamming codes:** Correct single-bit errors
- **Reed-Solomon:** Used in CDs, QR codes, deep space communication
- **LDPC and Turbo codes:** Approach Shannon capacity

### Cryptography

- **One-time pad:** Perfect secrecy when key entropy equals message entropy
- **Entropy sources:** True randomness for key generation
- **Information-theoretic security:** Unbreakable regardless of computational power

### Machine Learning

- **Cross-entropy loss:** Standard objective for classification
- **Maximum entropy models:** Least biased inference from constraints
- **Variational inference:** Minimize KL divergence to approximate distributions
- **Information bottleneck:** Compress representations while preserving relevant information

## Summary

| Concept | Formula | Meaning |
|---------|---------|---------|
| Information | $I = -\log_2 p$ | Surprise of an event |
| Entropy | $H = -\sum p_i \log_2 p_i$ | Average information |
| Mutual information | $I(X;Y) = H(X) + H(Y) - H(X,Y)$ | Shared information |
| KL divergence | $D_{KL}(P\|Q) = \sum p_i \log_2(p_i/q_i)$ | Distribution difference |
| Channel capacity | $C = \max_{p(x)} I(X;Y)$ | Maximum reliable rate |

| Theorem | Statement |
|---------|-----------|
| Source coding | Can compress to $H$ bits/symbol, no fewer |
| Channel coding | Reliable transmission possible at rates $< C$ |

**The essential insight:** Information is quantifiable. Shannon showed that entropy measures the irreducible content of a message, and channel capacity measures the maximum rate of reliable communication. These limits are universal—they apply to any compression scheme or error-correcting code, achieved or not yet invented. Information theory doesn't just describe technology; it defines what technology can ultimately achieve.
