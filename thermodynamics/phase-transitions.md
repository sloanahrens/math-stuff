# Phase Transitions

Matter can exist in different phases—solid, liquid, gas, ferromagnet, superconductor—and transitions between them reveal deep principles of [statistical mechanics](statistical-mechanics.md). This document covers first and second-order transitions, order parameters, mean field theory, critical phenomena, and the renormalization group. Prerequisites: [thermodynamics](thermodynamics.md), [statistical mechanics](statistical-mechanics.md), [entropy](entropy.md).

## Classification of Phase Transitions

### Ehrenfest Classification

**First-order transitions:** First derivatives of free energy are discontinuous.

```math
S = -\left(\frac{\partial G}{\partial T}\right)_P, \quad V = \left(\frac{\partial G}{\partial P}\right)_T
```

- Latent heat: $L = T\Delta S$
- Volume change: $\Delta V \neq 0$
- Examples: melting, boiling, sublimation

**Second-order (continuous) transitions:** First derivatives continuous, second derivatives diverge.

```math
C_P = -T\left(\frac{\partial^2 G}{\partial T^2}\right)_P, \quad \kappa_T = -\frac{1}{V}\left(\frac{\partial^2 G}{\partial P^2}\right)_T
```

- No latent heat
- Examples: ferromagnetic transition, superconducting transition, lambda point of helium

### Modern Classification

**First-order:** Order parameter jumps discontinuously.

**Continuous (critical):** Order parameter goes continuously to zero at the critical point.

## Order Parameters

### Definition

An **order parameter** $\phi$ distinguishes phases:
- $\phi = 0$ in disordered (high-symmetry) phase
- $\phi \neq 0$ in ordered (low-symmetry) phase

### Examples

| System | Order Parameter |
|--------|----------------|
| Ferromagnet | Magnetization $M$ |
| Liquid-gas | Density difference $\rho_L - \rho_G$ |
| Superconductor | Gap $\Delta$ or wave function $\psi$ |
| Superfluid | Condensate wave function |
| Crystal | Density modulation (Fourier component) |

### Symmetry Breaking

The ordered phase has lower symmetry than the Hamiltonian.

**Ferromagnet:** Hamiltonian is rotationally symmetric, but magnetization picks a direction.

```math
H = -J\sum_{\langle ij\rangle}\mathbf{S}_i \cdot \mathbf{S}_j
```

**What this means:** The system spontaneously chooses one of many equivalent ground states.

## Landau Theory

### Free Energy Expansion

Near a continuous transition, expand free energy in powers of order parameter:

```math
\boxed{F = F_0 + a(T)\phi^2 + b\phi^4 + \cdots}
```

where $a(T) = a_0(T - T_c)$ changes sign at the critical temperature $T_c$.

### Minimizing the Free Energy

For $T > T_c$ ($a > 0$): Minimum at $\phi = 0$ (disordered phase).

For $T < T_c$ ($a < 0$): Minima at:

```math
\boxed{\phi = \pm\sqrt{\frac{|a|}{2b}} = \pm\sqrt{\frac{a_0(T_c - T)}{2b}}}
```

The order parameter grows as $(T_c - T)^{1/2}$ below $T_c$.

### First-Order Transitions

If a $\phi^3$ term is allowed (when symmetry permits):

```math
F = F_0 + a\phi^2 - c\phi^3 + b\phi^4
```

This produces a first-order transition with discontinuous jump in $\phi$.

### Landau-Ginzburg Theory

Include spatial variations:

```math
F = \int d^dr \left[\frac{1}{2}(\nabla\phi)^2 + \frac{a}{2}\phi^2 + \frac{b}{4}\phi^4\right]
```

The gradient term penalizes spatial variations, setting a correlation length.

## The Ising Model

### Definition

Spins $s_i = \pm 1$ on a lattice with nearest-neighbor coupling:

```math
H = -J\sum_{\langle ij\rangle} s_i s_j - h\sum_i s_i
```

- $J > 0$: Ferromagnetic (spins want to align)
- $h$: External magnetic field

### Exact Solution (1D)

No phase transition at finite temperature (fluctuations destroy order).

Correlation length diverges as $T \to 0$:

```math
\xi = -\frac{1}{\ln(\tanh(J/k_BT))}
```

### Exact Solution (2D)

Onsager (1944) solved the 2D Ising model:

