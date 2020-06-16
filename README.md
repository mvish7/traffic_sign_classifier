# traffic_sign_classifier

This project contains the tensorflow based neural network for classification of Traffic signs in [German Traffic Sign dataset](http://benchmark.ini.rub.de/?section=gtsrb&subsection=dataset)

# Dependencies

* Python 3.x
* Matplotlib
* Sklearn
* Tensorflow 1.x

# Steps:

## Loading the Dataset:

The pickle files of dataset were hosted on the google drive and then drive was mounted on the colab notebook.

## Exploring the Dataset:

With the help of Python and Numpy commands the dataset was explored. The summary of exploration is as follows

* Number of images in training set is 34799
* Number of images in validation set is 4410
* Number of images in test set is 12630
* The shape of a traffic sign image is (32, 32, 3)
* The number of unique classes/labels in the data set is 43

## Data Preprocessing:

Currently only normalization and gray scale conversion techniques are being applied. 

## Network architecture design:

A slightly modified version of LeNet was used, details of the network and training can be found below.

| Layer         		|     Description	        					| 
|:---------------------:|:---------------------------------------------:| 
| Input         		| 32x32x1 grayscaled, normalized image   							| 
| Convolution 5x5     	| 1x1 stride, valid padding, outputs 28x28x6 	|
| RELU					|												|
| Max pooling	      	| 2x2 stride,  outputs 14x14x6 				|
| Convolution 5x5     	| 1x1 stride, valid padding, outputs 10x10x16 	|
| RELU					|												|
| Max pooling	      	| 2x2 stride,  outputs 5x5x16 				|
| Flatten					|					5x5x16 -> 400							|
| Dropout     | keep_prob = 0.8    |
| Fully connected    | 400 -> 120 |
| RELU					|												|
| Dropout     | keep_prob = 0.75    |
| Fully connected    | 120 -> 84 |
| RELU					|												|
| Fully connected    | 84 -> 43 |

To train the model, I used Adam optimizer. The final settings utilized for training are given below:

| Parameter        		|     Value        					| 
|:---------------------:|:-------------------------------------:| 
| Batch size         		| 128   							| 
| Epochs     	| 50 	|
| Learning rate					|		0.001										|
| Mean, mu	      	| 0 				|
| Variance, sigma     	| 0.1 	|
| Dropout keep probability | 0.80 (layer 1), 0.70 (layer 2)|

## Results:

My final results include,

* Training accuracy of 98%
* Validation accuracy of 94%

Initial results showed lot of overfitting as validation accuracy was stagnant @ 87%, fine tuning of dropout layers boosted the validation accuracy.
Below are the graphs of Training/Validation accuracy/losses vs Epochs.

![alt text](https://github.com/mvish7/traffic_sign_classifier/tree/master/images/graphs.PNG?raw=true)

## Improvements:

* Overfitting can still be reduced
* Synthetic data generation can be performed to balance the samples per class.