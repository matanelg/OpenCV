# Template Matching

## Summary
  
Template Matching with open cv example.
Detect basketball in an image. 

```python
import  cv2   
import numpy as np
import matplotlib.pyplot as plt
```

```python
full = cv2.cvtColor(cv2.imread("../files/full.png"),cv2.COLOR_BGR2RGB)
plt.figure(1)
plt.imshow(full)
```
<p align="center">
  <img src="https://github.com/matanelg/OpenCV/blob/master/Template-Matching/files/full.png">
</p>

```python
ball = full[45:175,580:705]
plt.figure(2)
plt.imshow(ball)
```
<p align="center">
  <img src="https://github.com/matanelg/OpenCV/blob/master/Template-Matching/files/ball.png">
</p>

```python
height, width, channel = ball.shape
full_copy = full.copy()
result = cv2.matchTemplate(full_copy, ball, cv2.TM_CCOEFF)
min_val, max_val, min_loc, max_loc = cv2.minMaxLoc(result)
top_left = max_loc
bottom_right = (top_left[0]+width,top_left[1]+height)
cv2.rectangle(img=full_copy, pt1=top_left, pt2=bottom_right, color=(255,0,0),thickness=5)
plt.figure(3)
plt.imshow(result)
```
<p align="center">
  <img src="https://github.com/matanelg/OpenCV/blob/master/Template-Matching/files/result.png">
</p>

```python
plt.figure(4)
plt.imshow(full_copy)
```
​<p align="center">
  <img src="https://github.com/matanelg/OpenCV/blob/master/Template-Matching/files/full_copy.png.png">
</p>




