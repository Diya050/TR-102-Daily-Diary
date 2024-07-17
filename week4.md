# Daily Dairy: Week 4

## Day 22

- ### Overview of Matplotlib (Python Plotting Library)

Human minds are more adaptive for the visual representation of data rather than textual data. We
can easily understand things when they are visualized. It is better to represent the data through the
graph where we can analyze the data more efficiently and make the specific decision according to
data analysis.

![image](https://github.com/Diya050/TR-102-Daily-Diary/assets/124448340/5ffe88b5-c9dd-4f7e-8a25-5f5a61815016)

  **Why need data visualization?**
  
  Data visualization can perform below tasks:
  - It identifies areas that need improvement and attention.
  - It clarifies the factors.
  - It helps to understand which product to place where.
  - Predict sales volumes.

- ### Matplotlib Architecture

There are three different layers in the architecture of the matplotlib which are the following:

**Backend Layer:** The backend layer is the bottom layer of the figure, which consists of the implementation of the
various functions that are necessary for plotting. There are three essential classes from the backend
layer FigureCanvas(The surface on which the figure will be drawn), Renderer(The class that takes care
of the drawing on the surface), and Event(It handle the mouse and keyboard events).

**Artist Layer:** The artist layer is the second layer in the architecture. It is responsible for the various plotting
functions, like axis, which coordinates on how to use the renderer on the figure canvas.

**Scripting layer:** The scripting layer is the topmost layer on which most of our code will run. The methods in the
scripting layer, almost automatically take care of the other layers, and all we need to care about is the
current state (figure & subplot).

- ### The General Concept of Matplotlib

A Matplotlib figure can be categorized into various parts as below:

![image](https://github.com/Diya050/TR-102-Daily-Diary/assets/124448340/83c8db61-44ae-4e42-85ce-1bdbf67c3930)

**Figure:** It is a whole figure which may hold one or more axes (plots). We can think of a Figure as a
canvas that holds plots.

**Axes:** A Figure can contain several Axes. It consists of two or three (in the case of 3D) Axis objects.
Each Axes is comprised of a title, an x-label, and a y-label.

**Axis:** Axises are the number of line like objects and responsible for generating the graph limits.

**Artist:** An artist is the all which we see on the graph like Text objects, Line2D objects, and collection
objects. Most Artists are tied to Axes.

- ### Working with Pyplot

The matplotlib.pyplot is the collection command style functions that make matplotlib feel like
working with MATLAB. The pyplot functions are used to make some changes to figure such as create
a figure, creates a plotting area in a figure, plots some lines in a plotting area, decorates the plot
including labels, etc.
It is good to use when we want to plot something quickly without instantiating any figure or Axes.
While working with matplotlib.pyplot, some states are stored across function calls so that it keeps
track of the things like current figure and plotting area, and these plotting functions are directed to
the current axes.

- ### Plotting Graph

```python
import matplotlib.pyplot as plt

plt.plot([1,2,3],[4,5,1])
plt.show()
```
![Figure_1](https://github.com/Diya050/TR-102-Daily-Diary/assets/124448340/300f3c1f-b5c4-4ea4-b501-b5ef53c065f1)

- ### Bar Plot in Matplotlib

```python
import matplotlib.pyplot as plt

X=["Python", "C", "C++", "Java"]
Y=[85,70,60,82]
plt.bar(X, Y)
plt.show()
```
![Figure_2](https://github.com/user-attachments/assets/b69899a6-0e39-4a23-acf0-a69be6a1783b)


```python
import matplotlib.pyplot as plt

X=["Admin", "Sales", "Accounts", "IT"]
Y=[2000,3000,1000,4000]

plt.xlabel("Departments", fontsize=10)
plt.ylabel("No. of Employees", fontsize=10)
plt.title("Departments Chart")
#plt.bar(X, Y, width=0.3, color="g", align="center")

#giving the custom colors
c = ["y", "m", "c", "r"]

#alpha property is used to make the colors dull in barplot graph.
plt.bar(X, Y, width=0.3, align="center", color=c, edgecolor="r", linewidth=2, linestyle="--", alpha=0.6)

plt.legend(["Employee Count"])
plt.show()
```
![Figure_4](https://github.com/user-attachments/assets/920ba07d-65fd-4964-aefb-af20a2d47b0c)

- ### Double Bar Graph

```python
import matplotlib.pyplot as plt
import numpy as np

X=['Python', 'C', 'C++', 'Java']
Y=[85,70,60,82]
Z=[20,30,40,50]
width=0.2
P = np.arange(len(X))
P1 = [j+width for j in P]

plt.xticks(P, X)
plt.xlabel("Languages", fontsize=10)
plt.ylabel("No. of Student Likes", fontsize=10)
plt.title('Bar Graph')
plt.bar(P, Y, width, color='r', label='Popularity in class A')
plt.bar(P1, Z, width, color='y', label='Popularity in class B')

plt.legend()
plt.show()
```
![Figure_6](https://github.com/user-attachments/assets/3daa8b65-098a-46a5-aa6e-b75e69f3ddb6)

## Day 23

- ### Scatter Plots in Matplotlib

 ```python
import matplotlib.pyplot as plt

X=[1,2,3,4,5,6]
Y=[2,3,1,4,5,6]
Colors=[10,49,20,29,56,40]
Size=[170,200,300,400,150,300]

plt.scatter(X, Y, c=Colors, s=Size, alpha=0.8, marker="*", edgecolor="y", linewidth=1 , cmap="viridis")

plt.colorbar()
plt.title("Scatterplot Graph",fontsize=12)
plt.xlabel("Days", fontsize=12)
plt.ylabel("No.", fontsize=12)
plt.show()
 ```
![Figure_5](https://github.com/user-attachments/assets/a9ac1373-f21b-4ea0-9c5d-e1c70defc87b)

- ### Two ScatterPlots in Matplotlib

```python
import matplotlib.pyplot as plt

X=[1,2,3,4,5,6]
Y=[2,3,1,4,5,6]
Z=[3,2,4,5,1,2]
Colors1=[10,49,30,29,56,30]
Sizes=[100,200,300,400,150,500]

plt.scatter(X,Y,c=Colors1,s=200 ,cmap="viridis",alpha=0.5)
plt.scatter(X,Z,color="r",marker="*", s=Sizes,alpha=0.5)

t=plt.colorbar()
t.set_label("ColorBar",fontsize=12)
plt.title("Scatterplot",fontsize=12)
plt.xlabel("Day",fontsize=15)
plt.ylabel("No.",fontsize=15)
```

![image](https://github.com/user-attachments/assets/1625c549-7474-4939-b4e7-88e756f3a996)

- ### Plot() function

```python
import matplotlib.pyplot as plt

xpoints = np.array([0, 6])
ypoints = np.array([0, 250])
plt.plot(xpoints, ypoints)
plt.show()
```
![Figure_3](https://github.com/user-attachments/assets/519b978f-304c-4748-ad71-e98dcdbf9f27)

There is an optional third argument, which is a format string that indicates the color and line type of
the plot. The default format string is 'b-'which is the solid blue as you can observe in the above
plotted graph. Let's consider the following example where we plot the graph with the red circle.

```python
import matplotlib.pyplot as plt

plt.plot([1, 2, 3, 3.5, 4,5], [1, 4, 9, 2, 16,25], 'ro:') # "r"- red, "o"- circle, ":"- dotted line
plt.axis([0, 6, 0, 20])
plt.show()
```

![image](https://github.com/user-attachments/assets/b4cb5093-9402-4322-ae99-9e646d3df656)


<br>


- ### Colour Abbreviations

Here is the Markdown code with the data included:

| Character | Color   |
|-----------|---------|
| "b"       | Blue    |
| "g"       | Green   |
| "r"       | Red     |
| "c"       | Cyan    |
| "m"       | Magenta |
| "y"       | Yellow  |
| "k"       | Black   |
| "w"       | White   |


- ### Sub Plots

The subplot() function takes three arguments that describes the layout of the figure. The layout is organized in rows and columns, which are represented by the first and second argument.
The third argument represents the index of the current plot.

```python
plt.subplot(1, 2, 1)
#the figure has 1 row, 2 columns, and this plot is the first plot.

plt.subplot(1, 2, 2)
#the figure has 1 row, 2 columns, and this plot is the second plot.
```

```python
import matplotlib.pyplot as plt

names = ['Abhishek', 'Himanshu', 'Devansh']
marks= [87,50,98]

plt.subplot(311)
plt.bar(names, marks)

plt.subplot(312)
plt.scatter(names, marks)

plt.subplot(313)
plt.plot(names, marks)

plt.suptitle('Categorical Plotting')
plt.show()
```
![image](https://github.com/user-attachments/assets/4b19368a-2e57-4fce-8355-c65400156b99)

```python
import matplotlib.pyplot as plt

names = ['Abhishek', 'Himanshu', 'Devansh']
marks= [87,50,98]

plt.subplot(131)
plt.bar(names, marks)

plt.subplot(132)
plt.scatter(names, marks)

plt.subplot(133)
plt.plot(names, marks)

plt.suptitle('Categorical Plotting')
plt.show()
```
![image](https://github.com/user-attachments/assets/14ddb611-22b6-4eed-a968-882cfd5eeab7)


## Day 24

- ### Format Strings: "fmt"

We can also use the shortcut string notation parameter to specify the marker.
This parameter is also called fmt, and is written with this syntax: `marker|line|color`

<br>

| Example format String | Description                                                      |
|-----------------------|------------------------------------------------------------------|
| 'b'                   | Using for the blue marker with default shape.                    |
| 'ro'                  | Red circle                                                       |
| '-g'                  | Green solid line                                                 |
| '--'                  | A dashed line with the default color                             |
| '^k:'                 | Black triangle up markers connected by a dotted line             |

```python
import matplotlib.pyplot as plt

ypoints = np.array([3, 8, 1, 10])
plt.plot(ypoints, 'H:r', ms=10)
plt.show()
```

![image](https://github.com/user-attachments/assets/7b882500-d6b5-4aab-8408-e6a666dc1960)



- ### Marker Reference

| Marker | Description         |
|--------|---------------------|
| 'o'    | Circle              |
| '*'    | Star                |
| '.'    | Point               |
| ','    | Pixel               |
| 'x'    | X                   |
| 'X'    | X (filled)          |
| '+'    | Plus                |
| 'P'    | Plus (filled)       |
| 's'    | Square              |
| 'D'    | Diamond             |
| 'd'    | Diamond (thin)      |
| 'p'    | Pentagon            |
| 'H'    | Hexagon             |
| 'h'    | Hexagon             |
| 'v'    | Triangle Down       |
| '^'    | Triangle Up         |
| '<'    | Triangle Left       |
| '>'    | Triangle Right      |
| '1'    | Tri Down            |
| '2'    | Tri Up              |
| '3'    | Tri Left            |
| '4'    | Tri Right           |
| '\|'    | Vline               |
| '_'    | Hline               |

<br>
- ### Marker Size, Edge Color and Face Color

```python
import matplotlib.pyplot as plt
import numpy as np

ypoints = np.array([3, 8, 1, 10])
plt.plot(ypoints, marker = 'o', ms = 20, mec = 'b', mfc = 'y')
plt.show()
```
![image](https://github.com/user-attachments/assets/482c08d5-02be-44f5-9746-d74a76d314e6)


- ### Matplotlib Line: Linestyle

```python
import matplotlib.pyplot as plt
import numpy as np

ypoints = np.array([3, 8, 1, 10])
plt.plot(ypoints, linestyle = 'dotted')
plt.show()
```
![image](https://github.com/user-attachments/assets/9bbd8781-ea88-477f-ace1-3dc2d309eec2)

| Style    | Syntax |
|----------|--------|
| solid(default) | '-'    |
| dotted   | ':'    |
| dashed   | '--'   |
| dashdot  | '-.'   |
| None     | '' or ' ' |


- ### Line Color and Width

```python
import matplotlib.pyplot as plt
import numpy as np

ypoints = np.array([3, 8, 1, 10])
plt.plot(ypoints, c="b", lw=10)
plt.show()
```
![image](https://github.com/user-attachments/assets/f58bd160-166c-4f2f-96e4-a03eb57307b1)


- ### Multiple Lines

```python
import matplotlib.pyplot as plt
import numpy as np

y1 = np.array([3, 8, 1, 10])
y2 = np.array([6, 2, 7, 11])
plt.plot(y1)
plt.plot(y2)
plt.show()
```
![image](https://github.com/user-attachments/assets/5d745941-fec5-4cfc-a56b-73739f8f1c16)


- ### Set Font Properties for Title and Labels

```python
import matplotlib.pyplot as plt
import numpy as np

x = np.array([80, 85, 90, 95, 100, 105, 110, 115, 120, 125])
y = np.array([240, 250, 260, 270, 280, 290, 300, 310, 320, 330])
font1 = {'family':'serif','color':'blue','size':20}
font2 = {'family':'serif','color':'darkred','size':15}
plt.title("Sports Watch Data", fontdict = font1)
plt.xlabel("Average Pulse", fontdict = font2)
plt.ylabel("Calorie Burnage", fontdict = font2)
plt.plot(x, y)
plt.show()
```
![image](https://github.com/user-attachments/assets/5bd1fe6e-dacf-4ad5-a861-4f0c80c3367b)

- ### Matplotlib Adding Grid Lines

```python
import matplotlib.pyplot as plt
import numpy as np

x = np.array([80, 85, 90, 95, 100, 105, 110, 115, 120, 125])
y = np.array([240, 250, 260, 270, 280, 290, 300, 310, 320, 330])
plt.title("Sports Watch Data")
plt.xlabel("Average Pulse")
plt.ylabel("Calorie Burnage")
plt.plot(x, y)
plt.grid()
plt.show()
```
![image](https://github.com/user-attachments/assets/5de73c3d-beaa-4f7d-a3db-4270aac25aa9)

- ### Specify Which Grid Lines to Display

```python
import matplotlib.pyplot as plt
import numpy as np

x = np.array([80, 85, 90, 95, 100, 105, 110, 115, 120, 125])
y = np.array([240, 250, 260, 270, 280, 290, 300, 310, 320, 330])
plt.title("Sports Watch Data")
plt.xlabel("Average Pulse")
plt.ylabel("Calorie Burnage")
plt.plot(x, y)
plt.grid(axis = 'x')
plt.show()
```
![image](https://github.com/user-attachments/assets/d8886f78-6f91-45b4-b133-2db229e44ac7)

- ### Set Line Properties for the Grid

```python
import matplotlib.pyplot as plt
import numpy as np

x = np.array([80, 85, 90, 95, 100, 105, 110, 115, 120, 125])
y = np.array([240, 250, 260, 270, 280, 290, 300, 310, 320, 330])
plt.title("Sports Watch Data")
plt.xlabel("Average Pulse")
plt.ylabel("Calorie Burnage")
plt.plot(x, y)
plt.grid(color = 'green', linestyle = '--', linewidth = 0.5)
plt.show()
```
![image](https://github.com/user-attachments/assets/51b1a365-a1cd-41c4-91aa-d95599933a37)


## Day 25

- ### Histogram Chart in Matplotlib

A histogram is a graph showing frequency distributions. It shows the number of observations within each given interval.

In Matplotlib, we use the `hist()` function to create histograms. The `hist()` function will use an array of numbers to create a histogram, the array is sent into the function as an argument.

For simplicity, we use NumPy to randomly generate an array with 250 values, where the values will concentrate around 170, and the standard deviation is 10.

```python
import matplotlib.pyplot as plt
import numpy as np

x = np.random.normal(170, 10, 250)
plt.hist(x, color="b", edgecolor="r")
plt.title("Histogram")
plt.xlabel("Data in X axis")
plt.ylabel("Data in Y axis")
plt.show()
```

- ### Using 'bins', 'cumulative', and 'auto' Parameter in Histogram:

```python
import matplotlib.pyplot as plt
import numpy as np

n = [10, 20, 30, 34, 51, 41, 35, 42, 46, 49, 55, 56, 59, 60, 71, 75, 76, 79, 80]
l = [10, 20, 30, 40, 50, 60, 70]
plt.hist(n, color="r", bins=l)
# defining the range of x axis
plt.hist(n, color="b", bins='auto', range=(0, 200), edgecolor="r", align="left")  # mid, right
# cumulative parameter is used to reverse the frequency of data
plt.hist(n, color="b", bins='auto', range=(0, 200), edgecolor="r", cumulative=-1, bottom=10)
# if you want to start the y axis from 10 then you should use bottom parameter.
# we can use different types of histograms in our plot
plt.hist(n, color="b", edgecolor="r", cumulative=-1, bottom=10, histtype="step", orientation="horizontal", rwidth=0.8, label="python")
plt.legend()
plt.xlabel("Data in X axis")
plt.ylabel("Data in Y axis")
# axvline parameter used to divide the histogram
plt.axvline(45, color="r", label="line")
plt.grid()
plt.show()
```

- ### Formatting the Line graph With the Help of Modules

We can customize the graph by importing the style module. The style module will be built into a matplotlib installation. It contains various functions to make the plot more attractive. In the below program, we are using the style module:

```python
from matplotlib import pyplot as plt
from matplotlib import style

style.use('ggplot')
x = [16, 8, 10]
y = [8, 16, 6]
x2 = [8, 15, 11]
y2 = [6, 15, 7]
plt.plot(x, y, 'r', label='line one', linewidth=5)
plt.plot(x2, y2, 'm', label='line two', linewidth=5)
plt.title('Epic Info')
fig = plt.figure()
plt.ylabel('Y axis')
plt.xlabel('X axis')
plt.legend()
plt.grid(True, color='k')
plt.show()
```

```python
from matplotlib import pyplot as plt
from matplotlib import style

style.use('ggplot')
x = [5, 8, 10]
y = [12, 16, 6]
x2 = [6, 9, 11]
y2 = [7, 15, 7]
plt.bar(x, y, color='y', align='center')
plt.bar(x2, y2, color='c', align='center')
plt.title('Information')
plt.ylabel('Y axis')
plt.xlabel('X axis')
plt.show()
```

- ### Horizontal Bar Graphs

```python
from matplotlib import pyplot as plt

players = ['Virat', 'Rohit', 'Shikhar', 'Hardik']
runs = [51, 87, 45, 67]
plt.barh(players, runs, color='green')
plt.title('Score Card')
plt.xlabel('Players')
plt.ylabel('Runs')
plt.show()
```

- ### Pie Chart

A Pie Chart can only display one series of data. Pie charts show the size of items (called wedge) in one data series, proportional to the sum of the items. The data points in a pie chart are shown as a percentage of the whole pie. Matplotlib API has a pie() function that generates a pie diagram representing data in an array.

The size of each wedge is determined by comparing the value with all the other values, by using this formula:
The value divided by the sum of all values: `x/sum(x)`

```python
from matplotlib import pyplot as plt
import numpy as np

fig = plt.figure()
ax = fig.add_axes([0, 0, 1, 1])
ax.axis('equal')
langs = ['C', 'C++', 'Java', 'Python', 'PHP']
students = [23, 17, 35, 29, 12]
ax.pie(students, labels=langs)
plt.show()
```

```python
import matplotlib.pyplot as plt

x = [10, 20, 30, 40]
y = ["C", "C++", "Java", "Python"]
ex = [0.4, 0.0, 0.0, 0.0]
c = ["r", "b", "g", "y"]
plt.pie(x, labels=y, explode=ex)
# to show percentage in graph, to give shadow and defining radius in graph
plt.pie(x, labels=y, explode=ex, colors=c, autopct="%0.1f%%", shadow=True, radius=1.5, labeldistance=1.1, startangle=90, textprops={"fontsize": 15}, counterclock=False, wedgeprops={"linewidth": 8, "width": 2}, center=(3, 6), rotatelabels=True)
plt.title("Piechart of Subjects")
plt.legend(loc=2)
plt.show()
```

```python
import matplotlib.pyplot as plt

x = [10, 20, 30, 40]
x1 = [40, 30, 20, 10]
y = ["Sanya", "Karan", "Kartik", "Kiran"]
plt.pie(x, labels=y, radius=1)
plt.pie(x1, labels=y, radius=0.5)
plt.show()
```

## Day 26

- ### Stem Plot

A stem plot in Matplotlib is useful for displaying data points along with their stem lines.

```python
# Importing the required library
import matplotlib.pyplot as plt

# Defining the data points
X = [1, 2, 3, 4, 5, 6]
Y = [2, 2, 5, 6, 4, 3]

# Creating the stem plot with various formatting options
plt.stem(X, Y, linefmt=":", markerfmt="ro", bottom=1, basefmt="g", label="python", orientation="horizontal")

# Adding a legend
plt.legend()

# Displaying the plot
plt.show()
```

- ### Box Plot in Matplotlib

A box plot, also known as a whisker plot, displays a summary of a set of data containing the minimum, first quartile, median, third quartile, and maximum. In a box plot, a box is drawn from the first quartile to the third quartile. A vertical line goes through the box at the median. The whiskers go from each quartile to the minimum or maximum.

Boxplots are a measure of how well data is distributed across a data set. This divides the data set into three quartiles. This graph represents the minimum, maximum, average, first quartile, and the third quartile in the data set. Boxplot is also useful in comparing the distribution of data in a data set by drawing a boxplot for each of them.

`Example:` Finding the 5-number summary and making the box plot of the data

  - Define the data set: `25 28 29 29 30 34 35 35 37 38`

  - Find the median: The median is the mean of the middle two numbers. `(30 + 34) / 2 = 32`

  - Find the quartiles: The first quartile (Q1) is the median of the data points to the left of the median.

`25 28 29 29 30`<br>
`Q1 = 29`
  - The third quartile (Q3) is the median of the data points to the right of the median.

`34 35 35 37 38`
 <br> `Q3 = 35`

 - Complete the 5-number summary by finding the min and max:

   - Minimum value: 25
   - Maximum value: 38
   - 5-number summary: 25 29 32 35 38

 - Draw a box from Q1 to Q3 with a vertical line through the median:

   - Q1 = 29
   - Median = 32
   - Q3 = 35

 - Draw a whisker from Q1 to the min and from Q3 to the max: Min is 25 and max is 38


```python
# Importing the required library
import matplotlib.pyplot as plt

# Defining the data points
X = [10, 20, 30, 40, 50, 60, 70]

# Creating the box plot with various formatting options
plt.boxplot(X, notch=True, vert=False, labels=["python"], patch_artist=True, showmeans=True, sym="g+", 
            boxprops=dict(color="r"), capprops=dict(color="r"), whiskerprops=dict(color="r"))

# Displaying the plot
plt.show()
```

**Properties of Box Plot**

   - **X:** The data to be plotted as a boxplot.
   - **notch=True:** Adds notches to the box to indicate the confidence interval around the median.
   - **vert=False:** Creates a horizontal boxplot instead of the default vertical one.
   - **labels=["python"]:** Labels the boxplot with the name "python".
   - **patch_artist=True:** Allows customization of the boxplot's appearance.
   - **showmeans=True:** Displays the mean value of the data in the boxplot.
   - **sym="g+":** Specifies the symbol and color for outliers ("g+" means green plus signs).
   - **boxprops=dict(color="r"):** Sets the color of the box to red.
   - **capprops=dict(color="r"):** Sets the color of the caps (the horizontal lines at the ends of the whiskers) to red.
   - **whiskerprops=dict(color="r"):** Sets the color of the whiskers (the lines extending from the box to the caps) to red.

     
## Day 27

- ### np.random.normal()

```python
import matplotlib.pyplot as plt
import numpy as np
dataSet = np.random.normal(100, 25, 200)
print(dataSet)
```
The line of code np.random.normal(100, 25, 200) uses the numpy library to generate
random numbers that follow a normal (Gaussian) distribution. Let's break down the parameters
and the overall meaning of the code:
  - **np.random.normal:** This function generates random samples from a normal (Gaussian) distribution.
  - **Parameters:**
     `100:` This is the mean (average) of the distribution.
     `25:` This is the standard deviation of the distribution, which measures the spread of the data around the mean.
     `200:` This specifies the number of random samples to generate.

A normal distribution is a bell-shaped distribution that is symmetric around its mean. Most of
the data points lie close to the mean, and the probability of data points decreases as you move
further from the mean. The spread of the data is determined by the standard deviation:
  - A smaller standard deviation means the data points are closer to the mean.
  - A larger standard deviation means the data points are more spread out.

```python
import matplotlib.pyplot as plt
import numpy as np
dataSet = np.random.normal(100, 25, 200)
print(dataSet)

figure = plt.figure(figsize =(10, 8))
# Figure will be 10 inches wide and 8 inches tall.
plt.boxplot(dataSet)
plt.show()
```

- ### Multiple Box Plots

```python
import matplotlib.pyplot as plt
import numpy as np

dataSet1 = np.random.normal(100, 10, 220)
dataSet2 = np.random.normal(80, 20, 200)
dataSet3 = np.random.normal(60, 35, 220)
dataSet4 = np.random.normal(50, 40, 200)
dataSet = [dataSet1, dataSet2, dataSet3, dataSet4]

figure = plt.figure(figsize =(10, 7))
ax = figure.add_axes([0, 0, 1, 1])
bp = ax.boxplot(dataSet)
plt.show()
```
- ### Styling Components of Box Plot

```python
import matplotlib.pyplot as plt
import numpy as np

# These lines generate four datasets of random numbers drawn from normal distributions with different means and standard deviations
dataSet1 = np.random.normal(100, 10, 220)
dataSet2 = np.random.normal(80, 20, 200)
dataSet3 = np.random.normal(60, 35, 220)
dataSet4 = np.random.normal(50, 40, 200)

# This line combines the four datasets into a single list dataSet.
dataSet = [dataSet1, dataSet2, dataSet3, dataSet4]

# This line creates a new figure for the plot with a specified size of 10 inches by 7 inches. The figure object is stored in the variable figure
figure = plt.figure(figsize =(10, 7))

# This line adds a subplot to the figure. The argument 111 means that the figure has one row, one column, and this subplot is the first (and only) subplot.
ax = figure.add_subplot(111)
bp = ax.boxplot(dataSet, patch_artist = True,notch ='True', vert = 0)

colors = ['#00FF00','#0F00FF', '#F00FF0','#FFFF0F']
for patch, color in zip(bp['boxes'], colors):
  patch.set_facecolor(color)

for whisker in bp['whiskers']:
  whisker.set(color ='#8E008B',linewidth = 1.4,linestyle =":")

for cap in bp['caps']:
  cap.set(color ='#8E008B',linewidth = 2.1)

for median in bp['medians']:
  median.set(color ='blue',linewidth = 3)

for flier in bp['fliers']:
  flier.set(marker ='D',color ='#d7298c',alpha = 0.6)

ax.set_yticklabels(['dataSet1', 'dataSet2','dataSet3', 'dataSet4'])
plt.title("Customized box plot using attributes")
ax.get_xaxis().tick_bottom()
ax.get_yaxis().tick_left()
plt.show()
```

## Day 28

- ### Matplotlib - Object-oriented Interface with the Help Of Figure Classes

While it is easy to quickly generate plots with the matplotlib.pyplot module, the use of object-oriented
approach is recommended as it gives more control and customization of your plots. Most of the
functions are also available in the matplotlib.axes.Axes class.
The main idea behind using the more formal object-oriented method is to create figure objects and
then just call methods or attributes off of that object. This approach helps better in dealing with a
canvas that has multiple plots on it.

```python
from matplotlib import pyplot as plt
import numpy as np
import math

x = np.arange(0, math.pi*2, 0.05)
y = np.sin(x)

fig = plt.figure()
ax = fig.add_axes([0,0,1,1])
ax.plot(x,y)
ax.set_title("sine wave")
ax.set_xlabel('angle')
ax.set_ylabel('sine')
plt.show()
```

- ### Adding and Customizing Axes

```python
fig = plt.figure()
ax = fig.add_axes([0,0,1,1])
ax.set_title("Title")
ax.set_xlabel("X-axis")
ax.set_ylabel("Y-axis")

```

- ### Multiplots in Matplotlib
  - **Using subplot**
 
```python
import matplotlib.pyplot as plt

plt.subplot(211)
plt.plot(range(12))
plt.subplot(212, facecolor='y')
plt.plot(range(12))

```

  - **Using add_subplot**

```python
fig = plt.figure()
ax1 = fig.add_subplot(111)
ax1.plot([1,2,3])
ax2 = fig.add_subplot(221, facecolor='y')
ax2.plot([1,2,3])

```

  - **Using subplots**

 ```python
import matplotlib.pyplot as plt
import numpy as np

fig, a = plt.subplots(2,2)
x = np.arange(1,5)
a[0][0].plot(x, x*x)
a[0][0].set_title('square')
a[0][1].plot(x, np.sqrt(x))
a[0][1].set_title('square root')
a[1][0].plot(x, np.exp(x))
a[1][0].set_title('exp')
a[1][1].plot(x, np.log10(x))
a[1][1].set_title('log')
plt.show()

```

- ### Formatting Axes
  - **Logarithmic Scale and Label Padding**

```python
import matplotlib.pyplot as plt
import numpy as np

fig, axes = plt.subplots(1, 2, figsize=(10,4))
x = np.arange(1,5)

axes[0].plot(x, np.exp(x))
axes[0].plot(x, x**2)
axes[0].set_title("Normal scale")
axes[0].set_xlabel("x axis")
axes[0].set_ylabel("y axis")
axes[0].xaxis.labelpad = 10

axes[1].plot(x, np.exp(x))
axes[1].plot(x, x**2)
axes[1].set_yscale("log")
axes[1].set_title("Logarithmic scale (y)")
axes[1].set_xlabel("x axis")
axes[1].set_ylabel("y axis")

plt.show()

```
  
  - **Customizing Spines**

```python
fig = plt.figure()
ax = fig.add_axes([0,0,1,1])
ax.spines['bottom'].set_color('blue')
ax.spines['left'].set_color('red')
ax.spines['left'].set_linewidth(2)
ax.spines['right'].set_color(None)
ax.spines['top'].set_color(None)
ax.plot([1,2,3,4,5])
plt.show()

```
  
  - **Setting Limits**
  
```python
import matplotlib.pyplot as plt
import numpy as np

fig = plt.figure()
a1 = fig.add_axes([0,0,1,1])
x = np.arange(1,10)
a1.plot(x, np.exp(x),'r')
a1.set_title('exp')
a1.set_ylim(0,10000)
a1.set_xlim(0,10)
plt.show()

``` 

  - **Setting Ticks and Tick Labels**
  
```python
import matplotlib.pyplot as plt
import numpy as np
import math

x = np.arange(0, math.pi*2, 0.05)
fig = plt.figure()
ax = fig.add_axes([0.1, 0.1, 0.8, 0.8])
y = np.sin(x)
ax.plot(x, y)
ax.set_xlabel('angle')
ax.set_title('sine')
ax.set_xticks([0,2,4,6])
ax.set_xticklabels(['zero','two','four','six'])
ax.set_yticks([-1,0,1])
plt.show()

```

  - **Twin Axes**
  
```python
import matplotlib.pyplot as plt
import numpy as np

fig = plt.figure()
a1 = fig.add_axes([0,0,1,1])
x = np.arange(1,11)
a1.plot(x,np.exp(x))
a1.set_ylabel('exp')

a2 = a1.twinx()
a2.plot(x, np.log(x),'ro-')
a2.set_ylabel('log')
fig.legend(labels = ('exp','log'),loc='upper left')
plt.show()

``` 
  
  - **Contour Plot**

```python
import numpy as np
import matplotlib.pyplot as plt

xlist = np.linspace(-3.0, 3.0, 100)
ylist = np.linspace(-3.0, 3.0, 100)
X, Y = np.meshgrid(xlist, ylist)
Z = np.sqrt(X**2 + Y**2)

plt.contour(X, Y, Z)
plt.show()

```
