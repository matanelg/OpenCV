# Corner Detection

## Summary
  
  Corner Detection by Shi-Tomase with open cv examples.

  Example 1. detect corners on flat chessboard.

  Example 2. detect roi of text in an image. 


```python
import  cv2   
import numpy as np
import matplotlib.pyplot as plt
```


```python
flat_chess = cv2.imread("../Files/flat_chess.png")

flat_chess = cv2.cvtColor(flat_chess,cv2.COLOR_BGR2RGB)

plt.figure(1)
plt.imshow(flat_chess)
```

<p align="center">
  <img src="https://github.com/matanelg/OpenCV/blob/master/Corner-Detection/Files/flat_chess.png">
</p>

```python
flat_chess_gray = cv2.cvtColor(flat_chess,cv2.COLOR_RGB2GRAY)

corners =cv2.goodFeaturesToTrack(image=flat_chess_gray, 
                                 maxCorners=64, 
                                 qualityLevel=0.01, 
                                 minDistance=10)

flat_chess_new = flat_chess.copy()

corners = np.int0(corners)

for i in corners:
    x,y = i.ravel()
    cv2.circle(flat_chess_new,(x,y),3,255,-1)

plt.figure(2)
plt.imshow(flat_chess_new)
```

<p align="center">
  <img src="https://github.com/matanelg/OpenCV/blob/master/Corner-Detection/Files/flat_chess_new.png">
</p>

```python
img = cv2.imread("../Files/img.png")

img = cv2.cvtColor(img,cv2.COLOR_BGR2RGB)

plt.figure(3)
plt.imshow(img)
```

<p align="center">
  <img src="https://github.com/matanelg/OpenCV/blob/master/Corner-Detection/Files/img.png">
</p>

```python
img_gray = cv2.cvtColor(img,cv2.COLOR_RGB2GRAY)

corners =cv2.goodFeaturesToTrack(image=img_gray, 
                                 maxCorners=200, 
                                 qualityLevel=0.01, 
                                 minDistance=10)

corners = np.int0(corners)

x_lst,y_lst =[],[]

img_all_corners = img.copy()

for i in corners:
    x,y = i.ravel()
    x_lst.append(x)
    y_lst.append(y)
    cv2.circle(img_all_corners,( x,y ),3,255,-1)

plt.figure(4)
plt.imshow(img_all_corners)
```

<p align="center">
  <img src="https://github.com/matanelg/OpenCV/blob/master/Corner-Detection/Files/img_all_corners.png">
</p>

```python
values, counts = np.unique(corners[:,0,1], return_counts=True)

values_y = values[counts>=sorted(counts)[-4]] 

x_lst1,y_lst1 =[],[]

img_selected = img.copy()

for idx,val in enumerate(y_lst):
    if val in values_y:
        x_lst1.append(x_lst[idx])
        y_lst1.append(y_lst[idx])
        cv2.circle(img_selected,(x_lst[idx],y_lst[idx]),3,255,-1)

plt.figure(5)
plt.imshow(img_selected)
```

<p align="center">
  <img src="https://github.com/matanelg/OpenCV/blob/master/Corner-Detection/Files/img_selected.png">
</p>

```python
y_min,y_max = min(y_lst1),max(y_lst1)

x_min,x_max = min(x_lst1),max(x_lst1)

space = 5

img_new = img.copy()

cv2.rectangle(img_new, 
              pt1=(x_min-space,y_min-space), 
              pt2=(x_max+space,y_max+space), 
              color=(255,0,0),
              thickness=2)

plt.figure(6)
plt.imshow(img_new)
```

<p align="center">
  <img src="https://github.com/matanelg/OpenCV/blob/master/Corner-Detection/Files/img_new.png">
</p>

