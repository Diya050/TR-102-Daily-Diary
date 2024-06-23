# Daily Diary: Week 1

## Day 1

- ### Overview of NumPy:

  NumPy is a fundamental package for scientific computing in Python, essential for data analysis due to its efficient handling of large, multi-dimensional arrays and its extensive collection of mathematical functions. Key features include:
    - **N-Dimensional Arrays (ndarray):** Fast, flexible containers for large datasets.
    - **Mathematical Functions:** Broad range of functions for array operations.
    - **Broadcasting:** Simplifies arithmetic operations on arrays of different shapes.
    - **Linear Algebra:** Tools for matrix operations and more.
    - **Random Number Generation:** Useful for simulations and statistical modeling.
    - **Integration:** Seamlessly works with libraries like Pandas, SciPy, and Matplotlib.

- ### Importance in Data Analysis

    - **Performance:** Optimized for speed and efficiency.
    - **Ease of Use:** User-friendly syntax for complex tasks.
    - **Data Manipulation:** Powerful tools for preparing and cleaning data.
    - **Foundation for Other Libraries:** Underpins many scientific and machine learning libraries.
    - **Community and Ecosystem:** Extensive support and resources.

- ### Installing NumPy

   - For **Windows**,to install Python NumPy, go to your command prompt and type
```
pip install numpy
```
   - For **Ubuntu & Debian**,
```
sudo apt-get install python-numpy
OR
sudo pip3/pip install numpy
```
   - For **Fedora 22** and later:
```
sudo dnf install numpy
OR
sudo pip3/pip install numpy
```
   - For **Macports**, for Python 3.5 with Macports execute this command in a terminal:
```
sudo port install py35-numpy
```

- ### NumPy Creating Arrays

```python
import numpy as np
arr = np.array((1, 2, 3, 4, 5))
arr1 = np.array(['a', 'b', 'c'])

print(arr)  # [1 2 3 4 5]

print(arr1)  # ['a' 'b' 'c']
print(type(arr1))  # <class 'numpy.ndarray'>
```

- ### Dimensions in Arrays

  - **0-D Arrays:** 0-D arrays, or Scalars, are the elements in an array. Each value in an array is a 0-D array.
```python
import numpy as np
arr = np.array(42)
print(arr)  # 42
print(arr.ndim)  # 0
```
  - **1-D Arrays:** An array that has 0-D arrays as its elements is called uni-dimensional or 1-D array.
```python
import numpy as np
arr = np.array([1, 2, 3, 4, 5])
print(arr)  # [1 2 3 4 5]
print(arr.ndim)  # 1
```
  - **2-D Arrays:** An array that has 1-D arrays as its elements is called 2-D array.
```python
import numpy as np
arr = np.array([[1, 2, 3], [4, 5, 6]])
print(arr)
"""
[[1 2 3]
 [4 5 6]]
"""
print(arr.ndim)  # 2 
```
  - **3-D Arrays:** An array that has 2-D arrays (matrices) as its elements is called 3-D array.<br>
```python
import numpy as np
arr = np.array([[[1, 2, 3], [4, 5, 6]], [[1, 2, 3], [4, 5, 6]]])
print(arr)
print(arr.ndim)  # 3
```
  - **Higher Dimensional Arrays**: Arrays can be created of any dimension using `ndmin` attribute.
```python
import numpy as np
arr = np.array([1, 2, 3, 4], ndmin=5)
print(arr)
print('number of dimensions :', arr.ndim)
```

- ### NumPy Array Indexing

```python
import numpy as np
arr = np.array([1, 2, 3, 4])
print(arr[2] + arr[3])  # 7

arr = np.array([[1,2,3,4,5], [6,7,8,9,10]])
print('2nd element on 1st dim: ', arr[0, 1])  # 2

arr = np.array([[[1, 2, 3], [4, 5, 6]], [[7, 8, 9], [10, 11, 12]]])
print(arr[0, 1, 2])  # 6

arr = np.array([[1,2,3,4,5], [6,7,8,9,10]])
print('Last element from 2nd dim: ', arr[1, -1])  # 10
```
- ### NumPy Array Slicing

