# Line-and-Circle-detection-on-images-using-OpenCV
## Idea and Descripytion

The Idea of this project is to find where lines and circles are present in an image. 
This can be used to make a co-ordinate map of where lines and circles in an image is present. 
Here we use OpenCV to extract the coordinates of lines and circles present in the images using the Hough functions.

## Installation

Use the package manager [pip](https://pypi.org/project/opencv-python/) to install OpenCV.

```bash
pip install opencv-python
```
## Usage
### Import packages

```python
#cv2 is refered to openCV
import cv2  
import numpy as np
```
### Loads image
```python
img = cv2.imread("image.png")
```
### Convert image to grayscale and make a canny out of it
```python
img_gray = cv2.cvtColor(img, cv2.COLOR_BGR2GRAY)
img_canny = cv2.Canny(img_gray, 50, 100)
#using other filters like histogram, blur, etc can also increase the efficiency of recognition for your image
```
### Position of circles and its radius
```python
# returns co-ordinates of circles along with its radius to 'circle' ->(x1,y1,r)
circle = cv2.HoughCircles(gray_img, cv2.HOUGH_GRADIENT, 1, 200)
# using and changing other parameters like minRadius, maxRadius, param1, param2, etc 
# can increase the efficiency of recognition for your image

```
### Position of Lines
```python
# returns co-ordinates of lines ->(x1,y1,x2,y2)
linesP = cv2.HoughLinesP(img_canny, 1, np.pi / 180, 50, None, 50, 10)
```
### View found lines by ploting it
```python
for i in range(0,len(lines):
    l=lines[i][0]
    cv2.line(img, (l[0], l[1]), (l[2], l[3]), (0,0,255), 3, cv2.LINE_AA)
    plt.imshow(img)
```
### View found circles by ploting it
```python
circle = np.uint16(np.around(circles))
       for i in circle[0, :]:                       #i[0]=x1
           center = (i[0], i[1])                    #i[1]=y1
           # center                                 #i[2]=radius
           cv2.circle(img, center, 1, (0, 100, 100), 3)
           # outline
           radius = i[2]
           cv2.circle(img, center, radius, (255, 0, 255), 3)
           cr.append([i[0],i[1],radius])	
```
