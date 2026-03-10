# Brownian Motion — Random Walks & Stock Price Simulation

## The Concept

**Brownian motion** (or a **Wiener process**) describes the random, continuous movement of particles suspended in a fluid — first observed by botanist Robert Brown in 1827. Mathematically, it's the foundation for modeling randomness in physics, biology, and finance.

A standard Brownian motion $W(t)$ satisfies:

1. $W(0) = 0$
2. $W(t) - W(s) \sim \mathcal{N}(0, t - s)$ for $0 \leq s < t$ (independent, normally distributed increments)
3. $W(t)$ has continuous paths

In discrete form, we approximate this by summing scaled random steps:

$$W(t) = \sum_{i=1}^{n} \frac{Z_i}{\sqrt{n}}$$

where $Z_i$ are i.i.d. random variables (either $\pm 1$ for a random walk, or $\mathcal{N}(0,1)$ for the normal approximation).

---

## Implementation

The notebook implements a `Brownian` class with three core methods:

### 1. Random Walk

The simplest discrete approximation — at each step, the particle moves up or down with equal probability:

```python
def randomwalk(self, n_step=100):
    w = np.ones(n_step) * self.x0
    for i in range(1, n_step):
        yi = np.random.choice([1, -1])
        w[i] = w[i-1] + (yi / np.sqrt(n_step))
    return w
```

Each step $\Delta W_i = \pm \frac{1}{\sqrt{n}}$ ensures the variance scales correctly — after $n$ steps, $\text{Var}(W) = n \cdot \frac{1}{n} = 1$.

### 2. Normal (Gaussian) Increments

A more accurate approximation using normally distributed steps:

```python
def gen_normal(self, n_step=100):
    w = np.ones(n_step) * self.x0
    for i in range(1, n_step):
        yi = np.random.normal(loc=0, scale=1)
        w[i] = w[i-1] + (yi / np.sqrt(n_step))
    return w
```

This directly models the Gaussian increment property of true Brownian motion.

### 3. Geometric Brownian Motion (Stock Prices)

The **Geometric Brownian Motion** (GBM) model is the standard model for stock prices, used in the Black-Scholes formula:

$$S(t) = S(0) \cdot \exp\left[\left(\mu - \frac{\sigma^2}{2}\right)t + \sigma W(t)\right]$$

where:

| Parameter | Meaning |
|---|---|
| $S(0)$ | Initial stock price |
| $\mu$ | Drift (expected return) |
| $\sigma$ | Volatility (standard deviation of returns) |
| $W(t)$ | Standard Wiener process |

```python
def stock_price(self, s0=100, mu=0.2, sigma=0.68, deltaT=52, dt=0.1):
    n_step = int(deltaT / dt)
    time_vector = np.linspace(0, deltaT, num=n_step)
    stock_var = (mu - (sigma**2 / 2)) * time_vector
    self.x0 = 0
    weiner_process = sigma * self.gen_normal(n_step)
    s = s0 * (np.exp(stock_var + weiner_process))
    return s
```

The $\mu - \frac{\sigma^2}{2}$ correction term accounts for the difference between arithmetic and geometric returns (Itô's lemma).

---

## Experiments in the Notebook

### Random Walk (x₀ = 0)

Four independent random walks of 1,000 steps each, starting from the origin. The paths diverge unpredictably — illustrating how randomness accumulates over time.

### Brownian Motion with Normal Increments (x₀ = 20)

Five Brownian motion paths starting from $x_0 = 20$, using Gaussian increments. The paths are smoother than the random walk version and better approximate continuous Brownian motion.

### Stock Price Simulation

Using GBM with $S(0) = 100$, $\mu = 0.2$, and varying volatility:

- **σ = 0.68** — High volatility produces wildly divergent price scenarios. Some paths spike above $1000, others crash below $10.
- **σ = 0.65** — Slightly lower volatility, but still produces dramatic spread.
- **σ = 0.60** — More contained, though uncertainty remains substantial.

**Key insight:** Small changes in volatility have an outsized effect on price uncertainty — the exponential in GBM amplifies $\sigma$.

### 2D Brownian Motion

Two independent 1D Brownian motions are combined to create a 2D random path — modeling particle diffusion in a plane. The resulting trajectory is a classic example of a fractal curve with Hausdorff dimension 2.

---

## Key Takeaways

- **Random walks** are the discrete backbone of Brownian motion — as step size shrinks, they converge to continuous Brownian paths (Donsker's theorem).
- **Volatility dominates** in GBM: the exponential structure means $\sigma$ has a far greater impact on long-term price distributions than drift $\mu$.
- **Brownian motion is scale-invariant**: zooming into any segment of a path reveals the same statistical structure — a hallmark of fractal geometry.
- **No predictive power**: each increment is independent, so past movements give zero information about future direction — consistent with the efficient market hypothesis.
