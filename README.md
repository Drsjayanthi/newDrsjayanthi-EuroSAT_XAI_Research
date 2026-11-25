
# EuroSAT-XAI: Leakage-Controlled Classification and Quantitative Explainable AI

A reproducible deep-learning and explainable AI research workflow for EuroSAT-RGB remote-sensing image classification.

## Overview

This repository provides an eight-stage experimental pipeline covering dataset quality control, leakage prevention, CNN-based image classification, predictive evaluation, explainability, quantitative explanation evaluation, robustness testing, and research reporting.

The implementation emphasizes reproducibility, transparent evaluation, duplicate-aware data partitioning, and methodological validity.

## Research Workflow

| Stage | Description |
|---|---|
| Stage 1 | Dataset audit and quality control |
| Stage 2 | Leakage prevention, metadata assessment, and data splitting |
| Stage 3 | Deep-learning model development |
| Stage 4 | Predictive performance evaluation |
| Stage 5 | Explainable AI generation |
| Stage 6 | Quantitative explanation evaluation |
| Stage 7 | Robustness and statistical validation |
| Stage 8 | Reporting and reproducibility |

## Models

Two convolutional neural network architectures are implemented:

- ResNet-18
- EfficientNet-B0

ImageNet-pretrained weights are used, with input images resized to 224 × 224 pixels.

## Explainable AI Methods

- Grad-CAM
- Integrated Gradients

Explanation evaluation includes:

- Deletion and insertion experiments
- Most-attributed, least-attributed, and random ordering controls
- Faithfulness AUC
- Transformation stability
- Cascading parameter-randomisation sanity checks

## Evaluation and Statistical Analysis

Predictive evaluation includes:

- Accuracy
- Macro-F1 and weighted-F1
- Balanced accuracy
- Matthews correlation coefficient (MCC)
- Negative log-likelihood (NLL)
- Expected calibration error (ECE)
- Temperature scaling

Statistical and robustness analysis includes:

- Group-aware bootstrap confidence intervals
- Exact McNemar tests
- Holm multiple-testing correction
- Label-preserving perturbation experiments

## Dataset

This project uses the EuroSAT-RGB image collection.

- Number of images: 27,000
- Number of classes: 10
- Original image dimensions: 64 × 64 pixels
- Input representation: RGB

The dataset is not included in this repository.

Users must obtain the dataset from its original distribution source and follow the applicable dataset licence and citation requirements.

## Repository Structure

```text
EuroSAT_XAI_Research/
│
├── README.md
├── requirements.txt
├── .gitignore
│
├── EuroSAT_XAI_Lean_8_Stage_Research_Notebook.ipynb
│
└── outputs/
    ├── audit/
    ├── figures/
    ├── result/
    └── splits/
```

## Installation

Create a Python environment:

```bash
conda create -n eurosat_xai python=3.11 -y
conda activate eurosat_xai
```

Install PyTorch and Torchvision using the official PyTorch installation instructions appropriate for your hardware:

https://pytorch.org/get-started/locally/

Install the remaining dependencies:

```bash
pip install -r requirements.txt
```

Register the Jupyter kernel:

```bash
python -m ipykernel install --user --name eurosat_xai --display-name "Python (EuroSAT-XAI)"
```

Launch Jupyter:

```bash
jupyter notebook
```

Open the research notebook and configure the dataset path before execution.

## Reproducibility

The experimental workflow includes:

- Random-seed control
- Dataset integrity verification
- SHA-256 exact-duplicate detection
- Near-duplicate candidate review
- Group-aware data splitting
- Validation-based model selection
- Validation-only temperature calibration
- Locked test evaluation
- Experiment and software-version manifests

The test set is reserved for final evaluation.

## Methodological Limitations

The standard EuroSAT-RGB class-folder collection does not independently establish geographic independence.

Perceptual-hash similarity is treated as a candidate signal requiring review, rather than automatic proof of duplicate scenes.

Resizing 64 × 64 images to 224 × 224 does not increase the original spatial resolution.

Grad-CAM and Integrated Gradients are evaluated using complementary quantitative and sanity-check procedures. No single explanation metric is treated as sufficient evidence of explanation faithfulness.

## Outputs

The repository includes research artefacts such as:

- Dataset audit reports
- Duplicate and grouping reports
- Data split assignments
- Model predictions and evaluation metrics
- Confusion matrices and reliability diagrams
- XAI visualizations
- Robustness and faithfulness evaluation results
- Statistical comparison tables
- Reproducibility manifest
- Automated validity audit

## Responsible Reporting

Results should be reported according to the actual experimental evidence.

Geographic generalisation should not be claimed without appropriate geographic grouping and independent evaluation.

## Citation

If you use this implementation, please cite the associated research publication when it becomes available.

The original EuroSAT dataset must also be cited according to its source publication and licence.

## License

The repository licence and third-party dataset and software licences should be respected. See the LICENSE file for the repository's licensing terms.
