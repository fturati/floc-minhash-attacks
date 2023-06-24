# Attack on the MinHash Hierarchy
## Prerequisites

A requirements.txt file is provided.
Example setup using a virtual environment on Windows.
```powershell
python -m venv ./venv
.\venv\Scripts\activate
pip install -r requirements.txt
```

A docker is also provided (see [Usage](#usage) section).


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

Running with docker.
The Dockerfile has a command to keep running even if no command is specified in the docker-compose.yml.

By default, it will run porto_trajectories.py. This can be changed in docker-compose.yml

```shell
# in the same folder as the docker-compose.yml file run:
docker compose up
# Can also start a shell in the running container
docker ps # check the container's name e.g. attack 
docker exec -it attack /bin/bash
# Should be in /source
python minhash.py
exit
# container does not stop so that can exec shell inside it
docker stop attack 
```

### Outputs
Running porto_trajectories.py will create a log folder and output its path on the terminal.
In that log folder the console_output.txt file contains some debug information about the run along with some statistic on the attack.