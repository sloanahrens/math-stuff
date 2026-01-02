# Thermodynamics

Thermodynamics describes the behavior of macroscopic systems through state variables like temperature, pressure, and entropy. It's remarkably universal—the same laws govern steam engines, black holes, and quantum computers. This document introduces the classical framework; see [statistical mechanics](statistical-mechanics.md) for the microscopic foundations and [entropy](entropy.md) for the central concept in depth.

## The Four Laws

### Zeroth Law: Thermal Equilibrium

> If system A is in thermal equilibrium with system B, and B is in equilibrium with C, then A is in equilibrium with C.

**What this means:** This defines temperature. Systems in equilibrium share a common temperature, and we can use thermometers.

### First Law: Energy Conservation

```math
\boxed{dU = \delta Q - \delta W}
```

where:
- $U$ is internal energy (a state function)
- $\delta Q$ is heat added to the system
- $\delta W$ is work done by the system

**What this means:** Energy is conserved. Heat and work are both forms of energy transfer. The notation $\delta$ (not $d$) indicates these are path-dependent, not exact differentials.

**For reversible processes:**
```math
dU = T\,dS - P\,dV
```

This is the fundamental thermodynamic relation.

### Second Law: Entropy Increases

Several equivalent statements:

**Clausius:** Heat cannot spontaneously flow from cold to hot.

**Kelvin-Planck:** No process can convert heat entirely into work.

**Entropy:** For an isolated system:
```math
\boxed{\Delta S \geq 0}
```

with equality only for reversible processes.

**What this means:** There's a preferred direction to natural processes. You can't unscramble an egg. See [entropy](entropy.md) for why this is perhaps the deepest law in physics.

### Third Law: Absolute Zero

> As $T \to 0$, the entropy of a perfect crystal approaches zero.

```math
\lim_{T \to 0} S = 0
```

**What this means:** Absolute zero is unattainable in finite steps. At $T = 0$, a system is in its unique ground state (for non-degenerate systems).

## State Functions

### Definition

A **state function** depends only on the current state, not on how the system got there.

| State Function | Not State Function |
|----------------|-------------------|
| $U$ (internal energy) | $Q$ (heat) |
| $S$ (entropy) | $W$ (work) |
| $T$, $P$, $V$ | Path taken |
| $H$, $F$, $G$ (below) | Process details |

### Internal Energy

For an ideal gas:
```math
U = \frac{f}{2}nRT
```

where $f$ is degrees of freedom (3 for monatomic, 5 for diatomic at moderate $T$).

### Enthalpy

```math
H = U + PV
```

**What this means:** Enthalpy is the "heat content" at constant pressure. For isobaric processes, $\Delta H = Q_P$.

### Heat Capacities

```math
C_V = \left(\frac{\partial U}{\partial T}\right)_V, \qquad C_P = \left(\frac{\partial H}{\partial T}\right)_P
```

For ideal gases:
```math
C_P - C_V = nR
```

## Free Energies

### Helmholtz Free Energy

```math
\boxed{F = U - TS}
```

**Natural variables:** $F = F(T, V)$

**Differential:**
```math
dF = -S\,dT - P\,dV
```

**What this means:** At constant $T$ and $V$, systems minimize $F$. The maximum work extractable at constant $T$ equals $-\Delta F$.

### Gibbs Free Energy

```math
\boxed{G = U - TS + PV = H - TS}
```

**Natural variables:** $G = G(T, P)$

**Differential:**
```math
dG = -S\,dT + V\,dP
```

**What this means:** At constant $T$ and $P$ (typical lab conditions), systems minimize $G$. This determines chemical equilibrium and phase transitions.

### Summary of Potentials

| Potential | Definition | Natural Variables | Minimized When |
|-----------|------------|-------------------|----------------|
| $U$ | Internal energy | $S, V$ | Isolated system |
| $H$ | $U + PV$ | $S, P$ | Constant entropy, pressure |
| $F$ | $U - TS$ | $T, V$ | Constant temperature, volume |
| $G$ | $U - TS + PV$ | $T, P$ | Constant temperature, pressure |

## Maxwell Relations

From the equality of mixed partial derivatives:

```math
\left(\frac{\partial T}{\partial V}\right)_S = -\left(\frac{\partial P}{\partial S}\right)_V
```

```math
\left(\frac{\partial T}{\partial P}\right)_S = \left(\frac{\partial V}{\partial S}\right)_P
```

```math
\left(\frac{\partial S}{\partial V}\right)_T = \left(\frac{\partial P}{\partial T}\right)_V
```

```math
\left(\frac{\partial S}{\partial P}\right)_T = -\left(\frac{\partial V}{\partial T}\right)_P
```

**What this means:** These connect measurable quantities (like thermal expansion $\partial V/\partial T$) to entropy changes that are harder to measure directly.

## Thermodynamic Processes

### Types of Processes

