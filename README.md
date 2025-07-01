# Simultaneous cortico-spinal fMRI (CoSpine) Pain-dataset

**Version:** v1.1.0  
**Date:** 2025-06-19  
**BIDS-compliant**

---

## 1. Dataset overview

This is the first open-access, BIDS-compliant cortico-spinal task-based fMRI dataset. It enables exploration of cortical and spinal responses to thermal pain in healthy adults by providing simultaneous brain-and-spinal fMRI, physiological recordings, and behavioural ratings.

- **Task:** 4 s thermal pain stimuli followed by self-report ratings  
- **Modalities:** fMRI (task-pain BOLD), T1-weighted structural MRI, field maps (GRE magnitude/phase, reversed phase-encoding B0), physiological signals (pulse & respiration), events/behavioural logs
- **Subjects:** 39  

---

## 2. Experimental design

- **Pain stimulus:** contact thermode, temperatures 42–47 °C (subject-specific)  
- **Ratings:**  
  - PR – pain intensity (0–10 VAS)  
  - UpR – unpleasantness (0–10 VAS)

> Full stimulus & rating onset/duration are recorded in each `*_events.tsv`.

---

## 3. Data acquisition

- **Scanner:** 3 T Siemens Prisma (Erlangen, Germany)  
- **Coil:** Standard 64-channel head-neck coil

---

## 4. Dataset structure

```text
dataset/
├── dataset_description.json
├── README
├── task-pain_events.json
├── participants.tsv + .json
├── sub-01
│   ├── anat
│   │   ├── sub-01_T1w.json
│   │   └── sub-01_T1w.nii.gz
│   ├── fmap
│   │   ├── sub-01_acq-GRE_magnitude1.json
│   │   ├── sub-01_acq-GRE_magnitude1.nii.gz
│   │   ├── sub-01_acq-GRE_magnitude2.json
│   │   ├── sub-01_acq-GRE_magnitude2.nii.gz
│   │   ├── sub-01_acq-GRE_phase1.json
│   │   ├── sub-01_acq-GRE_phase1.nii.gz
│   │   ├── sub-01_dir-AP_epi.json
│   │   ├── sub-01_dir-AP_epi.nii.gz
│   │   ├── sub-01_dir-PA_epi.json
│   │   └── sub-01_dir-PA_epi.nii.gz
│   └── func
│       ├── sub-01_task-pain_bold.json
│       ├── sub-01_task-pain_bold.nii.gz
│       ├── sub-01_task-pain_dicom001_anonymized.IMA
│       ├── sub-01_task-pain_events.tsv
│       ├── sub-01_task-pain_recording-pulse_physio.json
│       ├── sub-01_task-pain_recording-pulse_physio.tsv.gz
│       ├── sub-01_task-pain_recording-respiratory_physio.json
│       └── sub-01_task-pain_recording-respiratory_physio.tsv.gz
├── derivatives/
│   └── preprocessed/
│       ├── dataset_description.json
│       └── sub-01/
```
---

## 5. Column & label definitions

**`*_events.tsv`**

| Column       | Description                          |
|--------------|--------------------------------------|
| `trial_type` | `pain` = heat stimulus, `rating` = VAS response period |
| `PR`         | Pain intensity (0–10)                |
| `UpR`        | Unpleasantness (0–10)                |

**`participants.tsv`**

| Column            | Units         |
|-------------------|---------------|
| `age`             | years         |
| `sex`             | m / f         |
| `education`       | years         |
| `heat_temperature` | °C           |

---

## 6. Quality control / preprocessing

- Structural images have been **defaced** to protect participant identity.  
- Optimized preprocessing pipeline applied using:
  - **FSL 6.0.7**
  - **Spinal Cord Toolbox 5.9**

> Includes distortion correction (TOPUP) and physiological noise correction.  
> Preprocessed data available in `derivatives/preprocessed/`.

---

## Contact

- **Zhaoxing Wei** – zhaoxing.wei@dartmouth.edu  
- **Yazhuo Kong** – kongyz@psych.ac.cn