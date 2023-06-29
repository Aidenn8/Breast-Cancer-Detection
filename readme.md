# Breast Cancer Detection

 Add short description of project here >
 
 This project determines if there is breast cancer based off an ultrasound.
 
[Imgur](https://i.imgur.com/wW2hFsV.jpg)

## The Algorithm

Add an explanation of the algorithm and how it works. Make sure to include details about how the code works, what it depends on, and any other relevant info. Add images or other descriptions for your project here. 

This project uses a resnet18 model that was retrained with two different sets of data. One dataset contained images of ultrasounds that were confirmed to contain malignant breast cancer. Another dataset was consisted of ultrasounds that did not show any evidence of breast cancer. Once the model was retrained, I exported it using the ONNX format. The program uses imagenet.py to determine the whether or not breast cancer is present in an ultrasound. 

The dataset can be found https://www.kaggle.com/datasets/aryashah2k/breast-ultrasound-images-dataset  

## Running this project

1. Add steps for running this project.

   Setup
   
   Download the jetson-inference container from github to a jetson-nano: https://github.com/dusty-nv/jetson-inference
   

   Training
   

   Exporting
   Output
   
   
3. Make sure to include any required libraries that need to be installed for your project to run.

[View a video explanation here](video link)
