# Fourier Analysis

Fourier analysis decomposes functions into sums of sinusoids, revealing the frequency content hidden in signals and solutions. It is fundamental to [quantum mechanics](../quantum-mechanics/quantum-mechanics.md) (momentum space), [electromagnetism](../electromagnetism/electromagnetic-waves.md) (wave decomposition), and signal processing. Prerequisites: [calculus](calculus-primer.md), [Euler's formula](euler-formula.md), [trigonometry](trigonometry-primer.md).

## Fourier Series

### Periodic Functions

A function $f(x)$ is **periodic** with period $L$ if $f(x + L) = f(x)$ for all $x$. The fundamental frequency is $\omega_0 = 2\pi/L$.

### The Fourier Series (Trigonometric Form)

Any reasonable periodic function can be written as:

```math
\boxed{f(x) = \frac{a_0}{2} + \sum_{n=1}^{\infty} \left[ a_n \cos\left(\frac{2\pi nx}{L}\right) + b_n \sin\left(\frac{2\pi nx}{L}\right) \right]}
```

The coefficients are:

```math
a_n = \frac{2}{L} \int_0^L f(x) \cos\left(\frac{2\pi nx}{L}\right) dx
```

```math
b_n = \frac{2}{L} \int_0^L f(x) \sin\left(\frac{2\pi nx}{L}\right) dx
```

**What this means:** Any periodic signal can be built from pure sinusoids. The coefficients tell you "how much" of each frequency is present.

### Complex Exponential Form

Using [Euler's formula](euler-formula.md), the series becomes more elegant:

```math
\boxed{f(x) = \sum_{n=-\infty}^{\infty} c_n e^{2\pi inx/L}}
```

with coefficients:

```math
\boxed{c_n = \frac{1}{L} \int_0^L f(x) e^{-2\pi inx/L} dx}
```

The connection: $c_0 = a_0/2$, and for $n > 0$: $c_n = (a_n - ib_n)/2$, $c_{-n} = (a_n + ib_n)/2$.

**What this means:** Complex exponentials are the natural basis for Fourier analysis. Negative frequencies correspond to clockwise rotation in the complex plane.

### Convergence

For $f$ piecewise continuous with piecewise continuous derivative:
- At continuity points: series converges to $f(x)$
- At discontinuities: series converges to $\frac{1}{2}[f(x^+) + f(x^-)]$

The **Gibbs phenomenon**: near discontinuities, partial sums overshoot by about 9%, regardless of how many terms are used.

## Examples of Fourier Series

### Square Wave

```math
f(x) = \begin{cases} 1 & 0 < x < \pi \\ -1 & \pi < x < 2\pi \end{cases}
```

Fourier series ($L = 2\pi$):

```math
f(x) = \frac{4}{\pi} \sum_{n=1,3,5,\ldots} \frac{\sin(nx)}{n} = \frac{4}{\pi}\left(\sin x + \frac{\sin 3x}{3} + \frac{\sin 5x}{5} + \cdots\right)
```

**What this means:** A square wave contains only odd harmonics, with amplitudes decreasing as $1/n$.

### Sawtooth Wave

```math
f(x) = x \quad \text{for } -\pi < x < \pi, \quad \text{period } 2\pi
```

Fourier series:

```math
f(x) = 2\sum_{n=1}^{\infty} \frac{(-1)^{n+1}}{n} \sin(nx) = 2\left(\sin x - \frac{\sin 2x}{2} + \frac{\sin 3x}{3} - \cdots\right)
```

### Triangle Wave

```math
f(x) = |x| \quad \text{for } -\pi < x < \pi
```

Fourier series:

```math
f(x) = \frac{\pi}{2} - \frac{4}{\pi} \sum_{n=1,3,5,\ldots} \frac{\cos(nx)}{n^2}
```

Coefficients decay as $1/n^2$ because the function is continuous (smoother = faster decay).

## Parseval's Theorem

### Energy Conservation

```math
\boxed{\frac{1}{L} \int_0^L |f(x)|^2 dx = \sum_{n=-\infty}^{\infty} |c_n|^2}
```

In trigonometric form:

```math
\frac{1}{L} \int_0^L |f(x)|^2 dx = \frac{a_0^2}{4} + \frac{1}{2}\sum_{n=1}^{\infty} (a_n^2 + b_n^2)
```

**What this means:** The total "energy" (integral of $|f|^2$) equals the sum of energies in each frequency component. Energy is conserved when switching between time and frequency domains.

### Application: Summing Series

Setting $x = 0$ in the sawtooth series gives nothing useful, but Parseval's theorem yields:

```math
\frac{1}{2\pi} \int_{-\pi}^{\pi} x^2 dx = \sum_{n=1}^{\infty} \frac{1}{n^2}
```

```math
\frac{\pi^2}{3} = 2\sum_{n=1}^{\infty} \frac{1}{n^2} \quad \Rightarrow \quad \sum_{n=1}^{\infty} \frac{1}{n^2} = \frac{\pi^2}{6}
```

## The Fourier Transform

### From Series to Transform

For non-periodic functions, let $L \to \infty$. The discrete frequencies become continuous, and sums become integrals:

```math
\boxed{\hat{f}(k) = \int_{-\infty}^{\infty} f(x) e^{-ikx} dx}
```

```math
\boxed{f(x) = \frac{1}{2\pi} \int_{-\infty}^{\infty} \hat{f}(k) e^{ikx} dk}
```

**What this means:** $\hat{f}(k)$ is the amplitude density at wavenumber $k$. The function and its transform contain the same information in different representations.

### Alternative Conventions

Different fields use different normalizations:

| Convention | Transform | Inverse | Used in |
|------------|-----------|---------|---------|
| Physics | $\int f e^{-ikx} dx$ | $\frac{1}{2\pi}\int \hat{f} e^{ikx} dk$ | Wave mechanics |
| Symmetric | $\frac{1}{\sqrt{2\pi}}\int f e^{-ikx} dx$ | $\frac{1}{\sqrt{2\pi}}\int \hat{f} e^{ikx} dk$ | Quantum mechanics |
| Engineering | $\int f e^{-2\pi i\nu x} dx$ | $\int \hat{f} e^{2\pi i\nu x} d\nu$ | Signal processing |

All are equivalent up to factors of $2\pi$.

## Properties of the Fourier Transform

### Linearity

```math
\mathcal{F}[af + bg] = a\mathcal{F}[f] + b\mathcal{F}[g]
```

### Shift Theorem

```math
\mathcal{F}[f(x - a)] = e^{-ika} \hat{f}(k)
```

**What this means:** Shifting in position adds a phase in frequency space. This is why wave packets propagate.

### Modulation Theorem

```math
\mathcal{F}[e^{ik_0 x} f(x)] = \hat{f}(k - k_0)
```

Multiplying by a complex exponential shifts the spectrum.

### Scaling

```math
\mathcal{F}[f(ax)] = \frac{1}{|a|} \hat{f}(k/a)
```

**What this means:** Compressing in space spreads in frequency (and vice versa). This is the uncertainty principle in disguise.

### Derivative Theorem

```math
\mathcal{F}[f'(x)] = ik \hat{f}(k)
```

```math
\mathcal{F}[f^{(n)}(x)] = (ik)^n \hat{f}(k)
```

**What this means:** Differentiation becomes multiplication. This turns differential equations into algebraic equations.

### Convolution Theorem

```math
\boxed{\mathcal{F}[f * g] = \hat{f}(k) \cdot \hat{g}(k)}
```

where the **convolution** is:

```math
(f * g)(x) = \int_{-\infty}^{\infty} f(x') g(x - x') dx'
```

**What this means:** Convolution in real space is multiplication in Fourier space. This is why Fourier methods simplify linear systems.

### Parseval's Theorem (Transform Version)

```math
\boxed{\int_{-\infty}^{\infty} |f(x)|^2 dx = \frac{1}{2\pi} \int_{-\infty}^{\infty} |\hat{f}(k)|^2 dk}
```

Energy is preserved between domains.

## Important Fourier Transform Pairs

| Function $f(x)$ | Transform $\hat{f}(k)$ |
|-----------------|------------------------|
| $e^{-a|x|}$ ($a > 0$) | $\frac{2a}{a^2 + k^2}$ |
| $e^{-ax^2}$ | $\sqrt{\frac{\pi}{a}} e^{-k^2/4a}$ |
| $\frac{1}{x^2 + a^2}$ | $\frac{\pi}{a} e^{-a|k|}$ |
| $\text{rect}(x/a)$ | $a \, \text{sinc}(ka/2)$ |
| $\delta(x)$ | $1$ |
| $1$ | $2\pi \delta(k)$ |
| $e^{ik_0 x}$ | $2\pi \delta(k - k_0)$ |
| $\cos(k_0 x)$ | $\pi[\delta(k-k_0) + \delta(k+k_0)]$ |

where $\text{sinc}(u) = \sin(u)/u$ and $\text{rect}(u) = 1$ for $|u| < 1/2$, else $0$.

**What this means:** A Gaussian transforms to a Gaussian—it's the unique function equal to its own Fourier transform (up to scaling). The delta function has all frequencies equally.

## The Uncertainty Principle

### Width Definitions

For a function $f(x)$ and its transform $\hat{f}(k)$:

```math
\Delta x = \sqrt{\langle x^2 \rangle - \langle x \rangle^2}, \qquad \Delta k = \sqrt{\langle k^2 \rangle - \langle k \rangle^2}
```

### The Inequality

```math
\boxed{\Delta x \cdot \Delta k \geq \frac{1}{2}}
```

Equality holds only for Gaussian functions.

**What this means:** A function cannot be simultaneously localized in both position and frequency. This is the mathematical basis for the [Heisenberg uncertainty principle](../quantum-mechanics/quantum-mechanics.md) in quantum mechanics, where $k = p/\hbar$.

## The Discrete Fourier Transform

### Definition

For a sequence of $N$ samples $\{f_0, f_1, \ldots, f_{N-1}\}$:

```math
\hat{f}_m = \sum_{n=0}^{N-1} f_n e^{-2\pi imn/N}, \qquad m = 0, 1, \ldots, N-1
```

```math
f_n = \frac{1}{N} \sum_{m=0}^{N-1} \hat{f}_m e^{2\pi imn/N}
```

### The Fast Fourier Transform (FFT)

Direct computation: $O(N^2)$ operations.

**FFT algorithm** (Cooley-Tukey): $O(N \log N)$ operations.

**What this means:** The FFT makes spectral analysis practical for large datasets. It's one of the most important algorithms in computational science.

### Sampling and Aliasing

The **Nyquist theorem**: To capture a signal with maximum frequency $f_{\max}$, sample at rate $f_s > 2f_{\max}$.

**Aliasing**: Undersampling makes high frequencies appear as low frequencies—the signal "folds" onto itself.

## Applications in Physics

### Quantum Mechanics

Position and momentum are Fourier conjugates:

```math
\tilde{\psi}(p) = \frac{1}{\sqrt{2\pi\hbar}} \int_{-\infty}^{\infty} \psi(x) e^{-ipx/\hbar} dx
```

The uncertainty principle $\Delta x \cdot \Delta p \geq \hbar/2$ follows directly from Fourier analysis.

### Wave Equations

For the wave equation $\partial_{tt} u = c^2 \nabla^2 u$:

Fourier transforming in space: $\partial_{tt} \hat{u} = -c^2 k^2 \hat{u}$

Each mode oscillates as $e^{\pm i\omega t}$ with $\omega = c|k|$ (the dispersion relation).

### Diffraction

The far-field diffraction pattern is the Fourier transform of the aperture function:

```math
E(\theta) \propto \int_{\text{aperture}} E_0(x) e^{-ik x \sin\theta} dx
```

A single slit gives a sinc pattern; a double slit gives interference fringes.

### Signal Processing

- **Filtering**: Multiply spectrum by transfer function
- **Spectral analysis**: Identify frequency components
- **Compression**: Keep only significant frequencies (MP3, JPEG)

### Solving PDEs

For linear PDEs with constant coefficients, Fourier transform converts derivatives to multiplication, solving the PDE algebraically:

```math
\text{Heat equation: } \partial_t u = D\nabla^2 u \quad \Rightarrow \quad \partial_t \hat{u} = -Dk^2 \hat{u}
```

Solution: $\hat{u}(k,t) = \hat{u}(k,0) e^{-Dk^2 t}$

## Related Transforms

### Laplace Transform

```math
F(s) = \int_0^{\infty} f(t) e^{-st} dt
```

The Fourier transform is the Laplace transform evaluated on the imaginary axis: $\hat{f}(\omega) = F(i\omega)$ (for causal functions).

### Sine and Cosine Transforms

For even/odd functions or boundary value problems:

```math
\hat{f}_c(k) = \int_0^{\infty} f(x) \cos(kx) dx, \qquad \hat{f}_s(k) = \int_0^{\infty} f(x) \sin(kx) dx
```

### Wavelet Transform

Provides time-frequency localization (unlike Fourier, which is global):

```math
W_f(a, b) = \frac{1}{\sqrt{a}} \int f(t) \psi^*\left(\frac{t-b}{a}\right) dt
```

Useful when frequency content changes over time.

## Summary

| Concept | Formula | Application |
|---------|---------|-------------|
| Fourier series | $f = \sum c_n e^{2\pi inx/L}$ | Periodic functions |
| Fourier transform | $\hat{f}(k) = \int f e^{-ikx} dx$ | Non-periodic functions |
| Derivative rule | $\mathcal{F}[f'] = ik\hat{f}$ | Solving DEs |
| Convolution | $\mathcal{F}[f*g] = \hat{f}\hat{g}$ | Linear systems |
| Parseval | $\int|f|^2 = \frac{1}{2\pi}\int|\hat{f}|^2$ | Energy conservation |
| Uncertainty | $\Delta x \cdot \Delta k \geq 1/2$ | Localization limits |
| FFT | $O(N\log N)$ computation | Practical spectral analysis |

**The essential insight:** Fourier analysis reveals that any function can be decomposed into pure oscillations. This connects space and frequency, time and energy, position and momentum. The same mathematics describes [quantum wave functions](../quantum-mechanics/quantum-mechanics.md), [electromagnetic waves](../electromagnetism/electromagnetic-waves.md), heat diffusion, musical tones, and image compression. When you see oscillations, periodicity, or waves, think Fourier.
