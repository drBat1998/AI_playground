Title: 15 - Python Classes
Author: [[DigitalSreeni]]
Tags: #youtube #python 


# Notes
``` python
class Cell:
  pass
  
cell_1 = Cell() #instence 1
cell_2 = Cell() #instence 2

print(cell_1, cell_2) # two different objects
# <__main__.Cell object at 0x7b2f6cc61f70> <__main__.Cell object at 0x7b2f6cc61610>

```
``` python
from math import sqrt

class Cell_real:
  def __init__(self, name, x, y):
    self.name = name
    self.x = x
    self.y = y


  def cell_distance(self, other_cell):
    distance = sqrt((self.x - other_cell.x)**2 + (self.y - other_cell.y)**2)
    return distance
    

cell_1 = Cell_real("cell_one", 0,0)
cell_2 = Cell_real("cell_two", 10,10)
cell_3 = Cell_real("cell_tree", 20,20)

distance_1 = cell_1.cell_distance(cell_2)
print(distance_1)
# 14.142135623730951

```
# Links
next : [[16 - Understanding digital images for Python processing]]
https://youtu.be/ENPECc0n7XI?si=mfn8wrZG_N_63HOl