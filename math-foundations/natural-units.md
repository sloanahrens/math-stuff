# Natural Units: Setting $G = c = 1$

In relativistic physics, equations become much cleaner when we use **natural units** where the speed of light $c$ and Newton's gravitational constant $G$ are set to unity. This document explains how this works and how to convert between natural and SI units. These conventions are used throughout the documents on [special relativity](../relativity/special-relativity.md), [general relativity](../relativity/schwarzschild-solution.md), [gravitational waves](../relativity/gravitational-waves.md), [quantum mechanics](../quantum-mechanics/quantum-mechanics.md), and [the Dirac equation](../quantum-mechanics/dirac-equation.md). See [physical constants](physical-constants.md) for precise values and unit conversions.

## Why Use Natural Units?

In SI units, fundamental equations carry factors of $c$ and $G$ that obscure the physics:

**Einstein's mass-energy relation:**
```math
E = mc^2 \quad \longrightarrow \quad E = m
```

**Schwarzschild radius:**
```math
r_s = \frac{2GM}{c^2} \quad \longrightarrow \quad r_s = 2M
```

**Einstein field equations:**
```math
R_{\mu\nu} - \frac{1}{2}Rg_{\mu\nu} = \frac{8\pi G}{c^4} T_{\mu\nu} \quad \longrightarrow \quad R_{\mu\nu} - \frac{1}{2}Rg_{\mu\nu} = 8\pi T_{\mu\nu}
```

The natural unit versions reveal the essential structure without dimensional clutter.

## What It Means Physically

### Setting $c = 1$

This equates units of **length** and **time**:

```math
c = 3 \times 10^8 \; \text{m/s} = 1 \quad \Rightarrow \quad 1 \text{ second} = 3 \times 10^8 \text{ meters}
```

Consequences:
- Velocities become dimensionless fractions of $c$
- Energy and mass have the same units: $E = m$ (not $mc^2$)
- Momentum and mass have the same units: $p = mv\gamma$
- Time and length are interchangeable: spacetime intervals $ds^2 = -dt^2 + dx^2$

### Setting $G = 1$

This further equates **mass** with **length** (and time):

```math
G = 6.67 \times 10^{-11} \; \text{m}^3 \text{kg}^{-1} \text{s}^{-2} = 1
```

With $c = 1$ already set:
```math
G = 1 \quad \Rightarrow \quad 1 \text{ kg} = 7.43 \times 10^{-28} \text{ meters}
```

This means:
- Mass, length, and time all share a common unit
- The Sun's mass $M_\odot \approx 1.5$ km
- Energy density has units of inverse length squared

## Dimensional Analysis

In natural units, every quantity can be expressed as a power of a single dimension (typically length or mass):

| Quantity | SI Dimensions | Natural Units |
|----------|---------------|---------------|
| Length | $[L]$ | $[L]$ |
| Time | $[T]$ | $[L]$ |
| Mass | $[M]$ | $[L]$ |
| Velocity | $[LT^{-1}]$ | dimensionless |
| Energy | $[ML^2T^{-2}]$ | $[L]$ |
| Momentum | $[MLT^{-1}]$ | $[L]$ |
| Force | $[MLT^{-2}]$ | dimensionless |
| Energy density | $[ML^{-1}T^{-2}]$ | $[L^{-2}]$ |

## Converting to SI Units

To restore SI units, multiply by appropriate powers of $c$ and $G$ to fix dimensions.

### The Conversion Factors

```math
c = 2.998 \times 10^8 \; \text{m/s}
```

```math
G = 6.674 \times 10^{-11} \; \text{m}^3 \text{kg}^{-1} \text{s}^{-2}
```

```math
\frac{G}{c^2} = 7.426 \times 10^{-28} \; \text{m/kg}
```

```math
\frac{G}{c^3} = 2.477 \times 10^{-36} \; \text{s/kg}
```

### Conversion Rules

| To convert from natural units | Multiply by |
|------------------------------|-------------|
| Mass $\to$ length | $G/c^2$ |
| Mass $\to$ time | $G/c^3$ |
| Length $\to$ mass | $c^2/G$ |
| Time $\to$ mass | $c^3/G$ |
| Energy $\to$ mass | $1/c^2$ |
| Mass $\to$ energy | $c^2$ |

### Recipe

1. Write the quantity in natural units
2. Determine what SI dimensions you need
3. Insert factors of $G$ and $c$ to balance dimensions

**Example:** Schwarzschild radius

Natural units: $r_s = 2M$

Need: length from mass

```math
r_s = 2M \cdot \frac{G}{c^2} = \frac{2GM}{c^2}
```

For the Sun ($M_\odot = 2 \times 10^{30}$ kg):
```math
r_s = \frac{2 \times 6.67 \times 10^{-11} \times 2 \times 10^{30}}{(3 \times 10^8)^2} \approx 3 \text{ km}
```

## Common Quantities in Both Systems

| Quantity | Natural Units | SI Units |
|----------|---------------|----------|
| Schwarzschild radius | $r_s = 2M$ | $r_s = \frac{2GM}{c^2}$ |
| Gravitational time dilation | $\sqrt{1 - \frac{2M}{r}}$ | $\sqrt{1 - \frac{2GM}{rc^2}}$ |
| Orbital velocity | $v = \sqrt{\frac{M}{r}}$ | $v = \sqrt{\frac{GM}{r}}$ |
| Gravitational potential | $\Phi = -\frac{M}{r}$ | $\Phi = -\frac{GM}{r}$ |
| Einstein equations | $G_{\mu\nu} = 8\pi T_{\mu\nu}$ | $G_{\mu\nu} = \frac{8\pi G}{c^4} T_{\mu\nu}$ |

