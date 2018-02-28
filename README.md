# Semantic Segmentation
## Introduction
In this project, the pixels of a road in images are labeled using a Fully Convolutional Network (FCN) based on the VGG-16 image classifier. 

## Architecture

A pre-trained VGG-16 model was used to convert to a fully convolutional network. This is achieved by converting the final fully connected layer to a 1x1 convolution and setting the depth equal to the number of desired classes (in this case, two: road and not-road). Input image dataset is followed by multiple convolution and max pooling layers. The spatial information is retained by deconvoluting the model. 

Performance is improved through the use of skip connections, performing 1x1 convolutions on previous VGG layers (in this case, layers 3 and 4) and adding them element-wise to upsampled (through transposed convolution) lower-level layers (i.e. the 1x1-convolved layer 7 is upsampled before being added to the 1x1-convolved layer 4). Each convolution and transpose convolution layer includes a kernel initializer.

## Optimizer
The loss function for the network is cross-entropy, and an Adam optimizer is used.

## Training: 

Hyper parameters used in the training are:

    -Epochs: 25
    -Batch Size: 8
    -Learning rate: 0.0001
    -Dropouts: 0.2

## Results 

The following images of the output of the results of Fully Convolutional Network for Semantic Segmentation:

![](runs/um_000028.png)

![](runs/um_000063.png)

![](runs/um_000015.png)

![](runs/uu_000090.png)

## Setup
### Frameworks and Packages
Make sure you have the following is installed:
 - [Python 3](https://www.python.org/)
 - [TensorFlow](https://www.tensorflow.org/)
 - [NumPy](http://www.numpy.org/)
 - [SciPy](https://www.scipy.org/)

### Dataset
Download the [Kitti Road dataset](http://www.cvlibs.net/datasets/kitti/eval_road.php) from [here](http://www.cvlibs.net/download.php?file=data_road.zip).  Extract the dataset in the `data` folder.  This will create the folder `data_road` with all the training a test images.

### Run
Run the following command to run the project:
```
python main.py
```
## Refernces
https://people.eecs.berkeley.edu/~jonlong/long_shelhamer_fcn.pdf
