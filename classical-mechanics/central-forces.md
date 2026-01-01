# Central Forces and Orbital Mechanics

Central forces—forces that point toward (or away from) a fixed center and depend only on distance—govern planetary motion, satellite orbits, and atomic physics. This document builds on [Newtonian mechanics](newtonian-mechanics.md) and [Lagrangian mechanics](lagrangian-mechanics.md). See [geodesics](../relativity/geodesics.md) for the relativistic treatment of orbits.

## Central Force Definition

A **central force** has the form:

$$
\mathbf{F} = F(r)\hat{\mathbf{r}}
$$

where $F(r)$ depends only on the distance from the force center, and $\hat{\mathbf{r}}$ points radially.

**Examples:**
- Gravity: $F(r) = -GMm/r^2$
- Coulomb: $F(r) = kq_1q_2/r^2$
- Spring: $F(r) = -k(r - r_0)$

## Conservation Laws

### Angular Momentum Conservation

For central forces, torque vanishes:

$$
\boldsymbol{\tau} = \mathbf{r} \times \mathbf{F} = \mathbf{r} \times F(r)\hat{\mathbf{r}} = 0
$$

Therefore:

$$
\mathbf{L} = \mathbf{r} \times \mathbf{p} = \text{constant}
$$

**Consequences:**
1. Motion is confined to a plane (perpendicular to $\mathbf{L}$)
2. $L = mr^2\dot{\theta}$ is constant

### Kepler's Second Law

$$
\frac{dA}{dt} = \frac{L}{2m} = \text{constant}
$$

**What this means:** Equal areas are swept out in equal times. Planets move faster when closer to the Sun.

### Energy Conservation

If $F(r) = -dV/dr$ (conservative):

$$
E = \frac{1}{2}m\dot{r}^2 + \frac{1}{2}mr^2\dot{\theta}^2 + V(r) = \text{constant}
$$

Using $L = mr^2\dot{\theta}$:

$$
E = \frac{1}{2}m\dot{r}^2 + \frac{L^2}{2mr^2} + V(r)
$$

## The Effective Potential

### Definition

$$
\boxed{V_{\text{eff}}(r) = V(r) + \frac{L^2}{2mr^2}}
$$

The term $L^2/(2mr^2)$ is the **centrifugal potential**—it creates a barrier that prevents collapse to $r = 0$.

### Energy Equation

$$
E = \frac{1}{2}m\dot{r}^2 + V_{\text{eff}}(r)
$$

**What this means:** The 2D problem reduces to 1D motion in the effective potential. Radial motion is like a particle moving in $V_{\text{eff}}(r)$.

### Orbit Classification

| $E$ vs $V_{\text{eff}}$ | Orbit Type |
|-------------------------|------------|
| $E < V_{\text{eff,min}}$ | Impossible |
| $E = V_{\text{eff,min}}$ | Circular orbit |
| $V_{\text{eff,min}} < E < 0$ | Bound (ellipse) |
| $E = 0$ | Marginally unbound (parabola) |
| $E > 0$ | Unbound (hyperbola) |

## Gravitational Orbits

### The Kepler Problem

For gravity: $V(r) = -GMm/r$

$$
V_{\text{eff}}(r) = -\frac{GMm}{r} + \frac{L^2}{2mr^2}
$$

### Circular Orbits

At the minimum of $V_{\text{eff}}$:

$$
\frac{dV_{\text{eff}}}{dr} = 0 \quad \Rightarrow \quad r_c = \frac{L^2}{GMm^2}
$$

**Orbital velocity:**
$$
v_c = \sqrt{\frac{GM}{r}}
$$

**Orbital period:**
$$
T = 2\pi\sqrt{\frac{r^3}{GM}}
$$

### The Orbit Equation

The trajectory $r(\theta)$ satisfies:

$$
\boxed{r = \frac{p}{1 + e\cos\theta}}
$$

where:
- $p = L^2/(GMm^2)$ is the **semi-latus rectum**
- $e = \sqrt{1 + \frac{2EL^2}{G^2M^2m^3}}$ is the **eccentricity**

### Conic Sections

| Eccentricity | Energy | Orbit Shape |
|--------------|--------|-------------|
| $e = 0$ | $E = E_{\min}$ | Circle |
| $0 < e < 1$ | $E < 0$ | Ellipse |
| $e = 1$ | $E = 0$ | Parabola |
| $e > 1$ | $E > 0$ | Hyperbola |

**What this means:** All orbits under inverse-square forces are conic sections. This was known empirically (Kepler) before Newton derived it from gravity.

## Elliptical Orbits

### Geometry

- **Semi-major axis:** $a = p/(1-e^2) = -GMm/(2E)$
- **Semi-minor axis:** $b = a\sqrt{1-e^2}$
- **Perihelion (closest):** $r_{\min} = a(1-e)$
- **Aphelion (farthest):** $r_{\max} = a(1+e)$

### Kepler's Laws

**First Law:** Planets orbit in ellipses with the Sun at one focus.

**Second Law:** Equal areas in equal times ($dA/dt = L/2m$).

**Third Law:**
$$
\boxed{T^2 = \frac{4\pi^2}{GM}a^3}
$$

