# Daily Dairy: Week 2

## Day 8

- ### Create a Series from dict

```python
import pandas as pd

data = {'a' : 0., 'b' : 1., 'c' : 2.}
s = pd.Series(data)  # Create a Series from dict
print(s)
'''
a 0.0
b 1.0
c 2.0
dtype: float64
'''

data = {'a' : 0., 'b' : 1., 'c' : 2.}
s = pd.Series(data,index=['b','c','d','a'])
print(s)
'''
b 1.0
c 2.0
d NaN
a 0.0
dtype: float64
'''
```

- ### Accessing Data from Series with Position

Data in the series can be accessed similar to that in an ndarray.

```python
import pandas as pd

s = pd.Series([1,2,3,4,5],index = ['a','b','c','d','e'])

print(s[0])  # 1

s = pd.Series([1,2,3,4,5],index = ['a','b','c','d','e'])
print(s[:3])
'''
a    1
b    2
c    3
dtype: int64
'''
```

- ### Checking Pandas Version

The version string is stored under __version__ attribute.

```python
import pandas as pd
print(pd.__version__)  # 1.0.3
```

- ### Retrieving Index array and data array of a series object

We can retrieve the index array and data array of an existing Series object by using the attributes index and values:

```python
import numpy as np
import pandas as pd

x=pd.Series(data=[2,4,6,8])
y=pd.Series(data=[11.2,18.6,22.5], index=['a','b','c'])

print(x.index)
print(x.values)
'''
RangeIndex(start=0, stop=4, step=1)
[2 4 6 8]
'''

print(y.index)
print(y.values)
'''
Index(['a', 'b', 'c'], dtype='object')
[11.2 18.6 22.5]
'''
```

- ### Retrieving Types (dtype)

```python
import numpy as np
import pandas as pd

a=pd.Series(data=[1,2,3,4])
b=pd.Series(data=[4.9,8.2,5.6], index=['x','y','z'])

print(a.dtype)  # int64

print(b.dtype)  # float64
```

- ### Retrieving Shape, Dimension, Size and Number of bytes

```python
import pandas as pd

a=pd.Series(data=[[1,2,3,4], [1,2], 2, np.NaN]) # Data treated as 1-dimensional
b=pd.Series(data=[4.9,8.2,5.6], index=['x','y','z'])
print(a)
'''
0    [1, 2, 3, 4]
1          [1, 2]
2               2
3             NaN
dtype: object
'''

print(b)
'''
x    4.9
y    8.2
z    5.6
dtype: float64
'''

print(a.shape)  # (4,)

print(b.shape)  # (3,)
print(a.ndim, b.ndim)  # 1 1
print(a.size, b.size)  # 4 3
print(a.nbytes, b.nbytes)  # 32 24

print(len(a),len(b))  # 4 3
print(a.count( ),b.count( ))  # 3 3
```

- ### Checking Emptiness and Presence of NaNs

```python
import numpy as np
import pandas as pd

a=pd.Series(data=[1,2,3,np.NaN])
b=pd.Series(data=[4.9,8.2,5.6],index=['x','y','z'])
c=pd.Series()

print(a.empty,b.empty,c.empty)  # False False True
print(a.hasnans,b.hasnans,c.hasnans)  # True False False
```

- ### Python Pandas DataFrame

It is a widely used data structure of pandas and works with a two-dimensional array with labeled axes (rows and columns). DataFrame is defined as a standard way to store data and has two different indexes, i.e., row index and column index. It consists of the following properties:
   - The columns can be heterogeneous types like int, bool, and so on.
   - It can be seen as a dictionary of Series structure where both the rows and columns are indexed. It is denoted as "columns" in case of columns and "index" in case of rows.

- ### Create an Empty DataFrame, a DataFrame from Lists, a DataFrame from Dict of ndarrays / Lists, a DataFrame from List of Dicts and a DataFrame from Dict of Series

