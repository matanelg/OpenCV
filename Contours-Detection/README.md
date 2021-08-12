# Contours Detection

## Summary
Contours Detection with open cv example.<br />
Detect contours around objects in an image.

```python
import  cv2   
import numpy as np
import matplotlib.pyplot as plt

img = cv2.imread(../files/01.png,0)

plt.figure(1)
plt.imshow(img,cmap='gray')
```
<p align="center">
  <img src="https://github.com/matanelg/OpenCV/blob/master/Contours-Detection/files/01.png" width="50%" height="50%" />
</p>

```python
contours,hierarchy = cv2.findContours(img, cv2.RETR_CCOMP, cv2.CHAIN_APPROX_SIMPLE)
external_contours = np.ones(img.shape)
for i in range(len(contours)):
	if hierarchy[0,i,3]==-1:
    		cv2.drawContours(external_contours, contours, i, 255,-1)

plt.figure(2)
plt.imshow(external_contours,cmap='gray')
```
<p align="center">
  <img src="https://github.com/matanelg/OpenCV/blob/master/Contours-Detection/files/02.png" width="50%" height="50%" />
</p>

```python
internal_contours = np.ones(img.shape)
for i in range(len(contours)):
	if hierarchy[0,i,3]!=-1:
    		cv2.drawContours(internal_contours, contours, i, 255,-1)

plt.figure(3)
plt.imshow(internal_contours,cmap='gray')
```
​<p align="center">
  <img src="https://github.com/matanelg/OpenCV/blob/master/Contours-Detection/files/03.png" width="50%" height="50%" />
</p>



