# Epileptic Seizure Detection from EEG Signals

![Python](https://img.shields.io/badge/Python-3.8%2B-blue)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange)
![scikit--learn](https://img.shields.io/badge/scikit--learn-Machine%20Learning-yellow)

This project explores how classical machine-learning methods can be used to detect epileptic seizure activity from EEG signals. It was developed as an academic project for a Computational Intelligence course and focuses on the full workflow from EEG signal preparation to model evaluation.

> **Note**: This project is for educational and research purposes only. It is not intended for clinical diagnosis or medical decision-making.

## Overview

Electroencephalography, or EEG, records electrical activity in the brain and is commonly used in epilepsy research. The goal of this project is to distinguish seizure-related EEG segments from non-seizure segments using a machine-learning pipeline.

At a high level, the project includes:

- Loading EEG signal data
- Filtering noisy signal components
- Extracting meaningful numerical features
- Training classical machine-learning models
- Evaluating model performance with cross-validation
- Comparing the effect of feature engineering and normalization

The main implementation is available in [`experiments.ipynb`](experiments.ipynb).

## Dataset

The project uses the public **Bonn EEG time-series dataset**, a commonly used dataset for seizure-detection experiments. The dataset contains EEG recordings divided into five groups representing different brain states and recording conditions.

In this project, the data is treated as a binary classification problem:

- **Seizure**
- **Non-seizure**

The notebook expects preprocessed data files named `x.pkl` and `y.pkl`. These files are not included in the repository and must be prepared from the original EEG dataset before running the notebook.

## Approach

The project follows a traditional machine-learning approach rather than a deep-learning approach. Instead of feeding raw EEG signals directly into a neural network, it first converts each EEG segment into a set of descriptive features.

The workflow is:

1. **Signal preparation**  
   EEG segments are loaded and filtered to keep the most relevant frequency range.

2. **Feature extraction**  
   Time-domain and frequency-domain characteristics are extracted from each signal.

3. **Model training**  
   Several classical classifiers are trained and compared.

4. **Evaluation**  
   Models are evaluated using 5-fold cross-validation and standard classification metrics.

5. **Normalization comparison**  
   Different scaling strategies are tested to understand their impact on model performance.

## Machine-Learning Models

The notebook compares three common classical machine-learning models:

- Support Vector Machine
- Random Forest
- k-Nearest Neighbors

The experiments show how model choice, feature engineering, and normalization can affect seizure-detection performance.

## Results Summary

The strongest overall results were achieved using engineered EEG features with a Random Forest classifier. This model provided the best recall among the tested feature-based models, which is especially important in seizure detection because missing seizure cases is more harmful than producing occasional false alarms.

Normalization had different effects depending on the model. Distance-based models such as KNN benefited more from scaling, while Random Forest was less sensitive to normalization.

## Repository Structure

```text
.
├── README.md
├── experiments.ipynb
├── Phase1(in Farsi).docx 
├── x.pkl        # expected input data file, not included
└── y.pkl        # expected label file, not included
```

## How to Run

1. Clone the repository.
2. Download and preprocess the Bonn EEG dataset.
3. Place `x.pkl` and `y.pkl` in the project root directory.
4. Install the required Python packages.
5. Open and run `experiments.ipynb` in Jupyter Notebook.

Required Python packages include:

- NumPy
- SciPy
- pandas
- scikit-learn
- matplotlib
- seaborn
- Jupyter Notebook

## Possible Improvements

Some useful next steps for improving this project would be:

- Add a reproducible dataset-preparation script
- Convert the notebook into reusable Python modules
- Add a `requirements.txt` file
- Use more EEG-specific features such as entropy, Hjorth parameters, wavelet features, and band-power features
- Add model explainability and feature-importance analysis
- Compare the classical machine-learning approach with deep-learning models such as 1D CNNs or LSTMs

## References

- Andrzejak, R. G., Lehnertz, K., Rieke, C., Mormann, F., David, P., & Elger, C. E. (2001). *Indications of nonlinear deterministic and finite-dimensional structures in time series of brain electrical activity: Dependence on recording region and brain state*. Physical Review E, 64(6), 061907.
- Official Bonn EEG dataset page: https://www.upf.edu/web/ntsa/downloads/-/asset_publisher/xvT6E4pczrBw/content/2001-indications-of-nonlinear-deterministic-and-finite-dimensional-structures-in-time-series-of-brain-electrical-activity-dependence-on-recording-regi
