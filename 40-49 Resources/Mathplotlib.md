Tags: [[Aprendizaje Automático]] [[Vision Artificial]] [[Python]]

**Matplotlib** is a Python library for creating customizable data visualizations.

Data Analysts & Data Scientists are now able to use Python to:
1. Process data ([[NumPy]])
2. Organize data ([[Pandas]])
3. Visualize data (Matplotlib) 

## import
``` python
import matplotlib.pyplot
```

``` python
import matplotlib.pyplot as plt
```

## Creating a Plot

Once we've imported Matplotlib, we can create a line plot with:

```python
plt.plot(x, y)
```

Here, `x` and `y` are the data we want to visualize. The `x` values go on the horizontal axis, and the `y` values go on the vertical axis.

For example, if we want to plot how many cups of coffee we drink vs. the energy level:

```python
coffee = np.array([0, 1, 2, 3, 4, 5])
energy = np.array([3, 6, 8, 9, 8.5, 7])

plt.plot(coffee, energy)
```

## Displaying the Plot
There's one more important step! After creating a plot, we need to display it with:
```python
plt.show()
```

Without this line, the visualization won't appear in your notebook.
Here's the complete code:
```python
coffee = np.array([0, 1, 2, 3, 4, 5])
energy = np.array([3, 6, 8, 9, 8.5, 7])

plt.plot(coffee, energy)
plt.show()
```

