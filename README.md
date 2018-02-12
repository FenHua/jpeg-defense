# Shield: Fast, Practical Defense and Vaccination for Deep Learning using JPEG Compression

## Overview

This is the code repository for the under-review KDD 2018 Applied Data Science paper: **Shield: Fast, Practical Defense and Vaccination for Deep Learning using JPEG Compression**

The code included here reproduces our techniques (e.g. SHIELD) presented in the paper, and also our experiment results reported, such as using various JPEG compression qualities to remove adversarial perturbation introduced by Carlini-Wagner-L2, DeepFool, I-FSGM, and FSGM.

## Installation and Setup

### Install Dependencies

This repository requires [Cleverhans](https://github.com/tensorflow/cleverhans) and [TensorFlow-Slim image classification model library](https://github.com/tensorflow/models/tree/master/research/slim), please see their respective pages for instructions for installation.

> Note: When installing [TF-slim image models library](https://github.com/tensorflow/models/tree/master/research/slim), find `models/research/slim`, and put directory `slim` under `utils`. So that your directory structure should contain `utils/slim`.

### Config Home Directory

In `constants.py`, fill in the home directory of your choice.

```python
HOME_DIR = '' # eg. '/home/yourusername/'
```

## Example usage:

```bash
python orchestrator.py --use_gpu 0 --debug false --perform attack --models resnet_50_v2 --attacks fgsm,df
```

```bash
python orchestrator.py --use_gpu 0 --debug true --perform evaluate --models resnet_50_v2 --checkpoint_paths /home/.../model.ckpt --attacks fgsm --defenses jpeg --attack_ablations '{"fgsm": [{"ord": Infinity, "eps": 2}]}' --defense_ablations '{"jpeg": [{"quality": 60}]}'
```

```bash
python retrain.py --use_gpu 0 --model_name resnet_50_v2 --jpeg_compression_quality 90
```

## Researchers

|  Name                 | Affiliation                     |
|-----------------------|---------------------------------|
| Nilaksh Das           | Georgia Institute of Technology |
| Madhuri Shanbhogue    | Georgia Institute of Technology |
| Shang-Tse Chen        | Georgia Institute of Technology |
| Fred Hohman           | Georgia Institute of Technology |
| Siwei Li              | Georgia Institute of Technology |
| Li Chen               | Intel Corporation               |
| Michael E. Kounavis   | Intel Corporation               |
| Polo Chau             | Georgia Institute of Technology |