# **Trafic Sign Classification Project** 

## Writeup

---

**Build a Traffic Sign Recognition Project**

The goals / steps of this project are the following:
* Load the data set (see below for links to the project data set)
* Explore, summarize and visualize the data set
* Design, train and test a model architecture
* Use the model to make predictions on new images
* Analyze the softmax probabilities of the new images
* Summarize the results with a written report


[//]: # (Image References)

[image1]: ./examples/index.png "Visualization"
[image2]: ./examples/index1.png "Grayscaling"
[image3]: ./examples/index3.png "Random Noise"


### Data Set Summary & Exploration

#### 1. Provide a basic summary of the data set. In the code, the analysis should be done using python, numpy and/or pandas methods rather than hardcoding results manually.

I used the numpy library to calculate summary statistics of the traffic
signs data set:

* The size of training set is 34799
* The size of test set is 12630
* The shape of a traffic sign image is (32, 32, 3)
* The number of unique classes/labels in the data set is 43


#### 2. Include an exploratory visualization of the dataset.

Here is an exploratory visualization of the data set. It is a bar chart showing how the data ...

![alt text][image1]

And the distribution of the classes in the training set

![alt text][image2]

### Design and Test a Model Architecture

First I normalized all the data by dividing it by 255. Then I constructed LeNet model :


| Layer         		|     Description	        					       | 
|:---------------------:|:---------------------------------------------:       | 
| Input         		| 32x32x3 RGB image   							       | 
| Convolution 5x5     	| 6 filters, 1x1 stride, same padding, output 28x28x6  |
| RELU					|												       |
| Max pooling 2x2	  	| 2x2 stride, output 15x14x6				           |
| Convolution 5x5     	| 16 filters, 1x1 stride, same padding, output 10x10x16|
| RELU					|												       |
| Max pooling 2x2    	| 2x2 stride,  outputs 5x5x16 				           |
| Fully connected     	| 120 neurones 	                                       |
| RELU					|												       |
| Fully connected    	| 84 neurones				                           |
| RELU					|												       |
| Fully connected		| 10 neurones										   |

To train the model I used 50 epochs with mini batches of size 128 and a learning rate of 0.001. As for the lost function I used the cross entropy and for the optimization I chosed Adam Optmizer. The final results are :
* The accuracy of the training set : 1
* The accuracy of the validation set : 0.931
* The accuracy of the test set : 0.916

### Test a Model on New Images

Here are five German traffic signs that I found on the web:

![alt text][image3]

Here are the results of the prediction:

| Image			        |     Prediction	        					| 
|:---------------------:|:---------------------------------------------:| 
| Pedestrians      		| Pedestrians   								| 
| Speed limit (60km/h)  | Speed limit (50km/h) 				            |
| Stop					| Stop											|
| No entry      		| No entry			 				            |
| Yield			        | Yield    						             	|


The model was able to correctly guess 4 of the 5 traffic signs, which gives an accuracy of 80%.

The code for making predictions on my final model is located in the 16th cell of the Ipython notebook.
When we look at the top 5 probabilitise of the 5 images, we see that the biggest probability is close to 1. The model is very sure of its predictions except for the second image, it hesitated between 50km/h and 80km/h.

