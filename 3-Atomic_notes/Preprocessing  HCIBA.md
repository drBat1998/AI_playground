Title: Preprocessing  HCIBA
tags: #atomic_note


# Notes
``` python
import os
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
from tifffile import imread, imwrite
from skimage import exposure, filters, morphology, measure, util, segmentation, restoration
from scipy import ndimage as ndi
```

``` python
# Change this to your own image (16-bit TIFF recommended)
IMAGE_PATH = ''  # e.g., '/content/PlateA_W01A_F01_Z01_CDAPI.tif'
DATA_DIR = Path('.')
```

``` python
assert IMAGE_PATH, 'Set IMAGE_PATH to a TIFF file path.'
img = imread(IMAGE_PATH)
print('Shape:', img.shape, 'Dtype:', img.dtype)
print('Min/Max:', int(img.min()), int(img.max()))
print('Mean/Std:', float(img.mean()), float(img.std()))

# Show the image
plt.figure(figsize=(5,5))
plt.imshow(img)  # set cmap='gray' if you prefer grayscale
plt.title('Raw image')
plt.axis('off')
plt.show()

# Histogram (contrast distribution)
plt.figure(figsize=(6,4))
plt.hist(img.ravel(), bins=256)
plt.title('Histogram of intensities')
plt.xlabel('Pixel value')
plt.ylabel('Count')
plt.show()
```

### 1. File organization & metadata
### 2. Flat-field (shading) correction
[[117 - Shading correction using rolling ball background subtraction]]
[[basicpy]]
``` python
# pip install BaSiCPy tifffile aicsimageio
import numpy as np, tifffile as tiff
from basicpy import BaSiC

# 1) Load a representative stack of images (e.g., 50–200 FOVs across the plate)
stack = np.stack([tiff.imread(p) for p in training_paths])  # shape: (N, H, W)

# 2) Fit BaSiC model to estimate flatfield & darkfield
basic = BaSiC(max_iters=200, smoothness_flat=1e6, smoothness_dark=1e6)
flatfield, darkfield = basic.fit(stack)

# 3) Apply correction to any image (single FOV)
img = tiff.imread("A01_s1_ch1.tif").astype(np.float32)
corrected = basic.transform(img, flatfield, darkfield)  # same shape as img

# 4) (Optional) normalise/clip and save
corrected = np.clip(corrected, 0, None).astype(np.float32)
tiff.imwrite("A01_s1_ch1_corrected.tif", corrected)
```
### 3. Background correction
### 4. Denoising
### 5. Deconvolution (optional but valuable)
### 6. Z-stack projection
### 7. Channel registration
### 8. Intensity normalization
### 9. Segmentation readiness
# Links
[[High-content image-based analysis]]
