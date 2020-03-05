The objective of this task is to predict keypoint positions on face images. This can be used as a building block in several applications, such as:

tracking faces in images and video
analysing facial expressions
detecting dysmorphic facial signs for medical diagnosis
biometrics / face recognition
Detecing facial keypoints is a very challenging problem.  Facial features vary greatly from one individual to another, and even for a single individual, there is a large amount of variation due to 3D pose, size, position, viewing angle, and illumination conditions. Computer vision research has come a long way in addressing these difficulties, but there remain many opportunities for improvement.

You can download the data from : https://www.kaggle.com/c/facial-keypoints-detection/data

This is well beyond the competition data, but did this for understanding purposes only. There may be a better approach. I have not tuned the hyper parameters. Just used Adam as Optimizer and MSE as loss function. 50 Epochs of 200 batch size. (This itself took close to 2 hrs in Colabs)

Approach :

Used a CN with following to achieve the objective. This is a regression problem, where given an image, 30 different points of the face needs to be identified (predicted). I have used the training data to map the points on the face. Post prediction of target values, five images were mapped and plotted againts the various target attributes.

CNN Layers : (All layers use LeakyReLU except the target layer. Target Layer has no activation function - Regression Problem)

Layer 1 : 32 3x3 Kernel Filter with BatchNormalization
Layer 2 : MaxPool2D
Layer 3 : 32 3x3 Kernel Filter with BatchNormalization
Layer 4 : MaxPool2D
Layer 5 : 64 5x5 Kernel Filter with BatchNormalization
Layer 6 : MaxPool2D
Layer 7 : Flatten
Layer 8 : Fully Connected DNN with 256 neurons with BatchNormalization
Layer 9 : Fully Connected DNN with 128 neurons with BatchNormalization
Layer 10 : Fully Connected DNN with 64 neurons with BatchNormalization
Layer 11 : Output Layer with 30 neurons for 30 target attributes prediction
