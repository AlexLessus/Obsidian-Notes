Tags: [[Aprendizaje Automático]] [[Vision Artificial]] [[Python]]

**Matplotlib** is a Python library for creating customizable data visualizations.

Data Analysts & Data Scientists are now able to use Python to:
1. Process data ([[Numpy]])
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

# Personalización
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

## Ticks - Marcas
Marcas en el eje x, en vez de 1000 muestra 1k
``` python
# Scatter plot
plt.scatter(gdp_cap, life_exp)

# Previous customizations
plt.xscale('log') 
plt.xlabel('GDP per Capita [in USD]')
plt.ylabel('Life Expectancy [in years]')
plt.title('World Development in 2007')
  
# Definition of tick_val and tick_lab
tick_val = [1000, 10000, 100000]
tick_lab = ['1k', '10k', '100k']
  
# Adapt the ticks on the x-axis
plt.xticks(tick_val, tick_lab)
  
# After customizing, display the plot
plt.show()
```
![[Pasted image 20260225212015.png]]

## Tamaños
Cambiar el tamaño de los puntos
``` python
# Import numpy as np
import numpy as np

# Store pop as a numpy array: np_pop
np_pop = np.array(pop)
  
# Double np_pop
np_pop = np_pop * 2

# Update: set s argument to np_pop  s=size
plt.scatter(gdp_cap, life_exp, s = np_pop)

# Previous customizations
plt.xscale('log') 
plt.xlabel('GDP per Capita [in USD]')
plt.ylabel('Life Expectancy [in years]')
plt.title('World Development in 2007')

plt.xticks([1000, 10000, 100000],['1k', '10k', '100k'])

# Display the plot
plt.show()
```


## Colores
`c=col` col es un diccionario de colores
``` python
dict = {
    'Asia':'red',
    'Europe':'green',
    'Africa':'blue',
    'Americas':'yellow',
    'Oceania':'black'
}
```

``` Python
# Specify c and alpha inside plt.scatter()
plt.scatter(x = gdp_cap, y = life_exp, s = np.array(pop) * 2, c=col, alpha = 0.8)

# Previous customizations
plt.xscale('log') 
plt.xlabel('GDP per Capita [in USD]')
plt.ylabel('Life Expectancy [in years]')
plt.title('World Development in 2007')
plt.xticks([1000,10000,100000], ['1k','10k','100k'])

# Show the plot
plt.show()
```
![[Pasted image 20260225212828.png]]

## Otras personalizaciónes
```python
# Scatter plot
plt.scatter(x = gdp_cap, y = life_exp, s = np.array(pop) * 2, c = col, alpha = 0.8)

# Previous customizations
plt.xscale('log') 
plt.xlabel('GDP per Capita [in USD]')
plt.ylabel('Life Expectancy [in years]')
plt.title('World Development in 2007')
plt.xticks([1000,10000,100000], ['1k','10k','100k'])

# Additional customizations
plt.text(1550, 71, 'India')
plt.text(5700, 80, 'China')

# Add grid() call
plt.grid(True)

# Show the plot
plt.show()
```
![[Pasted image 20260225213018.png]]


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

## Scatter Plot
We can use `plt.scatter()` to look at the number of hours spent studying vs. the test score and _see_ if there's a relationship.

For example:

```python
data = {
  'hours': [1, 2, 3, 4, 5, 6, 7, 8],
  'scores': [55, 30, 56, 70, 72, 81, 81, 92]
}

df = pd.DataFrame(data)

plt.scatter(df['hours'], df['scores'])

plt.title('Study Time vs. Test Score')
plt.xlabel('Study Time (Hours)')
plt.ylabel('Test Score')

plt.show()
```

