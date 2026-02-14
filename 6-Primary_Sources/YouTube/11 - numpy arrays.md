Title: 11 - numpy arrays
Author: [[DigitalSreeni]]
Tags: #python #youtube 


# Notes
```python
import numpy

# you can do the math without numpy but it is difficult
square = [i**2 for i in a if i%2==0]

c = [[1,2,3],[3,4,5]]
c= np.array(c)
# array([[1, 2, 3],
#       [3, 4, 5]])
c *2
#array([[ 2,  4,  6],
#       [ 6,  8, 10]])

zero_numpy = np.zeros((2,4))
#array([[0., 0., 0., 0.],
       [0., 0., 0., 0.]])
       
ones_numpy = np.ones((5,5))

full_numpy = np.full((3,4), "Hell")
#array([['Hell', 'Hell', 'Hell', 'Hell'],
#       ['Hell', 'Hell', 'Hell', 'Hell'],
#       ['Hell', 'Hell', 'Hell', 'Hell']], dtype='<U4'
```

slicing
np.array[columns, rows]

``` python
b = a[:2] # print first two rows

c = a[:,:2] # all rows,but first two columns

d = a[1,:2] # one specific rows(second), two columns

```
math numpy
``` python
x = np.array([[1,2],[3,4]], dtype=np.float128)
y = np.array([[5,6],[7,8]], dtype=np.float128)

print(np.multiply(x,y))
[[ 5. 12.]
 [21. 32.]]

print(np.add(x,y))
 [[ 6.  8.]
 [10. 12.]]
 
x.T # change row and columns place
array([[1., 3.],
       [2., 4.]], dtype=float128)
```
broadcasting
``` python

a = np.array([[1,2,3],[4,5,6],[7,8,9],[10,11,12]])
b = np.array([2,0,2])
c = a+b
print(c)
[[ 3  2  5]
 [ 6  5  8]
 [ 9  8 11]
 [12 11 14]]

```
# Links
https://youtu.be/4uFs1qouPEI?si=hZY9ODM6e-wtIrxT