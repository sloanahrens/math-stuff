# Lie Groups and Lie Algebras

Lie groups are continuous symmetry groups that appear throughout physics—rotations, Lorentz transformations, gauge symmetries. Their infinitesimal structure, encoded in Lie algebras, connects to [Hamiltonian mechanics](../classical-mechanics/hamiltonian-mechanics.md) via Poisson brackets and to [quantum mechanics](../quantum-mechanics/quantum-mechanics.md) via commutators. This document requires [linear algebra](linear-algebra.md) (matrices, exponentials, eigenvalues) and [calculus](calculus-primer.md) (Taylor series). The Lorentz group underlies [special relativity](../relativity/special-relativity.md); SU(2) describes [spin angular momentum](../quantum-mechanics/spin-angular-momentum.md); spinor representations appear in the [Dirac equation](../quantum-mechanics/dirac-equation.md).

## What Is a Lie Group?

A **Lie group** is a group that is also a smooth manifold—you can continuously parametrize its elements and smoothly multiply them.

**What this means:** Think of rotations in 3D. You can smoothly rotate by any angle about any axis. The set of all rotations forms a continuous group, and you can do calculus on it.

### Definition

A Lie group $G$ is:
1. A **group** (has identity, inverses, associative multiplication)
2. A **smooth manifold** (locally looks like $\mathbb{R}^n$)
3. Group operations (multiplication, inversion) are **smooth maps**

### Examples

| Lie Group | Description | Dimension |
|-----------|-------------|-----------|
| $\mathbb{R}$ | Real numbers under addition | 1 |
| $U(1) \cong S^1$ | Complex phases $e^{i\theta}$ under multiplication | 1 |
| $SO(2)$ | Rotations in 2D | 1 |
| $SO(3)$ | Rotations in 3D | 3 |
| $SU(2)$ | Special unitary $2 \times 2$ matrices | 3 |
| $SO(3,1)$ | Lorentz group (special relativity) | 6 |
| $SU(3)$ | Color symmetry of QCD | 8 |

## Matrix Lie Groups

Most important Lie groups are **matrix groups**—groups of invertible matrices.

### General Linear Group

```math
GL(n, \mathbb{R}) = \{ A \in M_n(\mathbb{R}) : \det A \neq 0 \}
```

All invertible $n \times n$ real matrices. Dimension: $n^2$.

### Special Linear Group

```math
SL(n, \mathbb{R}) = \{ A \in GL(n, \mathbb{R}) : \det A = 1 \}
```

Volume-preserving linear transformations. Dimension: $n^2 - 1$.

### Orthogonal Group

```math
O(n) = \{ A \in GL(n, \mathbb{R}) : A^T A = I \}
```

Length-preserving transformations (rotations and reflections). Dimension: $\frac{n(n-1)}{2}$.

### Special Orthogonal Group

```math
SO(n) = \{ A \in O(n) : \det A = 1 \}
```

Rotations only (no reflections). The rotation group in $n$ dimensions.

**What this means:** $SO(3)$ is the group of all rotations in 3D space—fundamental to classical mechanics and [angular momentum in quantum mechanics](../quantum-mechanics/quantum-mechanics.md).

### Unitary Group

```math
U(n) = \{ A \in GL(n, \mathbb{C}) : A^\dagger A = I \}
```

Preserve complex inner products. Dimension: $n^2$.

### Special Unitary Group

```math
SU(n) = \{ A \in U(n) : \det A = 1 \}
```

Dimension: $n^2 - 1$.

**What this means:** $SU(2)$ describes spin-1/2 particles. $SU(3)$ is the gauge group of quantum chromodynamics.

## The Lorentz Group

The **Lorentz group** $SO(3,1)$ preserves the spacetime interval:

```math
ds^2 = -dt^2 + dx^2 + dy^2 + dz^2
```

(in [natural units](natural-units.md) with $c = 1$).

```math
SO(3,1) = \{ \Lambda : \Lambda^T \eta \Lambda = \eta \}
```

where $\eta = \text{diag}(-1, 1, 1, 1)$ is the Minkowski metric.

**What this means:** Lorentz transformations include rotations (3 parameters) and boosts (3 parameters), giving 6 dimensions total. This is the symmetry group of special relativity.

## Lie Algebras: Infinitesimal Structure

The **Lie algebra** $\mathfrak{g}$ of a Lie group $G$ captures the infinitesimal (nearby-identity) structure.

### Definition

For matrix Lie groups, elements near the identity can be written as:

```math
g = I + \epsilon X + O(\epsilon^2)
```

The Lie algebra consists of all such $X$:

```math
\mathfrak{g} = \{ X : e^{tX} \in G \text{ for all } t \in \mathbb{R} \}
```

