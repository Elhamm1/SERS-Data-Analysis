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

Create an environment:

Option A: pip
python -m venv .venv
macOS/Linux: 
source .venv/bin/activate
Windows:
.venv\Scripts\activate

pip install -r requirements.txt

Option B: conda
conda create -n sers python=3.10 -y
conda activate sers
pip install -r requirements.txt

Recommended run order (end-to-end)
Step 1 — Data preparation: 
Run the scripts in:
Data Preparation/
This should generate the dataset used by all models (e.g., processed spectra + labels).
Check DataPreparationInstruction.pdf for details.
Step 2 — Train/evaluate models WITHOUT preprocessing (raw spectra): 
Run each folder below using its main script:
Linear Regression/
Partial Least Square Regression/
Support Vector Machine Regression/
Random Forest Regression/
1D-CNN/
Each folder typically contains a script that loads the dataset, trains the model, and saves metrics/plots.
Step 3 — Preprocess spectra: 
Run preprocessing scripts in:
Preprocessing_sers/
This applies:
Savitzky–Golay smoothing
ModPoly baseline correction
Min–Max normalization
Then it saves a preprocessed dataset (or overwrites/exports a new processed file).
Step 4 — Train/evaluate models WITH preprocessing:
Repeat Step 2 using the preprocessed dataset as input.
Step 5 — LOCO generalization experiments:
Run the LOCO folders:
Linear Regression - LOCO/
Partial Least Square Regression - LOCO/
Support Vector Machine Regression - LOCO/
Random Forest Regression - LOCO/
1D-CNN-LOCO/
LOCO = Leave-One-Cultivar-Out: train on all cultivars except one, test on the held-out cultivar, repeat for each cultivar.
Step 6 — SHAP interpretability and Noise Study: 
1D-CNN-SHAP Analysis/
Computes SHAP explanations for the 1D-CNN predictions.
Noise Study/
Adds controlled noise / simulates fewer scan counts (as implemented in the code) and re-evaluates performance.


