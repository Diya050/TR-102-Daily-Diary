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
 [7 8]]'''

```

- ### Joining Arrays(concatenate(), stack(), hstack(), vstack())

Joining means putting contents of two or more arrays in a single array. We pass a sequence of arrays that we want to join to
the concatenate() function, along with the axis. If axis is not explicitly passed, it is taken as 0.

```python
import numpy as np
arr1 = np.array([[1, 2], [3, 4]])
arr2 = np.array([[5, 6], [7, 8]])
arr = np.concatenate((arr1, arr2), axis=1)
print(arr)
'''
[[1 2 5 6]
 [3 4 7 8]]
'''

arr = np.concatenate((arr1, arr2))
print(arr)
'''
[[1 2]
 [3 4]
 [5 6]
 [7 8]]
'''
```

```python
import numpy as np
arr1 = np.array([1, 2, 3])
arr2 = np.array([4, 5, 6])
arr = np.stack((arr1, arr2), axis=0)
print(arr)

'''
[[1 2 3]
 [4 5 6]]
'''

arr = np.stack((arr1, arr2), axis=1)
print(arr)

'''
[[1 4]
 [2 5]
 [3 6]]
'''

arr1 = np.array([1, 2, 3])
arr2 = np.array([4, 5, 6])
arr = np.hstack((arr1, arr2))
print(arr)

'''
[1 2 3 4 5 6]
'''

arr1 = np.array([1, 2, 3])
arr2 = np.array([4, 5, 6])
arr = np.vstack((arr1, arr2))
print(arr)

'''
[[1 2 3]
 [4 5 6]]
'''
```


## Day 5

- ### Joining Arrays(dstack())

```python
import numpy as np

arr1 = np.array([1, 2, 3])
arr2 = np.array([4, 5, 6])
arr = np.dstack((arr1, arr2))
print(arr)

'''
[[[1 4]
  [2 5]
  [3 6]]]
'''
```

- ### Splitting NumPy Arrays(array_split())

Splitting is reverse operation of Joining.Joining merges multiple arrays into one and Splitting breaks one array into multiple. We use array_split() for splitting arrays, we pass it the array we want to split and the number of splits.

```python
import numpy as np
arr = np.array([1, 2, 3, 4, 5, 6])
newarr = np.array_split(arr, 3)
print(newarr)  # [array([1, 2]), array([3, 4]), array([5, 6])]

arr = np.array([[1, 2, 3], [4, 5, 6], [7, 8, 9], [10, 11, 12], [13, 14, 15], [16, 17, 18]])
newarr = np.array_split(arr, 3, axis=0)
print(newarr)

'''
[array([[1, 2, 3],
       [4, 5, 6]]), array([[ 7,  8,  9],
       [10, 11, 12]]), array([[13, 14, 15],
       [16, 17, 18]])]
'''

newarr = np.array_split(arr, 3, axis=1)
print(newarr)

'''
[array([[1, 2, 3],
       [4, 5, 6]]), array([[ 7,  8,  9],
       [10, 11, 12]]), array([[13, 14, 15],
       [16, 17, 18]])]
[array([[ 1],
       [ 4],
       [ 7],
       [10],
       [13],
       [16]]), array([[ 2],
       [ 5],
       [ 8],
       [11],
       [14],
       [17]]), array([[ 3],
       [ 6],
       [ 9],
       [12],
       [15],
       [18]])]
'''
```

- ### Searching Arrays(where(), searchsorted())

```python
import numpy as np

arr = np.array([1, 2, 3, 4, 5, 6, 7, 8])
x = np.where(arr%2 == 0)
print(x)  # (array([1, 3, 5, 7]),)

arr = np.array([6, 7, 8, 9])
x = np.searchsorted(arr, 9)
print(x)  # 3
```

- ### Sorting Arrays

```python
import numpy as np
arr = np.array([[3, 2, 4], [5, 0, 1]])
print(np.sort(arr))

'''[[2 3 4]
 [0 1 5]]'''

arr = np.array(['banana', 'cherry', 'apple'])
print(np.sort(arr))  # ['apple' 'banana' 'cherry']
```

- ### Filtering Arrays

Getting some elements out of an existing array and creating a new array out of them is called
filtering. 

```python
import numpy as np

arr = np.array([41, 42, 43, 44, 45])
newarr = np.array([], dtype=int)
for x in arr:
    if x > 42:
        newarr = np.append(newarr, x)
    
print(newarr)  # [43 44 45]
```

- ### Adding / Removing Elements(numpy.resize(), numpy.append())

```python
import numpy as np
a = np.array([[1,2,3],[4,5,6]])
print('Original array:')
print(a)
print('\n')
print('The shape of original array:')
print(a.shape)
print('\n')

print( 'Resize the second array:')
b = np.resize(a,(3,3))
print(b)

'''Original array:
[[1 2 3]
 [4 5 6]]