## Mass-Length-Time Equivalences

Some useful reference values:

| Object | Mass (kg) | Mass in natural units (m) | Mass in natural units (s) |
|--------|-----------|---------------------------|---------------------------|
| Sun | $2.0 \times 10^{30}$ | $1.5 \times 10^{3}$ m | $4.9 \times 10^{-6}$ s |
| Earth | $6.0 \times 10^{24}$ | $4.4 \times 10^{-3}$ m | $1.5 \times 10^{-11}$ s |
| Proton | $1.7 \times 10^{-27}$ | $1.2 \times 10^{-54}$ m | $4.1 \times 10^{-63}$ s |

## Other Natural Unit Systems

### Quantum Mechanics: $\hbar = 1$

In quantum mechanics, setting $\hbar = 1$ simplifies equations by removing factors of Planck's reduced constant:

```math
\hbar = 1.055 \times 10^{-34} \; \text{J} \cdot \text{s} = 1
```

This equates units of **energy** and **frequency** (or equivalently, **momentum** and **inverse length**):

```math
\hbar = 1 \quad \Rightarrow \quad 1 \text{ Hz} = 1.055 \times 10^{-34} \text{ J} = 6.58 \times 10^{-16} \text{ eV}
```

**Key simplifications with $\hbar = 1$:**

| Equation | SI Units | Natural Units |
|----------|----------|---------------|
| de Broglie relation | $p = \frac{h}{\lambda} = \frac{2\pi\hbar}{\lambda}$ | $p = \frac{2\pi}{\lambda}$ |
| Schrödinger equation | $i\hbar \frac{\partial \psi}{\partial t} = \hat{H}\psi$ | $i \frac{\partial \psi}{\partial t} = \hat{H}\psi$ |
| Commutator | $[\hat{x}, \hat{p}] = i\hbar$ | $[\hat{x}, \hat{p}] = i$ |
| Uncertainty principle | $\Delta x \cdot \Delta p \geq \frac{\hbar}{2}$ | $\Delta x \cdot \Delta p \geq \frac{1}{2}$ |
| Momentum operator | $\hat{p} = -i\hbar \frac{\partial}{\partial x}$ | $\hat{p} = -i \frac{\partial}{\partial x}$ |

**Converting back to SI units:**

| To convert from $\hbar = 1$ | Multiply by |
|-----------------------------|-------------|
| Momentum $\to$ SI | $\hbar$ |
| Angular momentum $\to$ SI | $\hbar$ |
| Energy (from frequency) $\to$ SI | $\hbar$ |
| Inverse length $\to$ momentum | $\hbar$ |

**Example:** The ground state energy of hydrogen

Natural units ($\hbar = 1$, but keeping $m_e$, $e$, and $c$):
```math
E_1 = -\frac{m_e \alpha^2}{2}
```

where $\alpha = e^2/(4\pi\epsilon_0 \hbar c) \approx 1/137$ is the fine structure constant.

In SI units:
```math
E_1 = -\frac{m_e e^4}{2(4\pi\epsilon_0)^2 \hbar^2} = -13.6 \text{ eV}
```

### Particle Physics: $\hbar = c = 1$

Setting both $\hbar = 1$ and $c = 1$ makes energy the fundamental dimension:
- Mass in GeV (since $E = mc^2 \to E = m$)
- Length in GeV$^{-1}$ (since $\lambda = \hbar/p \to \lambda = 1/p$)
- Time in GeV$^{-1}$ (since $t = \hbar/E \to t = 1/E$)

**Useful conversion factors:**

```math
\hbar c = 197.3 \; \text{MeV} \cdot \text{fm}
```

This means:
- $1 \text{ GeV}^{-1} = 0.197 \text{ fm} = 1.97 \times 10^{-16} \text{ m}$ (length)
- $1 \text{ GeV}^{-1} = 6.58 \times 10^{-25} \text{ s}$ (time)
- $1 \text{ GeV} = 1.78 \times 10^{-27} \text{ kg}$ (mass)

### Planck Units: $\hbar = c = G = 1$

The ultimate natural system, defining:

```math
\ell_P = \sqrt{\frac{\hbar G}{c^3}} = 1.6 \times 10^{-35} \text{ m}
```

```math
t_P = \sqrt{\frac{\hbar G}{c^5}} = 5.4 \times 10^{-44} \text{ s}
```

```math
m_P = \sqrt{\frac{\hbar c}{G}} = 2.2 \times 10^{-8} \text{ kg}
```

In Planck units, all three constants equal 1 and quantum gravity effects become order unity.

## Summary

Setting $G = c = 1$:
1. Simplifies equations by removing dimensional constants
2. Unifies mass, length, and time into a single dimension
3. Makes the geometric nature of gravity transparent
4. Requires restoring $G$ and $c$ factors for numerical calculations

The key insight: these constants aren't fundamental physics—they're unit conversion factors between our arbitrary measurement systems.
