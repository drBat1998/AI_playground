Title: 29 - Key points, detectors and descriptors in openCV
Author: [[DigitalSreeni]]
Tags: #youtube #python 

[[openCV]]
# Notes
The key point is a region of interest
The key detectors detect the point, and the key descriptor describes it. 
### HARRIS corner

``` python
#HARRIS corner
import cv2
import numpy as np

img = cv2.imread("file/grains.jpg")
gray = cv2.cvtColor(img, cv2.COLOR_BGR2GRAY)

gray_float = np.float32(gray)

harris = cv2.cornerHarris(gray_float,2,3,0.04)

img[harris>0.01*harris.max()] = [255,0,0]
```
### Shi-Tomasi Corner Detector & Good Features to Track
```python
import cv2
import numpy as np

img = cv2.imread('images/grains.jpg')
gray = cv2.cvtColor(img,cv2.COLOR_BGR2GRAY)

#input image, #points, quality level (0-1), min euclidean dist. between detected points
corners = cv2.goodFeaturesToTrack(gray,50,0.05,10)
corners = np.int0(corners)   #np.int0 is int64

for i in corners:
    x,y = i.ravel()   # Ravel Returns a contiguous flattened array.
#    print(x,y)
    cv2.circle(img,(x,y),3,255,-1)  #Draws circle (Img, center, radius, color, etc.)

```


# Links
next: [[30 - Image registration using homography in openCV]]
link: https://youtu.be/DZtUt4bKtmY?si=Pxe-2oHoR2DNOja_