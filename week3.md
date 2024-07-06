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

- ### 
