Title: 04 - What is a digital image?
Author: [[DigitalSreeni]]
Tags: #python #youtube 


# Notes
RGB - red green blue, have tree values for each pixel
Every time when you do some changes inside softwere like ImegeJ some mathematical formula apply to the values. 
``` python
import cv2

img = cv2.imread("images/test_image.jpg", 1) # 1 - for RGB, 0 - for black and white

cv2.imshow("pic", img)
print(img.shape)

```
# Links
https://youtu.be/_xIcIrdIqlA?si=SM8F2H_as-K5GH6_

next : [[05 - What is Python?]]
[[06 - Python basics - IDE & operators]]
[[07 - Python basics - logical operators and basic math]]
[[08 - A warning about round off errors in Python]]