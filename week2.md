# Daily Dairy: Week 2

## Day 8

- ### Create a Series from dict
- ### Accessing Data from Series with Position
- ### Checking Pandas Version
- ### Retrieving Index array and data array of a series object
- ### Retrieving Types (dtype) and Size of Type (itemsize)
- ### Retrieving Shape, Dimension, Size and Number of bytes
- ### Checking Emptiness and Presence of NaNs
- ### Python Pandas DataFrame
- ### Create an Empty DataFrame, a DataFrame from Lists, a DataFrame from Dict of ndarrays / Lists, a DataFrame from List of Dicts and a DataFrame from Dict of Series
- ### Column Selection, Addition and Deletion


## Day 9

- ### Pandas Series.to_frame()
- ### Row Selection, Addition, and Deletion
- ### Selection by Label and by by integer location
- ### Slice Rows
- ### Pandas Series.value_counts()
- ### Pandas DataFrame.append()
- ### Pandas DataFrame.aggregate()

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

