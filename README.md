# Biometric_Recognition

## Table of contents
* [General info](#general-info)
* [Requirements](#requirements)
* [Project 1: Fingerprint recognition](#Project-1---Fingerprint-recognition)
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

## Project 2 - Fingerprint autoencoder

This second project aim to **repair** damaged fingerprint by using an autoencoder also made from scratch.

We can use this idea to improve handwritting for instance.
