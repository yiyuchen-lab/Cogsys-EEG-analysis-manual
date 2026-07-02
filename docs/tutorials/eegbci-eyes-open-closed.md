# EEGBCI Eyes Open vs Eyes Closed

???+ abstract "Tutorial goal"
    Use MNE-Python to compare eyes-open and eyes-closed resting-state EEG from the EEGBCI dataset. Focus on inspection, preprocessing, and PSD comparison.

## Load data

```python
import mne
from mne.datasets import eegbci
from mne.io import read_raw_edf

subject = 1
runs = [1, 2]
files = eegbci.load_data(subject, runs)
```

## Preprocess

```python
labels = {1: "eyes_open", 2: "eyes_closed"}
raws = {}

for run, file in zip(runs, files):
    raw = read_raw_edf(file, preload=True)
    eegbci.standardize(raw)
    raw.set_montage(mne.channels.make_standard_montage("standard_1005"))
    raw.filter(1.0, 40.0)
    raw.set_eeg_reference("average")
    raws[labels[run]] = raw
```

## Inspect

```python
raws["eyes_open"].plot()
raws["eyes_closed"].plot()
```

## PSD comparison

```python
for condition, raw in raws.items():
    raw.compute_psd(fmin=1, fmax=40).plot(average=True, picks="eeg")
```

## Interpretation questions

??? question "Questions to answer in the report"
    - Is alpha power visually stronger in eyes-closed EEG?
    - Which channels show the clearest difference?
    - Did any channels look noisy or flat?
    - Which preprocessing step was hardest to understand?
