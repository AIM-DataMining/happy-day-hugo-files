+++
title = "Live evaluation"
weight=10 
+++

# happy-day-live

Allows live evaluation on the PC via webcam. 
The application can be used to train different networks and evaluate the result directly with a webcam.
The live evaluation can be found in the github repository [happyday-day-live](https://github.com/AIM-DataMining/happy-day-live).
The evironment of the live evaluation is based on [Emotion Recognition using DNN](https://github.com/isseu/emotion-recognition-neural-networks) project. 

## Requirements
Anaconda in the 32 bit version is used as runtime environment.

There are dependencies to the following modules that must be installed before use:

* numpy 1.13.3
* opencv 3.3.1
* tensorflow 1.4.0
* h5py 2.7.1
* Pillow 4.3.0

## Available models
In the live evaluation you can choose between 3 different networks:

1. Self CNN: A adapted model with an moderate complexity based on the [literature](https://arxiv.org/pdf/1512.00743.pdf).
2. Fast CNN: A model with an reduced complexity for an fast learning process based on the SelfCNN.
3. Optimized CNN: A model with an high complexity. Takes a long time for training due to a lot of optimations.

## How to train a model?
In main directory of the repository the folder "data" and the subfolders "train" and "test" must be created.
The folder "train" should include all images which are used for training the network.
The folder "test" should include all images which are used for validation.
Suitable images can be downloaded from the [Kaggel Facial Expression Recognition Challenge](https://www.kaggle.com/c/challenges-in-representation-learning-facial-expression-recognition-challenge/data). 
The images used should only contain the face of the person and not its body.
After that the data can be used for training.

Training the data: 
```
train <filename> <CNN to use values between the 3 models 1-3>
```

Example:
```
python Test train myModel 3
python Test train mySecondModel 2
```

## How to test a model?
The trained models can be testet by using the name of the model and the id of the used network.
For test purpose one trained model with the name `optimizedModel` based on the Optimized CNN is added for direct testing.

Test the trained model: 
```
testloop <filename> <CNN to use values between the 3 models 1-3>
```

Example:
```
python Test testloop optimizedModel 3
python Test testloop mySecondModel 2
```

