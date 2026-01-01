# Quantum Mechanics: An Overview (Extended Edition)

$$
\boxed{i\hbar \frac{\partial \psi}{\partial t} = -\frac{\hbar^2}{2m} \nabla^2 \psi + V \psi}
$$

The **Schrödinger equation**—the master equation of quantum mechanics. It governs how the wave function $\psi$ evolves in time, where $\hbar = 1.055 \times 10^{-34}$ J·s is Planck's reduced constant, $m$ is the particle mass, and $V$ is the potential energy.

---

This document covers the core mathematical framework of quantum mechanics and how different interpretations address the measurement problem. We use [natural units](natural-units.md) where $\hbar = 1$. The formalism connects deeply to [Hamiltonian mechanics](hamiltonian-mechanics.md) (Poisson brackets become commutators) and [Lie groups](lie-groups.md) (symmetries determine particle types).

This extended version includes physical explanations for readers less familiar with the mathematical formalism.

## The Wave Function

The **wave function** $\psi(x, t)$ is the fundamental object in quantum mechanics. It encodes everything knowable about a quantum system.

For a single particle in one dimension:

$$
\psi: \mathbb{R} \times \mathbb{R} \to \mathbb{C}
$$

**What this means:** The wave function takes a position $x$ and time $t$ as inputs, and outputs a complex number. You can think of it as a "field" that exists everywhere in space, with a value at each point. The complex number contains both an amplitude (how "strong" the wave is there) and a phase (where the wave is in its cycle). Unlike a classical particle that has a definite position, a quantum particle is described by this spread-out wave.

The wave function lives in a **Hilbert space** $\mathcal{H}$—a complex vector space with an inner product:

$$
\langle \phi | \psi \rangle = \int_{-\infty}^{\infty} \phi^*(x) \psi(x) \, dx
$$

**What this means:** This formula measures the "overlap" between two wave functions $\phi$ and $\psi$. Imagine laying one wave on top of another and measuring how much they align. The $\phi^*$ means we take the complex conjugate of $\phi$ (flip the sign of its imaginary part). If two states are completely different (orthogonal), this integral gives zero. If they're identical, it gives 1 (for normalized states). This overlap determines transition probabilities between states.

### Normalization

The wave function must be normalized:

$$
\langle \psi | \psi \rangle = \int_{-\infty}^{\infty} |\psi(x)|^2 \, dx = 1
$$

**What this means:** If you add up $|\psi|^2$ over all of space, you must get exactly 1. This ensures that the particle exists *somewhere* with 100% certainty. The wave function describes probabilities, and all probabilities must sum to 1.

### Born Rule

The probability of finding the particle between $x$ and $x + dx$ is:

$$
P(x) \, dx = |\psi(x)|^2 \, dx
$$

**What this means:** To find the probability of locating a particle near position $x$, take the wave function's value at $x$, compute its absolute value squared, and multiply by the small interval $dx$. Where $|\psi|^2$ is large, you're likely to find the particle; where it's small, you're unlikely. This is the **Born rule**—the bridge between the abstract wave function and actual experimental predictions. The wave function itself isn't directly observable; only $|\psi|^2$ connects to measurements.

## The Schrödinger Equation

The wave function evolves according to the **Schrödinger equation**:

$$
i \frac{\partial \psi}{\partial t} = \hat{H} \psi
$$

**What this means:** This equation tells us how the wave function changes over time. The left side is the rate of change of $\psi$. The right side involves the Hamiltonian operator $\hat{H}$, which represents the total energy of the system. In essence: "how fast the wave function changes depends on the system's energy." The $i$ (imaginary unit) makes the evolution oscillatory rather than growing/decaying—this is why quantum states rotate in complex space rather than blowing up or dying out.

where $\hat{H}$ is the Hamiltonian operator. For a non-relativistic particle in a potential $V(x)$:

$$
\hat{H} = -\frac{1}{2m} \frac{\partial^2}{\partial x^2} + V(x)
$$

**What this means:** The Hamiltonian has two parts:
- The first term ($-\frac{1}{2m} \frac{\partial^2}{\partial x^2}$) is the **kinetic energy**—it measures how "curved" or "wiggly" the wave function is. More wiggles = higher momentum = more kinetic energy.
- The second term ($V(x)$) is the **potential energy**—it's determined by external forces (gravity, electric fields, etc.) at each position.

