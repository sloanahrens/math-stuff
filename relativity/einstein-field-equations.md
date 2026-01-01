# Einstein Field Equations: Full Derivation

This document provides the complete mathematical derivation of Einstein's field equations from the action principle. We derive the equations from the Einstein-Hilbert action, showing every step. Prerequisites: [tensor calculus](../math-foundations/tensor-calculus.md), [differential forms](../math-foundations/differential-forms.md), [general relativity overview](general-relativity.md). We use [natural units](../math-foundations/natural-units.md) with $G = c = 1$.

## The Action Principle

### Motivation

In [Lagrangian mechanics](../classical-mechanics/lagrangian-mechanics.md), equations of motion follow from extremizing an action. The same principle applies to fields. For gravity, we need an action that:

1. Is a scalar (coordinate-independent)
2. Depends on the metric $g_{\mu\nu}$ and its derivatives
3. Gives second-order field equations
4. Reduces to Newtonian gravity in the appropriate limit

### The Einstein-Hilbert Action

The simplest action satisfying these requirements is:

$$
\boxed{S_{EH} = \frac{1}{16\pi} \int R \sqrt{-g} \, d^4x}
$$

where:
- $R = g^{\mu\nu} R_{\mu\nu}$ is the Ricci scalar
- $g = \det(g_{\mu\nu})$ is the metric determinant
- $\sqrt{-g} \, d^4x$ is the invariant volume element

**Why $R$?** The Ricci scalar is the unique scalar constructed from the metric and its first two derivatives that is linear in second derivatives. Higher-order scalars like $R^2$ or $R_{\mu\nu}R^{\mu\nu}$ give higher-derivative equations.

### Total Action

Including matter:

$$
S = S_{EH} + S_M = \frac{1}{16\pi} \int R \sqrt{-g} \, d^4x + S_M[g_{\mu\nu}, \psi]
$$

where $S_M$ is the matter action depending on the metric and matter fields $\psi$.

## Variation of the Action

### Setup

We vary the metric: $g_{\mu\nu} \to g_{\mu\nu} + \delta g_{\mu\nu}$

The field equations come from requiring:
$$
\delta S = 0
$$

for arbitrary variations $\delta g_{\mu\nu}$ that vanish at the boundary.

### Useful Variations

Before tackling the full action, we establish key identities.

**Inverse metric:**

From $g^{\mu\rho} g_{\rho\nu} = \delta^\mu_\nu$, varying both sides:
$$
\delta g^{\mu\rho} \cdot g_{\rho\nu} + g^{\mu\rho} \cdot \delta g_{\rho\nu} = 0
$$

Solving:
$$
\boxed{\delta g^{\mu\nu} = -g^{\mu\rho} g^{\nu\sigma} \delta g_{\rho\sigma}}
$$

**Metric determinant:**

Using the identity $\ln(\det A) = \text{Tr}(\ln A)$, we have:
$$
\delta g = g \cdot g^{\mu\nu} \delta g_{\mu\nu}
$$

Therefore:
$$
\boxed{\delta \sqrt{-g} = \frac{1}{2} \sqrt{-g} \, g^{\mu\nu} \delta g_{\mu\nu} = -\frac{1}{2} \sqrt{-g} \, g_{\mu\nu} \delta g^{\mu\nu}}
$$

### Variation of the Ricci Scalar

The Ricci scalar is $R = g^{\mu\nu} R_{\mu\nu}$, so:
$$
\delta R = \delta g^{\mu\nu} \cdot R_{\mu\nu} + g^{\mu\nu} \cdot \delta R_{\mu\nu}
$$

The first term is straightforward. For the second term, we need $\delta R_{\mu\nu}$.

### The Palatini Identity

The variation of the Riemann tensor gives:
$$
\delta R^\rho{}_{\sigma\mu\nu} = \nabla_\mu (\delta \Gamma^\rho_{\nu\sigma}) - \nabla_\nu (\delta \Gamma^\rho_{\mu\sigma})
$$

Contracting:
$$
\delta R_{\mu\nu} = \nabla_\rho (\delta \Gamma^\rho_{\nu\mu}) - \nabla_\nu (\delta \Gamma^\rho_{\rho\mu})
$$

Therefore:
$$
g^{\mu\nu} \delta R_{\mu\nu} = \nabla_\rho \left( g^{\mu\nu} \delta \Gamma^\rho_{\nu\mu} - g^{\rho\mu} \delta \Gamma^\sigma_{\sigma\mu} \right) \equiv \nabla_\rho V^\rho
$$

This is a total divergence!

### Variation of the Christoffel Symbols

