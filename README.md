# MASAN

## Overview
Aiming at the problems of the high computational complexity of self-attention and unable to accurately measure the importance of items in the existing session-based recommendation methods combined with self-attention,a multi-interest aware adaptive self-attention network model is proposed for session-based recommendation. The overall framework of MASAN is depicted bellow.

<img src="https://github.com/JXY66/MASAN/assets/104990190/2e56cbba-bd63-429b-82c3-9dbfbd10b9f2" width = "500px" align=center />

## Requirements
- entmax   1.0
- hyperopt   0.2.7
- pytorch  1.6.0 （cu102 ver.）
- pyyaml   5.3.1
- tqdm  4.49.0
- CUDA    10.2
- cuDNN    7.6
- Python    3.7.9

Notice: The PyTorch library is installed with cu102 version and the Python version is 3.7.9. All library dependencies are stored in the requirements.txt file and can be installed directly by executing the above command.

## Datasets
We use three real-world benchmark datasets, including Yelp, Amazon Books and ML-1M. The details about full version of these datasets are on [RecSysDatasets](https://github.com/RUCAIBox/RecSysDatasets). For all datasets, we group the interaction records by users and sort them by the interaction timestamps ascendingly. 

## Folders
In the main folder:
run_recbole.py: This is the main file used to run the model by executing this .py file.

In the recbole folder:
(1) properties folder: This folder contains parameter configuration files.
A. overall.yaml: This is the main configuration file where parameters such as learning rate, epochs, etc. are set. For different datasets, only the learning rate needs to be changed.
B. model/MASAN.yaml: This file contains the configuration for model-related parameters, allowing adjustment of different key hyperparameters.
C. dataset folder: This folder contains the parameter configurations for the dataset, and usually does not need to be modified.

(2) model folder:
A. model/layers.py: This file contains the relevant components of the model, with lines 340-351 being the interest aggregation layer, and lines 353-504 representing the adaptive self-attention network.
B. model/sequential_recommender/masan.py: This file is responsible for building the entire model. During the model construction process, components from model/layers.py are utilized.

(3)dataset folder: This folder contains the dataset.
