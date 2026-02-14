Title: 16 - Understanding digital images for Python processing
Author: [[DigitalSreeni]]
Tags: #youtube #python 


# Notes
Image in Python is a numpy array consisting of three values for each pixel: Red, Green, and Blue. 
In order to work with the image, we shall use matplotlib and numpy:
``` python
import matplotlib.image as mpimg
import numpy as np
import matplotlib.pyplot as plt
```

```python
img = mpimg.imread("/content/1330557.jpg")   # read

random_image = np.random.random([500,500])

plt.imshow(random_image)
```

dtypes
uint8 0 to 255
unit16 from 0 to 65535
unit32 from 0 to ((2 ** 32)-1)
float = -1 to 1 or 0 to 1
int8 = -128 to 127
int16 = -32768 to 32768
int32 = -2 ** 31 to 2 ** 31 -1

img_as_float - 64-bit floating point
img_as_ubyte - 8-bit init
img_as_uint - 16-bit uint
img_as_int - 16-biy int
# Links
next: [[17 - Reading images in Python]]
https://youtu.be/Ijc-9L2iXEc?si=sJXCIsMBqMI-wKa4