We need $\delta \Gamma^\rho_{\mu\nu}$ in terms of $\delta g_{\mu\nu}$. From:
$$
\Gamma^\rho_{\mu\nu} = \frac{1}{2} g^{\rho\sigma} (\partial_\mu g_{\nu\sigma} + \partial_\nu g_{\mu\sigma} - \partial_\sigma g_{\mu\nu})
$$

The variation is:
$$
\delta \Gamma^\rho_{\mu\nu} = \frac{1}{2} g^{\rho\sigma} (\nabla_\mu \delta g_{\nu\sigma} + \nabla_\nu \delta g_{\mu\sigma} - \nabla_\sigma \delta g_{\mu\nu})
$$

Note: $\delta \Gamma^\rho_{\mu\nu}$ is a tensor (unlike $\Gamma^\rho_{\mu\nu}$ itself).

### Putting It Together

The variation of $S_{EH}$ is:

$$
\delta S_{EH} = \frac{1}{16\pi} \int \left[ \delta(g^{\mu\nu}) R_{\mu\nu} \sqrt{-g} + g^{\mu\nu} \delta R_{\mu\nu} \sqrt{-g} + R \, \delta\sqrt{-g} \right] d^4x
$$

**Term 1:**
$$
\delta g^{\mu\nu} \cdot R_{\mu\nu} \sqrt{-g} = -g^{\mu\rho} g^{\nu\sigma} \delta g_{\rho\sigma} \cdot R_{\mu\nu} \sqrt{-g} = -R^{\rho\sigma} \delta g_{\rho\sigma} \sqrt{-g}
$$

**Term 2:**
$$
g^{\mu\nu} \delta R_{\mu\nu} \sqrt{-g} = \nabla_\rho V^\rho \sqrt{-g} = \partial_\rho (V^\rho \sqrt{-g})
$$

This is a total derivative—it vanishes under the integral (boundary terms).

**Term 3:**
$$
R \, \delta\sqrt{-g} = R \cdot \frac{1}{2}\sqrt{-g} \, g^{\mu\nu} \delta g_{\mu\nu} = \frac{1}{2} R g^{\mu\nu} \delta g_{\mu\nu} \sqrt{-g}
$$

### Combined Result

$$
\delta S_{EH} = \frac{1}{16\pi} \int \left( -R^{\mu\nu} + \frac{1}{2} g^{\mu\nu} R \right) \delta g_{\mu\nu} \sqrt{-g} \, d^4x
$$

Equivalently:
$$
\delta S_{EH} = -\frac{1}{16\pi} \int G^{\mu\nu} \delta g_{\mu\nu} \sqrt{-g} \, d^4x
$$

where $G^{\mu\nu} = R^{\mu\nu} - \frac{1}{2} g^{\mu\nu} R$ is the Einstein tensor.

## The Stress-Energy Tensor

### Definition from the Action

The stress-energy tensor is defined as:

$$
\boxed{T_{\mu\nu} = -\frac{2}{\sqrt{-g}} \frac{\delta S_M}{\delta g^{\mu\nu}}}
$$

This definition ensures $T_{\mu\nu}$ is symmetric and covariantly conserved.

### Variation of the Matter Action

$$
\delta S_M = \int \frac{\delta S_M}{\delta g^{\mu\nu}} \delta g^{\mu\nu} \, d^4x = -\frac{1}{2} \int T_{\mu\nu} \delta g^{\mu\nu} \sqrt{-g} \, d^4x
$$

Or equivalently:
$$
\delta S_M = \frac{1}{2} \int T^{\mu\nu} \delta g_{\mu\nu} \sqrt{-g} \, d^4x
$$

## Deriving the Field Equations

### The Variational Principle

Setting $\delta S = \delta S_{EH} + \delta S_M = 0$:

$$
\int \left( -\frac{1}{16\pi} G^{\mu\nu} + \frac{1}{2} T^{\mu\nu} \right) \delta g_{\mu\nu} \sqrt{-g} \, d^4x = 0
$$

Since this must hold for arbitrary $\delta g_{\mu\nu}$:

$$
-\frac{1}{16\pi} G^{\mu\nu} + \frac{1}{2} T^{\mu\nu} = 0
$$

Therefore:

$$
\boxed{G_{\mu\nu} = 8\pi T_{\mu\nu}}
$$

or explicitly:

$$
\boxed{R_{\mu\nu} - \frac{1}{2} g_{\mu\nu} R = 8\pi T_{\mu\nu}}
$$

These are the **Einstein field equations**.

## Adding the Cosmological Constant

### Modified Action

Including a cosmological constant $\Lambda$:

