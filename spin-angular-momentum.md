# Spin and Angular Momentum

Angular momentum in quantum mechanics comes in two varieties: orbital (from motion) and spin (intrinsic). This document develops both, their addition, and the deep connection to [Lie groups](lie-groups.md). It provides essential background for the [Dirac equation](dirac-equation.md) and [hydrogen atom](hydrogen-atom.md).

## Orbital Angular Momentum

### Classical to Quantum

In classical mechanics, angular momentum is $\mathbf{L} = \mathbf{r} \times \mathbf{p}$. In [quantum mechanics](quantum-mechanics.md), we promote this to operators:

$$
\hat{L}_i = \epsilon_{ijk} \hat{x}_j \hat{p}_k
$$

or explicitly:

$$
\hat{L}_x = \hat{y}\hat{p}_z - \hat{z}\hat{p}_y, \quad \hat{L}_y = \hat{z}\hat{p}_x - \hat{x}\hat{p}_z, \quad \hat{L}_z = \hat{x}\hat{p}_y - \hat{y}\hat{p}_x
$$

### Commutation Relations

Using $[\hat{x}_i, \hat{p}_j] = i\hbar\delta_{ij}$, we find:

$$
\boxed{[\hat{L}_i, \hat{L}_j] = i\hbar\epsilon_{ijk}\hat{L}_k}
$$

or equivalently:

$$
[\hat{L}_x, \hat{L}_y] = i\hbar\hat{L}_z \quad \text{(and cyclic permutations)}
$$

**What this means:** You cannot simultaneously know all three components of angular momentum. Measuring $L_x$ disturbs $L_y$ and $L_z$. This is not a limitation of measurement—it's how quantum angular momentum fundamentally works.

### The Total Angular Momentum Operator

$$
\hat{L}^2 = \hat{L}_x^2 + \hat{L}_y^2 + \hat{L}_z^2
$$

This commutes with all components:

$$
[\hat{L}^2, \hat{L}_i] = 0
$$

**What this means:** We can simultaneously know $L^2$ (the total angular momentum) and one component (conventionally $L_z$). These form a complete set of commuting observables for angular momentum.

### Eigenvalues

The simultaneous eigenstates $|l, m\rangle$ satisfy:

$$
\boxed{\hat{L}^2 |l, m\rangle = \hbar^2 l(l+1) |l, m\rangle}
$$

$$
\boxed{\hat{L}_z |l, m\rangle = \hbar m |l, m\rangle}
$$

where:
- $l = 0, 1, 2, 3, \ldots$ (orbital quantum number)
- $m = -l, -l+1, \ldots, l-1, l$ (magnetic quantum number)

**What this means:** Angular momentum is quantized. The total angular momentum squared takes values $\hbar^2 l(l+1)$, not $\hbar^2 l^2$ as you might naively expect. The z-component can take $2l+1$ values.

### Ladder Operators

Define raising and lowering operators:

$$
\hat{L}_+ = \hat{L}_x + i\hat{L}_y, \quad \hat{L}_- = \hat{L}_x - i\hat{L}_y
$$

These satisfy:

$$
[\hat{L}_z, \hat{L}_\pm] = \pm\hbar\hat{L}_\pm, \quad [\hat{L}_+, \hat{L}_-] = 2\hbar\hat{L}_z
$$

Acting on eigenstates:

$$
\hat{L}_\pm |l, m\rangle = \hbar\sqrt{l(l+1) - m(m\pm 1)} |l, m \pm 1\rangle
$$

**What this means:** The ladder operators step between $m$ values while keeping $l$ fixed. They're zero at the ends ($m = \pm l$), which is why $m$ is bounded.

### Spherical Harmonics

In position space, the eigenfunctions are the **spherical harmonics** $Y_l^m(\theta, \phi)$:

$$
\hat{L}^2 Y_l^m = \hbar^2 l(l+1) Y_l^m, \quad \hat{L}_z Y_l^m = \hbar m Y_l^m
$$

The first few:

$$
Y_0^0 = \frac{1}{\sqrt{4\pi}}, \quad Y_1^0 = \sqrt{\frac{3}{4\pi}}\cos\theta, \quad Y_1^{\pm 1} = \mp\sqrt{\frac{3}{8\pi}}\sin\theta \, e^{\pm i\phi}
$$

**What this means:** The spherical harmonics are the angular wave functions of particles with definite angular momentum. They appear everywhere—atomic orbitals, multipole expansions, gravitational waves.