```python
import pandas as pd
import numpy as np

df = pd.DataFrame()
print(df)
'''
Empty DataFrame
Columns: []
Index: []
'''

print('\n')
# DataFrame from List
data = np.array(['a', 'b', 'x', 'y'])
df = pd.DataFrame(data, columns=['data'])
print(df)
'''
  data
0    a
1    b
2    x
3    y
'''

# list of lists
print('\n')
info = [['Diya', 95, 20], ['Rohan', 90, 22], ['Kavya', 85, 18]]
df = pd.DataFrame(info, columns=['Name', 'Score', 'Age'])
print(df)
'''
    Name  Score  Age
0   Diya     95   20
1  Rohan     90   22
2  Kavya     85   18
'''

# dictionary of lists
info = {'Name': ['Diya', 'Rohan', 'Kavya'], 'Age': [20, 22, 18]}
df = pd.DataFrame(info, index=['rank1', 'rank2', 'rank3'])
print(df)
'''
        Name  Age
rank1   Diya   20
rank2  Rohan   22
rank3  Kavya   18
'''

# list of dictionaries
info = [{'a': 0, 'b': 41}, {'a': 15, 'b': 20, 'c': 24}]
df = pd.DataFrame(info, index=['first', 'second'])
print(df)
'''
         a   b     c
first    0  41   NaN
second  15  20  24.0
'''

data = [{'a': 1, 'b': 2}, {'a': 5, 'b': 10, 'c': 20}]
df1 = pd.DataFrame(data, index=['first', 'second'], columns=['a', 'b'])

df2 = pd.DataFrame(data, index=['first', 'second'], columns=['a', 'b1'])
print(df1)
print(df2)
'''
        a   b
first   1   2
second  5  10

        a  b1
first   1 NaN
second  5 NaN
'''
```

- ### Column Selection, Addition and Deletion

```python
import pandas as pd

d = {'one': pd.Series([1, 2, 3], index=['a', 'b', 'c']), 'two': pd.Series([1, 2, 3, 4], index=['a', 'b', 'c', 'd'])}
df = pd.DataFrame(d)
print(df, '\n')
print(df['one'], '\n')  # column selection
'''
   one  two
a  1.0    1
b  2.0    2
c  3.0    3
d  NaN    4 

a    1.0
b    2.0
c    3.0
d    NaN
Name: one, dtype: float64
'''

# column addition
df['three'] = pd.Series([1, 2, 3, 4], index=('a', 'b', 'c', 'd'))
df['four'] = df['one']+df['three']
print(df, '\n')
'''
   one  two  three  four
a  1.0    1      1   2.0
b  2.0    2      2   4.0
c  3.0    3      3   6.0
d  NaN    4      4   NaN 
'''

# column deletion
del df['one']
print(df)
df.pop('three')
print(df)
print(df[1:3])
'''
   two  three  four
a    1      1   2.0
b    2      2   4.0
c    3      3   6.0
d    4      4   NaN
   two  four
a    1   2.0
b    2   4.0
c    3   6.0
d    4   NaN
'''
```

## Day 9

- ### Pandas Series.to_frame()

```python
import pandas as pd

# series to dataframe
s = pd.Series([11, 22, 13], name='age')
print(s.to_frame())
'''
   age
0   11
1   22
2   13
'''

emp_series = pd.Series(['abc', 'xyz'])
id_series = pd.Series([1001, 1003])

d = {'Emp': emp_series, 'ID': id_series}

df = pd.DataFrame(d)
print(df)
'''
   Emp    ID
0  abc  1001
1  xyz  1003
'''
```

- ### Row Selection, Addition, and Deletion

```python
import pandas as pd

d = {'one': pd.Series([1, 2, 3], index=['a', 'b', 'c']), 'two': pd.Series([1, 2, 3, 4], index=['a', 'b', 'c', 'd'])}
df = pd.DataFrame(d)
print(df, '\n')
'''
   one  two
a  1.0    1
b  2.0    2
c  3.0    3
d  NaN    4
'''

print(df.loc['b'])  # row selection by label
print(df.iloc[1], '\n')  # row selection by integer location
'''
one    2.0
two    2.0
Name: b, dtype: float64
one    2.0
two    2.0
Name: b, dtype: float64
'''

# row addition
d = pd.DataFrame([[7, 8], [9, 10]], columns=['x', 'y'])
d2 = pd.DataFrame([[11, 12], [13, 14]], columns=['x', 'y'])
d = d._append(d2, ignore_index=True)
print(d)
'''
    x   y
0   7   8
1   9  10
2  11  12
3  13  14
'''

# row deletion
d = d.drop(1)
print(d)
'''
    x   y
0   7   8
2  11  12
3  13  14
'''
```
- ### Slice Rows

