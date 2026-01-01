# Black Hole Thermodynamics

The discovery that black holes have temperature and entropy revolutionized our understanding of gravity, quantum mechanics, and information. This document connects [Schwarzschild](schwarzschild-solution.md) and [Kerr](kerr-metric.md) black holes to [statistical mechanics](statistical-mechanics.md), revealing deep relationships between gravity and thermodynamics.

## The Paradox That Started It All

### Wheeler's Teacup

John Wheeler posed a thought experiment: What happens if you throw a hot cup of tea into a black hole? The tea has entropy, but once it crosses the horizon, it's gone. Has the entropy of the universe decreased, violating the second law of thermodynamics?

**The resolution:** Black holes must carry entropy themselves. The total entropy (black hole + exterior) never decreases.

## The Four Laws of Black Hole Mechanics

Bardeen, Carter, and Hawking (1973) discovered that black holes obey laws strikingly similar to thermodynamics.

### Zeroth Law

**Statement:** The surface gravity $\kappa$ is constant over the event horizon of a stationary black hole.

$$
\kappa = \text{const. on horizon}
$$

For Schwarzschild: $\kappa = \frac{1}{4M}$ (in $G = c = 1$ units).

**Thermodynamic analog:** Temperature is uniform throughout a body in thermal equilibrium.

**What this means:** Just as a body in equilibrium has uniform temperature, a stationary black hole has uniform surface gravity. This is the first hint that $\kappa$ plays the role of temperature.

### First Law

**Statement:** For small perturbations of a stationary black hole:

$$
\boxed{dM = \frac{\kappa}{8\pi}dA + \Omega_H dJ + \Phi_H dQ}
$$

where:
- $M$ = mass (energy)
- $A$ = horizon area
- $J$ = angular momentum
- $Q$ = electric charge
- $\Omega_H$ = angular velocity of horizon
- $\Phi_H$ = electrostatic potential at horizon

**Thermodynamic analog:** $dE = TdS + \text{work terms}$

**What this means:** This is energy conservation for black holes. The term $\frac{\kappa}{8\pi}dA$ suggests that $\kappa$ is proportional to temperature and $A$ to entropy.

### Second Law (Area Theorem)

**Statement (Hawking, 1971):** In any classical process, the total horizon area never decreases:

$$
\boxed{\frac{dA}{dt} \geq 0}
$$

**Thermodynamic analog:** Entropy never decreases: $dS \geq 0$

**What this means:** When black holes merge, the final area exceeds the sum of the initial areas. You cannot extract energy from a black hole without increasing its area (except via the Penrose process, which extracts rotational energy).

### Third Law

**Statement:** It is impossible to reduce $\kappa$ to zero by any finite sequence of operations.

**Thermodynamic analog:** It is impossible to reach absolute zero temperature.

**What this means:** You cannot create an extremal black hole ($\kappa = 0$) starting from a non-extremal one. The extremal limit, where $M = |Q|$ or $M = |J|/M$, is unattainable.

## Bekenstein-Hawking Entropy

### Bekenstein's Argument

Jacob Bekenstein (1972) argued that black hole entropy should be proportional to horizon area:

$$
S_{BH} \propto \frac{A}{\ell_P^2}
$$

where $\ell_P = \sqrt{\hbar G/c^3} \approx 1.6 \times 10^{-35}$ m is the Planck length.

**The reasoning:** Information about what fell in is stored on the horizon. The number of Planck-area "cells" on the horizon gives the number of microstates.

### Hawking's Calculation

Stephen Hawking (1975) derived the exact coefficient by studying quantum fields near the horizon:

$$
\boxed{S_{BH} = \frac{k_B c^3 A}{4 G \hbar} = \frac{A}{4\ell_P^2}}
$$

In [natural units](natural-units.md) with $G = c = \hbar = k_B = 1$:

$$
\boxed{S_{BH} = \frac{A}{4}}
$$

**What this means:** A black hole's entropy is enormous—proportional to the surface area in Planck units. A solar-mass black hole has entropy $\sim 10^{77}$, far exceeding any ordinary matter.

