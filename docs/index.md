<div class="cogsys-hero" markdown>

<div class="cogsys-kicker">CogSys Lab Documentation</div>

# EEG Analysis Manual

A structured onboarding and reference manual for learning EEG analysis, maintaining lab SOPs, and documenting reproducible preprocessing workflows.

</div>

???+ info "How to use this manual"
    Start from **Start Here** if you are new to EEG analysis. Use **Tutorials** for hands-on practice, **SOPs** for lab procedures, **Preprocessing** for analysis decisions, **Reference** for stable technical notes, and **Troubleshooting** when something goes wrong.

??? note "What this repository should store"
    Store documentation, scripts, environment files, checklists, and small figures here. Raw EEG datasets, video recordings, and large BIDS folders should be stored separately on lab storage, OSF, DVC remote storage, or Git LFS when appropriate.

<div class="grid cards" markdown>

-   :material-school-outline: **Start Here**

    ---

    A guided path for new students: learning sequence, software setup, and first EEG practice.

    [:octicons-arrow-right-24: Open Start Here](start-here/index.md)

-   :material-chart-line: **Tutorials**

    ---

    Hands-on walkthroughs for MNE-Python, EEGBCI, resting-state EEG, PSD, ERP, and later EEGLAB comparisons.

    [:octicons-arrow-right-24: View Tutorials](tutorials/index.md)

-   :material-clipboard-check-outline: **SOPs**

    ---

    Lab procedures for EEG acquisition, cap preparation, impedance checks, trigger tests, and data backup.

    [:octicons-arrow-right-24: View SOPs](sops/index.md)

-   :material-filter-cog-outline: **Preprocessing**

    ---

    Practical decisions for filtering, re-referencing, bad channels, ICA, epoching, and quality control.

    [:octicons-arrow-right-24: Open Preprocessing](preprocessing/index.md)

-   :material-book-open-page-variant-outline: **Reference**

    ---

    Stable notes for channel layouts, EEG file formats, frequency bands, and common parameter settings.

    [:octicons-arrow-right-24: Open Reference](reference/index.md)

-   :material-tools: **Troubleshooting**

    ---

    Quick fixes for noisy channels, montage errors, missing triggers, MNE import problems, and plotting issues.

    [:octicons-arrow-right-24: Fix Problems](troubleshooting/index.md)

</div>

## Recommended first path

```text
1. Start Here → Learning Path
2. Start Here → Software Setup
3. Start Here → First EEG Practice
4. Tutorials → EEGBCI Eyes Open vs Eyes Closed
5. Preprocessing → Overview
```
