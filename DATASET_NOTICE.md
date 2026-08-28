# Dataset Notice

This release contains curated numerical alloy-state records used for model training,
validation, and evidence auditing. The original datasheets, handbooks, journal
articles, patents, and standards remain the property of their respective
publishers or owners and are not redistributed here.

The CSV files preserve source identifiers such as `paper_id`, `source_title`,
`source_url`, `doi`, `figure_or_table`, and extraction metadata where available.
Users should cite the original source documents when reusing individual records.

Rows are role annotated. Not every row is intended for supervised training:

- `train_core_fixed.csv`: broad quality-gated training view.
- `tc_design_fixed.csv`: thermal-conductivity design view without EC leakage.
- `joint_uts_ys_tc_fixed.csv`: states with UTS, YS, and TC for joint screening.
- `strict_external_benchmark.csv`: independent validation states excluded from training.
- `al_alloy_archive_role_annotated.csv`: full role-annotated evidence archive.

The archive contains heterogeneous literature and datasheet records. Use the role
and quality fields before fitting models.
