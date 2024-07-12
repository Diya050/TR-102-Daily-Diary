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
| '|'    | Vline               |
| '_'    | Hline               |

<br>
- ### Marker Size, Edge Color and Face Color
- ### Matplotlib Line: Linestyle
- ### Line Styles, Color and Width
- ### Multiple Lines
- ### Set Font Properties for Title and Labels
- ### Matplotlib Adding Grid Lines
- ### Specify Which Grid Lines to Display
- ### Set Line Properties for the Grid
