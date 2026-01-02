# Linear Algebra

Linear algebra is the mathematics of vectors, matrices, and linear transformations. It's the language of [quantum mechanics](../quantum-mechanics/quantum-mechanics.md), essential for understanding [tensors](../math-foundations/tensor-calculus.md), [Lie groups](../math-foundations/lie-groups.md), and the [Dirac equation](../quantum-mechanics/dirac-equation.md). This primer covers the essentials needed for physics.

## Vectors

### Abstract Vectors

A **vector space** is a set of objects that can be added and scaled:

```math
\mathbf{u} + \mathbf{v} \in V, \qquad c\mathbf{v} \in V
```

**What this means:** Vectors aren't just arrows in 3D space. Functions, matrices, and quantum states are all vectors in appropriate vector spaces. This abstraction is powerful.

### Basis and Components

A **basis** $\{\mathbf{e}_1, \mathbf{e}_2, \ldots, \mathbf{e}_n\}$ spans the space. Any vector can be written:

```math
\mathbf{v} = v_1\mathbf{e}_1 + v_2\mathbf{e}_2 + \cdots + v_n\mathbf{e}_n = \sum_i v_i\mathbf{e}_i
```

The numbers $(v_1, v_2, \ldots, v_n)$ are the **components** in this basis.

**What this means:** Components depend on your choice of basis. The vector itself is basis-independent—changing basis just changes how you describe it.

### Linear Independence

Vectors $\{\mathbf{v}_1, \ldots, \mathbf{v}_k\}$ are **linearly independent** if:

```math
c_1\mathbf{v}_1 + c_2\mathbf{v}_2 + \cdots + c_k\mathbf{v}_k = 0 \quad \Rightarrow \quad c_1 = c_2 = \cdots = c_k = 0
```

**What this means:** None of the vectors can be written as a combination of the others. A basis must be linearly independent.

## Inner Products

### Definition

An **inner product** $\langle \mathbf{u}, \mathbf{v} \rangle$ gives a notion of "angle" and "length":

**Properties:**
1. Linearity: $\langle a\mathbf{u} + b\mathbf{v}, \mathbf{w} \rangle = a\langle \mathbf{u}, \mathbf{w} \rangle + b\langle \mathbf{v}, \mathbf{w} \rangle$
2. Conjugate symmetry: $\langle \mathbf{u}, \mathbf{v} \rangle = \langle \mathbf{v}, \mathbf{u} \rangle^*$
3. Positive definite: $\langle \mathbf{v}, \mathbf{v} \rangle \geq 0$, with equality only if $\mathbf{v} = 0$

### Real vs Complex

**Real vectors:** $\langle \mathbf{u}, \mathbf{v} \rangle = \mathbf{u} \cdot \mathbf{v} = \sum_i u_i v_i$

**Complex vectors:** $\langle \mathbf{u}, \mathbf{v} \rangle = \sum_i u_i^* v_i$

**What this means:** For complex vectors (like quantum states), the inner product involves complex conjugation. This ensures $\langle \mathbf{v}, \mathbf{v} \rangle$ is real and non-negative.

### Norm and Orthogonality

**Norm (length):** $|\mathbf{v}| = \sqrt{\langle \mathbf{v}, \mathbf{v} \rangle}$

**Orthogonal:** $\mathbf{u} \perp \mathbf{v}$ if $\langle \mathbf{u}, \mathbf{v} \rangle = 0$

**Orthonormal basis:** $\langle \mathbf{e}_i, \mathbf{e}_j \rangle = \delta_{ij}$

### Dirac Notation

In quantum mechanics, we write:

```math
\langle \psi | \phi \rangle \quad \text{(inner product of states } |\psi\rangle \text{ and } |\phi\rangle)
```

See [quantum mechanics](../quantum-mechanics/quantum-mechanics.md) for details on bra-ket notation.

## Matrices

### Definition

A **matrix** is a rectangular array of numbers. An $m \times n$ matrix has $m$ rows and $n$ columns:

```math
A = \begin{pmatrix} a_{11} & a_{12} & \cdots & a_{1n} \\ a_{21} & a_{22} & \cdots & a_{2n} \\ \vdots & \vdots & \ddots & \vdots \\ a_{m1} & a_{m2} & \cdots & a_{mn} \end{pmatrix}
```

### Matrix Multiplication

For $A$ ($m \times n$) and $B$ ($n \times p$), the product $C = AB$ is $m \times p$:

```math
C_{ij} = \sum_{k=1}^n A_{ik} B_{kj}
```

**What this means:** Matrix multiplication is composition of linear transformations. If $A$ and $B$ represent two operations, $AB$ represents doing $B$ first, then $A$.

**Important:** Matrix multiplication is **not commutative**: $AB \neq BA$ in general.

### Special Matrices

| Type | Definition | Example |
|------|------------|---------|
| Identity | $I_{ij} = \delta_{ij}$ | Does nothing: $AI = IA = A$ |
| Diagonal | $D_{ij} = 0$ for $i \neq j$ | Scales each basis vector |
| Symmetric | $A^T = A$ | Real eigenvalues |
| Antisymmetric | $A^T = -A$ | $A_{ii} = 0$ |
| Orthogonal | $A^T A = I$ | Preserves lengths |
| Hermitian | $A^\dagger = A$ | Quantum observables |
| Unitary | $A^\dagger A = I$ | Quantum evolution |

