Title: 17 - Reading images in Python
Author: [[DigitalSreeni]]
Tags: #youtube #python 


# Notes
matplotlib
``` python
import matplotlib.image as mpimg
import matplotlib.pyplot as plt

img = mpimg.imread("/content/1330557.jpg")
print(type(img))
plt.imshow(img)
```
plt.imshow(img) ! plt.imshow() not plt.show()

skiimage
``` python
from skimage import io

image = io.imread("/content/1330557.jpg")
print(type(image))
```
opencv-python
- different colour plt.imshow()
- normal in cv.2imshow()
``` python
import cv2
img = cv2.imread("/content/1330557.jpg")
img
```

czi file
- proprietary image for Zeiss microscope
- have another dimension
``` python
!pip install czifile
import czifile
img = czifile.imread("image.czi")
```
OME-TIFF
``` python
!pip install apeer-ometiff-library
from apeer_ometiff_library import io

(pic2, omexml) = io.read_ometiff("image.ome.tiff")
```
glob
``` python
import glob 
import cv2

path = "image/data/*"

for file in glob.glob(path):
  print(file)
  a = cv2.imread(file)
  print(a)
```
# Links
next: [[18 - Image processing using pillow in Python]]
https://youtu.be/52pMFnkDU-4?si=nF-Qcxej6gH5kW9s