**What this means:** The period squared is proportional to the semi-major axis cubed. This allows measuring masses from orbital observations.

### Orbital Energy and Angular Momentum

$$
E = -\frac{GMm}{2a}, \qquad L = m\sqrt{GMa(1-e^2)}
$$

### Vis-Viva Equation

The speed at any point:

$$
v^2 = GM\left(\frac{2}{r} - \frac{1}{a}\right)
$$

**What this means:** Given the position, this gives the speed without solving the full orbit.

## Escape Velocity

Setting $E = 0$ for a parabolic trajectory:

$$
v_{\text{esc}} = \sqrt{\frac{2GM}{r}}
$$

**From Earth's surface:** $v_{\text{esc}} \approx 11.2$ km/s

**What this means:** Objects launched at or above escape velocity will never return (ignoring other gravitational influences).

## Orbital Maneuvers

### Hohmann Transfer

To transfer between circular orbits of radii $r_1$ and $r_2$:

1. Burn to enter ellipse tangent to both circles
2. Coast to the other orbit
3. Burn to circularize

**Delta-v required:**
$$
\Delta v_{\text{total}} = \sqrt{\frac{GM}{r_1}}\left(\sqrt{\frac{2r_2}{r_1+r_2}} - 1\right) + \sqrt{\frac{GM}{r_2}}\left(1 - \sqrt{\frac{2r_1}{r_1+r_2}}\right)
$$

### Gravity Assist

Using a planet's gravity to change velocity without fuel. The spacecraft gains (or loses) energy relative to the Sun while conserving energy relative to the planet.

## The Two-Body Problem

### Reduced Mass

For two bodies of masses $m_1$ and $m_2$:

$$
\mu = \frac{m_1 m_2}{m_1 + m_2}
$$

The relative motion satisfies:

$$
\mu \ddot{\mathbf{r}} = \mathbf{F}(r)
$$

**What this means:** The two-body problem reduces to one body of reduced mass $\mu$ orbiting a fixed center. Both bodies actually orbit the common center of mass.

### Center of Mass Frame

Total mass $M = m_1 + m_2$

$$
\mathbf{r}_1 = -\frac{m_2}{M}\mathbf{r}, \qquad \mathbf{r}_2 = \frac{m_1}{M}\mathbf{r}
$$

For the Sun-Earth system, $m_{\text{Sun}} \gg m_{\text{Earth}}$, so $\mu \approx m_{\text{Earth}}$ and the Sun barely moves.

## Perturbations and Stability

### Precession

Real orbits precess due to:
- Other planets (Newtonian perturbation)
- Oblateness of central body
- General relativity (Mercury's perihelion advance)

### Stability of Circular Orbits

A circular orbit at $r_0$ is stable if:

$$
\left.\frac{d^2V_{\text{eff}}}{dr^2}\right|_{r_0} > 0
$$

For power-law forces $F \propto r^n$: stable if $n > -3$.

**What this means:** Gravity ($n = -2$) gives stable orbits. For $n \leq -3$, perturbations grow—orbits are unstable.

## The Runge-Lenz Vector

For inverse-square forces, there's an additional conserved quantity:

$$
\mathbf{A} = \mathbf{v} \times \mathbf{L} - GMm\hat{\mathbf{r}}
$$

**What this means:** This vector points toward perihelion and has constant magnitude $A = GMme$. Its conservation explains why Kepler orbits are closed (don't precess). This hidden symmetry leads to the "accidental" degeneracy in the [hydrogen atom](../quantum-mechanics/hydrogen-atom.md).

## Connection to Quantum Mechanics

The Kepler problem has a quantum analog—the hydrogen atom. The correspondence:

| Classical | Quantum |
|-----------|---------|
| Bound orbits ($E < 0$) | Discrete energy levels |
| Angular momentum $L$ | $\ell(\ell+1)\hbar^2$ quantized |
| Runge-Lenz conservation | $\ell$-degeneracy of energy levels |
| Circular orbit | Most probable radius for high $n$ |

See [hydrogen atom](../quantum-mechanics/hydrogen-atom.md) for the quantum treatment.

## Summary

| Concept | Formula | Meaning |
|---------|---------|---------|
| Central force | $\mathbf{F} = F(r)\hat{\mathbf{r}}$ | Radial, distance-dependent |
| Angular momentum | $L = mr^2\dot{\theta}$ | Conserved; confines to plane |
| Effective potential | $V_{\text{eff}} = V(r) + L^2/(2mr^2)$ | Reduces to 1D problem |
| Orbit equation | $r = p/(1 + e\cos\theta)$ | Conic section |
| Kepler's 3rd law | $T^2 \propto a^3$ | Period from size |
| Escape velocity | $v_{\text{esc}} = \sqrt{2GM/r}$ | Minimum to escape |

**The essential insight:** Central force problems are exactly solvable because angular momentum conservation reduces the 2D problem to 1D motion in an effective potential. For gravity, orbits are conic sections—ellipses for bound motion. This same mathematical structure, with quantum modifications, describes the hydrogen atom, making orbital mechanics a gateway to quantum physics.
