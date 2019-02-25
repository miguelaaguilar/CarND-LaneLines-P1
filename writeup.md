# **Finding Lane Lines on the Road** 

## Writeup of Miguel Aguilar
---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[gray]: ./test_images_output/gray.png "Grayscale"
[contrast]: ./test_images_output/contrast.png "Contrast"
[gaussian]: ./test_images_output/gaussian.png "Gaussian"
[canny]: ./test_images_output/canny.png "Canny"
[region1]: ./test_images_output/region1.png "Region 1"
[region2]: ./test_images_output/region2.png "Region 2"
[lines]: ./test_images_output/lines.png "Lines"
[final]: ./test_images_output/final.png "Final"

---

### Reflection

### 1. Description of the proposed and implemented lane detection pipeline

My pipeline consisted of 7 steps decribed as following:

#### 1. Gray Scale

![alt text][gray]

#### 2. Contrast Improvement

![alt text][contrast]

#### 3. Gaussian

![alt text][gaussian]

First, I converted the images to grayscale, then I .... 

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by ...

If you'd like to include images to show how the pipeline works, here is how to include an image: 


### 2. Potential shortcomings of the pipeline

The following are potential shorcomings of the implemented pipeline:

* Shadows and other forms of noise on the road might create trouble while detection the lanes. This effect was observed in the challenge video
* When the contrast between the lanes and the road is small, it becomes difficult to detect the edges. This effect was observed in the challenge video
* Sharp curves along the road might be challenging to detect, in particular when it comes to extrapolate the lines
* The region of interest is defined statically, which might be a problem if the width of the lanes is bigger of smaller than expected

### 3. Possible improvements

Some potential improvements that I would suggest are:

* Improve the preprocessing of the images to allow the line detection even with the contrast between the road and the lanes is small
* Improve the detection approach to support sharp curves
* Adaptive definition of the region of interest
