# Preprocessing

???+ info "How to use this section"
    This section documents analysis decisions. Each preprocessing step should explain the purpose, typical parameters, quality-control checks, and what should be reported.

## Core steps

<div class="grid cards" markdown>

-   **Load and inspect raw data**

    ---

    Confirm channel names, sampling rate, events, annotations, and recording quality.

-   **Set montage**

    ---

    Map EEG channels to standard or study-specific electrode positions.

-   **Filter**

    ---

    Apply high-pass, low-pass, and line-noise filtering with documented parameters.

-   **Re-reference**

    ---

    Choose average reference, mastoid reference, or study-specific reference.

-   **Bad channels and segments**

    ---

    Mark unstable channels and contaminated segments before final analysis.

-   **ICA and artifact handling**

    ---

    Use ICA carefully and document component rejection criteria.

</div>

## Reporting checklist

??? checklist "Minimum information to report"
    - Software and version.
    - Filtering parameters.
    - Reference choice.
    - Bad-channel handling.
    - Artifact rejection or ICA criteria.
    - Epoch window and baseline window when applicable.
