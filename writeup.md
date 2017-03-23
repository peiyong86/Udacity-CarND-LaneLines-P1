**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image_gray]: ./examples/grayscale.jpg "Grayscale"
[image_colordetect]: ./examples/cimage.jpg "Color detetion"
[image_combinedlines]: ./examples/combinedlines.jpg "Combined lines"
[image_result]: ./examples/result.jpg "result"

---

### Reflection

###1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 5 steps. 
* First, I converted the images to grayscale, then I apply gaussion smooth and canny edge detection to get edge image 1.
Second, I did white/yellow color detection on images, then I apply canny edge detection to the result image to get edge image 2.
* Third, I apply region of interest mask to both edge image 1 and edge image2, the mask is calculate according to image size.
* Forth, I apply hough transform line detection on both edge images, and combine all detected lines together.
* Fifth, I removed some unwanted lines by the slope of lines, and grouping remained lines into to groups according to the slope, then combined lines of each group to get left line and right line.
* Sixth, I adjust left line and right line's length to make them even.
* Seventh, I drawed lines to image.

In order to implement above pipline, I wrote several functions include: 
filter_lines: filter out unwanted lines by slope
color_of_interest: detect white and yellow color
equal_lines: modify two input lines to make them even
get_slope: calculate slope of input line
combine_lines: combine input lines into left line and right line

This is images of some step, for more detailed decription, please review the code: 

![alt text][image_gray]
![alt text][image_colordetect]
![alt text][image_combinedlines]
![alt text][image_result]


###2. Identify potential shortcomings with your current pipeline
One potential shortcoming would be what would happen when some detected lines can not be removed by ROI and slope filter, that would generate inaccurate results.
Also current algorithm does not consider more difficult cases, such as shadow, rain, dark enviroment and light reflection.

###3. Suggest possible improvements to your pipeline
A possible improvement would be to use more advanced filtering algorithm, such as combine both slope and distance to coordinate origin to filter unwanted lines.
Another potential improvement could be to use HSV color space to remove shadow and lighting effects.
