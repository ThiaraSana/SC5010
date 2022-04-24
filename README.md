# SC5010

BACKGROUND
- Happywhale is an NGO founded in 2015, with a mission to increase global understanding of marine environments. They collaborate with many individual organisations and volunteers to photograph different whales and dolphins, which are then identified by species and individual ID by experts. this is a very labor intensive process which takes up thousands of hours. They chose to make their database avaliable in hopes of building a predictive model, which can reliably predict species and individual ID's for species of whales and dolphins.

HAPPYWHALE DATASET:
- The happywhale dataset is significant in size, with more than 57k entries and 28 different species making up more than 57GB of data. The data itself consists of a photo of a whale/dolphin fin or tail, as well as the species and individual ID provided. A lot of the species are closely related, and since it's only a small part of the animal above the waterline, it can be challenging to tell different individuals or species from another.

EDA AND DATA PREP.
- Since 





Table of Contents:

SCRIPTS:
- EDA Whale.ipynb:
  - Exploration of the train.csv (labels of the training images), this is where we decided on the classses of species and generated the .csv file of the images that were going to be used for our analysis
- BoundingBoxYOLO.ipynb: 
  - Cropping of Selected images using the object detection model YOLOv5l
	- Reference: https://www.kaggle.com/code/awsaf49/happywhale-boundingbox-yolov5/notebook
- VGG16-ManualCropping.ipynb:
  - VGG16 for classification of the species of the images using a non-deep learning guided cropping method
- VGG16-YOLOv5CroppedImages.ipynb:
  - VGG16 for classification of the species of the images using the YOLOv5l cropped images

DATA:
- final.csv: filtered image lable database
- train.csv: original image lable database
- images
	- Final: Original filtered images sorted into Train, Test, and CrossValidation, and then into the images respective classes
	- results: YOLOv5l cropped images sorted into Train, Test, and CrossValidation, and then into the images respective classes

