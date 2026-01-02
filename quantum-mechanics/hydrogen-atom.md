# The Hydrogen Atom

The hydrogen atom—a single electron bound to a proton—is the cornerstone of atomic physics. It's one of the few exactly solvable systems in [quantum mechanics](quantum-mechanics.md), revealing the quantum numbers that organize the periodic table. The solution requires [vector calculus](../math-foundations/vector-calculus.md) in spherical coordinates, [linear algebra](../math-foundations/linear-algebra.md), and [probability](../math-foundations/probability-statistics.md) for interpreting wave functions. This document uses [spin and angular momentum](spin-angular-momentum.md) and connects to the [Dirac equation](dirac-equation.md) for relativistic corrections.

## The Physical Setup

### The Hamiltonian

In atomic units (see [natural units](../math-foundations/natural-units.md)), or with $\hbar = m_e = e = 4\pi\epsilon_0 = 1$:

```math
\hat{H} = -\frac{1}{2}\nabla^2 - \frac{1}{r}
```

Or in SI units:

```math
\hat{H} = -\frac{\hbar^2}{2m_e}\nabla^2 - \frac{e^2}{4\pi\epsilon_0 r}
```

**What this means:** The electron has kinetic energy (Laplacian term) and is attracted to the proton by the Coulomb potential ($-1/r$). We're using the infinite-proton-mass approximation; the reduced mass correction is small ($m_e \to m_e m_p/(m_e + m_p)$).

### Separation of Variables

In spherical coordinates $(r, \theta, \phi)$, we seek solutions:

```math
\psi(r, \theta, \phi) = R(r) Y_l^m(\theta, \phi)
```

where $Y_l^m$ are spherical harmonics (from [spin-angular-momentum](spin-angular-momentum.md)).

## The Radial Equation

### Standard Form

After separating angular variables, the radial equation is:

```math
-\frac{1}{2}\frac{1}{r^2}\frac{d}{dr}\left(r^2\frac{dR}{dr}\right) + \left[\frac{l(l+1)}{2r^2} - \frac{1}{r}\right]R = ER
```

Substituting $u(r) = rR(r)$:

```math
-\frac{1}{2}\frac{d^2u}{dr^2} + \left[\frac{l(l+1)}{2r^2} - \frac{1}{r}\right]u = Eu
```

**What this means:** This is a 1D Schrödinger equation with an effective potential $V_{eff} = \frac{l(l+1)}{2r^2} - \frac{1}{r}$. The first term is the centrifugal barrier; the second is the Coulomb attraction.

### Asymptotic Behavior

**Large $r$:** For bound states ($E < 0$):
```math
u \sim e^{-\kappa r}, \quad \text{where } \kappa = \sqrt{-2E}
```

**Small $r$:**
```math
u \sim r^{l+1}
```

### Energy Quantization

Demanding normalizable solutions leads to quantized energies:

```math
\boxed{E_n = -\frac{1}{2n^2}} \quad \text{(atomic units)}
```

Or in SI:

```math
\boxed{E_n = -\frac{m_e e^4}{32\pi^2\epsilon_0^2\hbar^2}\frac{1}{n^2} = -\frac{13.6 \text{ eV}}{n^2}}
```

where $n = 1, 2, 3, \ldots$ is the **principal quantum number**.

**What this means:** Energy levels get closer as $n$ increases. The ground state ($n=1$) is 13.6 eV below the ionization threshold. This is the Rydberg formula, explaining atomic spectra.

## Quantum Numbers

Each state is labeled by three quantum numbers:

| Quantum Number | Symbol | Values | Physical Meaning |
|----------------|--------|--------|------------------|
| Principal | $n$ | $1, 2, 3, \ldots$ | Energy, size |
| Orbital | $l$ | $0, 1, \ldots, n-1$ | Angular momentum magnitude |
| Magnetic | $m_l$ | $-l, \ldots, +l$ | Angular momentum z-component |

### Degeneracy

For each $n$, the degeneracy is:

```math
g_n = \sum_{l=0}^{n-1}(2l+1) = n^2
```

Including spin ($m_s = \pm 1/2$):

```math
g_n^{total} = 2n^2
```

**What this means:** The 2s and 2p states have the same energy (without relativistic corrections). This "accidental" degeneracy is due to a hidden symmetry—hydrogen has SO(4) symmetry, not just SO(3).

### Spectroscopic Notation

States are labeled as $nl$ where $l$ is written as a letter:

| $l$ | 0 | 1 | 2 | 3 | 4 |
|-----|---|---|---|---|---|
| Letter | s | p | d | f | g |

Examples: 1s, 2s, 2p, 3s, 3p, 3d, ...

## Wave Functions

### Radial Wave Functions

The radial functions are:

```math
R_{nl}(r) = N_{nl} \left(\frac{2r}{na_0}\right)^l e^{-r/(na_0)} L_{n-l-1}^{2l+1}\left(\frac{2r}{na_0}\right)
```

where:
- $a_0 = \hbar^2/(m_e e^2) \approx 0.529$ Å is the **Bohr radius**
- $L_{n-l-1}^{2l+1}$ are associated Laguerre polynomials
- $N_{nl}$ is a normalization constant

### First Few Radial Functions

**1s ($n=1, l=0$):**
```math
R_{10}(r) = 2\left(\frac{1}{a_0}\right)^{3/2} e^{-r/a_0}
```

**2s ($n=2, l=0$):**
```math
R_{20}(r) = \frac{1}{2\sqrt{2}}\left(\frac{1}{a_0}\right)^{3/2} \left(2 - \frac{r}{a_0}\right) e^{-r/(2a_0)}
```

**2p ($n=2, l=1$):**
```math
R_{21}(r) = \frac{1}{2\sqrt{6}}\left(\frac{1}{a_0}\right)^{3/2} \frac{r}{a_0} e^{-r/(2a_0)}
```

### Probability Density

The probability of finding the electron in a shell at radius $r$:

```math
P(r) = r^2 |R_{nl}(r)|^2
```

The most probable radius for 1s is $r_{max} = a_0$ (the Bohr radius).

**What this means:** The electron isn't at a fixed orbit but is spread out in a probability cloud. The 1s orbital is spherically symmetric; the 2p orbital has a node at the origin and angular structure.

## Complete Wave Functions

```math
\psi_{nlm}(r, \theta, \phi) = R_{nl}(r) Y_l^m(\theta, \phi)
```

### Ground State

```math
\psi_{100} = \frac{1}{\sqrt{\pi}}\left(\frac{1}{a_0}\right)^{3/2} e^{-r/a_0}
```

Spherically symmetric, maximum at the origin.

### First Excited States

**2s:**
```math
\psi_{200} = \frac{1}{4\sqrt{2\pi}}\left(\frac{1}{a_0}\right)^{3/2} \left(2 - \frac{r}{a_0}\right) e^{-r/(2a_0)}
```

**2p ($m=0$):**
```math
\psi_{210} = \frac{1}{4\sqrt{2\pi}}\left(\frac{1}{a_0}\right)^{3/2} \frac{r}{a_0} e^{-r/(2a_0)} \cos\theta
```

**2p ($m=\pm 1$):**
```math
\psi_{21\pm 1} = \mp\frac{1}{8\sqrt{\pi}}\left(\frac{1}{a_0}\right)^{3/2} \frac{r}{a_0} e^{-r/(2a_0)} \sin\theta \, e^{\pm i\phi}
```

## Fine Structure

### Sources of Correction

The fine structure lifts the $l$-degeneracy through three effects (all of order $\alpha^2$):

1. **Relativistic kinetic energy:** The correct relativistic formula $E = \sqrt{p^2c^2 + m^2c^4}$ differs from $E = p^2/(2m)$
2. **Spin-orbit coupling:** $\hat{H}_{SO} = \xi(r)\hat{\mathbf{L}} \cdot \hat{\mathbf{S}}$ (see [spin-angular-momentum](spin-angular-momentum.md))
3. **Darwin term:** Contact interaction at the nucleus (s-states only)

### Combined Result

The fine-structure correction is:

```math
\boxed{E_{nj}^{(1)} = -\frac{\alpha^2}{2n^3}\left(\frac{1}{j+1/2} - \frac{3}{4n}\right) E_1}
```

where:
- $\alpha = e^2/(4\pi\epsilon_0\hbar c) \approx 1/137$ is the fine-structure constant
- $j = l \pm 1/2$ is the total angular momentum

**What this means:** States with the same $n$ but different $j$ have different energies. The 2p level splits into $2p_{1/2}$ and $2p_{3/2}$.

### Fine Structure Energy Levels

```math
E_{nj} = E_n\left[1 + \frac{\alpha^2}{n}\left(\frac{n}{j+1/2} - \frac{3}{4}\right)\right]
```

For $n=2$:
- $2s_{1/2}$ and $2p_{1/2}$: degenerate (same $j=1/2$)
- $2p_{3/2}$: slightly higher energy

## Hyperfine Structure

### The Interaction

The electron's magnetic moment interacts with the proton's magnetic moment:

```math
\hat{H}_{hf} = A \hat{\mathbf{I}} \cdot \hat{\mathbf{S}}
```

where $\hat{\mathbf{I}}$ is the nuclear spin (proton has $I = 1/2$).

### The 21-cm Line

For the 1s ground state, the total spin $F = I + S$ can be:
- $F = 1$ (triplet): spins parallel
- $F = 0$ (singlet): spins antiparallel

The energy splitting:

```math
\Delta E = 5.9 \times 10^{-6} \text{ eV}
```

corresponds to:

```math
\lambda = 21.1 \text{ cm}, \quad \nu = 1420.4 \text{ MHz}
```

**What this means:** This is the famous 21-cm line of neutral hydrogen—essential for radio astronomy. It maps the distribution of hydrogen in the universe.

## Selection Rules

### Allowed Transitions

Electric dipole transitions (the dominant type) obey:

```math
\boxed{\Delta l = \pm 1, \quad \Delta m = 0, \pm 1, \quad \Delta n = \text{any}}
```

**What this means:** Only certain transitions can occur (with high probability). Transitions like $2s \to 1s$ are forbidden by the $\Delta l = \pm 1$ rule—the 2s state is **metastable**.

### Spectral Series

| Series | Final State | Wavelength Range |
|--------|-------------|------------------|
| Lyman | $n = 1$ | Ultraviolet |
| Balmer | $n = 2$ | Visible |
| Paschen | $n = 3$ | Infrared |
| Brackett | $n = 4$ | Infrared |

The Balmer series includes the famous $H_\alpha$ (red), $H_\beta$ (blue-green), $H_\gamma$ (violet) lines.

## The Rydberg Formula

### Transition Frequencies

```math
\boxed{\frac{1}{\lambda} = R_H\left(\frac{1}{n_f^2} - \frac{1}{n_i^2}\right)}
```

where $R_H = 1.097 \times 10^7$ m$^{-1}$ is the Rydberg constant.

**What this means:** This empirical formula, known since 1888, is exactly explained by quantum mechanics. The Rydberg constant is:

```math
R_H = \frac{m_e e^4}{8\epsilon_0^2 h^3 c}
```

## Stark Effect

In an external electric field $\mathbf{E}$:

```math
\hat{H}' = -e\mathbf{E} \cdot \mathbf{r} = eEz
```

### Linear Stark Effect (n > 1)

For degenerate states (like 2s and 2p), first-order perturbation theory gives:

```math
\Delta E = \pm \frac{3}{2}n(n_1 - n_2)a_0 eE
```

**What this means:** Degenerate levels split linearly with field strength. This was one of the first applications of quantum perturbation theory.

### Quadratic Stark Effect (Ground State)

The non-degenerate ground state shifts quadratically:

```math
\Delta E = -\frac{1}{2}\alpha_0 E^2
```

where $\alpha_0 = (9/2)a_0^3$ is the polarizability.

## Zeeman Effect

In an external magnetic field $\mathbf{B}$:

```math
\hat{H}' = \frac{\mu_B}{\hbar}(\hat{L}_z + g_s\hat{S}_z)B
```

See [spin-angular-momentum](spin-angular-momentum.md) for details.

### Normal Zeeman Effect (No Spin)

If spin is ignored, levels split into $2l+1$ equally spaced sublevels:

```math
\Delta E = m_l \mu_B B
```

### Anomalous Zeeman Effect (With Spin)

Including spin, the splitting depends on both $m_l$ and $m_s$, leading to more complex patterns characterized by the Landé g-factor.

## Relativistic Treatment

### The Dirac Equation Solution

The [Dirac equation](dirac-equation.md) gives the exact energy levels for hydrogen:

```math
\boxed{E_{nj} = m_e c^2 \left[1 + \frac{\alpha^2}{\left(n - j - \frac{1}{2} + \sqrt{(j+\frac{1}{2})^2 - \alpha^2}\right)^2}\right]^{-1/2}}
```

Expanding in $\alpha$:

```math
E_{nj} \approx m_e c^2 - \frac{13.6 \text{ eV}}{n^2} - \frac{13.6 \text{ eV} \cdot \alpha^2}{n^4}\left(\frac{n}{j+1/2} - \frac{3}{4}\right) + \cdots
```

**What this means:** The Dirac equation naturally incorporates spin and gives the fine structure exactly. It predicts $2s_{1/2}$ and $2p_{1/2}$ are exactly degenerate—the Lamb shift (a QED effect) actually breaks this degeneracy.

## Worked Examples

### Example 1: Transition Rate for Lyman-α

Calculate the spontaneous emission rate for the 2p → 1s transition (Lyman-α line).

**Solution:**

The spontaneous emission rate is given by:
```math
A_{21} = \frac{\omega^3}{3\pi\epsilon_0\hbar c^3}|\langle 1s|e\mathbf{r}|2p\rangle|^2
```

For the 2p → 1s transition, we need the dipole matrix element. Using $|2p, m=0\rangle$:
```math
\langle 1s|z|2p_0\rangle = \int_0^\infty R_{10}^* r R_{21} r^2 dr \int Y_0^{0*} \cos\theta Y_1^0 d\Omega
```

