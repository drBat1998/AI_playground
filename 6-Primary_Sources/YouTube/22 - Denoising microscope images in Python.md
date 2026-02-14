Title: 22 - Denoising microscope images in Python
Author: [[DigitalSreeni]]
Tags: #youtube #python 


# Notes
A Gaussian kernel is a matrix (filter) used in image processing to blur or smooth an image, based on the Gaussian (normal) distribution function. The values in the kernel are highest at the center and decrease smoothly toward the edges. == hill.

```python
from skimage import io
from scipy import ndimage as nd
import matplotlib.pyplot as plt

img = io.imread("/content/drive/MyDrive/data/1.png",as_gray=True)


# Use a range for sigma (e.g., from 1 to 6)
for sigma in range(1, 6):   # will use 1, 2, 3, 4, 5
    gaussian_img = nd.gaussian_filter(img, sigma=sigma)
    
    plt.figure(figsize=(4, 4))
    plt.title(f"Gaussian filter, sigma={sigma}")
    plt.imshow(gaussian_img, cmap='gray')
    plt.axis('off')
    plt.show()
    
    
    

# Try different filter sizes
for size in [3, 5, 7]:
    median_img = nd.median_filter(img, size=size)
    
    plt.figure(figsize=(4, 4))
    plt.title(f"Median filter, size={size}")
    plt.imshow(median_img, cmap='gray')
    plt.axis('off')
    plt.show()
```
Instead of looking only at a pixel’s local neighborhood (like Gaussian or median), NLM looks across the entire image for similar patterns (patches).
- Each pixel is replaced by a weighted average of many pixels in the image.
- The weights depend on how similar the surrounding patches are.
- “Non-local” means it can use information from far away parts of the image, not just nearby.
``` python
import numpy as np
from skimage import data, img_as_float
from skimage.restoration import denoise_nl_means, estimate_sigma

# Example image (convert to float for restoration functions)
img = img_as_float(data.astronaut())

# Estimate noise standard deviation (per channel)
sigma_est = np.mean(estimate_sigma(img, multichannel=True))
print(f"Estimated sigma = {sigma_est:.4f}")

# Apply Non-Local Means denoising
nlm = denoise_nl_means(img,
                       h=1.15 * sigma_est,   # filter strength
                       fast_mode=False,      # higher quality, slower
                       patch_size=5,         # size of patches used for comparison
                       patch_distance=3,     # max distance to search patches
                       multichannel=True)    # image has RGB channels

```

Gaussian = “average nearby pixels.”
Median = “take middle value nearby.”
NLM = “find pixels that look like me anywhere in the image, and average them.”
# Links
Next: [[23 - Histogram based image segmentation in Python]]
link: https://youtu.be/2PrzKWkqOtU?si=rFaF9ZeRxmjtIdK2