giving the full equation:

$$
i \frac{\partial \psi}{\partial t} = -\frac{1}{2m} \frac{\partial^2 \psi}{\partial x^2} + V(x) \psi
$$

**What this means:** This is the complete Schrödinger equation for a single particle. Given the wave function at one moment, this equation uniquely determines how it will evolve. It's completely deterministic—there's no randomness in how $\psi$ changes. The apparent randomness of quantum mechanics only enters when we make measurements.

### Time-Independent Case

For stationary states with definite energy $E$:

$$
\psi(x, t) = \phi(x) e^{-iEt}
$$

**What this means:** Some special wave functions just rotate in complex space without changing shape. The spatial part $\phi(x)$ stays fixed while $e^{-iEt}$ spins around the complex plane at a rate proportional to the energy $E$. These are the "stationary states" or energy eigenstates—they have definite, well-defined energy.

The spatial part satisfies:

$$
\hat{H} \phi = E \phi
$$

**What this means:** This is an eigenvalue equation. It says: "applying the energy operator to $\phi$ just gives back $\phi$ multiplied by the number $E$." Not every function satisfies this—only special functions (eigenstates) work, and only for specific values of $E$. This is why energy in quantum systems is often **quantized**—only certain discrete energy values are allowed.

### Key Properties

| Property | Mathematical Expression |
|----------|------------------------|
| Linearity | If $\psi_1$ and $\psi_2$ are solutions, so is $\alpha\psi_1 + \beta\psi_2$ |
| Unitarity | $\langle \psi(t) | \psi(t) \rangle = \langle \psi(0) | \psi(0) \rangle$ (probability conserved) |
| Determinism | Given $\psi(0)$, the equation uniquely determines $\psi(t)$ |

**What these mean:**
- **Linearity**: You can add wave functions together (superposition). If a particle can be "here" and can be "there," it can also be in a combination of both.
- **Unitarity**: Total probability never changes—it always sums to 1. Probability isn't created or destroyed, just moved around.
- **Determinism**: The Schrödinger equation has no randomness. If you know $\psi$ now, you can calculate $\psi$ at any future time exactly.

## Operators and Observables

Physical observables correspond to **Hermitian operators**:

| Observable | Operator |
|------------|----------|
| Position | $\hat{x} = x$ |
| Momentum | $\hat{p} = -i \frac{\partial}{\partial x}$ |
| Energy | $\hat{H} = \frac{\hat{p}^2}{2m} + V(\hat{x})$ |

**What this means:** In quantum mechanics, measurable quantities aren't just numbers—they're *operators* that act on wave functions.
- The position operator just multiplies by $x$.
- The momentum operator takes a derivative (measuring how fast $\psi$ changes in space).
- The energy operator combines both, as we saw above.

Hermitian operators have the special property that their eigenvalues (possible measurement outcomes) are always real numbers, as physical measurements must be.

### Expectation Values

The expected value of an observable $\hat{A}$:

$$
\langle A \rangle = \langle \psi | \hat{A} | \psi \rangle = \int \psi^* \hat{A} \psi \, dx
$$

**What this means:** If you measure observable $A$ on many identical systems all prepared in state $\psi$, this formula gives the average result you'd get. It's not the value of any single measurement, but the statistical average over many measurements.

### Commutators

The **commutator** of two operators:

$$
[\hat{A}, \hat{B}] = \hat{A}\hat{B} - \hat{B}\hat{A}
$$

**What this means:** The commutator asks: "Does it matter which order I apply these operators?" For ordinary numbers, $AB - BA = 0$ always. But for quantum operators, the order often matters—applying $\hat{A}$ then $\hat{B}$ gives a different result than $\hat{B}$ then $\hat{A}$.

The fundamental commutator of quantum mechanics:

$$
[\hat{x}, \hat{p}] = i
$$

**What this means:** Position and momentum don't commute—measuring position then momentum gives a different result than momentum then position. This non-commutativity is the mathematical root of the uncertainty principle. The $i$ (not zero!) on the right side is what makes quantum mechanics fundamentally different from classical physics.

## The Heisenberg Uncertainty Principle

For any two observables $\hat{A}$ and $\hat{B}$, the **uncertainty principle** states:

$$
\Delta A \cdot \Delta B \geq \frac{1}{2} |\langle [\hat{A}, \hat{B}] \rangle|
$$

