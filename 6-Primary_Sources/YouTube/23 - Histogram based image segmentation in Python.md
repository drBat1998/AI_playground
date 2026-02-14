Title: 23 - Histogram based image segmentation in Python
Author: [[DigitalSreeni]]
Tags: #youtube #python 


# Notes
Histogram-based image segmentation in Python
- segmentation based on gray level. 
``` python
import numpy as np
import matplotlib.pyplot as plt
from skimage import io, img_as_float, img_as_ubyte
from skimage.restoration import denoise_nl_means, estimate_sigma
from skimage.color import rgb2gray

# --- Load as float in [0,1]
img = img_as_float(io.imread("/content/drive/MyDrive/data/RAW_EM-p-800.png"))

# --- Handle per image type
ch_axis = -1 if img.ndim == 3 else None

# --- Estimate noise (mean across channels if RGB)
sigma_est = np.mean(estimate_sigma(img, channel_axis=ch_axis))

# --- NLM denoise with correct channel_axis
nlm = denoise_nl_means(
    img,
    h=1.15 * sigma_est,
    fast_mode=True,
    patch_size=5,
    patch_distance=3,
    channel_axis=ch_axis
)

# --- Convert to 8-bit
denoise_ubyte = img_as_ubyte(nlm)

# --- Build a 2D intensity image for thresholding
if denoise_ubyte.ndim == 3:
    # rgb2gray returns float [0,1]; scale to 0–255 uint8 for your thresholds
    gray = (rgb2gray(denoise_ubyte) * 255).astype(np.uint8)
else:
    gray = denoise_ubyte

# --- Masks (2D)
segm1 = (gray <= 55)
segm2 = (gray > 55) & (gray <= 100)
segm3 = (gray > 150) & (gray <= 200)

# --- Color canvas (H,W,3) uint8
all_segments = np.zeros((*gray.shape, 3), dtype=np.uint8)

# Paint with RGB triplets
all_segments[segm1] = (255, 0, 0)   # red
all_segments[segm2] = (0, 255, 0)   # green
all_segments[segm3] = (0, 0, 255)   # blue

# --- (Optional) histogram & quick view
plt.figure(); plt.hist(gray.ravel(), bins=32); plt.title("Histogram (gray)")
plt.figure(); plt.imshow(all_segments); plt.axis('off'); plt.title("Segments")
plt.show()


```
# Links
next: [[24 - Random Walker segmentation in Python]]
https://youtu.be/kIVk0IhDMwY?si=qgCMceAX4STVFYcN