# Continual Learning Project

## Overview
The main resource included is an ipython notebook. The notebook includes code to download and manipulate the Core50 dataset for the purposes of Continual Learning. The dataset is comprised of 50 different classes of images and 11 different sessions. The sessions are differentiated by background and object orientation. The main reference for this workbook is published CVPR 2020 Challenge paper (link: https://arxiv.org/pdf/2009.09929.pdf) which covers the various winning strategies on this benchmark.

The approaches below include: Transfer Learning with Resnet and Continual Learning using replay. The framework used was Pytorch.

## Core50 Data
The dataset is pulled via a wget method. The original organization of the data has been altered for the purposes of this notebook. Originally it was comprised of txt files and image folders along with a good deal of infrastructure intended for the competition. This notebook adjusts the folders to take advantage of ImageFolder found in the torchvision library. 

**Preprocessing:** The image files were split into training and validaiton sets - roughly an 80 / 20 split. The images were normalized and center-cropped.


## Main Code Blocks

**Transfer Learning:** This section handles the Resnet initialization. The last layer is altered to handle the 50 classes of images.

**Training:** The model is fine tuned and follows a similar approach to the example code provided by pytorch (link: https://pytorch.org/tutorials/beginner/finetuning_torchvision_models_tutorial.html). The learning rate is adjusted as the training progress.

**Evaluation:** The models are compared to the preceeding session to see the effects of catastrophic forgetting. There appeared to be around a 10% decrease after training the new session.

**Continual Learining - Replay:** The approach I used to handle the forgetting was replay or rehearsal. Again, this is between session to session where the backgrounds might be slightly different causing the model to fail. The forgetting is mitigated by concatenating a sampling of previously seen data to preserve some of the parameters that are important for the prior task. Other methodologies attack the problem through regularization. 



## Requirements
The notebook was intended to be used in a Colab environment with a GPU. Code is provided to download Conda and the relevant dependencies.
