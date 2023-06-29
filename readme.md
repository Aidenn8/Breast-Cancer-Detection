# Breast Cancer Detection
 
 This project determines if there is breast cancer based off an ultrasound.
 
![image](https://github.com/Aidenn8/Breast-Cancer-Detection/assets/138057733/9dab020a-77ff-4b2c-9811-920e98fb49ba)

## Algorithm

This project uses a resnet18 model that was retrained with two different sets of data. One dataset contained images of ultrasounds that were confirmed to contain malignant breast cancer. Another dataset was consisted of ultrasounds that did not show any evidence of breast cancer. Once the model was retrained, I exported it using the ONNX format. The program uses imagenet.py to determine the whether or not breast cancer is present in an ultrasound. 

The dataset can be found here: https://www.kaggle.com/datasets/aryashah2k/breast-ultrasound-images-dataset  

![image](https://github.com/Aidenn8/Breast-Cancer-Detection/assets/138057733/1c9b8135-0c58-45ba-ba63-2ee68f04e005)


## Running this project


   Setup
   
   1) Download the jetson-inference container from github to a jetson-nano: https://github.com/dusty-nv/jetson-inference
   2) Download the files listed on this github page
   5) Transfer the files downloaded to the jetson-nano to the directory jetson-inference/python/training/classification/ by using an app such as FileZilla
 




   Execution

   1) If you are in the docker container, exit it by pressing ctrl d
   2) Change directories to jetson-inference/python/training/classification
   3) In the terminal enter in
      NET=models/breast_cancer_detection 
      DATASET=data/breast_cancer_detection
   4) Then enter in
      imagenet.py --model=$NET/resnet18.onnx --input_blob=input_0 --output_blob=output_0 --labels=$DATASET/labels.txt $DATASET/test/breast_cancer/malignant8.png    
      output.jpg
   5) If you look in your classification directory there will be a file called output.jpg
   6) Display the file to see if there is breast cancer




      
   Note:  
   
   In step 4 you can replace "malignant8.png" with any file in the breast_cancer directory and you can rename "output.jpg" to anything you want.
      
   You can also try using ultrasounds that have no breast cancer by changing "breast_cancer" in step 4 to "no_breast_cancer" and replacing      
   "malignant8.png" with any file in the "no_breast_cancer" directory.

    If you like, you can also upload images of ultrasounds found online to the "breast_cancer" or "no_breast_cancer" directories and try running step 4 
    with your own image instead of "malignant8.png" to check if there is breast cancer.
         

    
   
3. Make sure to include any required libraries that need to be installed for your project to run.

[View a video explanation here](video link)
