# DLProject

## Team Members: Apoorv Khattar, Madhav Thakker, Madhur Tandon

## Motivation
Visual question answering is a task proposed to connect Computer Vision and Natural Language Processing (NLP). Computer vision is concerned with methods that teach computers to perceive images same as how humans do. On the other hand, NLP deals with interactions of computers with natural languages same as how humans do. Many significant developments in both these fields have happened separately but VQA requires simultaneous understanding of the visual content of images and the textual content of questions. There has been a huge interest to explore techniques that can fuse multimodal information, in this case the features of an image with the textual features of a question. In our project, we focus on some of the recent fusion techniques that have been proposed for bilinear models. Bilinear models consist of two networks: one for extracting visual features from an image and the other for extracting textual features from a question, which are then fused to generate an answer for a question.

## Data preprocessing
We use the publicly available VQAv2 Dataset. The dataset consists of around 200,000 images from the MS-COCO dataset with at least 3 questions per image. Each one of these questions is then answered by 10 annotators, yielding a list of 10 ground truth answers. Due to the large size of the dataset, we take 5000 samples from the training set containing questions with yes/no answers, 800 samples as validation set and 200 samples as test samples. We chose only yes/no questions since they had the most number of samples and all the papers report their accuracy, allowing us to compare the results of our model with those mentioned in the paper. .For data preprocessing, we refer to the code provided by [https://github.com/Shivanshu-Gupta/Visual-Question-Answering](https://github.com/Shivanshu-Gupta/Visual-Question-Answering) and make appropriate changes to get only yes/no questions.

During the training phase, each image is resized to (256,256) and a random patch of size (224,224) is passed through the network. The training set and validation set are used to determine the vocabulary and tokenize each question.

## About the project
Given an image and a question, we use two models to extract the image and question feature vector, **v** and **q** respectively. Now we need to fuse **q** and **v** to predict the final answer. In our project we focus on the following fusion techniques:

1. MLB: Kim et al. \cite{kim2016hadamard} explore simple techniques for fusion such as element-wise sum, concatenation, hadamard product etc. They show empirically that hadamard product between **q** and **v** produces the best results. For the image vector **v** and question vector **q**, the fused feature vector, **f** is given by:

  ![eq](https://latex.codecogs.com/svg.latex?y_i%20=%20(q^T%20W_q)_i%20*%20(v^T%20W_v)_i,)
  
where ![eq](https://latex.codecogs.com/svg.latex?W_q) and ![eq](https://latex.codecogs.com/svg.latex?W_q) are weight matrices that transform **q** and **v** to have the same dimensions.


###### This work was done as part of our project for CSE641: Deep Learning course at IIIT Delhi.
