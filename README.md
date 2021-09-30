# pycds
Client for Microsoft Dataverse/CDS/Dynamics CRM tables
## Description
A simple and easy to mantain dataverse client.  
Uses msal for oauth2 autentication. Uses selenium to display a browser window for user autentication and automated token retrieval.  
The requests module is the workhorse for handling REST API calls.
Settings are stored externally in a json file to avoid hardcoding sensitive parameters.  
## Recomended Python Distribution
WinPython 3.8+
## Modules Required
(multiple modules included by default in WinPython)
pip install msal
pip install selenium
## License
Apache 2.0
