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
"""
[[[1 2 3]
  [4 5 6]]

 [[1 2 3]
  [4 5 6]]]"""
print(arr.ndim)  # 3
```
  - **Higher Dimensional Arrays**: Arrays can be created of any dimension using `ndmin` attribute.
```python
import numpy as np
arr = np.array([1, 2, 3, 4], ndmin=5)
print(arr)
print('number of dimensions :', arr.ndim)

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

- NumPy Data Types
- Structured Arrays
- NumPy - Array Attributes(shape, reshape, itemsize, ndim)
- NumPy - Array Creation Routines(empty, ones, zeros, full, eye)
- NumPy Array Copy vs View
- NumPy - Arithmetic Operations


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
