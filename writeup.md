# **Finding Lane Lines on the Road** 

## Writeup

### This is the summary report of the first project - Finding Lane Lines on the Road.

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on the work in a written report

* Output of images are in https://github.com/shingte/CarND-LaneLines-P1/tree/master/results
* Output of videos are in https://github.com/shingte/CarND-LaneLines-P1/tree/master/test_videos_output

[//]: # (Image References)

[image1]: ./test_images/solidWhiteCurve.jpg "Original"
[image2]: ./gray/solidWhiteCurve.jpg "Gray"
[image3]: ./edges/solidWhiteCurve.jpg "Edges"
[image4]: ./mask_edges/solidWhiteCurve.jpg "Masked_Edges"
[image5]: ./results/solidWhiteCurve.jpg "Final_Results"



---

### Reflection

### 1. My pipeline function, and how I modified the draw_lines() function.

My pipeline consisted of the follwoing steps -
1. Read in the original image and convert to grayscale.
2. Applt the Canny edge detection to get edges image
3. Find the region of intereand ignore everything outside it.
4. Run Hough transform on masked edge detected image
5. Draw lines extrapolated from line segments on top of the original image

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by getting a list of lines detected by the Hough transform, and seperate them to left and right lanes using the sign of the slopes. I then took the average of slopes and interception points of the two lanes, and compute the end points to draw the lane lines.

The images below show how the pipeline works: 

Original:
![alt text][image1]  

Grayscale:
![alt text][image2] 

Canny edge detection:
![alt text][image3] 

Mask edge outside region of interest:
![alt text][image4] 
 
Draw lan lines:
![alt text][image5] 



### 2. Potential shortcomings with my current pipeline

One potential shortcoming would be what would happen when the lane changes direction rapidly.

Another shortcoming is that Lane lines could be hard to detect sometimes during night time or bad weather.


### 3. Possible improvements to my pipeline

A possible improvement would be to improve the draw_line function to better fit the lane lines

Another potential improvement could be to use other algorithms such as deep learning to detect and draw the lan lines.
