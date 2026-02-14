Title: Cellpose
tags: #atomic_note #python 


# Notes
the general algorithm
1. Generate an auxiliary representation for the masks
2. Horizontal and vertical gradients
3. Classify pixels as inside or outside of the cell mask

U-net architecture

for Mac 
``` python
python -m cellpose --dir path --gpu_device mps --use_gpu
```

# Cellpose 1
``` python
from cellpose import models, plot
import tifffile as tiff
import numpy as np
import matplotlib.pyplot as plt

# ---- Load a 2D grayscale TIFF ----
img = tiff.imread("/content/drive/MyDrive/data/B2_01_1_3_GFP_001.tif")
assert img.ndim == 2, f"Expected 2D image, got shape {img.shape}"

# (Optional) normalize to 0–1 for display; Cellpose can handle uint16 directly
img_disp = img.astype(np.float32)
m = img_disp.max()
if m > 0:
    img_disp /= m

# ---- Configure Cellpose for 2D ----
# For grayscale 2D images use channels=(0,0)
channels = (0, 0)

model = models.Cellpose(gpu=True, model_type="nuclei")

masks, flows, styles, diams = model.eval(
    img,                # 2D array
    diameter=None,      # let Cellpose estimate; or set (e.g., 12)
    flow_threshold=None,
    channels=channels
)

# ---- Visualize segmentation ----
fig = plt.figure(figsize=(6,5))
try:
    # Many cellpose versions return flows as a list-like; show the first element
    flow_to_show = flows[0] if isinstance(flows, (list, tuple)) else flows
    plot.show_segmentation(fig, img_disp, masks, flow_to_show, channels=channels)
except Exception:
    # Fallback: simple mask overlay if flow format differs
    overlay = plot.mask_overlay(img_disp, masks)
    plt.imshow(overlay)
    plt.title("Mask overlay")
    plt.axis("off")

plt.tight_layout()
plt.show()
```
# Links
[[305 - What is Cellpose algorithm for segmentation?]]
https://youtu.be/DL-j-hPFixk?si=LPCpDV3OPJhxPaor
https://github.com/MouseLand/cellpose