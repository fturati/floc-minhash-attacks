# Attack on the MinHash Hierarchy
## Prerequisites

A requirements.txt file is also provided.
Example setup using a virtual environment on Windows.
```powershell
python -m venv ./venv
.\venv\Scripts\activate
pip install -r requirements.txt
```

## Dataset

The dataset is available for download [here](https://archive.ics.uci.edu/dataset/339/taxi+service+trajectory+prediction+challenge+ecml+pkdd+2015)
The README.md file in the `data/` folder contains more information on where to place the necessary downloaded dataset.

## Attacks

* `minhash.py` contains preimage attacks for MinHash.
* `porto_trajectories.py` contains the attack on a reproduction of the settings from the MinHash Hierarchy system experiments.

## Usage 

Both file contain a main function and can be run individually.
```shell
python3 minhash.py
python3 porto_trajectories.py
```
It is also possible to play with some of the variable parameters in the main function.