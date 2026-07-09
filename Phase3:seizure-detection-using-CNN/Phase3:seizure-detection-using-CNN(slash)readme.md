# EEG Seizure Detection

This repository contains an academic Computational Intelligence project for detecting epileptic seizure activity from EEG signals. The project builds a full experimental pipeline: EEG recordings are prepared, split into time windows, processed, classified with a neural network, and evaluated using both standard classification metrics and false-alarm analysis.

> **Disclaimer:** This project is for educational and research purposes only. It is not a medical device and should not be used for diagnosis, treatment, or clinical decision-making.

## Project Summary

Epileptic seizures can appear as abnormal patterns in EEG signals. The goal of this project is to automatically classify EEG windows as either **seizure** or **non-seizure**.

The final model combines two sources of information:

- raw EEG signal windows processed by a 1D Convolutional Neural Network
- selected handcrafted signal features extracted from each window

This hybrid approach allows the model to learn patterns directly from the signal while also using compact statistical features that describe the EEG window.

## Dataset

The project uses the **CHB-MIT Scalp EEG Database**, a public EEG dataset available through PhysioNet:

[CHB-MIT Scalp EEG Database](https://physionet.org/content/chbmit/1.0.0/)

The dataset is not included in this repository. To run the notebook, download the required EDF files separately and place them in the expected directories.

The experiment uses EEG recordings from selected CHB-MIT subjects and focuses on two EEG channels:

- `FZ-CZ`
- `CZ-PZ`

## Repository Structure

The current repository contains:

```text
.
├── CI_project3.ipynb   # Main notebook with the full implementation and experiments
└── readme.md           # Project overview
```

When running the notebook, the data folders are expected to be available locally or in Google Drive:

```text
.
├── seizure_data/       # EDF files containing annotated seizure intervals
├── notSezure_data/     # EDF files without seizure intervals
└── models/             # Saved model output, generated after training
```

> Note: the notebook uses the folder name `notSezure_data`. Keep this spelling unless you also update the paths in the notebook.

## Methodology

At a high level, the notebook follows this workflow:

1. **Load EEG recordings** from EDF files.
2. **Filter the signals** to reduce noise and keep EEG-relevant frequencies.
3. **Create labeled windows** for seizure and non-seizure intervals.
4. **Extract handcrafted features** from each EEG window.
5. **Select informative features** using decision-tree recall and correlation-based redundancy reduction.
6. **Train a CNN-based classifier** using both raw windows and selected features.
7. **Evaluate performance** on held-out test data and on a full recording to study false alarms.

## Model Overview

The final model is a hybrid neural network:

```text
Raw EEG window
    -> 1D CNN layers
    -> Dense layers

Selected signal features
    -> Dense layer

Combined representation
    -> Softmax classifier
    -> Seizure / Non-seizure prediction
```

The model uses 7-second EEG windows sampled at 256 Hz. Each input window contains two channels and 1,792 samples per channel.

## Results

The following results are taken from the saved notebook outputs. Re-running the notebook may produce slightly different values depending on the environment, random seed behavior, and TensorFlow version.

### Window-Level Classification

| Metric | Result |
|---|---:|
| Test accuracy | **88.27%** |
| Precision | **85.10%** |
| Recall | **86.11%** |
| F1-score | **85.60%** |
| Final validation accuracy | **89.91%** |

The notebook also compares the final hybrid CNN + feature model with a simpler neural network experiment. The simpler model reached about **58.66%** test accuracy, while the final hybrid model reached **88.27%**, showing that combining learned CNN representations with selected handcrafted features improved performance in this experiment.

### Full-Recording Detection and False Alarms

The trained model was also evaluated on a full one-hour EEG recording using a sliding window.

| Item | Result |
|---|---:|
| Sliding windows evaluated | 3,593 |
| False-alarm windows | 904 |
| Candidate seizure periods before merging | 679 |
| Merged detected periods | 24 |

For the evaluated recording `chb01_03.edf`, the true seizure interval was approximately:

```text
2996s to 3036s
```

The model detected a merged seizure interval around:

```text
2992s to 3096s
```

This means the model successfully covered the true seizure region, but it also produced many false positives outside the seizure interval.

## Conclusions

The project shows that EEG seizure detection is feasible using a combination of CNN-based signal learning and handcrafted EEG features. The final model achieved reasonable window-level performance and was able to identify the true seizure region in a continuous recording.

However, the false-alarm analysis shows that the system is not ready for real-world medical use. In a practical seizure-response system, false alarms are especially important because unnecessary treatment actions could harm the patient. A production-quality system would need stronger validation, patient-specific testing, better thresholding, and much lower false-alarm rates.

The main takeaway is that the hybrid CNN + feature approach is promising for academic experimentation, but continuous seizure detection requires more robust evaluation than window-level accuracy alone.

## How to Run

1. Clone the repository.
2. Download the required CHB-MIT EDF files from PhysioNet.
3. Place the files in the expected dataset folders or update the notebook paths.
4. Install the required Python packages.
5. Open and run `CI_project3.ipynb` in Jupyter Notebook or Google Colab.

Common dependencies include:

```bash
pip install numpy scipy scikit-learn matplotlib tensorflow pyEDFlib jupyter
```

## Future Improvements

Useful next steps for improving this project include:

- reducing false alarms during continuous monitoring
- evaluating on completely unseen subjects
- adding patient-specific calibration
- tuning decision thresholds instead of relying only on `argmax`
- adding early stopping and model checkpointing
- moving preprocessing and training code from the notebook into reusable Python scripts
- saving experiment metrics in reproducible CSV or JSON files
- comparing CNN-only, feature-only, and CNN + feature models under the same protocol
- exploring temporal models such as LSTM, GRU, CNN-LSTM, or Transformer-based architectures

## Acknowledgments

This project was developed as part of a Computational Intelligence course assignment. The EEG recordings come from the CHB-MIT Scalp EEG Database hosted by PhysioNet.
