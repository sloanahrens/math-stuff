# Math Stuff

Mathematical physics notes with embedded LaTeX.

## Documents

### Mathematical Foundations

| Document | Topic |
|----------|-------|
| [Tensor Calculus](tensor-calculus.md) | Indices, metrics, covariant derivatives, curvature |
| [Differential Forms](differential-forms.md) | Exterior calculus, wedge products, Stokes' theorem |
| [Lie Groups & Algebras](lie-groups.md) | Continuous symmetries, representations, structure constants |

### Classical Mechanics

| Document | Topic |
|----------|-------|
| [Lagrangian Mechanics](lagrangian-mechanics.md) | Principle of least action, Euler-Lagrange equations, Noether's theorem |
| [Hamiltonian Mechanics](hamiltonian-mechanics.md) | Phase space, Poisson brackets, symplectic structure |

### Special Relativity

| Document | Topic |
|----------|-------|
| [Special Relativity](special-relativity.md) | Lorentz transformations, 4-vectors, spacetime intervals |

### General Relativity & Cosmology

| Document | Topic |
|----------|-------|
| [Natural Units](natural-units.md) | Using and converting $G = c = 1$ and $\hbar = 1$ units |
| [Schwarzschild Solution](schwarzschild-solution.md) | Vacuum solution for non-rotating black holes |
| [Kerr Metric](kerr-metric.md) | Rotating black hole spacetime geometry |
| [Geodesics](geodesics.md) | Motion in curved spacetime, orbits, light bending |
| [Gravitational Waves](gravitational-waves.md) | Linearized gravity, polarizations, LIGO detection |
| [Black Hole Thermodynamics](black-hole-thermodynamics.md) | Hawking radiation, entropy, information paradox |
| [Friedmann Equations](friedmann-equations.md) | Cosmology, expansion, dark energy |

### Electromagnetism

| Document | Topic |
|----------|-------|
| [Maxwell Covariant](maxwell-covariant.md) | Maxwell's equations in relativistic tensor form |

### Quantum Mechanics

| Document | Topic |
|----------|-------|
| [Quantum Mechanics](quantum-mechanics.md) | Wave functions, uncertainty, entanglement (with explanations) |
| [Quantum Math](quantum-math.md) | Concise version with equations only |
| [Spin & Angular Momentum](spin-angular-momentum.md) | Orbital and spin angular momentum, Clebsch-Gordan coefficients |
| [Hydrogen Atom](hydrogen-atom.md) | Exact solution, quantum numbers, fine structure |
| [Dirac Equation](dirac-equation.md) | Relativistic quantum mechanics, spinors, antimatter |
| [Path Integrals](path-integrals.md) | Feynman's formulation, propagators, stationary phase |

### Statistical Mechanics

| Document | Topic |
|----------|-------|
| [Statistical Mechanics](statistical-mechanics.md) | Ensembles, partition functions, quantum statistics |

## Document Relationships

```
                    ┌─────────────────────────────────────────────────────────────────┐
                    │                    MATHEMATICAL FOUNDATIONS                      │
                    │                                                                  │
                    │  Tensor Calculus ─────► Differential Forms                       │
                    │        │                      │                                  │
                    │        ▼                      ▼                                  │
                    │  Lie Groups ◄───────── Symmetries ─────► Gauge Theories          │
                    └───┬───────────────────────────────────────────────────────────────┘
                        │
        ┌───────────────┼───────────────────────────────────────┐
        ▼               ▼                                       ▼
┌───────────────┐ ┌─────────────────────────────────────┐ ┌─────────────────┐
│   CLASSICAL   │ │         SPECIAL RELATIVITY          │ │    QUANTUM      │
│               │ │                                     │ │   MECHANICS     │
│ Lagrangian    │ │  4-vectors, Lorentz transformations │ │                 │
│     │         │ │              │                      │ │ Wave functions  │
│     ▼         │ │              │                      │ │      │          │
│ Hamiltonian ──┼─┼──────────────┼──────────────────────┼─┤      ▼          │
│     │         │ │              │                      │ │ Path Integrals  │
│     │         │ │              ▼                      │ │      │          │
│     ▼         │ │       ┌──────┴──────┐               │ │      ▼          │
│ Poisson ≈─────┼─┼───────┤ Commutators ├───────────────┼─► Spin/Angular   │
│ Brackets      │ │       └─────────────┘               │ │ Momentum        │
└───────────────┘ │                                     │ │      │          │
                  │              │                      │ │      ▼          │
                  └──────────────┼──────────────────────┘ │ Hydrogen Atom   │
                                 │                        │      │          │
                                 ▼                        │      ▼          │
                    ┌────────────────────────┐            │ Dirac Equation  │
                    │   GENERAL RELATIVITY   │            └────────┬────────┘
                    │                        │                     │
                    │ Schwarzschild ◄── Kerr │                     │
                    │      │            │    │                     │
                    │      ▼            ▼    │                     │
                    │    Geodesics          │                     │
                    │      │                │                     │
                    │      ▼                │                     ▼
                    │ Gravitational Waves   │            ┌─────────────────┐
                    │                       │            │   STATISTICAL   │
                    │ Black Hole ◄──────────┼────────────│   MECHANICS     │
                    │ Thermodynamics        │            │                 │
                    │      │                │            │  Quantum Stats  │
                    │      ▼                │            │  (Fermi/Bose)   │
                    │ Friedmann Equations   │            └─────────────────┘
                    │ (Cosmology)           │
                    └────────────────────────┘

Maxwell Covariant: Differential Forms + Special Relativity + Tensor Calculus
```

## Prerequisites

Suggested reading order for newcomers:

1. **Start here:** [Natural Units](natural-units.md) → [Special Relativity](special-relativity.md)
2. **Classical foundations:** [Lagrangian](lagrangian-mechanics.md) → [Hamiltonian](hamiltonian-mechanics.md)
3. **Math tools:** [Tensor Calculus](tensor-calculus.md) → [Lie Groups](lie-groups.md)
4. **Quantum track:** [Quantum Mechanics](quantum-mechanics.md) → [Spin](spin-angular-momentum.md) → [Hydrogen](hydrogen-atom.md) → [Dirac](dirac-equation.md)
5. **GR track:** [Schwarzschild](schwarzschild-solution.md) → [Geodesics](geodesics.md) → [Kerr](kerr-metric.md) → [Gravitational Waves](gravitational-waves.md)
6. **Advanced:** [Path Integrals](path-integrals.md), [Black Hole Thermodynamics](black-hole-thermodynamics.md), [Friedmann Equations](friedmann-equations.md)

## LaTeX Rendering

These documents use LaTeX for mathematical notation. To view rendered equations:

- **VS Code**: Use Markdown preview (`Cmd+Shift+V`) with a math-supporting extension
- **GitHub**: Renders LaTeX natively in markdown files

### Examples

Inline math: $E = mc^2$

Block math (Schwarzschild metric):

$$
ds^2 = -\left(1 - \frac{2M}{r}\right) dt^2 + \left(1 - \frac{2M}{r}\right)^{-1} dr^2 + r^2 d\Omega^2
$$

Matrix (Minkowski metric):

```math
g_{\mu\nu} = \begin{pmatrix} -1 & 0 & 0 & 0 \\ 0 & 1 & 0 & 0 \\ 0 & 0 & r^2 & 0 \\ 0 & 0 & 0 & r^2\sin^2\theta \end{pmatrix}
```
