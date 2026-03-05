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

## 🛠️ Tech Stack

- **Python 3**
- **NumPy** — numerical computation & random sampling
- **Matplotlib** — data visualization

## 📦 Getting Started

```bash
# Clone the repository
git clone <repo-url>
cd Stat_maths

# Install dependencies
pip install numpy matplotlib

# Open the notebooks
jupyter notebook
```

## 📌 Roadmap

This is a living project. More topics will be added over time, including but not limited to:

- [ ] Central Limit Theorem
- [ ] Bayes' Theorem
- [ ] Monte Carlo Simulations
- [ ] Probability Distributions
- [ ] Hypothesis Testing
- [ ] Markov Chains
- [ ] Regression Analysis

---

## 🤝 Contributing

Ideas, suggestions, and contributions are welcome! Feel free to open an issue or submit a pull request.

## 📄 License

This project is open-source and available under the [MIT License](LICENSE).