```python
import pandas as pd

d = {'one': pd.Series([1, 2, 3], index=['a', 'b', 'c']), 'two': pd.Series([1, 2, 3, 4], index=['a', 'b', 'c', 'd'])}
df = pd.DataFrame(d)

print(df[1:3])
'''
   one  two
b  2.0    2
c  3.0    3
'''
```
-  ### Pandas Series.value_counts()

The value_counts() function returns a Series that contain counts of unique values. It returns an object that will be in descending order so that its first element will be the most frequently-occurred element. By default, it excludes NA values.

```python
index = pd.Index([2, 1, 1, 1, 3, np.nan, 3])
print(index.value_counts())  # counts unique values
'''
1.0    3
3.0    2
2.0    1
Name: count, dtype: int64
'''
```

- ### Pandas DataFrame.append()

The Pandas append() function is used to add the rows of other dataframe to the end of the given
dataframe, returning a new dataframe object. 

```python
import pandas as pd

info1 = pd.DataFrame({"x":[25,15,12,19],
"y":[47, 24, 17, 29]})

info2 = pd.DataFrame({"x":[25, 15, 12],
"y":[47, 24, 17],
"z":[38, 12, 45]})

print(info1.append(info2, ignore_index = True))

'''
    x   y     z
0  25  47   NaN
1  15  24   NaN
2  12  17   NaN
3  19  29   NaN
4  25  47  38.0
5  15  24  12.0
6  12  17  45.0
'''
```

- ### Pandas DataFrame.aggregate()

The main task of DataFrame.aggregate() function is to apply some aggregation to one or more column.
Most frequently used aggregations are:
   - sum: It is used to return the sum of the values for the requested axis.
   - min: It is used to return the minimum of the values for the requested axis.
   - max: It is used to return the maximum values for the requested axis.

```python
import pandas as pd

# aggregate function
info=pd.DataFrame([[1,5,7],[10,12,15],[18,21,24],[np.nan,np.nan,np.nan]],columns=['X','Y','Z'])
print(info.agg(['sum','min', 'max']))
print(info.agg({'X':['sum','min', 'max'], 'Z':['sum', 'max']}))
'''
        X     Y     Z
sum  29.0  38.0  46.0
min   1.0   5.0   7.0
max  18.0  21.0  24.0
        X     Z
sum  29.0  46.0
min   1.0   NaN
max  18.0  24.0
'''
```

## Day 10

- ### Pandas DataFrame.assign()
- ### Pandas DataFrame.count()
- ### Pandas DataFrame.drop_duplicates()
- ### Pandas DataFrame.apply()
- ### Pandas.groupby() Function
- ### Pandas DataFrame.head()
- ### Pandas DataFrame.iterrows()
- ### Pandas Join(inner, outer, left, right)

## Day 11

- ### Pandas DataFrame.mean()

The mean() function is used to return the mean of the values for the requested axis. If we apply this method on a Series object, then it returns a scalar value, which is the mean value of all the observations in the dataframe.

```python
import pandas as pd

info = pd.DataFrame({"A":[5, 2, 6, 4, None],
"B":[12, 19, None, 8, 21],
"C":[15, 26, 11, None, 3],
"D":[14, 17, 29, 16, 23]})
print(info)
'''
     A     B     C   D
0  5.0  12.0  15.0  14
1  2.0  19.0  26.0  17
2  6.0   NaN  11.0  29
3  4.0   8.0   NaN  16
4  NaN  21.0   3.0  23
'''

print(info.mean(axis = 0, skipna = True))
'''
A     4.25
B    15.00
C    13.75
D    19.80
dtype: float64
'''

print(info.mean(axis = 1, skipna = True))
'''
0    11.500000
1    16.000000
2    15.333333
3     9.333333
4    15.666667
dtype: float64
'''
```

