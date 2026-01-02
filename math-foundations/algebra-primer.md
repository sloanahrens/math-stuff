# Algebra Primer

This document covers the essential algebra needed for [calculus](calculus-primer.md) and physics. Mastering these fundamentals makes everything else—from solving equations to manipulating complex expressions—straightforward.

## Numbers and Operations

### Types of Numbers

| Type | Symbol | Examples | Description |
|------|--------|----------|-------------|
| Natural | $\mathbb{N}$ | $1, 2, 3, \ldots$ | Counting numbers |
| Integers | $\mathbb{Z}$ | $\ldots, -2, -1, 0, 1, 2, \ldots$ | Whole numbers with negatives |
| Rational | $\mathbb{Q}$ | $\frac{1}{2}, -\frac{3}{4}, 0.75$ | Ratios of integers |
| Real | $\mathbb{R}$ | $\pi, \sqrt{2}, e$ | All points on the number line |
| Complex | $\mathbb{C}$ | $3 + 4i, e^{i\pi}$ | Include imaginary unit $i = \sqrt{-1}$ |

**What this means:** Physics uses all these number types. Quantum mechanics fundamentally requires complex numbers; classical mechanics mostly uses reals.

### Properties of Operations

For real numbers $a$, $b$, $c$:

| Property | Addition | Multiplication |
|----------|----------|----------------|
| Commutative | $a + b = b + a$ | $ab = ba$ |
| Associative | $(a + b) + c = a + (b + c)$ | $(ab)c = a(bc)$ |
| Identity | $a + 0 = a$ | $a \cdot 1 = a$ |
| Inverse | $a + (-a) = 0$ | $a \cdot \frac{1}{a} = 1$ (if $a \neq 0$) |
| Distributive | $a(b + c) = ab + ac$ | $a(b + c) = ab + ac$ |

**What this means:** These properties let you rearrange and simplify expressions freely. They're so fundamental you use them without thinking.

## Exponents and Logarithms

### Exponent Rules

For any base $a > 0$ and exponents $m$, $n$:

| Rule | Expression |
|------|------------|
| Product | $a^m \cdot a^n = a^{m+n}$ |
| Quotient | $\frac{a^m}{a^n} = a^{m-n}$ |
| Power of power | $(a^m)^n = a^{mn}$ |
| Power of product | $(ab)^n = a^n b^n$ |
| Zero exponent | $a^0 = 1$ |
| Negative exponent | $a^{-n} = \frac{1}{a^n}$ |
| Fractional exponent | $a^{1/n} = \sqrt[n]{a}$ |

**What this means:** Exponents compress repeated multiplication. The rule $a^m \cdot a^n = a^{m+n}$ is why we add exponents when multiplying—it's counting the total factors.

### Logarithms

The **logarithm** is the inverse of exponentiation:

```math
\log_a(x) = y \quad \Longleftrightarrow \quad a^y = x
```

**What this means:** "What power of $a$ gives $x$?" The answer is $\log_a(x)$.

### Logarithm Rules

| Rule | Expression |
|------|------------|
| Product | $\log(xy) = \log x + \log y$ |
| Quotient | $\log(x/y) = \log x - \log y$ |
| Power | $\log(x^n) = n \log x$ |
| Change of base | $\log_a x = \frac{\log_b x}{\log_b a}$ |
| Inverse | $\log_a(a^x) = x$ and $a^{\log_a x} = x$ |

**What this means:** Logarithms convert multiplication to addition and powers to multiplication. This is why slide rules worked and why logarithmic scales are useful for large ranges.

### Common Logarithms

| Notation | Base | Name | Used in |
|----------|------|------|---------|
| $\log_{10} x$ or $\log x$ | 10 | Common log | pH, decibels, earthquakes |
| $\ln x$ or $\log_e x$ | $e \approx 2.718$ | Natural log | Calculus, physics |
| $\log_2 x$ | 2 | Binary log | Computer science |

**What this means:** The natural logarithm $\ln x$ is special because $(d/dx)\ln x = 1/x$—it's the logarithm that calculus prefers.

## Polynomials

### Definition

A **polynomial** in $x$ is a sum of terms $a_n x^n$:

```math
p(x) = a_n x^n + a_{n-1} x^{n-1} + \cdots + a_1 x + a_0
```

The **degree** is the highest power with a nonzero coefficient.

### Factoring Patterns

| Pattern | Factored Form |
|---------|---------------|
| Common factor | $ax + ay = a(x + y)$ |
| Difference of squares | $x^2 - a^2 = (x-a)(x+a)$ |
| Perfect square | $x^2 \pm 2ax + a^2 = (x \pm a)^2$ |
| Sum of cubes | $x^3 + a^3 = (x+a)(x^2 - ax + a^2)$ |
| Difference of cubes | $x^3 - a^3 = (x-a)(x^2 + ax + a^2)$ |

