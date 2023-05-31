# Dataset

We provide a file used during the FLoC Origin Trial to map SimHashes to FLoC ID. It was located on a user's machine. 
For example on windows could find this file following `%userprofile%\appdata\Local\Google\Chrome\User Data\Floc\1.0.6`

The MovieLens 25M dataset can be downloaded [here](https://grouplens.org/datasets/movielens/25m/).

The included Tranco list is taken from [here](https://tranco-list.eu/list/NLKW/1000000). 

The host_list.json is taken from Shigeki's [floc_simulator](https://github.com/shigeki/floc_simulator/blob/WIP/demos/floc_sample/host_list.json).
It is used in `../chromium_floc`.

```
data
├── Floc
│   └── 1.0.6
│      └── SortingLshClusters 
├── ml-25m
│   ├── genome-scores.csv
│   ├── ...
│   └── tags.csv
├── host_list.json
├── README.md
└── tranco_NLKW.csv
```