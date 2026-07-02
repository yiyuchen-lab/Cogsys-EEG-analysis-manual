# Learning Path

???+ question "What should I learn first?"
    Start with the conceptual workflow rather than advanced statistics. The first goal is to understand how raw EEG becomes a clean signal that can be interpreted or modeled.

## Recommended sequence

1. **EEG data structure**  
   Learn channels, sampling rate, events, annotations, and file formats.

2. **Raw data inspection**  
   Learn to recognize noisy channels, flat channels, eye movement artifacts, muscle artifacts, and line noise.

3. **Basic preprocessing**  
   Practice filtering, re-referencing, montage setting, bad-channel marking, and segment inspection.

4. **Spectral analysis**  
   Compare power spectral density and alpha-band power in eyes-open versus eyes-closed resting state.

5. **ERP analysis**  
   Later, move to event extraction, epoching, baseline correction, averaging, and component interpretation.

6. **EEGLAB replication**  
   After completing the Python workflow, reproduce the same steps in MATLAB using EEGLAB.

## What to postpone

??? note "Do not start here"
    Do not begin with source localization, deep learning, XAI, or complex time-frequency statistics. These methods are useful later, but they are difficult to interpret without a strong preprocessing foundation.

## First deliverable

Prepare a short notebook or report comparing eyes-open and eyes-closed EEG from one or two subjects.