### For Schwarzschild Black Holes

The horizon area is $A = 4\pi r_s^2 = 16\pi M^2$, so:

$$
S_{BH} = 4\pi M^2 = \frac{\pi r_s^2}{\ell_P^2}
$$

### For Kerr Black Holes

The horizon area is (see [Kerr metric](kerr-metric.md)):

$$
A = 8\pi M r_+ = 8\pi M(M + \sqrt{M^2 - a^2})
$$

where $a = J/M$. The entropy is:

$$
S_{BH} = 2\pi M(M + \sqrt{M^2 - a^2})
$$

## Hawking Temperature

### The Discovery

Hawking showed that black holes are not truly black—they emit thermal radiation:

$$
\boxed{T_H = \frac{\hbar c^3}{8\pi G M k_B} = \frac{\kappa}{2\pi}}
$$

In natural units:

$$
T_H = \frac{1}{8\pi M}
$$

**What this means:** Black holes glow! The temperature is inversely proportional to mass—small black holes are hot, large ones are cold.

### Numerical Values

| Black Hole | Mass | Temperature |
|------------|------|-------------|
| Primordial (asteroid-mass) | $10^{12}$ kg | $10^{11}$ K |
| Stellar (10 $M_\odot$) | $2 \times 10^{31}$ kg | $6 \times 10^{-9}$ K |
| Supermassive (Sgr A*) | $4 \times 10^6 M_\odot$ | $10^{-14}$ K |

**What this means:** Astrophysical black holes are colder than the cosmic microwave background (2.7 K). They absorb more than they emit and grow over time. Only microscopic black holes would be hot enough to visibly radiate.

### Origin of Hawking Radiation

Near the horizon, quantum vacuum fluctuations create virtual particle-antiparticle pairs. Occasionally:
- One particle falls in with negative energy
- The other escapes to infinity with positive energy
- The black hole loses mass

This is a semiclassical picture—the full quantum gravity description remains unknown.

## Black Hole Evaporation

### Mass Loss Rate

A black hole radiates approximately as a blackbody with area $A$ and temperature $T_H$:

$$
\frac{dM}{dt} = -\sigma A T_H^4 \propto -\frac{1}{M^2}
$$

Integrating:

$$
M(t) = M_0\left(1 - \frac{t}{t_{evap}}\right)^{1/3}
$$

### Evaporation Time

$$
\boxed{t_{evap} = \frac{5120 \pi G^2 M_0^3}{\hbar c^4} \approx 10^{67} \left(\frac{M_0}{M_\odot}\right)^3 \text{ years}}
$$

**What this means:** A solar-mass black hole takes $10^{67}$ years to evaporate—vastly longer than the age of the universe. But a mountain-mass black hole ($10^{12}$ kg) would evaporate in about 10 billion years.

### Final Moments

As $M \to 0$, $T_H \to \infty$. The black hole becomes increasingly hot and radiates more intensely. The final moments release $\sim Mc^2$ of energy in a burst of radiation.

## The Information Paradox

### The Problem

If a black hole evaporates completely:
1. **Initial state:** Pure quantum state (book, star, etc.) falls in
2. **Final state:** Thermal Hawking radiation (mixed state)

But quantum mechanics requires unitary evolution: pure states must evolve to pure states. Where did the information go?

### Proposed Resolutions

| Resolution | Idea | Status |
|------------|------|--------|
| Information destruction | Quantum mechanics fails | Violates unitarity |
| Remnants | Information stored in Planck-mass remnant | Infinite number of species problem |
| Baby universes | Information goes elsewhere | Untestable |
| Complementarity | Different observers see different physics | Challenged by AMPS firewall |
| Holography/AdS-CFT | Information preserved in boundary theory | Leading candidate |
| Page curve | Information gradually escapes | Recent progress |

### Recent Developments

