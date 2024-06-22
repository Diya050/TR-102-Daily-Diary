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
    **Checking the Data Type of an Array:** The NumPy array object has a property called dtype that returns the data type of the array:
```python
import numpy as np
# checking datatype of array
arr = np.array([1, 2, 3, 4])
print(arr.dtype)  # int64

arr1=np.array(['apple', 'banana', 'cherry'])
print(arr1.dtype)  # <U6

# defining datatype
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

- NumPy - Array From Existing Data(asarray, frombuffer, fromiter)
- NumPy - Array From Numerical Ranges(arange, linspace)
- Iterating Arrays(1-D, 2-D, 3-D)
- numpy.nditer function(order)


## Day 4

- numpy.nditer function(op_flags, flags, external_loop)
- Broadcasting Iteration
- Enumerated Iteration Using ndenumerate()
- numpy.logspace
- Random Function(randint, rand, randn)
- Joining Arrays(concatenate(), stack(), hstack(), vstack())


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