The shape of original array:
(2, 3)

Resize the second array:
[[1 2 3]
 [4 5 6]
 [1 2 3]]'''

a = np.array([[1,2,3],[4,5,6]])
print ('Given array:')
print (a)
print( '\n')
print ('Append elements to given array:')
print (np.append(a, [7,8,9]))

'''Given array:
[[1 2 3]
 [4 5 6]]


Append elements to given array:
[1 2 3 4 5 6 7 8 9]
'''
```

## Day 6

- ### Adding / Removing Elements(numpy.insert(), numpy.delete())

```python
import numpy as np
a = np.array([[1,2],[3,4],[5,6]])
print('First array:')
print(a)
print('\n')

print('Axis parameter not passed. The input array is flattened before insertion.')
print(np.insert(a,3,[11,12]))
print('\n')

print('Axis parameter passed. The values array is broadcast to match input array.')
print('Broadcast along axis 0:' )
print(np.insert(a,1,[11],axis = 0))
print('\n')

print('Broadcast along axis 1:')
print(np.insert(a,1,11,axis = 1))

'''
First array:
[[1 2]
 [3 4]
 [5 6]]

Axis parameter not passed. The input array is flattened before insertion.
[ 1  2  3 11 12  4  5  6]

Axis parameter passed. The values array is broadcast to match input array.
Broadcast along axis 0:
[[ 1  2]
 [11 11]
 [ 3  4]
 [ 5  6]]

Broadcast along axis 1:
[[ 1 11  2]
 [ 3 11  4]
 [ 5 11  6]]
'''

a = np.arange(12).reshape(3,4)
print('First array:')
print(a)
print('\n')

print('Array flattened before delete operation as axis not used:')
print(np.delete(a,5))
print('\n')

print('Column 2 deleted:')
print(np.delete(a,1,axis = 1))
print('\n')

print('A slice containing alternate values from array deleted:')
a = np.array([1,2,3,4,5,6,7,8,9,10])
print(np.delete(a, np.s_[::2]))

'''First array:
[[ 0  1  2  3]
 [ 4  5  6  7]
 [ 8  9 10 11]]

Array flattened before delete operation as axis not used:
[ 0  1  2  3  4  6  7  8  9 10 11]

Column 2 deleted:
[[ 0  2  3]
 [ 4  6  7]
 [ 8 10 11]]

A slice containing alternate values from array deleted:
[ 2  4  6  8 10]
'''
```
- ### NumPy Broadcasting(Arithmetic Operations)

```python
import numpy as np
a = np.array([[1,2,3,4],[2,4,5,6],[10,20,39,3]])  # (3,4)
b = np.array([2,4,6,8])  # (4,)
print("\nprinting array a..")
print(a)
print("\nprinting array b..")
print(b)
print("\nAdding arrays a and b ..")
c = a + b # (3,4)
print(c)

'''
printing array a..
[[ 1  2  3  4]
 [ 2  4  5  6]
 [10 20 39  3]]

printing array b..
[2 4 6 8]

Adding arrays a and b ..
[[ 3  6  9 12]
 [ 4  8 11 14]
 [12 24 45 11]]
'''

print('\n')
arr1 = np.array([1,2,3,4])  # (4,)
arr2 = np.array(2)  # (1,)
arr3 = arr1 * arr2  # (4,)
print(arr3)  # [2 4 6 8]

print('\n')
a1 = np.array([1,2,3])
a2 = a1.reshape(3,1) # (3,1)
b1 = np.array([4,5]) # (1,2)
c1 = a2 * b1 # (3,2)
print(c1)

'''
[[ 4  5]
 [ 8 10]
 [12 15]]
'''

a = np.array([[1,2,3,4],[2,4,5,6],[10,20,39,3]])  # (3,4)
b = np.array([[2,4,6,8], [2,4,6,8], [2,4,6,8]])  # (3,4)
print("\nprinting array a..")
print(a)
print("\nprinting array b..")
print(b)
print("\nAdding arrays a and b ..")
c = a + b # (3,4)
print(c)

'''
printing array a..
[[ 1  2  3  4]
 [ 2  4  5  6]
 [10 20 39  3]]

printing array b..
[[2 4 6 8]
 [2 4 6 8]
 [2 4 6 8]]

Adding arrays a and b ..
[[ 3  6  9 12]
 [ 4  8 11 14]
 [12 24 45 11]]
