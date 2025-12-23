# Customer Segmentation Using Unsupervised Learning

## Project Overview
This repository contains an end-to-end machine learning capstone project that demonstrates the full ML lifecycle—problem framing, data preprocessing, modeling, evaluation, and ethical AI considerations—using an industry-relevant customer dataset. The objective is to identify meaningful customer segments through unsupervised learning techniques and to evaluate the results from both a technical and ethical perspective.

The project emphasizes not only model performance, but also interpretability, fairness, and real-world deployability.

---

## Business Problem
Customers are often treated as a homogeneous group, limiting the effectiveness of personalization, targeting, and lifecycle management strategies. This project addresses the need to segment customers based on similarity in behavior and characteristics, enabling more data-driven decision-making.

---

## Machine Learning Task
- **Task Type:** Unsupervised Learning (Clustering)
- **Techniques Used:** K-Means, Hierarchical Clustering, DBSCAN
- **Target Variable:** None

---

## Dataset
- **Source:** Kaggle – Customer Purchases Behaviour Dataset  
- **Link:** https://www.kaggle.com/datasets/sanyamgoyal401/customer-purchases-behaviour-dataset  
- **Granularity:** One row per customer  
- **Observational Unit:** Individual customer  

### Feature Groups
- **Demographic:** age, gender, education, region  
- **Economic:** income  
- **Behavioral:** purchase frequency, purchase amount, promotion usage  
- **Relationship / Attitudinal:** loyalty status, satisfaction score  
- **Product Preference:** product category  

---

## Methodology

### Data Preprocessing & Feature Engineering
- Missing value handling (median / mode imputation)
- Outlier treatment using robust statistics
- Encoding of categorical variables (ordinal and one-hot)
- Feature scaling using RobustScaler
- Dimensionality reduction using PCA for visualization and scalability

### Model Implementation
Multiple clustering algorithms were implemented and tuned:
- **K-Means:** cluster count optimized using Elbow Method and Silhouette Score
- **Hierarchical Clustering:** evaluated using linkage strategies with PCA-based mitigation for scalability
- **DBSCAN:** tuned using k-distance plots for eps selection

### Evaluation Metrics
As no ground truth labels exist, internal clustering metrics were used:
- Silhouette Score (primary)
- Davies–Bouldin Index
- Calinski–Harabasz Index

Final model selection balanced quantitative metrics with business interpretability and scalability.

---

## Model Selection
**Final Model:** K-Means (k = 2)

**Rationale:**
- Full population coverage (no noise exclusion)
- Stable and scalable for large datasets
- Interpretable clusters suitable for business use
- Behavioral separation aligns with real-world engagement patterns

---

## Ethical AI, Bias & Fairness Analysis
A dedicated bias and fairness audit was conducted despite the unsupervised nature of the task.

- **Explainability:** Surrogate model with SHAP-style feature contributions
- **Fairness Auditing:** Demographic parity and disparate impact–style analysis
- **Sensitive Attributes Audited:** income, age, gender, education, region

Results show no observable demographic or socioeconomic bias in cluster assignment. Behavioral differentiation—particularly purchase frequency—was identified as the primary driver of segmentation, which is appropriate and intended for this use case.

---

## Repository Structure

```text
customer-segmentation-ml-capstone/
│
├── README.md
├── requirements.txt
│
├── data/
│   ├── raw/
│   │   └── customer_data.xlsx
│   └── processed/
│       ├── X_preprocessed.npy
│       └── selected_feature_names.xlsx
├── notebooks/
│   ├── capstone python script.ipynb  # Modeling & evaluation
│   └── Technical Deck.ipynb  # Technical presentation
│
├── models/
│   ├── kmeans_k2.joblib
│   └── dbscan_eps0.3_ms10.joblib
│
├── artifacts_step4/  # Step 4 modeling outputs (metrics, configs, labels)
│   ├── metrics/
│       ├── dbscan_sweep_metrics.xlsx
│       ├── hierarchical_sweep_metrics.xlsx
│       ├── kmeans_sweep_metrics.xlsx
│       └── model_comparison_best.xlsx
│   
│
└── report/
    ├── Capstone Project Write-up.pdf
    └── Business Deck.pdf
```

## Reproducibility
To reproduce the results:

1. Clone the repository  
2. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```
3. Open and run the main notebook:

    capstone python script.ipynb (end-to-end ML pipeline)

    Technical Deck.ipynb (technical presentation)

All model configurations, trained models, metrics, and artifacts are saved in the repository to ensure reproducibility without requiring retraining.


## Author
CHRISTIAN PAUL FIRME

## Notes
This project was developed as an academic capstone and is structured to resemble a real-world, open-source machine learning project. The focus is on methodological rigor, interpretability, and ethical deployment rather than purely optimizing performance metrics.
