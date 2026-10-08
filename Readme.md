# Confidence Intervals: The Art of Being Honestly Uncertain #

## Margin of error, critical values, and a common misunderstanding ##

![Confidence Interval cover](confidence_interval_cover.png)

A story-style blog on confidence intervals: why a single point estimate is not enough, how an interval estimate is built, where the famous **1.96** comes from, and what "95% confidence" actually means. Every idea is backed by Python code and a simulation.

---

## What this blog covers

- Point estimate vs. interval estimate
- Confidence interval as **Estimate ± Margin of Error**
- Standard error and the role of the critical value
- Where **z = 1.96** comes from (90%, 95% and 99% confidence)
- Why higher confidence gives a wider interval
- How sample size (n) narrows the interval
- The correct interpretation of a 95% confidence interval
- Using the t-distribution when σ is unknown (introduced here, covered in detail later)
- Confidence interval vs. prediction interval
- Python: computing a CI with `scipy`, plotting it, and simulating 100 intervals

---

## Key formulas

$$ SE = \frac{\sigma}{\sqrt{n}} $$

$$ \text{Confidence Interval} = \text{Estimate} \pm (\text{Critical Value} \times SE) $$

$$ \bar{x} \pm z_{\alpha/2}\frac{\sigma}{\sqrt{n}} \qquad \text{(σ known)} $$

$$ \bar{x} \pm t_{\alpha/2,\,n-1}\frac{s}{\sqrt{n}} \qquad \text{(σ unknown)} $$

| Confidence level | Critical value (z) |
|---|---|
| 90% | 1.645 |
| 95% | 1.96 |
| 99% | 2.576 |

---

## Key takeaways

1. A confidence interval gives a **range** of plausible values for a population parameter, built from sample data.
2. Higher confidence means a larger z, a larger margin of error and a **wider** interval.
3. A larger sample size means a smaller SE and a **narrower** interval.
4. A 95% confidence level does **not** mean there is a 95% chance the true mean lies in one particular interval. It means that if we repeated the process many times, about **95% of the intervals** would contain the true mean.
5. In the simulation of 100 intervals (seed = 42), **97 captured** the true mean and 3 did not, which is consistent with 95% confidence.

---

## Folder structure

```
Confidence_Interval
├── Confidence_Interval.md            # The blog (Markdown, with LaTeX equations)
├── code_file.ipynb                   # Jupyter notebook with all the Python code
├── confidence_interval_cover.png     # Cover image for the blog
├── Readme.md                         # This file
├── other_images/
│   ├── normal_dist.jpg               # Standard normal curve with confidence regions
│   └── z-table.png                   # Z-table used to find critical values
└── python_images/
    ├── one_sample.png                # CI from a single sample
    └── 100_samples.png               # 100 simulated 95% confidence intervals
```

---

## Running the code

**Requirements**

- Python 3.8+
- `numpy`
- `scipy`
- `matplotlib`
- Jupyter Notebook or JupyterLab

**Install and run**

```bash
pip install numpy scipy matplotlib notebook
jupyter notebook code_file.ipynb
```

**What the notebook does**

| Section | Description |
|---|---|
| CI with `scipy` | Computes a 95% CI using `stats.norm.interval` (sample mean = 52, σ = 10, n = 100, giving 50.04 to 53.96) |
| Single-sample plot | Plots the interval, the sample mean and the true population mean |
| Simulation | Draws 100 samples (n = 30) from N(50, 10²), builds a 95% CI for each, and colours the intervals that capture the true mean green and the ones that miss it red |

---

## Series navigation

- **Previous:** Sampling Distribution
- **Next:** Hypothesis Testing Fundamentals

## Author

**Mansi Bramta**

Linkedin: https://www.linkedin.com/in/mansi-bramta-65358741b

Medium Account: https://medium.com/@mansibramta12

Kaggle: https://www.kaggle.com/code/mansibramta/confidence-intervals
