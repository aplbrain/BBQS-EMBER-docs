# Getting Started

## What is EMBER?

EMBER is the Ecosystem for Multi-Modal Brain-behavior Experimentation and Research.

The EMBER Archive supports free storage and sharing of public neurophysiological and behavioral data, prioritizing data generated as a part of the [Brain Behavior Quantification and Synchronization (BBQS) Program](https://braininitiative.nih.gov/research/systems-neuroscience/brain-behavior-quantification-and-synchronization-program).

## Storage and Analytics Platforms

EMBER has two data storage platforms - EMBER-DANDI and EMBER-Vault. EMBER-Hearth enables sandboxed analyses in the cloud on both of these platforms. 

!!! note 
    EMBER-Hearth is currently in development. EMBER-DANDI and EMBER-Vault are functional.

EMBER-DANDI supports multimodal data from both animals and humans. Human data must not contain any PHI/PII and must be completely deidentified. 

If you want to store sensitive human data, use EMBER-Vault. 

<figure style="text-align: center;">
  <div style="display: flex; flex-direction: column; gap: 16px; align-items: center;">
    
    <div style="width: 100%;">
      <img src="/assets/emberdandi_vault_hearth.png"
           alt="EMBER-DANDI, EMBER-Vault, EMBER-Hearth"
           style="width: 100%;">
      <p style="font-size: 0.9em; margin-top: 4px;">
        <strong>(A)</strong> EMBER architecture
      </p>
    </div>

    <div style="width: 100%;">
      <img src="/assets/emberdandi_vault_detail.png"
           alt="Details of EMBER-DANDI and EMBER-Vault"
           style="width: 100%;">
      <p style="font-size: 0.9em; margin-top: 4px;">
        <strong>(B)</strong> EMBER-DANDI and EMBER-Vault
      </p>
    </div>

  </div>

  <figcaption style="margin-top: 8px;">
    EMBER-DANDI is the open data archive that can store animal and de-identified human data.
    EMBER-Vault is a HIPAA-compliant storage for identifiable human data, such as raw video and audio.
  </figcaption>
</figure>


## How do I upload data?

1. Standardize your data.
2. Create an account for each appropriate storage platform using instructions in the [User Guide](../user-guide/index.md).
3. Upload the standardized data to the appropriate storage platform(s) using instructions in the [User Guide](../user-guide/index.md).


### Standardizing Data
The general approach is to organize your data using the BIDS schema and convert relevant data into NWB. 

BIDS broadly describes how to rename files and folders and organize them into a standardized directory. It als requires associated metadata files to help explain the experiment and data.

NWB is a specific file type that can store one more modalities within it. Relevant metadata is also stored directly inside the NWB file.

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



### I'm new to these standards - how can I get help? 

More specific instructions for how to standardize data can be found in the [User Guide](../user-guide/index.md). 

Feel free to use AI tools like ChatGPT and Codex to help you convert your data according to the standards.

If you need help, please reach out to [help@emberarchive.org](mailto:help@emberarchive.org)