The code will create this scatter plot:
![](https://firebasestorage.googleapis.com/v0/b/codedex-io.appspot.com/o/curriculum%2Fimages%2Fmatplotlib-chapter-2%2Fmpl-2-01.png?alt=media&token=7ba393b7-fa58-42e9-9942-129c96cdd93a)


## Bar Graph
A **bar graph** is also a common visualization you may have seen in math class. It uses rectangular bars to compare categories, making it easy to see differences at a glance. 📊

We can use `plt.bar()` to create a bar graph:
```python
data = {
  'major': ['Math', 'Physics', 'CS', 'Chemistry', 'Biology'],
  'num_students': [25, 30, 20, 15, 10]
}

df = pd.DataFrame(data)

plt.bar(df['major'], df['num_students'])

plt.title('Number of Students in Each Major')
plt.xlabel('Major')
plt.ylabel('Number of Students')

plt.show()
```

The code will create this:

![](https://firebasestorage.googleapis.com/v0/b/codedex-io.appspot.com/o/curriculum%2Fimages%2Fmatplotlib-chapter-2%2Fmpl-2-02.png?alt=media&token=ec6c4b1b-1fc2-4bd6-b320-c58f21bb0de9)


# Pie Charts
A **pie chart** shows different categories as slices of a circle. 🥧

Let's say we surveyed people: “What's your favorite pie?” and we got the following votes:
```python
flavors = np.array(['pumpkin', 'apple', 'blueberry', 'pecan', 'key lime', 'chocolate cream'])
votes = np.array([24, 23, 11, 12, 10, 14])
```

We can create a pie chart using `plt.pie()`:
```python
plt.pie(votes, labels=flavors)

plt.title('Favorite Pie Flavors 😋')

plt.show()
```

This will look like:
![](https://i.imgur.com/SkONvhR.png)

### Adding Percentages
To make it easier to see the breakdown, we can add percentages with:

```python
plt.pie(votes, labels=flavors, autopct='%1.1f%%')
```

`autopct` means automatic percentages with:
- `%d%%`: no decimals
- `%.1f%%`: 1 decimal
- `%.2f%%`: 2 decimals

### "Explode" The Best Pie
We can highlight the winner with the `explode` parameter:

```python
explode = [0.1, 0, 0, 0, 0, 0]

plt.pie(votes, labels=flavors, autopct='%1.1f%%', explode=explode)
```

This means that we want to explode the first slice by `0.1` (10% of radius).

This will look like:
![](https://i.imgur.com/E3wu9LL.png)

# Object-Oriented Plotting
 we will be using **Object-Oriented (OO) Interface** plotting as we start to build more complex plots! OO provides us with more flexibility as we work with figure and axes objects directly.

As an example, this is what it looks like in code. This will plot the same visualization as the example above, but with an OO interface.

```python
fig, ax = plt.subplots()
ax.plot(x, y)
ax.set_title('Title')
plt.show()
```

As we know, a Figure is our canvas, and our Axes are our plots inside the figure. With OO, we can now have multiple, or **subplots**, inside one figure.

Note that our visualizations will look the same, but our code will be written with an OO interface to account for more complex plots. This way, we'll be able to control more than one plot at a time.

## Multiline Plots
Take a look at this DataFrame of sales and profit for 5 months. We can create a multiline plot to showcase both sales and profit on the same plot using the OO interface.

```python
df = pd.DataFrame({
  'Month': ['Jan', 'Feb', 'Mar', 'Apr', 'May'],
  'Sales': [100, 120, 90, 150, 130],
  'Profit': [20, 25, 18, 30, 28]
})
```

Instead of using `plt.plot()`, we can create a figure and axes object:
```python
fig, ax = plt.subplots()
```

With the Object-Oriented interface, we no longer rely on Matplotlib to guess which plot we're working with. Instead, we tell Matplotlib exactly where to draw by calling methods directly on the Axes object:

- `fig` represents the entire figure (the canvas that holds everything)
- `ax` represents a single plot area where data is drawn

Next, we can add on `ax.plot(x, y, label)` to plot data on specific axes. Since we're plotting two `y` variables (Sales and Profit) against one `x` variable (Month), we have the capability now to create two axes.

```python
ax.plot(df['Month'], df['Sales'], label='Sales')
ax.plot(df['Month'], df['Profit'], label='Profit')
```

We are also labeling "Sales" and "Profit" to create a **legend** on our visualization.

Now, all is left to add a title, and `x` and `y` labels as we've been doing already. We can do this by calling methods (`set_title()`, `set_xlabel()`, `set_ylabel()`) directly on the Axes object:

```python
ax.set_title('Company Metrics')
ax.set_xlabel('Month')
ax.set_ylabel('Amount (Thousands, $USD)')
```

We'll then use `ax.legend()` to add the legend which we have created labels for, and `plt.show()` to see our plot.

In the end, we'll have 8 lines of code:

```python
fig, ax = plt.subplots()

ax.plot(df['Month'], df['Sales'], label='Sales')
ax.plot(df['Month'], df['Profit'], label='Profit')
ax.set_title('Monthly Sales and Profit')
ax.set_xlabel('Month')
ax.set_ylabel('Amount')
ax.legend()

plt.show()
```

The finished plot will look something like this!

![](https://firebasestorage.googleapis.com/v0/b/codedex-io.appspot.com/o/curriculum%2Fimages%2Fmatplotlib-chapter-2%2Fmpl-2-03.png?alt=media&token=48b79121-08bc-4156-89e1-01d36fe9b3fd)

# Subplots
## Subplot Attributes
Beyond lineplots, OO plotting lets us quickly create multiple visualizations into one figure.

For example:
![](https://firebasestorage.googleapis.com/v0/b/codedex-io.appspot.com/o/curriculum%2Fimages%2Fmatplotlib-chapter-2%2Fmpl-2-04.png?alt=media&token=bdddbeb7-b93f-4f29-bde4-5ca2162d06d4)

Remember our sales and profit multiline plot? We can also create two different plots on the same figure. The two bar graphs above show both profit data and sales amount as two different visualizations together. Cool, right?

To do this, we need to learn a few subplot attributes. Here, we have a declaration for our graph data:

```python
fig, axes = plt.subplots(2, 1, figsize=(8, 8)) 
# 2 rows 
# 1 column 
# 8 x 8 inches
```

- Layout: `(2,1)` tells the figure to draw 2 rows and 1 column so we have a top plot and a bottom plot
- Figure size: `figsize=(8,8)` this is the overall size of the figure, measured in inches, to make a plot more readable

Now that we have an outline for our figure, we need to draw both plots. To draw the first plot, we need to index the top subplot. Since we declared 2 rows with 1 column, we have 2 subplots or **axes objects**.

Axes objects are stored similarly to a Python list:

```python
axes = [axes_for_row1, axes_for_row2]
```

Therefore:

- `axes[0]` is the first subplot in the 2x1 layout (top)
- `axes[1]` is the second subplot (bottom)

To draw a bar graph, we can use `axes.bar(x,y)`. To start with the top subplot, let's use `axes[0].bar()` and fill in our data information:

```python
axes[0].bar(df['Month'], df['Sales'], color='skyblue') 
axes[0].set_title('Monthly Sales') 
axes[0].set_ylabel('Sales Amount')
```

Note that we can also add a `color=` using basic color names (like `'skyblue'`), hex codes (like `'#87CEEB'`), or RGB Tuples (like `'135, 206, 235'`). We have also set a `title` and `y_label` for the top subplot.

```python
color='lightgreen'  # Color string
color='#87CEEB'  # HEX code
color=(1, 0.5, 0)     # RGB tuple
```

We'll do the same for the bottom subplot:

```python
axes[1].bar(df['Month'], df['Profit'], color='lightgreen') 
axes[1].set_title('Monthly Profit') 
axes[1].set_ylabel('Profit Amount')
```

Color strings are the most common way to add a color to a plot. Here's some of the colors you can choose from:

```output
'blue', 'green', 'red', 'cyan', 'magenta', 'yellow', 'black', 'white', 'gray', 'orange', 'purple', 'brown', 'pink', 'lime', 'teal', 'navy', 'olive', 'maroon'
```

Now, using `plt.show()` to conclude will show our plots! 🎉

## Sharing Axes

If you look back at the visualization, you'll notice the x axes on the top plot is unlabeled, and the x axes on the bottom plot is labeled "Month". If both plots share the x axis, you'll add `sharex=True`. This would be the same for a shared Y axis (`sharey=True`)

```py
fig, axes = plt.subplots(2, 1, figsize=(8, 8), sharex=True)
```

Then, before the `plt.show()` line, you can add the label

```py
plt.xlabel("Month")  # shared x-axis label
```

Your finished visualization should then look like this, with the x-axis labeled once for both graphs.

![](https://firebasestorage.googleapis.com/v0/b/codedex-io.appspot.com/o/curriculum%2Fimages%2Fmatplotlib-chapter-2%2Fmpl-2-05.png?alt=media&token=cb069ac7-8cd5-4395-8986-ac1b790bfe74)

Your finished code should look like this:

```python
fig, axes = plt.subplots(2, 1, figsize=(8, 8), sharex=True)
axes[0].bar(df['Month'], df['Sales'], color='skyblue')
axes[0].set_title('Monthly Sales')
axes[0].set_ylabel('Sales Amount')
axes[1].bar(df['Month'], df['Profit'], color='lightgreen')
axes[1].set_title('Monthly Profit')
axes[1].set_ylabel('Profit Amount')
plt.xlabel("Month")
plt.show()
```

## Marker Styles
Remember our multiline plot from a few exercises back?
![](https://firebasestorage.googleapis.com/v0/b/codedex-io.appspot.com/o/curriculum%2Fimages%2Fmatplotlib-chapter-2%2Fmpl-2-03.png?alt=media&token=48b79121-08bc-4156-89e1-01d36fe9b3fd)

While we get to see visually trends and change over time, it can be a bit hard to distinguish different values if they're super close together. The profit line in this example shows that.

To fix this, we can add **markers** to have our plot look like the one above.

![](https://firebasestorage.googleapis.com/v0/b/codedex-io.appspot.com/o/curriculum%2Fimages%2Fmatplotlib-chapter-2%2Fmpl-2-07.png?alt=media&token=1353549e-2dcc-48ac-8792-0dadd79a69cf)

Notice that we have a circle marker for the "Sales" line and a square marker for the "Profit" line. This makes the plot much more visually appealing, and useful to really distinguish points.

Here are some of the other markers available to use with Matplotlib.

|Marker|Name|Visual|
|---|---|---|
|`o`|Circle|●|
|`s`|Square|■|
|`^`|Triangle Up|▲|
|`v`|Triangle Down|▼|
|`D`|Diamond|◆|
|`x`|X|✕|
|`+`|Plus|+|
|`*`|Star|★|
|`P`|Filled Plus|✚|
|`H`|Hexagon|⬢|
|`_`|Horizontal Line|—|
|`|`|Vertical Line|

To add a marker to your plot, simply add a `marker='o'` line:

```python
ax.plot(df["Month"], df["Sales"], marker='o', label="Sales")
ax.plot(df["Month"], df["Profit"], marker='s', label="Profit")
```

## Iteration with Python

What if our line plot didn't have only 2 lines, but 5? Or 30? Notice that we would have to write `ax.plot()` for each line we would want to show on our figure.

Luckily, we can use a **Python `for` loop** to iterate through our data very easily and display any data we might need!

Let's say you have a CSV file of weather data for multiple cities for days of the week, including temperatures in celsius and rainfall in millimeters.

```text
Day,City,Temp_C,Rain_mm
Mon,New York,22,5
Tue,New York,24,0
Wed,New York,21,2
Thu,New York,23,1
Fri,New York,25,0
Mon,Los Angeles,26,0
Tue,Los Angeles,27,0
Wed,Los Angeles,26,0
Thu,Los Angeles,28,0
Fri,Los Angeles,29,0
Mon,Chicago,20,8
Tue,Chicago,22,6
```

There seems to only be 3 cities in the list, but there are duplicates. Once we have created a DataFrame of this data, we can use a single line of code to create a list of all the unique values in the `"City"` column.

```python
cities = df["City"].unique()
```

`cities` now has: `["New York", "Los Angeles", "Chicago"]` stored, and is ready for us to use!

We can create a **Python `for` loop** that iterates through this list and plots its data accordingly. Then, we can and style it as we would like:

```python
for city in cities:
  city_data = df[df["City"] == city]
  ax.plot(
    city_data["Day"],
    city_data["Temp_C"],
    marker='o',
    label=city
  )
```

- `df[df[“City”] == city]` is acquiring the lists of cities, and if `True`, is creating a different DataFrame of only true values of that city each iteration
- `axes.plot()` plots every line, grabbing the `Day` and `Temp_C` values and adds a marker to all the lines in the city

This would then result in your plot looking like this:

![](https://firebasestorage.googleapis.com/v0/b/codedex-io.appspot.com/o/curriculum%2Fimages%2Fmatplotlib-chapter-2%2Fmpl-2-08.png?alt=media&token=cdb1b47e-8942-426c-87fd-0058a2611352)

The code for the visualization above looks like this:

```python
df = pd.read_csv("city_weather_data.csv")
fig, ax = plt.subplots(figsize=(10, 6))

cities = df["City"].unique()

for city in cities:
  city_data = df[df["City"] == city]
  ax.plot(
    city_data["Day"],
    city_data["Temp_C"],
    marker='o',
    label=city
  )

ax.set_title("Daily Temperature Trends by City")
ax.set_xlabel("Day")
ax.set_ylabel("Temperature (°C)")
ax.legend()

plt.show()
```

# Histogram
``` python
# Create histogram of life_exp data
plt.hist(life_exp)

# Display histogram
plt.show()
```
![[Pasted image 20260225210946.png]]



``` python
# Build histogram with 5 bins
plt.hist(life_exp, 5)
  
# Show and clean up plot
plt.show()
plt.clf() 

# Build histogram with 20 bins
plt.hist(life_exp, 20)

# Show and clean up again
plt.show()
plt.clf()
```
![[Pasted image 20260225211155.png]]![[Pasted image 20260225211200.png]]