$$
S = \frac{1}{16\pi} \int (R - 2\Lambda) \sqrt{-g} \, d^4x + S_M
$$

### Variation

The variation of the $\Lambda$ term:
$$
\delta \int (-2\Lambda) \sqrt{-g} \, d^4x = \int (-2\Lambda) \cdot \frac{1}{2}\sqrt{-g} \, g^{\mu\nu} \delta g_{\mu\nu} \, d^4x = -\int \Lambda g^{\mu\nu} \delta g_{\mu\nu} \sqrt{-g} \, d^4x
$$

### Field Equations with $\Lambda$

$$
\boxed{G_{\mu\nu} + \Lambda g_{\mu\nu} = 8\pi T_{\mu\nu}}
$$

## Properties of the Einstein Tensor

### Symmetry

$G_{\mu\nu} = G_{\nu\mu}$ (inherited from $R_{\mu\nu}$ and $g_{\mu\nu}$)

### The Contracted Bianchi Identity

The Bianchi identity for the Riemann tensor:
$$
\nabla_\lambda R^\rho{}_{\sigma\mu\nu} + \nabla_\mu R^\rho{}_{\sigma\nu\lambda} + \nabla_\nu R^\rho{}_{\sigma\lambda\mu} = 0
$$

Contracting $\rho = \mu$:
$$
\nabla_\lambda R_{\sigma\nu} - \nabla_\mu R^\mu{}_{\sigma\nu\lambda} + \nabla_\nu R_{\sigma\lambda} = 0
$$

Contracting again with $g^{\sigma\lambda}$:
$$
\nabla_\lambda R^\lambda{}_\nu - \nabla_\mu R^\mu{}_\nu + \nabla_\nu R = 0
$$
$$
\nabla^\mu R_{\mu\nu} - \frac{1}{2} \nabla_\nu R = 0
$$

Therefore:
$$
\boxed{\nabla_\mu G^{\mu\nu} = 0}
$$

**What this means:** The Einstein tensor is automatically divergence-free. This is a geometric identity, not a consequence of the field equations. It's crucial for consistency.

### Consequences for Conservation

From $G_{\mu\nu} = 8\pi T_{\mu\nu}$ and $\nabla_\mu G^{\mu\nu} = 0$:

$$
\boxed{\nabla_\mu T^{\mu\nu} = 0}
$$

Energy-momentum conservation follows automatically from the field equations and the Bianchi identity.

## Trace of the Field Equations

### Taking the Trace

Contract $G_{\mu\nu} = 8\pi T_{\mu\nu}$ with $g^{\mu\nu}$:
$$
g^{\mu\nu} G_{\mu\nu} = 8\pi g^{\mu\nu} T_{\mu\nu}
$$

The left side:
$$
g^{\mu\nu} \left( R_{\mu\nu} - \frac{1}{2} g_{\mu\nu} R \right) = R - \frac{1}{2} \cdot 4 \cdot R = R - 2R = -R
$$

Therefore:
$$
R = -8\pi T
$$

where $T = g^{\mu\nu} T_{\mu\nu}$ is the trace of the stress-energy tensor.

### Alternative Form

Substituting back:
$$
R_{\mu\nu} = 8\pi \left( T_{\mu\nu} - \frac{1}{2} g_{\mu\nu} T \right)
$$

This is useful for finding solutions.

## Vacuum Solutions

### Vacuum Field Equations

In vacuum, $T_{\mu\nu} = 0$, so:
$$
G_{\mu\nu} = 0 \quad \Rightarrow \quad R_{\mu\nu} = 0
$$

**Note:** $R_{\mu\nu} = 0$ does NOT imply flat spacetime. The full Riemann tensor $R^\rho{}_{\sigma\mu\nu}$ can be nonzero while its contraction $R_{\mu\nu}$ vanishes.

### Examples

- **Schwarzschild:** $R_{\mu\nu} = 0$ but $R^\rho{}_{\sigma\mu\nu} \neq 0$ (tidal forces exist)
- **Kerr:** $R_{\mu\nu} = 0$ but curved spacetime with frame dragging
- **Gravitational waves:** $R_{\mu\nu} = 0$ but propagating curvature

## The Newtonian Limit

### Setup

For weak fields and slow motion:
- $g_{\mu\nu} = \eta_{\mu\nu} + h_{\mu\nu}$ with $|h_{\mu\nu}| \ll 1$
- $v \ll 1$ (speeds much less than $c$)
- $T_{\mu\nu} \approx \rho \, u_\mu u_\nu \approx \rho \, \delta^0_\mu \delta^0_\nu$ (dust)

### Linearized Equations