**What this means:** Factoring reveals the structure of expressions. A factored polynomial shows its roots immediately: $(x-2)(x+3) = 0$ when $x = 2$ or $x = -3$.

### The Quadratic Formula

For $ax^2 + bx + c = 0$:

```math
\boxed{x = \frac{-b \pm \sqrt{b^2 - 4ac}}{2a}}
```

The **discriminant** $\Delta = b^2 - 4ac$ determines the nature of roots:

| Discriminant | Roots |
|--------------|-------|
| $\Delta > 0$ | Two distinct real roots |
| $\Delta = 0$ | One repeated real root |
| $\Delta < 0$ | Two complex conjugate roots |

**What this means:** Every quadratic can be solved explicitly. The discriminant tells you whether the parabola crosses the x-axis (twice, once, or never).

### Completing the Square

Any quadratic can be written as:

```math
ax^2 + bx + c = a\left(x + \frac{b}{2a}\right)^2 + \left(c - \frac{b^2}{4a}\right)
```

**What this means:** This reveals the vertex of the parabola and is essential for evaluating [Gaussian integrals](gaussian-integral.md) with linear terms.

## Equations and Solving

### Linear Equations

For $ax + b = 0$:

```math
x = -\frac{b}{a}
```

### Systems of Linear Equations

For two equations in two unknowns:

```math
\begin{cases}
a_1 x + b_1 y = c_1 \\
a_2 x + b_2 y = c_2
\end{cases}
```

**Methods:**
- **Substitution:** Solve one equation for one variable, substitute into the other
- **Elimination:** Add/subtract equations to eliminate a variable
- **Matrix methods:** See [linear algebra](linear-algebra.md) for systematic approaches

### Polynomial Equations

**Factor Theorem:** If $p(a) = 0$, then $(x - a)$ is a factor of $p(x)$.

**Rational Root Theorem:** For integer coefficients, rational roots $p/q$ have $p$ dividing the constant term and $q$ dividing the leading coefficient.

**What this means:** These theorems help find roots systematically. Once you find one root, polynomial division reduces the degree.

## Functions

### Definition

A **function** $f: A \to B$ assigns to each input $x \in A$ exactly one output $f(x) \in B$.

- **Domain:** The set of valid inputs
- **Range (Image):** The set of actual outputs
- **Codomain:** The set of possible outputs

### Function Operations

| Operation | Definition |
|-----------|------------|
| Sum | $(f + g)(x) = f(x) + g(x)$ |
| Product | $(fg)(x) = f(x) \cdot g(x)$ |
| Quotient | $(f/g)(x) = f(x)/g(x)$ (where $g(x) \neq 0$) |
| Composition | $(f \circ g)(x) = f(g(x))$ |

**What this means:** Functions can be combined like numbers. Composition is especially important—applying one function, then another.

### Inverse Functions

If $f$ is one-to-one (each output comes from exactly one input), the **inverse** $f^{-1}$ satisfies:

```math
f(f^{-1}(x)) = x \quad \text{and} \quad f^{-1}(f(x)) = x
```

**What this means:** The inverse "undoes" the function. For example, $\ln$ and $e^x$ are inverses: $\ln(e^x) = x$ and $e^{\ln x} = x$.

### Important Function Properties

| Property | Definition | Meaning |
|----------|------------|---------|
| Even | $f(-x) = f(x)$ | Symmetric about y-axis |
| Odd | $f(-x) = -f(x)$ | Symmetric about origin |
| Periodic | $f(x + T) = f(x)$ | Repeats with period $T$ |
| Increasing | $x_1 < x_2 \Rightarrow f(x_1) < f(x_2)$ | Goes up as $x$ increases |
| Decreasing | $x_1 < x_2 \Rightarrow f(x_1) > f(x_2)$ | Goes down as $x$ increases |

## Inequalities

### Rules for Inequalities

- Adding/subtracting the same quantity preserves direction
- Multiplying/dividing by a **positive** number preserves direction
- Multiplying/dividing by a **negative** number **reverses** direction

### Absolute Value

The **absolute value** $|x|$ is the distance from zero:

```math
|x| = \begin{cases} x & \text{if } x \geq 0 \\ -x & \text{if } x < 0 \end{cases}
```

**Key properties:**

| Property | Expression |
|----------|------------|
| Non-negative | $|x| \geq 0$ |
| Product | $|xy| = |x| \cdot |y|$ |
| Triangle inequality | $|x + y| \leq |x| + |y|$ |
| Reverse triangle | $||x| - |y|| \leq |x - y|$ |

**What this means:** The triangle inequality says the direct path is never longer than going via a third point. It's fundamental to analysis and appears throughout physics.