**What this means:** The Lie algebra is the tangent space at the identity. It's a vector space (you can add and scale elements), and it encodes the local structure of the group.

### The Lie Bracket

The Lie algebra has a **bracket** operation:

```math
[X, Y] = XY - YX
```

(For matrix groups, this is just the commutator.)

**What this means:** The bracket measures how much two infinitesimal transformations fail to commute. It encodes all the group's structure—you can reconstruct the local group from its Lie algebra.

### Properties of the Bracket

| Property | Expression |
|----------|------------|
| Antisymmetry | $[X, Y] = -[Y, X]$ |
| Bilinearity | $[aX + bY, Z] = a[X, Z] + b[Y, Z]$ |
| Jacobi identity | $[X, [Y, Z]] + [Y, [Z, X]] + [Z, [X, Y]] = 0$ |

**What this means:** These are the same properties as [Poisson brackets](../classical-mechanics/hamiltonian-mechanics.md)! This is no coincidence—Poisson brackets make functions on phase space into a Lie algebra.

## Examples of Lie Algebras

### $\mathfrak{so}(3)$: Rotations in 3D

The Lie algebra of $SO(3)$ consists of antisymmetric matrices:

```math
\mathfrak{so}(3) = \{ X \in M_3(\mathbb{R}) : X^T = -X \}
```

Basis (generators):

```math
J_1 = \begin{pmatrix} 0 & 0 & 0 \\ 0 & 0 & -1 \\ 0 & 1 & 0 \end{pmatrix}, \quad
J_2 = \begin{pmatrix} 0 & 0 & 1 \\ 0 & 0 & 0 \\ -1 & 0 & 0 \end{pmatrix}, \quad
J_3 = \begin{pmatrix} 0 & -1 & 0 \\ 1 & 0 & 0 \\ 0 & 0 & 0 \end{pmatrix}
```

The **structure constants** are given by:

```math
[J_i, J_j] = \epsilon_{ijk} J_k
```

where $\epsilon_{ijk}$ is the Levi-Civita symbol.

**What this means:** This is the angular momentum algebra! In [quantum mechanics](../quantum-mechanics/quantum-mechanics.md), $[\hat{L}_i, \hat{L}_j] = i\hbar \epsilon_{ijk} \hat{L}_k$ is the same structure (with an $i\hbar$).

### $\mathfrak{su}(2)$: Special Unitary 2×2

The Lie algebra of $SU(2)$ consists of traceless anti-Hermitian matrices:

```math
\mathfrak{su}(2) = \{ X \in M_2(\mathbb{C}) : X^\dagger = -X, \text{Tr}(X) = 0 \}
```

Basis (Pauli matrices times $i/2$):

```math
T_k = \frac{i}{2} \sigma_k
```

where the Pauli matrices are:

```math
\sigma_1 = \begin{pmatrix} 0 & 1 \\ 1 & 0 \end{pmatrix}, \quad
\sigma_2 = \begin{pmatrix} 0 & -i \\ i & 0 \end{pmatrix}, \quad
\sigma_3 = \begin{pmatrix} 1 & 0 \\ 0 & -1 \end{pmatrix}
```

**What this means:** $\mathfrak{su}(2) \cong \mathfrak{so}(3)$ as Lie algebras—they have the same commutation relations. But $SU(2)$ and $SO(3)$ are different as groups: $SU(2)$ is the double cover of $SO(3)$. This is why spin-1/2 particles need a 360° rotation to return to their original state.

### $\mathfrak{so}(3,1)$: Lorentz Algebra

The Lorentz algebra has 6 generators:
- 3 rotation generators $J_i$
- 3 boost generators $K_i$

Commutation relations:

```math
[J_i, J_j] = \epsilon_{ijk} J_k
```

```math
[J_i, K_j] = \epsilon_{ijk} K_k
```

```math
[K_i, K_j] = -\epsilon_{ijk} J_k
```

**What this means:** Rotations form a subalgebra. Boosts don't close among themselves—boosting in two different directions involves a rotation (Thomas precession).

## The Exponential Map

The **exponential map** connects the Lie algebra to the Lie group:

```math
\exp: \mathfrak{g} \to G, \qquad X \mapsto e^X = \sum_{n=0}^\infty \frac{X^n}{n!}
```

For matrix groups, this is the matrix exponential.

**What this means:** Every element near the identity is the exponential of an algebra element. The algebra element represents an "infinitesimal" transformation, and exponentiation gives the finite transformation.

### Example: Rotations

A rotation by angle $\theta$ about the $z$-axis:

