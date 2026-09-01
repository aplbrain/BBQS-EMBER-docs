# Data Upload
Once your user account and project have been set up, you are ready to upload your [***validated***](../user-guide/data-standardization.md#5-validation-required-before-upload) data to EMBER-Vault!

**1. Log in via Globus & EMBER-Vault**
<ol type="a">
  <li>Log in to Globus using your institutional or any other authentication method you use to access the Globus Web UI</li>

  <li>Once you're logged in to Globus, navigate to your collections and ensure the default "Recent Tasks" filter is deactivated
    <img src="/assets/VaultUpload_Fig1_Collections.png" alt="Collections screen in Globus Web UI"/>
  </li>

  <li>Search for "EMBER" and you should find your project's collection located on the <code>Ember-Vault Endpoint</code>
    <img src="/assets/VaultUpload_Fig2_GlobusCollectionSearch.png" alt="Collections ember search results screen in Globus Web UI"/>
  </li>

  <li>Select your project's EMBER Vault collection by clicking on the name. In this case, it is <code>EMBER-Vault YOUR-PROJECT-NAME</code></li> 
  
  <li>This should take you to the collection manager. Here, you should select <code>Open in File Manager</code> as indicated in the figure below
    <img src="/assets/VaultUpload_Fig3_ProjectCollectionManager.png" alt="Project collection manager in Globus Web UI"/>
  </li>

  <li>In the File Manager, you will be met with a warning that you are not authenticated with <code>auth.emberarchive-vault.org</code>. Press the <code>Continue</code> button in order to authenticate with EMBER-Vault
    <img src="/assets/VaultUpload_Fig4_ProjectFileManagerUnauth.png" alt="Project collection file manager in Globus Web UI"/>
  </li>
</ol>


!!! note
    If you have not yet created an account with EMBER-Vault and thus do not possess Keycloak credentials, please refer to the above section titled ``Account Setup``

<ol type="a" start="7">

<li>You will then be redirected to EMBER-Vault's user login page. Here, you will sign in using your EMBER-Vault credentials which were generated during account setup. <br><br>
These should be a username provided to you by admins ending in <code>@auth.emberarchive-vault.org</code> and the password you set up. <br><br>
After this screen you will also be prompted to enter a one-time code from your MFA application
  <img src="/assets/VaultUpload_Fig5_Keycloak.png" alt="Account login screen in EMBER-Vault Keycloak"/>
</li>

</ol>

**2. Select File/Folder to Upload**
<ol type="a">

  <li>Once you have signed in to Globus and EMBER-Vault, you can now access your EMBER-Vault project via the file manager. To begin uploading your data, click on the <code>Upload</code> button circled in the figure below.
    <img src="/assets/VaultUpload_Fig6_CollectionFileManager.png" alt="File manager for EMBER-Vault project collection in Globus web UI"/>
  </li>

  <li>Clicking the <code>Upload</code> button will bring up an option to select files or a folder to upload to the collection from your local machine. For this demonstration, we will be uploading a folder
    <img src="/assets/VaultUpload_Fig7_CollectionUpload.png" alt="File manager file/folder upload for EMBER-Vault project collection in Globus web UI"/>
  </li>

  <li>You will be prompted to select a folder in your local system to upload to EMBER-Vault via Globus. Select your desired folder and click <code>Upload</code>
    <img src="/assets/VaultUpload_Fig8_SelectFolder.png" alt="File manager file/folder select for upload to EMBER-Vault project collection in Globus web UI"/>
  </li>

  <li>You will then be prompted to confirm your upload, to do so select <code>Upload</code>
    <img src="/assets/VaultUpload_Fig9_ConfirmUpload.png" alt="File manager confirm upload to EMBER-Vault project collection in Globus web UI"/>
  </li>

  <li>You should then see in real time the upload progress of your file or each file in the folder you selected. Congratulations! You have successfully uploaded your data to EMBER-Vault :) 
    <img src="/assets/VaultUpload_Fig10_UploadSuccess.png" alt="File manager successful upload to EMBER-Vault project collection in Globus web UI"/>
  </li>

</ol>
