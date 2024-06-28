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
- ### Changing Multiple NaN Values with the forward values which is mentioned in dataframe
- ### Changing Multiple NaN Values with Copying Next Values
- ### Changing Multiple NaN Values with Copying Columns Adjacent to that Value
- ### Changing Multiple NaN Values with Copying Specific No of Values Vertically
