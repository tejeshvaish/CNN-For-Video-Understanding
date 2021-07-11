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
The Biggest Hurdle I faced while implementing the paper or any 3D CNN for matter was the video dataset , It was extremenly difficult to parese the dataset and load it into different different frames which would them be sent into our model, where then the last TGAP layer of the model then use to average the score of each of the frame to get the Actual classification of the model. 

So, Finally I 


# Model Architecture and Details

I implemented many models including Resnext, Renset, ConvLSTM, VGG(pretrained) , i3D(pretrained) .




## Usage 
Due to Resource Constraint, I was only able to train my model on 900 images target  
