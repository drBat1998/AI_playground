Title: 10 - lists tuples and dictionaries
Author: [[DigitalSreeni]]
Tags: #python #youtube 


# Notes
``` python
b = [1,2,3,4,5,6]
# it is always start with 0.

b[0] # 1
b[1] # 2

b.append(1)
b[2:4]
# list[from value : to value, but not include it]
```
tuple can not be changed
``` python
t = (1,23,4)
t[1] = 2
TypeError: 'tuple' object does not support item assignment
AttributeError: 'tuple' object has no attribute 'append'

```
We can convert between tuple and list
```python
l =list(t)
t = tuple(l)
```

``` python
two_dem_list = [[2,3],[3,4]]
two_dem_list *2
# [[2, 3], [3, 4], [2, 3], [3, 4]]

```
How do we do the math?
NUMPY

# Links
https://youtu.be/c83l59sx6tU?si=c4ZWtveVGRjhblXZ
next: [[11 - numpy arrays]]