To first order in $h_{\mu\nu}$:
$$
R_{\mu\nu} \approx \frac{1}{2} \left( \partial_\mu \partial_\rho h^\rho{}_\nu + \partial_\nu \partial_\rho h^\rho{}_\mu - \partial_\mu \partial_\nu h - \Box h_{\mu\nu} \right)
$$

where $h = \eta^{\mu\nu} h_{\mu\nu}$ and $\Box = \eta^{\mu\nu} \partial_\mu \partial_\nu$.

### The 00 Component

For static fields and $T_{00} = \rho$:
$$
R_{00} \approx -\frac{1}{2} \nabla^2 h_{00}
$$

The field equation $R_{00} = 8\pi (T_{00} - \frac{1}{2} \eta_{00} T) = 4\pi \rho$ gives:
$$
\nabla^2 h_{00} = -8\pi \rho
$$

With $h_{00} = -2\Phi$ (where $\Phi$ is the Newtonian potential):
$$
\boxed{\nabla^2 \Phi = 4\pi \rho}
$$

This is Poisson's equation—Newtonian gravity.

## Degrees of Freedom

### Counting

The metric $g_{\mu\nu}$ has 10 components (symmetric $4 \times 4$).

The field equations $G_{\mu\nu} = 8\pi T_{\mu\nu}$ give 10 equations.

But $\nabla_\mu G^{\mu\nu} = 0$ provides 4 constraints (Bianchi identity).

And coordinate freedom gives 4 gauge degrees of freedom.

**Physical degrees of freedom:** $10 - 4 - 4 = 2$

These correspond to the two polarizations of gravitational waves. See [gravitational waves](gravitational-waves.md).

### Gauge Freedom

The metric transforms under coordinate changes $x^\mu \to x^\mu + \xi^\mu$:
$$
g_{\mu\nu} \to g_{\mu\nu} - \nabla_\mu \xi_\nu - \nabla_\nu \xi_\mu
$$

Different choices of coordinates give physically equivalent solutions—this is gauge freedom.

## Alternative Derivations

### The Palatini Formalism

Treat $g_{\mu\nu}$ and $\Gamma^\rho_{\mu\nu}$ as independent variables:
$$
S = \frac{1}{16\pi} \int g^{\mu\nu} R_{\mu\nu}(\Gamma) \sqrt{-g} \, d^4x
$$

Varying with respect to $\Gamma$ gives the Christoffel symbol formula. Varying with respect to $g$ gives the Einstein equations. The result is the same as the metric formalism.

### Lovelock's Theorem

The Einstein-Hilbert action is unique (in 4D) as the action that:
1. Depends only on $g_{\mu\nu}$ and its derivatives
2. Gives second-order field equations
3. Is diffeomorphism invariant

Any other such action differs only by a cosmological constant and boundary terms.

## Summary

| Step | Result |
|------|--------|
| Action | $S = \frac{1}{16\pi} \int R\sqrt{-g} \, d^4x + S_M$ |
| Vary metric | $\delta g^{\mu\nu} = -g^{\mu\rho}g^{\nu\sigma}\delta g_{\rho\sigma}$ |
| Vary determinant | $\delta\sqrt{-g} = \frac{1}{2}\sqrt{-g} \, g^{\mu\nu}\delta g_{\mu\nu}$ |
| Vary curvature | $g^{\mu\nu}\delta R_{\mu\nu} = \nabla_\rho V^\rho$ (boundary term) |
| Stress-energy | $T_{\mu\nu} = -\frac{2}{\sqrt{-g}}\frac{\delta S_M}{\delta g^{\mu\nu}}$ |
| Field equations | $G_{\mu\nu} = 8\pi T_{\mu\nu}$ |

| Key Identity | Consequence |
|--------------|-------------|
| $\nabla_\mu G^{\mu\nu} = 0$ | 4 constraints on 10 equations |
| $\nabla_\mu T^{\mu\nu} = 0$ | Energy-momentum conservation |
| $R = -8\pi T$ | Trace of field equations |

**The essential insight:** Einstein's field equations aren't arbitrary—they're the unique second-order equations for the metric that can be derived from an action principle. The Einstein-Hilbert action $\int R\sqrt{-g}\,d^4x$ is the simplest diffeomorphism-invariant action depending on spacetime curvature. The automatic conservation of energy-momentum ($\nabla_\mu T^{\mu\nu} = 0$) follows from the Bianchi identity, which is a geometric fact about curvature. This beautiful mathematical structure ensures that general relativity is internally consistent: the source of gravity (energy-momentum) is automatically conserved, as it must be for the theory to make sense.
