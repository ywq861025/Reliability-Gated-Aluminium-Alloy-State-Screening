# Reliability-Gated Aluminium Alloy State Screening

This repository contains the public data and reproducibility scripts for the
reliability-gated multi-property aluminium alloy screening study.

The central idea is to separate two questions:

1. What properties does the model predict for a material state?
2. Is the evidence around that state strong enough for engineering use?

The release therefore includes both fixed training views and non-training
evidence views. Do not treat the full archive as one supervised-learning matrix.

## Contents

```text
data/
  al_alloy_archive_role_annotated.csv
  train_core_fixed.csv
  tc_design_fixed.csv
  joint_uts_ys_tc_fixed.csv
  strict_external_benchmark.csv

scripts/
  audit_dataset.py
  train_fixed_views.py
  evaluate_external.py
  make_summary_figures.py

reports/
  training_audit_by_view_target.csv
  training_audit_report.json
  strict_external_metrics_with_bootstrap.csv
```

## Quick Start

```bash
python -m pip install -r requirements.txt
python scripts/audit_dataset.py
python scripts/train_fixed_views.py
python scripts/evaluate_external.py
python scripts/make_summary_figures.py
```

Outputs are written to `outputs/` and trained models to `models/`; both directories are generated locally and ignored by Git. These scripts are lightweight public-release checks for the fixed data views. They do not recreate every historical experiment and do not include text-editing utilities.

## Data Views

The main data views are fixed so that later data additions do not silently change
the training definition:

- `train_core_fixed.csv`: broad quality view for UTS, YS, HV, and auxiliary checks.
- `tc_design_fixed.csv`: TC-design view using direct or accepted TC labels while
  avoiding EC as an input feature.
- `joint_uts_ys_tc_fixed.csv`: joint UTS/YS/TC states for multi-objective screening.
- `strict_external_benchmark.csv`: independent benchmark excluded from training.

The full archive is included for transparency and evidence auditing.

## Reproducibility Notes

The scripts use deterministic splits with `random_state=42`. Reported values may
vary slightly across library versions, especially LightGBM versions. The
published paper uses the fixed views included here rather than dynamically
rebuilding views from the historical project workspace.

## Data Use

See `DATASET_NOTICE.md`. Original source documents are not redistributed in this
repository. Please cite original datasheets, handbooks, and papers when reusing
individual records.

