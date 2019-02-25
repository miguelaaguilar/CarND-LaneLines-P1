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

The first step is to convert the image to gray scale with 

![alt text][gray]

#### 2. Contrast Improvement

I added a bit of contrast improvement to help in cases such in the challenge video, where the contrast of the lane is low due to the color of a road section

![alt text][contrast]

#### 3. Gaussian

The Gaussian Blur is applied using the function cv2.GaussianBlur()

![alt text][gaussian]

#### 4. Canny

The Canny transform is applied using the function cv2.Canny()

![alt text][canny]

#### 5. Region Definition

I defined narrow regions removing the area in the middle of the lanes to filter out any noise comming for example of shades of tree, etc.

![alt text][region1]
![alt text][region2]

#### 6. Hogh Lines

I modified the draw_lines() function by using linear region to find the lines. First I divided the list into the ones that belong to the left lane and the ones to the right lane. Using the points that define those lines I performed the linear region using the functions np.polyfit() and np.poly1d(z_left). The linear regression allowed to consolidate and extrapolate both lines.

![alt text][lines]

#### 7. Final Images

The final images look as follows:

![alt text][final]

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
