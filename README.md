# Semantic Segmentation

---

**Semantic Segmentation Project**

The goals / steps of this project are the following:

* The ``load_vgg``, ``layers``, ``optimize`` & ``train_nn`` functions are implemented correctly
* The model decreases loss over time
* Number of epoch and batch size are set to a reasonable number
* Most of the images must be labeled correctly (80% of the road and no more than 20% of non-road pixels as the road) 
* Summarize the results with a written report

[//]: # (References)
[python3]: https://www.python.org/
[tensorflow]: https://www.tensorflow.org/
[numpy]: http://www.numpy.org/
[scipy]: https://www.scipy.org/
[kitti-download]: http://www.cvlibs.net/download.php?file=data_road.zip
[starter-code]: https://github.com/udacity/CarND-Semantic-Segmentation
[img1]: ./imgs/um_000034.png "Kitti Road Test Image 1"
[img2]: ./imgs/umm_000015.png "Kitti Road Test Image 2"
[img3]: ./imgs/uu_000025.png "Kitti Road Test Image 3"
[img4]: ./imgs/umm_000082.png "Kitti Road Test Image 4"

---

## Setup

### Frameworks and Packages
Make sure you have the following installed:
 - [Python 3][python3]
 - [TensorFlow][tensorflow]
 - [NumPy][numpy]
 - [SciPy][scipy]

### Dataset
In order to test the Fully Convolutional Network (FCN) download the [Kitti Road dataset][kitti-download]. Extract the dataset in the `data` folder. This will create the folder `data_road` with all the training and test images.

## Files Submitted & Code Quality

#### 1. The submission includes all required files and every TODO task has been accomplished
For this project, I have used the [Semantic Segmentation Starter Code][starter-code] from Udacity and I have modified the following files:
``main.py``

#### 2. The submission includes functional code
To run this project, clone this repository and execute the following command in the repository's root folder:
```python
python main.py
```
#### 3. Final Output:
All labeled test images from the Kitti Road dataset can be found in the ``imgs`` folder of this repository.
Here are a few examples of the results:

![Kitti Road Test Image 1][img1]

![Kitti Road Test Image 2][img2]

![Kitti Road Test Image 3][img3]

![Kitti Road Test Image 4][img4]


## Model Architecture

#### 1. An appropriate model architecture has been employed
The model is based on the pre-trained VGG-16 network which was converted to an FCN (Fully Convolutional Network).

For training the following parameters have been chosen:
* Epochs = 20
* Batch size = 18
* Learning rate = 0.0001
* Dropout rate = 0.55

The training loss decreased over time by each epoch. The overall minimum loss was in the last epoch ``Epoch: 20`` and had a ``Training loss: 0.069`` at ``Batch number: 15``.

#### 2. Final Model Architecture

The final model architecture (``main.py`` lines 63-79) is a Fully Convolutional Network with the following layers and layer sizes:

| Layer                 |     Description                               | 
|:---------------------:|:---------------------------------------------:| 
| Convolution 1x1       | Strides: 1x1                                  |
| Convolution 1x1       | Strides: 1x1                                  |
| Convolution 1x1       | Strides: 1x1                                  |
| Deconvolution 4x4     | Strides: 2x2                                  |
| Skip Connection layer |                                               |
| Deconvolution 4x4     | Strides: 2x2                                  |
| Skip Connection layer |                                               |
| Deconvolution 16x16   | Strides: 8x8                                  |