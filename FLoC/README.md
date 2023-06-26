# Attacks on FLoC

This folder contains the code for the attacks on FLoC and their evaluation. 
It is adapted from the technical report **"Analysing and exploiting Google's FLoC advertising proposal"**.

## Table of Contents

- [Requirements](#requirements)
- [Data](#data)
- [Directory Structure](#directory-structure)
- [Usage](#usage)


## Requirements

This project makes use of [LeakGAN](https://github.com/CR-Gjx/LeakGAN) by [@CR-Gjx](https://github.com/CR-Gjx).
Note that they do not provide a license for their code.

It requires the use of Python 2.7 and Tensorflow r1.2.1 but we updated the requirements to Python 3.6 and TensorFlow 1.8.0.

For convenience, we provide a conda environment file for Windows users (tested on Windows 10 and 11). Some listed dependencies may not be needed anymore.
```shell
conda env create -f attacks-on-floc-windows.yml
```

A requirements.txt file is also provided. It however does not contain all dependencies that are in the conda env.
```shell
pip install -r requirements-cpu.txt
```

A docker is also provided for running using only the CPU. 
For training a GAN this is very slow, so an example of running a docker with a GPU is also given.
```shell
docker compose up -d 
docker ps                                 # check the name of the container e.g. attack-floc
docker exec -it attack-floc /bin/bash     # replace attack-floc by name of container in previous command if different

```


An example running inside a docker
```shell
docker run -it -v "/path/to/repo":/home/attacks python:3.6.13-slim /bin/bash
cd /home/attacks/FLoC
python -m venv ./venv 
source ./venv/bin/activate
apt update
apt upgrade
apt install build-essential
python3 -m pip install -r requirements-cpu.txt
cd GAN
python3 ml-25m_main.py
```

Note that training the GAN with an nvidia GPU requires specific Nvidia drivers that are cumbersome to install.
The provided conda environment only works on Windows, but it also takes care of installing the Nvidia GPU drivers.
However, to train the GAN using a GPU it is also possible to use a docker with tensorflow and the Nvidia driver installed.

```shell
docker run -it --gpus all -v "/path/to/folder/FLoC":/home tensorflow/tensorflow:1.8.0-gpu-py3 /bin/bash
# inside the container run 
cd /home 
pip install -r requirements-gpu-docker.txt
cd GAN
python ml-25m_main.py
```
This docker should be only used to train the GAN, since it uses Python 3.5.2 and other libraries require python 3.6


## Data
We provide the file used during the FLoC Origin Trial to map SimHashes to FLoC ID.

The Tranco list used can be found [here](https://tranco-list.eu/list/NLKW/1000000).

The MovieLens 25M dataset can be downloaded [here](https://grouplens.org/datasets/movielens/25m/).

The README.md file in the `data/` folder contains more information on where to place the necessary downloaded dataset.

## Directory Structure

```
FLoC
├── attack
│   ├── generating_histories.py
│   ├── ...
│   └── README.md
├── chromium_components
│   ├── cityhash.py
│   ├── ...
│   └── sorting_lsh_cluster.py
├── chromium_floc
│   ├── floc_sample.py
│   └── setup.py
├── data
│   ├── Floc
│   │   └── 1.0.6
│   │       └── SortingLshClusters
│   ├── ml-25m
│   │   └── ...
│   ├── host_list.json
│   └── tranco_NLKW.csv
├── evaluation
│   ├── logs
│   ├── saved
│   ├── anonymity_evaluation.py
│   ├── ...
│   └── wasserstein_distance.py
├── GAN
│   ├── chkpts_ml25m
│   ├── save_ml25m
│   ├── dataloader.py
│   ├── ...
│   └── README.md
├── preprocessing
│   ├── movielens_extractor.py
│   ├── ...
│   └── vocab_corpus_builder.py
├── README.md
└── utils.py
```

## Usage

First the LeakGAN needs to be trained, this can be done by running the `ml-25m_main.py` file in the `GAN` folder.
It was trained on a Windows computer using an Nvidia GeForce RTX 2070 Super.

Then, once some checkpoints from the GAN training have been saved, it is possible to run `pipeline.py` in the `evaluation` folder.
It runs the GAN-IP attack on FLoC.

Each folder containing code has its own `README.md` which provide additional information on its content. 

