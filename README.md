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
  <img src = /Images/Final_model.png>
 </p>

## Training 
The loss is evaluated as weighted combination of the BCE and L1 with the original image. The generators and discriminators have differe LR with intermitant noise feed to prevent mode collapse. Limited by the model and time for tuning. The discrinminator ultimately overpowers the generator at higher epochs. Additional tuning and adjustment to the architecture should be expected in the future. 

<p align="center">
  <img src=/Images/Training_curve.png width="450" height="300">
  <img src=/Images/Training_Accuracy.png width="450" height="300">
  </p>

## Performance

### Baseline Autoencoder
<p align="center">
  <img src=/Images/autoencoder5_1.png>
  <img src=/Images/autoencoder5_2.png>
  <img src=/Images/autoencoder5_3.png>
  <img src=/Images/autoencoder5_4.png>
  </p>
  
### Training
<p align="center">
  <img src=/Images/GAN_train_1.png>
  <img src=/Images/GAN_train_2.png>
  <img src=/Images/GAN_train_3.png>
  <img src=/Images/GAN_train_4.png>

  </p>
### Validating
<p align="center">
  <img src=/Images/GAN_val_1.png>
  <img src=/Images/GAN_val_2.png>

</p>
  
### Testing
<p align="center">
  <img src=/Images/GAN_test_1.png>
  <img src=/Images/GAN_test_2.png>
  <img src=/Images/GAN_test_3.png>
  <br/>
  <img src=/Images/google_test_1.png>
  <img src=/Images/google_test_2.png>
  <img src=/Images/google_test_3.png>
  <img src=/Images/google_test_4.png>
  <img src=/Images/google_test_5.png>
  <img src=/Images/google_test_6.png>
  <img src=/Images/google_test_7.png>
 </p>
  
### Comparison with baseline
<p align="center">
  <img src=/Images/compare_autoencoder5.png>
  <br/>

  <img src=/Images/compare_autoencoder7.png>  
  <br/>

  <img src=/Images/compare_autoencoder7LR.png>  
  <br/>

  <img src=/Images/compare_autoencoder9skip.png>  
  <br/>

  <img src=/Images/compare_GAN9skip.png>  
  <br/>

</p>

## Conclusion
Problem with the autoencoder source from the MSE loss function. The bluriness resulting from autoencoder is improved by the GAN. Limited by the computational power, only a small dataset on flowers is used. The model architecture can be extended for more feature maps and for more generalized colorization tasks Currently, features not recognizable in flower (like the road and concrete) will be ignored by the model. Reason for using the flower dataset is to test how well the model can generalize for a "hard" set.
