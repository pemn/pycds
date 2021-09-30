# pycds
Client for Microsoft Dataverse/CDS/Dynamics CRM tables
## Description
A simple and easy to mantain dataverse client.  
Uses msal for oauth2 autentication. Uses selenium to display a browser window for user autentication and automated token retrieval.  
The requests module is the workhorse for handling REST API calls.
Settings are stored externally in a json file to avoid hardcoding sensitive parameters.  
## Features
 - Pandas integration for download, upload and deletion of table records
 - Easy oauth2 authentication using a automated Chrome window
 - Bultt-in encrypted token storage
 - Lean implementation allowing direct use of the requests methods
## Recomended Python Distribution
WinPython 3.8+
## Modules Required
(multiple modules included by default in WinPython)  
`pip install msal`  
`pip install selenium`  
## Tutorial
### Installation
Manually download all files.  
Edit the `dataverse_settings.json` file with your organization specific parameters.  
### Usage
Instantiate the client and call the authenticate function:  
```from dataverse import DataverseClient
client = DataverseClient()
client.authenticate()```
Tipical use would be using the the .get() and .post() methods. More details on the help() documentation of each method.  
Usefull methods:  
 - get
 - post
 - upload_df
 - delete_df
### Example 1 - Download an entire CDS table to CSV file
```df = client.get('crfbc_table1')
df.to_csv('table1.csv', index=False)```
### Example 2 - Upload data from a CSV file as new records on a CDS table
```df = pd.from_csv('table1upload.csv')
client.upload_df('table1', df)```
## License
Apache 2.0
