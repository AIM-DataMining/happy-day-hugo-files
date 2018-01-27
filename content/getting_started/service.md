+++
title = "Web Service"
weight=10 
+++

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

If you want to be able to store the images on a webdav endpoint, you have to define the environment variables `DAV_USER` and `DAV_PASSWORD`.
Otherwise you can't store data for retraining and collecting without issues. 

## Requirements
- Python 3.x
- Tensorflow 1.4
- Keras 2.x
- pip
- docker (optional) 

For further requirements take a look into [`requirements.txt`](https://github.com/ofesseler/happy-day-service/blob/master/requirements.txt)

## Training

To train a new model, one can easily download the Dataset from a Kaggle Challenge ["Facial Expression Recognition"](https://www.kaggle.com/c/challenges-in-representation-learning-facial-expression-recognition-challenge/data). The other option is to generate the data yourself and take a **lot** of photos from your friends. We had about 5000 photos of 15-20 Friends and it helped a lot to improve the modell. 

Do the following steps to start training the `self-cnn` model

```
# change into happyday folder
cd happy-day-service/happyday

# preprocess data for scaling, folder structure, ... 
python data_processing.py -s "/source/path" -d "/destination/path"

# train model 
python self_nn.py --path "/destination/path"
```

Then your machine will work a while and eventually show you the results. You can modify the parameters in the `self_cnn.py` file itself.



