# The Dirac Equation

The Dirac equation unifies [quantum mechanics](quantum-mechanics.md) and [special relativity](special-relativity.md), describing spin-1/2 particles like electrons. It predicted antimatter before its discovery and reveals the deep connection between spin and relativity. This document connects to [Lie groups](lie-groups.md) (spinor representations) and [spin angular momentum](spin-angular-momentum.md).

## The Problem with Klein-Gordon

### Relativistic Energy-Momentum

From [special relativity](special-relativity.md), the energy-momentum relation is:

$$
E^2 = p^2c^2 + m^2c^4
$$

In [natural units](natural-units.md) with $c = 1$:

$$
E^2 = p^2 + m^2
$$

### The Klein-Gordon Equation

Applying the quantum replacements $E \to i\hbar\partial_t$ and $\mathbf{p} \to -i\hbar\nabla$ (with $\hbar = 1$):

$$
-\frac{\partial^2 \psi}{\partial t^2} = -\nabla^2 \psi + m^2 \psi
$$

or:

$$
(\Box + m^2)\psi = 0
$$

where $\Box = -\partial_t^2 + \nabla^2$ is the d'Alembertian.

**The problems:**

1. **Negative probability densities:** The probability density $\rho \propto i(\psi^*\partial_t\psi - \psi\partial_t\psi^*)$ can be negative
2. **Second-order in time:** Unlike Schrödinger, requires two initial conditions
3. **Negative energy solutions:** $E = \pm\sqrt{p^2 + m^2}$ includes negative energies

## Dirac's Insight

Dirac sought an equation **first-order in time** that remains Lorentz covariant. He proposed:

$$
i\frac{\partial \psi}{\partial t} = (-i\boldsymbol{\alpha} \cdot \nabla + \beta m)\psi
$$

For this to reproduce $E^2 = p^2 + m^2$, we need:

$$
(i\partial_t)^2 = (-i\boldsymbol{\alpha} \cdot \nabla + \beta m)^2
$$

Expanding:

$$
-\partial_t^2 = -\alpha_i\alpha_j\partial_i\partial_j - im(\alpha_i\beta + \beta\alpha_i)\partial_i + \beta^2 m^2
$$

Comparing with $-\partial_t^2 = -\nabla^2 + m^2$, we require:

$$
\{\alpha_i, \alpha_j\} = 2\delta_{ij}, \quad \{\alpha_i, \beta\} = 0, \quad \beta^2 = 1
$$

where $\{A, B\} = AB + BA$ is the anticommutator.

**What this means:** The $\alpha_i$ and $\beta$ can't be numbers—they must be **matrices**. Dirac found that the minimum size is $4 \times 4$, so $\psi$ must be a 4-component object called a **spinor**.

## The Dirac Equation

### Covariant Form

Using gamma matrices $\gamma^\mu$ (defined below), the Dirac equation is:

$$
\boxed{(i\gamma^\mu\partial_\mu - m)\psi = 0}
$$

or equivalently:

$$
\boxed{(i\not\partial - m)\psi = 0}
$$

where $\not\partial = \gamma^\mu\partial_\mu$ is Feynman slash notation.

**What this means:** This single equation describes a spin-1/2 particle in a relativistically invariant way. The four components of $\psi$ encode both spin states (up/down) and particle/antiparticle.

### Gamma Matrices

The **gamma matrices** satisfy the **Clifford algebra**:

$$
\{\gamma^\mu, \gamma^\nu\} = 2\eta^{\mu\nu}
$$

where $\eta^{\mu\nu} = \text{diag}(-1, 1, 1, 1)$.

In the **Dirac representation**:

$$
\gamma^0 = \begin{pmatrix} I & 0 \\ 0 & -I \end{pmatrix}, \quad
\gamma^i = \begin{pmatrix} 0 & \sigma^i \\ -\sigma^i & 0 \end{pmatrix}
$$

where $I$ is the $2 \times 2$ identity and $\sigma^i$ are the Pauli matrices:

$$
\sigma^1 = \begin{pmatrix} 0 & 1 \\ 1 & 0 \end{pmatrix}, \quad
\sigma^2 = \begin{pmatrix} 0 & -i \\ i & 0 \end{pmatrix}, \quad
\sigma^3 = \begin{pmatrix} 1 & 0 \\ 0 & -1 \end{pmatrix}
$$