```math
\boxed{T_c = \frac{2J}{k_B \ln(1 + \sqrt{2})} \approx \frac{2.27J}{k_B}}
```

Below $T_c$: spontaneous magnetization

```math
M = \left(1 - \sinh^{-4}\frac{2J}{k_BT}\right)^{1/8}
```

### 3D Ising

No exact solution. Critical exponents known numerically and from renormalization group.

## Critical Phenomena

### Critical Exponents

Near the critical point $T_c$, thermodynamic quantities show power-law behavior.

Define reduced temperature $t = (T - T_c)/T_c$:

| Quantity | Exponent | Definition |
|----------|----------|------------|
| Order parameter | $\beta$ | $\phi \sim \|t\|^\beta$ for $T < T_c$ |
| Susceptibility | $\gamma$ | $\chi \sim \|t\|^{-\gamma}$ |
| Heat capacity | $\alpha$ | $C \sim \|t\|^{-\alpha}$ |
| Correlation length | $\nu$ | $\xi \sim \|t\|^{-\nu}$ |
| Critical isotherm | $\delta$ | $h \sim \phi^\delta$ at $T = T_c$ |
| Correlation function | $\eta$ | $G(r) \sim r^{-(d-2+\eta)}$ at $T_c$ |

### Scaling Relations

Not all exponents are independent:

```math
\alpha + 2\beta + \gamma = 2
```

```math
\gamma = \beta(\delta - 1)
```

```math
\gamma = \nu(2 - \eta)
```

```math
2 - \alpha = d\nu
```

The last is the **hyperscaling relation** (valid below upper critical dimension).

### Mean Field Values

| Exponent | Mean Field | 2D Ising | 3D Ising |
|----------|------------|----------|----------|
| $\alpha$ | 0 (jump) | 0 (log) | 0.110 |
| $\beta$ | 1/2 | 1/8 | 0.326 |
| $\gamma$ | 1 | 7/4 | 1.237 |
| $\delta$ | 3 | 15 | 4.789 |
| $\nu$ | 1/2 | 1 | 0.630 |
| $\eta$ | 0 | 1/4 | 0.036 |

**What this means:** Mean field theory (like Landau) gives wrong exponents below the upper critical dimension $d_c = 4$. Fluctuations matter.

## Universality

### The Key Insight

```math
\boxed{\text{Critical exponents depend only on dimension } d \text{ and symmetry, not microscopic details}}
```

Systems in the same **universality class** share the same exponents.

### Examples

| Universality Class | Examples |
|-------------------|----------|
| Ising ($n=1$) | Uniaxial ferromagnet, liquid-gas, binary alloy |
| XY ($n=2$) | Planar ferromagnet, superfluid $^4$He |
| Heisenberg ($n=3$) | Isotropic ferromagnet |
| Mean field | Systems above $d_c = 4$ |

### Why Universality?

Near criticality, correlation length $\xi \to \infty$. The system "forgets" microscopic details and only remembers:
- Dimensionality $d$
- Symmetry of order parameter (number of components $n$)
- Range of interactions (short vs long-range)

## The Renormalization Group

### The Idea

Systematically integrate out short-wavelength fluctuations and rescale:

1. **Coarse-grain:** Average over small scales
2. **Rescale:** Restore original lattice spacing
3. **Renormalize:** Adjust coupling constants

### Fixed Points

Under RG flow, coupling constants flow to **fixed points** where the system is scale-invariant.

- **Stable fixed point:** Flows toward it (determines critical behavior)
- **Unstable fixed point:** Flows away (separates phases)

### Critical Exponents from RG

At a fixed point, the linearized RG transformation has eigenvalues $\lambda_i$.

```math
\text{Scaling dimension: } y_i = \frac{\ln\lambda_i}{\ln b}
```

where $b$ is the rescaling factor.

```math
\nu = \frac{1}{y_t}, \quad \beta = \frac{d - y_h}{y_t}
```

where $y_t$ and $y_h$ are the temperature and field scaling dimensions.

### Wilson's Triumph

Ken Wilson showed (Nobel 1982) how RG explains:
- Universality
- Scaling relations
- Corrections to mean field theory
- The upper critical dimension

## Mean Field Theory

### The Approximation

Replace interactions with an average (mean) field:

