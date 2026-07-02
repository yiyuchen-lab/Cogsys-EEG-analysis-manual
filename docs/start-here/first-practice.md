# First EEG Practice

???+ abstract "Practice objective"
    Analyze the EEGBCI eyes-open and eyes-closed baseline recordings for one subject. The main goal is to become comfortable with loading, inspecting, preprocessing, and comparing basic spectral properties.

## Dataset

Use the **PhysioNet EEG Motor Movement/Imagery Dataset**, also called **EEGBCI**.

| Run | Condition |
|---:|---|
| 1 | Eyes-open baseline |
| 2 | Eyes-closed baseline |

## Minimal code

```python
import mne
from mne.datasets import eegbci
from mne.io import read_raw_edf

subject = 1
runs = [1, 2]
files = eegbci.load_data(subject, runs)

labels = {1: "eyes_open", 2: "eyes_closed"}
raws = {}

for run, file in zip(runs, files):
    raw = read_raw_edf(file, preload=True)
    eegbci.standardize(raw)
    raw.set_montage(mne.channels.make_standard_montage("standard_1005"))
    raw.filter(l_freq=1.0, h_freq=40.0)
    raw.set_eeg_reference("average")
    raws[labels[run]] = raw

raws["eyes_open"].plot()
raws["eyes_closed"].plot()
```

## Compare PSD

```python
for condition, raw in raws.items():
    raw.compute_psd(fmin=1, fmax=40).plot(average=True, picks="eeg")
```

## First report checklist

??? checklist "What to submit"
    - Raw signal screenshots for both conditions.
    - A list of preprocessing steps.
    - PSD plots for both conditions.
    - A short alpha-band comparison.
    - A reflection on what was confusing or unclear.

## Expected observation

Eyes-closed resting EEG often shows stronger alpha-band power, especially over posterior channels. The goal here is not to prove a strong result, but to practice the workflow.
