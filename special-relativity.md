# Special Relativity

Special relativity describes physics in inertial (non-accelerating) reference frames, where the speed of light is constant for all observers. This document provides the foundation for [the Dirac equation](dirac-equation.md), [covariant electromagnetism](maxwell-covariant.md), and the transition to general relativity ([Schwarzschild](schwarzschild-solution.md), [Kerr](kerr-metric.md)).

## The Postulates

Einstein's 1905 theory rests on two postulates:

1. **Principle of Relativity**: The laws of physics are the same in all inertial reference frames
2. **Constancy of Light Speed**: The speed of light in vacuum is $c$ for all inertial observers, regardless of their motion or the motion of the source

**What this means:** There is no preferred "rest frame" of the universe. An observer moving at constant velocity has just as valid a perspective as one "at rest." And light always travels at $c \approx 3 \times 10^8$ m/s—you can't catch up to a light beam.

## Time Dilation

A moving clock runs slower. If a clock at rest measures time $\Delta t_0$, an observer seeing it move at velocity $v$ measures:

$$
\boxed{\Delta t = \gamma \Delta t_0 = \frac{\Delta t_0}{\sqrt{1 - v^2/c^2}}}
$$

where the **Lorentz factor** is:

$$
\gamma = \frac{1}{\sqrt{1 - v^2/c^2}}
$$

**What this means:** Time itself passes at different rates for different observers. A muon created in the upper atmosphere traveling at $0.99c$ has $\gamma \approx 7$, so its 2.2 μs lifetime becomes 15 μs in Earth's frame—allowing it to reach the ground.

### Example Values

| $v/c$ | $\gamma$ | Effect |
|-------|----------|--------|
| 0.1 | 1.005 | 0.5% slower |
| 0.5 | 1.15 | 15% slower |
| 0.9 | 2.29 | 2.3× slower |
| 0.99 | 7.09 | 7× slower |
| 0.999 | 22.4 | 22× slower |

## Length Contraction

A moving object is shortened along its direction of motion:

$$
\boxed{L = \frac{L_0}{\gamma} = L_0 \sqrt{1 - v^2/c^2}}
$$