The angular integral gives $\sqrt{1/3}$. The radial integral:
```math
\int_0^\infty R_{10} r R_{21} r^2 dr = \frac{2^7}{3^5}\sqrt{6} \, a_0 = 1.29 \, a_0
```

Combined: $|\langle 1s|\mathbf{r}|2p\rangle|^2 = 3 \times (1.29 \, a_0/\sqrt{3})^2 = 1.67 \, a_0^2$

The transition energy: $\hbar\omega = 13.6(1 - 1/4) = 10.2$ eV, so $\omega = 1.55 \times 10^{16}$ rad/s.

```math
A_{21} = \frac{(1.55 \times 10^{16})^3}{3\pi\epsilon_0\hbar c^3} \times e^2 \times 1.67 a_0^2 \approx 6.3 \times 10^8 \text{ s}^{-1}
```

The lifetime: $\tau = 1/A_{21} \approx 1.6$ ns.

The wavelength: $\lambda = hc/\Delta E = 121.6$ nm (far UV).

---

### Example 2: Expectation Value of 1/r

Find $\langle 1/r \rangle$ for the ground state of hydrogen.

**Solution:**

For the 1s state: $\psi_{100} = \frac{1}{\sqrt{\pi}a_0^{3/2}} e^{-r/a_0}$

```math
\langle 1/r \rangle = \int |\psi_{100}|^2 \frac{1}{r} d^3r = \frac{1}{\pi a_0^3} \int_0^\infty e^{-2r/a_0} \frac{1}{r} \cdot 4\pi r^2 dr
```

```math
= \frac{4}{a_0^3} \int_0^\infty r e^{-2r/a_0} dr = \frac{4}{a_0^3} \cdot \frac{a_0^2}{4} = \frac{1}{a_0}
```

```math
\boxed{\langle 1/r \rangle_{1s} = \frac{1}{a_0}}
```

**General formula:** For state $|nlm\rangle$:
```math
\langle 1/r \rangle = \frac{1}{n^2 a_0}
```

This is useful for calculating the average potential energy: $\langle V \rangle = -e^2\langle 1/r \rangle/(4\pi\epsilon_0) = -27.2/n^2$ eV.

---

### Example 3: Stark Effect for n=2

Find the first-order Stark effect energy shifts for the n=2 states in an electric field $\mathbf{E} = E\hat{z}$.

**Solution:**

The perturbation is $\hat{H}' = eEz = eEr\cos\theta$.

The n=2 states are 4-fold degenerate: $|2s\rangle$, $|2p_0\rangle$, $|2p_{+1}\rangle$, $|2p_{-1}\rangle$.

By symmetry, $|2p_{\pm 1}\rangle$ don't couple to other states (wrong $m$ values). We focus on the $|2s\rangle$-$|2p_0\rangle$ subspace.

The matrix element:
```math
\langle 2s|eEr\cos\theta|2p_0\rangle = eE \int R_{20}^* r R_{21} r^2 dr \int Y_0^{0*}\cos\theta Y_1^0 d\Omega
```

Radial integral: $\int_0^\infty R_{20} r R_{21} r^2 dr = -3a_0$

Angular integral: $\int Y_0^0 \cos\theta Y_1^0 d\Omega = \sqrt{1/3}$

```math
\langle 2s|H'|2p_0\rangle = -3eEa_0/\sqrt{3} = -\sqrt{3}eEa_0
```

The 2×2 matrix in the $\{|2s\rangle, |2p_0\rangle\}$ basis:
```math
W = \begin{pmatrix} 0 & -\sqrt{3}eEa_0 \\ -\sqrt{3}eEa_0 & 0 \end{pmatrix}
```

Eigenvalues: $E^{(1)} = \pm\sqrt{3}eEa_0 = \pm 3eEa_0$

```math
\boxed{\Delta E = \pm 3eEa_0}
```

The states split linearly with electric field strength (linear Stark effect).

## Summary

| Quantity | Formula | Meaning |
|----------|---------|---------|
| Energy levels | $E_n = -13.6/n^2$ eV | Quantized binding energy |
| Bohr radius | $a_0 = 0.529$ Å | Characteristic size |
| Quantum numbers | $n, l, m_l, m_s$ | Complete state specification |
| Degeneracy | $2n^2$ | States per energy level |
| Fine structure | $\Delta E \propto \alpha^2$ | Relativistic + spin-orbit |
| Hyperfine | 21-cm line | Nuclear spin interaction |
| Selection rules | $\Delta l = \pm 1$ | Allowed transitions |

**The essential insight:** The hydrogen atom is where quantum mechanics becomes chemistry. The discrete energy levels explain atomic spectra; the quantum numbers $n, l, m$ organize the periodic table; the wave functions describe chemical bonding. The exact solvability makes hydrogen the testing ground for quantum theory, from the Bohr model to the Lamb shift.