### Relation to $\alpha$ and $\beta$

$$
\gamma^0 = \beta, \quad \gamma^i = \beta\alpha^i
$$

## Spinors

### The Dirac Spinor

The wave function $\psi$ is a **4-component spinor**:

$$
\psi = \begin{pmatrix} \psi_1 \\ \psi_2 \\ \psi_3 \\ \psi_4 \end{pmatrix}
$$

It can be written as two 2-component **Weyl spinors**:

$$
\psi = \begin{pmatrix} \phi \\ \chi \end{pmatrix}
$$

**What this means:** The four components aren't four different particles. They encode:
- 2 spin states (up and down)
- 2 energy signs (particle and antiparticle)

### Lorentz Transformation of Spinors

Under a Lorentz transformation $\Lambda$, a spinor transforms as:

$$
\psi(x) \to S(\Lambda)\psi(\Lambda^{-1}x)
$$

where $S(\Lambda)$ is a $4 \times 4$ matrix in the **spinor representation** of the Lorentz group—see [Lie groups](lie-groups.md).

**What this means:** Spinors don't transform like vectors. Under a 360° rotation, a spinor picks up a minus sign: $\psi \to -\psi$. You need 720° to return to the original state. This is the mathematical origin of fermion statistics.

## Plane Wave Solutions

### Positive Energy Solutions

For a free particle with 4-momentum $p^\mu = (E, \mathbf{p})$:

$$
\psi = u(p) e^{-ip \cdot x} = u(p) e^{-i(Et - \mathbf{p}\cdot\mathbf{x})}
$$

The spinor $u(p)$ satisfies:

$$
(\gamma^\mu p_\mu - m)u(p) = 0
$$

There are **two** independent solutions $u^{(1)}$ and $u^{(2)}$, corresponding to spin up and spin down.

### Negative Energy Solutions

$$
\psi = v(p) e^{+ip \cdot x}
$$

where $v(p)$ satisfies:

$$
(\gamma^\mu p_\mu + m)v(p) = 0
$$

Again, two independent solutions $v^{(1)}$ and $v^{(2)}$.

**What this means:** The negative energy solutions can't be ignored—they're essential for consistency. Dirac reinterpreted them as **antiparticles** (positrons for electrons).

## Antimatter

### The Dirac Sea (Historical)

Dirac originally proposed that all negative energy states are filled (the "Dirac sea"). A "hole" in this sea behaves like a positive-energy particle with opposite charge—an antiparticle.

### Modern Interpretation

In quantum field theory, negative energy solutions are reinterpreted as positive energy antiparticles moving forward in time. The positron is the antiparticle of the electron:
- Same mass
- Opposite charge
- Opposite magnetic moment

