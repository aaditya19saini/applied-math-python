# 📊 Practical Mathematics & Statistics in Python

A hands-on collection of mathematical and statistical concepts brought to life through Python simulations and visualizations.

This project is an ongoing effort to explore, implement, and visualize core ideas from **mathematics** and **statistics** — making theory tangible through code.

---

## 🚀 Topics Covered

### 1. Law of Large Numbers (LLN)

> *As the number of trials increases, the sample average converges to the expected value.*

**Notebook:** [`LLN.ipynb`](LLN.ipynb)

We simulate **10,000 tosses** of a slightly biased coin (P(heads) = 0.51) across **10 independent experiments**. The plot below shows how each experiment's cumulative heads ratio converges toward the true probability as the number of tosses grows — a direct demonstration of the Law of Large Numbers.

![Law of Large Numbers](images/law_of_large_numbers_plot.png)

**Key observations:**
- Early tosses show high variance — the heads ratio fluctuates wildly.
- As the number of tosses increases, all 10 experiments converge toward the true probability of **51%**.
- The difference between 50% (fair coin) and 51% (biased coin) becomes distinguishable only with a large sample size.

---

### 2. Monte Carlo Integration

> *Approximate definite integrals using random sampling instead of deterministic grids.*

**Notebook:** [`monte_carlo_integrations.ipynb`](monte_carlo_integrations.ipynb) | **Explainer:** [`monte_carlo_integration.md`](monte_carlo_integration.md)

We compute the integral $\int_{0}^{4}\sqrt[4]{15x^3+21x^2+41x+3} \cdot e^{-0.5x}\,dx$ using random sampling, compare it against Riemann sums, and visualize how the estimate converges to the true value as the sample size grows.

![Monte Carlo Convergence](images/mc_convergence.png)

**Key observations:**
- Monte Carlo estimates converge to the true integral value as sample count increases.
- The distribution of estimates follows a normal distribution (Central Limit Theorem).
- The method scales to high-dimensional problems where grid-based methods fail.

---

## 🛠️ Tech Stack

- **Python 3**
- **NumPy** — numerical computation & random sampling
- **SciPy** — scientific computing & numerical integration
- **Matplotlib** — data visualization

## 📦 Getting Started

```bash
# Clone the repository
git clone <repo-url>
cd Stat_maths

# Install dependencies
pip install numpy matplotlib scipy

# Open the notebooks
jupyter notebook
```

## 📌 Roadmap

This is a living project. More topics will be added over time, including but not limited to:

- [ ] Central Limit Theorem
- [ ] Bayes' Theorem
- [x] Monte Carlo Integration
- [ ] Probability Distributions
- [ ] Hypothesis Testing
- [ ] Markov Chains
- [ ] Regression Analysis

---

## 🤝 Contributing

Ideas, suggestions, and contributions are welcome! Feel free to open an issue or submit a pull request.

## 📄 License

This project is open-source and available under the [MIT License](LICENSE).
