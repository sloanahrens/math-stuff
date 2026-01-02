# Numerical Methods for Physics

When analytical solutions fail, numerical methods provide answers. This document covers the essential computational techniques every physicist needs: root finding, ODE integration, PDE discretization, and Monte Carlo sampling. Prerequisites: [calculus](calculus-primer.md), [linear algebra](linear-algebra.md), [probability](probability-statistics.md).

## Root Finding

### The Problem

Find $x$ such that $f(x) = 0$.

### Bisection Method

Given $f(a)$ and $f(b)$ with opposite signs:

1. Compute midpoint $c = (a + b)/2$
2. If $f(c) = 0$ or interval small enough, done
3. If $f(a)f(c) < 0$, set $b = c$; else set $a = c$
4. Repeat

**Convergence:** Linear. Error halves each iteration: $\epsilon_n = \epsilon_0 / 2^n$

**Pros:** Always converges (if root bracketed)
**Cons:** Slow

### Newton-Raphson Method

```math
\boxed{x_{n+1} = x_n - \frac{f(x_n)}{f'(x_n)}}
```

**Convergence:** Quadratic near root. Error squares: $\epsilon_{n+1} \sim \epsilon_n^2$

**Pros:** Very fast when it works
**Cons:** Requires derivative; can diverge; sensitive to initial guess

### Secant Method

Approximate derivative using two points:

```math
x_{n+1} = x_n - f(x_n)\frac{x_n - x_{n-1}}{f(x_n) - f(x_{n-1})}
```

**Convergence:** Superlinear ($\sim 1.618$)

No derivative needed; nearly as fast as Newton.

### When to Use What

| Method | Use When |
|--------|----------|
| Bisection | Need guaranteed convergence |
| Newton | Have derivative, good initial guess |
| Secant | No derivative available |
| Hybrid | Combine bisection safety with Newton speed |

## Ordinary Differential Equations

### Initial Value Problems

Solve $\frac{dy}{dt} = f(t, y)$ with $y(t_0) = y_0$.

### Euler's Method

```math
y_{n+1} = y_n + h f(t_n, y_n)
```

**Error:** $O(h)$ per step, $O(h)$ global (first-order)

Simple but inaccurate; rarely used in practice.

### Runge-Kutta Methods

**RK4 (Fourth-order Runge-Kutta):**

```math
\boxed{y_{n+1} = y_n + \frac{h}{6}(k_1 + 2k_2 + 2k_3 + k_4)}
```

where:
```math
k_1 = f(t_n, y_n)
```
```math
k_2 = f(t_n + h/2, y_n + hk_1/2)
```
```math
k_3 = f(t_n + h/2, y_n + hk_2/2)
```
```math
k_4 = f(t_n + h, y_n + hk_3)
```

**Error:** $O(h^4)$ per step, $O(h^4)$ global

**What this means:** RK4 is the workhorse of ODE integration. Four function evaluations per step give fourth-order accuracy—good balance of cost and precision.

### Adaptive Step Size

Adjust $h$ based on error estimate:
- Compare RK4 and RK5 results
- If error too large, reduce $h$
- If error very small, increase $h$

Common implementations: RK45 (Dormand-Prince), RK23

### Stiff Equations

When timescales differ greatly, explicit methods require tiny steps.

**Implicit methods** (e.g., backward Euler) are stable for stiff problems:

```math
y_{n+1} = y_n + h f(t_{n+1}, y_{n+1})
```

Requires solving nonlinear equation at each step.

### Symplectic Integrators

For Hamiltonian systems, preserve phase space structure.

**Leapfrog (Störmer-Verlet):**

```math
p_{n+1/2} = p_n - \frac{h}{2}\nabla V(q_n)
```
```math
q_{n+1} = q_n + h \frac{p_{n+1/2}}{m}
```
```math
p_{n+1} = p_{n+1/2} - \frac{h}{2}\nabla V(q_{n+1})
```

**What this means:** Energy may oscillate but doesn't drift—essential for long-term orbital mechanics.

