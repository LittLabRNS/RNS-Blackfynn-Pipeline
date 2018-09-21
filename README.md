# RNS-Blackfynn-Pipeline
This collection of scripts converts and analyzes the information in Neuropace RNS .dat files.

## Functions
* MEF_writer.jar converts .dat files to .mef files

* dat2mef_RNS.m calls MEF_writer.jar to convert Neuropace RNS .dat files to .mef files and organize them so that they can be uploaded to Blackfynn.

* dat2vector.m concatenates Voltage data in .dat files into vectors AllData and AllTime to allow for easy matrix calculations

* findStim finds Stimulations or Stimulation Groups in AllData and labels them according to number of stimulation per group, length of stimulation group, and gap between stimulations.

## Background
The Neuropace Responsive Neurostimulator (RNS) detects epileptiform activity and stimulates regions of the brain to terminate siezures. Though the RNS is continuously monitoring brain activity, it only saves 90 second recordings when it is triggered to do so. Recording triggers include:

* LONG EPISODES triggers initiate ECoG storage when a detected episode continues beyond a preset duration (LONG EPISODE LENGTH).

* PATTERN A and PATTERN B triggers initiate ECoG storage when an episode beginning with a characteristic pattern (Pattern A or Pattern B) is detected. Selecting one of these triggers may be helpful in evaluating the detection setting parameters.

* RESPONSIVE THERAPY triggers initiate ECoG storage when electrical stimulation therapy is delivered in response to a detected event. Selecting this trigger may be helpful in determining if therapy was delivered appropriately as well as evaluating the result of the therapy delivered.

* NOISE triggers initiate ECoG storage when a 60 Hz signal is detected in the ECoG signal. Selecting this trigger may be helpful in troubleshooting the RNS® System.

* SATURATION triggers initiate ECoG storage when the amplitude of the ECoG is high. Selecting this trigger may be helpful in troubleshooting the RNS® System.

* MAGNET triggers initiate ECoG storage when a magnet is passed by the RNS® Neurostimulator. Selecting this trigger may be helpful in storing electrographic events that correspond to clinical symptoms experienced by the patient.

* SCHEDULED triggers initiate ECoG storage at a specific time of day (ECOG STORAGE START TIMES). Selecting this trigger may be helpful in viewing activity occurring during specific times throughout the day.

### Therapy Sequence
Responsive therapy is delivered as a therapy sequence of up to 5 individually configured sequential
therapies (electrical stimulation) in response to each detected episode.

## Setup
### Installing dependencies
It is recommended to set up a virtual environment for these scripts in order to avoid conflicts with globally installed packages<sup>[1](#note-1)</sup>. This can be done using `pip` and `virtualenv`:
```bash
virtualenv env
source env/bin/activate # to enter the virtual environment
pip install -r requirements.txt
deactivate # to exit the virtual environment
```
### Configuring the Blackfynn client
For the Blackfynn API to work correctly, the user profile must be set up (see [this guide](http://docs.blackfynn.io/platform/clients/getting_started.html) for help).

### Inputs and Outputs

## Inputs
1. An ECoG_Catalog.csv file sent from Neuropace mapping each .dat file to a timestamp and a patient id
2. The .dat files sent from Neuropace for each patient in folders labeled UPenn_PatientInitials
3. A key list (in CSV form) we create that associates the processed file names with the patient whose data it contains 

## Outputs
1. The processed CSV file, which is outputted by the Python script and is identical to the original CSV file except that it also contains a column to keep track of the new file names
2. The processed .dat files, which are outputted by the Python script and are identical to the original .dat files in content but have been assigned to a different file name

## Notes
<b name="note-1">1.</b> Note that if this installation method is used, **all scripts** must also be run from inside the virtual environment.

## References
http://www.neuropace.com/manuals/RNS_System_Physician_Manual.pdf
