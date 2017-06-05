# **Finding Lane Lines on the Road** 

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.


My pipeline consisted of 6 steps. First, I converted the images to grayscale, then I applied colorselection by applying cv2.adaptiveTreshold function. The output images are as follows:

###1 - Grayscale conversion :
![alt text] (./test_images_output/01_grayscaled_solidWhiteCurve.jpg) 

###1a - Color selection : 
![alt text] (./test_images_output/01a_color_selected_solidWhiteCurve.jpg) 

After that I applied canny edge detection algorithm to the image and the result was below:

###2 - Canny Edge Detection : 
![alt text] (./test_images_output/02_cannied_solidWhiteCurve.jpg) 

After canny edge detection I applied gaussian blur to the image in order to soften
the edges below:

###3 - Applied Gaussian Blur : 
![alt text] (./test_images_output/03_blurred_solidWhiteCurve.jpg) 

Then I applied region of interest helper function in order to ignore to ignore
the areas out of the region of interest: 

###4 - Removed rest part of Region Of Interest: 
![alt text] (./test_images_output/04_roi_applied_solidWhiteCurve.jpg) 

Now it is time to apply hough transfom to draw lines on the image. 
In order to draw a single line on the left and right lanes, I modified the draw_lines() function by creating additional helper functions. First I created
get_min_max() function. This function separates the lines according to their 
slope and after that calculates an average slope of the left and right lines.
And finally extends the lines according to the average slope. 
It also ignores the lines if the coordinates of the lines are higher
than the standard deviation of the list. In order to get the output
of the above method return slope_right_avg and slope_left_avg.
    
Another method is to create a list of the lines coordinates and get
their minimum and maximum values. If the minimum and maximum points
are calculated from the points list then we can calculate the slope
and extend the line.
    
I tried both method and I think  second method works better. Because when 
I use the first method on challenge video, it crashes on aroun %75.

I created 2 helper functions more (calculate_new_x() and calculate_slope())
in order to extrapolate the lines to maximum and minimum y.

###5 - Applied Hough Transform:
![alt text] (./test_images_output/05_hough_lined_solidWhiteCurve.jpg) 

Finally I combined the hough lines with the original image below:

###6 - Combined with Original Image:
![alt text] (./test_images_output/06_final_solidWhiteCurve.jpg) 



### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when ... 

Another shortcoming could be ...


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to ...

Another potential improvement could be to ...