- ### Pandas DataFrame.merge()

Pandas merge() is defined as the process of bringing the two datasets together into one and aligning the rows based on the common attributes or columns. 

```python
import pandas as pd

info = pd.DataFrame({"A":[5, 2, 6, 4, None],
"B":[12, 19, None, 8, 21],
"C":[15, 26, 11, None, 3],
"D":[14, 17, 29, 16, 23]})

print(info)
print(info.mean(axis = 0, skipna = True))

print(info.mean(axis = 1, skipna = True))

import pandas as pd

left = pd.DataFrame({
'id':[1,2,3,4,5],
'Name': ['Alex', 'Amy', 'Allen', 'Alice', 'Ayoung'],
'subject_id':['sub1','sub2','sub4','sub6','sub5']})
print(left)
'''
   id    Name subject_id
0   1    Alex       sub1
1   2     Amy       sub2
2   3   Allen       sub4
3   4   Alice       sub6
4   5  Ayoung       sub5
'''
right = pd.DataFrame({
'id':[1,2,3,4,5],
'Name': ['Billy', 'Brian', 'Bran', 'Bryce', 'Betty'],
'subject_id':['sub2','sub4','sub3','sub6','sub5']})
print(right)
'''
   id   Name subject_id
0   1  Billy       sub2
1   2  Brian       sub4
2   3   Bran       sub3
3   4  Bryce       sub6
4   5  Betty       sub5
'''

print(pd.merge(left,right,on='subject_id'))
'''
   id_x  Name_x subject_id  id_y Name_y
0     2     Amy       sub2     1  Billy
1     3   Allen       sub4     2  Brian
2     4   Alice       sub6     4  Bryce
3     5  Ayoung       sub5     5  Betty
'''
```

- ### Pandas Dataframe.Query() Method

Pandas DataFrame.query() method is used to query the rows based on the expression (single or multiple column conditions) provided and returns a new DataFrame.

```python
import pandas as pd
import numpy as np

technologies= {
'Courses':["Spark","PySpark","Hadoop","Python","Pandas"],
'Fee' :[22000,25000,23000,24000,26000],
'Duration':['30days','50days','30days', None,np.nan],
'Discount':[1000,2300,1000,1200,2500]
}

df = pd.DataFrame(technologies)
print(df)
'''
   Courses    Fee Duration  Discount
0    Spark  22000   30days      1000
1  PySpark  25000   50days      2300
2   Hadoop  23000   30days      1000
3   Python  24000     None      1200
4   Pandas  26000      NaN      2500
'''

df2=df.query("Fee >= 24000")
print(df2)
'''
   Courses    Fee Duration  Discount
1  PySpark  25000   50days      2300
3   Python  24000     None      1200
4   Pandas  26000      NaN      2500
'''
```

- ### Pandas DataFrame.rename()

This method is useful for renaming some selected columns because we have to specify the information only for those columns that we want to rename.

```python
import pandas as pd

# Define a dictionary containing information of employees
info = {'name': ['Parker', 'Smith', 'William', 'Robert'],
'age': [38, 47, 44, 34],
'language': ['Java', 'Python', 'JavaScript', 'Python']}

# Convert dictionary into DataFrame
info_pd = pd.DataFrame(info)

# Before renaming columns
print(info_pd)
'''
      name  age    language
0   Parker   38        Java
1    Smith   47      Python
2  William   44  JavaScript
3   Robert   34      Python
'''

info_pd.rename(columns = {'name':'Name', 'age':'Age', 'language':'Language'}, inplace = True)

print(info_pd)
'''
      Name  Age    Language
0   Parker   38        Java
1    Smith   47      Python
2  William   44  JavaScript
3   Robert   34      Python
'''
```

- ### Dataframe.Sample() Function

The sample() function is used to get a random sample of items from an axis of object.

