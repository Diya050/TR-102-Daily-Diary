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

The assign() method is also responsible for adding a new column into a DataFrame.

```python
import pandas as pd

df = pd.DataFrame({'ID': [101, 102, 103]})
df = df.assign(Name=['abc', 'xyz', 'lmn'])
print(df)

info = pd.DataFrame({'temp_c': [17.0, 25.0]},
index=['Canada', 'Australia'])
print(info)
print(info.assign(temp_f=lambda x: x.temp_c * 7 / 2 + 24))
print(info.assign(temp_f=lambda x: x['temp_c'] * 7/2 + 24))
```

- ### Pandas DataFrame.count()

```python
info = pd.DataFrame({"Person":["Parker", "Smith", "William", "John"],
"Age": [27., 29, np.nan, 32]})

print(info.count())
print(info.count(axis='columns'))
```

- ### Pandas DataFrame.drop_duplicates()

```python
emp = {"Name": ["Parker", "Smith", "William", "Parker"],
"Age": [21, 32, 29, 21]}
info = pd.DataFrame(emp)

info = info.drop_duplicates()
print(info)
```

- ### Pandas DataFrame.apply()

```python
info = pd.DataFrame([[2, 7]] * 4, columns=['P', 'Q'])
print(info.apply(np.sqrt))
print(info)

print(info.apply(np.sum, axis=0))
print(info.apply(np.sum, axis=1))
print(info.apply(lambda x: [1, 2], axis=1))
print(info.apply(lambda x: [1, 2], axis=1, result_type='expand'))
print(info.apply(lambda x: pd.Series([1, 2, 3], index=['foo', 'bar', 'hoe']), axis=1))
print(info.apply(lambda x: [1, 2], axis=1, result_type='broadcast'))
```

- ### Pandas.groupby() Function

```python
technologies = ({
    'Courses':["Spark","PySpark","Hadoop","Python","Pandas","Hadoop","Spark","Python","NA"],
    'Fee' :[22000,25000,23000,24000,26000,25000,25000,22000,1500],
    'Duration':['30days','50days','55days','40days','60days','35days','30days','50days','40days'],
    'Discount':[1000,2300,1000,1200,2500,None,1400,1600,0]
})
df = pd.DataFrame(technologies)
print(df, '\n')
df2 = df.groupby(['Courses','Duration']).sum()
print(df2, '\n')
df2 = df.groupby(['Courses','Duration']).sum().reset_index()
print(df2, '\n')
```

- ### Pandas DataFrame.head()

```python
print(df.head(4), '\n')
print(df.tail(2), '\n')
```

- ### Pandas DataFrame.iterrows()

```python
info = pd.DataFrame(np.random.randn(4,2), columns=['col1','col2'])
print(info, '\n')
for row_index,row in info.iterrows():
    print (row_index,'\n', row)
    
print('\n')
for r in info.itertuples():
    print(r)
    
print('\n')
for r in info._iter_column_arrays():
    print(r)
```

- ### Pandas Join(inner, outer, left, right)

```python
import pandas as pd

technologies = {
'Courses':["Spark","PySpark","Python","pandas"],
'Fee' :[20000,25000,22000,30000],
'Duration':['30days','40days','35days','50days'],
}
index_labels=['r1','r2','r3','r4']
df1 = pd.DataFrame(technologies,index=index_labels)

technologies2 = {
'Courses':["Spark","Java","Python","Go"],
'Discount':[2000,2300,1200,2000]
}
index_labels2=['r1','r6','r3','r5']
df2 = pd.DataFrame(technologies2,index=index_labels2)

df3=df1.join(df2, lsuffix="_left", rsuffix="_right")
print(df3)

print('\n')
df3=df1.join(df2, lsuffix="_left", rsuffix="_right", how='right')
print(df3)

print('\n')
df3=df1.join(df2, lsuffix="_left", rsuffix="_right", how='inner')
print(df3)

print('\n')
df3=df1.join(df2, lsuffix="_left", rsuffix="_right", how='outer')
print(df3)

'''
   Courses_left    Fee Duration Courses_right  Discount
r1        Spark  20000   30days         Spark    2000.0
r2      PySpark  25000   40days           NaN       NaN
r3       Python  22000   35days        Python    1200.0
r4       pandas  30000   50days           NaN       NaN


   Courses_left      Fee Duration Courses_right  Discount
r1        Spark  20000.0   30days         Spark      2000
r6          NaN      NaN      NaN          Java      2300
r3       Python  22000.0   35days        Python      1200
r5          NaN      NaN      NaN            Go      2000


   Courses_left    Fee Duration Courses_right  Discount
r1        Spark  20000   30days         Spark      2000
r3       Python  22000   35days        Python      1200


   Courses_left      Fee Duration Courses_right  Discount
r1        Spark  20000.0   30days         Spark    2000.0
r2      PySpark  25000.0   40days           NaN       NaN
r3       Python  22000.0   35days        Python    1200.0
r4       pandas  30000.0   50days           NaN       NaN
r5          NaN      NaN      NaN            Go    2000.0
r6          NaN      NaN      NaN          Java    2300.0
'''
```

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

