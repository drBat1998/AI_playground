Title: 19 - image processing using scipy in Python
Author: [[DigitalSreeni]]
Tags: #youtube #python 


# Notes
``` python
from scipy import misc
from scipy import ndimage

from skimage import io, img_as_float

img = io.imread("/content/drive/MyDrive/data/1.png")

g_f = ndimage.gaussian_filter(img, sigma = 3)

ndimage.filter()

```
# Links
next: [[20 - Introduction to image processing using scikit-image in Python]]
https://youtu.be/s_hDL2fGvow?si=huzYM5gfqqO6T-Hq