**What this means:** The product of uncertainties (standard deviations) in two measurements is bounded below by their commutator. If two observables don't commute, you cannot simultaneously know both with arbitrary precision—reducing uncertainty in one necessarily increases uncertainty in the other.

where $\Delta A = \sqrt{\langle A^2 \rangle - \langle A \rangle^2}$ is the standard deviation.

**What this means:** $\Delta A$ is the "spread" in measurement outcomes—how much individual measurements typically deviate from the average. A small $\Delta A$ means measurements cluster tightly around the average; large $\Delta A$ means they're spread out.

For position and momentum:

$$
\boxed{\Delta x \cdot \Delta p \geq \frac{1}{2}}
$$

(In SI units: $\Delta x \cdot \Delta p \geq \frac{\hbar}{2}$)

**What this means:** You cannot simultaneously know exactly where a particle is AND how fast it's moving. If you pin down position very precisely ($\Delta x$ small), momentum becomes very uncertain ($\Delta p$ large), and vice versa. This isn't a limitation of our instruments—it's built into nature itself.

### What It Means

This is **not** about measurement disturbance. It's a fundamental property of waves:

- A wave localized in position requires many momentum components (Fourier transform)
- A wave with definite momentum extends infinitely in space

The uncertainty principle is a theorem about the wave function itself, not about our knowledge or instruments.

**Physical intuition:** Think of a guitar string. A pure musical note (definite frequency/momentum) requires a wave that extends forever. A sharp "pluck" localized to one spot contains many frequencies mixed together. You can't have both a perfectly localized position AND a perfectly defined frequency—this is true for all waves, and quantum particles are described by waves.

## Superposition

A quantum system can exist in a **superposition** of states:

$$
|\psi\rangle = \alpha |0\rangle + \beta |1\rangle
$$

where $|\alpha|^2 + |\beta|^2 = 1$.

**What this means:** A quantum system doesn't have to be in one definite state—it can be in multiple states simultaneously. The coefficients $\alpha$ and $\beta$ are complex numbers called "amplitudes." When measured, the system will be found in state $|0\rangle$ with probability $|\alpha|^2$ and in state $|1\rangle$ with probability $|\beta|^2$. Before measurement, it's genuinely in both.

The system is not "secretly" in one state or the other—it genuinely exists in both simultaneously until measurement.

**Why this matters:** Superposition is what makes quantum computers powerful. A classical bit is either 0 or 1. A quantum bit (qubit) can be in a superposition of both, allowing quantum computers to explore many possibilities simultaneously.

## Entanglement

When two particles interact, their wave functions can become **entangled**—they can no longer be described independently.

### Product vs. Entangled States

**Separable (product) state:**

$$
|\psi\rangle = |\phi_A\rangle \otimes |\phi_B\rangle
$$

**What this means:** In a product state, particle A has its own independent state $|\phi_A\rangle$, and particle B has its own independent state $|\phi_B\rangle$. You can fully describe each particle without mentioning the other. Measuring one tells you nothing about the other.

**Entangled state (Bell state):**

$$
|\Phi^+\rangle = \frac{1}{\sqrt{2}} \left( |0\rangle_A |0\rangle_B + |1\rangle_A |1\rangle_B \right)
$$

**What this means:** In this entangled state, neither particle has a definite state of its own—only the *pair* has a well-defined state. The particles are correlated: if you measure A and find $|0\rangle$, particle B will definitely be $|0\rangle$ too; if A is $|1\rangle$, B is $|1\rangle$. But before measurement, neither has a definite value.

In the Bell state, neither particle has a definite state of its own. Measuring particle A instantly determines the state of particle B, regardless of distance.

**The spooky part:** This correlation is instantaneous, even if the particles are light-years apart. Einstein called this "spooky action at a distance." However, you can't use it to send information faster than light—the outcomes are random, so you can't control what "message" gets sent.

### Bell's Theorem

Bell (1964) proved that no **local hidden variable theory** can reproduce all quantum predictions. Experiments confirm quantum mechanics—nature is genuinely nonlocal in this sense, though no information travels faster than light.

**What this means:** You might think the particles secretly decided their values when they separated (like gloves in boxes—if you find a left glove, you know the other box has the right glove). Bell proved this explanation doesn't work. The correlations are too strong to be explained by any pre-existing hidden information. The particles genuinely don't have definite values until measured.