| Process | Condition | Result |
|---------|-----------|--------|
| Isothermal | $T = \text{const}$ | $\Delta U = 0$ (ideal gas) |
| Isobaric | $P = \text{const}$ | $W = P\Delta V$ |
| Isochoric | $V = \text{const}$ | $W = 0$ |
| Adiabatic | $Q = 0$ | $PV^\gamma = \text{const}$ |
| Isentropic | $S = \text{const}$ | Reversible adiabatic |

### Ideal Gas Laws

**Equation of state:**
```math
PV = nRT
```

**Adiabatic process:**
```math
TV^{\gamma-1} = \text{const}, \qquad PV^\gamma = \text{const}
```

where $\gamma = C_P/C_V$.

## Heat Engines

### Efficiency

A heat engine absorbs heat $Q_H$ from a hot reservoir, does work $W$, and exhausts heat $Q_C$ to a cold reservoir.

```math
\eta = \frac{W}{Q_H} = 1 - \frac{Q_C}{Q_H}
```

### Carnot Engine

The most efficient engine operating between temperatures $T_H$ and $T_C$:

```math
\boxed{\eta_{\text{Carnot}} = 1 - \frac{T_C}{T_H}}
```

**The Carnot cycle:**
1. Isothermal expansion at $T_H$ (absorb $Q_H$)
2. Adiabatic expansion ($T_H \to T_C$)
3. Isothermal compression at $T_C$ (release $Q_C$)
4. Adiabatic compression ($T_C \to T_H$)

**What this means:** No engine can be more efficient than Carnot. This is another statement of the second law.

### Refrigerators and Heat Pumps

**Coefficient of performance (refrigerator):**
```math
\text{COP} = \frac{Q_C}{W} \leq \frac{T_C}{T_H - T_C}
```

**Heat pump COP:**
```math
\text{COP} = \frac{Q_H}{W} \leq \frac{T_H}{T_H - T_C}
```

## Phase Transitions

### Clausius-Clapeyron Equation

Along a phase boundary:
```math
\frac{dP}{dT} = \frac{L}{T\Delta V}
```

where $L$ is the latent heat and $\Delta V$ is the volume change.

**What this means:** This predicts how boiling/melting points change with pressure.

### Types of Phase Transitions

**First-order:** Discontinuous first derivatives of $G$ (latent heat, volume change)
- Examples: melting, boiling, sublimation

**Second-order (continuous):** Continuous first derivatives, discontinuous second derivatives
- Examples: superconducting transition, ferromagnetic transition

### Critical Point

Above the critical temperature $T_c$, liquid and gas phases become indistinguishable. Near the critical point, fluctuations diverge and universal scaling behavior emerges.

## Chemical Thermodynamics

### Chemical Potential

```math
\mu_i = \left(\frac{\partial G}{\partial N_i}\right)_{T,P,N_{j\neq i}}
```

At equilibrium, chemical potential is uniform throughout the system.

### Gibbs-Duhem Relation

```math
S\,dT - V\,dP + \sum_i N_i\,d\mu_i = 0
```

### Equilibrium Constant

For a reaction $aA + bB \rightleftharpoons cC + dD$:

```math
\Delta G = \Delta G^\circ + RT \ln Q
```

At equilibrium ($\Delta G = 0$):
```math
K = e^{-\Delta G^\circ/RT}
```

## Connection to Other Areas

### Statistical Mechanics

Classical thermodynamics is phenomenological—it doesn't explain *why* entropy increases. [Statistical mechanics](statistical-mechanics.md) provides the microscopic foundation:

```math
S = k_B \ln W
```

where $W$ is the number of microstates.

### Information Theory

Entropy has a deep connection to [information theory](../information-theory/information-theory.md). The [entropy](entropy.md) document explores how thermodynamic entropy and Shannon entropy are fundamentally the same concept.

### Black Hole Thermodynamics

Black holes obey thermodynamic laws with:
- Temperature: $T = \hbar c^3/(8\pi G M k_B)$
- Entropy: $S = k_B c^3 A/(4G\hbar)$

See [black hole thermodynamics](../relativity/black-hole-thermodynamics.md).

## Summary

| Law | Statement | Consequence |
|-----|-----------|-------------|
| Zeroth | Equilibrium is transitive | Temperature exists |
| First | $dU = \delta Q - \delta W$ | Energy conserved |
| Second | $\Delta S \geq 0$ | Entropy increases |
| Third | $S \to 0$ as $T \to 0$ | Absolute zero unattainable |

| Potential | Formula | Minimized at constant |
|-----------|---------|----------------------|
| Helmholtz $F$ | $U - TS$ | $T, V$ |
| Gibbs $G$ | $H - TS$ | $T, P$ |

**The essential insight:** Thermodynamics describes what's possible and what's forbidden for macroscopic systems, without needing microscopic details. The second law—entropy always increases—is arguably the most universal law in physics, governing everything from engines to ecosystems to the fate of the universe.
