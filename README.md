# RNS-Blackfynn-Pipeline
This collection of scripts converts Neuropace RNS .dat files to .mef files, and organizes them so that they can be uploaded to Blackfynn.
The Neuropace Responsive Neurostimulator (RNS) detects epileptiform activity and stimulates regions of the brain to terminate siezures. Though the RNS is continuously monitoring brain activity, it only saves 90 second recordings when it is triggered to do so. Recording triggers

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

### Settings
Before running anything, make sure all of the correct settings and patient-specific info are set in `settings.py`. This file contains:

## Data Given By Neuropace
Neuropace sends us
1. An ECoG_Catalog.csv file mapping each .dat file to a timestamp and a patient id
2. The .dat files for each patient in folders labeled UPenn_PatientInitials
3. A list (in CSV form) that associates the processed file names with the patient whose data it contains 

## Outputs of Scripts


## Notes
<b name="note-1">1.</b> Note that if this installation method is used, **all scripts** must also be run from inside the virtual environment.

<b name="note-2">2.</b> I recommend using wheels to install the dependencies so that pip installs an optimized, pre-compiled version of numpy instead of building it from source. Newer versions of pip (9.0.1 and above) do this by default. Otherwise, this can be done by adding the `--use-wheel` option.