'''
```

- ### NumPy String Functions(add(), multiply(), center(), capitalize(), title(), lower(), upper(), strip(), split(), splitlines(), join(), replace(), encode(), decode())

```python
import numpy as np
print("Concatenating two string arrays:")
print(np.char.add(['welcome','Hi'], [' to numpy', ' read python'] ))

'''
['welcome to numpy' 'Hi read python']
'''

print("Printing a string multiple times:")
print(np.char.multiply("hello ",3))

'''
Printing a string multiple times:
hello hello hello
'''

print("Padding the string through left and right with the fill char *");
print(np.char.center("Numpy", 20, '*'))

'''
Padding the string through left and right with the fill char *
*******Numpy********
'''

print("Converting all the characters of the string into lowercase...")
print(np.char.lower("LEARN NUMPY"))

'''
Converting all the characters of the string into lowercase...
learn numpy
'''

print("Converting all the characters of the string into uppercase...")
print(np.char.upper("Learn Numpy"))

'''
Converting all the characters of the string into uppercase...
LEARN NUMPY
'''

print("Splitting the String word by word..")
print(np.char.split("Learn Numpy"),sep = " ")

'''
Splitting the String word by word..
['Learn', 'Numpy']
'''

print("Splitting the String line by line..")
print(np.char.splitlines("Welcome\nTo\nCoding\nWorld"))

'''
Splitting the String line by line..
['Welcome', 'To', 'Coding', 'World']
'''

str = " welcome to coding world "
print("Original String:",str)
print("Removing the leading and trailing whitespaces from the string")
print(np.char.strip(str))

'''
Original String:  welcome to coding world 
Removing the leading and trailing whitespaces from the string
welcome to coding world
'''

print(np.char.join(':','HM'))

'''
H:M
'''

str = "Welcome to Coding World"
print("Original String:",str)
print("Modified String:",end=" ")
print(np.char.replace(str, "Welcome to","www."))

'''
Original String: Welcome to Coding World
Modified String: www. Coding World
'''

enstr = np.char.encode("welcome to coding world", 'cp500')
dstr = np.char.decode(enstr, 'cp500')
print(enstr)
print(dstr)

'''
b'\xa6\x85\x93\x83\x96\x94\x85@\xa3\x96@\x83\x96\x84\x89\x95\x87@\xa6\x96\x99\x93\x84'
welcome to coding world
'''
```

- ### Trigonometric functions(sin, cos, tan, arcsin, arccos, arctan, degrees)

```python
import numpy as np
arr = np.array([0, 30, 60, 90])
print("printing the sin values of different angles")
sin_val = np.sin(arr*np.pi/180)
print(sin_val)  # [0.        0.5       0.8660254 1.       ]

print("printing the inverse of the sin")
arcsin_val = np.arcsin(sin_val)
print(arcsin_val)  # [0.         0.52359878 1.04719755 1.57079633]


print("printing the values in degrees")
print(np.degrees(cosec))  # [ 0. 30. 60. 90.]

print("\nprinting the cos values of different angles")
cos_val = np.cos(arr*np.pi/180)
print(cos_val)  # [1.00000000e+00 8.66025404e-01 5.00000000e-01 6.12323400e-17]

print("printing the inverse of the cos")
arccos_val = np.arccos(cos_val)
print(arccos_val)  # [0.    0.52359878 1.04719755 1.57079633]

print("\nprinting the values in degrees")
print(np.degrees(sec))  # [ 0. 30. 60. 90.]

print("\nprinting the tan values of different angles")
tan_val = np.tan(arr*np.pi/180)
print(tan_val)  # [0.00000000e+00 5.77350269e-01 1.73205081e+00 1.63312394e+16]

print("printing the inverse of the tan")
arc_tan = np.arctan(tan_val)
print(arc_tan)  # [0.      0.52359878 1.04719755 1.57079633]

print("\nprinting the values in degrees")
print(np.degrees(arc_tan))  # [ 0. 30. 60. 90.]

```

## Day 7

- ### Rounding Functions(numpy.around(), numpy.floor(), numpy.ceil())

```python
import numpy as np

arr = np.array([12.202, 90.23120, 123.020, 23.202])
print("Printing the original array values:",end = " ")
print(arr)
print("Array values rounded off to 2 decimal position",np.around(arr, 2))  # [ 12.2   90.23 123.02  23.2 ]

arr = np.array([12.202, 90.23120, 123.020, 23.202])
print(np.floor(arr))  # [ 12. 90. 123. 23.]

arr = np.array([12.202, 90.23120, 123.020, 23.202])
print(np.ceil(arr))  # [ 13. 91. 124. 24.]

```

- ### NumPy Linear Algebra- numpy.linalg(numpy.dot(), numpy.vdot(), numpy.inner(), numpy.matmul(), numpy.linalg.det())

```python
import numpy as np

a = np.array([[100,200],[23,12]])
b = np.array([[10,20],[12,21]])
dot = np.dot(a,b)
print(dot)

'''[[3400 6200]
 [ 374  712]]'''

a = np.array([[100,200],[23,12]])
b = np.array([[10,20],[12,21]])
vdot = np.vdot(a,b)
print(vdot)  # 5528

a = np.array([1,2,3,4,5,6])
b = np.array([23,23,12,2,1,2])
inner = np.inner(a,b)
print(inner)  # 130

a = np.array([[1,2,3],[4,5,6],[7,8,9]])
b = np.array([[23,23,12],[2,1,2],[7,8,9]])
mul = np.matmul(a,b)
print(mul)

'''[[ 48  49  43]
 [144 145 112]
 [240 241 181]]'''

array1 = np.array([[1, 2], [3, 4]])
print(np.linalg.det(array1))  # -2.0000000000000004
```

- ### NumPy Matrix Multiplication(numpy.multiply(), numpy.matmul())

```python
import numpy as np

array1=np.array([[1,2,3],[4,5,6],[7,8,9]],ndmin=3)
array2=np.array([[9,8,7],[6,5,4],[3,2,1]],ndmin=3)
result=np.multiply(array1,array2)
print(result)

'''
array([[[ 9, 16, 21],
[24, 25, 24],
[21, 16, 9]]])
'''

array1=np.array([[1,2,3],[4,5,6],[7,8,9]],ndmin=3)
array2=np.array([[9,8,7],[6,5,4],[3,2,1]],ndmin=3)
result=np.matmul(array1,array2)
print(result)

'''
[[[ 30  24  18]
  [ 84  69  54]
  [138 114  90]]]