CSV files contains plain text and is a well know format that can be read by everyone including Pandas.
pd.read_csv function is used to import the dataframes in python which has been created in excel files

```python
import pandas as pd
df = pd.read_csv('data.csv')
print(df.to_string())
```
We are using to_string() function to print the entire DataFrame. If you have a large DataFrame with
many rows, Pandas will only return the first 5 rows, and the last 5 rows:

```python
import pandas as pd
df = pd.read_csv('data.csv')
print(df)
```

- ### Check max_rows

```python
print(pd.options.display.max_rows)
pd.options.display.max_rows = 1000
print(pd.options.display.max_rows)

'''
60
1000
'''
```

- ### Read JSON

```python
import pandas as pd
df = pd.read_json('data.json')
print(df.to_string(
```

- ### Dictionary as JSON

JSON = Python Dictionary
JSON objects have the same format as Python dictionaries. If your JSON code is not in a file, but in a
Python Dictionary, you can load it into a DataFrame directly:

```python
data = {
"Duration":{
"0":60,
"1":60,
"2":60,
"3":45,
"4":45,
"5":60
},
"Pulse":{
"0":110,
"1":117,
"2":103,
"3":109,
"4":117,
"5":102
},
"Maxpulse":{
"0":130,
"1":145,
"2":135,
"3":175,
"4":148,
"5":127
},
"Calories":{
"0":409.1,
"1":479.0,
"2":340.0,
"3":282.4,
"4":406.0,
"5":300.5
}
}
df = pd.DataFrame(data)
print(df)

'''
   Duration  Pulse  Maxpulse  Calories
0        60    110       130     409.1
1        60    117       145     479.0
2        60    103       135     340.0
3        45    109       175     282.4
4        45    117       148     406.0
5        60    102       127     300.5
'''
```

- ### Viewing the Data

One of the most used method for getting a quick overview of the DataFrame, is the head() method.
The head() method returns the headers and a specified number of rows, starting from the top.

```python
import pandas as pd
df = pd.read_csv('data.csv')
print(df.head(10))
print(df.tail(5))
```
`Note:` If the number of rows is not specified, the head() method will return the top 5 rows.

- ### Information About the Dataframe

The DataFrames object has a method called info(), that gives you more information about the data
set.

```python
print(df.info())
```
The info() method also tells us how many Non-Null values there are present in each column, and in
our data set it seems like there are 164 of 169 Non-Null values in the "Calories" column.

- ### Data Cleaning

Data cleaning means fixing bad data in your data set.
Bad data could be:
   1. Empty cells
   2. Data in wrong format
   3. Wrong data
   4. Duplicates

## Day 13

- ### Empty Cells: Remove Rows

```python
import pandas as pd
df = pd.read_csv('data.csv')
new_df = df.dropna()
print(new_df.to_string())
```
`Note:` By default, the dropna() method returns a new DataFrame, and will not change the original. If
you want to change the original DataFrame, use the inplace = True argument.

```python
import pandas as pd
df = pd.read_csv('data.csv')
df.dropna(inplace = True)
print(df.to_string())
```

- ### Empty Cells: Replace Empty Values

```python
import pandas as pd
df = pd.read_csv('data.csv')

df.fillna(130, inplace = True)
```
The example above replaces all empty cells in the whole Data Frame. To only replace empty values
for one column, specify the column name for the DataFrame:

```python
import pandas as pd
df = pd.read_csv('data.csv')

df["Calories"].fillna(130, inplace = True)
```

- ### Empty Cells: Replace Using Mean, Median, or Mode

```python
import pandas as pd
df = pd.read_csv('data.csv')
x = df["Calories"].mean()
df["Calories"].fillna(x, inplace = True)

x = df["Calories"].mode()[0]
df["Calories"].fillna(x, inplace = True)

x = df["Calories"].median()
df["Calories"].fillna(x, inplace = True)
```

- ### Convert Data of Wrong Format into Correct Format

Cells with data of wrong format can make it difficult, or even impossible, to analyze data. To fix it,
you have two options: remove the rows, or convert all cells in the columns into the same format. In our Data Frame, we have two cells with the wrong format. Check out row 22 and 26, the 'Date' column should be a string that represents a date:

```python
import pandas as pd
df = pd.read_csv('data.csv')
df['Date'] = pd.to_datetime(df['Date'])
print(df.to_string())
```

## Day 14

- ### Fixing Wrong Data

"Wrong data" does not have to be "empty cells" or "wrong format", it can just be wrong, like if
someone registered "199" instead of "1.99".
Sometimes you can spot wrong data by looking at the data set, because you have an expectation of
what it should be.

If you take a look at our data set, you can see that in row 7, the duration is 450, but for all the other
rows the duration is between 30 and 60.It doesn't have to be wrong, but taking in consideration that
this is the data set of someone's workout sessions, we conclude with the fact that this person did
not work out in 450 minutes.


