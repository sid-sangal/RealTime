# RealTime
Machinve vision project. An open source library based attempt the replication of NI LabView and Adaptive Vision Studio modules
Real-time object detection using Python, Tensorflow, OpenCV.

@@@ All sources have been linked and steps have been mentioned along with SOTA research papers for reference. 
$$$ All softwares, datasets, libraries, frameworks, etc are opensource and can be replicated by anyone.

7/10/21
This project is inspired by multiple YouTube videos and docunentation that will be posted in appropriate locations in this file

*** One of the things that I am looking forward to most is to make a video explanation of the build and implementation of this project because I personally tend to
have a bias towards video walkthroughs.

@Time stamp: 8:14 pm

As an application of Computer Vision, this projec will be detecting an targeted object in a live video feed. One of the observations has been that the training in the instructions has been using very few images leading to unnderfitting.  I will be combining my project from previous semseter which was a binary classification problem on static labled data detecting the presence or absence of masks.

This project uses transfer learning techniques usiing the MobileNest SSD or single shot detector.
Steps:

1. Downloading and labeling dataset
2. Transfer Learning Using YoloV4 and YoloV4-tiny
3. Real time detection(webcam) using OpenCV

@Time stamp 7/16

After 3 attempts of building the project I have reached a point of training the model with the error being that the model expects a 3D or 4D input numpy array but recieves a 2D one.

The error according to online search is due to the input file format not being in JPEG. Which is not the case here. The suspected problem is due to there being multile boundign boxes in the trainign image and the corresponding xml files. I will be training a new model with a new dataset and xml files with only one bounding boxes and updating the proper documentation for the same.

The following few days will be spent on learning and reading about various architecturesand available documentation for the models.

@Time stamp 7/21

The project will be implemented on Google Colab instead of locally using CUDA and CUDNN because of the numerous version incompatability errors. Although the project is taking a different route for now, the local implementation will still be performed as a separate project.

Sources used: 
1. https://medium.com/analytics-vidhya/yolov4-vs-yolov4-tiny-97932b6ec8ec
2. https://www.youtube.com/watch?v=SCAgktactKE
3. https://www.youtube.com/watch?v=H3SJcwttTi4&t=23s
4. https://medium.com/analytics-vidhya/train-a-custom-yolov4-tiny-object-detector-using-google-colab-b58be08c9593

Step 1: Reading about how Yolo tackeles the problem.

Research paper: https://arxiv.org/abs/2004.10934
Explanations: https://www.youtube.com/watch?v=_JzOFWx1vZg

Step 2: Selection of framework: The darknet framework has been selected and the repo has been cloned. Out of the available config files, I will be using the YoloV4 custom config file and making changes for binary classification nad number of of training steps. Classes: 2, steps: 6,000. This number is based on online search for the model. 

The ideal loss value for the model in a Yolo V4 environment should be between 0.05 and 0.3. For a dataset of the selected size (1500 images) we would meed 6000 steps.

Step 3: sourcing the datset: I previously attempted to create my own dataset but the labelimg software did not accept images wiht the file format on iOS. As the requiremnet of data is quite high as well, I will be taking data from available datasets on Kaggle.

  Dataset source: https://www.kaggle.com/techzizou/labeled-mask-dataset-yolo-darknet


Step 4: For ease of access, the dataset will be mounted on cloud. As uploading such a big dataset for every instace of Colab could be a hassle(the VM has crashed due to unknown reasons multiple times in the past) it makes sense to mount the developer's Google drive for this application. The steps are quite simple and will be eexplained in the colab window or the Ipynb.

Step 5: Creating the labels for the images. Each image contains one face with one bounding box and the .txt files have bee ngenerated using ""

Step 6: Train/test split: Since the dataset is large enough, I am splitting it into 90:10 (Train:test)

Step 7: After mounting the drive, making changes to the config file and splitting the train, test files into appropriate folders and providing file path variables for all necessary directories( it is a good practice to provide path variables to make the code look cleaner and easier to debug)

Step 8: We are now close to the training phase. We will now build our Yolo model using the !make command and import the existing weights from the repository. We are not trainig the weights from scratch but rather performing transfer learning as the time required and scope for error is quite large and unnecessary. The model has been previously trained on the famous MSCOCO dataset and is ver ywell generalized on day-to-day objects. We will be retraining these weights for our application on th edataset containing faces with labels mask and no_mask.

Step 9: We now begin the training of the model by using the command: !./darknet detector train data/obj.data cfg/yolov4-custom.cfg yolov4.conv.137 -dont_show -map

We can visualize the loss graph using the cv2 library and plot the average loss value at every 100 iterations. This will only work for uninterrupted training.

Step 10: Train the model. Finally!!!! The model has been started for training and the documentation till this point has been updated.

@Time Stamp: 3:45 pm The training has been started.

@Time stamp: 5:12 pm Th etraining has reached step 980 wit hthe current loss value being 2.31. At the current pace, it would take approximately 5 more hours for the training to finish or the loss curve to reach an asymptotic behaviour.
