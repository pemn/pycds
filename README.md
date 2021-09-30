# pycds
Client for Microsoft Dataverse/CDS/Dynamics CRM tables
## Description
A simple and easy to mantain dataverse client.  
Dataverse/CDS/Dynamics is a easy-to-use and powerful database for structured data. Also can store files in special fields. Think SQL+ADAUTH+HTTPD+RESTAPI.  
The main selling point is easy integration to the Office365 ecosystem and the fact it comes bundled with Enterprize plans.  
The requests module is the workhorse for handling REST API calls.  
Settings are stored externally in a json file to avoid hardcoding sensitive parameters.  
## Features
 - Pandas integration for download, upload and deletion of table records using DataFrames
 - Frictionless (as possible) oauth2 authentication using a automated Chrome window
 - Built-in encrypted token storage for a white picket fence level security. No credentials are stored, only token tied to your Azure AppId.
 - Automatic handling of odata pagination, enabling full download of datasets over 5000 records.
 - Lean implementation allowing direct use of the requests methods
## Recomended Python Distribution
WinPython 3.8+
## Modules Required
(multiple modules included by default in WinPython)  
`pip install msal`  
`pip install selenium`  
Selenium requires the apropriated chromedriver.exe to be in the same folder or somewhere in $PATH.
Download the latest version on:  
https://chromedriver.chromium.org/downloads
## Tutorial
### Installation
Manually download all files.  
Edit the `dataverse_settings.json` file with your organization specific parameters.  
A Azure App Id is required. Create one in azure portal if needed.  
Tenant Id and server URL can be found in: Office365 > Power Apps > Session Details.
### Usage
Instantiate the client and call the authenticate function:  
```
from dataverse import DataverseClient
client = DataverseClient()
client.authenticate()
```
Tipical use would be using the the .get() and .post() methods. More details on the help() documentation of each method.  
Usefull methods:  
 - get
 - post
 - upload_df
 - delete_df
### Example 1 - Download an entire CDS table to CSV file
```
df = client.get('crfbc_table1')
df.to_csv('table1download.csv', index=False)
```
### Example 2 - Upload data from a CSV file as new records on a CDS table
```
import pandas as pd
df = pd.from_csv('table1upload.csv')
client.upload_df('crfbc_table1', df)
```
## License
Apache 2.0
