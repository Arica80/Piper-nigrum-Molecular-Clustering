# Molecular Descriptor Clustering of *Piper nigrum* Constituents

Reproducible unsupervised ML analysis of 49 molecular records using three molecular descriptors: `Gap_eV`, `BDE_MIN_kcal_moL`, and `Carga_no_C`.

## Results reproduced in Google Colab

| Metric | Result |
|---|---:|
| Records | 49 |
| Selected K (tested K=2–8) | 2 |
| Silhouette score | 0.492687 |
| Cluster sizes | 11 and 38 |
| PCA variance explained (PC1+PC2) | 84.47% |
| K-means runs (random states 0–29) | 30 |
| Distinct partitions | 1 |
| ARI vs. reference partition | 1.0 (min/mean/max) |

## How to reproduce

1. Open [`notebooks/Piper_nigrum_KMeans_Reproducible.ipynb`](notebooks/Piper_nigrum_KMeans_Reproducible.ipynb) in Google Colab.
2. Run the notebook and upload your original `ml.xlsx` when prompted.
3. The notebook reads the first 49 records of worksheet `Analise_Oleo_Pimenta`, checks input integrity, standardizes the three descriptors, evaluates K=2–8, visualizes a K=2 model via PCA, evaluates stability over 30 random seeds, and exports metrics, cluster membership and plots to `outputs/`.

**Input data:** `ml.xlsx` is not distributed in this public repository. It must be supplied by an authorized owner. Without the workbook, the notebook cannot independently regenerate results; metrics in `reports/` are prior execution records.

## Interpretation and limitations

- The observed two-cluster partition is stable **across the 30 tested K-means random seeds**, but stability to descriptor choice or resampling was not established.
- Silhouette ~0.493 suggests moderate geometric separation, not validated chemical or biological classes.
- PCA is used for **visualization only**; K-means uses all three standardized original features.
- Average cluster descriptor differences describe the features used to define the clusters and are **not** independent evidence for antioxidant activity or toxicity.
- Computational descriptors and compound identities depend on the original research data and require independent chemical verification for broader claims.
- A public version of the input dataset should be added only after verifying publication rights and any unpublished-research restrictions.

## Files

- `notebooks/Piper_nigrum_KMeans_Reproducible.ipynb`: complete executable workflow.
- `reports/reference_metrics.json`: metrics from the user's validated Colab run.
- `requirements.txt`: Python dependencies.
- `outputs/`: generated locally by the notebook; excluded from Git by default pending review.