**What this means:** Antimatter was predicted by the Dirac equation in 1928 and discovered experimentally in 1932 (Anderson's positron). The equation demanded antimatter exist.

## The Adjoint Spinor

Define the **Dirac adjoint**:

$$
\bar{\psi} = \psi^\dagger \gamma^0
$$

This transforms properly under Lorentz transformations, unlike $\psi^\dagger$ alone.

### Bilinear Forms

Important Lorentz-covariant quantities:

| Bilinear | Transformation | Physical Meaning |
|----------|----------------|------------------|
| $\bar{\psi}\psi$ | Scalar | Mass term |
| $\bar{\psi}\gamma^\mu\psi$ | Vector | Current density |
| $\bar{\psi}\gamma^5\psi$ | Pseudoscalar | Parity-odd scalar |
| $\bar{\psi}\gamma^\mu\gamma^5\psi$ | Axial vector | Parity-odd current |

### Probability Current

The conserved current is:

$$
j^\mu = \bar{\psi}\gamma^\mu\psi
$$

with $\partial_\mu j^\mu = 0$.

The probability density:

$$
\rho = j^0 = \psi^\dagger\psi = |\psi_1|^2 + |\psi_2|^2 + |\psi_3|^2 + |\psi_4|^2 \geq 0
$$

**What this means:** Unlike Klein-Gordon, the Dirac equation gives a positive-definite probability density. This was one of Dirac's main motivations.

## Spin

### The Spin Operator

The Dirac equation automatically includes spin. The spin operator is:

$$
\mathbf{S} = \frac{1}{2}\boldsymbol{\Sigma}
$$

where:

$$
\Sigma^i = \begin{pmatrix} \sigma^i & 0 \\ 0 & \sigma^i \end{pmatrix}
$$

### Total Angular Momentum

The orbital angular momentum $\mathbf{L} = \mathbf{r} \times \mathbf{p}$ alone is not conserved. The conserved quantity is:

$$
\mathbf{J} = \mathbf{L} + \mathbf{S}
$$

**What this means:** Spin isn't added by hand—it emerges naturally from requiring a first-order relativistic wave equation. The Dirac equation explains why electrons have spin 1/2.

## Electromagnetic Coupling

### Minimal Coupling

To include electromagnetic interactions, replace:

$$
\partial_\mu \to D_\mu = \partial_\mu + ieA_\mu
$$

where $A_\mu = (\phi, \mathbf{A})$ is the 4-potential and $e$ is the charge.

The Dirac equation becomes:

$$
(i\gamma^\mu D_\mu - m)\psi = 0
$$

or:

$$
[i\gamma^\mu(\partial_\mu + ieA_\mu) - m]\psi = 0
$$

### The Magnetic Moment

Expanding in the non-relativistic limit gives:

$$
H = \frac{(\mathbf{p} - e\mathbf{A})^2}{2m} + e\phi - \frac{e}{2m}\boldsymbol{\sigma} \cdot \mathbf{B}
$$

The last term gives a magnetic moment:

$$
\boldsymbol{\mu} = g_s \frac{e}{2m}\mathbf{S}
$$

with **g-factor**:

$$
\boxed{g_s = 2}
$$

**What this means:** The Dirac equation predicts that electrons have a magnetic moment exactly twice what classical physics would suggest. This was a stunning success—no free parameter.

(Quantum electrodynamics gives small corrections: $g_s = 2.002319...$)

## $\gamma^5$ and Chirality

### The Fifth Gamma Matrix

$$
\gamma^5 = i\gamma^0\gamma^1\gamma^2\gamma^3 = \begin{pmatrix} 0 & I \\ I & 0 \end{pmatrix}
$$

Properties: $(\gamma^5)^2 = I$, $\{\gamma^5, \gamma^\mu\} = 0$.

### Chirality Projection Operators

$$
P_L = \frac{1 - \gamma^5}{2}, \quad P_R = \frac{1 + \gamma^5}{2}
$$

These project onto **left-handed** and **right-handed** components:

$$
\psi_L = P_L\psi, \quad \psi_R = P_R\psi
$$

**What this means:** For massless particles, chirality equals helicity (spin alignment with momentum). The weak force only couples to left-handed particles—chirality is fundamental to the Standard Model.

## Non-Relativistic Limit

In the limit $E \approx m$ (particle nearly at rest), the lower components of the spinor become small, and the Dirac equation reduces to the **Pauli equation**:

$$
i\frac{\partial \psi}{\partial t} = \left[ \frac{(\mathbf{p} - e\mathbf{A})^2}{2m} + e\phi - \frac{e}{m}\mathbf{S} \cdot \mathbf{B} \right] \psi
$$

This is the Schrödinger equation with spin—the bridge to non-relativistic quantum mechanics.

## Summary

| Concept | Expression | Meaning |
|---------|------------|---------|
| Dirac equation | $(i\gamma^\mu\partial_\mu - m)\psi = 0$ | Relativistic equation for spin-1/2 |
| Gamma matrices | $\{\gamma^\mu, \gamma^\nu\} = 2\eta^{\mu\nu}$ | Clifford algebra |
| Spinor | $\psi$ (4 components) | Encodes spin and particle/antiparticle |
| Adjoint | $\bar{\psi} = \psi^\dagger\gamma^0$ | For Lorentz-covariant bilinears |
| Current | $j^\mu = \bar{\psi}\gamma^\mu\psi$ | Conserved probability current |
| g-factor | $g_s = 2$ | Predicted magnetic moment |
| Chirality | $\gamma^5$, $P_{L/R}$ | Left/right-handed projections |

**The essential insight:** The Dirac equation shows that spin is not an add-on but a necessary consequence of combining quantum mechanics with special relativity. It predicted antimatter, explained the electron's magnetic moment, and revealed that spacetime symmetries determine particle properties. The 4-component spinor structure encodes the deep connection between rotation (spin) and Lorentz boosts.
