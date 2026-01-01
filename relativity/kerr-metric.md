# The Kerr Metric

The Kerr metric is the unique stationary, axially symmetric vacuum solution to Einstein's field equations. It describes the spacetime geometry outside a rotating, uncharged black hole. This document requires understanding of [general relativity](general-relativity.md) and uses [tensor calculus](../math-foundations/tensor-calculus.md) notation. We use [natural units](../math-foundations/natural-units.md) where $G = c = 1$. For orbital motion and light paths, see [geodesics](geodesics.md); for thermodynamic properties, see [black hole thermodynamics](black-hole-thermodynamics.md); for dynamical aspects, see [gravitational waves](gravitational-waves.md).

## The Metric

In Boyer-Lindquist coordinates $(t, r, \theta, \phi)$, the line element is:

$$
ds^2 = -\left(1 - \frac{2Mr}{\Sigma}\right) dt^2 - \frac{4Mar\sin^2\theta}{\Sigma} \, dt \, d\phi + \frac{\Sigma}{\Delta} dr^2 + \Sigma \, d\theta^2 + \frac{A \sin^2\theta}{\Sigma} d\phi^2
$$

where we define:

$$
\Sigma = r^2 + a^2 \cos^2\theta
$$

$$
\Delta = r^2 - 2Mr + a^2
$$

$$
A = (r^2 + a^2)^2 - a^2 \Delta \sin^2\theta
$$

Here $M$ is the mass and $a = J/M$ is the spin parameter (angular momentum per unit mass).

## Parameters

| Parameter | Definition | Range |
|-----------|------------|-------|
| $M$ | Mass of the black hole | $M > 0$ |
| $a$ | Spin parameter $J/M$ | $0 \leq |a| \leq M$ |
| $J$ | Angular momentum | $J = Ma$ |

The dimensionless spin is often written as $a_* = a/M$, with $|a_*| \leq 1$ for black holes.

## Key Surfaces

### Event Horizons

The horizons occur where $\Delta = 0$:

$$
r_\pm = M \pm \sqrt{M^2 - a^2}
$$

- $r_+$ is the **outer horizon** (event horizon)
- $r_-$ is the **inner horizon** (Cauchy horizon)

For $a = 0$, we recover the Schwarzschild radius $r_+ = 2M$.

For $a = M$ (extremal), both horizons coincide at $r = M$.

### Ergosphere

The **static limit** occurs where $g_{tt} = 0$:

$$
r_E(\theta) = M + \sqrt{M^2 - a^2\cos^2\theta}
$$

The region between the static limit and the outer horizon is the **ergosphere**:

$$
r_+ < r < r_E(\theta)
$$

In the ergosphere, no observer can remain stationary—all must co-rotate with the black hole.

## Special Cases

| Condition | Spacetime |
|-----------|-----------|
| $a = 0$ | Schwarzschild (non-rotating) |
| $a = M$ | Extremal Kerr (maximum spin) |
| $a > M$ | Naked singularity (no horizon) |

## Frame Dragging

A key feature of the Kerr metric is **frame dragging**: spacetime itself is dragged around by the rotating mass. The angular velocity of a zero angular momentum observer (ZAMO) is:

$$
\omega = -\frac{g_{t\phi}}{g_{\phi\phi}} = \frac{2Mar}{A}
$$

This approaches $\omega \to a/(2Mr_+)$ at the horizon.

## The Ring Singularity

Unlike Schwarzschild, the Kerr singularity is not a point but a **ring** in the equatorial plane at:

$$
\Sigma = 0 \quad \Rightarrow \quad r = 0, \; \theta = \frac{\pi}{2}
$$

The ring has coordinate radius $a$ and can theoretically be traversed (though the interior geometry is likely unstable).

## Penrose Process

The ergosphere enables **energy extraction** from a rotating black hole. A particle entering the ergosphere can split, with one fragment falling into the black hole with negative energy (as measured at infinity), while the other escapes with more energy than the original particle.

The maximum extractable energy is:

$$
E_{\text{max}} = M\left(1 - \frac{1}{\sqrt{2}}\right) \approx 0.29M
$$

reducing the black hole to an irreducible mass $M_{\text{irr}} = M/\sqrt{2}$.

## Comparison with Schwarzschild

| Property | Schwarzschild | Kerr |
|----------|---------------|------|
| Symmetry | Spherical | Axial |
| Singularity | Point at $r=0$ | Ring at $r=0, \theta=\pi/2$ |
| Horizons | One at $r=2M$ | Two at $r_\pm$ |
| Ergosphere | None | Yes |
| Frame dragging | None | Yes |
| Parameters | $M$ | $M, a$ |
