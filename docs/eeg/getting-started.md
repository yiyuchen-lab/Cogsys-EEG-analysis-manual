# Getting Started with EEG Analysis

This page is a first practice guide for becoming familiar with EEG analysis. The goal is not to perform advanced analysis immediately, but to become comfortable with the standard workflow: loading raw EEG, checking channel names, setting montage, filtering, re-referencing, visually inspecting signals, identifying bad channels or bad segments, and comparing basic spectral properties.

## Learning path

As a starting point, begin with **MNE-Python**. After becoming comfortable with the main preprocessing concepts in Python, try to replicate the same workflow in **MATLAB using EEGLAB**. This allows you to compare how similar EEG preprocessing steps are handled in two widely used environments.

The recommended first practice dataset is the **PhysioNet EEG Motor Movement/Imagery Dataset**, also called **EEGBCI**. It includes simple eyes-open and eyes-closed baseline recordings, which are suitable for learning basic resting-state EEG preprocessing.

In MNE-Python, the dataset can be downloaded directly using `mne.datasets.eegbci.load_data()`.

| Run | Condition |
|---:|---|
| 1 | Eyes-open baseline |
| 2 | Eyes-closed baseline |

## First practice goal

Use one or two subjects from the EEGBCI dataset and produce a short notebook or report comparing eyes-open and eyes-closed resting-state EEG.

A minimal first deliverable should include:

1. A short description of the dataset and selected subject.
2. Raw EEG visualization.
3. Basic preprocessing steps.
4. Power spectral density plots.
5. A short interpretation of whether alpha-band power appears stronger during eyes-closed resting state.

!!! note "Main concept"
    Eyes-closed resting-state EEG often shows stronger alpha-band activity, especially over posterior channels. The purpose of this exercise is to learn how to inspect and quantify this kind of difference.

## Environment setup

Create a Python environment and install the required packages:

```bash
conda create -n eeg-practice python=3.11
conda activate eeg-practice

pip install mne matplotlib numpy scipy
```

Optional packages for notebook-based work:

```bash
pip install jupyter ipykernel
python -m ipykernel install --user --name eeg-practice --display-name "Python (eeg-practice)"
```

## Minimal MNE-Python example

```python
import mne
from mne.datasets import eegbci
from mne.io import read_raw_edf

subject = 1
runs = [1, 2]  # run 1 = eyes open, run 2 = eyes closed

files = eegbci.load_data(subject, runs)

labels = {
    1: "eyes_open",
    2: "eyes_closed",
}

raws = {}

for run, file in zip(runs, files):
    raw = read_raw_edf(file, preload=True)

    # Standardize channel names for this dataset
    eegbci.standardize(raw)

    # Set a standard 10-20 montage
    montage = mne.channels.make_standard_montage("standard_1005")
    raw.set_montage(montage)

    # Basic preprocessing
    raw.filter(l_freq=1.0, h_freq=40.0)
    raw.set_eeg_reference("average")

    raws[labels[run]] = raw

# Visual inspection
raws["eyes_open"].plot()
raws["eyes_closed"].plot()
```

## Visual inspection checklist

When inspecting the raw signals, check the following:

- Are the EEG channels named correctly?
- Does the montage appear correct?
- Are there unusually noisy channels?
- Are there flat channels?
- Are there large movement artifacts?
- Are there strong line-noise or muscle artifacts?
- Are the eyes-open and eyes-closed recordings visually different?

!!! tip "Good first habit"
    Do not immediately trust the data after loading. Always inspect the raw signal before running automated preprocessing.

## Power spectral density comparison

After basic preprocessing, compare the power spectral density between the two conditions.

```python
for condition, raw in raws.items():
    raw.compute_psd(fmin=1, fmax=40).plot(
        average=True,
        picks="eeg"
    )
```

You can also focus on alpha-band activity:

```python
alpha_band = (8, 13)

for condition, raw in raws.items():
    psd = raw.compute_psd(fmin=alpha_band[0], fmax=alpha_band[1], picks="eeg")
    alpha_power = psd.get_data().mean()

    print(f"{condition}: mean alpha power = {alpha_power:.4e}")
```

## Suggested report structure

For the first report, use the following structure:

```text
Title: First EEG preprocessing practice using EEGBCI eyes-open and eyes-closed data

1. Dataset
   - Dataset name
   - Subject ID
   - Runs used
   - Recording conditions

2. Preprocessing steps
   - Data loading
   - Channel-name standardization
   - Montage setting
   - Filtering
   - Average reference
   - Visual inspection

3. Results
   - Raw signal screenshots
   - PSD plots
   - Alpha-band comparison

4. Short interpretation
   - Does eyes-closed EEG show stronger alpha power?
   - Which channels or regions show the clearest difference?
   - What preprocessing problems did you notice?

5. Questions for next step
   - Which channels looked noisy?
   - Would you reject any segment manually?
   - How would this workflow be implemented in EEGLAB?
```

## Recommended tutorials

Start with the official MNE-Python tutorials:

- [MNE-Python official tutorials](https://mne.tools/stable/auto_tutorials/index.html)
- [MNE-Python preprocessing tutorials](https://mne.tools/stable/auto_tutorials/preprocessing/index.html)

## Recommended reading

For introductory concepts and theory, read selectively from the following resources:

- [Luck Lab's free online ERP data-processing book](https://lucklab.ucdavis.edu/books)
- Cohen, *Analyzing Neural Time Series Data: Theory and Practice*
- Gramfort et al. 2013, "MEG and EEG data analysis with MNE-Python"

Useful links:

- [Cohen book page](https://direct.mit.edu/books/monograph/4013/Analyzing-Neural-Time-Series-DataTheory-and)
- [MNE-Python reference paper](https://www.frontiersin.org/journals/neuroscience/articles/10.3389/fnins.2013.00267/full)

## Recommended video introductions

- [Neural signal processing and analysis: Zero to hero — Mike X Cohen](https://www.youtube.com/watch?v=Bmt89hHyxuM&list=PL6Q1zmN6V-zF3gWS1aXIX7fT5oMnmCyRV)
- [MNE-Python tutorial for EEG and MEG data analysis and visualization](https://www.youtube.com/watch?v=sttf-Rgfl1Q)

## First assignment

Analyze EEGBCI subject 1, runs 1 and 2.

Submit a short notebook or report containing:

- Raw signal plots for eyes-open and eyes-closed recordings.
- A short description of preprocessing steps.
- PSD plots for both conditions.
- A short comparison of alpha-band power.
- A brief reflection on what was easy or confusing.

The main purpose is to understand the workflow, not to produce a perfect analysis.
