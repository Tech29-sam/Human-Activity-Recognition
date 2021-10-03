# Human-Activity-Recognition

## Objective: 
To train a model that classifies different human activities/hobbies like playing cricket, punching, playing piano etc. by processing information from the videos. To train a video classifier by transfer learning to increase accuracy.

## Dataset: 
I’ve used the UCF101 dataset to build the video classifier. The dataset consists of videos categorized into different actions, like cricket shot, punching, biking, etc. This dataset is commonly used to build action recognizers, which are an application of video classification.
link: [dataset-link](https://www.crcv.ucf.edu/data/UCF101.php)

## Technique used:
1) I have collected the dataset and analyze about the various classes present.
Note: As the dataset is quite huge, it will take a lot of time to train all the videos. So, I have taken a subsample of the dataset. So, my model will be trained on 5 subclasses (for recognition of 5 different activities)

2) Network Architecture: The video is actually a sequence of frames of images. So, CNN is used to train those images. Each frame contains spatial information, and the sequence of those frames contains temporal information. To model both of these aspects, a hybrid architecture is used that consists of CNN (for spatial processing) as well as RNN (for temporal processing).
 
3) I used OpenCV's VideoCapture() method to read frames from videos.
Saved video frames at a fixed interval until a maximum frame count is reached.
i) Capture the frames of a video.
ii) Extract frames from the videos until a maximum frame count is reached.
iii) In the case, where a video's frame count is lesser than the maximum frame count, we will pad the video with zeros.

4) Then I used Transfer learning approach to extract meaningful features from the extracted frames. Here, I have obtained the accuracy by training on InceptionV3. Then use the StringLookup layer encode the class labels as integers. Finally, we can put all the pieces together to create our data processing utility.

5) Training & Testing: Now, fed this data to a sequence model consisting of recurrent layers like GRU. Then tested on a random sample of videos in the test folder. The model has accurately predicted the correct prediction. Also, the probabilities of various classes are made to print which determines the accurateness.

## Assumptions: 
Training over a shorter subsample of dataset which will take less amount of time, so it can be checked if the architecture can be used to predict over a large dataset
Further Improvements to increase accuracy: This architecture can be deployed on the whole dataset to increase the classes. Also, hyperparameter tuning can be done, and also training with different transfer learning approaches like VGG16, efficientnet etc.
