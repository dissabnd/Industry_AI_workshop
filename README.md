# Industrial AI Capability Building Workshop

A hands-on 2-day workshop on machine learning and AI fundamentals for manufacturing organization. 

# Github Repo

<img src="assets/qr.png" alt="QR Code" width="200">

## Overview

This workshop teaches how AI (specifically supervised ML) can solve real manufacturing problems Engineers learn by doing — building models, interpreting results, and translating findings into maintenance decisions.

**Why it matters:** AI isn't just ML. It's understanding when and why to use it, avoiding pitfalls, and acting on insights.

---

# Day 1: Supervised Learning — "From Data to Predictions"
- **Day1_Reject_Rate_Notebook.ipynb** — Main hands-on activity (1 hr)
  - Predicts shift reject rate from operating conditions (speed, fill, downtime, product)
  - Teaches: EDA → feature engineering → train/test split → feature importance → SHAP interpretation
  - Outcome: Rejects are a *reliability* problem; downtime is the #1 driver

## Prerequisites

- Python 3.8+
- Jupyter Notebook or JupyterLab
- Libraries: pandas, scikit-learn, matplotlib, seaborn, xgboost, shap
- **Alternatively** Google colab

### Install
```bash
pip install pandas scikit-learn matplotlib seaborn xgboost shap
```

---

## Quick Start

1. **Clone or download this repo**
2. **Open `Day1_Reject_Rate_Notebook.ipynb` in Jupyter**
3. **Run all cells** (top to bottom; CONFIG cell at top is the only edit point for reuse)
4. **Observe:**
   - Section 2: Problem anchor (what does reject rate look like?)
   - Section 4: Target leakage discussion (critical teaching point)
   - Section 9–10: Feature importance & SHAP (why does the model decide?)


## Reusing This Notebook

Both notebooks are **template-driven**: edit the `CONFIG` cell to retarget on a different dataset or problem.

Example: To predict `Unplanned Downtime (min)` instead of reject rate:
```python
CONFIG = {
    "data_path": "your_data.csv",
    "target": "Unplanned Downtime (min)",
    "numeric_features": [...],  # your inputs
    "categorical_features": [...],
}
```

Everything below adapts automatically.


## FAQs

**Q: Why synthetic data?**  
A: Real production data is proprietary. Synthetic data is built to show genuine patterns (e.g., reject rate doubles on disrupted shifts), so the model and lessons transfer directly.

**Q: Should I use `has_fault` as a feature?**  
A: No. It's target leakage — you can't know a fault will happen until it happens. The real drivers are the conditions that precede faults (speed drift, fill variability).

**Q: Can I retrain on my own data?**  
A: Yes. Use the CONFIG cell. Ensure your target is known *after* the shift (for explanation) or *before* (for strict prediction) — the leakage discussion makes this clear.

**Q: What if my R² is much lower?**  
A: Check for: (1) target leakage going the wrong way (features that are consequences, not causes), (2) too much noise in your data, (3) missing key features. Start with EDA (Section 2 pattern).


