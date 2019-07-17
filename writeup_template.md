# **Finding Lane Lines on the Road** 

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Improve the pipeline 
* Reflect on the project


[//]: # (Image References)
[image0]:./test_images/solidWhiteRight.jpg
[image1]:./test_images_output/solidWhiteRight.jpg_1:gray.jpg
[image2]:./test_images_output/solidWhiteRight.jpg_2:blur_gray.jpg
[image3]:./test_images_output/solidWhiteRight.jpg_3:canny_edge.jpg
[image4]:./test_images_output/solidWhiteRight.jpg_4:masked_edge.jpg
[image5]:./test_images_output/solidWhiteRight.jpg_5:hough_line.jpg
[image6]:./test_images_output/solidWhiteRight.jpg_6:final_output.jpg

---

### Reflection

### 1. Pipeline Description.

My pipeline consisted of 5 steps. First, I converted the images to grayscale, then I .... 
Main goal of following project is to create pipeline for the lane line detection on the road. Final pipeline consists of 5 steps to detect lane lines on the road.
First, given the image of road as following,
![alt text][image0]

Step 1: Convert the image to grayscale.
![alt text][image1]

Step 2: Smooth out the image by applying gaussian blur
![alt text][image2]

Step 3: Detect the edges using canny edge
![alt text][image3]

Step 4: Define the region of interest and discard edges located outside of region of interest. Region of interest is defined by trapezoid, where lane right infront of the car is located at. 
![alt text][image4]

Step 5: Draw Hough line on the image where lanes are located at.
![alt text][image5]

step 6: Add the hough line on the initial image.
![alt text][image6]

### 2. Pipeline Improvement.

Original model was able to detect the lane and draw hough line. However, as some of the lanes were disconnected, it was not able to detect the full extent of the lane. Therefore modification on the pipeline was necessary for improvement.
In order to get full extent of lane, draw_lines() function was modified. First, left lane and right lane were detected seperately and slope of each lanes were calculated using polyfit function. After the slopes were calculated, linear function of each lane were obtained and full extent of the line were able to be drawn.

### 3. Identify potential shortcomings with your current pipeline

Following project used images and videos when car was driven at daytime and when view was clear. It may not be able to detect the lanes if there is too much or less sunlight, during rainy day. From the project, it is seen that model does not perform well when the road color is too bright or there is too much sunlight. It is necessary to consider various weather and road condition. 
Also, model can only be used for straight lane. If it faces with curves, it would not be able to detect the lane. 

### 4. Suggest possible improvements to your pipeline

Instead of detecting and drawing a linear line, fitting lanes to higher polynomial function could improve the model. Also preprocessing image differently depending on the weather, and average brightness of the image could improve the pipeline.
