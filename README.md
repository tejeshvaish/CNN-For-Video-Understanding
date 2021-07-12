#  Convolutional Neural Network for Video Understanding
## SnT Project 2021, Brain Cognitive Society

This repository contains the code for this project done so far.

### Relevant Links

- [Midterm Evaluation presentation](https://docs.google.com/presentation/d/1mcNrgg31MDGAspPVvKMbi0IHepgr3-vRvQAGZNgbrmE/edit?usp=sharing)
- [Midterm Documentation](https://docs.google.com/document/d/1ms3ODc83bDkgF-Gggv8UQRUD-J4djhEAuWdEN9mAAkM/edit?usp=sharing)


This is the repository which implements late temporal modeling on top of the 3D CNN architectures and mainly focus on BERT for this aim.

## Environment 
- python 3.6.4
- tensorflow 1.x
- keras>=2.0.0
- pytest>=3.0.3
- pytest-cov>=2.4.0
- pytest-xdist>=1.15.0
- basically a normal colab environment 

## DataSet
The Biggest Hurdle we faced while implementing the paper or any 2D/3D CNN for that matter was the video dataset , It was extremenly difficult to parse the dataset and load it into different different frames which would them be sent into our model, where then the last TGAP layer of the model then use to average the score of each of the frame to get the Actual classification of the model. 

So, Finally I Used many methods to accomplish this task, one of them was to convert the video into many frames which are then normalized and then transformed into a numpy array which can be given as input to our model to get the result.  

* For the first implementation I used UCF101 dataset and trained the model on just 10% of it(due to lack of GPUs , RAM and time).

* For the second implementaton I again used HMDB51 dataset and then extracted it, and then passed it batch fram wise through a CNN+LSTM model we got 67% accuracy by trainin it on just 1/5 of one of the three split of HMDB51 dataset. 

* For third implementation I used glucon and mxnet library which has prewritten script to download and extract hmdb51 dataset and then used it on 3D resNeXt model.


# Model Architecture and Details
I implemented many models including  VGG(pretrained) with 4 FC layers on top of it with one Classification layer , CNN with LSTM, and Finally 3DReseXt101. 


## 1.VGG16 + 4 FC layers
![image](https://user-images.githubusercontent.com/55567070/125229053-8fa7c800-e2f3-11eb-8a27-43c9fa290a24.png)

-[Inspired from](https://github.com/chen0040/keras-video-classifier)
The First Model utilizes the VGG16 architecture to extract the spatial and temporal features out of the frames of the video and Then several softmax, Relu layer
This model is basically a simple 2D CNN architecture which is trained on frames of the video and then use to classify them and taking the average over all the frames of the video. -[ref2](https://towardsdatascience.com/transfer-learning-with-vgg16-and-keras-50ea161580b4)

Result : By this Method , we were getting 27% accuracy on UCF101 dataset(because I was just able to use 10% of train data to train my model), while the official implementation was giving 44% accuracy, we Implemented this , as this was the first thing which would come to someones mind, if one has to do Action Recognition. 


## 2.CNN + LSTM
-[Inspired from here](https://github.com/HHTseng/video-classification)

- This was the second model that I Implemented in my learning process to classify video: 
This model basically had CNN + LSTM , conv to explicitely exploit spatial features while LSTM efficiently utilises temporal features. 

In CNN-LSTM we have two different modules which are combined together. The CNN is a regular CNN which acts as a 'spatial feature extractor'. The output of the CNN is multiplied by the LSTM cell to learn the 'temporal features'.
We implemented this, as it was the foundation for the future work for Action recognition task, because in our 3rd implementation we were using *BERT* which is a much better version of LSTM to do the job with 3D CNN. 


![image](https://user-images.githubusercontent.com/55567070/125219543-8cf0a700-e2e2-11eb-8eb7-ae8113f9cfd5.png)

## 3.Late Temporal Modeling in 3D CNN Architecture with BERT for Action Recognition - [here](https://arxiv.org/pdf/2008.01232.pdf) 

In this paper we had to implement 3D CNN architecture with its TGAP layer replaced with BERT so as to classify the video.  
![image](https://user-images.githubusercontent.com/55567070/125230362-41e08f00-e2f6-11eb-8ec4-62c7fed26389.png)
this Implementation was extremely difficult for us due to the use of 3D CNN , we are able to reach till the model architecture implementation of the ResneXt 3D CNN.

But, it was very difficult to pass the Video data through the 3D CNN architecture, and we are currently stucked at this point. 



## Usage 
All the ipynb files of the task that we did are in their respective folder 

To Run any script just open it in colab and install the necessary packages which are already mentioned there. 
- It will take  2 hrs to train first model on 10% of the ucf101 dataset.( time is less cause we imported the VGG16 pretrained on imagenet dataset)
- 24 hrs to run the second model on HMDB51 dataset. 
- Still in progress, we have implemented resneXt101 architecture till now, and are going to train it on UCF101 dataset, this part is complex due to the fact that we are using 3D CNNs

## Individual Contribution: 

| Weeks | 1-2 | 3-4 | 5-6 | 7-8 | 
| ------------- | ------------- |------------- |------------- |------------- |
| Tejesh  | Did the Prework part , completed various exercises of ML crash course while doing probability side wise | In week 3-4 I completed Kaggle and image classification crash course and tried my hands on tensorflow and pytorch and started working on paper review of the Paper  | completed paper review , PPt, Documentation of the paper and I was the speaker for my team  , now in these two week I daily spend 3-4 hrs religiously doing the work , Then firstly I implemented simple VGG16 model, and trained it on UCF101 dataset, also implemented tensorhub i3d model to classify video into action(easy task)  | In the second last weeks of the project I focused on CNN + LSTM  and implemented its architecture, I took its insipiration from a github repo which made use of CNN with LSTM to give good results on AR task this took complete one week and then started with the last task of implementing 3D ResneXt101 with BERT , but currently I am stucked at the task of passing video through its complex architecture , I will try my best to make working model with it |
| Saloni  | Content Cell  |Content Cell  |Content Cell  |Content Cell  |
| Nikita  | Content Cell  |Content Cell  |Content Cell  |Content Cell  |