### Solving Absolute Value Inequalities

```math
|x| < a \quad \Longleftrightarrow \quad -a < x < a
```

```math
|x| > a \quad \Longleftrightarrow \quad x < -a \text{ or } x > a
```

## Complex Numbers

### The Imaginary Unit

Define $i$ by:

```math
i^2 = -1
```

A **complex number** has the form $z = a + bi$ where $a$ (real part) and $b$ (imaginary part) are real.

### Complex Arithmetic

| Operation | Formula |
|-----------|---------|
| Addition | $(a + bi) + (c + di) = (a+c) + (b+d)i$ |
| Multiplication | $(a + bi)(c + di) = (ac - bd) + (ad + bc)i$ |
| Conjugate | $\overline{a + bi} = a - bi$ |
| Modulus | $|a + bi| = \sqrt{a^2 + b^2}$ |
| Division | $\frac{z}{w} = \frac{z \bar{w}}{|w|^2}$ |

**What this means:** Complex numbers extend the reals to include solutions to all polynomial equations. Every polynomial of degree $n$ has exactly $n$ roots (counting multiplicity) in $\mathbb{C}$.

### Euler's Formula

```math
\boxed{e^{i\theta} = \cos\theta + i\sin\theta}
```

This connects exponentials to [trigonometry](trigonometry-primer.md). See [Euler's formula](euler-formula.md) for derivations and applications.

**What this means:** Complex exponentials are rotations in the complex plane. This unifies oscillations, waves, and quantum mechanics. See [quantum mechanics](../quantum-mechanics/quantum-mechanics.md) for applications.

### Polar Form

Any complex number can be written as:

```math
z = re^{i\theta} = r(\cos\theta + i\sin\theta)
```

where $r = |z|$ is the modulus and $\theta = \arg(z)$ is the argument (angle).

**What this means:** Multiplication in polar form is elegant: multiply moduli, add arguments. This makes powers and roots easy: $z^n = r^n e^{in\theta}$.

## Summation and Product Notation

### Sigma Notation

```math
\sum_{k=1}^{n} a_k = a_1 + a_2 + \cdots + a_n
```

### Common Sums

| Sum | Formula |
|-----|---------|
| Arithmetic | $\sum_{k=1}^{n} k = \frac{n(n+1)}{2}$ |
| Squares | $\sum_{k=1}^{n} k^2 = \frac{n(n+1)(2n+1)}{6}$ |
| Geometric | $\sum_{k=0}^{n-1} r^k = \frac{1 - r^n}{1 - r}$ (if $r \neq 1$) |
| Infinite geometric | $\sum_{k=0}^{\infty} r^k = \frac{1}{1-r}$ (if $|r| < 1$) |

### Product Notation

```math
\prod_{k=1}^{n} a_k = a_1 \cdot a_2 \cdots a_n
```

**Factorial:**
```math
n! = \prod_{k=1}^{n} k = 1 \cdot 2 \cdot 3 \cdots n
```

## Binomial Theorem

### The Binomial Coefficient

```math
\binom{n}{k} = \frac{n!}{k!(n-k)!}
```

Read as "$n$ choose $k$"—the number of ways to choose $k$ items from $n$.

### The Theorem

```math
(a + b)^n = \sum_{k=0}^{n} \binom{n}{k} a^{n-k} b^k
```

**What this means:** This expands powers of sums. Pascal's triangle gives the coefficients: each entry is the sum of the two above it.

### First Few Expansions

```math
(a+b)^2 = a^2 + 2ab + b^2
```

```math
(a+b)^3 = a^3 + 3a^2b + 3ab^2 + b^3
```

```math
(a+b)^4 = a^4 + 4a^3b + 6a^2b^2 + 4ab^3 + b^4
```

## Summary

| Concept | Key Formula | Where It's Used |
|---------|-------------|-----------------|
| Exponent rules | $a^m \cdot a^n = a^{m+n}$ | Everywhere |
| Logarithms | $\log(xy) = \log x + \log y$ | Simplification, calculus |
| Quadratic formula | $x = \frac{-b \pm \sqrt{b^2-4ac}}{2a}$ | Solving equations |
| Completing the square | $ax^2 + bx + c = a(x + \frac{b}{2a})^2 + \cdots$ | Gaussian integrals |
| Euler's formula | $e^{i\theta} = \cos\theta + i\sin\theta$ | Complex analysis, QM |
| Binomial theorem | $(a+b)^n = \sum \binom{n}{k} a^{n-k}b^k$ | Expansions, probability |

**The essential insight:** Algebra provides the language for manipulating mathematical expressions. These rules—for exponents, logarithms, polynomials, and complex numbers—are the grammar you need before tackling [calculus](calculus-primer.md) and physics.