```math
\mathbf{S}_i \cdot \mathbf{S}_j \approx \langle\mathbf{S}\rangle \cdot \mathbf{S}_j + \mathbf{S}_i \cdot \langle\mathbf{S}\rangle - \langle\mathbf{S}\rangle^2
```

### Self-Consistent Equation

For the Ising model:

```math
m = \tanh\left(\frac{Jzm + h}{k_BT}\right)
```

where $z$ is the coordination number and $m = \langle s\rangle$.

At $h = 0$: Non-trivial solution for $T < T_c = Jz/k_B$.

### When Mean Field Works

Mean field is exact:
- In infinite dimensions
- For infinite-range interactions
- Above the upper critical dimension $d_c = 4$ (for short-range)

Below $d_c$, fluctuations dominate and mean field fails.

### Ginzburg Criterion

Mean field breaks down when fluctuations are comparable to order parameter:

```math
\left(\frac{\delta\phi}{\phi}\right)^2 \sim 1
```

This occurs within a temperature range:

```math
|t| < t_G \sim \left(\frac{T_c}{J^d/k_B}\right)^{4/(4-d)}
```

## Specific Phase Transitions

### Liquid-Gas Critical Point

- Order parameter: $\rho_L - \rho_G$
- Universality class: Ising
- Critical opalescence: density fluctuations scatter light

### Superconductivity

- Order parameter: Cooper pair condensate $\psi$
- BCS mean field theory
- Type I/II distinguished by Ginzburg-Landau parameter
- See connection to [statistical mechanics](statistical-mechanics.md)

### Superfluidity

- Order parameter: Bose-Einstein condensate wave function
- Lambda transition in $^4$He (XY universality)
- Quantized vortices

### Ferromagnetism

- Curie temperature $T_c$
- Heisenberg (3D isotropic) or Ising (uniaxial) universality
- Domains and hysteresis (first-order domain effects)

## Topological Transitions

### Kosterlitz-Thouless Transition

In 2D XY model, no long-range order at any $T > 0$ (Mermin-Wagner theorem).

But there is a transition:
- Low $T$: Bound vortex-antivortex pairs
- High $T$: Free vortices

The transition is infinite-order (all derivatives of free energy continuous).

### Topological Order

Some phases distinguished not by symmetry breaking but by topological properties:
- Quantum Hall states
- Topological insulators
- Spin liquids

## Summary

| Concept | Description |
|---------|-------------|
| First-order transition | Latent heat, discontinuous order parameter |
| Second-order transition | No latent heat, continuous order parameter |
| Order parameter | Distinguishes phases; zero in disordered phase |
| Symmetry breaking | Ordered phase has lower symmetry than Hamiltonian |
| Universality | Same exponents for same $(d, n)$ |
| Correlation length | $\xi \to \infty$ at critical point |

| Theory | Key Feature |
|--------|-------------|
| Landau | Free energy expansion in order parameter |
| Mean field | Replace fluctuations by average |
| Ising model | Exact (2D), paradigm for phase transitions |
| Renormalization group | Coarse-grain and rescale; explains universality |

| Exponent | Symbol | Mean Field | Physical Meaning |
|----------|--------|------------|------------------|
| Order parameter | $\beta$ | 1/2 | How $\phi$ vanishes at $T_c$ |
| Susceptibility | $\gamma$ | 1 | Response to field |
| Heat capacity | $\alpha$ | 0 | Singular part of $C$ |
| Correlation length | $\nu$ | 1/2 | Divergence of $\xi$ |

| Universality Class | $n$ | Examples |
|-------------------|-----|----------|
| Ising | 1 | Ferromagnet, liquid-gas |
| XY | 2 | Superfluid, planar magnet |
| Heisenberg | 3 | Isotropic ferromagnet |

**The essential insight:** Phase transitions reveal the collective behavior of many interacting degrees of freedom. Near critical points, correlation lengths diverge and systems become scale-invariant, leading to universal power-law behavior independent of microscopic details. The renormalization group provides a unifying framework: by systematically integrating out short-wavelength fluctuations, we can understand why universality emerges and calculate critical exponents. Mean field theory captures the essential physics but fails in low dimensions where fluctuations dominate. These concepts connect statistical mechanics to [quantum field theory](../quantum-mechanics/qft-introduction.md), where the RG governs the running of coupling constants, and to [information theory](../information-theory/information-theory.md) through the statistical mechanics of information.
