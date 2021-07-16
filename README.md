# RealTime
Real-time object detection using Python, Tensorflow, OpenCV.

7/9/21
This project is inspired by multiple YouTube videos and docunentation that will be posted in appropriate locations in this file

*** One of the things that I am looking forward to most is to make a video explanation of the build and implementation of this project because I personally tend to
have a bias towards video walkthroughs.

@Time stamp: 8:14 pm

As an application of Computer Vision, this projec will be detecting an targeted object in a live video feed. One of the observations has been that the training in the instructions has been using very few images leading to unnderfitting.  I will be combining my project from previous semseter which was a binary classification problem on static labled data detecting the presence or absence of masks.

This project uses transfer learning techniques usiing the MobileNest SSD or single shot detector.
Steps:

1. Downloading and labeling dataset
2. Transfer Learning Using MobileNet SSD
3. Real time detection(webcam) using OpenCV

@Time stamp 7/16

After 3 attempts of building the project I have reached a point of training the model with the error being that the model expects a 3D or 4D input numpy array but recieves a 2D one.

The error according to online search is due to the input file format not being in JPEG. Which is not the case here. The suspected problem is due to there being multile boundign boxes in the trainign image and the corresponding xml files. I will be training a new model with a new dataset and xml files with only one bounding boxes and updating the proper documentation for the same.

Step 1: Downloading data from Kaggle: 

