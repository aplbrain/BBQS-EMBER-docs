# Why do I need to standardize my data?

The ultimate goal for standardizing data is to enable secondary users to

1. reproduce previous results (e.g., figures from papers) and 
2. reuse data for new analyses or models.

# What standards are accepted?
EMBER accepts two standards: BIDS and NWB. 

- **BIDS (Brain Imaging Data Specification)** describes how to name files and organize them into appropriately named folders. It also requires metadata to describe data and the experiment. 
- **NWB (Neurodata without Borders)** is a single file that can hold multiple data streams and associated metadata that correspond to a single experimental session.

## Which standard should I use for my data?

You can choose to convert your data into either standard, or a combination of both. The important considerations are 

1. **Quality and reusability** — Does the standardized dataset contain enough information for someone unfamiliar with the experiment to understand and reuse it?
2. **Fit to the existing data structure** — Which standard requires the least unnecessary transformation from the original data representation?

### Guidelines

You can use the following decision aid to help you decide whether your data should be converted into BIDS, NWB, or some hybrid.

| Data characteristic | Standard | 
| -- | -- |
| My data are already separated by modality, session, and subject, and those modalities have established BIDS representations (e.g., separate EEG, video, audio, physiology, event, stimulus, or motion files). | [BIDS](https://bids-specification.readthedocs.io/en/stable/) and [BIDS extensions](https://bids.neuroimaging.io/extensions/beps.html) |
| A single file (e.g., .mat, .h5) of my data contains multiple time series modalities within it and/or featurized data corresponding to the same recording session | [NWB](https://nwb-schema.readthedocs.io/en/latest/format.html#type-specifications) and [NWB extensions](https://nwb-extensions.github.io) |

If both descriptions apply to substantial portions of your dataset, consider a hybrid approach: use BIDS for the overall dataset organization and modalities that map naturally to established BIDS representations, and use NWB for integrated recordings that are better represented together.

For example, in the following dataset, the raw modalities (EEG and behavioral events) are represented in separate BIDS folders. In the BIDS derivatives folder, a NWB file that combines processed EEG, events, and kinematics represents the integrated data.

```
my_study/
├── dataset_description.json
├── participants.tsv
├── participants.json
│
├── sub-01/
│   └── ses-01/
│       ├── eeg/
│       │   ├── sub-01_ses-01_task-walk_eeg.edf
│       │   ├── sub-01_ses-01_task-walk_eeg.json
│       │   ├── sub-01_ses-01_task-walk_channels.tsv
│       │   ├── sub-01_ses-01_task-walk_electrodes.tsv
│       │   └── sub-01_ses-01_task-walk_events.tsv
│       │
│       └── beh/
│           ├── sub-01_ses-01_task-walk_beh.tsv
│           └── sub-01_ses-01_task-walk_beh.json
│
├── sub-02/
│   └── ses-01/
│       ├── eeg/
│       │   └── ...
│       └── beh/
│           └── ...
│
└── derivatives/
    └── integrated-nwb/
        ├── dataset_description.json
        │
        ├── sub-01/
        │   └── ses-01/
        │       └── sub-01_ses-01_task-walk_desc-integrated.nwb
        │
        └── sub-02/
            └── ses-01/
                └── sub-02_ses-01_task-walk_desc-integrated.nwb

```


## How to Standardize

### AI tools

The use of AI tools to write conversion scripts is encouraged. Once you have decided on your conversion strategy, prompt your favorite AI tool with this strategy, pointing it at your unstandardized dataset. 

To help you get started, we've published some of the prompts and conversion scripts we've put together for certain datasets (link)

### Quality Check

There are two quality checks:

1. Is your standardized data correctly formatted with all necessary metadata? In other words, does this data pass the [DANDI validator](../user-guide/uploading-data.md#upload-data-to-your-dandiset)?
2. Can your standardized data be used by a secondary analyst who has little to no knowledge of your data to, at a minimum, recreate figures from your paper? 

The first check is relatively quick - once your data is standardized, you can run validation checks to ensure that it can be uploaded (see [uploading data](..assets/user-guide/uploading-data.md)) without errors to EMBER. 

The second (optional) check requires rebuilding analyses that were conducted on the original unstandardized data using the new, standardized data. At a minimum, this is recreation of figures generated for a publication.

!!! success "EMBER-verified"
    EMBER-DANDI datasets that meet this second quality check will be denoted as "EMBER Verified".

### Getting Help

If you need help or have any questions, please reach out to [help@emberarchive.org](mailto:help@emberarchive.org).