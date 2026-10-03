[QSAR_README.md](https://github.com/user-attachments/files/29122393/QSAR_README.md)

# QSAR Property Prediction for Kinase Inhibitor Libraries

**Machine learning models for predicting ADMET-relevant physicochemical properties of small molecule kinase inhibitors**

[![Python](https://img.shields.io/badge/Python-3.8+-blue)]()
[![RDKit](https://img.shields.io/badge/RDKit-Cheminformatics-green)]()
[![scikit-learn](https://img.shields.io/badge/scikit--learn-ML-orange)]()

## Overview

This project develops QSAR (Quantitative Structure–Activity Relationship) models to predict key physicochemical and ADMET properties of kinase inhibitor drug candidates. The workflow demonstrates a complete cheminformatics pipeline from molecular representation through descriptor generation, model training, and interpretability analysis.

### Target Properties
- **pIC50** - Binding potency against kinase targets
- **logP** - Lipophilicity (critical for oral bioavailability)
- **logS** - Aqueous solubility (critical for formulation)

### Kinase Targets Covered
EGFR, JAK2, BCR-ABL, VEGFR, ALK, BRAF, MEK, CDK4/6

## Methods

### Molecular Representations
- **ECFP4 Fingerprints:** 2048-bit extended-connectivity fingerprints (Morgan, radius=2) capturing local chemical environments
- **Physicochemical Descriptors:** 12 RDKit-computed 2D descriptors (MW, LogP, TPSA, HBA, HBD, RotBonds, AromaticRings, FractionCSP3, etc.)

### Machine Learning Models
- **Random Forest Regressor** - 500 trees, robust baseline
- **Gradient Boosting Regressor** - 500 estimators, learning rate 0.05

### Evaluation
- 5-fold cross-validation on training set
- Held-out test set (80/20 split)
- Metrics: R², RMSE, MAE

## Repository Structure

```
QSAR-Kinase-Inhibitors/
├── QSAR_Kinase_Inhibitors.ipynb    # Main analysis notebook
├── kinase_inhibitors_dataset.csv   # Dataset (30 FDA-approved inhibitors)
├── figures/                        # Generated plots
│   ├── property_distributions.png
│   ├── correlation_matrix.png
│   ├── pIC50_predictions.png
│   ├── logP_predictions.png
│   ├── logS_predictions.png
│   └── *_feature_importance.png
└── README.md
```

## Quick Start

### Requirements
```
rdkit
scikit-learn
pandas
numpy
matplotlib
```

### Installation
```bash
conda create -n qsar python=3.10
conda activate qsar
conda install -c conda-forge rdkit scikit-learn pandas matplotlib
```

### Run
```bash
jupyter notebook QSAR_Kinase_Inhibitors.ipynb
```

## Key Results

The combined ECFP4 + physicochemical descriptor representation provides robust predictive performance across all three target properties. Gradient Boosting consistently achieves slightly higher accuracy than Random Forest, consistent with published QSAR benchmarks. Feature importance analysis reveals molecular weight, TPSA, and LogP as the most informative physicochemical descriptors, aligning with known ADMET structure–property relationships.

## Dataset

The dataset contains 30 FDA-approved kinase inhibitors with experimentally derived properties. Molecules span 8 kinase target classes, providing structural diversity representative of the current kinase inhibitor pharmacopeia.

## Future Directions

- Expand to larger datasets from ChEMBL bioactivity database
- Implement graph neural networks (GNN) for learned molecular representations
- Multi-task learning across correlated ADMET endpoints
- Virtual screening of novel compound libraries

## Author

**Mahdi Aarabi, Ph.D.**  
Computational Scientist

