# Data Compression

Data compression reduces the number of bits needed to represent information. Shannon's source coding theorem proves that entropy is the fundamental limit—you cannot compress below $H$ bits per symbol on average. This document explores the theory and algorithms that approach this limit.

Prerequisites: [information theory](information-theory.md), [probability](../math-foundations/probability-statistics.md). For the physics connection, see [entropy](../thermodynamics/entropy.md).

## The Fundamental Limit

### Source Coding Theorem

For a source with entropy $H(X)$:

```math
\boxed{\text{Average bits per symbol} \geq H(X)}
```

Equality is achievable in the limit of long sequences.

**What this means:** Entropy is the incompressible core. A source that produces truly random bits (entropy = 1 bit/symbol) cannot be compressed at all. A source with patterns (lower entropy) can be compressed.

### Example: English Text

English has about 4.5 bits of entropy per character (accounting for letter frequencies and patterns), not $\log_2 26 \approx 4.7$ bits.

- Naive encoding: 8 bits/char (ASCII)
- Entropy limit: ~4.5 bits/char
- Good compression achieves ~2-3 bits/char by exploiting word patterns

## Prefix-Free Codes

### Definition

A **prefix-free code** (or instantaneous code) has the property that no codeword is a prefix of another.

**Example:**
| Symbol | Codeword |
|--------|----------|
| A | 0 |
| B | 10 |
| C | 110 |
| D | 111 |

This is prefix-free. The code $\{0, 01, 10\}$ is NOT prefix-free because 0 is a prefix of 01.

**What this means:** Prefix-free codes allow immediate decoding—you know when each codeword ends without looking ahead.

### Kraft Inequality

For a prefix-free code with codeword lengths $\ell_1, \ell_2, \ldots, \ell_n$:

```math
\sum_{i=1}^{n} 2^{-\ell_i} \leq 1
```

Conversely, if lengths satisfy this inequality, a prefix-free code with those lengths exists.

### Optimal Code Lengths

For a source with probabilities $\{p_i\}$, the optimal codeword length for symbol $i$ is:

```math
\ell_i^* = -\log_2 p_i
```

This gives average length exactly equal to entropy $H(X)$.

**Problem:** $-\log_2 p_i$ usually isn't an integer. Practical codes must round.

## Huffman Coding

### Algorithm

Huffman coding constructs an optimal prefix-free code:

1. Create a leaf node for each symbol with its probability
2. Repeat until one node remains:
   - Take the two nodes with smallest probabilities
   - Create a parent node with probability = sum of children
   - Assign 0 to one branch, 1 to the other
3. Codewords are the paths from root to leaves

### Example

Source: $P(A) = 0.4$, $P(B) = 0.3$, $P(C) = 0.2$, $P(D) = 0.1$

```
              (1.0)
             /     \
          (0.6)    A(0.4)
          /   \       |
       (0.3)  B(0.3)  0
       /   \    |
    D(0.1) C(0.2)
      |      |
     11     10
```

| Symbol | Probability | Codeword | Length |
|--------|-------------|----------|--------|
| A | 0.4 | 0 | 1 |
| B | 0.3 | 10 | 2 |
| C | 0.2 | 110 | 3 |
| D | 0.1 | 111 | 3 |

**Average length:** $0.4(1) + 0.3(2) + 0.2(3) + 0.1(3) = 1.9$ bits

**Entropy:** $H = -\sum p_i \log_2 p_i \approx 1.85$ bits

Huffman achieves within 1 bit of entropy per symbol.

### Properties

- **Optimal:** Among all prefix-free codes, Huffman minimizes average length
- **Limitation:** Average length is between $H$ and $H + 1$
- **Inefficiency:** For low-entropy sources, the "+1" overhead is significant

## Arithmetic Coding

### The Idea

Instead of assigning codewords to individual symbols, arithmetic coding represents an entire message as a single number in $[0, 1)$.

Each symbol narrows the interval proportionally to its probability.

### Algorithm (Encoding)

Start with interval $[0, 1)$. For each symbol:
1. Divide current interval into subintervals proportional to symbol probabilities
2. Select the subinterval corresponding to the symbol
3. This becomes the new interval

The final interval uniquely identifies the message.

### Example

Source: $P(A) = 0.6$, $P(B) = 0.4$

Encode "ABA":

| Step | Symbol | Interval |
|------|--------|----------|
| Start | — | $[0, 1)$ |
| A | A | $[0, 0.6)$ |
| AB | B | $[0.36, 0.6)$ |
| ABA | A | $[0.36, 0.504)$ |

