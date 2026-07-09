# Computational Intelligence Projects — EEG Seizure Detection

![Python](https://img.shields.io/badge/Python-3.8%2B-blue)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange)
![Machine Learning](https://img.shields.io/badge/Machine%20Learning-EEG%20Classification-yellow)
![Deep Learning](https://img.shields.io/badge/Deep%20Learning-1D%20CNN-green)

This repository contains a three-phase academic project on **epileptic seizure detection from EEG signals**. The work starts with classical machine-learning methods, continues with feature evaluation and selection, and ends with a deep-learning model for seizure detection on continuous EEG recordings.

The project was developed for a Computational Intelligence course and is intended for educational and research purposes.

> **Disclaimer:** This repository is not a medical device and should not be used for diagnosis, treatment, or clinical decision-making.

---

## Project Overview

Electroencephalography (EEG) records electrical activity in the brain and is widely used in epilepsy research. Across the three phases, this project investigates how EEG signals can be processed and classified as **seizure** or **non-seizure** using different computational-intelligence techniques.

At a high level, the project explores:

- EEG signal preprocessing and filtering
- handcrafted time-domain and frequency-domain feature extraction
- classical machine-learning classifiers
- feature ranking, redundancy reduction, and feature selection
- clustering-assisted classification
- CNN-based seizure detection using raw EEG windows
- hybrid modeling that combines learned CNN representations with selected handcrafted features
- evaluation using classification metrics and false-alarm analysis

---

## Phase README Overview

| Phase | Focus | Dataset | Main Methods | Key Outcome | Detailed README |
|---|---|---|---|---|---|
| **Phase 1** | Baseline seizure detection with classical machine learning | Bonn EEG dataset | Filtering, handcrafted features, SVM, Random Forest, KNN, cross-validation | Random Forest performed best among the tested feature-based classical models, especially in recall | [Phase 1 README](Phase1:Feature-Extraction-and-classification/README.md) |
| **Phase 2** | Feature evaluation, selection, and clustering-based improvement | Bonn EEG dataset | ID3-style feature scoring, Pearson correlation, F1-like feature-selection score, Random Forest, K-Means | A compact 10-feature subset achieved strong recall; K-Means with `K = 2` improved the main binary seizure-detection recall from `0.9231` to `0.9599` | [Phase 2 README](Phase2:feature-Selection-and-improving-classification-using-clustering/README.md) |
| **Phase 3** | Seizure detection with neural networks | CHB-MIT Scalp EEG Database | EDF loading, EEG windowing, handcrafted features, selected features, 1D CNN, hybrid CNN + feature model | The final hybrid model reached `88.27%` test accuracy and detected the true seizure interval in a full recording, but produced many false alarms | [Phase 3 README](Phase3:seizure-detection-using-CNN/readme.md) |

---

## Phase 1 — Feature Extraction and Classical Classification

Phase 1 builds the first end-to-end seizure-detection pipeline using the **Bonn EEG time-series dataset**. EEG segments are filtered, converted into numerical features, and classified using classical machine-learning algorithms.

The main goals of this phase are to:

1. prepare EEG signal data,
2. remove noisy signal components,
3. extract meaningful time-domain and frequency-domain features,
4. compare classical classifiers, and
5. evaluate the effect of normalization and feature engineering.

The tested models include:

- Support Vector Machine
- Random Forest
- k-Nearest Neighbors

The strongest overall result in this phase was achieved with engineered EEG features and a **Random Forest** classifier. Recall was treated as an especially important metric because missing seizure cases is more harmful than producing occasional false positives.

---

## Phase 2 — Feature Selection and Clustering-Based Classification

Phase 2 improves the classical machine-learning pipeline by selecting a smaller and more informative feature subset. Instead of using all extracted features, the phase evaluates both the individual predictive power of each feature and its redundancy with already selected features.

The feature-selection workflow includes:

1. extracting 26 handcrafted EEG features,
2. ranking individual features using decision-tree recall,
3. measuring redundancy with Pearson correlation,
4. combining recall and independence using an F1-like score,
5. selecting a compact subset of 10 features, and
6. testing whether K-Means clustering improves Random Forest classification.

The final selected feature subset was:

```text
Var, Skew, Kurtosis, Mean, Skew_f, PulseIndicator, Var_f, Max, CrestFactor, ShapeFactor
```

Using this subset, the notebook reported a **5-fold recall of 0.9511** with a Random Forest classifier. In the main binary seizure-detection experiment, K-Means segmentation improved the reported average recall from **0.9231** without clustering to **0.9599** with **K = 2**.

The phase also showed that clustering is task-dependent: it improved some classification settings but reduced performance in others.

---

## Phase 3 — Seizure Detection with a Hybrid CNN Model

Phase 3 extends the project from classical machine learning to deep learning. It uses the **CHB-MIT Scalp EEG Database**, which contains scalp EEG recordings in EDF format.

The final model combines two types of input:

```text
Raw EEG windows -> 1D CNN layers -> Dense layers
Selected handcrafted features -> Dense layer
Combined representation -> Softmax classifier -> Seizure / Non-seizure
```

The model uses 7-second EEG windows sampled at 256 Hz, with two EEG channels:

- `FZ-CZ`
- `CZ-PZ`

### Main Phase 3 Results

| Metric | Result |
|---|---:|
| Test accuracy | **88.27%** |
| Precision | **85.10%** |
| Recall | **86.11%** |
| F1-score | **85.60%** |
| Final validation accuracy | **89.91%** |

The final hybrid CNN + feature model significantly outperformed a simpler neural-network baseline in the saved notebook outputs. The simpler model reached about **58.66%** test accuracy, while the hybrid model reached **88.27%**.

The model was also tested on a full one-hour recording using a sliding window. It successfully covered the true seizure interval in `chb01_03.edf`, but it also produced many false-positive windows. This shows that continuous seizure detection requires more careful validation than window-level accuracy alone.

---

## Overall Conclusions

Across the three phases, the project shows a gradual progression from classical feature-based EEG classification to a hybrid deep-learning seizure-detection model.

The main conclusions are:

- Handcrafted EEG features can provide strong seizure-detection performance when paired with classical classifiers.
- Random Forest was a strong baseline for the feature-based experiments.
- Feature selection improved interpretability and reduced redundancy by identifying a compact subset of informative EEG features.
- Clustering can improve recall in some settings, but it is not universally beneficial.
- A hybrid CNN + handcrafted-feature model can learn useful patterns from both raw EEG windows and selected statistical features.
- Window-level performance alone is not enough for real-world seizure detection; false-alarm behavior on continuous EEG recordings is a critical limitation.

The final phase demonstrates that the hybrid approach is promising for academic experimentation, but the system is not suitable for clinical use without stronger validation, patient-specific testing, threshold tuning, and major false-alarm reduction.

---

## Repository Structure

```text
.
├── README.md
├── Phase1:Feature-Extraction-and-classification/
│   ├── README.md
│   ├── experiments.ipynb
│   ├── Phase1(in Farsi).docx
│   ├── x.pkl        # expected input data file, not included
│   └── y.pkl        # expected label file, not included
├── Phase2:feature-Selection-and-improving-classification-using-clustering/
│   ├── README.md
│   ├── experiments.ipynb
│   ├── x.pkl        # expected input data file, not included
│   ├── y.pkl        # expected label file, not included
│   └── assets/
│       └── readme/
└── Phase3:seizure-detection-using-CNN/
    ├── readme.md
    ├── CI_project3.ipynb
    ├── seizure_data/       # expected EDF files, not included
    ├── notSezure_data/     # expected EDF files, not included
    └── models/             # generated after training
```

> Some datasets and generated model files are not included in the repository. They must be downloaded or generated separately before running the notebooks.

---

## Datasets

This repository uses two public EEG datasets across the project phases:

### Bonn EEG Dataset

Used in Phase 1 and Phase 2. The dataset contains EEG time-series groups representing different brain states and recording conditions. In the main binary setup, seizure activity is separated from non-seizure activity.

Expected local files:

```text
x.pkl
y.pkl
```

### CHB-MIT Scalp EEG Database

Used in Phase 3. The dataset contains scalp EEG recordings in EDF format and annotated seizure intervals.

Expected local folders:

```text
seizure_data/
notSezure_data/
```

---

## How to Run

Each phase has its own notebook and README file. In general:

1. Clone the repository.
2. Open the README file for the phase you want to run.
3. Download and prepare the required dataset files.
4. Place the data in the expected folders.
5. Install the required Python packages.
6. Run the corresponding Jupyter Notebook.

Common dependencies include:

```bash
pip install numpy pandas scipy scikit-learn matplotlib seaborn jupyter
```

For Phase 3, additional deep-learning and EDF-reading dependencies are required:

```bash
pip install tensorflow pyEDFlib
```

---

## Future Improvements

Useful improvements for the full repository include:

- add a shared `requirements.txt` or `environment.yml`
- add reproducible dataset-preparation scripts
- refactor notebook code into reusable Python modules
- save experiment metrics in CSV or JSON files
- run experiments across multiple random seeds
- report confusion matrices, ROC-AUC, and precision-recall curves consistently
- compare CNN-only, feature-only, and CNN + feature models under the same protocol
- reduce false alarms in continuous EEG monitoring
- evaluate on unseen subjects and patient-specific splits
- add model explainability and feature-importance analysis

---

## Project Authors

- [Sajjad Shaffaf](https://github.com/sajad002)
- [Amir Hesari](https://github.com/Amir1848)

---

## Acknowledgments

This project was developed as part of a Computational Intelligence course. The EEG recordings used in the experiments come from public EEG datasets used for academic research.
