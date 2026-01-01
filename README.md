# Math Stuff

Mathematical physics notes with LaTeX. 27 interlinked documents covering prerequisites through advanced topics.

## Documents

### Prerequisites
| Document | Topic |
|----------|-------|
| [Calculus Primer](calculus-primer.md) | Derivatives, integrals, partial derivatives, Taylor series |
| [Vector Calculus](vector-calculus.md) | Gradient, divergence, curl, Laplacian, integral theorems |
| [Linear Algebra](linear-algebra.md) | Vectors, matrices, eigenvalues, inner products |
| [Probability & Statistics](probability-statistics.md) | Distributions, expectation values, central limit theorem |
| [Gaussian Integral](gaussian-integral.md) | The $\int e^{-ax^2}dx$ proof and generalizations |

### Mathematical Foundations
| Document | Topic |
|----------|-------|
| [Natural Units](natural-units.md) | Setting $G = c = \hbar = 1$ |
| [Tensor Calculus](tensor-calculus.md) | Indices, metrics, covariant derivatives |
| [Differential Forms](differential-forms.md) | Exterior calculus, Stokes' theorem |
| [Lie Groups](lie-groups.md) | Symmetries, representations, algebras |

### Classical Mechanics
| Document | Topic |
|----------|-------|
| [Harmonic Oscillator](harmonic-oscillator.md) | Classical, quantum, and thermodynamic treatments |
| [Lagrangian Mechanics](lagrangian-mechanics.md) | Action principle, Euler-Lagrange, Noether |
| [Hamiltonian Mechanics](hamiltonian-mechanics.md) | Phase space, Poisson brackets |

### Relativity
| Document | Topic |
|----------|-------|
| [Special Relativity](special-relativity.md) | Lorentz transformations, 4-vectors |
| [Schwarzschild Solution](schwarzschild-solution.md) | Non-rotating black holes |
| [Kerr Metric](kerr-metric.md) | Rotating black holes |
| [Geodesics](geodesics.md) | Orbits, light bending, ISCO |
| [Gravitational Waves](gravitational-waves.md) | Linearized gravity, LIGO |
| [Black Hole Thermodynamics](black-hole-thermodynamics.md) | Hawking radiation, entropy |
| [Friedmann Equations](friedmann-equations.md) | Cosmology, dark energy |

### Electromagnetism
| Document | Topic |
|----------|-------|
| [Maxwell Covariant](maxwell-covariant.md) | Relativistic tensor formulation |

### Quantum Mechanics
| Document | Topic |
|----------|-------|
| [Quantum Mechanics](quantum-mechanics.md) | Wave functions, measurement (extended) |
| [Quantum Math](quantum-math.md) | Equations only (concise) |
| [Spin & Angular Momentum](spin-angular-momentum.md) | Pauli matrices, Clebsch-Gordan |
| [Hydrogen Atom](hydrogen-atom.md) | Exact solution, fine structure |
| [Dirac Equation](dirac-equation.md) | Relativistic QM, spinors, antimatter |
| [Path Integrals](path-integrals.md) | Feynman formulation |

### Thermodynamics
| Document | Topic |
|----------|-------|
| [Statistical Mechanics](statistical-mechanics.md) | Ensembles, Fermi-Dirac, Bose-Einstein |

## How Documents Connect

```
PREREQUISITES                    MATH FOUNDATIONS                    PHYSICS
─────────────                    ────────────────                    ───────

Calculus Primer ──────┬──────► Tensor Calculus ─────┬──────────────► Special Relativity
        │             │              │              │                       │
        ▼             │              ▼              │                       ▼
Vector Calculus ──────┤      Differential Forms     │  Lagrangian ──► Hamiltonian ──► Quantum Mechanics
        │             │              │              │       │              │                  │
        ▼             │              ▼              │       ▼              ▼                  ▼
Linear Algebra ───────┴───────► Lie Groups ─────────┴► Path Integrals ◄── Commutators    Spin/Angular
        │                            │                      │                              Momentum
        ▼                            │                      ▼                                 │
Probability ─────────────────────────┴────────────► Statistical Mechanics ◄───────────────────┤
                                                           │                                 ▼
                                                           ▼                           Hydrogen Atom
                                    Maxwell Covariant    Black Hole Thermodynamics           │
                                                                   ▲                         ▼
                                                                   │                   Dirac Equation
                                                          ┌────────┴────────┐
                                                          │                 │
                                                  Schwarzschild ◄─────► Kerr
                                                          │                 │
                                                          └────────┬────────┘
                                                                   │
                                                               Geodesics
                                                                   │
                                                        ┌──────────┼──────────┐
                                                        ▼          ▼          ▼
                                              Gravitational    Friedmann   Light Bending
                                                  Waves        Equations
```

## Reading Order

**New to physics math?** Start with the prerequisites:
- [Calculus Primer](calculus-primer.md) → [Vector Calculus](vector-calculus.md) for differential equations and field theory
- [Linear Algebra](linear-algebra.md) for quantum mechanics and tensors
- [Probability & Statistics](probability-statistics.md) for quantum mechanics and statistical mechanics

**Ready for physics:** Start with [Natural Units](natural-units.md), then choose a track:

| Track | Path |
|-------|------|
| **Quantum** | [Quantum Mechanics](quantum-mechanics.md) → [Spin](spin-angular-momentum.md) → [Hydrogen](hydrogen-atom.md) → [Dirac](dirac-equation.md) |
| **Relativity** | [Special Relativity](special-relativity.md) → [Schwarzschild](schwarzschild-solution.md) → [Geodesics](geodesics.md) → [Kerr](kerr-metric.md) |
| **Classical** | [Lagrangian](lagrangian-mechanics.md) → [Hamiltonian](hamiltonian-mechanics.md) → [Path Integrals](path-integrals.md) |
| **Math** | [Tensor Calculus](tensor-calculus.md) → [Differential Forms](differential-forms.md) → [Lie Groups](lie-groups.md) |

**Advanced topics:** [Gravitational Waves](gravitational-waves.md), [Black Hole Thermodynamics](black-hole-thermodynamics.md), [Friedmann Equations](friedmann-equations.md), [Statistical Mechanics](statistical-mechanics.md)

## Rendering

GitHub renders LaTeX natively. For local viewing, use VS Code with a math-preview extension.

Example: $ds^2 = -\left(1 - \frac{2M}{r}\right) dt^2 + \left(1 - \frac{2M}{r}\right)^{-1} dr^2 + r^2 d\Omega^2$
