# Uploading Data

These instructions will guide you on how to upload data to EMBER-DANDI.

???+ info "Prerequisites"
    Please ensure that your data is formatted using NWB and BIDS before attempting to upload to EMBER-DANDI

    ??? question "My files are in a mix of standards or I have not used standards"
        Please contact the EMBER team at [help@emberarchive.org](mailto:help@emberarchive.org) to facilitate data ingestion into EMBER-DANDI. We are also happy to add you to our Slack workspace.


Below, we have provided one set of instructions for users that are new to EMBER-DANDI, and one set for experienced users. Please follow whichever best fits your needs:

1. [I've used DANDI or CLI tools before](#instructions-for-experienced-users)
2. [I'm new to Python, CLI, and/or DANDI](#instructions-for-new-users)
    - Learn how to set up Python, install the DANDI Client, and use NWB

----

## Instructions for Experienced Users

The following is a quick reference of the steps for uploading data using the DANDI Client:
```
dandi download https://dandi.emberarchive.org/dandiset/<dandiset_id>/draft
cd <dandiset_id>
dandi organize <source_folder> -f dry
dandi organize <source_folder>
dandi validate .
dandi upload -i ember-dandi
```

----

## Instructions for New Users

### Install Python and the DANDI Client

In these instructions, you will install Python 3.9+ and then install the DANDI Python Client.


#### Install Python

If you're new to Python, it may be useful to start by checking out [Python's Getting Started page](https://www.python.org/about/gettingstarted/) There are many ways to install and use Python, so we've highlighted a few common ways to get started below.

- [Install Anaconda](https://www.anaconda.com/docs/getting-started/getting-started)
- [Install uv](https://docs.astral.sh/uv/#installation)

#### Install the DANDI Client

Once you've gotten up and running with Python, the following command will install the DANDI Client:
```bash
pip install -U dandi
```

#### More Information

For more detailed information on the DANDI Python Client, please refer to the following resources:

- [DANDI Client on PyPI](https://pypi.org/project/dandi/)
- [DANDI Client docs](https://dandi.readthedocs.io/en/latest/)






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

1. Log in to [EMBER-DANDI](https://dandi.emberarchive.org) with your approved GitHub account
2. Select the "New Dandiset" button in the top right corner
3. Fill out basic metadata and hit "Register Dandiset"

<img src="https://ember-web-assets.s3.amazonaws.com/documentation-images/register_new_dandiset.png" alt="screenshot of the New Dandiset form on EMBER-DANDI website" style="width: 90%; display:block; margin-left: auto; margin-right: auto;">


### Upload data to your dandiset

1. Validate your converted files, replacing `<source_folder>` with the path to your .nwb files:  

    ```bash
    dandi validate --ignore DANDI.NO_DANDISET_FOUND <source_folder>
    ```

2. Navigate to your dandiset on EMBER-DANDI and copy the dandiset ID number

<img src="https://ember-web-assets.s3.amazonaws.com/documentation-images/test_number_data.png" alt="screenshot of where to find the Dandiset Id on EMBER-DANDI website" style="width: 90%; display:block; margin-left: auto; margin-right: auto;">

3. Upload your validated .nwb files using the following commands, replacing `<dandiset_id>` and `<source_folder>` with your specific information:  

    ```bash
    dandi download https://dandi.emberarchive.org/dandiset/<dandiset_id>/draft
    cd <dandiset_id>
    dandi organize <source_folder> -f dry
    dandi organize <source_folder>
    dandi validate .
    dandi upload -i ember-dandi
    ```

!!! note "Uploading Video Files"
    If using video files, replace `dandi organize "source folder"` with 
    `dandi organize --update-external-file-paths --files-mode copy /path/to/source_folder`
!!! warning "Password Prompt"
    If this is your first upload, you may get a prompt to enter a password.  In the EMBER-DANDI Portal, click on your user icon in the top right to retrieve your API key. Enter this when prompted for your password. 

    <img src="https://ember-web-assets.s3.amazonaws.com/documentation-images/API_key.png" alt="screenshot of the New Dandiset form" style="width: 50%; display:block; margin-left: auto; margin-right: auto;">
