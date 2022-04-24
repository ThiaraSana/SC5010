# SC5010

BACKGROUND
- Happywhale is an NGO founded in 2015, with a mission to increase global understanding of marine environments. They collaborate with many individual organisations and volunteers to photograph different whales and dolphins, which are then identified by species and individual ID by experts. this is a very labor intensive process which takes up thousands of hours. They chose to make their database avaliable in hopes of building a predictive model, which can reliably predict species and individual ID's for species of whales and dolphins. Our scope for the project was not to identify the individual ID, but somewhat accurately predict the species in a given photo.

HAPPYWHALE DATASET:
- The happywhale dataset is significant in size, with more than 57k entries and 28 different species making up more than 57GB of data. The data itself consists of a photo of a whale/dolphin fin or tail, as well as the species and individual ID provided. A lot of the species are closely related, and since it's only a small part of the animal above the waterline, it can be challenging to tell different individuals or species from another.

EDA AND DATA PREP.
- Since the data is provided by many different actors, it also varies greatly; this means that each photo has different resolution, size, crop, color etc. which makes it more challenging to standardize for our model. 
- The data has a very heavy class imbalance, with species having between 14 and 10.000 entries. 
- We performed some basic datacleaning, as we realised some of the species had been mislabelled, but otherwise there were no gruelling errors to the dataset.
- Under-or oversampling was not a realiable solution, as we would either end up with a huge or tiny dataset - and we did not think it was realistic to brute force 14 images to +10k using image augmentation.

- In order to standidize the data a bit, we chose 2 different methods for cropping the images to a 224x224 size:
- First we used a basic centerbox cropping which ended up working overall well, with a few edgecases where the fin would not fit in the crop.
- Next we used a YOLOv5 object detection, which yielded better results, but also placed the cropped image on a black bounding box. We also saw some examples where this tool would crop birds or boats instead of the dolphin or whale. 

DEEP LEARNING CLASSIFICATION
- For this step we used VGG16; a convolutional neural network primarily used for image recognition and classification. The model is 16 layers deep and is pretrained with ImageNet weights to make use of transsfer learning. This allowed us to utilize already-existing architecture as a foundation for the model.

RESULTS AND INSIGHTS:
- Surprisingly we saw the best results from the simple centerbox cropping method, yielding an accuracy of about 75%. We identified a key error on the bottlenose dolphin, but this was proved to be caused by a faulty crop (no dolphin in image)
- Our results on the object detection was slightly worse with an accuracy of about 64% This was not due to a bad crop, but we suspect the bounding box might influence the overall outcome. The Deep learning model uses a pixel-by-pixel approach, which might be influenced by the significant black border around most images.







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

