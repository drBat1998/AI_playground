Title: ZEISS arivis
Author: [[ZEISS arivis]]
Tags: #programming #youtube 


# Notes
## 2. What is digital image processing?
Image has minimum x and y axes; in addition, it consists of values that represent colour. 
A 3D image has a z-axis as well. 
A pixel in a digital image has a specific value based on the bit depth.
![[Screenshot 2025-06-27 at 11.56.29.png]]
Digital image processing involves the manipulation of pixel values using an algorithm.
# 3.
The basic operation in ImageJ is to convert to an 8 or 16-bit picture; however, you lose colour values. 


# 4. 
```python
from skimage import io, filters
from matplotlib.pyplot as plt

img = io.imread("pathway")
gaussian_img = filters.guassian(img, sigma =2)
plt.imshow(gaussian_img)
```

# 6
```python
!python -V
```

# 9
scikit-image
opencv-python

numpy
pandas

matplotlib

scipy
tesnorflow
seaborn
# 12 list
```python
a = [1,2,3,4]
b = [2,3, "apple", "bannana"]

print(b[2]) # print apple

c = a + b # you get big list consit of all values.
b.append("grape")

# when you slice data from the list first value include in slice but last does not.
b[1:3] # print 3, "apple"
```

# 13 Tuples
```python
# tuples can not be changed 
# In case of image, the size of the image is tuple, but information about pixels are lists.
a = (1,2,3,4)
```
# 14. Dictionaries
```python

b = {'list': "value", 'shit': 23}
```
# 15 Numply arrays

```python 
c = np.array(a)
c * 5 # all values would be multiply by 5

```
if array have different demention size you can not perform any miningfull calculation.

# 17
```python
a = 10
b = 10

if a < b and b >c:
	print("Small")
elif a == b or b >c:
	print("Equal")
else:
	print("Big")
```
# 18
```python
count = 0
while count >10:
	print(count)
	if count == 5:
	break
	count = count+1
	
```

# 19
```python
# for each point of data do something
a = [1,2,3,4,5]

for i in a:
	print(i)

for num in range(0, 20):
	if num%2 == 0:
		print()
	else:
		print()
		
```

# 20
```python

def my_function():
	print("Shit")
```

# 21
Lambda function
```python
a = lambda x : x**2 # square the imput
print(a(5)) 

b = lambda x,y : x+y # sum the two number
```
Difficult function with lambda
```python
# S = ut +1/2 a*t**2
def distance_eqn(u,a):
	lambda t: u*t +((1/2)*a*t**2)

dict = distance_eqn(10,2)
print(dict(20))
```
# 22
```python
from skimage import io, img_as_float, img_as_ubyte
img = io.imread("image/test.tif")
# y - hight
# x - weight
# c - RGB 

# convert wit img_to_float better than np version, due to scaling the number.
img_2 = img_as_float(img) # to float
img_3 = img_as_ubyte(img_2) # to uint8

#CV1 read the image in # BGR not in # RGB
```
# 23
# 24
# 25
# Links
https://youtu.be/7uE6hypji0o?si=Ky2fTXCk-YpmaAlS