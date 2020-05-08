# **Finding Lane Lines on the Road** 



### Objective

---

**Finding Lane Lines on the Road**

In this project, the tools learned in the lane finding lessons are applied to identify lane lines on the road. The pipeline is developed and tested on a series of individual images, and later applied to a video stream.


[image1]: ./test_images_output/solidWhiteCurve.jpg "Lane finding"

---

### Reflection

### 1. Pipeline description

My pipeline consisted of 5 steps:
1. The image is converted to Grayscale
2. A gaussian blur is then applied to reduce the noise. In this project the used Kernel size is 5.
3. Canny edge detection algorithm is then used, with lower threshold equal to 100 and higher threshold equal to 200
4. A region of interest is then extracted from the image using polygons to eliminate the other lines/edges that are outside of the vehicle's lane.
5. Hough algorithm is then applied to find the lines. The used parameters are: threshold = 15, minimum line length = 10 pixels ,maximum line gap = 170 pixles
6. The lines are then added to the image

In order to draw a single line on the left and right lanes, all the lines that are part of these lanes are averaged using least squares polynomial fit (degree = 1), then extrapolated to cover the lanes until the bottom of the image (in order to cover the missing lane parts for example to ensure continuity of lane finding between frames).




### 2. Potential shortcomings with current pipeline


The tuning of the lane finding horizon in the current pipeline is done manually. In fact, in this project lanes are drawn for 40% of the image height, and this value could lead to incorrect lane finding in the farthest lane points.

Another shortcoming could be the estimation of complex lane configurations like in curves.


### 3. Possible improvements to current pipeline

A possible improvement would be to further tune the parameters using more input images for diffrent tricky lane configurations.

