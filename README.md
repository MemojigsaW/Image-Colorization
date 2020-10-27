## Overview 
The task is to implement a black-n-white photo colorization techinique with machine learning. The baseline model is an Autoencoder and is improved with discriminator assessed losses. Essentailly a GAN with an autoencoder generator. 

## Set up
All models are in image colorization.ipynb. The demo file is for testing the finalized model on random images by inputing the url. The test folder and train weight folder are there due to the set up in google drive, if downloaded, one can adjust the pathing in the dataset creation section. 

## Data
The data used is the [flower data set from kaggle](https://www.kaggle.com/olgabelitskaya/flower-color-images). To replicate the training, download the data set and create a training folder with gray photos and colored photos in different folder then adjust the pathing in the code. The input are also resized to 128x128. 
<br/>

<p align="center">
  Example of training/validation data 
  <br/>
  <img src = /Images/processed_gray.png>
  <img src = /Images/processed_original.png>
</p>


## Model
The base line model is a 5-layer autoencoder, serveral adjustments were made e.g., increasing layer, adjusting downsampling rate, replacing avg/max pooling with conv2d. The file contains various model used for hyperparameter tunings. The finalized generator downsamples with convolution, RELU and uses a DenseNET style skiip connection. The passings are batch normalized. The embedding dimenison is 16x16x512. The discriminator is a standard CNN downsamples with average pooling and batch normalization. BCE for output error. 

<p align="center">
  <img src = /Images/Final_Model.png>
 </p>

## Training 
The loss is evaluated as weighted combination of the BCE and L1 with the original image. The generators and discriminators have differe LR with intermitant noise feed to prevent mode collapse. Limited by the model and time for tuning. The discrinminator ultimately overpowers the generator at higher epochs. Additional tuning and adjustment to the architecture should be expected in the future. 

<p align="center">
  <img src=/Images/Training_curce.png>
  <img src=/Images/Training_Accuracy.png>
  </p>



## Performance

## Conclusion