```python
import pandas as pd

df = pd.DataFrame({'num_legs': [2, 4, 8, 0],
'num_wings': [2, 0, 0, 0],
'num_specimen_seen': [8, 2, 5, 6]},
index=['sparrow', 'fox', 'spider', 'snake'])

print(df)
'''
         num_legs  num_wings  num_specimen_seen
sparrow         2          2                  8
fox             4          0                  2
spider          8          0                  5
snake           0          0                  6
'''

print(df['num_legs'].sample(n=3))
'''
sparrow    2
snake      0
fox        4
Name: num_legs, dtype: int64
'''
```

- ### DataFrame.sort()

Sort function is used to sort the dataframes in ascending or descending order.

```python
import pandas as pd

age_list = [['Afghanistan', 1952, 8425333, 'Asia'],
['Australia', 1957, 9712569, 'Oceania'],
['Brazil', 1962, 76039390, 'Americas'],
['China', 1957, 637408000, 'Asia'],
['France', 1957, 44310863, 'Europe'],
['India', 1952, 3.72e+08, 'Asia'],
['United States', 1957, 171984000, 'Americas']]

df = pd.DataFrame(age_list, columns=['Country', 'Year','Population', 'Continent'])
print(df)
'''
         Country  Year   Population Continent
0    Afghanistan  1952    8425333.0      Asia
1      Australia  1957    9712569.0   Oceania
2         Brazil  1962   76039390.0  Americas
3          China  1957  637408000.0      Asia
4         France  1957   44310863.0    Europe
5          India  1952  372000000.0      Asia
6  United States  1957  171984000.0  Americas
'''

print(df.sort_values(by=['Country', 'Year'], ascending=[False, True]))

'''
         Country  Year   Population Continent
6  United States  1957  171984000.0  Americas
5          India  1952  372000000.0      Asia
4         France  1957   44310863.0    Europe
3          China  1957  637408000.0      Asia
2         Brazil  1962   76039390.0  Americas
1      Australia  1957    9712569.0   Oceania
0    Afghanistan  1952    8425333.0      Asia
'''
```

- ### DataFrame.sum()

Pandas DataFrame.sum() function is used to return the sum of the values for the requested axis by
the user.

```python
import pandas as pd

info = {'Name': ['Parker', 'Smith', 'William'],
'age' : [32, 28, 39]}
data = pd.DataFrame(info)

data['total'] = data['age'].sum()
print(data)
'''
      Name  age  total
0   Parker   32     99
1    Smith   28     99
2  William   39     99
'''
```

- ### DataFrame.transpose()

The transpose() function helps to transpose the index and columns of the dataframe. It reflects
DataFrame over its main diagonal by writing the rows as columns and vice-versa.

```python
import pandas as pd

info = pd.DataFrame({"A":[8, 2, 7, None, 6],
"B":[4, 3, None, 9, 2],
"C":[17, 42, 35, 18, 24],
"D":[15, 18, None, 11, 12]})

index_ = ['Row1', 'Row2', 'Row3', 'Row4', 'Row5']
info.index = index_
print(info)
'''
        A    B   C     D
Row1  8.0  4.0  17  15.0
Row2  2.0  3.0  42  18.0
Row3  7.0  NaN  35   NaN
Row4  NaN  9.0  18  11.0
Row5  6.0  2.0  24  12.0
'''
result = info.transpose()
print(result)
'''
   Row1  Row2  Row3  Row4  Row5
A   8.0   2.0   7.0   NaN   6.0
B   4.0   3.0   NaN   9.0   2.0
C  17.0  42.0  35.0  18.0  24.0
D  15.0  18.0   NaN  11.0  12.0
'''
```

## Day 12

- ### Reading CSV Files in Pandas Python
- ### Check max_rows
- ### Read JSON
- ### Dictionary as JSON
- ### Viewing the Data
- ### Information About the Dataframe
- ### Data Cleaning

## Day 13

- ### Empty Cells: Remove Rows
- ### Empty Cells: Replace Empty Values
- ### Empty Cells: Replace Using Mean, Median, or Mode
- ### Convert Data of Wrong Format into Correct Format
