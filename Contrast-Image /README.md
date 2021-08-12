# Contrast Image

## Summary
Contrast image is the product of expanding the color distribution in the image and by doing so with the equalization on image's CDF, we will get more brighter / darker pixels which will give us the contrast in the image. lets explore that with Python & Open CV.

```python
import cv2
import numpy as np
import matplotlib.pyplot as plt

path_gorilla = "..files/gorilla.jpg"
gorilla = cv2.imread(path_gorilla)
gorilla_grey = cv2.cvtColor(gorilla,cv2.COLOR_BGR2GRAY)
plt.figure(num=0,figsize=(12,6))
plt.imshow(gorilla_grey,cmap='gray')
plt.title('Gorilla Gray-Scaled Image')
```
<p align="center">
  <img src="https://github.com/matanelg/OpenCV/blob/master/Canny-Edge-Detection/files/gorilla_gray.png" width="50%" height="50%" />
</p>

```python
histr = cv2.calcHist([gorilla_grey],[0],None,[256],[0,256])
plt.figure(num=1,figsize=(12,6))
plt.bar(list(range(0,256)),histr[:,0],align='center',color='b')
plt.xlim([0,256])
plt.xlabel('Pixels Value')
plt.ylabel('Frequency')
plt.title('Gray Scale Colors Distribution')
```
<p align="center">
  <img src="https://github.com/matanelg/OpenCV/blob/master/Contrast-Image/files/gorilla_distro.png" width="50%" height="50%" />
</p>

- We can see that most pixels in the image are darker around 40.
- We can see the high slops in ranges 0 ~ 40 and 170~200. 

Now our gold is to reduce the slops and expand the distro for receive more contrast.

```python
eq_gorilla = cv2.equalizeHist(gorilla_grey)
histr_eq = cv2.calcHist([eq_gorilla],[0],None,[256],[0,256]) # new distro
plt.figure(num=3,figsize=(12,6))
plt.bar(list(range(0,256)),histr_eq[:,0],align='center',color='b')
plt.plot(histr,color='r')
plt.legend(['Before Equalization','After Equalization'])
plt.xlim([0,256])
plt.xlabel('Pixel Value')
plt.ylabel('Frequency')
plt.title('Gray Scale Image Distribution')
```
<p align="center">
  <img src="https://github.com/matanelg/OpenCV/blob/master/Contrast-Image/files/gorilla_new_distro.png" width="50%" height="50%" />
</p>

- We can see the distribution expand, the pick around 170 shift right around 230 which give more bright pixels in the new image.
- We can see the slopes are more moderate all over the image.
​
```python
plt.figure(num=4,figsize=(12,6))
plt.imshow(eq_gorilla,cmap='gray')
```
​<p align="center">
  <img src="https://github.com/matanelg/OpenCV/blob/master/Contrast-Image/files/contrast_image.png" width="50%" height="50%" />
</p>



