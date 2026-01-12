# SERS-Data-Analysis
Code repository for the paper:

**“Generalizable Cysteine Quantification in Pea Cultivars from SERS Spectra Using AI”**

This repository contains:
- Data preparation scripts to assemble the SERS dataset
- Optional preprocessing pipeline (Savitzky–Golay smoothing, ModPoly baseline correction, Min–Max normalization)
- Regression baselines (LR, PLSR, SVR, RFR)
- Deep learning model (1D-CNN)
- Leave-One-Cultivar-Out (LOCO) generalization experiments
- SHAP-based interpretability and noise robustness study

---

## Repository structure
- `Data Preparation/`  
  Scripts to build the dataset used by all models.

- `Preprocessing_sers/`  
  Preprocessing module for SERS spectra (SG + ModPoly + Min–Max).

- Baseline models:
  - `Linear Regression/`
  - `Partial Least Square Regression/`
  - `Support Vector Machine Regression/`
  - `Random Forest Regression/`

- LOCO evaluation:
  - `Linear Regression - LOCO/`
  - `Partial Least Square Regression - LOCO/`
  - `Support Vector Machine Regression - LOCO/`
  - `Random Forest Regression - LOCO/`
  - `1D-CNN-LOCO/`

- Deep learning:
  - `1D-CNN/`
  - `1D-CNN-SHAP Analysis/`

- Robustness:
  - `Noise Study/`

PDF instructions:
- `DataPreparationInstruction.pdf`
- `PreprocessingInstruction.pdf`
- `1D-CNN-Instruction.pdf`

---

## Setup

### 1) Create an environment
**Option A: pip**
```bash
python -m venv .venv
# macOS/Linux
source .venv/bin/activate
# Windows
# .venv\Scripts\activate

pip install -r requirements.txt
