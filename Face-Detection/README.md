# Face Detection

## Summary
Face Detection with open cv example.<br />
Using Viola-Jones Algorithm with Haar Cascades.<br />
Calling XML classifier from opencv pre-trained Cascade files.<br />
Detect face in any image.<br />

```python
​import  cv2   
import numpy as np
import matplotlib.pyplot as plt

path = 'your path to the image'
stef = cv2.cvtColor(cv2.imread(../files/),cv2.COLOR_BGR2RGB)

plt.figure(1)
plt.imshow(stef)
```
<p align="center">
  <img src="https://github.com/matanelg/OpenCV/blob/master/Face-Detection/files/stef.png" width="50%" height="50%" />
</p>

```python
classifier_path = 'your path to the classifier'
face_cascade = cv2.CascadeClassifier(classifier_path)
def detect_face(img):
	face_img = img.copy()
        face_rects = face_cascade.detectMultiScale(face_img,scaleFactor=1.2)
        for (x,y,w,h) in face_rects:
            cv2.rectangle(face_img,(x,y),(x+w,y+h),(255,0,0),10)
        return face_img

plt.figure(2)
plt.imshow(detect_face(stef))
```
<p align="center">
  <img src="https://github.com/matanelg/OpenCV/blob/master/Face-Detection/files/detect.png" width="50%" height="50%" />
</p>




