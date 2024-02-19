# MASAN

## Overview
Aiming at the problems of the high computational complexity of self-attention and unable to accurately measure the importance of items in the existing session-based recommendation methods combined with self-attention,a multi-interest aware adaptive self-attention network model is proposed for session-based recommendation. The overall framework of LightSANs is depicted bellow.

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

Notice: For all sequencial recommendation models, we use the first version of RecBole v0.1.1 to do our experiments. The more details are on [RecBole](https://github.com/RUCAIBox/RecBole). For efficient Transformers([Synthesizer](https://github.com/leaderj1001/Synthesizer-Rethinking-Self-Attention-Transformer-Models), [LinTrans](https://linear-transformers.com), [Linformer](https://github.com/tatp22/linformer-pytorch), [Performer](https://github.com/lucidrains/performer-pytorch)), we implement them under RecBole Framework based on the source code, in order to ensure fair comparation. 

## Datasets
We use three real-world benchmark datasets, including Yelp, Amazon Books and ML-1M. The details about full version of these datasets are on [RecSysDatasets](https://github.com/RUCAIBox/RecSysDatasets). For all datasets, we group the interaction records by users and sort them by the interaction timestamps ascendingly. 

## Parameter Settings
We apply the leave-one-out strategy for evaluation, and employ HIT@k and NDCG@k to evaluate the performance. For fair evaluation, we pair each ground truth item in the test set with all items of dataset.

For all SANs-based models, 2 layers of self-attention are deployed, both of which have 2 attention heads. The hidden-dimension of embeddings are set to 64 uniformly. The maximum sequence length is 100, 150 and 200 and the parameter _k_interests_ of LightSANs is 10, 15 and 20 on Yelp, Books and ML-1M datasets, respectively. The dropout rate of turning off neurons is 0.2 for ML-1M and 0.5 for the other four datasets due to their sparsity. The low-rank projected dimension in Synthesizer, Linformer and Performer are set as the same as _k_interests_. We use the Adam optimizer with a learning rate of 0.003 on GPU (TITAN Xp), where the batch size is set as 1024 and 2048 in the training and the evaluation stage, respectively. 

More details about the settings are in .yaml files in properties/dataset and properties/model.


## Acknowledgement
Any scientific publications that use our codes and datasets should cite the following paper as the reference:
````
@inproceedings{Fan-SIGIR-2021,
    title = "Lighter and Better: Low-Rank Decomposed Self-Attention Networks for Next-Item Recommendation",
    author = {Xinyan Fan and
              Zheng Liu and
              Jianxun Lian and
              Wayne Xin Zhao and
              Xing Xie and 
              Ji{-}Rong Wen},
    booktitle = {{SIGIR}},
    year = {2021},
}
````
If you have any questions for our paper or codes, please send an email to xinyan.fan@ruc.edu.cn.