| Duration | Date       | Pulse | Maxpulse | Calories |
|----------|------------|-------|----------|----------|
| 0        | 60         | 2020/12/01 | 110   | 130      | 409.1    |
| 1        | 60         | 2020/12/02 | 117   | 145      | 479.0    |
| 2        | 60         | 2020/12/03 | 103   | 135      | 340.0    |
| 3        | 45         | 2020/12/04 | 109   | 175      | 282.4    |
| 4        | 45         | 2020/12/05 | 117   | 148      | 406.0    |
| 5        | 60         | 2020/12/06 | 102   | 127      | 300.0    |
| 6        | 60         | 2020/12/07 | 110   | 136      | 374.0    |
| 7        | 450        | 2020/12/08 | 104   | 134      | 253.3    |
| 8        | 30         | 2020/12/09 | 109   | 133      | 195.1    |
| 9        | 60         | 2020/12/10 | 98    | 124      | 269.0    |
| 10       | 60         | 2020/12/11 | 103   | 147      | 329.3    |
| 11       | 60         | 2020/12/12 | 100   | 120      | 250.7    |
| 12       | 60         | 2020/12/12 | 100   | 120      | 250.7    |
| 13       | 60         | 2020/12/13 | 106   | 128      | 345.3    |
| 14       | 60         | 2020/12/14 | 104   | 132      | 379.3    |
| 15       | 60         | 2020/12/15 | 98    | 123      | 275.0    |
| 16       | 60         | 2020/12/16 | 98    | 120      | 215.2    |
| 17       | 60         | 2020/12/17 | 100   | 120      | 300.0    |
| 18       | 45         | 2020/12/18 | 90    | 112      | NaN      |
| 19       | 60         | 2020/12/19 | 103   | 123      | 323.0    |
| 20       | 45         | 2020/12/20 | 97    | 125      | 243.0    |
| 21       | 60         | 2020/12/21 | 108   | 131      | 364.2    |
| 22       | 45         | NaN        | 100   | 119      | 282.0    |
| 23       | 60         | 2020/12/23 | 130   | 101      | 300.0    |
| 24       | 45         | 2020/12/24 | 105   | 132      | 246.0    |
| 25       | 60         | 2020/12/25 | 102   | 126      | 334.5    |
| 26       | 60         | 20201226   | 100   | 120      | 250.0    |
| 27       | 60         | 2020/12/27 | 92    | 118      | 241.0    |
| 28       | 60         | 2020/12/28 | 103   | 132      | NaN      |
| 29       | 60         | 2020/12/29 | 100   | 132      | 280.0    |
| 30       | 60         | 2020/12/30 | 102   | 129      | 380.3    |
| 31       | 60         | 2020/12/31 | 92    | 115      | 243.0    |


- ### Fixing Wrong Data: Replacing Values

One way to fix wrong values is to replace them with something else.
In our example, it is most likely a typo, and the value should be "45" instead of "450", and we could
just insert "45" in row 7:

```python
df.loc[7, 'Duration'] = 45
```
or small data sets you might be able to replace the wrong data one by one, but not for big data sets.
To replace wrong data for larger data sets you can create some rules, e.g. set some boundaries for
legal values, and replace any values that are outside of the boundaries.

```python
for x in df.index:
   if df.loc[x, "Duration"] > 120:
      df.loc[x, "Duration"] = 120
```

- ### Fixing Wrong Data: Removing Rows

Another way of handling wrong data is to remove the rows that contains wrong data.
This way you do not have to find out what to replace them with, and there is a good chance you do
not need them to do your analyses

```python
for x in df.index:
   if df.loc[x, "Duration"] > 120:
      df.drop(x, inplace = True)
```

- ### Discovering Duplicates and Removing Duplicates

Duplicate rows are rows that have been registered more than one time.
By taking a look at our test data set, we can assume that row 11 and 12 are duplicates.
To discover duplicates, we can use the duplicated() method.
The duplicated() method returns a Boolean values for each row:

```python
print(df.duplicated())
```

To remove duplicates, use the drop_duplicates() method.

```python
df.drop_duplicates(inplace = True)
```

- ### Skip Rows Argument and Header Argument

Skip row argument is used to skip the rows from the dataframe. In the function we need to mention
the no of rows which you want to skip in the program.

```python
import pandas as pd
df = pd.read_csv('data.csv',skiprows=1)
print(df)
```

On the other hand we can also mention header argument which importing the csv file in python.
Header will do the same work as skip rows argument.

```python
import pandas as pd
df = pd.read_csv('data.csv',header=1)
print(df)
```

In the case of when we don’t have headers in our excel dataframe , we can create headers at the
time of importing files.

```python
import pandas as pd
df = pd.read_csv('data.csv',header=None,names=[“Srno”,”stunames”,”rollno”])
print(df)
```

To print specific no of rows:

```python
import pandas as pd
df = pd.read_csv('data.csv',nrows=3)
print(df)
```
