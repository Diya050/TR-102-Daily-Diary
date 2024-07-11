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
- ### Double Bar Graph

## Day 23

- ### Scatter Plots in Matplotlib
- ### Two ScatterPlots in Matplotlib
- ### Plot() function
- ### Colour Abbreviations
- ### Sub Plots
- ### Plotting with categorical variables

## Day 24

- ### Format Strings: "fmt"
- ### Marker Reference
- ### Marker Size, Edge Color and Face Color
- ### Matplotlib Line: Linestyle
- ### Line Styles, Color and Width
- ### Multiple Lines
- ### Set Font Properties for Title and Labels
- ### Matplotlib Adding Grid Lines
- ### Specify Which Grid Lines to Display
- ### Set Line Properties for the Grid
