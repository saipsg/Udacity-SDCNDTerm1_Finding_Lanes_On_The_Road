# **Finding Lane Lines on the Road** 
The project was good learning experience and a starting curve for my beginner coding skills.
---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following  and are met
* Make a pipeline that finds lane lines on the road
* The algorithm should be able to detect lanes both for the white lines and yellow lines in the video



### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.
The pipeline is done by sequential steps
1. Reading and conversion of a 3 channel RGB image to Grayscale image
2. Apply Gaussian blur to smooth the sharp edges and minimise noise
3. Apply Canny algorithm to extract the edges from the grayscale image, i.e using the change in gradient of pixel densities
4. Mark a region of interest on the image, by masking the image with a polygon covering the lanes with their horizon
5. Using Hough transform draw lines on the masked images from the points in the edges detected using canny algorithm
6. Display a weighted image with the hough lines overlapping on the actual image as final output

Steps to Draw_lines from canny_edges
- find the slope of the lines from two points identified from the edges in the region of interest
- based on the value of the slope differentiate into left and right lanes,i.e., if slope is negative, it is right lane and if positive left lanes
- average the position of the left and right coordinates
-repeat this for i,j number of points identified in the edges
- now find the mean of slope and mean of the coordinates of the left and right lane
- using the equation of line,y=mx+c, we find the top and bottom values of the x-cordinate and for the mean-y intercept we found and adjust them to the mean value of x
- also provide fixed values if a frame is skipped/ lane is not detected in the particular frame
-use the CV2.line function to draw the line on the image




### 2. Identify potential shortcomings with your current pipeline


The detected lane line in the SolidWhiteRight.mp4 is shaky or intermittent for intial few seconds. 

Tthis algorithm is suitable for a simple straightline application and parameters need to be tuned further.


### 3. Suggest possible improvements to your pipeline

I can still try the HSV transformation for more robustness to light colour detection and this may reduce the shaky effect in the white lane video
I can still try using the curve fitting functions for exptrapolating the identified slopes and points and make them roboust to curvy roads

This algorithm is not roboust to curves in the road, low light and darkness conditions and roads without clear lane markings. I am expecting to the advanced lane findings project for further knowledge of these shortcomings