Recent work on the "island formula" and gravitational entropy suggests that information is indeed preserved, encoded subtly in Hawking radiation correlations. This involves replica wormholes and new gravitational contributions to entropy.

## Generalized Second Law

### Statement

Bekenstein proposed the **Generalized Second Law (GSL)**:

$$
\boxed{\frac{d}{dt}(S_{matter} + S_{BH}) \geq 0}
$$

The total entropy—ordinary matter plus black holes—never decreases.

**What this means:** You can throw entropy into a black hole, but the black hole's entropy increases more. The GSL unifies thermodynamics and black hole mechanics.

### Tests of the GSL

1. **Throwing matter into a black hole:** The increase in $S_{BH}$ exceeds the entropy of matter absorbed
2. **Hawking radiation:** The radiation entropy exceeds the decrease in $S_{BH}$
3. **Mining a black hole:** Any attempt to extract work respects the GSL

## Surface Gravity

### Definition

The surface gravity $\kappa$ is the acceleration experienced at the horizon as measured by a distant observer:

$$
\kappa = \lim_{r \to r_+} \frac{d\phi/dr}{\sqrt{-g_{tt}}}
$$

where $\phi$ is the gravitational potential.

### For Schwarzschild

$$
\kappa = \frac{1}{4M} = \frac{c^4}{4GM}
$$

### For Kerr

$$
\kappa = \frac{r_+ - M}{2M r_+} = \frac{\sqrt{M^2 - a^2}}{2M(M + \sqrt{M^2 - a^2})}
$$

**What this means:** Rapidly rotating black holes have lower surface gravity (and temperature). An extremal Kerr black hole ($a = M$) has $\kappa = 0$—it is "cold."

## Euclidean Methods

### Wick Rotation

In the Euclidean (imaginary time) approach:
- Replace $t \to -i\tau$
- The black hole metric becomes Euclidean
- Regularity at the horizon requires $\tau$ to be periodic with period $\beta = 2\pi/\kappa$

### Temperature from Periodicity

The thermal interpretation of quantum field theory (see [path integrals](path-integrals.md)) gives:

$$
T = \frac{1}{\beta} = \frac{\kappa}{2\pi}
$$

**What this means:** The Hawking temperature emerges naturally from the geometric requirement that Euclidean space be smooth at the horizon.

## Holographic Principle

### The Entropy Bound

Bekenstein argued that the maximum entropy in a region is bounded by its surface area:

$$
S \leq \frac{A}{4\ell_P^2}
$$

**What this means:** Information about a 3D region is encoded on its 2D boundary—like a hologram. This is a profound statement about the nature of space and information.

### AdS/CFT Connection

The holographic principle is realized precisely in the AdS/CFT correspondence:
- Gravity in (d+1)-dimensional anti-de Sitter space
- Equivalent to a conformal field theory on the d-dimensional boundary
- Black hole entropy = entanglement entropy in the CFT

## Summary

| Quantity | Black Hole | Thermodynamics |
|----------|------------|----------------|
| Mass $M$ | Energy $E$ | Internal energy |
| Surface gravity $\kappa$ | Temperature $T$ | $T = \kappa/(2\pi)$ |
| Horizon area $A$ | Entropy $S$ | $S = A/4$ |
| Angular momentum $J$ | Rotation | Work term |
| Charge $Q$ | Electrostatics | Work term |

| Law | Black Holes | Thermodynamics |
|-----|-------------|----------------|
| Zeroth | $\kappa$ constant on horizon | $T$ uniform in equilibrium |
| First | $dM = \frac{\kappa}{8\pi}dA + \cdots$ | $dE = TdS + \cdots$ |
| Second | $dA \geq 0$ | $dS \geq 0$ |
| Third | Cannot reach $\kappa = 0$ | Cannot reach $T = 0$ |

**The essential insight:** Black holes are thermodynamic objects with temperature and entropy. The Bekenstein-Hawking entropy $S = A/4$ suggests that spacetime itself has microscopic degrees of freedom—one per Planck area on the horizon. This connection between geometry and information may be the key to quantum gravity.
