# Physics Stuff

Mathematical physics notes with LaTeX. 34 interlinked documents covering prerequisites through advanced topics.

## Documents

### Prerequisites
| Document | Topic |
|----------|-------|
| [Algebra Primer](prerequisites/algebra-primer.md) | Exponents, logarithms, polynomials, complex numbers |
| [Trigonometry Primer](prerequisites/trigonometry-primer.md) | Unit circle, identities, Euler's formula |
| [Calculus Primer](prerequisites/calculus-primer.md) | Derivatives, integrals, partial derivatives, Taylor series |
| [Vector Calculus](prerequisites/vector-calculus.md) | Gradient, divergence, curl, Laplacian, integral theorems |
| [Linear Algebra](prerequisites/linear-algebra.md) | Vectors, matrices, eigenvalues, inner products |
| [Probability & Statistics](prerequisites/probability-statistics.md) | Distributions, expectation values, central limit theorem |
| [Gaussian Integral](prerequisites/gaussian-integral.md) | The $\int e^{-ax^2}dx$ proof and generalizations |

### Mathematical Foundations
| Document | Topic |
|----------|-------|
| [Natural Units](math-foundations/natural-units.md) | Setting $G = c = \hbar = 1$ |
| [Tensor Calculus](math-foundations/tensor-calculus.md) | Indices, metrics, covariant derivatives |
| [Differential Forms](math-foundations/differential-forms.md) | Exterior calculus, Stokes' theorem |
| [Lie Groups](math-foundations/lie-groups.md) | Symmetries, representations, algebras |

### Classical Mechanics
| Document | Topic |
|----------|-------|
| [Newtonian Mechanics](classical-mechanics/newtonian-mechanics.md) | Newton's laws, forces, energy, momentum |
| [Central Forces](classical-mechanics/central-forces.md) | Kepler problem, orbits, effective potential |
| [Harmonic Oscillator](classical-mechanics/harmonic-oscillator.md) | Classical, quantum, and thermodynamic treatments |
| [Lagrangian Mechanics](classical-mechanics/lagrangian-mechanics.md) | Action principle, Euler-Lagrange, Noether |
| [Hamiltonian Mechanics](classical-mechanics/hamiltonian-mechanics.md) | Phase space, Poisson brackets |
| [Path Integrals](classical-mechanics/path-integrals.md) | Feynman formulation |

### Relativity
| Document | Topic |
|----------|-------|
| [Special Relativity](relativity/special-relativity.md) | Lorentz transformations, 4-vectors |
| [Schwarzschild Solution](relativity/schwarzschild-solution.md) | Non-rotating black holes |
| [Kerr Metric](relativity/kerr-metric.md) | Rotating black holes |
| [Geodesics](relativity/geodesics.md) | Orbits, light bending, ISCO |
| [Gravitational Waves](relativity/gravitational-waves.md) | Linearized gravity, LIGO |
| [Black Hole Thermodynamics](relativity/black-hole-thermodynamics.md) | Hawking radiation, entropy |
| [Friedmann Equations](relativity/friedmann-equations.md) | Cosmology, dark energy |

### Electromagnetism
| Document | Topic |
|----------|-------|
| [Electrostatics](electromagnetism/electrostatics.md) | Coulomb, Gauss, potential, capacitance |
| [Maxwell's Equations](electromagnetism/maxwell-equations.md) | The four equations, differential/integral forms |
| [Electromagnetic Waves](electromagnetism/electromagnetic-waves.md) | Wave equation, polarization, energy |
| [Maxwell Covariant](electromagnetism/maxwell-covariant.md) | Relativistic tensor formulation |

### Quantum Mechanics
| Document | Topic |
|----------|-------|
| [Quantum Mechanics](quantum-mechanics/quantum-mechanics.md) | Wave functions, measurement (extended) |
| [Quantum Math](quantum-mechanics/quantum-math.md) | Equations only (concise) |
| [Spin & Angular Momentum](quantum-mechanics/spin-angular-momentum.md) | Pauli matrices, Clebsch-Gordan |
| [Hydrogen Atom](quantum-mechanics/hydrogen-atom.md) | Exact solution, fine structure |
| [Dirac Equation](quantum-mechanics/dirac-equation.md) | Relativistic QM, spinors, antimatter |

### Thermodynamics
| Document | Topic |
|----------|-------|
| [Statistical Mechanics](thermodynamics/statistical-mechanics.md) | Ensembles, Fermi-Dirac, Bose-Einstein |

## Folder Structure

```
physics-stuff/
├── prerequisites/          # Foundational math
├── math-foundations/       # Advanced mathematical tools
├── classical-mechanics/    # Lagrangian, Hamiltonian, oscillators
├── relativity/             # Special, general, black holes, cosmology
├── electromagnetism/       # Maxwell equations
├── quantum-mechanics/      # QM, spin, atoms, Dirac
└── thermodynamics/         # Statistical mechanics
```

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
- [Algebra Primer](prerequisites/algebra-primer.md) → [Trigonometry Primer](prerequisites/trigonometry-primer.md) → [Calculus Primer](prerequisites/calculus-primer.md) → [Vector Calculus](prerequisites/vector-calculus.md) for differential equations and field theory
- [Linear Algebra](prerequisites/linear-algebra.md) for quantum mechanics and tensors
- [Probability & Statistics](prerequisites/probability-statistics.md) for quantum mechanics and statistical mechanics

**Ready for physics:** Start with [Natural Units](math-foundations/natural-units.md), then choose a track:

| Track | Path |
|-------|------|
| **Quantum** | [Quantum Mechanics](quantum-mechanics/quantum-mechanics.md) → [Spin](quantum-mechanics/spin-angular-momentum.md) → [Hydrogen](quantum-mechanics/hydrogen-atom.md) → [Dirac](quantum-mechanics/dirac-equation.md) |
| **Relativity** | [Special Relativity](relativity/special-relativity.md) → [Schwarzschild](relativity/schwarzschild-solution.md) → [Geodesics](relativity/geodesics.md) → [Kerr](relativity/kerr-metric.md) |
| **Classical** | [Newtonian](classical-mechanics/newtonian-mechanics.md) → [Central Forces](classical-mechanics/central-forces.md) → [Lagrangian](classical-mechanics/lagrangian-mechanics.md) → [Hamiltonian](classical-mechanics/hamiltonian-mechanics.md) |
| **EM** | [Electrostatics](electromagnetism/electrostatics.md) → [Maxwell's Equations](electromagnetism/maxwell-equations.md) → [EM Waves](electromagnetism/electromagnetic-waves.md) → [Maxwell Covariant](electromagnetism/maxwell-covariant.md) |
| **Math** | [Tensor Calculus](math-foundations/tensor-calculus.md) → [Differential Forms](math-foundations/differential-forms.md) → [Lie Groups](math-foundations/lie-groups.md) |

**Advanced topics:** [Gravitational Waves](relativity/gravitational-waves.md), [Black Hole Thermodynamics](relativity/black-hole-thermodynamics.md), [Friedmann Equations](relativity/friedmann-equations.md), [Statistical Mechanics](thermodynamics/statistical-mechanics.md)

## Rendering

GitHub renders LaTeX natively. For local viewing, use VS Code with a math-preview extension.

Example: $ds^2 = -\left(1 - \frac{2M}{r}\right) dt^2 + \left(1 - \frac{2M}{r}\right)^{-1} dr^2 + r^2 d\Omega^2$
