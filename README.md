# SC5010

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

