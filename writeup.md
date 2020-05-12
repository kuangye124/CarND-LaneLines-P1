# **Finding Lane Lines on the Road** 

## Writeup Template

### You can use this file as a template for your writeup if you want to submit it as a markdown file. But feel free to use some other method and submit a pdf if you prefer.

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

Pipe line:
1. Convert to grayscale image for the following processing
2. Apply Gaussian smoothing
3. Apply Canny transform to detect edges
4. Set region of interest
5. Apply Hough transform to detect lanes
6. Merge lines with the original image

In order to change the line segments to full solid lines, I did the following:
1. Separate line segments by slope (left lane has positive slope and right lane has negative slope). During the separation, I set a threshold for the slope to extract non-lane lines (noise).
2. Use numply polyfit function to find the slope and intersection for both left and right lane.
3. From y_top & y_bottom coordinate, calculate the x top and bottom coordinates for both left and right lane.
4. Draw the lanes seperately by bottom and top x,y coordinates


![alt text][image1]


### 2. Identify potential shortcomings with your current pipeline


Potential shortcoming:
1. Need to change code every time when input/output a different image/video
2. Need to change region of interest for different image/video
3. Need to change Hough transofrm parameters for different image/video


### 3. Suggest possible improvements to your pipeline

A possible improvement would be before processing images/videos, modify them so they share a more general info.
