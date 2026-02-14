Title: 18 - Image processing using pillow in Python
Author: [[DigitalSreeni]]
Tags: #youtube #python 


# Notes
basic work
``` python
from PIL import Image

img = Image.open("/content/drive/MyDrive/data/3b47a8ae-0ea9-47db-a0f0-502999d429b5.png")

print(img.format)
# PNG

print(img.mode)
#RGB
print(img.size)
# (1024, 1024)

small_img = img.resize((200, 300))
small_img.save("/content/drive/MyDrive/data/small.png")
# it didn't crop, it squise it
```

cropped 
```python
cropped_img = img.crop((0,0, 300,300))
# first cordinate and second cordinate

cropped_img.save("/content/drive/MyDrive/data/croped.png")

img90 = img.rotate(90)
```
# Links
next: [[19 - image processing using scipy in Python]]
https://youtu.be/uDNqNv2N-pY?si=mqTCQBDaRgep2c7r