```math
R_z(\theta) = e^{\theta J_3} = \begin{pmatrix} \cos\theta & -\sin\theta & 0 \\ \sin\theta & \cos\theta & 0 \\ 0 & 0 & 1 \end{pmatrix}
```

**What this means:** The generator $J_3$ "generates" rotations about the $z$-axis. Exponentiating $\theta J_3$ gives a rotation by angle $\theta$.

## Representations

A **representation** is a homomorphism from the Lie group (or algebra) to matrices:

```math
\rho: G \to GL(V)
```

**What this means:** A representation tells you how the group acts on a vector space. Different representations describe different types of physical objects.

### Important Representations of $SU(2)$

| Dimension | Spin | Physical Objects |
|-----------|------|------------------|
| 1 | 0 | Scalars (Higgs) |
| 2 | 1/2 | Electrons, quarks |
| 3 | 1 | Photon, W/Z bosons |
| $2j+1$ | $j$ | General spin-$j$ particles |

**What this means:** Spin-1/2 particles transform in the 2-dimensional representation, spin-1 particles in the 3-dimensional representation, etc. The representation theory of Lie groups classifies all possible particle spins.

### Adjoint Representation

Every Lie algebra has an **adjoint representation** where it acts on itself:

```math
\text{ad}_X(Y) = [X, Y]
```

Dimension equals the dimension of the algebra.

**What this means:** Gauge bosons (photons, gluons) transform in the adjoint representation of their gauge group.

## Connection to Physics

### Symmetries and Conservation Laws

By [Noether's theorem](../classical-mechanics/lagrangian-mechanics.md), every continuous symmetry gives a conserved quantity:

| Symmetry Group | Conservation Law |
|----------------|------------------|
| Translations $\mathbb{R}^3$ | Momentum |
| Rotations $SO(3)$ | Angular momentum |
| Time translation $\mathbb{R}$ | Energy |
| $U(1)$ phase | Electric charge |
| $SU(3)$ color | Color charge |

**What this means:** The Lie algebra generators become conserved quantities. Angular momentum operators $\hat{L}_i$ generate rotations and satisfy the $\mathfrak{so}(3)$ algebra.

### Quantum Mechanics

In [quantum mechanics](../quantum-mechanics/quantum-mechanics.md), Lie algebra elements become operators:

```math
[X, Y] = Z \quad \longrightarrow \quad [\hat{X}, \hat{Y}] = i\hbar \hat{Z}
```

The factor of $i\hbar$ makes Hermitian operators from anti-Hermitian algebra elements.

**Example:** Angular momentum operators satisfy:

```math
[\hat{L}_x, \hat{L}_y] = i\hbar \hat{L}_z
```

This is the $\mathfrak{so}(3)$ algebra with the quantum $i\hbar$ factor.

### Gauge Theories

Modern particle physics is built on **gauge symmetries**—local Lie group transformations:

| Theory | Gauge Group | Force |
|--------|-------------|-------|
| Electromagnetism | $U(1)$ | Electromagnetic |
| Weak force | $SU(2)$ | Weak |
| Strong force | $SU(3)$ | Strong (color) |
| Standard Model | $SU(3) \times SU(2) \times U(1)$ | All three |

**What this means:** Each force arises from requiring invariance under a local Lie group transformation. The gauge bosons (photon, W/Z, gluons) live in the adjoint representation.

## Structure Constants

For a basis $\{T_a\}$ of the Lie algebra, the **structure constants** $f_{abc}$ are defined by:

```math
[T_a, T_b] = f_{abc} T_c
```

**What this means:** Structure constants encode all the information about the Lie algebra. They appear in gauge theory Lagrangians and Feynman rules.

### Antisymmetry

```math
f_{abc} = -f_{bac}
```

### Jacobi Identity Constraint

```math
f_{abe} f_{ecd} + f_{bce} f_{ead} + f_{cae} f_{ebd} = 0
```

## Summary

| Concept | Definition | Physical Meaning |
|---------|------------|------------------|
| Lie group | Continuous group + smooth manifold | Continuous symmetry |
| Lie algebra | Tangent space at identity | Infinitesimal transformations |
| Bracket $[X,Y]$ | $XY - YX$ | Non-commutativity of transformations |
| Exponential map | $e^X$ | Finite transformation from infinitesimal |
| Representation | Homomorphism to matrices | How objects transform |
| Structure constants | $[T_a, T_b] = f_{abc} T_c$ | Encode algebra structure |

**The essential insight:** Lie groups describe continuous symmetries in physics. Their infinitesimal structure—the Lie algebra—appears as commutators in quantum mechanics and Poisson brackets in classical mechanics. The representation theory of Lie groups classifies all possible particle types and explains the structure of gauge theories.