## Partial Differential Equations

### Finite Difference Method

Replace derivatives with difference quotients on a grid.

**First derivative:**
```math
\frac{\partial u}{\partial x} \approx \frac{u_{i+1} - u_{i-1}}{2\Delta x} + O(\Delta x^2)
```

**Second derivative:**
```math
\frac{\partial^2 u}{\partial x^2} \approx \frac{u_{i+1} - 2u_i + u_{i-1}}{\Delta x^2} + O(\Delta x^2)
```

### Heat Equation (Diffusion)

```math
\frac{\partial u}{\partial t} = \alpha \frac{\partial^2 u}{\partial x^2}
```

**FTCS (Forward Time, Centered Space):**

```math
u_i^{n+1} = u_i^n + r(u_{i+1}^n - 2u_i^n + u_{i-1}^n)
```

where $r = \alpha\Delta t/\Delta x^2$.

**Stability:** Requires $r \leq 1/2$ (CFL condition)

**Implicit (Crank-Nicolson):** Unconditionally stable, second-order in time.

### Wave Equation

```math
\frac{\partial^2 u}{\partial t^2} = c^2 \frac{\partial^2 u}{\partial x^2}
```

**Explicit scheme:**

```math
u_i^{n+1} = 2u_i^n - u_i^{n-1} + r^2(u_{i+1}^n - 2u_i^n + u_{i-1}^n)
```

where $r = c\Delta t/\Delta x$.

**Stability:** Requires $r \leq 1$ (CFL condition)

### Laplace/Poisson Equations

```math
\nabla^2 u = f
```

**Relaxation methods:**

*Jacobi:* Update all points using old values
*Gauss-Seidel:* Use new values as soon as available
*SOR (Successive Over-Relaxation):* Accelerate with parameter $\omega$

```math
u_i^{new} = (1-\omega)u_i^{old} + \omega \cdot (\text{Gauss-Seidel update})
```

Optimal $\omega \approx 2 - O(1/N)$ for $N \times N$ grid.

### Spectral Methods

Expand in basis functions (Fourier, Chebyshev).

For periodic problems, FFT gives $O(N\log N)$ speed.

Much higher accuracy for smooth solutions.

## Linear Algebra

### Direct Methods

**Gaussian elimination:** $O(N^3)$ for $N \times N$ system

**LU decomposition:** Factor $A = LU$, then solve $Ly = b$, $Ux = y$

**Cholesky:** For symmetric positive-definite: $A = LL^T$

### Iterative Methods

For large sparse systems, direct methods are too slow.

**Jacobi iteration:**
```math
x_i^{(k+1)} = \frac{1}{a_{ii}}\left(b_i - \sum_{j \neq i} a_{ij}x_j^{(k)}\right)
```

**Gauss-Seidel:** Use updated values immediately

**Conjugate gradient:** For symmetric positive-definite; converges in $N$ steps (exact arithmetic)

### Eigenvalue Problems

**Power method:** Find largest eigenvalue by iteration

**QR algorithm:** Find all eigenvalues; $O(N^3)$

**Lanczos:** For large sparse matrices; finds extreme eigenvalues

## Monte Carlo Methods

### Random Sampling

Estimate integrals by averaging random samples:

```math
\boxed{\int f(x)dx \approx \frac{V}{N}\sum_{i=1}^N f(x_i)}
```

where $V$ is the volume and $x_i$ are random points.

**Error:** $O(1/\sqrt{N})$ regardless of dimension

**What this means:** Monte Carlo wins in high dimensions where grid methods suffer the "curse of dimensionality."

### Importance Sampling

Sample from distribution $p(x)$ instead of uniformly:

```math
\int f(x)dx = \int \frac{f(x)}{p(x)}p(x)dx \approx \frac{1}{N}\sum_{i=1}^N \frac{f(x_i)}{p(x_i)}
```

Choose $p(x) \propto |f(x)|$ to reduce variance.

### Markov Chain Monte Carlo (MCMC)

