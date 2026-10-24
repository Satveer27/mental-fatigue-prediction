# Predicting Mental Fatigue Using Physiological Sensors

MSci dissertation project by Satveer Sahaas Ganasan (University of Glasgow).

This study investigates whether heart rate variability (HRV) and wrist skin temperature from wearable sensors can detect mental fatigue, using machine learning and deep learning on the [FatigueSet](https://www.esense.io/datasets/fatigueset) dataset (12 participants, 36 sessions).

**Paper (unpublished manuscript):** [`paper/Predicting_mental_fatigue_research_paper.pdf`](paper/Predicting_mental_fatigue_research_paper.pdf)

## Summary of the work

- 22 HRV features from raw RR intervals plus 6 skin temperature features, computed over 180 s sliding windows (60 s step).
- Leave-One-Subject-Out (LOSO) cross-validation throughout.
- Feature ablation, PCA / k-means analysis, classical ML (SVM, XGBoost, etc.), CNN / LSTM / CNN-LSTM on raw RR intervals, an MLP, and autoencoder-based feature compression.
- Best feature-based result: F1 = 0.778 (HRV + temperature). HRV alone: 0.376; temperature alone: 0.570. See the paper for caveats (small cohort, overlapping windows).

## Repository layout

| Path | Contents |
|:---|:---|
| `code/script.ipynb` | Main pipeline: feature extraction, labelling, statistics, models, ablations (outputs included) |
| `code/extra_graphs.ipynb` | Additional skin temperature figures |
| `paper/` | Manuscript PDF |

## Reproducing

The FatigueSet data is **not** included in this repository. Download it from the [original authors](https://www.esense.io/datasets/fatigueset) (see the dataset paper below), extract it to a folder named `fatigueset/` next to the notebooks' working directory (or edit the path near the top of each notebook), then:

```bash
pip install -r requirements.txt
jupyter notebook code/script.ipynb
```

## Data citation

Kalanadhabhatta, M., Min, C., Montanari, A. and Kawsar, F. *FatigueSet: A Multi-modal Dataset for Modeling Mental Fatigue and Fatigability.* 15th International Conference on Pervasive Computing Technologies for Healthcare (PervasiveHealth), 2021.
