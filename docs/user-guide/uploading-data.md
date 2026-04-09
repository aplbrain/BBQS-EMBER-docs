# Upload Data

These instructions will guide you on how to upload data to EMBER-DANDI. 

Please follow the instructions for the option that best fits your needs:

**My files are all in NWB and BIDS:**

Below, we have provided one set of instructions for users that new to EMBER-DANDI, and one set for experienced users.

1. [I've used DANDI or CLI tools before](#instructions-for-experienced-users)
2. [I'm new to Python, CLI, and/or DANDI](#instructions-for-new-users)
    - Learn how to set up Python, install the DANDI CLI, and use NWB

**My files are in a mix of standards or I have not used standards:**

Please contact the EMBER team at [help@emberarchive.org](mailto:help@emberarchive.org) to facilitate data ingestion into EMBER-DANDI. We are also happy to add you to our Slack workspace.


## Instructions for Experienced Users

The following is a quick reference of the steps for uploading data using the DANDI CLI:
```
dandi download https://dandi.emberarchive.org/dandiset/<dandiset_id>/draft
cd <dandiset_id>
dandi organize <source_folder> -f dry
dandi organize <source_folder>
dandi validate .
dandi upload -i ember-dandi
```

## Instructions for New Users

### Install Python

If you're new to Python, it may be useful to start by checking out (Python's Getting Started page)[https://www.python.org/about/gettingstarted/]. There are many ways to install and use Python, so we've highlighted a few common ways to get started below.
- [Install Anaconda](https://www.anaconda.com/docs/getting-started/getting-started)
- [Install uv](https://docs.astral.sh/uv/#installation)

### Install the [DANDI Client](https://pypi.org/project/dandi/)

Once you've gotten up and running with Python, the following command will install the DANDI CLI:
```bash
pip install -U dandi
```

### Register for an EMBER-DANDI Account

The steps for registering for an EMBER-DANDI account can found on our [Getting Started](../getting-started/index.md#account-creation) page.

### Getting Started with NWB

For the latest information on NWB (Neurodata Without Borders), we recommend referring to their documentation at [nwb.org](https://nwb.org)!

Below, you will find a brief set of steps to help you quickly get started with NWB.

1. We recommended installing the [NWB Guide](https://nwb-guide.readthedocs.io/en/stable/installation.html), a desktop application that converts common neuroscience data formats into NWB to enable uploading to EMBER-DANDI.
2. Complete key tutorials for NWB GUIDE:
    - [Generate a dataset](https://nwb-guide.readthedocs.io/en/stable/tutorials/dataset.html)
    - Convert a [single session of data](https://nwb-guide.readthedocs.io/en/stable/tutorials/single_session.html)
    - Convert a [multi-session of data](https://nwb-guide.readthedocs.io/en/stable/tutorials/multiple_sessions.html)
3. Repeat steps with your own your data
    - Important Note: All data formats are not currently supported! Ensure your data is supported by checking the [ecosystem compatibility](https://nwb-guide.readthedocs.io/en/stable/format_support.html)

### Create an EMBER-DANDI dandiset

1. Log in to EMBER-DANDI with your approved GitHub account
2. Select the "New Dandiset" button in the top right corner
3. Fill out basic metadata and hit "Register Dandiset"

### Upload data to your dandiset

1. Validate your converted files, replacing `<source_folder>` with the path to your .nwb files:  

    ```bash
    dandi validate --ignore DANDI.NO_DANDISET_FOUND <source_folder>
    ```

2. Navigate to your dataset in the EMBER-DANDI archive and copy the dandiset ID number
3. Upload your validated .nwb files using the following commands, replacing `<dandiset_id>` and `<source_folder>` with your specific information:  

    ```bash
    dandi download https://dandi.emberarchive.org/dandiset/<dandiset_id>/draft
    cd <dandiset_id>
    dandi organize <source_folder> -f dry
    dandi organize <source_folder>
    dandi validate .
    dandi upload -i ember-dandi
    ```