And here's what it looks like:
![](https://i.imgur.com/c3gfunZ.png)


## Figure and Axes
Every Matplotlib visualization has two core parts: the figure and the axes.

- **Figure** is your blank canvas, the overall window or image.
- **Axes** is the actual plot area inside the canvas where the data gets drawn.

Think of it as a painting: the figure is the canvas and frame, and the axes holds the artwork. 🖼️
![](https://firebasestorage.googleapis.com/v0/b/codedex-io.appspot.com/o/curriculum%2Fimages%2Fmatplotlib-chapter-1%2Fmpl-022.png?alt=media&token=badd2437-9a70-4b69-b8fc-50ccc63678c4)

When we call `plt.plot()`, Matplotlib automatically creates the axes (plot area). We don't need to set it up manually, but getting familiar with the terminology helps when we build more advanced plots later in the course!

## Setting Up the Canvas
Before we plot, we can set up our canvas with:

```python
plt.figure()
```

This creates a blank canvas for our visualization. While it's optional for simple plots, it's a good habit to include it. Later in the course, it becomes essential for more complex visuals.

Here's the complete structure:
```python
plt.figure()           # 1. Set up the canvas
plt.plot(x, y)         # 2. Create the plot
plt.show()             # 3. Display the plot
```

## How Data Points Work
When we pass data to `plt.plot()`, each x and y pair becomes a point on the graph.

So for example:
```python
x_values = np.array([0, 1, 2, 3])
y_values = np.array([3, 1, 4, 2])
```

This creates four points:
- (0, 3) → x is 0, y is 3
- (1, 1) → x is 1, y is 1
- (2, 4) → x is 2, y is 4
- (3, 2) → x is 3, y is 2

Matplotlib then connects these points with a line:
![](https://firebasestorage.googleapis.com/v0/b/codedex-io.appspot.com/o/curriculum%2Fimages%2Fmatplotlib-chapter-1%2Fmpl-02.png?alt=media&token=526d7747-fc27-4881-9cbe-3865489bb471)

The **x-axis** runs horizontally (left to right), and the **y-axis** runs vertically (bottom to top).

## Titles & Axis Labels
Titles
```python
plt.title('Emails received on the week of 12/2')
```

Axis Labels
```python
plt.xlabel('Day of the Week')
plt.ylabel('Number of Emails')
```


## Multiple Lines
We can plot both lines using the `plt.plot()` method twice:

```python
time = np.array([10, 20, 30, 40, 50, 60])

uber = np.array([59.99, 82.43, 66.34, 62.15, 60.99, 55.21])
lyft = np.array([65.81, 76.11, 72.45, 59.22, 55.26, 57.23])

plt.figure()

plt.plot(time, uber)
plt.plot(time, lyft)

plt.show()
```

This creates two lines on the same plot:
![](https://i.imgur.com/RMWFDZ4.png)

## Legends
A **legend** explains what each plotted line represents and helps viewers tell the lines apart.

To create a legend, we first add `label=` to each plot:
```python
plt.plot(time, uber, label='Uber prices')
plt.plot(time, lyft, label='Lyft prices')
```
These are the text that will appear in the legend.

After plotting, call this method:
```python
plt.legend()
```

And the legend will appear in the top-right corner:
![](https://i.imgur.com/wnW5r6F.png)

Full example:
```python
plt.figure()

plt.plot(time, uber, label='Uber prices')
plt.plot(time, lyft, label='Lyft prices')

plt.legend()
plt.show()
```

**Note:** The `.legend()` must come after `.plot()` and before `.show()`.

## Line Colors
Our plots are still looking a bit dry! There are ways to add line colors & line styles to make our visualizations pop more. 🎨

Suppose we have the emails data again:
```python
days = np.array(['Mon', 'Tue', 'Wed', 'Thu', 'Fri'])
emails = np.array([45, 38, 70, 49, 30])
```

We can specify the line colors by using the `color` parameter:
```python
plt.plot(days, emails, color='red')
```

There are three ways to set colors:
- Color names, such as `'red'`, `'green'`, `'blue'`, `'yellow'`, '`orange`, `'skyblue'`.
- Hex codes, such as `#FF5733`.
- Letter codes: `'r'` red, `'g'` green, `'b'` blue, `'c'` cyan, `'m'` magenta, `'y'` yellow, `'k'` black, `'w'` white.

## Line Styles
We're also able to change the line style using the `linestyle=` parameter:
```python
plt.plot(days, emails, color='purple', linestyle='--')
```

Here are some common line styles to choose from:

|Syntax|Line Style|Description|
|---|---|---|
|`'--'`|- - - - - - - - - - -|Dashed|
|`'-.'`|-·-·-·-·-·-·-·-·-·-·-·|Dash-dot|
|`':'`|·······························|Dotted|
|`'-'`|───────|Solid (default)|

Full example:

```python
days = np.array(['Mon', 'Tue', 'Wed', 'Thu', 'Fri'])
emails = np.array([45, 38, 70, 49, 30])

plt.figure()
plt.plot(days, emails, color='purple', linestyle='--')

plt.title('Emails received on the week of 12/2')
plt.xlabel('Day of the Week')
plt.ylabel('Number of Emails')

plt.show()
```

Resulting with a finished plot like this:
![](https://firebasestorage.googleapis.com/v0/b/codedex-io.appspot.com/o/curriculum%2Fimages%2Fmatplotlib-chapter-1%2Fmpl-04.png?alt=media&token=f578279a-1208-4097-8618-2de83619e306)

# Importing Data
So far, we’ve only used NumPy arrays to create line plots, but Matplotlib can work with other types of data, too. Here are two more ways.
### Pandas DataFrames

We can also use a [Pandas](https://codedex.io/pandas) DataFrame to feed data into Matplotlib:
```python
import pandas as pd

df = pd.DataFrame({
  'hour_of_day': ['7', '8', '9', '10', '11', '12', '13', '14', '15', '16', '17', '18'],
  'water_consumed_liters': [0.4, 0.5, 1, 0.2, 0, 0.3, 0, 0, 0, 0.7, 0, 0]
})

plt.figure()
plt.plot(df['hour_of_day'], df['water_consumed_liters'])
plt.show()
```
## CSV Files

![](https://i.imgur.com/pmhET82.png)

Most of the time, you'll work with much larger datasets stored in **CSV** (**C**omma-**S**eparated **V**alues) files. In these cases, you can use Pandas to import the data into your program.

For example, if we have a **weather.csv** file that looks like:
``` terminal
day,temperature
Mon,72
Tue,75
Wed,78
Thu,73
Fri,70
Sat,68
Sun,71
```

We would import it and plot the temperature for each day of the week like this:
```python
import pandas as pd

df = pd.read_csv('weather.csv')

plt.figure()
plt.plot(df['day'], df['temperature'])
plt.show()
```

Pandas allows you to also [import data from Excel and JSON files](https://www.codedex.io/pandas/bonus/importing-datasets). For the upcoming chapters, we'll be sticking to NumPy arrays and CSVs as they're typically the most common.