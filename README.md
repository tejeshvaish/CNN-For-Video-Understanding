#  Convolutional Network for Video Understanding
## SnT Project 2021, Brain Cognitive Society

This repository contains the code for this project done so far.

### Relevant Links

- [Midterm Evaluation presentation](https://docs.google.com/presentation/d/1mcNrgg31MDGAspPVvKMbi0IHepgr3-vRvQAGZNgbrmE/edit?usp=sharing)
- [Midterm Documentation](https://docs.google.com/document/d/1ms3ODc83bDkgF-Gggv8UQRUD-J4djhEAuWdEN9mAAkM/edit?usp=sharing)


## Paper Info 

Keras implementation of Late Temporal Modeling in 3D CNN Architectures with BERT for Action Recognition. - [here](https://arxiv.org/pdf/2008.01232.pdf) 

This is the repository which implements late temporal modeling on top of the 3D CNN architectures and mainly focus on BERT for this aim.

## Environment 
python 3.6.4

## DataSet
The Biggest Hurdle I faced while implementing the paper or any 2D/3D CNN for that matter was the video dataset , It was extremenly difficult to parse the dataset and load it into different different frames which would them be sent into our model, where then the last TGAP layer of the model then use to average the score of each of the frame to get the Actual classification of the model. 

So, Finally I Used many methods to accomplish this task, one of them was to convert the video into images which are then normalized and then transformed into a numpy array which can be given as input to our model to get the result. 


# Model Architecture and Details

I implemented many models including  VGG(pretrained) with 4 FC layers on top of it with one Classification layer , Renset with convLSTM, and Finally 3DReseXt101. 

The First Model utilizes the VGG16 architecture to extract the spatial and temporal features out of the frames of the video and Then several softmax, Relu layer



### Conv + LSTM
This was the second model that I Implemented in my learning process to classify video:
This model basically had Conv + LSTM , conv to explicitely exploit spatial features while LSTM efficiently utilises temporal features. 

In CNN-LSTM we have two different modules which are combined together. The CNN is a regular CNN which acts as a 'spatial feature extractor'. The output of the CNN is multiplied by the LSTM cell to learn the 'temporal features'.

![image](https://user-images.githubusercontent.com/55567070/125219543-8cf0a700-e2e2-11eb-8eb7-ae8113f9cfd5.png)





## Usage 
Due to Resource Constraint, I was only able to train my VGG model on 900 images train images only  
