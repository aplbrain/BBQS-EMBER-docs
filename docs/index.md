# Welcome to the EMBER Archive Documentation

![ember_logo](assets/ember-logo.png){ style="width: 20%; display:block; margin-left: auto; margin-right: auto;" }

# Getting Started

## What is EMBER?

EMBER is the Ecosystem for Multimodal Brain-behavior Experimentation and Research.

The EMBER Archive enables storage, sharing, and analysis of multimodal neurophysiological and behavioral data, primarily supporting the [Brain Behavior Quantification and Synchronization (BBQS) Program](https://braininitiative.nih.gov/research/systems-neuroscience/brain-behavior-quantification-and-synchronization-program).

As you deposit data, the most important thing is to determine if your data contains sensitive human data that should *not* be shared with the public. If you have sensitive data you should upload such data to EMBER-Vault (coming soon!). Other data may go to EMBER-DANDI, where standard embargo options are available. It is your job as PI to consult with your IRB and other relevant entities to ensure that data can be shared.

Regardless of what resource you choose, the main goal is to deposit data such that a secondary user can reuse data for analyses. To accomplish this, you will need to convert your data with existing standards (NWB/BIDS). This document will also help you think through how to use these standards to best fit your data. 

If you are part of a BBQS team, you can contact us at [help@emberarchive.org](mailto:help@emberarchive.org) for additional help/resources.

---- 

## Storage Platforms

If your data are:


- animal data or de-identified human data, use **EMBER-DANDI**, which supports multimodal data from both animals and humans. Human data must not contain any PHI/PII and must be completely deidentified. 
- sensitive human data, use  **EMBER-Vault**, which supports HIPAA aligned, restricted human data storage


<br>
<figure style="text-align: center;" markdown>
<div style="display: flex; flex-direction: column; gap: 16px; align-items: center;" markdown>

<div style="width: 100%;" markdown="span">
![EMBER-DANDI and EMBER-Vault](assets/emberdandi_vault.png){ style="width: 100%;" }
<p style="font-size: 0.9em; margin-top: 4px;">
  <strong></strong> How EMBER is architected to support neuroscience
</p>
</div>

<!-- <div style="width: 100%;" markdown="span">
![Details of EMBER-DANDI and EMBER-Vault](assets/emberdandi_vault_detail.png){ style="width: 100%;" }
<p style="font-size: 0.9em; margin-top: 4px;">
  <strong>(B)</strong> EMBER-DANDI and EMBER-Vault
</p>
</div> -->

</div>

<figcaption style="margin-top: 8px;">
  EMBER-DANDI is the open data archive that can store animal and de-identified human data.
  EMBER-Vault is a HIPAA-compliant storage for identifiable human data, such as raw video and audio.
</figcaption>
</figure>



### How do I use EMBER-DANDI?

1. Create an account for EMBER-DANDI as described in the [User Guide](user-guide/EMBER-DANDI-account.md).
2. [Standardize your data](user-guide/standardizing-EMBERDANDI.md) using community standards [Brain Imaging Data Structure (BIDS)](https://bids-specification.readthedocs.io/en/stable/) and/or [Neurodata without Borders (NWB)](https://nwb-schema.readthedocs.io/en/latest/format.html#type-specifications).
3. Finally, upload your standardized data to [EMBER-DANDI](user-guide/uploading-data.md).
4. You can embargo your dataset for a desired period of time, which means it is viewable only to you and selected individuals.
5. You can publish your dataset, making it publicly available and creating a DOI.

### How do I use EMBER-Vault?

COMING SOON

Read more about it at our [EMBER-Vault](user-guide/embervault-account.md) page, and contact us for more details at [help@emberarchive.org](mailto:help@emberarchive.org).

<!-- # User Guide

1. The first step is to [standardize your data](../user-guide/standardizing-EMBERDANDI.md), which will be similar regardless of whether you are using EMBER-DANDI or EMBER-Vault.

2. After standardizing the data, you must validate the converted data using the [DANDI CLI](../user-guide/data-standardization.md#5-validation-required-before-upload).

3. Create account(s) for the appropriate storage platform(s).

3. Finally, upload your validated and standardized data to the appropriate storage platform [EMBER-DANDI](../user-guide/uploading-data.md) or [EMBER-Vault](../user-guide/embervault-uploading-data.md). -->



### Standardizing Data
Data standardization into BIDS and/or NWB is required for uploading to either of the EMBER storage platforms to enable easy and accessible reuse of data by secondary users who were not involved in the original study that created the data. We show one example of reproducing published figures using the NWB version of a BBQS dataset at [Example Standardization and Reproducibility](example-standardization-and-reproducibility/Suthana_Zenodo.md).

BIDS broadly describes how to rename files and folders and organize them into a standardized directory. It also requires associated metadata files to help explain the experiment and data.

NWB is a specific file type that can store one or more modalities within it. Relevant metadata is also stored directly inside the NWB file.

The recommended approach for standardiziation is as follows:

- If there is a data standardization scheme that you or your field is most comfortable using, then prioritize that
- Otherwise, we recommend that you try to get your data packaged into NWB as much as possible, and then utilize BIDS as the folder/file organization/naming scheme to capture the rest of the information
- If you already have multimodal data that are packaged into a single-ish file, collected at the same time point, etc., then use NWB
- If your data are already organized in a file structure corresponding to session, subject, modality, etc., then use BIDS
- If a bit a both, consider a hybrid option




<!-- Here is a minimal multimodal dataset layout as an example, including iEEG in NWB formats and audio and video files:

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
``` -->



### I'm new to these standards - how can I get help? 

More specific instructions for how to standardize data can be found in the [User Guide](user-guide/standardizing-EMBERDANDI.md). 

<!-- You are welcome to consult external sources (websites, LLMs, coding harnesses) to help you standardize your data, but please ensure that converted data has been checked for quality. 

If you are using an AI-based or -assisted workflow, please make sure to exercise due diligence to check for quality/accuracy, understanding that it is ultimately the Principal Investigator's responsibility to make the data truly reusable by other investigators. 
We also have repo for example conversion scripts?
-->

If you need help, please reach out to [help@emberarchive.org](mailto:help@emberarchive.org).

<!-- If you are a member of the **BBQS consortium**, you can also reach out to the Data Ingest Task Force by starting a discussion on the [BBQS Helpdesk](https://github.com/orgs/brain-bbqs/discussions) to request a streamlined pathway for uploading and data standardization. -->

---- 

## If you are interested in analysis tools

EMBER is also planning development of a cloud-based analysis ecosystem connected to the data storage resources:

- **EMBER-Hearth**: will support analysis pipelines such as spike sorting and pose estimation inference in the cloud through both EMBER-DANDI and EMBER-Vault. 


<br>
<figure style="text-align: center;" markdown>
<div style="display: flex; flex-direction: column; gap: 16px; align-items: center;" markdown>

<div style="width: 100%;" markdown="span">
![EMBER-DANDI and EMBER-Vault](assets/emberdandi_vault_hearth.png){ style="width: 100%;" }
<p style="font-size: 0.9em; margin-top: 4px;">

</p>
</div>

<!-- <div style="width: 100%;" markdown="span">
![Details of EMBER-DANDI and EMBER-Vault](assets/emberdandi_vault_detail.png){ style="width: 100%;" }
<p style="font-size: 0.9em; margin-top: 4px;">
  <strong>(B)</strong> EMBER-DANDI and EMBER-Vault
</p>
</div> -->

</div>

<figcaption style="margin-top: 8px;">
  Envisioned connection of analysis platform EMBER-Hearth to EMBER's data storage platforms.
</figcaption>
</figure>