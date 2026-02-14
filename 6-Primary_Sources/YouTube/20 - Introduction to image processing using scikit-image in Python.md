Title: 20 - Introduction to image processing using scikit-image in Python
Author: [[DigitalSreeni]]
Tags: #youtube #python 


# Notes
```python
from skimage import io
from skimage.transform import rescale, resize, downscale_local_mean

from skimage.filters import roberts, sobel, scharr, prewitt

# edge detectors
from skimage.feature import canny
edge_canny = canny(img, sigma = 2)
plt.imshow(edge_canny)


import matplotlib.pyplot as plt


```

```python
# deconvolution
from skimage import restoration
import numpy as np
psf = np.ones((3,3))/9
deconvolved, _ = restoration.unsupervised_wiener(img, psf)

plt.imshow(deconvolved)
```

point spread function
``` python
def gkern(kernlen = 21, nsig =2):
  lim = kernlen//2 + (kernlen%2)/2
  x = np.linspace(-lim, lim, kernlen+1)
  kern1d = np.diff(st.norm.cdf(x))
  kern2d = np.outer(kern1d, kern1d)
  return kern2d/kern2d.sum()
```

real life situation
``` python
import matplotlib.pyplot as plt
from skimage import io, restoration
from skimage.filters.rank import entropy
from skimage.morphology import disk
from skimage.filters import try_all_threshold, threshold_otsu
# entropy
entr_img = entropy(img, disk(3))
# try all threshold
fig, ax = try_all_threshold(entr_img, figsize=(10,8))
# chose on of the threshold

thresh = threshold_otsu(entr_img)

binary = entropy <= thresh

plt.imshow(binary, cmap = "gray")
print("The presnet white region is: ", (np.sum(binary==1)*100/np.sum(binary == 0) + np.sum(binary == 1)))
```
# Links
next: [[21 - Scratch assay analysis with just 5 lines code in Python]]
https://youtu.be/CTOURPZftuU?si=8z0kKrjYh-ykdXV1