### Quantifying Entanglement

For a pure state, entanglement can be measured by the **von Neumann entropy** of the reduced density matrix:

$$
S(\rho_A) = -\text{Tr}(\rho_A \log \rho_A)
$$

where $\rho_A = \text{Tr}_B(|\psi\rangle\langle\psi|)$.

**What this means:** To quantify entanglement, we "trace out" (ignore) particle B and ask: how much do we know about particle A alone? The entropy $S$ measures our ignorance. If the particles are unentangled, $S = 0$ (we know everything about A). If they're maximally entangled, knowing A alone tells us nothing—all the information is in the correlations.

For separable states: $S = 0$. For maximally entangled states: $S = \log 2$.

## The Measurement Problem

The Schrödinger equation is **deterministic** and **linear**. But measurements appear to:

1. Give random outcomes (probabilistic)
2. "Collapse" the wave function (nonlinear)

How does the smooth, deterministic wave function produce definite outcomes?

**The puzzle:** Before measurement, Schrödinger's equation says a particle can be "here AND there" in superposition. After measurement, we always find it in one definite place. The equation doesn't describe this sudden jump. Something seems to happen during measurement that isn't captured by the standard evolution equation.

### The Collapse Postulate

The standard (Copenhagen) approach adds a separate rule:

> Upon measurement of observable $\hat{A}$, the wave function collapses to an eigenstate $|a_n\rangle$ with probability $|\langle a_n | \psi \rangle|^2$.

**What this means:** When you measure, the wave function instantaneously "collapses" from a spread-out superposition to a single definite state corresponding to your measurement result. This rule works perfectly for predictions but feels ad hoc—it's separate from the Schrödinger equation and seems to require a special role for "measurement" or "observers."

This works empirically but raises questions:
- What counts as a "measurement"?
- When exactly does collapse occur?
- Why is measurement different from other interactions?

## Decoherence

**Decoherence** explains why we don't see quantum superpositions at macroscopic scales—without solving the full measurement problem.

### How It Works

A quantum system interacting with its environment becomes entangled with it:

$$
\left( \alpha |0\rangle + \beta |1\rangle \right) |E_0\rangle \to \alpha |0\rangle |E_0\rangle + \beta |1\rangle |E_1\rangle
$$

where $|E_0\rangle$ and $|E_1\rangle$ are environment states.

**What this means:** A quantum system doesn't exist in isolation—it interacts with air molecules, photons, etc. These interactions entangle the system with its environment. The particle's state becomes correlated with countless environmental particles.

If we ignore (trace out) the environment, the system's **reduced density matrix** becomes:

$$
\rho_{\text{system}} = |\alpha|^2 |0\rangle\langle 0| + |\beta|^2 |1\rangle\langle 1| + \underbrace{\alpha\beta^* |0\rangle\langle 1| + \alpha^*\beta |1\rangle\langle 0|}_{\text{off-diagonal terms}}
$$

**What this means:** The density matrix describes our knowledge of the system. The diagonal terms ($|0\rangle\langle 0|$ and $|1\rangle\langle 1|$) represent classical probabilities of being in each state. The off-diagonal terms represent quantum coherence—the ability to interfere, the "quantumness" of the superposition.

The off-diagonal "coherence" terms decay exponentially fast:

$$
\rho_{01}(t) \propto e^{-t/\tau_D}
$$

where $\tau_D$ is the **decoherence time** (often $< 10^{-20}$ seconds for macroscopic objects).

**What this means:** Environmental interactions destroy the off-diagonal terms incredibly fast. For large objects, this happens in a tiny fraction of a second. Without these terms, there's no interference, no superposition—just classical probabilities. This is why cats are never observed in superposition of alive and dead.

### What Decoherence Explains

- Why macroscopic superpositions are never observed
- Why certain bases (position, not momentum) are preferred
- Why the world looks classical

### What Decoherence Doesn't Explain

Decoherence gives a **diagonal** density matrix—a classical probability distribution—but doesn't explain why we see one outcome rather than all of them. The full wave function still contains all branches.

**The remaining puzzle:** Decoherence explains why we don't see interference between "alive cat" and "dead cat." But it doesn't explain why we see a *specific* outcome. The wave function still contains both possibilities—decoherence just makes them unable to interfere. We still need to explain why we experience one definite reality.