```python
import numpy as np
arr = np.array([1, 2, 3, 4, 5, 6, 7])
print(arr[1:5:2])  # [2 4]

arr = np.array([1, 2, 3, 4, 5, 6, 7])
print(arr[4:])  # [5 6 7]

arr = np.array([1, 2, 3, 4, 5, 6, 7])
print(arr[:4])  # [1 2 3 4]

arr = np.array([[1, 2, 3, 4, 5], [6, 7, 8, 9, 10]])
print(arr[1, 1:4])  # [7 8 9]

arr = np.array([[1, 2, 3, 4, 5], [6, 7, 8, 9, 10]])
print(arr[0:2, 2])  # [3 8]

```

## Day 2

- ### NumPy Data Types

```python
import numpy as np

arr = np.array([1, 2, 3, 4])
print(arr.dtype)  # int64

arr1=np.array(['apple', 'banana', 'cherry'])
print(arr1.dtype)  # <U6

dt = np.dtype('i4')
print(dt)  # int32

dt = np.dtype(np.int32)
print(dt)  # int32
```

- ### Structured Arrays

```python
import numpy as np

# defining data type object
dt = np.dtype([('name', '<U10'), ('age', 'i1'), ('salary', 'f4')])

# creating structured array
employee = np.array([('Sonal', 28, 30000.5), ('Jay', 30, 25000.0), ('Diya', 25, 100000.0)], dtype = dt)

print(employee)  # [('Sonal', 28,  30000.5) ('Jay', 30,  25000. ) ('Diya', 25, 100000. )]
print(employee['name'])  # ['Sonal' 'Jay' 'Diya']
```

- ### NumPy - Array Attributes(shape, reshape, itemsize, ndim)

```python
import numpy as np
arr = np.array([[1, 2, 3, 4], [5, 6, 7, 8]])
print(arr.shape)  # (2,4)

arr = np.array([1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12])
newarr = arr.reshape(4, 3)
print(newarr)

# dtype of array is int8 (1 byte)
import numpy as np
x = np.array([1,2,3,4,5], dtype = np.int8)
print (x.itemsize)

import numpy as np
arr = np.array([1, 2, 3, 4], ndmin=5)
print(arr)  # [[[[[1 2 3 4]]]]]
print(arr.ndim)  # 5
```
`Note:` Reshape function when tested using base attribute returns the original array, so it is a view.

- ### Flattening the arrays

```python
import numpy as np
arr = np.array([[1, 2, 3], [4, 5, 6]])
newarr = arr.reshape(-1)
print(newarr)
```
- ### NumPy - Array Creation Routines(empty, ones, zeros, full, eye)

```python
import numpy as np
arr = np.empty((3,2), dtype = int)
print(arr)

arr = np.ones((3,3), dtype = int)
print(arr)

arr = np.zeros((3,3), dtype = float)
print(arr)

arr = np.identity(3, dtype=int)
print(arr)

arr = np.full((2,3),20, dtype = int)
print(arr)

arr = np.eye(8, 7, k=1)
print(arr)
```

- ### NumPy Array Copy vs View
The main difference between a copy and a view of an array is that the copy is a new array, and the view is just a view of the original array. The copy owns the data and any changes made to the copy will not affect original array, and any changes made to the original array will not affect the copy. The view does not own the data and any changes made to the view will affect the original array, and any changes made to the original array will affect the view. Every NumPy array has the attribute base that returns None if the array owns the data. Otherwise, the base attribute refers to the original object.

```python
import numpy as np
arr = np.array([1, 2, 3, 4, 5])
x = arr.copy()
y = arr.view()
print(x.base)  # None (copy)
print(y.base)  # [1  2  3  4  5] (view)
arr[0] = 15
print(x)  # [1  2  3  4  5] (copy)
print(y)  # [15  2  3  4  5] (view)
```

- ### NumPy - Arithmetic Operations

```python
import numpy as np
x = np.array([[1,2],[3,4]], dtype=np.float64)
y = np.array([[5,6],[7,8]], dtype=np.float64)

# print(x + y)
print(np.add(x, y))

# print(x - y)
print(np.subtract(x, y))

# print(x * y)
print(np.multiply(x, y))

# print(x / y)
print(np.divide(x, y))

print(np.sqrt(x))
```


