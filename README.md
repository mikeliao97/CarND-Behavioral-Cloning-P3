# **Behavioral Cloning** 


**Behavioral Cloning Project**

The goals / steps of this project are the following:
* Use the simulator to collect data of good driving behavior
* Build, a convolution neural network in Keras that predicts steering angles from images
* Train and validate the model with a training and validation set
* Test that the model successfully drives around track one without leaving the road
* Summarize the results with a written report


[//]: # (Image References)

[image1]: ./examples/model_summary.png "Model Visualization"
[image2]: ./examples/model.png "Grayscaling"
[image3]: ./examples/run.gif "Recovery Image"
[image4]: ./examples/placeholder_small.png "Recovery Image"
[image5]: ./examples/placeholder_small.png "Recovery Image"
[image6]: ./examples/placeholder_small.png "Normal Image"
[image7]: ./examples/placeholder_small.png "Flipped Image"


#### 1. Submission includes all required files and can be used to run the simulator in autonomous mode

My project includes the following files:
* notebook.ipynb containing the script to create and train the model
* drive.py for driving the car in autonomous mode
* model.h5 containing a trained convolution neural network 


#### 2. Submission includes functional code
Using the Udacity provided simulator and my drive.py file, the car can be driven autonomously around the track by executing 
```sh
python drive.py model.h5
```
### Model Architecture and Training Strategy

#### 1. Model Architecture
My model consists of the [Nvidia Self-Driving Model Architecture](https://images.nvidia.com/content/tegra/automotive/images/2016/solutions/pdf/end-to-end-dl-using-px.pdf). Below is an image of the model summary and model code

![model_summary][image1]
![model_summ][image2]

Essentially, there are three main components
1) Cropping and Normalization Layers. The crop is because we don't need to know about the car hood/sky for the car to able to drive. Normalization is to center our data around some ranger, so our neural network can better fit our mean-centered data. 
2) Convolutional Layers. Convolutions starting with 5x5 kernels and then 3x3 kernels are used to extract important features in our image. 
3) Dense Layers. These dense layers use our feature maps produced by the convolutional layers to make a prediction for the steering angle. 


#### 2. Attempts to reduce overfitting in the model
Originall, I tried different types of normalization. I also tried drop-out, L2-L1 Loss. However, the most important thing that helped me succeed was just to get **high quality** data. To do this, I drove the car for many laps to gain good data. Moreover, I also drove in reverse afterwards. This meant the hardest part, steering, was generalized for forwards and reverse. This meant the model wouldn't overfit on just one track.
#### 3. Model parameter tuning

The model used an adam optimizer, so the learning rate was not tuned manually (notebook.ipynb section 6).

#### 4. Results
![gif][image3]


See run1.mp4 for the full video.