Sample from distribution $\pi(x)$ using random walk.

**Metropolis algorithm:**

1. Propose move $x \to x'$
2. Accept with probability $\min(1, \pi(x')/\pi(x))$
3. Repeat

Generates samples from $\pi$ after equilibration.

**Applications:** [Statistical mechanics](../thermodynamics/statistical-mechanics.md), Bayesian inference, lattice QCD

### Random Number Generation

**Linear congruential:** $x_{n+1} = (ax_n + c) \mod m$

**Mersenne Twister:** Period $2^{19937} - 1$; standard in most libraries

**Cryptographic:** For security applications

## Error Analysis

### Truncation Error

From approximating continuous operations discretely.

Example: Taylor series truncation in finite differences.

### Round-off Error

From finite precision arithmetic.

**Machine epsilon:** Smallest $\epsilon$ such that $1 + \epsilon \neq 1$ in floating point.

Double precision: $\epsilon \approx 2 \times 10^{-16}$

### Stability

**Stable algorithm:** Errors don't grow uncontrollably

**Unstable algorithm:** Small errors amplify exponentially

Example: Forward vs backward recurrence for Bessel functions.

### Condition Number

```math
\kappa(A) = \|A\| \cdot \|A^{-1}\|
```

Measures sensitivity of solution to input perturbations.

Large $\kappa$ means ill-conditioned; results unreliable.

## Practical Considerations

### Choosing a Method

| Problem Type | Recommended Methods |
|--------------|---------------------|
| ODE (general) | RK45, LSODA |
| ODE (Hamiltonian) | Symplectic (leapfrog) |
| ODE (stiff) | BDF, implicit methods |
| PDE (parabolic) | Crank-Nicolson |
| PDE (hyperbolic) | Upwind, Lax-Wendroff |
| PDE (elliptic) | Multigrid, FFT |
| High-dimensional integral | Monte Carlo |
| Eigenvalues (few) | Lanczos, power method |
| Eigenvalues (all) | QR algorithm |

### Verification

1. **Convergence test:** Refine grid, check solution changes appropriately
2. **Conservation:** Check energy, momentum, probability conservation
3. **Analytical limits:** Compare to known solutions
4. **Symmetry:** Check expected symmetries preserved

### Common Pitfalls

- Using too large a time step (violating CFL)
- Ignoring boundary conditions
- Not checking convergence
- Accumulating round-off error
- Using wrong method for problem type (e.g., explicit for stiff ODEs)

## Summary

| Method | Application | Typical Error |
|--------|-------------|---------------|
| Bisection | Root finding | Linear convergence |
| Newton-Raphson | Root finding | Quadratic convergence |
| RK4 | ODE integration | $O(h^4)$ |
| Leapfrog | Hamiltonian systems | $O(h^2)$, symplectic |
| FTCS | Diffusion equation | $O(\Delta t, \Delta x^2)$ |
| Crank-Nicolson | Diffusion equation | $O(\Delta t^2, \Delta x^2)$ |
| Monte Carlo | Integration | $O(1/\sqrt{N})$ |

| Concept | Key Point |
|---------|-----------|
| CFL condition | Stability constraint on time step |
| Stiffness | Widely separated timescales |
| Symplectic | Preserves phase space structure |
| Condition number | Sensitivity to perturbations |
| Importance sampling | Reduce Monte Carlo variance |

**The essential insight:** Numerical methods convert continuous physics into discrete computations. The art is matching method to problem: explicit methods for non-stiff ODEs, implicit for stiff; symplectic integrators for Hamiltonian systems; spectral methods for smooth solutions; Monte Carlo for high dimensions. Always verify results through convergence tests, conservation laws, and comparison to known limits. These tools enable solutions to problems across all areas of physics—from [orbital mechanics](../classical-mechanics/central-forces.md) to [quantum systems](../quantum-mechanics/quantum-mechanics.md) to [statistical ensembles](../thermodynamics/statistical-mechanics.md).