## Day 3

- ### NumPy - Array From Existing Data(asarray, frombuffer, fromiter)

```python
import numpy as np

l = [[1,2,3,4],[8,9]]  # using list
arr = np.asarray(l,  dtype = object)
print(arr)  # [list([1, 2, 3, 4]) list([8, 9])]

l=(1,2,3,4,5,6,7)  # using tuple
a = np.asarray(l)
print(type(a))  # <class 'numpy.ndarray'>
print(a)  # [1 2 3 4 5 6 7]

s = b'Hello World'
a = np.frombuffer(s, dtype = 'S1')
print(a)  # [b'H' b'e' b'l' b'l' b'o' b' ' b'W' b'o' b'r' b'l' b'd']

print(np.frombuffer(b'\x01\x02\x03', dtype = 'i1')  # [1 2 3]

list = range(5)
it = iter(list)

x = np.fromiter(it, dtype = float)
print(x) # [0. 1. 2. 3. 4.]
```

- ### NumPy - Array From Numerical Ranges(arange, linspace)
     - **Numpy.arange Function:** The Numpy arange function (sometimes called np.arange) is a tool for creating numeric sequences in Python. The NumPy arange function returns evenly spaced numeric values within an interval, stored as a NumPy array (i.e., an ndarray object). There are 4 parameters that we can modify:
        - start
        - stop
        - step
        - dtype
     - **Numpy.linspace Function:** The NumPy linspace function (sometimes called np.linspace) is a tool in Python for creating numeric
sequences. It’s somewhat similar to the NumPy arange function, in that it creates sequences of
evenly spaced numbers structured as a NumPy array.
        - start
        - stop
        - number of values
        - endpoint
        - return step value(retstep)

```python
import numpy as np

print(np.arange(1, 10, 2, dtype=float))  # [1. 3. 5. 7. 9.]

print(np.linspace(1,100, num=4, endpoint=False, retstep=True))  # (array([ 1.  , 25.75, 50.5 , 75.25]), 24.75)
```

- ### Iterating Arrays(1-D, 2-D, 3-D)

```python
import numpy as np

arr = np.array([1, 2, 3])  # 1-D array
for x in arr:
  print(x)

arr = np.array([[1, 2, 3], [4, 5, 6]])  # 2-D array
for x in arr:
  for y in x:
    print(y)

arr = np.array([[[1, 2, 3], [4, 5, 6]], [[7, 8, 9], [10, 11, 12]]])  # 3-D array
for x in arr:
  for y in x:
    for z in y:
      print(z)

```

- ### numpy.nditer function(order)
NumPy package contains an iterator object numpy.nditer. It is an efficient multidimensional iterator
object using which it is possible to iterate over an array. We can specify the order of iteration:
   - C Style: means row wise
   - F style: means column wise

```python
import numpy as np

a = np.arange(0,60,5)
a = a.reshape(3,4)

print ('Original array is:' )
print (a)
print ('\n')

print ('Sorted in C-style order:')
for x in np.nditer(a, order = 'C'):
  print (x),
print ('\n')

print ('Sorted in F-style order:')
for x in np.nditer(a, order = 'F'):
  print (x)
```


## Day 4

- ### numpy.nditer function(op_flags, flags, external_loop)
```python
import numpy as np
a = np.arange(0,60,5)
a = a.reshape(3,4)
print ('Original array is:')
print (a)
print ('\n')
for x in np.nditer(a, op_flags = ['readwrite']):
  x[...] = 2*x
print ('Modified array is:')
print (a)

'''Original array is:
[[ 0  5 10 15]
 [20 25 30 35]
 [40 45 50 55]]


Modified array is:
[[  0  10  20  30]
 [ 40  50  60  70]
 [ 80  90 100 110]]'''

a = np.arange(0,60,5)
a = a.reshape(3,4)
print('Original array is:')
print(a)
print('\n')
print('Modified array is:' )
for x in np.nditer(a, flags = ['external_loop'], order = 'F'):
  print(x)

`
'''Original array is:
[[ 0  5 10 15]
 [20 25 30 35]
 [40 45 50 55]]


Modified array is:
[ 0 20 40]
[ 5 25 45]
[10 30 50]
[15 35 55]'''

