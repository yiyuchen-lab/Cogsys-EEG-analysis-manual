# Software Setup

???+ info "Recommended beginner environment"
    Use a clean Python environment for EEG practice. This prevents package conflicts with existing research code or deep-learning environments.

## Create the environment

```bash
conda create -n eeg-practice python=3.11
conda activate eeg-practice
```

## Install basic packages

```bash
pip install mne matplotlib numpy scipy
```

## Optional notebook setup

```bash
pip install jupyter ipykernel
python -m ipykernel install --user --name eeg-practice --display-name "Python (eeg-practice)"
```

## Quick check

```python
import mne
print(mne.__version__)
```

## Folder suggestion

```text
eeg-practice/
├── notebooks/
├── figures/
├── reports/
└── notes/
```

!!! warning "Do not store raw data inside this documentation repository"
    Keep large raw EEG files outside the docs repo. Use a lab server, NAS, OSF, or another controlled storage location.
