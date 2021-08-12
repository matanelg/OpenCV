# Canny Edge Detection

## Summary   
Canny Edge Detection with open cv example.<br/>
Detect object's edges in the image.

```python
import cv2
import numpy as np
import matplotlib.pyplot as plt
```

```python
img = cv2.imread(path)
img = cv2.cvtColor(img,cv2.COLOR_BGR2RGB)
plt.figure(1)
plt.imshow(img)
```
<p align="center">
  <img src="https://github.com/matanelg/OpenCV/blob/master/Canny-Edge-Detection/files/01.png" width="50%" height="50%" />
</p>

```python
canny = cv2.Canny(img,127,127)
plt.figure(2)
plt.imshow(canny,cmap='gray')
```
<p align="center">
  <img src="https://github.com/matanelg/OpenCV/blob/master/Canny-Edge-Detection/files/02.png" width="50%" height="50%" />
</p>

```python
med_val = np.median(img)
lower = int(max(0,0.7*med_val))
upper = int(min(255,1.3*med_val))
canny1 = cv2.Canny(img,lower,upper)
plt.figure(3)
plt.imshow(canny1,cmap='gray')
```
<p align="center">
  <img src="https://github.com/matanelg/OpenCV/blob/master/Canny-Edge-Detection/files/03.png" width="50%" height="50%" />
</p>

```python
blurred_img = cv2.blur(img,ksize=(5,5))
plt.figure(4)
plt.imshow(canny2,cmap='gray')
```
<p align="center">
  <img src="https://github.com/matanelg/OpenCV/blob/master/Canny-Edge-Detection/files/04.png" width="50%" height="50%" />
</p>


