# Marketing A/B Test Analysis

An end-to-end analysis of a digital advertising experiment comparing product ads with a public service announcement (PSA) control. The project uses Python to validate the dataset, compare conversion rates, quantify uncertainty, and examine descriptive segments.

## Project question

Did users in the ad group convert at a different rate from users in the PSA group? The primary metric is user-level conversion rate. The notebook reports a two-sided two-proportion z-test and a 95% Newcombe confidence interval for the absolute difference.

## Key findings

- **588,101 users** across the two groups; no missing cells or duplicate user IDs in the supplied dataset.
- **Ads:** 14,423 / 564,577 converted (**2.555%**). **PSA:** 420 / 23,524 converted (**1.785%**).
- The estimated absolute difference (Ads − PSA) is **0.769 percentage points** (about **43.1% relative lift** vs. PSA); z = **7.370**, two-sided p = **1.71 × 10⁻¹³**.
- The 95% Newcombe interval for the absolute difference is approximately **0.587 to 0.936 percentage points**.

These results describe the provided groups. A causal interpretation depends on the original assignment and measurement process. Statistical significance alone does not show that the campaign was profitable; cost and revenue data are not provided.

## Analysis and limitations

The notebook also compares conversion rates by weekday and observed ad-exposure bands. Exposure is measured after group assignment and is not randomized in this dataset, so these breakdowns are descriptive. They do **not** establish an optimal frequency cap or prove ad fatigue. The observed group allocation is about 96% Ads / 4% PSA; check it against the experiment plan before assessing allocation quality.

## Repository contents

```text
├── data/README.md
├── notebooks/marketing_ab_analysis.ipynb
├── outputs/figures/marketing_ab_analysis.png
├── requirements.txt
└── README.md
```

## Run the notebook

1. Download `marketing_AB.csv` from the [Kaggle dataset page](https://www.kaggle.com/datasets/faviovaz/marketing-ab-testing) and place it at `data/marketing_AB.csv`. Dataset download details are in [`data/README.md`](data/README.md).
2. Create and activate a virtual environment, then install dependencies:

   ```bash
   python -m venv .venv
   # macOS/Linux
   source .venv/bin/activate
   # Windows PowerShell: .venv\Scripts\Activate.ps1
   pip install -r requirements.txt
   jupyter notebook
   ```

3. Open [`notebooks/marketing_ab_analysis.ipynb`](notebooks/marketing_ab_analysis.ipynb) and run all cells. The notebook locates the project root whether Jupyter starts from the repository root or the `notebooks` folder.

## Visualization

![Conversion and exploratory segment analysis](outputs/figures/marketing_ab_analysis.png)
