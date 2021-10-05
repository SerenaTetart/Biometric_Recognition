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

The network is designed to have 2 inputs and substract embeddings from both inputs to classify if the inputs are from the same person or not.

The network is made from scratch and thus very slow to train, I achieved 87% accuracy (~13% error), if I want to improve it I will use Resnet50 or VGG19.

## Project 1b - Fingerprint recognition (Siamese network using triplet loss)

This time we will use triplets and triplet-loss instead of a sigmoid to classify if a person belong to a database.

Triplet-loss consist of retrieving batch of triplets such as one image serves as the anchor, one as the positive (same class or person) and one negative (different person), we then compute the distance between the anchor and the positive then the distance between the anchor and the negative image.
The goal is to make the positive image closer to the anchor than the negative image.

<p align="center">
  <img src="https://user-images.githubusercontent.com/65224852/136037732-40608fcb-2ab0-42db-adba-eba74076dd3c.png"/>
  <br><a href="https://www.cv-foundation.org/openaccess/content_cvpr_2015/papers/Schroff_FaceNet_A_Unified_2015_CVPR_paper.pdf">(From 2015 Facenet paper)</a>
</p>

The formula to compute the loss is: 
<img src="https://render.githubusercontent.com/render/math?math=%5Cdisplaystyle+%5Csum_%7Bi%7D%5E%7BN%7D%5B+%5Cleft%5C%7C+f%28x_%7Bi%7D%5E%7Ba%7D%29+-+f%28x_%7Bi%7D%5E%7Bp%7D%29+%5Cright%5C%7C_%7B2%7D%5E%7B2%7D+-+%5Cleft%5C%7C+f%28x_%7Bi%7D%5E%7Ba%7D%29+-+f%28x_%7Bi%7D%5E%7Bn%7D%29+%5Cright%5C%7C_%7B2%7D%5E%7B2%7D+%2B+%5Calpha%5D">

Where: 

## Project 2 - Fingerprint autoencoder

This second project aims to **repair** damaged fingerprint by using an autoencoder also made from scratch.

We can use this idea to improve handwriting for instance.
