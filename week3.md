# Daily Dairy: Week 3

## Day 15

- ### na_values Argument

This is used to create a string that is considered by pandas as NaN (Not a Number). By-default pandas consider #N/A, -NaN, -n/a, N/A, NULL etc as NaN value. let’s see the example for better understanding.

```python
import pandas as pd 

df = pd.read_csv('Example.csv') 

print(df)
```
![image](https://github.com/Diya050/TR-102-Daily-Diary/assets/124448340/b34ac1ef-5acd-4c65-8bb3-ed5f2082ea64)

Now the na_values parameter is used to tell pandas they consider “not available” as NaN value and print NaN at the place of “not available”.

```python
import pandas as pd 

df = pd.read_csv('Example.csv', na_values = "not available") 

print(df) 
```
![image](https://github.com/Diya050/TR-102-Daily-Diary/assets/124448340/5aa6e82b-7c13-4727-9cc5-b80de0c636b0)

- ### Writing DataFrame into CSV Files

```python
import pandas as pd

df=pd.DataFrame([[1,2,3,4],[5,6,7,8],[2,7,3,23],[3,6,8,23],[23,23,63,12]],columns=['a1','b1','c1','d1'])

print(df.head())
df.to_csv('export.csv')
df.to_csv('export.csv',index=False) # delete indexes from files.
```

- ### Reading Excel Files into Pandas Dataframe

```python
import pandas as pd
df = pd.read_excel(“data.xlsx”)
print(df)
```

- ### Writing dataframe into excel file with to_excel() method

```python
df.to_excel(“new.xlsx”,sheet_name=”studentdatabase”)
df.to_excel(“new.xlsx”,sheet_name=”studentdatabase”, startrow=2,startcol=2)
```
## Day 16

- ### Changing Multiple NaN Values with the help of Dictionary

```python
import pandas as pd

df = pd.read_csv('data.csv')

new_df=df.fillna({
'Class':'no class given',
'Marks':0,
})

print(new_df)
```

- ### Changing Multiple NaN Values with the forward values which is mentioned in dataframe

```python
import pandas as pd

df=pd.DataFrame({"A":[5,None,None,4],
				"B":[None,None,4,3],
				"C":[4,None,8,5],
				"D":[5,4,2,None]})

print(df.ffill(limit=1))
'''
     A    B    C    D
0  5.0  NaN  4.0  5.0
1  5.0  NaN  4.0  4.0
2  NaN  4.0  8.0  2.0
3  4.0  3.0  5.0  2.0
'''

print(df.ffill(limit=1, axis=1))
'''
     A    B    C    D
0  5.0  5.0  4.0  5.0
1  NaN  NaN  NaN  4.0
2  NaN  4.0  8.0  2.0
3  4.0  3.0  5.0  5.0
'''
```

- ### Changing Multiple NaN Values with Copying Next Values

```python
import pandas as pd

df=pd.DataFrame({"A":[5,None,None,4],
				"B":[None,None,4,3],
				"C":[4,None,8,5],
				"D":[5,4,2,None]})

print(df.bfill(limit=1))
'''
     A    B    C    D
0  5.0  NaN  4.0  5.0
1  NaN  4.0  8.0  4.0
2  4.0  4.0  8.0  2.0
3  4.0  3.0  5.0  NaN
'''

print(df.bfill(limit=1, axis=1))
'''
     A    B    C    D
0  5.0  4.0  4.0  5.0
1  NaN  NaN  4.0  4.0
2  4.0  4.0  8.0  2.0
3  4.0  3.0  5.0  NaN
'''
```

## Day 17

- ### Interpolate Method

Interpolation in Python is a technique used to estimate unknown data points between two known data points. In Python, Interpolation is a technique mostly used to impute missing values in the data frame or series while preprocessing data.

```python
df=pd.DataFrame({"A":[5,None,None,4],
				"B":[None,None,4,3],
				"C":[4,None,8,5],
				"D":[5,4,2,None]})
print(df)

'''
     A    B    C    D
0  5.0  NaN  4.0  5.0
1  NaN  NaN  NaN  4.0
2  NaN  4.0  8.0  2.0
3  4.0  3.0  5.0  NaN
'''

df1 = df.interpolate()
print(df1)

'''
          A    B    C    D
0  5.000000  NaN  4.0  5.0
1  4.666667  NaN  6.0  4.0
2  4.333333  4.0  8.0  2.0
3  4.000000  3.0  5.0  2.0
'''
```

- ### Threshold Parameter

Threshold Parameter is used to keep the rows which are having atleast one value in the row and will drop those rows which are entirely empty.

```python
import pandas as pd

df = pd.read_csv('data.csv')

new_df=df.dropna(thresh=1)
print(new_df)
```

- ### Handle Missing Data : Replace Function

```python
df=pd.DataFrame({"A":[5,None,None,4],
				"B":[None,None,4,-9999],
				"C":[4,None,-1,5],
				"D":[5,"N/A",2,None]})
print(df)

'''
     A       B    C     D
0  5.0     NaN  4.0     5
1  NaN     NaN  NaN   N/A
2  NaN     4.0 -1.0     2
3  4.0 -9999.0  5.0  None
'''

new_df=df.replace([-9999, -1, "N/A", None],np.NaN)
print(new_df)

'''
     A    B    C    D
0  5.0  NaN  4.0  5.0
1  NaN  NaN  NaN  NaN
2  NaN  4.0  NaN  2.0
3  4.0  NaN  5.0  NaN
'''

new_df=df.replace([-9999, -1, "N/A", None],[9999, 1, "Not Available", np.NaN])
print(new_df) # replacing list by list

'''
     A       B    C              D
0  5.0     NaN  4.0              5
1  NaN     NaN  NaN  Not Available
2  NaN     4.0  1.0              2
3  4.0  9999.0  5.0            NaN
'''
```
- ### Concatenate Dataframes

Concatenation means to combine two dataframes into one dataframe.

```python
india_weather=pd.DataFrame({
"city":["Mumbai","Delhi","Banglore"],
"temperature":[32,45,30],
"humidity":[80,50,74]
})
print(india_weather)
'''
       city  temperature  humidity
0    Mumbai           32        80
1     Delhi           45        50
2  Banglore           30        74
'''

us_weather = pd.DataFrame({
"city":["New York","Washington DC","Alaska"],
"temperature":[32,45,30],
"humidity":[80,60,70]
})
print(us_weather)
'''
            city  temperature  humidity
0       New York           32        80
1  Washington DC           45        60
2         Alaska           30        70
'''

df = pd.concat([india_weather,us_weather],ignore_index=True)
print(df)
'''
            city  temperature  humidity
0         Mumbai           32        80
1          Delhi           45        50
2       Banglore           30        74
3       New York           32        80
4  Washington DC           45        60
5         Alaska           30        70
'''

df = pd.concat([india_weather,us_weather],keys=["India","US"])
print(df)
'''
                  city  temperature  humidity
India 0         Mumbai           32        80
      1          Delhi           45        50
      2       Banglore           30        74
US    0       New York           32        80
      1  Washington DC           45        60
      2         Alaska           30        70
'''

print(df.loc['US'])
'''
            city  temperature  humidity
0       New York           32        80
1  Washington DC           45        60
2         Alaska           30        70
'''
```

```python
temperature_df = pd.DataFrame({"city":["mumbai","delhi","bangalore"],
"temperature":[32,45,30],
})
print(temperature_df)

windspeed_df = pd.DataFrame({"city":["mumbai","delhi","bangalore"],
"windspeed":[10,5,9],
})
print(windspeed_df)

df = pd.concat([temperature_df,windspeed_df], axis=1)
print(df)
'''
        city  temperature
0     mumbai           32
1      delhi           45
2  bangalore           30

        city  windspeed
0     mumbai         10
1      delhi          5
2  bangalore          9

        city  temperature       city  windspeed
0     mumbai           32     mumbai         10
1      delhi           45      delhi          5
2  bangalore           30  bangalore          9
'''

s = pd.Series(["Humid","Dry","Rain"],name="event")
print(s)
df = pd.concat([temperature_df,s],axis=1)
print(df)
df = pd.concat([temperature_df,s],axis=0)
print(df)
'''
0    Humid
1      Dry
2     Rain
Name: event, dtype: object

        city  temperature  event
0     mumbai           32  Humid
1      delhi           45    Dry
2  bangalore           30   Rain

        city  temperature  event
0     mumbai         32.0    NaN
1      delhi         45.0    NaN
2  bangalore         30.0    NaN
0        NaN          NaN  Humid
1        NaN          NaN    Dry
2        NaN          NaN   Rain
'''

```

## Day 18

- ### Reshape DataFrame in Pandas: stack()

The stack() method works with the MultiIndex objects in DataFrame, it returns a DataFrame with an index with a new inner-most level of row
labels. It changes the wide table to a long table.

```python
import pandas as pd

df = pd.read_csv("data.csv")
print(df)
df_stacked = df.stack()
print(df_stacked.head(26))

'''
     Duration  Pulse  Maxpulse  Calories
0          60    110       130     409.1
1          60    117       145     479.0
2          60    103       135     340.0
3          45    109       175     282.4
4          45    117       148     406.0
..        ...    ...       ...       ...
164        60    105       140     290.8
165        60    110       145     300.0
166        60    115       145     310.2
167        75    120       150     320.4
168        75    125       150     330.4


[169 rows x 4 columns]
0  Duration     60.0
   Pulse       110.0
   Maxpulse    130.0
   Calories    409.1
1  Duration     60.0
   Pulse       117.0
   Maxpulse    145.0
   Calories    479.0
2  Duration     60.0
   Pulse       103.0
   Maxpulse    135.0
   Calories    340.0
3  Duration     45.0
   Pulse       109.0
   Maxpulse    175.0
   Calories    282.4
4  Duration     45.0
   Pulse       117.0
   Maxpulse    148.0
   Calories    406.0
5  Duration     60.0
   Pulse       102.0
   Maxpulse    127.0
   Calories    300.0
6  Duration     60.0
   Pulse       110.0
dtype: float64
'''

```

- ### Reshape DataFrame in Pandas: unstack()

The unstack() is similar to stack method, It also works with multi-index objects
in dataframe, producing a reshaped DataFrame with a new inner-most level
of column labels.

```python
import pandas as pd

df = pd.read_csv("data.csv")
print(df)
df_stacked = df.stack()
print(df_stacked.head(26))
new_df = df_stacked.unstack()
print(new_df.head(20))

'''
    Duration  Pulse  Maxpulse  Calories
0       60.0  110.0     130.0     409.1
1       60.0  117.0     145.0     479.0
2       60.0  103.0     135.0     340.0
3       45.0  109.0     175.0     282.4
4       45.0  117.0     148.0     406.0
5       60.0  102.0     127.0     300.0
6       60.0  110.0     136.0     374.0
7       45.0  104.0     134.0     253.3
8       30.0  109.0     133.0     195.1
9       60.0   98.0     124.0     269.0
10      60.0  103.0     147.0     329.3
11      60.0  100.0     120.0     250.7
12      60.0  106.0     128.0     345.3
13      60.0  104.0     132.0     379.3
14      60.0   98.0     123.0     275.0
15      60.0   98.0     120.0     215.2
16      60.0  100.0     120.0     300.0
17      45.0   90.0     112.0       NaN
18      60.0  103.0     123.0     323.0
19      45.0   97.0     125.0     243.0
'''
```

- ### Melt Function in Pandas

Melt function is used to transform or reshape data. It is used to transform wide-format data into a long-format,
making it suitable for various analytical tasks.

```python
import pandas as pd

df = pd.read_csv("new.csv")
print(df)
df1 = pd.melt(df, id_vars=["Duration"])
print(df1.head(26))

'''
   Duration  Pulse  Maxpulse  Calories
0        60    110       130     409.1
1        60    117       145     479.0
2        60    103       135     340.0
3        45    109       175     282.4
4        45    117       148     406.0
5        60    102       127     300.5

    Duration  variable  value
0         60     Pulse  110.0
1         60     Pulse  117.0
2         60     Pulse  103.0
3         45     Pulse  109.0
4         45     Pulse  117.0
5         60     Pulse  102.0
6         60  Maxpulse  130.0
7         60  Maxpulse  145.0
8         60  Maxpulse  135.0
9         45  Maxpulse  175.0
10        45  Maxpulse  148.0
11        60  Maxpulse  127.0
12        60  Calories  409.1
13        60  Calories  479.0
14        60  Calories  340.0
15        45  Calories  282.4
16        45  Calories  406.0
17        60  Calories  300.5
'''

```

- ### General Unstacking of pandas dataframe at multi-levels using unstack()

```python
import pandas as pd

data = pd.DataFrame({"cars": ["bmw", "bmw", "benz", "benz"],
"sale_q1 in Cr": [20, 22, 24, 26],
'sale_q2 in Cr': [11, 13, 15, 17]},
columns=["cars", "sale_q1 in Cr",
'sale_q2 in Cr'])
print(data)

stacked_data = data.stack()
print(stacked_data)

stack_level_1 = stacked_data.unstack(level=0)
print(stack_level_1)

stack_level_2 = stacked_data.unstack(level=1)
print(stack_level_2)

'''
   cars  sale_q1 in Cr  sale_q2 in Cr
0   bmw             20             11
1   bmw             22             13
2  benz             24             15
3  benz             26             17

0  cars              bmw
   sale_q1 in Cr      20
   sale_q2 in Cr      11
1  cars              bmw
   sale_q1 in Cr      22
   sale_q2 in Cr      13
2  cars             benz
   sale_q1 in Cr      24
   sale_q2 in Cr      15
3  cars             benz
   sale_q1 in Cr      26
   sale_q2 in Cr      17
dtype: object

                 0    1     2     3
cars           bmw  bmw  benz  benz
sale_q1 in Cr   20   22    24    26
sale_q2 in Cr   11   13    15    17

   cars sale_q1 in Cr sale_q2 in Cr
0   bmw            20            11
1   bmw            22            13
2  benz            24            15
3  benz            26            17
'''

```

- ### GroupBy Unstacking of pandas dataframe with simple unstack()

Whenever we use groupby function on pandas dataframe with more than
one aggregation function per column, the output is usually a multi-indexed
column where as the first index specifies the column name and the second
column index specifies the aggregation function name.

```python
import pandas as pd

# Data
data = pd.DataFrame({
    'cars': ['bmw', 'bmw', 'benz', 'benz'],
    'sale_q1 in Cr': [20, 22, 24, 26],
    'sale_q2 in Cr': [11, 13, 15, 17]
})

# Groupby and aggregate
grouped_data = data.groupby('cars').aggregate({
    'sale_q1 in Cr': ['sum', 'max'],
    'sale_q2 in Cr': ['sum', 'min']
})

# Reshape the data
unstack_level1 = grouped_data.stack(level=0, future_stack=True).unstack()
unstack_level2 = grouped_data.stack(level=1, future_stack=True).unstack()

print(data)
print(grouped_data)
print(unstack_level1)
print(unstack_level2)

'''
   cars  sale_q1 in Cr  sale_q2 in Cr
0   bmw             20             11
1   bmw             22             13
2  benz             24             15
3  benz             26             17

     sale_q1 in Cr     sale_q2 in Cr    
               sum max           sum min
cars                                    
benz            50  26            32  15
bmw             42  22            24  11

               sum                ...           min              
     sale_q1 in Cr sale_q2 in Cr  ... sale_q1 in Cr sale_q2 in Cr
cars                              ...                            
benz            50            32  ...           NaN          15.0
bmw             42            24  ...           NaN          11.0

[2 rows x 6 columns]

     sale_q1 in Cr           sale_q2 in Cr          
               sum   max min           sum max   min
cars                                                
benz          50.0  26.0 NaN          32.0 NaN  15.0
bmw           42.0  22.0 NaN          24.0 NaN  11.0
'''
```

## Day 19

- ### Indexing in Pandas

Indexing in pandas means selecting specific rows and columns from a DataFrame. This can be done in various ways:

  **Types of Multi-Axes Indexing**
   1. **DataFrame\[ \]** - Indexing operator for column selection.
   2. **DataFrame.loc\[ \]** - Indexing by labels.
   3. **DataFrame.iloc\[ \]** - Indexing by positions (integers).
   4. **DataFrame.ix\[ \]** - Deprecated; used for both label and integer-based indexing.

 - ### Indexing Using \[ \]

```python
import pandas as pd

# Selecting a Single Column
data = pd.read_csv("nba.csv", index_col="Name")
first = data["Age"]
print(first)

# Selecting Multiple Columns
data = pd.read_csv("nba.csv", index_col="Name")
first = data[["Age", "College", "Salary"]]
print(first)

```

 - ### Indexing Using .loc[ ]

```python
import pandas as pd

# Selecting a Single Row by Label
data = pd.read_csv("nba.csv", index_col="Name")
first = data.loc["Avery Bradley"]
print(first)

# Selecting Multiple Rows by Label
data = pd.read_csv("nba.csv", index_col="Name")
first = data.loc[["Avery Bradley", "R.J. Hunter"]]
print(first)

# Selecting Rows and Columns by Label
data = pd.read_csv("nba.csv", index_col="Name")
first = data.loc[["Avery Bradley", "R.J. Hunter"], ["Team", "Number", "Position"]]
print(first)

# Selecting All Rows and Some Columns
data = pd.read_csv("nba.csv", index_col="Name")
first = data.loc[:, ["Team", "Number", "Position"]]
print(first)
```

 - ### Indexing Using .iloc[ ]

```python
import pandas as pd

# Selecting a Single Row by Position
data = pd.read_csv("nba.csv", index_col="Name")
row2 = data.iloc[3]
print(row2)

# Selecting Multiple Rows by Position
data = pd.read_csv("nba.csv", index_col="Name")
row2 = data.iloc[[3, 5, 7]]
print(row2)

# Selecting Rows and Columns by Position
data = pd.read_csv("nba.csv", index_col="Name")
row2 = data.iloc[[3, 4], [1, 2]]
print(row2)

# Selecting All Rows and Some Columns by Position
data = pd.read_csv("nba.csv", index_col="Name")
row2 = data.iloc[:, [1, 2]]
print(row2)
```

 - ### Indexing Using .ix[ ] (Deprecated)

```python
# Deprecated, but for historical context:
import pandas as pd

# Selecting a Single Row using .ix[] as .loc[]
data = pd.read_csv("nba.csv", index_col="Name")
first = data.ix["Avery Bradley"]
print(first)

```

## Day 20

- ### Set index
 
```python
import pandas as pd

info = pd.DataFrame({'Name': ['Parker', 'Terry', 'Smith', 'William'],
'Year': [2011, 2009, 2014, 2010],
'Leaves': [10, 15, 9, 4]})
print(info)
'''
      Name  Year  Leaves
0   Parker  2011      10
1    Terry  2009      15
2    Smith  2014       9
3  William  2010       4
'''

print(info.set_index('Name'))
'''
         Year  Leaves
Name                 
Parker   2011      10
Terry    2009      15
Smith    2014       9
William  2010       4
'''

print(info.set_index(['Year', 'Name']))
'''
              Leaves
Year Name           
2011 Parker       10
2009 Terry        15
2014 Smith         9
2010 William       4
'''

print(info.set_index([pd.Index([1, 2, 3, 4]), 'Year']))
'''
           Name  Leaves
  Year                 
1 2011   Parker      10
2 2009    Terry      15
3 2014    Smith       9
4 2010  William       4
'''

a = pd.Series([1, 2, 3, 4])
print(info.set_index([a, a**2]))
'''
         Name  Year  Leaves
1 1    Parker  2011      10
2 4     Terry  2009      15
3 9     Smith  2014       9
4 16  William  2010       4
'''
```
- ### Multiple Index

```python
import pandas as pd

arrays = [['it', 'it', 'of', 'of', 'for', 'for', 'then', 'then'],
['one', 'two', 'one', 'two', 'one', 'two', 'one', 'two']]
tuples = list(zip(*arrays))
index = pd.MultiIndex.from_tuples(tuples, names=['first', 'second'])
print(index)
'''
MultiIndex([(  'it', 'one'),
            (  'it', 'two'),
            (  'of', 'one'),
            (  'of', 'two'),
            ( 'for', 'one'),
            ( 'for', 'two'),
            ('then', 'one'),
            ('then', 'two')],
           names=['first', 'second'])
'''
```

- ### Datetime Index

```python
import pandas as pd

# Reading a CSV file and parsing dates
df = pd.read_csv("aapl.csv", parse_dates=["Date"], index_col="Date")
print(df.head(2))
# Output: (first two rows of the DataFrame)
#                Open      High       Low     Close      Volume
# Date                                                       
# 2017-01-03  115.800003  116.330002  114.760002  116.150002  28781800
# 2017-01-04  115.849998  116.510002  115.750000  116.019997  21118100

print(df.index)
# Output: DatetimeIndex([...], dtype='datetime64[ns]', name='Date', freq=None)

# Selecting data for specific dates or ranges
print(df['2017-06-30'])
# Output: (row data for 2017-06-30)

print(df["2017-01"])
# Output: (rows data for January 2017)

print(df['2017-06'].head())
# Output: (first few rows of June 2017)

print(df['2017-06'].Close.mean())
# Output: (mean closing value for June 2017)

print(df['2017'].head(2))
# Output: (first two rows of 2017 data)

print(df['2017-01-08':'2017-01-03'])
# Output: (data between January 3 and January 8, 2017)

```
- ### DataFrame.pivot()

```python
import pandas as pd

# Creating a DataFrame for pivoting
data = {
    'Date': ['2021-01-01', '2021-01-02', '2021-01-03', '2021-01-04'],
    'Type': ['A', 'B', 'A', 'B'],
    'Value': [10, 20, 30, 40]
}
df = pd.DataFrame(data)
print(df)
# Output:
#          Date Type  Value
# 0  2021-01-01    A     10
# 1  2021-01-02    B     20
# 2  2021-01-03    A     30
# 3  2021-01-04    B     40

# Pivoting the DataFrame
pivoted_df = df.pivot(index='Date', columns='Type', values='Value')
print(pivoted_df)
# Output:
# Type           A     B
# Date                  
# 2021-01-01  10.0   NaN
# 2021-01-02   NaN  20.0
# 2021-01-03  30.0   NaN
# 2021-01-04   NaN  40.0

```

- ### Pandas.pivot_table()

```python
import pandas as pd

# Creating a DataFrame for pivot_table
data = {
    'A': ['foo', 'foo', 'foo', 'foo', 'foo',
          'bar', 'bar', 'bar', 'bar'],
    'B': ['one', 'one', 'one', 'two', 'two',
          'one', 'one', 'two', 'two'],
    'C': ['small', 'large', 'large', 'small',
          'small', 'small', 'large', 'small',
          'large'],
    'D': [1, 2, 2, 3, 3, 4, 5, 6, 7],
    'E': [2.5, 3.5, 4.5, 5.5, 6.5, 7.5, 8.5, 9.5, 10.5]
}
df = pd.DataFrame(data)
print(df)
# Output: (DataFrame content)

# Creating a pivot table
pivot_table_df = pd.pivot_table(df, values='D', index=['A', 'B'],
                                columns=['C'], aggfunc='sum')
print(pivot_table_df)
# Output:
# C         large  small
# A   B                    
# bar one    5.0    4.0
#     two    7.0    6.0
# foo one    4.0    1.0
#     two    NaN    6.0

```

- ### fill_value Parameter

```python
import pandas as pd

# Creating a DataFrame
df = pd.DataFrame({'A': ['foo', 'bar', 'foo', 'bar'],
                   'B': ['one', 'one', 'two', 'two'],
                   'C': ['small', 'large', 'large', 'small'],
                   'D': [1, 2, 3, 4]})
print(df)
# Output: (DataFrame content)

# Creating a pivot table with fill_value
pivot_table_df = pd.pivot_table(df, values='D', index=['A', 'B'],
                                columns=['C'], aggfunc='sum', fill_value=0)
print(pivot_table_df)
# Output:
# C         large  small
# A   B                    
# bar one    2      0
#     two    0      4
# foo one    0      1
#     two    3      0

```

- ### Pandas crosstab()

```python
import pandas as pd

# Creating data for crosstab
a = [1, 2, 2, 2, 3, 3]
b = [1, 1, 2, 2, 2, 2]
c = [1, 2, 2, 1, 1, 1]

# Creating a crosstab
crosstab_df = pd.crosstab(index=[a, b], columns=c)
print(crosstab_df)
# Output:
# col_0  1  2
# row_0        
# 1 1    1  0
# 2 1    0  1
#   2    1  1
# 3 2    2  0

```


## Day 21

- ### Pandas Series.str.slice()

```python
import pandas as pd

# Creating a Series
s = pd.Series(['abcdef', 'ghijkl', 'mnopqr', 'stuvwx'])
print(s)
# Output:
# 0    abcdef
# 1    ghijkl
# 2    mnopqr
# 3    stuvwx
# dtype: object

# Using str.slice() to get substrings
sliced_s = s.str.slice(1, 4)
print(sliced_s)
# Output:
# 0    bcd
# 1    hij
# 2    nop
# 3    tuv
# dtype: object

```

- ### Adding new column to existing DataFrame in Pandas: insert()

```python
import pandas as pd

# Creating a DataFrame
df = pd.DataFrame({'A': [1, 2, 3], 'B': [4, 5, 6]})
print(df)
# Output:
#    A  B
# 0  1  4
# 1  2  5
# 2  3  6

# Adding a new column at a specific location
df.insert(1, 'C', [7, 8, 9])
print(df)
# Output:
#    A  C  B
# 0  1  7  4
# 1  2  8  5
# 2  3  9  6

```

- ### Pandas Add Column to DataFrame using a Dictionary

```python
import pandas as pd

# Creating a DataFrame
df = pd.DataFrame({'A': [1, 2, 3], 'B': [4, 5, 6]})
print(df)
# Output:
#    A  B
# 0  1  4
# 1  2  5
# 2  3  6

# Adding a new column using a dictionary
new_data = {'C': [7, 8, 9]}
df = df.assign(**new_data)
print(df)
# Output:
#    A  B  C
# 0  1  4  7
# 1  2  5  8
# 2  3  6  9

```

- ### Adding More than One columns in Existing Dataframe

```python
import pandas as pd

# Creating a DataFrame
df = pd.DataFrame({'A': [1, 2, 3], 'B': [4, 5, 6]})
print(df)
# Output:
#    A  B
# 0  1  4
# 1  2  5
# 2  3  6

# Adding multiple columns
df[['C', 'D']] = pd.DataFrame({'C': [7, 8, 9], 'D': [10, 11, 12]})
print(df)
# Output:
#    A  B  C   D
# 0  1  4  7  10
# 1  2  5  8  11
# 2  3  6  9  12

```

- ### Pandas DataFrame.truncate

```python
import pandas as pd

# Creating a DataFrame with date range index
df = pd.DataFrame({'A': range(10)}, index=pd.date_range('2020-01-01', periods=10))
print(df)
# Output: (DataFrame content with date index)

# Truncating the DataFrame
truncated_df = df.truncate(before='2020-01-03', after='2020-01-06')
print(truncated_df)
# Output:
#             A
# 2020-01-03  2
# 2020-01-04  3
# 2020-01-05  4
# 2020-01-06  5

```

- ### Delete rows/columns from DataFrame using Pandas.drop()

```python
import pandas as pd

data = pd.DataFrame({'A': ['foo', 'bar', 'baz', 'qux', 'quux', 'corge'],
                     'B': [0, 1, 2, 3, 4, 5],
                     'C': [10.0, 11.1, 12.2, 13.3, 14.4, 15.5]})

# Delete a column
print(data.drop(columns=['B']))
'''
       A     C
0    foo  10.0
1    bar  11.1
2    baz  12.2
3    qux  13.3
4   quux  14.4
5  corge  15.5
'''

# Delete a row
print(data.drop(index=[1, 3]))
'''
       A  B     C
0    foo  0  10.0
2    baz  2  12.2
4   quux  4  14.4
5  corge  5  15.5
'''

```

- ### Pandas Iterate Over Columns of DataFrame

```python
import pandas as pd

data = pd.DataFrame({'A': ['foo', 'bar', 'baz', 'qux', 'quux', 'corge'],
                     'B': [0, 1, 2, 3, 4, 5],
                     'C': [10.0, 11.1, 12.2, 13.3, 14.4, 15.5]})

# Iterate over column names
for column in data:
    print(column)
    
# Iterate over column names and data
for column_name, column_data in data.items():
    print(f"Column name: {column_name}")
    print(column_data)
'''
A
B
C
Column name: A
0      foo
1      bar
2      baz
3      qux
4     quux
5    corge
Name: A, dtype: object
Column name: B
0    0
1    1
2    2
3    3
4    4
5    5
Name: B, dtype: int64
Column name: C
0    10.0
1    11.1
2    12.2
3    13.3
4    14.4
5    15.5
Name: C, dtype: float64
'''

```
