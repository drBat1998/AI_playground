Title: 21 - Scratch assay analysis with just 5 lines code in Python
Author: [[DigitalSreeni]]
Tags: #youtube #python 


# Notes
``` python
from skimage.filters.rank import entropy
from skimage.morphology import disk
from skimage import io
from skimage.filters import threshold_otsu
import matplotlib.pyplot as plt
import numpy as np
import glob


time = 0
time_list = []
area_list = []
path = "/content/drive/MyDrive/data/*"

for file in glob.glob(path):
  img = io.imread(file,as_gray=True)
  entropy_img = entropy(img, disk(5)) # entropy calculation that tells us the difference between the clean and cell-filled area
  thresh = threshold_otsu(entropy_img)
  # create a numerical threshold for the entropy
  binary = entropy_img <= thresh
  # extract the data into True False fashion
  scratch_area = np.sum(binary==1)
  # calculate 
  print(time, scratch_area)
  time_list.append(time)
  area_list.append(scratch_area)
  time +=1
  

plt.plot(time_list, area_list)
```
# Links
next: [[22 - Denoising microscope images in Python]]
link: https://youtu.be/jcUx-TQpcM8?si=YMWs0E-EiroCqxRC