'''
```

- ### 'numpy.unique' function

```python
import numpy as np

a=np.unique([1,2,3,4,3,6,2,4])
print(a)  # array([1, 2, 3, 4, 6])

```
- ### 'numpy.mean()' function

```python
import numpy as np

a = np.array([[1, 2], [3, 4]])
b=np.mean(a)
print(b)  # 2.5
```

- ### Overview of Pandas and it's importance in Data Analysis

Pandas is a powerful Python library for data analysis and manipulation, built on NumPy. It offers robust data structures and functions to handle structured data efficiently.<br>
**Key Features:**

  - **Data Structures:**
        Series: One-dimensional labeled array.
        DataFrame: Two-dimensional labeled table-like structure.

  - **Data Manipulation:**
        Tools for reshaping, merging, slicing, and handling missing data.

   - **Data Alignment and Indexing:**
        Intelligent label-based slicing, indexing, and data alignment.

  - **Input/Output:**
        Read/write data to/from CSV, Excel, SQL databases, JSON, etc.

  - **Time Series:**
        Tools for working with time series data.

   - **Group By:**
        Splitting data for aggregation, transformation, and analysis.

**Importance in Data Analysis:**

  - **Data Cleaning:** Comprehensive tools for preprocessing data.
  - **Data Exploration:** Easy calculation of summary statistics and data visualization.
  - **Data Transformation:** Reshaping data for analysis.
  - **Performance:** Efficient handling of large datasets.
  - **Ease of Use:** User-friendly syntax and extensive documentation.
  - **Reproducibility:** Clear documentation of data analysis workflows.
  - **Time Series Analysis:** Robust support for financial and forecasting analysis.
    
- ### Installing Pandas

   - For **Windows**,to install Python Pandas, go to your command prompt and type
```
pip install pandas
```
   - For **Linux**,
```
pip3 install pandas

```
   - For **MacOS**:
```
pip3 install pandas
```

- ### Series Data Structure: Introduction

It is defined as a one-dimensional array that is capable of storing various data types. The row labels of
series are called the index. We can easily convert the list, tuple, and dictionary into series using "series'
method. A Series cannot contain multiple columns.

A pandas Series can be created using the following constructor −
pandas.Series( data, index, dtype, copy)

```python
import pandas as pd
import numpy as np

s = pd.Series()  # empty series
print(s)

data = np.array(['a','b','c','d'])
s = pd.Series(data)  # series from array
print(s)
'''
0 a
1 b
2 c
3 d
dtype: object
'''
```
- ### Series Indexing

```python
import pandas as pd
import numpy as np

data = np.array(['a','b','c','d'])
s = pd.Series(data,index=[100,101,102,103])  # assigning our own index
print(s)
```

