# RNS-Blackfynn-Pipeline
This collection of scripts converts Neuropace RNS .dat files to .mef files, and organizes them so that they can be uploaded to Blackfynn.

## Setup
### Installing dependencies
It is recommended to set up a virtual environment for these scripts in order to avoid conflicts with globally installed packages<sup>[1](#note-1)</sup>. This can be done using `pip`<sup>[2](#note-2)</sup> and `virtualenv`:
```bash
virtualenv env
source env/bin/activate # to enter the virtual environment
pip install -r requirements.txt
deactivate # to exit the virtual environment
```

### Configuring the Blackfynn client
For the Blackfynn API to work correctly, the user profile must be set up (see [this guide](http://docs.blackfynn.io/platform/clients/getting_started.html) for help).

