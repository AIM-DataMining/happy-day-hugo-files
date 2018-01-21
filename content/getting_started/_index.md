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
The easiest way to get the Android app: check it out with your Android `>= 5.0` cell phone at: https://play.google.com/store/apps/details?id=de.data_mining.hs_esslingen.happyday

Or start your Android Studio and build it by yourself. 
Actually, if you want to connect happy-day-app to your own HTTP-endpoint you have to edit the source and build it by your own. 

# happy-day-live
Allows live evaluation on the PC via webcam.
The application can be used to train different networks
and evaluate the result directly with a webcam.

## Requirements
Anaconda in the 32 bit version is used as runtime environment.

There are dependencies to the following modules that must be installed before use:

* numpy 1.13.3
* opencv 3.3.1
* tensorflow 1.4.0
* h5py 2.7.1
* Pillow 4.3.0

Training the data: `train <filename> <CNN to use values between 1-3>`

Example:
```
python Test train myModel 3
python Test train mySecondModel 2
```
  
Test the trained model: `testloop <filename> <CNN to use values between 1-3>`

Example:
```
python Test testloop myModel 3
python Test testloop mySecondModel 2
```