## Spin Angular Momentum

### Intrinsic Angular Momentum

Spin is angular momentum with no classical analog—it doesn't come from motion in space. The spin operators $\hat{S}_i$ satisfy the same algebra:

$$
[\hat{S}_i, \hat{S}_j] = i\hbar\epsilon_{ijk}\hat{S}_k
$$

### The Crucial Difference

While orbital angular momentum requires integer $l$, spin allows **half-integer** values:

$$
s = 0, \frac{1}{2}, 1, \frac{3}{2}, 2, \ldots
$$

**What this means:** Electrons, protons, and neutrons have spin $s = 1/2$. Photons have spin $s = 1$. The Higgs boson has spin $s = 0$. Half-integer spins are impossible for orbital motion—they're purely quantum.

### Spin-1/2

For spin-1/2 particles (like electrons), the spin operators are:

$$
\hat{S}_i = \frac{\hbar}{2}\sigma_i
$$

where $\sigma_i$ are the **Pauli matrices**:

$$
\sigma_x = \begin{pmatrix} 0 & 1 \\ 1 & 0 \end{pmatrix}, \quad
\sigma_y = \begin{pmatrix} 0 & -i \\ i & 0 \end{pmatrix}, \quad
\sigma_z = \begin{pmatrix} 1 & 0 \\ 0 & -1 \end{pmatrix}
$$

The eigenstates of $\hat{S}_z$:

$$
|\uparrow\rangle = |+\rangle = \begin{pmatrix} 1 \\ 0 \end{pmatrix}, \quad
|\downarrow\rangle = |-\rangle = \begin{pmatrix} 0 \\ 1 \end{pmatrix}
$$

with eigenvalues $\pm\hbar/2$.

**What this means:** A spin-1/2 particle's spin state is described by a 2-component spinor. Measuring spin along any axis gives only two results: $+\hbar/2$ or $-\hbar/2$. There's no "spin sideways"—just probabilities of up or down.

### Properties of Pauli Matrices

$$
\sigma_i^2 = I, \quad \sigma_i\sigma_j = i\epsilon_{ijk}\sigma_k \quad (i \neq j)
$$

$$
\{\sigma_i, \sigma_j\} = 2\delta_{ij}I, \quad [\sigma_i, \sigma_j] = 2i\epsilon_{ijk}\sigma_k
$$

$$
\text{Tr}(\sigma_i) = 0, \quad \det(\sigma_i) = -1
$$

### Spin in Arbitrary Direction

The operator for spin along direction $\hat{n} = (\sin\theta\cos\phi, \sin\theta\sin\phi, \cos\theta)$:

$$
\hat{S}_n = \hat{\mathbf{S}} \cdot \hat{n} = \frac{\hbar}{2}\begin{pmatrix} \cos\theta & \sin\theta \, e^{-i\phi} \\ \sin\theta \, e^{i\phi} & -\cos\theta \end{pmatrix}
$$

Its eigenstates are:

$$
|+\rangle_n = \begin{pmatrix} \cos(\theta/2) \\ \sin(\theta/2) e^{i\phi} \end{pmatrix}, \quad
|-\rangle_n = \begin{pmatrix} \sin(\theta/2) \\ -\cos(\theta/2) e^{i\phi} \end{pmatrix}
$$

**What this means:** The probability of measuring spin-up along z when the particle is spin-up along $\hat{n}$ is $|\langle +|+\rangle_n|^2 = \cos^2(\theta/2)$.

## Connection to Lie Groups

### Angular Momentum as Generators

The angular momentum operators generate rotations. A rotation by angle $\theta$ about axis $\hat{n}$ is:

$$
\hat{R}(\hat{n}, \theta) = e^{-i\theta \hat{n} \cdot \hat{\mathbf{J}}/\hbar}
$$

where $\hat{\mathbf{J}}$ is the total angular momentum—see [Lie groups](lie-groups.md).

**What this means:** The commutation relations $[J_i, J_j] = i\hbar\epsilon_{ijk}J_k$ are the Lie algebra $\mathfrak{so}(3) \cong \mathfrak{su}(2)$.

### Representations

Different values of $j$ correspond to different **representations** of the rotation group:

