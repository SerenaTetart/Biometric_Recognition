# Biometric_Recognition

## Table of contents
* [General info](#general-info)
* [Requirements](#requirements)
* [Project 1: Fingerprint recognition](#project-1---fingerprint-recognition-siamese-network)
* [Project 1b: Fingerprint recognition (triplet loss)](#project-1b---fingerprint-recognition-siamese-network-using-triplet-loss)
* [Project 2: Fingerprint autoencoder](#Project-2---Fingerprint-autoencoder)

## General info
These are some little projects to learn how to identify people based on their biometrics using CNN, pre-trained models, triplet-loss etc...

## Requirements

The basic libraries for machine learning and computer vision 😃

Libraries:
* OpenCV (python)
* Numpy
* Tensorflow
* Keras

## Project 1 - Fingerprint recognition (Siamese network)

The dataset used is Sokoto Coventry Fingerprint Dataset (SOCOFing) from Kaggle: https://www.kaggle.com/ruizgara/socofing/home

The network is designed to have 2 inputs and substract embeddings from both to classify if the inputs are from the same person or not.

The network is made from scratch and thus very slow to train, I achieved 87% accuracy (~13% error), if I want to improve it I will use Resnet50 or VGG19, look the project 1b for better results.

The model architecture is the following:

<p align="center">
<img src="https://user-images.githubusercontent.com/65224852/136270793-0e8de9a3-8857-43b0-afaf-8c48ffd4098e.png">
</p>

## Project 1b - Fingerprint recognition (Siamese network using triplet loss)

This time we will use VGG19 as the base model and triplet-loss instead of a binary sigmoid activation to classify if a person belong to a database.

Triplet-loss consist of retrieving batch of triplets such as one image serves as the anchor, one as the positive (same class or person) and one negative (different person), we then compute the distance between the anchor and the positive then the distance between the anchor and the negative image.
The goal is to make the positive image closer to the anchor than the negative image.

<p align="center">
  <img src="https://user-images.githubusercontent.com/65224852/136042396-60948058-9c76-409d-8271-8ecb578a6381.png"/>
  <br><a href="https://www.cv-foundation.org/openaccess/content_cvpr_2015/papers/Schroff_FaceNet_A_Unified_2015_CVPR_paper.pdf">(From 2015 Facenet paper)</a>
</p>

The formula to compute the loss is:

<p align="center">
<img src="https://user-images.githubusercontent.com/65224852/136113757-b30d3451-6482-472a-973e-1a269a09f5f7.PNG">
</p>

Where:
* x is the training set, xa the anchor image, xp the positive, xn the negative
* α is a constant ranging from 0.2 to 1.0
* f(xi) is the embedding of the i-th image from the training set.

Hopefully tensorflow has already an implementation of triplet-loss with tfa.losses.TripletSemiHardLoss() which compute everything written before with one line of code.

And we have ~82% Accuracy with only a few epochs.

## Project 2 - Fingerprint autoencoder

This second project aims to **repair** damaged fingerprint by using the U-Net autoencoder.

We can use this idea to improve handwriting or image resolution, or even use this as part of a pipeline to identify a person based on biometrics.

Below you can see the U-Net architecture:
<p align="center">
  <img src="https://user-images.githubusercontent.com/65224852/136661667-c1bf2334-38ec-4737-9442-bfde615e1d3a.png"/>
  <br><a href="https://arxiv.org/pdf/1505.04597v1.pdf">(From 2015 U-Net paper)</a>
</p>

The loss is just a mean-squared error pixel by pixel:
<p align="center">
  <img src="https://user-images.githubusercontent.com/65224852/136663429-6cb4de0a-9b02-4789-99d0-c35da05550c5.png"/>
</p>

Where:
* x is the training set, xa the altered image, xb the real (clean) image
* f(xi) is the pixel's value of the i-th image from the batch

And some of my results:
<p align="center">
  <img src="https://user-images.githubusercontent.com/65224852/143256198-d422b94a-2cca-4e17-ae75-881903c7778f.png"/>
  <img src="https://user-images.githubusercontent.com/65224852/136662043-c614470d-2d6f-4e19-9ee8-e8b05c83b092.png"/>
</p>