### Transpose and Hermitian Conjugate

**Transpose:** $(A^T)_{ij} = A_{ji}$

**Complex conjugate:** $(A^*)_{ij} = (A_{ij})^*$

**Hermitian conjugate (adjoint):** $A^\dagger = (A^T)^* = (A^*)^T$

For real matrices, $A^\dagger = A^T$.

## Determinants

### Definition

The **determinant** of a square matrix is a single number encoding whether the matrix is invertible:

**2×2:**
```math
\det\begin{pmatrix} a & b \\ c & d \end{pmatrix} = ad - bc
```

**3×3:**
```math
\det\begin{pmatrix} a & b & c \\ d & e & f \\ g & h & i \end{pmatrix} = a(ei - fh) - b(di - fg) + c(dh - eg)
```

### Properties

- $\det(AB) = \det(A)\det(B)$
- $\det(A^T) = \det(A)$
- $\det(cA) = c^n \det(A)$ for $n \times n$ matrix
- $\det(A) = 0$ if and only if $A$ is singular (non-invertible)
- $\det(A^{-1}) = 1/\det(A)$

**What this means:** The determinant measures how a linear transformation scales volumes. $|\det(A)|$ is the volume scaling factor; the sign indicates orientation (whether handedness is preserved).

### Geometric Interpretation

For a 2×2 matrix mapping the unit square:
- $|\det(A)|$ = area of the parallelogram image
- $\det(A) > 0$: orientation preserved
- $\det(A) < 0$: orientation reversed
- $\det(A) = 0$: collapsed to lower dimension

## Eigenvalues and Eigenvectors

### Definition

An **eigenvector** $\mathbf{v}$ of matrix $A$ satisfies:

```math
\boxed{A\mathbf{v} = \lambda\mathbf{v}}
```

where $\lambda$ is the corresponding **eigenvalue**.

**What this means:** Eigenvectors are special directions that $A$ only stretches (by factor $\lambda$), without rotating. They're the "natural axes" of the transformation.

### Finding Eigenvalues

Eigenvalues satisfy the **characteristic equation**:

```math
\det(A - \lambda I) = 0
```

For a 2×2 matrix:
```math
\det\begin{pmatrix} a - \lambda & b \\ c & d - \lambda \end{pmatrix} = \lambda^2 - (a+d)\lambda + (ad - bc) = 0
```

The sum of eigenvalues equals the **trace**: $\lambda_1 + \lambda_2 = \text{Tr}(A) = a + d$

The product equals the determinant: $\lambda_1 \lambda_2 = \det(A)$

### Properties of Eigenvalues

| Matrix Type | Eigenvalue Property |
|-------------|---------------------|
| Hermitian ($A^\dagger = A$) | Real eigenvalues |
| Unitary ($A^\dagger A = I$) | Eigenvalues on unit circle ($|\lambda| = 1$) |
| Symmetric real | Real eigenvalues, orthogonal eigenvectors |
| Antisymmetric real | Pure imaginary eigenvalues |

### Diagonalization

If $A$ has $n$ linearly independent eigenvectors, it can be **diagonalized**:

```math
A = PDP^{-1}
```

where $D$ is diagonal with eigenvalues, and $P$ has eigenvectors as columns.

**What this means:** In the eigenvector basis, $A$ is just scaling along each axis. This simplifies computations enormously.

### Powers of Matrices

If $A = PDP^{-1}$:

```math
A^n = PD^nP^{-1}
```

And $D^n$ is trivial—just raise each diagonal element to the $n$th power.

## Matrices as Linear Transformations

### The Key Insight

A matrix $A$ defines a **linear transformation**:

```math
T(\mathbf{v}) = A\mathbf{v}
```

**Linearity:** $T(a\mathbf{u} + b\mathbf{v}) = aT(\mathbf{u}) + bT(\mathbf{v})$

The matrix $A$ is determined by how it acts on basis vectors:

```math
A = \begin{pmatrix} | & | & & | \\ T(\mathbf{e}_1) & T(\mathbf{e}_2) & \cdots & T(\mathbf{e}_n) \\ | & | & & | \end{pmatrix}
```

### Change of Basis

If $P$ is the matrix whose columns are a new basis, then a vector $\mathbf{v}$ in the new basis is:

```math
\mathbf{v}_{new} = P^{-1}\mathbf{v}_{old}
```

A transformation $A$ in the new basis is:

```math
A_{new} = P^{-1}AP
```

**What this means:** The same linear transformation looks like different matrices in different bases. Physics should be basis-independent, which leads to tensors—see [tensor calculus](../math-foundations/tensor-calculus.md).

## Matrices in Quantum Mechanics

### Operators as Matrices

In quantum mechanics, observables are **Hermitian operators**. In a discrete basis:

```math
\hat{A} \leftrightarrow A_{ij} = \langle i | \hat{A} | j \rangle
```

