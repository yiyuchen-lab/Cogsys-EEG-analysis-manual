# BrainAmp Setup

???+ info "What this page covers"
    This page summarizes the core hardware used in the CogSys BrainAmp recording setup, how the devices are connected, and how to run a basic connection test before data collection.

## 1. Hardware list

### Overview table

| Hardware | Reference image | Main role |
|---|---|---|
| PowerPack | Image 2 | Battery-based power supply for the BrainAmp system; helps reduce line-noise contamination compared with direct mains-powered recording. |
| BrainAmp Standard 32ch | Image 2 | Main EEG amplifier for acquiring, amplifying, and digitizing 32 channels of EEG signal. |
| USB2 Adapter (BUA) | Image 4 | USB interface between the BrainAmp hardware and the recording computer; also used to pass trigger information to BrainVision Recorder. |
| actiCAP ControlBox | Image 1 | Interface between the amplifier and the active cap system; used to connect the cap and enable actiCAP impedance measurement. |
| 32-channel actiCap + active electrodes | Image 3 | Active EEG cap and electrode set placed on the participant; each active electrode contains local circuitry to stabilize the signal and support impedance checking. |

### Detailed roles

=== "PowerPack"

    **Role**

    - Provides power to the BrainAmp system during recording.
    - Battery-powered operation helps reduce line-noise contamination from the mains supply.
    - Should be checked and charged before the recording session.

    **Practical note**

    - If the power status is uncertain, charge first and confirm that the system can remain stable for the full session.

=== "BrainAmp Standard 32ch"

    **Role**

    - Receives the EEG signals from the active cap chain.
    - Amplifies and digitizes up to 32 EEG channels.
    - Sends the acquired EEG data onward to the recording chain.

    **Practical note**

    - Confirm that the intended channel configuration matches the study workspace before recording.

=== "USB2 Adapter (BUA)"

    **Role**

    - Serves as the USB interface between the BrainAmp hardware and the recording computer.
    - Provides the data connection used by BrainVision Recorder.
    - Carries event / trigger information into the recording workflow.

    **Practical note**

    - For many experiments, the trigger signal comes from the stimulus presentation computer and is passed to the recording workflow via the BUA.
    - A separate **stimulus presentation computer** and **recording computer** is recommended when the experimental task is timing-sensitive or computationally heavy.
    - If the stimulus program is simple, the trigger cable and the BUA USB connection can be connected to the same computer.

=== "actiCAP ControlBox"

    **Role**

    - Connects the amplifier chain to the actiCap system.
    - Acts as the interface between the active electrodes and the BrainAmp hardware.
    - Enables actiCAP impedance measurement.

    **Practical note**

    - This unit is especially important during the preparation phase because it supports impedance checking before data acquisition begins.

=== "32-channel actiCap + active electrodes"

    **Role**

    - The cap and electrode set that sits on the participant.
    - The active electrodes contain local electronics / chips that buffer the EEG signal close to the scalp.
    - Supports more stable acquisition and the impedance-check workflow.

    **Practical note**

    - This is the participant-facing part of the system, so channel placement, electrode contact, and impedance quality matter directly for recording quality.

## 2. Hardware connection

???+ tip "Recommended setup principle"
    In general, keep the **EEG recording chain** and the **stimulus / trigger chain** conceptually separate. This makes troubleshooting easier and is usually safer for timing-critical experiments.

### Connection logic

```text
Participant
  ↓
actiCap + active electrodes
  ↓
actiCAP ControlBox
  ↓
BrainAmp Standard 32ch
  ↓
PowerPack (power supply for the amplifier chain)
  ↓
USB2 Adapter (BUA)
  ↓
Recording computer (BrainVision Recorder)

Stimulus presentation computer
  ↓
Trigger / event signal
  ↓
USB2 Adapter (BUA) / recording workflow
```

### Step-by-step connection order

1. **Prepare the participant-side hardware**  
   Place the actiCap and active electrodes on the participant and prepare the electrodes.

2. **Connect the cap to the actiCAP ControlBox**  
   Confirm that the cap-side connection is fully seated and not loose.

3. **Connect the ControlBox to the BrainAmp Standard 32ch**  
   This establishes the main signal path between the active cap system and the amplifier.

4. **Connect the BrainAmp chain to the PowerPack**  
   Confirm that the power supply is available and sufficiently charged.

5. **Connect the amplifier chain to the USB2 Adapter (BUA)**  
   This enables the data interface toward the recording computer.

6. **Connect the BUA to the recording computer by USB**  
   The recording computer should be the machine running BrainVision Recorder.

7. **Connect the trigger / event source**  
   If triggers are sent from a separate stimulus presentation computer, connect that trigger path into the recording workflow through the BUA.

8. **Power on and verify detection**  
   Start the devices in the lab's standard order and then open the recording software.

### Recommended computer arrangement

| Situation | Recommended arrangement |
|---|---|
| Timing-sensitive or complex experiment | Use a **separate stimulus computer** and **separate recording computer**. |
| Simple stimulus program | It is acceptable to let the same computer handle both the BUA USB connection and the trigger source. |

## 3. Hardware connection test

???+ question "When should this test be run?"
    Run a short connection test before every data collection session, and again whenever the hardware has been re-cabled or the software workspace has changed.

### Test checklist

- [ ] **Power check** — PowerPack is charged and the amplifier chain powers on correctly.
- [ ] **Software detection** — BrainVision Recorder detects the hardware and opens the expected workspace.
- [ ] **Channel-count check** — The expected 32 EEG channels are visible.
- [ ] **Impedance check** — The actiCAP impedance measurement works through the ControlBox.
- [ ] **Signal sanity check** — Live EEG appears reasonable, not flat, not saturated, and not obviously disconnected.
- [ ] **Movement / contact check** — Touching or adjusting one electrode produces the expected local change rather than random failure across many channels.
- [ ] **Trigger test** — Send one or more test triggers and confirm that they appear correctly in BrainVision Recorder.
- [ ] **Short test recording** — Record a brief file and reopen it if needed to verify that both EEG and triggers were stored correctly.

### Simple pass criteria

A basic connection test can be considered successful when:

- the hardware powers on normally;
- the software recognizes the intended recording setup;
- impedance checking is available;
- the live EEG stream looks plausible;
- the expected triggers are visible;
- and a short recording can be saved without errors.

## 4. Common connection problems

| Problem | Possible cause | First thing to check |
|---|---|---|
| Amplifier not detected | USB / interface path problem | Check the BUA USB connection and device power state. |
| Impedance check not available | ControlBox / cap connection issue | Check the ControlBox connection and cap interface. |
| Flat or missing channels | Electrode or cap-side connection problem | Check electrode contact, cap connection, and channel seating. |
| Triggers do not appear | Trigger path not connected correctly | Check the trigger cable, trigger source, and Recorder configuration. |
| Unstable / noisy data | Power, grounding, or poor electrode contact | Check PowerPack status, electrode preparation, and cable stability. |

## 5. Minimum pre-recording note

Before starting a real session, document at least the following:

- hardware configuration used;
- whether one or two computers were used;
- workspace / montage name;
- any unusual cable or power situation;
- and whether the connection test passed.