## The Many-Worlds Interpretation

The **Many-Worlds Interpretation** (MWI), proposed by Hugh Everett (1957), resolves the measurement problem by taking the Schrödinger equation literally—always and everywhere.

### Core Claims

1. **Universal Wave Function**: There's one wave function for the entire universe, evolving unitarily
2. **No Collapse**: The wave function never collapses—all branches are equally real
3. **Branching**: What looks like "measurement" is entanglement with the environment, causing the wave function to branch

**What this means:** Many-worlds says: don't add collapse as a separate rule. Just trust the Schrödinger equation completely. When a measurement happens, the universe doesn't pick one outcome—ALL outcomes occur, each in its own "branch." We experience one branch, but the others are equally real.

### How Measurement Works

Before measurement:

$$
|\text{observer}\rangle \otimes \left( \alpha |0\rangle + \beta |1\rangle \right)
$$

**What this means:** Before looking, the observer is in a single state, and the particle is in superposition.

After interaction:

$$
\alpha |\text{observer sees 0}\rangle |0\rangle + \beta |\text{observer sees 1}\rangle |1\rangle
$$

**What this means:** After measurement, the observer becomes entangled with the particle. There are now two "versions" of the observer: one who saw 0 and one who saw 1. Both exist in the wave function. Neither is more "real" than the other.

Both terms exist. There are now two "branches" of the observer, each experiencing a definite outcome.

### The Role of Decoherence

Decoherence explains why branches don't interfere:

$$
|\psi\rangle = \alpha |0\rangle |E_0\rangle + \beta |1\rangle |E_1\rangle
$$

If $\langle E_0 | E_1 \rangle \approx 0$, the branches evolve independently—they can't "see" each other.

**What this means:** The environment states $|E_0\rangle$ and $|E_1\rangle$ are so different (orthogonal) that the branches can never interfere or recombine. Each branch evolves as if the other doesn't exist. This is why you never experience being in two branches at once, and why you can't communicate with your "other selves."

Decoherence doesn't create branches, but it makes them **effectively separate** and explains the **preferred basis** (why we branch into position states, not momentum states).

### Probability in Many-Worlds

The Born rule ($P = |\alpha|^2$) is harder to justify if all outcomes occur. Approaches include:

- **Decision theory**: Rational agents should act as if the Born rule holds
- **Self-locating uncertainty**: Before looking, you're uncertain which branch you're in
- **Measure**: Branches have different "weights" proportional to amplitude squared

**What this means:** If all outcomes happen, why do we observe outcomes with frequencies matching $|\alpha|^2$? This is an active area of research. The leading ideas suggest that branches with larger amplitudes are more "likely" to be the one you find yourself in, or that rational betting behavior recovers the Born rule even though all outcomes occur.

### The Many-Worlds Picture

| Aspect | Copenhagen | Many-Worlds |
|--------|------------|-------------|
| Wave function | Epistemic (knowledge) | Ontic (real) |
| Collapse | Physical process | Apparent (branching + decoherence) |
| Outcomes | One is real | All are real |
| Randomness | Fundamental | Apparent (self-location) |
| Nonlocality | Explicit in collapse | Hidden in entanglement |

**What this table means:**
- **Copenhagen** treats the wave function as a tool for calculating probabilities (epistemic), with real collapse and fundamental randomness.
- **Many-worlds** treats the wave function as physically real (ontic), with no true collapse—just branching—and randomness that emerges from not knowing which branch you're in.

## Summary: Tying It Together

1. **Wave function** describes quantum systems in Hilbert space
2. **Schrödinger equation** governs deterministic, unitary evolution
3. **Uncertainty principle** is a fundamental property of waves, not measurement
4. **Entanglement** creates correlations that can't be explained classically
5. **Decoherence** explains why we don't see macroscopic superpositions
6. **Many-worlds** says: take the math literally—all branches exist, decoherence explains why we only experience one

The interpretations don't differ on predictions—they differ on what the formalism *means*. Many-worlds is arguably the most parsimonious: it adds nothing to the math, just takes it seriously.

**The big picture:** Quantum mechanics gives us a beautiful, precise mathematical framework that predicts experiments perfectly. The debates are about what that framework tells us about reality. Is the wave function real? Does measurement do something special? Does the universe split? These are open questions at the frontier of physics and philosophy.
