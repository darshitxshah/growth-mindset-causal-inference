# Causal Evaluation of Growth Mindset Interventions

## Overview
This project estimates the causal impact of a growth mindset intervention on student achievement using observational data and modern causal inference techniques. The analysis is conducted on a synthetic dataset modeled after the National Study of Learning Mindsets (NSLM), a large-scale educational experiment.

The goal is to evaluate whether students exposed to a growth mindset program demonstrate higher academic achievement, while rigorously addressing confounding, treatment imbalance, and identification assumptions.

---

## Research Question
What is the average causal effect of a growth mindset intervention on student achievement when treatment assignment is not randomized?

---

## Dataset
- **Size:** ~10,000 students
- **Structure:** Student-level and school-level covariates
- **Treatment:** Participation in a growth mindset intervention
- **Outcome:** Continuous achievement score
- **Data Type:** Synthetic observational data modeled after the NSLM study

Key covariates include:
- Student expectations (self-reported)
- Gender and first-generation status
- School-level mindset, test performance, racial composition, poverty, and size

A detailed variable description is provided in the included **Covariates Codebook**.

---

## Methodology
To estimate the Average Treatment Effect (ATE), multiple complementary causal inference methods were applied:

- **Inverse Probability Weighting (IPW):** Reweights observations using estimated propensity scores to simulate randomized assignment.
- **Propensity Score Matching (PSM):** Matches treated and control units using nearest-neighbor matching on propensity scores.
- **Generalized Linear Model (GLM):** Regression adjustment controlling for observed covariates.
- **Augmented Inverse Probability Weighting (AIPW):** A doubly robust estimator combining outcome regression and propensity weighting.

These methods were chosen to balance interpretability, robustness, and sensitivity to model misspecification.

---

## Identification Assumptions
The analysis relies on standard causal inference assumptions:

- **Ignorability:** All relevant confounders affecting treatment and outcome are observed.
- **Common Support:** Sufficient overlap in propensity scores between treatment groups (verified visually).
- **SUTVA:** No interference between students and a single version of the treatment.

Assumptions are explicitly checked and discussed throughout the analysis.

---

## Results
Across all estimation strategies, the growth mindset intervention demonstrates a **consistent positive effect** on student achievement:

- Estimated ATEs range from **~0.42 to ~0.46**
- AIPW produces the strongest and most robust estimate
- Confidence intervals overlap across methods, strengthening causal credibility

Post-weighting diagnostics confirm substantial improvement in covariate balance, particularly for key confounders such as prior expectations and demographic variables.

---

## Diagnostics and Validation
The analysis includes:
- Propensity score overlap visualizations
- Covariate balance tables before and after weighting
- Sensitivity to extreme weights under IPW
- Cross-method comparison of ATE estimates

These diagnostics ensure transparency and interpretability of causal claims.

---

## Project Structure
growth-mindset-causal-inference/
│
├── main_code.Rmd # Reproducible causal analysis
├── data/
│ ├── college_data.csv
│ └── Covariates_Codebook.pdf
├── poster/
│ └── Growth_Mindset_Causal_Evaluation_Poster.pdf
└── README.md

---

## Limitations
- The dataset is synthetic; real-world effects may differ.

- Results assume no unmeasured confounding.

- IPW estimates may be sensitive to extreme propensity weights.

- Causal interpretation depends on correct model specification.

---

## Academic Context

This project was completed as part of a graduate-level course in statistical modeling and causal inference. The analysis has been refactored and documented for professional and portfolio use.

---

## References

- **Yeager, D. S., et al. (2019). A national experiment reveals where a growth mindset improves achievement. Nature.**

- **Stuart, E. A. (2010). Matching methods for causal inference. Statistical Science.**

- **Imbens, G. W., & Rubin, D. B. (2015). Causal Inference in Statistics, Social, and Biomedical Sciences.**

---

## License

- This project is released under the **MIT License**.