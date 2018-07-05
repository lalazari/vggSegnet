# Image - Pixel Segmentation in Keras : Implementation of VggSegnet.

## Getting Started

### Prerequisites

* Keras 2.0
* opencv for python
* Tensorflow 
* Optional: Use Virtual Enviroment

```shell
sudo apt-get install python-pip python-dev python-virtualenv
virtualenv --system-site-packages targetDirectory
source ~/targetDirectory/bin/activate
easy_install -U pip
pip install --upgrade tensorflow-gpu
pip install opencv-python
sudo pip install --upgrade keras
```

### Preparing the data for training

You need to make four folders

*  images_train 
*  images_test
*  annotations_train
*  annotations_test

The filenames of the annotation images should be same as the filenames of the RGB images.
The size of the annotation image for the corresponding RGB image should be same. 
For each pixel in the RGB image, the class label of that pixel in the annotation image would be the value of the blue pixel.

Only use bmp or png format for the annotation images.

### Download the sample prepared dataset

Download and extract the following:

https://drive.google.com/file/d/0B0d9ZiqAgFkiOHR1NTJhWVJMNEU/view?usp=sharing

## Training the Model

To train the model run the following command:

```shell
python train.py \
 --save_weights_path=weights/ex1 \
 --train_images="data/dataset1/images_prepped_train/" \
 --train_annotations="data/dataset1/annotations_prepped_train/" \
 --n_classes=11 \
 --input_height=224 \
 --input_width=224 \
 --model_name="vgg_segnet" 
```

## Getting the predictions

To get the predictions of a trained model

```shell
python predict.py \
 --load_weights_path=weights/ex1 \
 --test_images="data/dataset1/images_prepped_test/" \
 --output_path="data/predictions/" \
 --n_classes=11 \
 --input_height=224 \
 --input_width=224 \
 --model_name="vgg_segnet" 
```

