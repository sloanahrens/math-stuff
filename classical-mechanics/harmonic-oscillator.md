# The Harmonic Oscillator

$$
\boxed{\ddot{x} + \omega^2 x = 0}
$$

The harmonic oscillator equation is arguably the most important equation in physics. It describes springs, pendulums, molecular vibrations, electromagnetic waves, quantum fields, and much more. This document covers its solutions and ubiquitous applications. It requires [calculus](../math-foundations/calculus-primer.md) and connects to [Lagrangian mechanics](lagrangian-mechanics.md), [Hamiltonian mechanics](hamiltonian-mechanics.md), [quantum mechanics](../quantum-mechanics/quantum-mechanics.md), and [statistical mechanics](../thermodynamics/statistical-mechanics.md).

## Why It's Everywhere

### Taylor Expansion of Any Potential

Near a stable equilibrium at $x_0$, any potential $V(x)$ can be expanded:

$$
V(x) = V(x_0) + V'(x_0)(x - x_0) + \frac{1}{2}V''(x_0)(x - x_0)^2 + \cdots
$$

At equilibrium, $V'(x_0) = 0$ (no force). For stability, $V''(x_0) > 0$. Ignoring constants and higher terms:

$$
V(x) \approx \frac{1}{2}k(x - x_0)^2 \quad \text{where } k = V''(x_0)
$$

**What this means:** Near any stable equilibrium, the potential is approximately quadratic. Small oscillations around equilibrium are always harmonic. This is why the harmonic oscillator appears everywhere—it's the universal approximation for small deviations from equilibrium.

## Classical Harmonic Oscillator

### The Equation of Motion

For a mass $m$ attached to a spring with constant $k$:

$$
F = -kx \quad \Rightarrow \quad m\ddot{x} = -kx
$$

Defining $\omega = \sqrt{k/m}$:

$$
\ddot{x} + \omega^2 x = 0
$$

### General Solution

The general solution is:

$$
\boxed{x(t) = A\cos(\omega t + \phi)}
$$

or equivalently:

$$
x(t) = C_1 \cos(\omega t) + C_2 \sin(\omega t)
$$

or in complex form:

$$
x(t) = \text{Re}\left[A e^{i(\omega t + \phi)}\right]
$$

**Parameters:**
- $A$ = amplitude (maximum displacement)
- $\omega$ = angular frequency (radians/second)
- $\phi$ = phase
- $T = 2\pi/\omega$ = period
- $f = \omega/(2\pi)$ = frequency (Hz)

### Energy

**Kinetic energy:**
$$
T = \frac{1}{2}m\dot{x}^2 = \frac{1}{2}m\omega^2 A^2 \sin^2(\omega t + \phi)
$$

**Potential energy:**
$$
V = \frac{1}{2}kx^2 = \frac{1}{2}k A^2 \cos^2(\omega t + \phi)
$$

**Total energy:**
$$
E = T + V = \frac{1}{2}kA^2 = \frac{1}{2}m\omega^2 A^2 = \text{constant}
$$

**What this means:** Energy oscillates between kinetic and potential, but the total is conserved. When $x$ is maximum, all energy is potential; when $x = 0$, all energy is kinetic.

### Phase Space

In [Hamiltonian mechanics](hamiltonian-mechanics.md), the state is $(x, p)$ where $p = m\dot{x}$. The Hamiltonian is:

$$
H = \frac{p^2}{2m} + \frac{1}{2}m\omega^2 x^2
$$

Trajectories in phase space are ellipses:

$$
\frac{x^2}{A^2} + \frac{p^2}{(m\omega A)^2} = 1
$$

## Examples of Classical Oscillators

### Mass on a Spring

$$
\omega = \sqrt{\frac{k}{m}}, \quad T = 2\pi\sqrt{\frac{m}{k}}
$$

Heavier masses oscillate slower; stiffer springs oscillate faster.

### Simple Pendulum (Small Angles)

For a pendulum of length $L$, the restoring force is $F = -mg\sin\theta \approx -mg\theta$ for small $\theta$:

$$
mL\ddot{\theta} = -mg\theta \quad \Rightarrow \quad \ddot{\theta} + \frac{g}{L}\theta = 0
$$

$$
\omega = \sqrt{\frac{g}{L}}, \quad T = 2\pi\sqrt{\frac{L}{g}}
$$

**What this means:** The period is independent of mass and amplitude (for small oscillations). This is why pendulums were used in clocks.

### LC Circuit

For an inductor $L$ and capacitor $C$:

$$
L\ddot{Q} + \frac{Q}{C} = 0 \quad \Rightarrow \quad \omega = \frac{1}{\sqrt{LC}}
$$

Charge oscillates between the capacitor's electric field energy and the inductor's magnetic field energy.

### Molecular Vibrations

Diatomic molecules vibrate with frequency:

$$
\omega = \sqrt{\frac{k}{\mu}}
$$

where $\mu = m_1 m_2/(m_1 + m_2)$ is the reduced mass.

## Damped Harmonic Oscillator

### The Equation

Adding a velocity-dependent damping force $-b\dot{x}$:

$$
m\ddot{x} + b\dot{x} + kx = 0
$$

Dividing by $m$ and defining $\gamma = b/(2m)$:

$$
\ddot{x} + 2\gamma\dot{x} + \omega_0^2 x = 0
$$

### Solution

Try $x = e^{\lambda t}$. The characteristic equation is:

$$
\lambda^2 + 2\gamma\lambda + \omega_0^2 = 0 \quad \Rightarrow \quad \lambda = -\gamma \pm \sqrt{\gamma^2 - \omega_0^2}
$$

**Three regimes:**

| Regime | Condition | Behavior |
|--------|-----------|----------|
| Underdamped | $\gamma < \omega_0$ | Oscillates with decaying amplitude |
| Critically damped | $\gamma = \omega_0$ | Fastest return without oscillation |
| Overdamped | $\gamma > \omega_0$ | Slow exponential return |

**Underdamped solution** ($\gamma < \omega_0$):

