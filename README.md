# MASAN
## Overview
Aiming at the problems of the high computational complexity of self-attention and unableto accurately measure the importance of items in the existing session-based recommendation methods combined with self-attention,a multi-interest aware adaptive self-attention network model is proposed for session-based recommendation. The overall framework of MASAN is depicted bellow.


<img src="https://github.com/JXY66/MASAN/assets/91231446/e0638695-6e21-400e-a4e3-081cb64613d4" width = "500px" align=center />

## Requirements
- entmax   1.0
- hyperopt   0.2.7
- pytorch  1.6.0 （cu102vers.）
- pyyaml   5.3.1
- tqdm  4.49.0
- CUDA    10.2
- cuDNN    7.6
- Python    3.7.9


Notice: The PyTorch installation is for the cu102 version, with Python version 3.7.9. All library dependencies are also stored in the requirements.txt file, which can be used to install them directly by executing the above command. 

## Datasets
We use three real-world benchmark datasets, including Yelp, Amazon Books and ML-1M. The details about full version of these datasets are on [RecSysDatasets](https://github.com/RUCAIBox/RecSysDatasets). For all datasets, we group the interaction records by users and sort them by the interaction timestamps ascendingly. 

## Folders
In the main directory:
run_recbole.py: main file for running the model via executing this python file.
In the recbole folder:
(1) properties folder: stores configuration files for parameters.
A. overall.yaml: main configuration file for setting parameters such as learning rate and epochs. For different datasets, only the learning rate needs to be changed.
B. model/MASAN.yaml: configuration file for model-related parameters, which is used to adjust different key hyperparameters.
C. dataset folder: configuration files for dataset parameters that do not need to be modified.
(2) model folder
A. model/layers.py: file for model components, where lines 340-351 are the interest aggregation layer and lines 353-504 are the adaptive self-attention network.
B. model/sequential_recommender/masan.py: file for constructing the entire model. Components from model/layers.py are used in the process.
dataset folder: stores the datasets.

