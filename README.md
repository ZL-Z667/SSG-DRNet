# SSG-DRNet

SSG-DRNet: **State Space Guided Coordination of Semantics and Details for Medical Image Segmentation**.

## Overview

SSG-DRNet is a medical image segmentation framework based on state space modeling, designed to coordinate semantic information and fine-grained details for accurate segmentation across multiple datasets.

## 0. Environment Setup

You can set up the environment in either of the following ways:

### Create a Conda environment

```bash
conda env create -f environment.yml
```

### Install dependencies with pip

```bash
pip install -r requirements.txt
```

## 1. Dataset Preparation

### ISIC17 / ISIC18

- The ISIC17 and ISIC18 datasets are split in a 7:3 ratio.
- You can download them by following the instructions in [VM-UNet](https://github.com/JCruan519/VM-UNet).
- After downloading, place the datasets in `./data/isic17/` and `./data/isic18/` respectively.

Expected structure for ISIC17 (same for ISIC18):

```text
./data/isic17/
├── train
│   ├── images
│   │   └── *.png
│   └── masks
│       └── *.png
└── val
    ├── images
    │   └── *.png
    └── masks
        └── *.png
```

### ACDC

- For the ACDC dataset, you can follow [CSwin-UNet](https://github.com/eatbeanss/CSWin-UNet) to download the dataset, or download it from [Baidu](https://pan.baidu.com/s/1CYogWveMjiqnjEekW_huWA?pwd=trv9).
- After downloading, place the dataset in `./data/acdc/`.
- Then run `split_acdc.py` to split the dataset.

Expected structure:

```text
./data/acdc/
├── train
│   └── patientxxx
│       ├── patientxxx_framexx_gt.nii
│       └── patientxxx_framexx.nii
├── test
│   └── patientxxx
│       ├── patientxxx_framexx_gt.nii
│       └── patientxxx_framexx.nii
└── val
    └── patientxxx
        ├── patientxxx_framexx_gt.nii
        └── patientxxx_framexx.nii
```

### Synapse

- For the Synapse dataset, you can follow [Swin-UNet](https://github.com/HuCaoFighting/Swin-Unet) to download the dataset, or download it from [Baidu](https://pan.baidu.com/s/1JCXBfRL9y1cjfJUKtbEhiQ?pwd=9jti).
- After downloading, place the dataset in `./data/Synapse/`.

Expected structure:

```text
./data/Synapse/
├── lists
│   └── list_Synapse
│       ├── all.lst
│       ├── test_vol.txt
│       └── train.txt
├── test_vol_h5
│   └── casexxxx.npy.h5
└── train_npz
    └── casexxxx_slicexxx.npz
```

## 2. Pre-trained Weights

- The pre-trained VMamba weights can be downloaded from [Baidu](https://pan.baidu.com/s/1ci_YvPPEiUT2bIIK5x8Igw?pwd=wnyy) or [Google Drive](https://drive.google.com/drive/folders/1ZJjc7sdyd-6KfI7c8R6rDN8bcTz3QkCx?usp=sharing).
- After downloading, place the weights in `./pretrained_weights/`.

## 3. Train SSG-DRNet

```bash
cd SSGDRNet
python train.py         # Train and test SSG-DRNet on the ISIC17 or ISIC18 dataset
python train_acdc.py    # Train and test SSG-DRNet on the ACDC dataset
python train_synapse.py # Train and test SSG-DRNet on the Synapse dataset
```

## 4. Output Results

- After training, results will be saved in `./results/`.

## 5. Acknowledgments

We thank the authors of [VMamba](https://github.com/MzeroMiko/VMamba) and [VM-UNet](https://github.com/JCruan519/VM-UNet) for their open-source code.
