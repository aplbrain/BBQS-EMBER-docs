# Data Standardization for EMBER-DANDI and EMBER-Vault

This guide walks you through a suggested procedure on how to prepare your dataset for upload using the BIDS standard, with support for common data types such as intracranial recordings, audio/video, and behavioral data, and optional use of NWB files.

This covers:

1. [The relevant standards](#1-relevant-data-standards)
2. [The standardization process and examples](#2-standardization-workflow)
3. [BIDS Standard](#3-bids-standard)
4. [Audio/Video](#bep047-motion-audio-video)
5. [Validation](#5-validation-required-before-upload)
6. [Common Pitfalls](#6-common-pitfalls)
7. [Recommended Workflow](#7-recommended-workflow-step-by-step)

## 1. Relevant Data Standards
Before formatting your dataset, familiarize yourself with the standards supported by the BBQS Program and the EMBER archive (defined by the BBQS DCAIC Data Standards Working Group):

[https://docs.google.com/document/d/1vIJ01La9G76FfGywS3IbG4o1GR4qquS31MoJ2B4_4os/edit?usp=sharing]()

A quick summary relevant to sensitive, multimodal human datasets (such as audio/video of participants) is outlined below.

### Core BIDS

- BIDS specification: [https://bids.neuroimaging.io/](https://bids.neuroimaging.io/)
- Defines folder structure, file naming, file types and metadata conventions for different data types

### BIDS Extensions Supported

#### Intracranial / Microelectrode Data

[https://bids-specification.readthedocs.io/en/stable/modality-specific-files/intracranial-electroencephalography.html](https://bids-specification.readthedocs.io/en/stable/modality-specific-files/intracranial-electroencephalography.html)

#### MEG Data

[https://bids-specification.readthedocs.io/en/stable/modality-specific-files/magnetoencephalography.html#meg-recording-data](https://bids-specification.readthedocs.io/en/stable/modality-specific-files/magnetoencephalography.html#meg-recording-data)

#### BEP032 (iEEG / microelectrode extensions)

[https://bids.neuroimaging.io/extensions/beps/bep_032.html](https://bids.neuroimaging.io/extensions/beps/bep_032.html)

Use for:

- Depth electrodes
- Microelectrode arrays
- Spike/LFP recordings

#### Audio / Video / Behavioral

##### BEP047 (motion, audio, video)

[https://bids.neuroimaging.io/extensions/beps/bep_047.html](https://bids.neuroimaging.io/extensions/beps/bep_047.html)

Use for:

- Video recordings (e.g., behavior, eye tracking)
- Audio recordings (speech, environment)
- Motion capture

### NWB (Neurodata Without Borders)

[https://www.nwb.org/](https://www.nwb.org/)

Recommended for:

- Spike times
- LFP
- Rich electrophysiology metadata
- General time series

!!! info "Important"
    If using NWB files, we recommend the files should still be organized within a BIDS structure.



NWB extensions can be found at [https://nwb-extensions.github.io](https://nwb-extensions.github.io)

For multi-subject data (multiple subjects interacting, recorded at the same time), refer to [`ndx-multisubjects`](https://pypi.org/project/ndx-multisubjects/)

!!! warning "`ndx-multisubjects`"
    This extension is undergoing development, and currently will not pass the validator. You can still use and upload this file to EMBER-DANDI using `--validation skip` argument until the validators are updated or this extension is incorporated into core NWB.
---
## 2. Standardization Workflow

Preparing your dataset involves three main steps:

### Step 1: Organize Files into BIDS Structure

- Create folders and filenames according to BIDS rules
- Convert to allowable filetypes if needed

### Step 2: Add Metadata

- JSON sidecars
- TSV files (events, channels, electrodes, etc.)
- Advise to use LinkML to create/describe their metadata. For advanced: point to complete systems like from Juelich
- Advise to use established lab notebook systems to formalize

### Step 3: Validate Locally

- Use the dandi-cli (which used the NWB inspector, BIDS Validator ([https://bids.neuroimaging.io/tools/validator.html]()) etc) before uploading.
- Please see the instructions here: [https://github.com/dandi/dandi-cli]()

---
## 3. BIDS Standard 

### 1. Folder Structure (Core BIDS Template)

BIDS specifies a particular set of folders and file names to organize data:

[https://bids.neuroimaging.io/getting_started/folders_and_files/index.html]()

More examples will be made available at:

[https://github.com/brain-bbqs]()

Here is a minimal multimodal dataset layout as an example, including iEEG in NWB formats and audio and video files:

```text
my_dataset/
├── dataset_description.json
├── participants.tsv
├── participants.json
├── sub-01/
│   ├── ses-01/
│   │   ├── ieeg/
│   │   │   ├── sub-01_ses-01_task-rest_ieeg.nwb
│   │   │   ├── sub-01_ses-01_task-rest_ieeg.json
│   │   │   ├── sub-01_ses-01_task-rest_channels.tsv
│   │   │   ├── sub-01_ses-01_task-rest_electrodes.tsv
│   │   │   └── sub-01_ses-01_task-rest_events.tsv
│   │   │
│   │   ├── beh/
│   │   │   ├── sub-01_ses-01_task-rest_beh.tsv
│   │   │   └── sub-01_ses-01_task-rest_beh.json
│   │   │
│   │   ├── video/
│   │   │   ├── sub-01_ses-01_task-rest_video.mp4
│   │   │   └── sub-01_ses-01_task-rest_video.json
│   │   │
│   │   └── audio/
│   │       ├── sub-01_ses-01_task-rest_audio.wav
│   │       └── sub-01_ses-01_task-rest_audio.json
```

---

### 2. BIDS File Naming Rules

As you go, please be sure to refer to the BIDS examples: https://github.com/bids-standard/bids-examples 

BIDS uses structured filenames:

```text
sub-<participant>[_ses-<session>]_task-<task>[_modality]
```

Examples:

- `sub-01_ses-01_task-rest_ieeg.nwb`
- `sub-01_ses-01_task-speaking_audio.wav`
- `sub-01_ses-01_task-walk_video.mp4`

---

### 3. Required Metadata Files for BIDS


#### 3.1 dataset_description.json

```json
{
  "Name": "Example Multimodal Dataset",
  "BIDSVersion": "1.9.0",
  "DatasetType": "raw",
  "Authors": ["Jane Doe", "John Smith"]
}
```

#### 3.2 participants.tsv

```tsv
participant_id	age	sex
sub-01	29	M
sub-02	34	F
```

#### 3.3 iEEG Metadata (BEP032)

##### channels.tsv

```tsv
name	type	units	sampling_frequency
chan01	microelectrode	uV	30000
```

##### electrodes.tsv

```tsv
name	x	y	z
elec01	12.3	-45.2	30.1
```

#### 3.4 events.tsv

```tsv
onset	duration	trial_type
0.0	1.0	stimulus
2.0	1.5	response
```

#### 3.5 Sidecar JSON Example

For an iEEG file:

```json
{
  "SamplingFrequency": 30000,
  "PowerLineFrequency": 60,
  "iEEGReference": "common average",
  "TaskName": "rest"
}
```

---

### 4. Using NWB within BIDS

If using NWB files within your project, they can be used to represent key time series data within BIDS, such as iEEG.

#### Recommended approach

- Store electrophysiology data as `.nwb` files
- Keep behavioral, events, and metadata in BIDS sidecars
- Organize the dataset with NWB files within the BIDS structure, getting the best of both worlds

Example:

```text
sub-01_ses-01_task-rest_ieeg.nwb
sub-01_ses-01_task-rest_events.tsv
sub-01_ses-01_task-rest_ieeg.json
```

When combining these standards, our key recommendations are:

- NWB = data container
- BIDS = dataset organization + metadata standard

---

## 4. Audio / Video (BEP047)

Supported formats:

- Video: `mp4`, `avi`
- Audio: `wav`

Example sidecar:

```json
{
  "SamplingFrequency": 48000,
  "Microphone": "Shure SM7B"
}
```

For video:

```json
{
  "FrameRate": 30,
  "Resolution": "1920x1080"
}
```

---

## 5. Validation (Required Before Upload)

Data uploaded to either EMBERVault or EMBER-DANDI must be properly standardized.
***Can this section be updated to jsut use the dandi validator?***
### Command Line Validation for BIDS (Recommended)

You can find detailed instructions on use of the BIDS validator here:

[https://bids.neuroimaging.io/tools/validator.html]()

We do not recommend using the online data validator for datasets containing PHI/PII.

[https://bids-validator.readthedocs.io/en/latest/user_guide/command-line.html]()

#### Install

(Use the Mac Terminal, Linux Command Line, or Windows Subsystem for Linux)

Using Deno:

[https://docs.deno.com/runtime/getting_started/installation/]()

```bash
deno install -ERWN -g -n bids-validator jsr:@bids/validator
```

### Run

```bash
deno run -ERWN jsr:@bids/validator <dataset>
```

When using an extension, you must use the flag `--schema` with the link to the pull request specific to the extension.

#### BEP032

```bash
--schema https://bids-specification--2307.org.readthedocs.build/en/2307/schema.json
```

#### BEP047

```bash
--schema https://bids-specification--2231.org.readthedocs.build/en/2231/schema.json
```


### Expected Output

- No errors → ready to upload
- Warnings → usually acceptable but should be reviewed
- Errors → must fix before upload to EMBER-Vault

!!! warning
    If you are using NWB files at all, you will need to validate those separately using the [DANDI CLI](../user-guide/uploading-data.md#upload-data-to-your-dandiset)

---

## 6. Common Pitfalls

### Incorrect filenames

- Missing `task-` or `sub-` labels

### Missing JSON sidecars

- Especially for iEEG and video/audio

### Inconsistent sampling rates

- Must match metadata

### Time misalignment

- Ensure events align across modalities

If your team is struggling, the EMBER archive team can help. Reach out at `info@emberarchive.org`.

---

## 7. Recommended Workflow (Step-by-Step)

1. Prepare raw data
    - Export from acquisition systems
    - Convert relevant modalities to NWB if appropriate, convert other data types to appropriate BIDS formats

2. Create folder structure

    ```bash
    mkdir -p my_dataset/sub-01/ses-01/ieeg
    ```

3. Rename files to BIDS format

4. Create metadata files
    - `dataset_description.json`
    - `participants.tsv`
    - sidecars

5. Add events + behavioral data

6. Validate BIDS dataset

7. Fix errors

8. Upload to platform