```
- ### Broadcasting Iteration

If two arrays are broadcastable, a combined nditer object is able to iterate upon them concurrently.
Assuming that an array a has dimension 3X4, and there is another array b of dimension 1X4, the
iterator of following type is used (array b is broadcast to size of a).

```python
import numpy as np

a = np.arange(0,60,5)
a = a.reshape(3,4)

print('First array is:')
print(a)
print('\n')

print('Second array is:')
b = np.array([1, 2, 3, 4], dtype = int)
print(b)
print('\n')

print('Modified array is:')
for x,y in np.nditer([a,b]):
  print("%d:%d" % (x, y),)

'''First array is:
[[ 0  5 10 15]
 [20 25 30 35]
 [40 45 50 55]]

Second array is:
[1 2 3 4]

Modified array is:
0:1
5:2
10:3
15:4
20:1
25:2
30:3
35:4
40:1
45:2
50:3
55:4'''

```
  
- ### Enumerated Iteration Using ndenumerate()

Enumeration means mentioning sequence number of somethings one by one. Sometimes we require
corresponding index of the element while iterating, the ndenumerate () method can be used for
those use cases.

```python
import numpy as np

arr = np.array([[1, 2, 3, 4], [5, 6, 7, 8]])
for idx, x in np.ndenumerate(arr):
    print(idx, x)

'''(0, 0) 1
(0, 1) 2
(0, 2) 3
(0, 3) 4
(1, 0) 5
(1, 1) 6
(1, 2) 7
(1, 3) 8'''

```
- ### numpy.logspace
This function returns an ndarray object that contains the numbers that are evenly spaced on a log
scale. 
```python
import numpy as np

a = np.logspace(1,10,num = 10, base = 2)
print(a)  # [   2.    4.    8.   16.   32.   64.  128.  256.  512. 1024.]
```

- ### Random Function(randint, rand, randn)
Python defines a set of functions that are used to generate or manipulate random numbers. This
particular type of functions is used in a lot of games, lotteries or any application requiring random
number generation.

```python
import numpy as np
a = np.random.rand(2,3)
b = np.random.randn(2,2)
c = np.random.randint(10,size=(3,2))

print(a)
print(b)
print(c)

'''[[0.89408006 0.66384241 0.29393314]
 [0.60898832 0.00642782 0.48096558]]

[[ 1.81134639 -0.90428606]
 [ 0.00276083  1.31003827]]

[[5 8]
 [4 6]
 [7 8]]
```

- ### Joining Arrays(concatenate(), stack(), hstack(), vstack())


## Day 5

- Joining Arrays(dstack())
- Splitting NumPy Arrays(array_split())
- Searching Arrays(where(), searchsorted())
- Sorting Arrays
- Filtering Arrays
- Adding / Removing Elements(numpy.resize(), numpy.append())


## Day 6

- Adding / Removing Elements(numpy.insert(), numpy.delete())
- NumPy Broadcasting(Arithmetic Operations)
- NumPy String Functions(add(), multiply(), center(), capitalize(), title(), lower(), upper(), strip(), split(), splitlines(), join(), replace(), encode(), decode())
- Trigonometric functions(sin, cos, tan, arcsin, arccos, arctan, degrees)


## Day 7

- Rounding Functions(numpy.around(), numpy.floor(), numpy.ceil())
- NumPy Matrix Library- numpy.matlib(zeros(), empty(), ones(), eye(), identity(), rand())
- NumPy Linear Algebra- numpy.linalg(numpy.dot(), numpy.vdot(), numpy.inner(), numpy.matmul(), numpy.linalg.det())
- NumPy Matrix Multiplication(numpy.multiply(), numpy.matmul())
- 'numpy.unique' function
- 'numpy.mean()' function
- Overview of Pandas and it's importance in Data Analysis
- Installing Pandas
- Series Data Structure(introduction and indexing)
