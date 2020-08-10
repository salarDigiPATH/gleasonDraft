# Pix2PixHD for PANDA Challenge
This is the code for Prostate cANcer graDe Assessment (PANDA) challenge. Check [here](https://www.kaggle.com/c/prostate-cancer-grade-assessment)

The first step is to create image patches for training and validation of the segmentation model. The dataset consists of around 11,000 whole-slide images of digitized H&E-stained biopsies originating from two centers. These two centers are Radboud University Medical Center and Karolinska Institute. These two centers labelled the images differently.

Radboud: Prostate glands are individually labelled. Valid values are:
0: background (non tissue) or unknown
1: stroma (connective tissue, non-epithelium tissue)
2: healthy (benign) epithelium
3: cancerous epithelium (Gleason 3)
4: cancerous epithelium (Gleason 4)
5: cancerous epithelium (Gleason 5)

(./images/Radbound.png)

Karolinska: Regions are labelled. Valid values are:
0: background (non tissue) or unknown
1: benign tissue (stroma and epithelium combined)
2: cancerous tissue (stroma and epithelium combined)

(./images/Karolinska.png)

The train script is based on reference script from torchvision 0.4.0 with minor modification. So, you need to install the latest PyTorch and torchvision >= 0.4.0. Check [requirements.txt](requirements.txt) for all packages you need.

This repo use [GluonCV-Torch](https://github.com/zhanghang1989/gluoncv-torch), thanks for Hang Zhang's outstanding work!

## Preprocessing
Each image is annotated in detail by several expert pathologists. So how to use this annotations is important. We use STAPLE to create final annotations used in training. Check the [preprocessing.py](preprocessing.py) script for detail.

![preprocessing](./images/preprocessing.png)

## Training

![PSPNet](./images/PSPNet.png)

To run the training, simply run `python train.py`, check `python train_gleason.py --help` for available args.

## Inference
To run the inference, simply run `python inference.py`, check `python inference.py --help` for available args.

## Note
I don't quite understand task2, and got it wrong when I participated this challenge. I would sincerely advise you read [this paper](https://ieeexplore.ieee.org/abstract/document/8853320/), which is written by the organizers and submitted to JBHI, for more detail about this challenge. I would not update any codes in this repository anymore. 