| $j$ | Dimension | Name | Physical Example |
|-----|-----------|------|------------------|
| 0 | 1 | Trivial | Scalars (Higgs) |
| 1/2 | 2 | Fundamental | Electron spin |
| 1 | 3 | Adjoint | Photon, Vector fields |
| 3/2 | 4 | | Omega baryon |
| 2 | 5 | | Graviton (hypothetical) |

### Spinor Rotation

For spin-1/2, a rotation by angle $\theta$ about $\hat{n}$:

$$
U(\hat{n}, \theta) = e^{-i\theta \hat{n} \cdot \boldsymbol{\sigma}/2} = \cos\frac{\theta}{2}I - i\sin\frac{\theta}{2}(\hat{n} \cdot \boldsymbol{\sigma})
$$

**Critical result:** A rotation by $2\pi$ gives:

$$
U(\hat{n}, 2\pi) = -I
$$

**What this means:** Rotating a spinor by 360° gives a minus sign—you need 720° to return to the original state. This is the mathematical origin of fermion statistics and is directly connected to the spin-statistics theorem.

## Addition of Angular Momentum

### The Problem

Given two angular momenta $\mathbf{J}_1$ and $\mathbf{J}_2$ with quantum numbers $(j_1, m_1)$ and $(j_2, m_2)$, what are the possible total angular momenta?

### Total Angular Momentum

$$
\hat{\mathbf{J}} = \hat{\mathbf{J}}_1 + \hat{\mathbf{J}}_2
$$

The operators $\hat{J}^2$ and $\hat{J}_z$ commute with $\hat{J}_1^2$ and $\hat{J}_2^2$ (but not with $\hat{J}_{1z}$ or $\hat{J}_{2z}$).

### Allowed Values

$$
\boxed{j = |j_1 - j_2|, |j_1 - j_2| + 1, \ldots, j_1 + j_2 - 1, j_1 + j_2}
$$

and for each $j$:

$$
m = -j, -j+1, \ldots, j-1, j
$$

**What this means:** Two spin-1/2 particles can combine to give total spin $j = 0$ (singlet) or $j = 1$ (triplet). Two spin-1 particles can give $j = 0, 1, 2$.

### Dimension Check

The total number of states must be conserved:

$$
(2j_1 + 1)(2j_2 + 1) = \sum_{j=|j_1-j_2|}^{j_1+j_2}(2j+1)
$$

### Clebsch-Gordan Coefficients

The coupled states $|j, m\rangle$ are related to uncoupled states $|j_1, m_1\rangle|j_2, m_2\rangle$ by:

$$
|j, m\rangle = \sum_{m_1, m_2} C_{j_1 m_1; j_2 m_2}^{j m} |j_1, m_1\rangle|j_2, m_2\rangle
$$

where $C_{j_1 m_1; j_2 m_2}^{j m}$ are the **Clebsch-Gordan coefficients**.

### Selection Rules

The Clebsch-Gordan coefficients vanish unless:

$$
m = m_1 + m_2, \quad |j_1 - j_2| \leq j \leq j_1 + j_2
$$

### Example: Two Spin-1/2 Particles

The four uncoupled states combine into:

**Triplet** ($j = 1$):
$$
|1, 1\rangle = |\uparrow\uparrow\rangle
$$
$$
|1, 0\rangle = \frac{1}{\sqrt{2}}(|\uparrow\downarrow\rangle + |\downarrow\uparrow\rangle)
$$
$$
|1, -1\rangle = |\downarrow\downarrow\rangle
$$

**Singlet** ($j = 0$):
$$
|0, 0\rangle = \frac{1}{\sqrt{2}}(|\uparrow\downarrow\rangle - |\downarrow\uparrow\rangle)
$$

**What this means:** The triplet is symmetric under exchange; the singlet is antisymmetric. This connects directly to the Pauli exclusion principle—identical fermions must be in the antisymmetric singlet if their spatial wave functions are the same.

## Spin-Orbit Coupling

### The Interaction

In atoms, the electron's spin interacts with its orbital motion:

$$
\hat{H}_{SO} = \xi(r) \hat{\mathbf{L}} \cdot \hat{\mathbf{S}}
$$

where $\xi(r) \propto \frac{1}{r}\frac{dV}{dr}$ depends on the central potential.

### Total Angular Momentum

With spin-orbit coupling, $\hat{\mathbf{L}}$ and $\hat{\mathbf{S}}$ are not separately conserved. The conserved quantity is:

$$
\hat{\mathbf{J}} = \hat{\mathbf{L}} + \hat{\mathbf{S}}
$$

