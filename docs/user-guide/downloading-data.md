# Downloading Data

These instructions will guide you on how to download data to EMBER-DANDI.

Below, we have provided one set of instructions for users that are new to EMBER-DANDI, and one set for experienced users. Please follow whichever best fits your needs:

1. [I've used DANDI or CLI tools before](#instructions-for-experienced-users)
2. [I'm new to Python, CLI, and/or DANDI](#instructions-for-new-users)
    - Learn how to set up Python, install the DANDI CLI, and use NWB

----

## Instructions for Experienced Users

### Download a full dandiset

The following is a quick reference for downloading data using the DANDI Client:
```
dandi download https://dandi.emberarchive.org/dandiset/<dandiset_id>/<version>
```

----

## Instructions for New Users

### Install Python and the DANDI Client

Please refer to our [Dandi Client](../user-guide/uploading-data.md#instructions-for-new-users) instructions.

### Download a full dandiset

1. Navigate to the dandiset of interest on [EMBER-DANDI](https://dandi.emberarchive.org/dandiset)

2. Click the "Download" tab on the right-hand panel.
    - Hint: If you want a different version of the dandiset than the default, click the dropdown labeled "Download a different version?" and select the desired version.

    <img src="https://ember-web-assets.s3.amazonaws.com/documentation-images/download_dandiset.png" alt="screenshot of where to find the Download button for a dandiset on EMBER-DANDI website" style="width: 70%; display:block; margin-left: auto; margin-right: auto;">

3. Copy the command and paste it into your terminal. For example,
    ```bash
    dandi download https://dandi.emberarchive.org/dandiset/<dandiset_id>/draft
    ```

### Download a single file

1. Navigate to the dandiset of interest on [EMBER-DANDI](https://dandi.emberarchive.org/dandiset)

2. Click the "Files" tab on the right-hand panel.

    <img src="https://ember-web-assets.s3.amazonaws.com/documentation-images/files_tab.png" alt="screenshot of where to find the Files button for a dandiset on EMBER-DANDI website" style="width: 100%; display:block; margin-left: auto; margin-right: auto;">

3. On the file explorer page for the dandiset, navigate to the folder containing the desired file (if not at the root level)

4. Click the download button on the desired file.
