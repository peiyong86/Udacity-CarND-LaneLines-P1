#**Finding Lane Lines on the Road** 

##Writeup Template

###You can use this file as a template for your writeup if you want to submit it as a markdown file. But feel free to use some other method and submit a pdf if you prefer.

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"

---

### Reflection

###1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 5 steps. 
First, I converted the images to grayscale, then I apply gaussion smooth and canny edge detection to get edge image 1.
Second, I did white/yellow color detection on images, then I apply canny edge detection to the result image to get edge image 2.
Third, I apply region of interest mask to both edge image 1 and edge image2, the mask is calculate according to image size.
Forth, I apply hough transform line detection on both edge images, and combine all detected lines together.
Fifth, I removed some unwanted lines by the slope of lines, and grouping remained lines into to groups according to the slope, then combined lines of each group to get left line and right line.
Sixth, I adjust left line and right line's length to make them even.
Seventh, I drawed lines to image.

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by ...

If you'd like to include images to show how the pipeline works, here is how to include an image: 

![alt text][image1]


###2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when ... 

Another shortcoming could be ...


###3. Suggest possible improvements to your pipeline

A possible improvement would be to ...

Another potential improvement could be to ...