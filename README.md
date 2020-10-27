## Overview 
The task is to implement a black-n-white photo colorization techinique with machine learning. The baseline model is an Autoencoder and is improved with discriminator assessed losses. Essentailly a GAN with an autoencoder generator. 

## Set up
All models are in image colorization.ipynb. The demo file is for testing the finalized model on random images by inputing the url. The test folder and train weight folder are there due to the set up in google drive, if downloaded, one can adjust the pathing in the dataset creation section. 

## Data
The data used is the [flower data set from kaggle](https://www.kaggle.com/olgabelitskaya/flower-color-images). To replicate the training, download the data set and create a training folder with gray photos and colored photos in different folder then adjust the pathing in the code. The input are also resized to 128x128. 
<br/>
Example of training/validation data 
<br/>
<p align="center">
![Image of grey][data_gray]
![Image of color][data_color]
</p>
[data_gray]: /Images/processed_gray.png
[data_color]: /Images/processed_original.png
## Model

## Training 

## Performance

## Conclusion
