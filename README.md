# [INT3123_20] EvolveGCN Experiments
Paper: [EvolveGCN](https://arxiv.org/abs/1902.10191)
Official code: [IBM/EvolveGCN](https://github.com/IBM/EvolveGCN)

This is the Experiments Reproduction code of EvolveGCN for the course ** INT3123_20 **. 
Members of our group:
1. Hoàng Thị Thu Hà - MSV: 21020189
2. Phạm Ngọc Thạch  - MSV: 21020113
3. Trần Đức Anh     - MSV: 21020606

# Instructions to reproduce the experiments

There are 2 folders containing the code: EvolveGCN and EvolveGCN_DGL.
- EvolveGCN contains the official code of the paper. We use this folder for experiments on Link Prediction and Edge Classification tasks. 
- EvolveGCN_DGL contains the code to run experiments on Node Classification task.

The Log folder contains the log files where the information about the experiment and validation metrics was saved, divided into 3 folders corresponding to 3 tasks in our experiments. 

## Data

7 datasets were used in the paper:

- stochastic block model
- bitcoin OTC: Downloadable from http://snap.stanford.edu/data/soc-sign-bitcoin-otc.html
- bitcoin Alpha: Downloadable from http://snap.stanford.edu/data/soc-sign-bitcoin-alpha.html
- uc_irvine: Downloadable from http://konect.uni-koblenz.de/networks/opsahl-ucsocial
- autonomous systems: Downloadable from http://snap.stanford.edu/data/as-733.html
- reddit hyperlink network: Downloadable from http://snap.stanford.edu/data/soc-RedditHyperlinks.html
- elliptic: A preprocessed version of https://www.kaggle.com/ellipticco/elliptic-data-set

** Note **: The Elliptic dataset is used for Node Classification task, so this dataset is contained in Elliptic folder inside EvolveGCN_DGL. 
On the other hand, EvolveGCN contains 5 datasets: SBM, BC-OTC, BC-Alpha, Autonomous Systems and Reddit hyperlink network. The dataset UC_irvine is not downloadable anymore. Downloaded data sets are placed in the 'data' folder.
Because some datasets are to large, we have compressed them into .rar file.

## Requirements
### General
- PyTorch 1.0 or higher
- Python 3.6 or higher

### Other dependency for EvolveGCN_DGL
* Deep Graph Library (DGL)
* Pandas
* Numpy


## Set up with Docker
There are clear instructions in the official Github repository for Docker set up to reproduce the experiments: https://github.com/IBM/EvolveGCN

## Usage

### For experiments in EvolveGCN folder

Set --config_file with a yaml configuration file to run the experiments. For example:

```sh
python run_exp.py --config_file ./experiments/parameters_example.yaml
```

Most of the parameters in the yaml configuration file are self-explanatory. For hyperparameters tuning, it is possible to set a certain parameter to 'None' and then set a min and max value. Then, each run will pick a random value within the boundaries (for example: 'learning_rate', 'learning_rate_min' and 'learning_rate_max').
The 'experiments' folder contains one file for each result reported in the [EvolveGCN paper](https://arxiv.org/abs/1902.10191).

Setting 'use_logfile' to True in the configuration yaml will output a file, in the 'log' directory, containing information about the experiment and validation metrics for the various epochs. The file could be manually analyzed, alternatively 'log_analyzer.py' can be used to automatically parse a log file and to retrieve the evaluation metrics at the best validation epoch. For example:
```sh
python log_analyzer.py log/filename.log
```

### For experiments in EvolveGCN_DGL folder

<!-- #### Dependency
* Deep Graph Library (DGL)
* Pandas
* Numpy -->

* Donwload Elliptic dataset from [kaggle](https://kaggle.com/ellipticco/elliptic-data-set)
* Unzip the dataset into a raw directory. For example in our code: INT3123_20-EvolveGCN-Experiments/EvoveGCN_DGL/Elliptic/elliptic_bitcoin_dataset/
* Make a new dir to save processed data. For example in our code: INT3123_20-EvolveGCN-Experiments/EvoveGCN_DGL/Elliptic/processed
* Run train.py by:

```bash
python train.py --raw-dir EvoveGCN_DGL/Elliptic/elliptic_bitcoin_dataset/ --processed-dir EvoveGCN_DGL/Elliptic/processed
```

## Results

We have reproduced some of the experiments which have the outstanding results presented in Table 2, Figure 3 and Figure 4 in the paper.
In general, the results we got are closely aligned with the results proposed. For more details, we have meticulously documented the experiments's results in our report.
The logs we got are also saved in the log files in Log folder.









 

