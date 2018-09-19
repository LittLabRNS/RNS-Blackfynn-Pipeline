# RNS-Blackfynn-Pipeline
This collection of scripts converts Neuropace RNS .dat files to .mef files, and organizes them so that they can be uploaded to Blackfynn.

## Background
The Neuropace Responsive Neurostimulator (RNS) detects epileptiform activity and stimulates regions of the brain to terminate siezures. Though the RNS is continuously monitoring brain activity, it only saves 90 second recordings when it is triggered to do so. Recording triggers include:

* LONG EPISODES triggers initiate ECoG storage when a detected episode continues beyond a preset duration (LONG EPISODE LENGTH). This trigger can be used whenever detection is ENABLED.

* PATTERN A and PATTERN B triggers initiate ECoG storage when an episode beginning with a characteristic pattern (Pattern A or Pattern B) is detected. Selecting one of these triggers may be helpful in evaluating the detection setting parameters. These triggers can be used whenever detection is ENABLED.

* RESPONSIVE THERAPY triggers initiate ECoG storage when electrical stimulation therapy is delivered in response to a detected event. Selecting this trigger may be helpful in determining if therapy was delivered appropriately as well as evaluating the result of the therapy delivered. This trigger can be used whenever responsive therapy is ENABLED.

* NOISE triggers initiate ECoG storage when a 60 Hz signal is detected in the ECoG signal. Selecting this trigger may be helpful in troubleshooting the RNS® System. This trigger can be used whenever detection is ENABLED.

* SATURATION triggers initiate ECoG storage when the amplitude of the ECoG is high. Selecting this trigger may be helpful in troubleshooting the RNS® System. This trigger can be used whenever detection is ENABLED.

* MAGNET triggers initiate ECoG storage when a magnet is passed by the RNS® Neurostimulator. Selecting this trigger may be helpful in storing electrographic events that correspond to clinical symptoms experienced by the patient.

* SCHEDULED triggers initiate ECoG storage at a specific time of day (ECOG STORAGE START TIMES). Selecting this trigger may be helpful in viewing activity occurring during specific times throughout the day. This trigger can be used whenever scheduled ECoGs are ENABLED.

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
