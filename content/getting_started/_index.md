+++
title = "Getting Started"
weight=10 
+++

This sections explains how to get an instance of `Happy Day` up and running in only a few steps.
To train one/all of the CNNs take a look into the documentation. 

# happy-day-service
With `make all` the scripts also starts an instance of the created docker container. 
It listens on port `80`, so keep in mind that you need the rights to listen on this port. 
Otherwise change the port in the `Makefile`.

```
# clones happy-day-service repository
git clone git@github.com:ofesseler/happy-day-service.git

# builds new containers from scratch
make all 
```

## Requirements
- Python 3.x
- Tensorflow 1.4
- Keras 2.x
- pip
- docker (optional) 

For further requirements take a look into [`requirements.txt`](https://github.com/ofesseler/happy-day-service/blob/master/requirements.txt)


# happy-day-app
The app serves as a client and can be used to generate test data as wel
l as to test emoji detection. The classification of the data does not take 
place directly in the app but in the backend.

The tasks of the app are:

- The recording of faces and their preprocessing (cropping).
- Send images with manually selected label to the backend.
- Display the results of a classification

## How to get started with the app?
The easiest way to get the Android app: check it out with your Android `>= 5.0` cell phone at: [Happy Day App at Google Play](https://play.google.com/store/apps/details?id=de.data_mining.hs_esslingen.happyday)

Or start your Android Studio and build it by yourself. 
Actually, if you want to connect happy-day-app to your own HTTP-endpoint you have to edit the source and build it by your own. 

## How to use the app?
In the first step, the user has to add a camera to the app. 
Afterwards a selfie can be created directly and you will be redirected to the next view.

Via the middle button (Tensorflow button), the image is sent to the backend, classified by it and the result is displayed in the upper left corner of the app.
Here, a probability is shown for each facial expressions (Smile, Neutral, Sad).
The processing can take a few seconds, but the user is not advised.
The images classified in this way are not saved on the server!
The button on the right can be used to manually label the image and then send it to the server.
Here, the labeled image is stored on the server and can be used to improve the emoji detection.


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