### Evaluating $\hat{\mathbf{L}} \cdot \hat{\mathbf{S}}$

Using $\hat{\mathbf{J}}^2 = (\hat{\mathbf{L}} + \hat{\mathbf{S}})^2$:

$$
\hat{\mathbf{L}} \cdot \hat{\mathbf{S}} = \frac{1}{2}(\hat{\mathbf{J}}^2 - \hat{\mathbf{L}}^2 - \hat{\mathbf{S}}^2)
$$

The eigenvalues are:

$$
\langle \hat{\mathbf{L}} \cdot \hat{\mathbf{S}} \rangle = \frac{\hbar^2}{2}[j(j+1) - l(l+1) - s(s+1)]
$$

**What this means:** The energy depends on how $\mathbf{L}$ and $\mathbf{S}$ are aligned. Parallel alignment ($j = l + s$) has higher energy than antiparallel ($j = |l - s|$) for most atoms.

### Fine Structure

For the hydrogen atom, the spin-orbit splitting gives:

$$
\Delta E_{SO} = \frac{E_n \alpha^2}{n} \frac{1}{l(l+1/2)(l+1)}[j(j+1) - l(l+1) - 3/4]
$$

where $\alpha \approx 1/137$ is the fine-structure constant.

**What this means:** This splits the $l > 0$ levels. For example, the 2p level splits into $2p_{1/2}$ and $2p_{3/2}$. See [hydrogen atom](hydrogen-atom.md).

## Magnetic Moments

### Orbital Magnetic Moment

A charged particle with orbital angular momentum has magnetic moment:

$$
\boldsymbol{\mu}_L = -\frac{e}{2m_e}\hat{\mathbf{L}} = -\mu_B \frac{\hat{\mathbf{L}}}{\hbar}
$$

where $\mu_B = e\hbar/(2m_e)$ is the **Bohr magneton**.

### Spin Magnetic Moment

The electron's spin magnetic moment is:

$$
\boldsymbol{\mu}_S = -g_s\frac{e}{2m_e}\hat{\mathbf{S}} = -g_s\mu_B \frac{\hat{\mathbf{S}}}{\hbar}
$$

where $g_s \approx 2$ is the electron g-factor (from the [Dirac equation](dirac-equation.md)).

### Zeeman Effect

In an external magnetic field $\mathbf{B}$:

$$
\hat{H}_B = -\boldsymbol{\mu} \cdot \mathbf{B} = \frac{\mu_B}{\hbar}(\hat{\mathbf{L}} + g_s\hat{\mathbf{S}}) \cdot \mathbf{B}
$$

For $\mathbf{B} = B\hat{z}$:

$$
\hat{H}_B = \frac{\mu_B B}{\hbar}(\hat{L}_z + g_s\hat{S}_z)
$$

**What this means:** A magnetic field splits energy levels according to their $m$ values. This is the Zeeman effect—essential for atomic spectroscopy and MRI.

## Summary

| Concept | Expression | Meaning |
|---------|------------|---------|
| Commutation | $[J_i, J_j] = i\hbar\epsilon_{ijk}J_k$ | Angular momentum algebra |
| Eigenvalues | $J^2 \to \hbar^2 j(j+1)$, $J_z \to \hbar m$ | Quantized angular momentum |
| Orbital $l$ | $l = 0, 1, 2, \ldots$ | Integer values only |
| Spin $s$ | $s = 0, 1/2, 1, 3/2, \ldots$ | Half-integer allowed |
| Pauli matrices | $\sigma_i$ with $\{\sigma_i, \sigma_j\} = 2\delta_{ij}$ | Spin-1/2 operators |
| Addition | $j = |j_1-j_2|, \ldots, j_1+j_2$ | Total angular momentum range |
| Spin-orbit | $\hat{H}_{SO} = \xi(r)\hat{\mathbf{L}} \cdot \hat{\mathbf{S}}$ | Coupling between spin and orbit |
| 360° rotation | $|\psi\rangle \to -|\psi\rangle$ | Spinor sign change |

**The essential insight:** Angular momentum in quantum mechanics reveals the deep connection between rotational symmetry and observable properties. The same algebraic structure—the Lie algebra of SU(2)—governs both orbital and spin angular momentum, but spin allows half-integer representations impossible for classical rotation. This leads to spinor behavior (720° periodicity), the spin-statistics connection, and the rich structure of atomic spectra.