$$
x(t) = A e^{-\gamma t} \cos(\omega' t + \phi)
$$

where $\omega' = \sqrt{\omega_0^2 - \gamma^2}$ is the damped frequency.

**What this means:** The amplitude decays exponentially while the system oscillates at a slightly lower frequency. This describes shock absorbers, swinging doors, and many real oscillators.

### Quality Factor

The **Q-factor** measures how underdamped a system is:

$$
Q = \frac{\omega_0}{2\gamma}
$$

- $Q \gg 1$: oscillates many times before damping out (tuning fork, laser cavity)
- $Q \sim 1$: critically damped (door closer)
- $Q \ll 1$: overdamped

Energy decays as $E(t) = E_0 e^{-2\gamma t} = E_0 e^{-\omega_0 t/Q}$.

## Driven Harmonic Oscillator

### The Equation

Adding a periodic driving force $F_0 \cos(\omega_d t)$:

$$
\ddot{x} + 2\gamma\dot{x} + \omega_0^2 x = \frac{F_0}{m}\cos(\omega_d t)
$$

### Steady-State Solution

After transients decay, the system oscillates at the driving frequency:

$$
x(t) = A(\omega_d) \cos(\omega_d t - \delta)
$$

**Amplitude:**
$$
A(\omega_d) = \frac{F_0/m}{\sqrt{(\omega_0^2 - \omega_d^2)^2 + (2\gamma\omega_d)^2}}
$$

**Phase lag:**
$$
\tan\delta = \frac{2\gamma\omega_d}{\omega_0^2 - \omega_d^2}
$$

### Resonance

The amplitude is maximum near $\omega_d = \omega_0$ (resonance):

$$
A_{max} \approx \frac{F_0}{2m\gamma\omega_0} = \frac{QF_0}{m\omega_0^2}
$$

**What this means:** At resonance, the driving force is perfectly synchronized with the natural oscillation. High-Q systems have sharp, tall resonance peaks. This explains why opera singers can shatter wine glasses (matching the glass's resonant frequency) and why soldiers break step on bridges.

## Quantum Harmonic Oscillator

### The Hamiltonian

In [quantum mechanics](../quantum-mechanics/quantum-mechanics.md), the Hamiltonian operator is:

$$
\hat{H} = \frac{\hat{p}^2}{2m} + \frac{1}{2}m\omega^2\hat{x}^2
$$

### Energy Eigenvalues

The allowed energies are quantized:

$$
\boxed{E_n = \hbar\omega\left(n + \frac{1}{2}\right), \quad n = 0, 1, 2, \ldots}
$$

**What this means:** Unlike classical oscillators, quantum oscillators can only have discrete energies, evenly spaced by $\hbar\omega$. The ground state ($n = 0$) has nonzero energy $E_0 = \frac{1}{2}\hbar\omega$—the **zero-point energy**.

### Wave Functions

The wave functions are:

$$
\psi_n(x) = \left(\frac{m\omega}{\pi\hbar}\right)^{1/4} \frac{1}{\sqrt{2^n n!}} H_n\left(\sqrt{\frac{m\omega}{\hbar}}x\right) e^{-m\omega x^2/(2\hbar)}
$$

where $H_n$ are Hermite polynomials:
- $H_0(\xi) = 1$
- $H_1(\xi) = 2\xi$
- $H_2(\xi) = 4\xi^2 - 2$
- $H_3(\xi) = 8\xi^3 - 12\xi$

The Gaussian factor $e^{-m\omega x^2/(2\hbar)}$ is normalized using the [Gaussian integral](../math-foundations/gaussian-integral.md).

### Ladder Operators

Define the **raising** and **lowering** operators:

$$
\hat{a} = \sqrt{\frac{m\omega}{2\hbar}}\left(\hat{x} + \frac{i\hat{p}}{m\omega}\right), \quad \hat{a}^\dagger = \sqrt{\frac{m\omega}{2\hbar}}\left(\hat{x} - \frac{i\hat{p}}{m\omega}\right)
$$

They satisfy:
$$
[\hat{a}, \hat{a}^\dagger] = 1
$$

The Hamiltonian becomes:
$$
\hat{H} = \hbar\omega\left(\hat{a}^\dagger\hat{a} + \frac{1}{2}\right) = \hbar\omega\left(\hat{n} + \frac{1}{2}\right)
$$

where $\hat{n} = \hat{a}^\dagger\hat{a}$ is the **number operator**.

**Action on states:**
$$
\hat{a}|n\rangle = \sqrt{n}|n-1\rangle, \quad \hat{a}^\dagger|n\rangle = \sqrt{n+1}|n+1\rangle
$$

**What this means:** The ladder operators add or remove quanta of energy $\hbar\omega$. This algebraic approach generalizes to quantum field theory, where $\hat{a}^\dagger$ creates particles and $\hat{a}$ destroys them.

### Coherent States

**Coherent states** $|\alpha\rangle$ are eigenstates of $\hat{a}$:

$$
\hat{a}|\alpha\rangle = \alpha|\alpha\rangle
$$

They are the quantum states closest to classical oscillation—minimum uncertainty wave packets that oscillate without spreading.

## Thermodynamics of Oscillators

### Partition Function

In [statistical mechanics](../thermodynamics/statistical-mechanics.md), the quantum oscillator partition function is:

$$
Z = \sum_{n=0}^{\infty} e^{-\beta E_n} = \sum_{n=0}^{\infty} e^{-\beta\hbar\omega(n+1/2)} = \frac{e^{-\beta\hbar\omega/2}}{1 - e^{-\beta\hbar\omega}}
$$

### Average Energy

$$
\langle E \rangle = -\frac{\partial \ln Z}{\partial \beta} = \hbar\omega\left(\frac{1}{e^{\beta\hbar\omega} - 1} + \frac{1}{2}\right) = \hbar\omega\left(\bar{n} + \frac{1}{2}\right)
$$

where $\bar{n} = 1/(e^{\beta\hbar\omega} - 1)$ is the Bose-Einstein occupation number.

### High and Low Temperature Limits

**High temperature** ($k_B T \gg \hbar\omega$):
$$
\langle E \rangle \approx k_B T
$$
This is the classical equipartition result.

**Low temperature** ($k_B T \ll \hbar\omega$):
$$
\langle E \rangle \approx \frac{1}{2}\hbar\omega
$$
Only the ground state is occupied.

**What this means:** Quantum effects matter when $k_B T \lesssim \hbar\omega$. This explains why the heat capacity of solids decreases at low temperatures (Einstein and Debye models).

## Coupled Oscillators and Normal Modes

### Two Coupled Oscillators

For two masses connected by springs:

$$
m\ddot{x}_1 = -kx_1 - k'(x_1 - x_2)
$$
$$
m\ddot{x}_2 = -kx_2 - k'(x_2 - x_1)
$$

### Normal Modes

The system has two **normal modes**—patterns where all parts oscillate at the same frequency:

**Symmetric mode:** $x_1 = x_2$, frequency $\omega_1 = \sqrt{k/m}$

**Antisymmetric mode:** $x_1 = -x_2$, frequency $\omega_2 = \sqrt{(k + 2k')/m}$

General motion is a superposition of normal modes.

**What this means:** Any coupled system of oscillators can be decomposed into independent normal modes. This is the basis of Fourier analysis, phonons in solids, and quantum field theory.

## Applications Across Physics

| Field | System | Equation |
|-------|--------|----------|
| Mechanics | Spring, pendulum | $m\ddot{x} + kx = 0$ |
| Circuits | LC oscillator | $L\ddot{Q} + Q/C = 0$ |
| Optics | EM wave in cavity | $\ddot{E} + \omega^2 E = 0$ |
| Acoustics | Sound wave | $\ddot{p} + c^2 k^2 p = 0$ |
| Molecules | Vibrational mode | $\mu\ddot{r} + kr = 0$ |
| Solids | Phonon | $\ddot{u} + \omega^2(k) u = 0$ |
| QFT | Field mode | $\ddot{\phi}_k + \omega_k^2 \phi_k = 0$ |
| Cosmology | Scalar field | $\ddot{\phi} + 3H\dot{\phi} + m^2\phi = 0$ |

## Worked Examples

### Example 1: Driven Damped Oscillator

A 0.5 kg mass on a spring ($k = 200$ N/m) experiences damping $b = 2$ kg/s and is driven by $F(t) = 10\cos(20t)$ N. Find the steady-state amplitude.

**Solution:**

Natural frequency: $\omega_0 = \sqrt{k/m} = \sqrt{200/0.5} = 20$ rad/s

Damping coefficient: $\gamma = b/(2m) = 2/(2 \times 0.5) = 2$ rad/s

Driving frequency: $\omega_d = 20$ rad/s (at resonance!)

Amplitude formula:
$$
A = \frac{F_0/m}{\sqrt{(\omega_0^2 - \omega_d^2)^2 + (2\gamma\omega_d)^2}}
$$

At resonance ($\omega_d = \omega_0$):
$$
A = \frac{10/0.5}{\sqrt{0 + (2 \times 2 \times 20)^2}} = \frac{20}{80} = 0.25 \text{ m}
$$

Q-factor: $Q = \omega_0/(2\gamma) = 20/4 = 5$

The amplitude at resonance can also be written as $A = QF_0/(m\omega_0^2) = 5 \times 10/(0.5 \times 400) = 0.25$ m. ✓

---

### Example 2: Quantum Oscillator Expectation Values

For the quantum harmonic oscillator in state $|n\rangle$, find $\langle x^2 \rangle$ and $\langle p^2 \rangle$.

**Solution:**

Express $\hat{x}$ and $\hat{p}$ in terms of ladder operators:
$$
\hat{x} = \sqrt{\frac{\hbar}{2m\omega}}(\hat{a} + \hat{a}^\dagger), \quad \hat{p} = i\sqrt{\frac{m\omega\hbar}{2}}(\hat{a}^\dagger - \hat{a})
$$

For $\hat{x}^2$:
$$
\hat{x}^2 = \frac{\hbar}{2m\omega}(\hat{a} + \hat{a}^\dagger)^2 = \frac{\hbar}{2m\omega}(\hat{a}^2 + \hat{a}^{\dagger 2} + \hat{a}\hat{a}^\dagger + \hat{a}^\dagger\hat{a})
$$

Using $\hat{a}\hat{a}^\dagger = \hat{a}^\dagger\hat{a} + 1 = \hat{n} + 1$:
$$
\langle n|\hat{x}^2|n\rangle = \frac{\hbar}{2m\omega}\langle n|2\hat{n} + 1|n\rangle = \frac{\hbar}{2m\omega}(2n + 1)
$$

$$
\boxed{\langle x^2 \rangle = \frac{\hbar(2n+1)}{2m\omega}}
$$

Similarly:
$$
\boxed{\langle p^2 \rangle = \frac{m\omega\hbar(2n+1)}{2}}
$$

Check: $\langle E \rangle = \frac{\langle p^2\rangle}{2m} + \frac{1}{2}m\omega^2\langle x^2\rangle = \frac{\hbar\omega(2n+1)}{4} + \frac{\hbar\omega(2n+1)}{4} = \hbar\omega(n + \frac{1}{2})$ ✓

---

### Example 3: Coupled Pendulums

Two identical pendulums of length $L$ and mass $m$ are coupled by a spring of constant $k$ attached at distance $d$ from the pivot. Find the normal mode frequencies.

**Solution:**

For small angles, the equations of motion are:
$$
mL^2\ddot{\theta}_1 = -mgL\theta_1 - kd^2(\theta_1 - \theta_2)
$$
$$
mL^2\ddot{\theta}_2 = -mgL\theta_2 - kd^2(\theta_2 - \theta_1)
$$

Define $\omega_0^2 = g/L$ and $\omega_c^2 = kd^2/(mL^2)$.

**Symmetric mode** ($\theta_1 = \theta_2$): The coupling term vanishes:
$$
\omega_1 = \omega_0 = \sqrt{g/L}
$$

**Antisymmetric mode** ($\theta_1 = -\theta_2$): The coupling doubles:
$$
\omega_2 = \sqrt{\omega_0^2 + 2\omega_c^2} = \sqrt{\frac{g}{L} + \frac{2kd^2}{mL^2}}
$$

For $L = 1$ m, $m = 0.1$ kg, $k = 10$ N/m, $d = 0.5$ m:
$$
\omega_1 = \sqrt{9.8} = 3.13 \text{ rad/s}
$$
$$
\omega_2 = \sqrt{9.8 + 2 \times 10 \times 0.25/(0.1 \times 1)} = \sqrt{9.8 + 50} = 7.73 \text{ rad/s}
$$

The beat frequency when both modes are excited: $\Delta\omega = \omega_2 - \omega_1 = 4.6$ rad/s.

## Summary

| Aspect | Classical | Quantum |
|--------|-----------|---------|
| Energy | $E = \frac{1}{2}kA^2$ (continuous) | $E_n = \hbar\omega(n + \frac{1}{2})$ (discrete) |
| Ground state | $E = 0$ | $E_0 = \frac{1}{2}\hbar\omega$ |
| State | $(x, p)$ point in phase space | $\psi_n(x)$ wave function |
| Time evolution | $x(t) = A\cos(\omega t + \phi)$ | $\psi_n(x,t) = \psi_n(x)e^{-iE_n t/\hbar}$ |
| Creation/destruction | — | $\hat{a}^\dagger$, $\hat{a}$ operators |

**The essential insight:** The harmonic oscillator is the universal model for small oscillations around equilibrium. Its quantum version, with equally spaced energy levels and ladder operators, provides the template for quantum field theory—where particles are excitations of oscillator modes, created and destroyed by $\hat{a}^\dagger$ and $\hat{a}$.
