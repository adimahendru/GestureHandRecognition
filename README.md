# GestureHandRecognition
This project was done by Aditya Mahendru for UW CSE 455 (Computer Vision)

1. [Code](https://github.com/adimahendru/GestureHandRecognition)
2. [Video](https://github.com/adimahendru/GestureHandRecognition/blob/main/video1281761444.mp4)

## About 
For this project I created a opencv and python program on hand gesture recognition. It detects numbers one through five but can easily expand to other hand gestures in sign language. While we have advancments in voice detection and face detection, hand gestures still face challenges with foreground vs background, movements, and diversity in gestures. To tackle some of these problems, I focused on segmenting the hand region, thresholding, and contours.

After creating this program, I decided to implement some machine learning. I collected images from kaggle, labeled them using the image package and built a sign language detector using Transfer Learning and Tensorflow Object Detection api to train a deep learning model. This gives us the ability to detect hand gestures in real time.  

## Approach
When creating the gesture_recognition.py program, I captured video from the webcamera, picked a frame and flipped the image. I converted to grayscale and then to binary to find the region of interest. A grayscale image can help with contouring the image unlike rgb. I then use gaussian blur to reduce noise components in the image. This is followed by thresholding for image segmentation to create binary images. The thresholding acts as a low pass filter. Then I find contour with max area and create a bounding rectangle around the contour. I find the contour defects which is the region between the fingers. Using the cosine law, I can find the defects. Using if statements I add text to suggest what hand gesture is being displayed based on the number of defects it counts. 

For detection in real time I used a template where I was able to setup Tensorflow Object Detection pipeline configuration and use transfer learning to train a deep learning model. This template can be found in the Tutorial.ipynb file.

## Datasets
I used this [dataset](https://www.kaggle.com/muhammadkhalid/sign-language-for-numbers). It contained hand gestures from zero to nine with 1500 images in each folder. I modified my dataset to using only the folders with numbers one through five. Also, when I added these images to my train and test folders, I decreased the number of images used significantly instead of incorporating every folder of 1500 pictures.

## Results & Discussion
I trained the model for 10,000 steps. At each 100 step I was given a loss value. By the 10,000 step the loss value result was 0.02. When running the program for detecting in real time, there were problems where the hand gestures were not very accurate and often confused certain hand gestures for a different number. One is that the gestures in the data were not as distinct as they should have been; the images may not have been clear. Another reason is the quantity of images was not sufficient. I most likely needed more data to have a better accuracy.

## Future
I do plan to work on this again. I want to try to improve the accuracy and fix any mistakes that may have resulted in the model's poor accuracy. Later I may attempt in creating actions on my laptop based on hand gestures such controlling the volume.

## References
* Hand Gesture Recognition: https://gogul.dev/software/hand-gesture-recognition-p2
* Real Time Sign Language Detection: https://www.youtube.com/watch?v=QkO_3absfdw&list=PLwyHr2n-aWLAiUSg9SK9sZhNCYuOjGejN&index=7