**What this means:** Every quantum operator can be represented as a matrix once you choose a basis. The Pauli matrices, Hamiltonians, and angular momentum operators are all matrices.

### The Pauli Matrices

These 2×2 matrices represent spin-1/2:

```math
\sigma_x = \begin{pmatrix} 0 & 1 \\ 1 & 0 \end{pmatrix}, \quad
\sigma_y = \begin{pmatrix} 0 & -i \\ i & 0 \end{pmatrix}, \quad
\sigma_z = \begin{pmatrix} 1 & 0 \\ 0 & -1 \end{pmatrix}
```

See [spin and angular momentum](../quantum-mechanics/spin-angular-momentum.md).

### Hermitian Matrices Have Real Eigenvalues

**Theorem:** If $A^\dagger = A$, all eigenvalues are real.

**Proof:** If $A\mathbf{v} = \lambda\mathbf{v}$, then:
```math
\langle \mathbf{v}, A\mathbf{v} \rangle = \lambda \langle \mathbf{v}, \mathbf{v} \rangle
```
```math
\langle A\mathbf{v}, \mathbf{v} \rangle = \langle \mathbf{v}, A\mathbf{v} \rangle^* = \lambda^* \langle \mathbf{v}, \mathbf{v} \rangle
```
But for Hermitian $A$: $\langle A\mathbf{v}, \mathbf{v} \rangle = \langle \mathbf{v}, A\mathbf{v} \rangle$, so $\lambda = \lambda^*$.

**What this means:** This is why quantum observables must be Hermitian—eigenvalues are measurement outcomes, which must be real.

### Unitary Matrices Preserve Inner Products

**Theorem:** If $U^\dagger U = I$, then $\langle U\mathbf{u}, U\mathbf{v} \rangle = \langle \mathbf{u}, \mathbf{v} \rangle$.

**What this means:** Unitary evolution preserves probabilities in quantum mechanics. This is why time evolution is unitary.

## Trace

### Definition

The **trace** of a square matrix is the sum of diagonal elements:

```math
\text{Tr}(A) = \sum_i A_{ii}
```

### Properties

- $\text{Tr}(A + B) = \text{Tr}(A) + \text{Tr}(B)$
- $\text{Tr}(cA) = c \cdot \text{Tr}(A)$
- $\text{Tr}(AB) = \text{Tr}(BA)$ (cyclic property)
- $\text{Tr}(A) = \sum_i \lambda_i$ (sum of eigenvalues)

**What this means:** The trace is basis-independent. In quantum mechanics, $\text{Tr}(\rho A)$ gives expectation values for density matrix $\rho$.

## Matrix Exponential

### Definition

```math
e^A = I + A + \frac{A^2}{2!} + \frac{A^3}{3!} + \cdots = \sum_{n=0}^\infty \frac{A^n}{n!}
```

### Properties

- $e^0 = I$
- $e^{A+B} = e^A e^B$ **only if** $[A, B] = 0$
- $(e^A)^{-1} = e^{-A}$
- $\det(e^A) = e^{\text{Tr}(A)}$

### Physics Applications

**Quantum time evolution:**
```math
|\psi(t)\rangle = e^{-iHt/\hbar}|\psi(0)\rangle
```

**Rotation matrices:**
```math
R_z(\theta) = e^{-i\theta J_z/\hbar}
```

**Lie groups:** The exponential map connects [Lie algebras to Lie groups](../math-foundations/lie-groups.md).

## Commutators

### Definition

The **commutator** of two matrices:

```math
[A, B] = AB - BA
```

**Properties:**
- $[A, B] = -[B, A]$ (antisymmetric)
- $[A, BC] = [A, B]C + B[A, C]$ (Leibniz rule)
- $[A, [B, C]] + [B, [C, A]] + [C, [A, B]] = 0$ (Jacobi identity)

**What this means:** The commutator measures how much operations fail to commute. In quantum mechanics, $[\hat{x}, \hat{p}] = i\hbar$ is the fundamental commutation relation. See [quantum mechanics](../quantum-mechanics/quantum-mechanics.md).

## Summary

| Concept | Definition | Physics Application |
|---------|------------|---------------------|
| Inner product | $\langle \mathbf{u}, \mathbf{v} \rangle$ | Probability amplitudes |
| Determinant | $\det(A)$ | Volume scaling, invertibility |
| Eigenvalue | $A\mathbf{v} = \lambda\mathbf{v}$ | Measurement outcomes |
| Hermitian | $A^\dagger = A$ | Quantum observables |
| Unitary | $A^\dagger A = I$ | Quantum evolution |
| Trace | $\text{Tr}(A) = \sum_i A_{ii}$ | Expectation values |
| Commutator | $[A, B] = AB - BA$ | Uncertainty principle |
| Matrix exponential | $e^A$ | Time evolution, rotations |

**The essential insight:** Linear algebra is the mathematics of linear transformations. Matrices represent these transformations in a basis; eigenvalues reveal their essential structure. Quantum mechanics is fundamentally linear algebra in infinite-dimensional spaces, which is why these concepts are indispensable for physics.
