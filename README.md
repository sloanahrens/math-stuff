# Physics Stuff

Mathematical physics notes with LaTeX. 45 interlinked documents covering mathematical foundations through advanced topics.

## Documents

### Mathematical Foundations
| Document | Topic |
|----------|-------|
| [Algebra Primer](math-foundations/algebra-primer.md) | Exponents, logarithms, polynomials, complex numbers |
| [Trigonometry Primer](math-foundations/trigonometry-primer.md) | Unit circle, identities, inverse functions |
| [Euler's Formula](math-foundations/euler-formula.md) | $e^{i\theta} = \cos\theta + i\sin\theta$, applications |
| [Calculus Primer](math-foundations/calculus-primer.md) | Derivatives, integrals, partial derivatives, Taylor series |
| [Vector Calculus](math-foundations/vector-calculus.md) | Gradient, divergence, curl, Laplacian, integral theorems |
| [Linear Algebra](math-foundations/linear-algebra.md) | Vectors, matrices, eigenvalues, inner products |
| [Probability & Statistics](math-foundations/probability-statistics.md) | Distributions, expectation values, central limit theorem |
| [Gaussian Integral](math-foundations/gaussian-integral.md) | The $\int e^{-ax^2}dx$ proof and generalizations |
| [Natural Units](math-foundations/natural-units.md) | Setting $G = c = \hbar = 1$ |
| [Tensor Calculus](math-foundations/tensor-calculus.md) | Indices, metrics, covariant derivatives |
| [Differential Forms](math-foundations/differential-forms.md) | Exterior calculus, Stokes' theorem |
| [Lie Groups](math-foundations/lie-groups.md) | Symmetries, representations, algebras |
| [Complex Analysis](math-foundations/complex-analysis.md) | Contour integrals, residues, conformal maps |
| [Fourier Analysis](math-foundations/fourier-analysis.md) | Fourier series/transforms, convolution, FFT |
| [Special Functions](math-foundations/special-functions.md) | Bessel, Legendre, spherical harmonics, Hermite |
| [Green's Functions](math-foundations/greens-functions.md) | Impulse response, propagators, boundary problems |

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
| [General Relativity](relativity/general-relativity.md) | Equivalence principle, curved spacetime, Einstein equations |
| [Einstein Field Equations](relativity/einstein-field-equations.md) | Full derivation from Einstein-Hilbert action |
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
| [Thermodynamics](thermodynamics/thermodynamics.md) | Laws of thermodynamics, free energies, heat engines |
| [Entropy](thermodynamics/entropy.md) | Boltzmann, Gibbs, Shannon entropy, information connection |
| [Statistical Mechanics](thermodynamics/statistical-mechanics.md) | Ensembles, Fermi-Dirac, Bose-Einstein |

### Information Theory
| Document | Topic |
|----------|-------|
| [Information Theory](information-theory/information-theory.md) | Shannon entropy, mutual information, channel capacity |
| [Data Compression](information-theory/data-compression.md) | Huffman, arithmetic coding, entropy limits |

## Folder Structure

```
physics-stuff/
├── math-foundations/       # All mathematical prerequisites and tools
├── classical-mechanics/    # Lagrangian, Hamiltonian, oscillators
├── relativity/             # Special, general, black holes, cosmology
├── electromagnetism/       # Maxwell equations
├── quantum-mechanics/      # QM, spin, atoms, Dirac
├── thermodynamics/         # Laws, entropy, statistical mechanics
└── information-theory/     # Shannon entropy, compression
```

## How Documents Connect

```
MATHEMATICAL FOUNDATIONS                                            PHYSICS
────────────────────────                                            ───────

Algebra ──► Trigonometry ──► Euler's Formula
     │            │                │
     ▼            ▼                ▼

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

**New to physics math?** Start with the foundations:
- [Algebra Primer](math-foundations/algebra-primer.md) → [Trigonometry Primer](math-foundations/trigonometry-primer.md) → [Euler's Formula](math-foundations/euler-formula.md) → [Calculus Primer](math-foundations/calculus-primer.md) → [Vector Calculus](math-foundations/vector-calculus.md) for differential equations and field theory
- [Linear Algebra](math-foundations/linear-algebra.md) for quantum mechanics and tensors
- [Probability & Statistics](math-foundations/probability-statistics.md) for quantum mechanics and statistical mechanics

**Ready for physics:** Start with [Natural Units](math-foundations/natural-units.md), then choose a track:

| Track | Path |
|-------|------|
| **Quantum** | [Quantum Mechanics](quantum-mechanics/quantum-mechanics.md) → [Spin](quantum-mechanics/spin-angular-momentum.md) → [Hydrogen](quantum-mechanics/hydrogen-atom.md) → [Dirac](quantum-mechanics/dirac-equation.md) |
| **Relativity** | [Special Relativity](relativity/special-relativity.md) → [General Relativity](relativity/general-relativity.md) → [Schwarzschild](relativity/schwarzschild-solution.md) → [Geodesics](relativity/geodesics.md) → [Kerr](relativity/kerr-metric.md) |
| **Classical** | [Newtonian](classical-mechanics/newtonian-mechanics.md) → [Central Forces](classical-mechanics/central-forces.md) → [Lagrangian](classical-mechanics/lagrangian-mechanics.md) → [Hamiltonian](classical-mechanics/hamiltonian-mechanics.md) |
| **EM** | [Electrostatics](electromagnetism/electrostatics.md) → [Maxwell's Equations](electromagnetism/maxwell-equations.md) → [EM Waves](electromagnetism/electromagnetic-waves.md) → [Maxwell Covariant](electromagnetism/maxwell-covariant.md) |
| **Math** | [Complex Analysis](math-foundations/complex-analysis.md) → [Fourier Analysis](math-foundations/fourier-analysis.md) → [Special Functions](math-foundations/special-functions.md) → [Green's Functions](math-foundations/greens-functions.md) |
| **Advanced Math** | [Tensor Calculus](math-foundations/tensor-calculus.md) → [Differential Forms](math-foundations/differential-forms.md) → [Lie Groups](math-foundations/lie-groups.md) |
| **Thermo** | [Thermodynamics](thermodynamics/thermodynamics.md) → [Entropy](thermodynamics/entropy.md) → [Statistical Mechanics](thermodynamics/statistical-mechanics.md) |
| **Information** | [Information Theory](information-theory/information-theory.md) → [Data Compression](information-theory/data-compression.md) ↔ [Entropy](thermodynamics/entropy.md) |

**Advanced topics:** [Gravitational Waves](relativity/gravitational-waves.md), [Black Hole Thermodynamics](relativity/black-hole-thermodynamics.md), [Friedmann Equations](relativity/friedmann-equations.md), [Statistical Mechanics](thermodynamics/statistical-mechanics.md)

## Rendering

GitHub renders LaTeX natively. For local viewing, use VS Code with a math-preview extension.

Example: $ds^2 = -\left(1 - \frac{2M}{r}\right) dt^2 + \left(1 - \frac{2M}{r}\right)^{-1} dr^2 + r^2 d\Omega^2$
