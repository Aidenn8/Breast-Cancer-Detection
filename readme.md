# Breast Cancer Detection
 
 This project determines if there is breast cancer based off an ultrasound.


![image](https://github.com/Aidenn8/Breast-Cancer-Detection/assets/138057733/ec1322f2-0e7d-4590-926c-bc86db0215ea)
![image](https://github.com/Aidenn8/Breast-Cancer-Detection/assets/138057733/9dab020a-77ff-4b2c-9811-920e98fb49ba)

## Algorithm

This project uses a resnet18 model that was retrained with two different sets of data. One dataset contained images of ultrasounds that were confirmed to contain malignant breast cancer. Another dataset was consisted of ultrasounds that did not show any evidence of breast cancer. Once the model was retrained, I exported it using the ONNX format. The program uses imagenet.py to determine the whether or not breast cancer is present in an ultrasound. 

The dataset can be found here: https://www.kaggle.com/datasets/aryashah2k/breast-ultrasound-images-dataset  




## Running this project


   Setup
   
   1) Download the jetson-inference container from github to a jetson-nano: https://github.com/dusty-nv/jetson-inference
   3) Change directories into `jetson-inference/python/training/classification/data`
   4) Create a directory called "breast_cancer_detection"
   5) Run this command in the terminal to download the data
      
      `wget https://www.kaggle.com/datasets/aryashah2k/breast-ultrasound-images-dataset/download?datasetVersionNumber=1 -O ultrasounds.tar.gz`
      
   6) Make 3 directories called "train, "test", and "val" in the "breast_cancer_detection" directory
   7) Make a .txt file called "labels.txt" in the "breast_cancer_detection" directory and write down the following (in exactly that order)
      
      breast_cancer
      no_breast_cancer

   8) Make 2 more directories called "breast_cancer" and "no_breast_cancer" in each directory: "train", "val", and "test"
   9) Move around 5% of the images from the "normal" folder inside of the downloaded "ultrasounds" folder to the jetson-nano to the directory `jetson-inference/python/training/classification/data/breast_cancer_detection/test/no_breast_cancer`
   10) Move around 5% of the images from the "malignant" folder inside of the downloaded "ultrasounds" folder to the jetson-nano to the directory `jetson-inference/python/training/classification/data/breast_cancer_detection/test/breast_cancer`
   11) Move around 15%-25% of the images from the "normal" folder inside of the downloaded "ultrasounds" folder to the jetson-nano to the directory `jetson-inference/python/training/classification/data/breast_cancer_detection/val/no_breast_cancer`
   12) Move around 15%-25% of the images from the "malignant" folder inside of the downloaded "ultrasounds" folder to the jetson-nano to the directory `jetson-inference/python/training/classification/data/breast_cancer_detection/val/breast_cancer`
   13) Put the remaining images from the "normal" folder to the directory
       `jetson-inference/python/training/classification/data/breast_cancer_detection/train/no_breast_cancer`
   14) Put the remaining images from the "malignant" folder to the directory
       `jetson-inference/python/training/classification/data/breast_cancer_detection/train/breast_cancer`
   15) Make a new directory called "breast_cancer_detection" in `jetson-inference/python/training/classification/models`




   Execution

   1) Change directories to jetson-inference
   2) Type and run `./docker/run.sh` in the terminal
   3) Then change directories to `jetson-inference/python/training/classification`
   4) Now train the model by running this command in the terminal
      `python3 train.py --model-dir=models/breast_cancer_detection data/breast_cancer_detection --epochs=150`

      Note: This will take approximately 2 hours and 30 minutes
      
   5) Once done, export the model by running this script

      `python3 onnx_export.py --model-dir=models/breast_cancer_detection`

   7) If you are in the docker container, exit it by pressing ctrl d
   8) Change directories to `jetson-inference/python/training/classification`
   9) In the terminal enter in
      `NET=models/breast_cancer_detection` and
      `DATASET=data/breast_cancer_detection`
   9) Then enter in
       
`imagenet.py --model=$NET/resnet18.onnx --input_blob=input_0 --output_blob=output_0 --labels=$DATASET/labels.txt $DATASET/test/breast_cancer/malignant8.png output.jpg`
       
   10) If you look in your classification directory there will be a file called output.jpg (or whatever you named the output to be)
   11) Display the file to see if there is breast cancer




      
   Note:  
   
   In step 4 you can replace "malignant8.png" with any file in the breast_cancer directory and you can rename "output.jpg" to anything you want.
      
   You can also try using ultrasounds that have no breast cancer by changing "breast_cancer" in step 4 to "no_breast_cancer" and replacing      
   "malignant8.png" with any file in the "no_breast_cancer" directory.

   If you like, you can also upload images of ultrasounds found online to the "breast_cancer" or "no_breast_cancer" directories and try running step 4 
   with your own image instead of "malignant8.png" to check if there is breast cancer.
         

    
   
[View a video explanation here](https://www.youtube.com/watch?v=Vtg-Jqz722k)
