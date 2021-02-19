# Image Transformations and Panorama - Overview
Project in *Computer Vision* Course 2020 at **Tel-Aviv University, Israel.**
Overview of my project with my colleague Omri P.

:fire:  Buzzwords : `Computer-Vision`, `Image-transformation`, `Homography`, `Panorama`.
## Project Assignments:
[![](images/fig_mp11b.jpg)](#project-assignments)
* Estimation of Homography transformation matrix `H` from *matching points* between two images.
* Apply forward and backward mapping transformation.
    * Forward mapping - self implemented
    * Backward mapping - using `cv2.warpPerspective`
* Attach the two images to a single panorama image (using backward mapping)


## Parameters Estimation:
**Input:** Two images and set of matching points between them:

<img src="images/a.png" width="200"><br>

We need to find the Homography transformation matrix `H` from the Equation:

<img src="images/b.png" width="300"><br>

To find the matrix `H` we need at least 4 matching points. We get the system:

<img src="images/c.png" width="400"><br>

More matching points will provide a better estimation for `H` params, but the data may contains outliers.

### Outliers :

The naive estimation using all the matching points will provide the transform:
 <p align="center">
 <img src="images/fig_fmpNAIVE.jpg" width="400"><br>
  <i>Forward mapping transformation with outliers
</i>
</p>

We can see that this transformation is not matched the Homography transformation between the images, because of the outliers in the data.
 
We used RANSAC algorithm to deal with the outliers and get the correct parameters of the transformation.

## Forward Mapping:
Forward mapping *(from src to dst)* :   this mapping may create artifacts in the transformed image:

 <p align="center">
 <img src="images/fig_fmp.jpg" width="400"><br>
  <i>Forward mapping artifacts
</i>
</p>

## Backward Mapping:
Backward mapping *(from dst to src values)* :   We can see that we get good result.

 <p align="center">
 <img src="images/fig_bmp.jpg" width="400"><br>
  <i>Backward mapping using cv2.warpPerspective
</i>
</p>

## Panorama result:
We Transformed and aligned the images on the same coordinates, we get the panorama image:

 <p align="center">
 <img src="images/pan11.jpg" width="800"><br>
  <i>
</i>
</p>

## Test Images:
We took two images and find some matching points between them:
(we also set few outliers in the data)

 <p align="center">
 <img src="images/fig_mp22b.jpg" width="1000"><br>
  <i>
</i>
</p>

We test our implementation on these images, and get the Panorama image:
 
 <p align="center">
 <img src="images/pan2.jpg" width="800"><br>
  <i>
</i>
</p>