where $L_0$ is the **proper length** (measured in the object's rest frame).

**What this means:** A meter stick flying past you at $0.9c$ appears only 44 cm long. This isn't an optical illusion—it's how space itself relates between moving frames.

## Relativity of Simultaneity

Events simultaneous in one frame are not simultaneous in another. If two events are separated by distance $\Delta x$ and are simultaneous in frame $S$, in frame $S'$ moving at velocity $v$:

$$
\Delta t' = -\gamma \frac{v \Delta x}{c^2}
$$

**What this means:** "Now" is not universal. Two observers can disagree about which of two distant events happened first—and both are correct in their own frames.

## Spacetime and 4-Vectors

### Minkowski Spacetime

Space and time unite into **spacetime**. An event has coordinates:

$$
x^\mu = (ct, x, y, z) = (x^0, x^1, x^2, x^3)
$$

We often use [natural units](natural-units.md) where $c = 1$, so $x^\mu = (t, x, y, z)$.

**What this means:** Just as 3D space has points labeled by $(x, y, z)$, 4D spacetime has events labeled by $(t, x, y, z)$. The geometry of this spacetime encodes all of special relativity.

### The Spacetime Interval

The **invariant interval** between two events:

$$
\boxed{(\Delta s)^2 = -c^2(\Delta t)^2 + (\Delta x)^2 + (\Delta y)^2 + (\Delta z)^2}
$$

Or in natural units with metric signature $(-,+,+,+)$:

$$
(\Delta s)^2 = \eta_{\mu\nu} \Delta x^\mu \Delta x^\nu
$$

where the **Minkowski metric** is:

$$
\eta_{\mu\nu} = \begin{pmatrix} -1 & 0 & 0 & 0 \\ 0 & 1 & 0 & 0 \\ 0 & 0 & 1 & 0 \\ 0 & 0 & 0 & 1 \end{pmatrix}
$$

**What this means:** While observers disagree on $\Delta t$ and $\Delta x$ separately, they all agree on $(\Delta s)^2$. This is the relativistic analog of how rotated observers in 3D disagree on $\Delta x$ and $\Delta y$ but agree on the distance $\sqrt{(\Delta x)^2 + (\Delta y)^2}$.

### Timelike, Spacelike, Lightlike

| Type | Condition | Physical Meaning |
|------|-----------|------------------|
| Timelike | $(\Delta s)^2 < 0$ | Events can be causally connected; a massive particle can travel between them |
| Lightlike (null) | $(\Delta s)^2 = 0$ | Light can travel between them |
| Spacelike | $(\Delta s)^2 > 0$ | No causal connection possible; events are "elsewhere" |

## Lorentz Transformations

### The Boost

For motion along the $x$-axis at velocity $v$:

$$
\boxed{
\begin{aligned}
t' &= \gamma \left( t - \frac{vx}{c^2} \right) \\
x' &= \gamma (x - vt) \\
y' &= y \\
z' &= z
\end{aligned}
}
$$

In matrix form (with $c = 1$):

$$
\begin{pmatrix} t' \\ x' \\ y' \\ z' \end{pmatrix} = \begin{pmatrix} \gamma & -\gamma v & 0 & 0 \\ -\gamma v & \gamma & 0 & 0 \\ 0 & 0 & 1 & 0 \\ 0 & 0 & 0 & 1 \end{pmatrix} \begin{pmatrix} t \\ x \\ y \\ z \end{pmatrix}
$$

**What this means:** This is how coordinates transform between frames. It mixes space and time—a boost in space affects the time coordinate and vice versa.

### Rapidity

Define **rapidity** $\phi$ by $\tanh \phi = v/c$. Then $\gamma = \cosh \phi$ and $\gamma v = c \sinh \phi$, giving:

$$
\begin{pmatrix} ct' \\ x' \end{pmatrix} = \begin{pmatrix} \cosh \phi & -\sinh \phi \\ -\sinh \phi & \cosh \phi \end{pmatrix} \begin{pmatrix} ct \\ x \end{pmatrix}
$$

**What this means:** This looks like a rotation, but with hyperbolic functions instead of trigonometric ones. Rapidities add simply: consecutive boosts of $\phi_1$ and $\phi_2$ give total rapidity $\phi_1 + \phi_2$.

### The Lorentz Group

Lorentz transformations form a group $SO(3,1)$—see [Lie groups](lie-groups.md). It includes:
- 3 spatial rotations
- 3 boosts (velocity changes along each axis)

This 6-parameter group is the symmetry group of special relativity.

## 4-Vectors

A **4-vector** transforms like spacetime coordinates under Lorentz transformations:

$$
A'^\mu = \Lambda^\mu{}_\nu A^\nu
$$

### Important 4-Vectors

**4-velocity:**

$$
U^\mu = \frac{dx^\mu}{d\tau} = \gamma(c, \mathbf{v})
$$

where $\tau$ is proper time. Note: $U^\mu U_\mu = -c^2$ (always!).

**What this means:** The 4-velocity has constant "length" in spacetime. As you speed up in space, your rate of movement through time adjusts to keep this length fixed.

**4-momentum:**

$$
p^\mu = mU^\mu = (E/c, \mathbf{p}) = (\gamma mc, \gamma m\mathbf{v})
$$

The invariant:

$$
p^\mu p_\mu = -m^2 c^2
$$

gives:

$$
\boxed{E^2 = (pc)^2 + (mc^2)^2}
$$

**What this means:** This is the relativistic energy-momentum relation. For a particle at rest ($p = 0$), it gives $E = mc^2$. For massless particles ($m = 0$), it gives $E = pc$.

**4-current:**

$$
J^\mu = (\rho c, \mathbf{J})
$$

where $\rho$ is charge density and $\mathbf{J}$ is current density—see [Maxwell covariant](maxwell-covariant.md).

## Relativistic Energy and Momentum

### Total Energy

$$
E = \gamma mc^2
$$

For small velocities ($v \ll c$):

$$
E \approx mc^2 + \frac{1}{2}mv^2
$$

**What this means:** The total energy has two parts: rest energy $mc^2$ and kinetic energy. At low speeds, the kinetic part reduces to the classical $\frac{1}{2}mv^2$.

### Relativistic Momentum

$$
\mathbf{p} = \gamma m\mathbf{v}
$$

As $v \to c$, momentum grows without bound ($\gamma \to \infty$), preventing massive objects from reaching light speed.

### Kinetic Energy

$$
K = E - mc^2 = (\gamma - 1)mc^2
$$

### Massless Particles

For photons ($m = 0$):

$$
E = pc, \quad v = c
$$

Photons always travel at $c$ and have momentum despite being massless.

## Velocity Addition

If object A moves at velocity $u$ relative to B, and B moves at velocity $v$ relative to C (all along the same direction), then A's velocity relative to C is:

$$
\boxed{w = \frac{u + v}{1 + uv/c^2}}
$$

**What this means:** Velocities don't simply add. Even if $u = 0.9c$ and $v = 0.9c$, the result is $w = 0.994c$—still less than $c$. You can never exceed light speed by combining subluminal velocities.

### Light Speed is Invariant

If $u = c$:

$$
w = \frac{c + v}{1 + cv/c^2} = \frac{c + v}{1 + v/c} = c
$$

Light travels at $c$ in all frames, regardless of the source's motion.

## Doppler Effect

### Relativistic Doppler Shift

For a source moving away at velocity $v$:

$$
\boxed{f_{obs} = f_{source} \sqrt{\frac{1 - v/c}{1 + v/c}}}
$$

For approach, flip the sign of $v$.

**What this means:** Light from receding objects is redshifted; from approaching objects, blueshifted. This is how we measure the expansion of the universe.

### Transverse Doppler Effect

Even for perpendicular motion, there's a redshift:

$$
f_{obs} = \frac{f_{source}}{\gamma}
$$

**What this means:** This is purely relativistic—it's time dilation directly observed. A clock moving perpendicular to your line of sight ticks slowly, and its light is redshifted.

## Proper Time and the Twin Paradox

### Proper Time

The **proper time** $\tau$ along a worldline is:

$$
d\tau = \frac{ds}{c} = dt\sqrt{1 - v^2/c^2} = \frac{dt}{\gamma}
$$

Integrated:

$$
\tau = \int \frac{dt}{\gamma(t)}
$$

**What this means:** Proper time is what a clock measures along its own worldline. Different paths through spacetime accumulate different proper times.

### Twin Paradox

Twin A stays on Earth; Twin B travels to a star and back at high speed. When B returns, B is younger than A.

**Resolution:** The situation is not symmetric. B accelerates (turns around), experiencing different spacetime geometry. The straight (inertial) path through spacetime has the *longest* proper time—the opposite of Euclidean geometry where straight lines are shortest.

## Connection to General Relativity

Special relativity applies in flat spacetime (no gravity). General relativity extends it:

- The Minkowski metric $\eta_{\mu\nu}$ becomes the general metric $g_{\mu\nu}$
- Lorentz transformations become general coordinate transformations
- Inertial frames exist only locally in curved spacetime

See [tensor calculus](tensor-calculus.md) for the mathematical machinery and [Schwarzschild](schwarzschild-solution.md)/[Kerr](kerr-metric.md) for curved spacetime solutions.

## Summary

| Concept | Formula | Meaning |
|---------|---------|---------|
| Time dilation | $\Delta t = \gamma \Delta t_0$ | Moving clocks run slow |
| Length contraction | $L = L_0/\gamma$ | Moving objects are shortened |
| Lorentz factor | $\gamma = 1/\sqrt{1-v^2/c^2}$ | Universal relativistic factor |
| Spacetime interval | $ds^2 = -c^2dt^2 + dx^2 + dy^2 + dz^2$ | Invariant "distance" in spacetime |
| Energy-momentum | $E^2 = (pc)^2 + (mc^2)^2$ | Unifies energy and momentum |
| Rest energy | $E = mc^2$ | Mass is energy |
| Velocity addition | $w = (u+v)/(1+uv/c^2)$ | Velocities don't simply add |

**The essential insight:** Space and time are not separate entities but components of a unified spacetime. Different observers slice spacetime differently, disagreeing about time intervals and spatial distances, but agreeing on spacetime intervals. The speed of light is the cosmic speed limit that enforces causality.