Any number in $[0.36, 0.504)$ decodes to "ABA". Choose, say, 0.4.

### Properties

- **Approaches entropy:** For long messages, achieves $\approx H + \epsilon$ bits per symbol
- **No "+1" overhead:** Unlike Huffman, efficiency doesn't suffer for low-entropy sources
- **Used in:** JPEG 2000, H.264/H.265 video codecs, modern compressors

### Comparison

| Property | Huffman | Arithmetic |
|----------|---------|------------|
| Unit of coding | Single symbol | Entire message |
| Overhead | Up to 1 bit/symbol | Negligible for long messages |
| Complexity | Simple | More complex |
| Adaptivity | Requires rebuild | Easy to adapt |

## Dictionary-Based Compression

### LZ77 (Sliding Window)

Used in gzip, ZIP, PNG.

Replace repeated strings with (distance, length) pairs pointing back to previous occurrences.

**Example:**
```
Input:  ABRACADABRA
Output: ABRACAD(7,4)
```

"(7,4)" means "go back 7 positions, copy 4 characters" = "ABRA"

### LZ78 / LZW

Used in GIF, Unix compress.

Build a dictionary of strings seen so far. Output dictionary indices instead of raw strings.

**What this means:** Dictionary methods exploit repeated patterns without knowing the source statistics in advance. They're universal—they work on any source and asymptotically achieve entropy.

## Entropy Coding in Practice

### Combining Techniques

Modern compressors combine:
1. **Modeling:** Predict probability of next symbol
2. **Entropy coding:** Encode using arithmetic coding

The better the model, the lower the entropy of the prediction errors, and the better the compression.

### Context Modeling

PPM (Prediction by Partial Matching): Use previous characters to predict the next.

"After 'th', 'e' has probability 0.3" → encode 'e' efficiently.

### Burrows-Wheeler Transform

Used in bzip2. Transforms data to cluster similar characters together, making entropy coding more effective.

1. Form all rotations of input
2. Sort lexicographically
3. Output last column

This is reversible and dramatically improves compression.

## Lossy vs Lossless

### Lossless Compression

- Perfect reconstruction
- Limited by entropy
- Examples: ZIP, PNG, FLAC

### Lossy Compression

- Some information discarded
- Can compress below entropy by accepting distortion
- Examples: JPEG, MP3, H.264

**Rate-Distortion Theory:** For a given distortion level $D$, the minimum rate is:

```math
R(D) = \min_{p(\hat{x}|x): \mathbb{E}[d(X,\hat{X})] \leq D} I(X; \hat{X})
```

This tells you the fundamental tradeoff between quality and file size.

### Transform Coding

Used in JPEG, MP3, video codecs:

1. Transform to frequency domain (DCT, FFT)
2. Quantize (discard small coefficients)
3. Entropy code the quantized values

Human perception is less sensitive to high frequencies, so they can be quantized more aggressively.

## Connection to Physics

### Kolmogorov Complexity

The **Kolmogorov complexity** $K(x)$ of a string $x$ is the length of the shortest program that outputs $x$.

- Random strings: $K(x) \approx |x|$ (incompressible)
- Patterned strings: $K(x) \ll |x|$ (compressible)

**What this means:** Kolmogorov complexity is the ultimate compression limit—beyond entropy, which assumes a probabilistic source.

### Thermodynamics

Compression is related to the second law. A compressed file has lower entropy (fewer bits). To decompress, you need a program, which itself has entropy. Total information is conserved.

Landauer's principle: Compression that discards information generates heat $\geq k_B T \ln 2$ per bit.

## Summary

| Method | Achieves | Best For |
|--------|----------|----------|
| Huffman | $H$ to $H+1$ bits/symbol | Simple implementation |
| Arithmetic | $\approx H$ bits/symbol | Best lossless compression |
| LZ77/LZ78 | Asymptotically $H$ | Universal, no model needed |
| BWT + Entropy | Near $H$ | Text compression |

| Concept | Formula | Meaning |
|---------|---------|---------|
| Entropy limit | $L \geq H(X)$ | Cannot compress below entropy |
| Kraft inequality | $\sum 2^{-\ell_i} \leq 1$ | Constraint on codeword lengths |
| Optimal length | $\ell_i = -\log_2 p_i$ | Probability determines code length |

**The essential insight:** Compression is fundamentally about exploiting patterns—deviations from randomness. Shannon's theorem says entropy is the limit, and practical algorithms approach it by modeling the source and efficiently encoding predictions. Whether compressing files, transmitting data, or understanding the physics of information, the same principles apply: information has an irreducible core measured by entropy.
