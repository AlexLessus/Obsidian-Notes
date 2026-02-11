Tags: [[Aprendizaje Automático]]

**[Pandas](https://pandas.pydata.org/)** is one of the most powerful and popular Python libraries for working with data. If you've ever used Google Sheets or Excel to explore and analyze a table full of numbers, you're already halfway there – `pandas` just lets us do it faster, smarter, and with code.

With Pandas, we can:

- 🗂️ **Import spreadsheets**: Load file types like CSV files, Excel spreadsheets, JSON files, or SQL databases into Python so we can play around with them.
- 🔎 **Analyze data**: Quickly calculate averages, totals, or spot missing values in seconds.
- 🧽 **Clean and manipulate data**: Rename columns, remove duplicates, and edit data programmatically. Saving hours of _manual_ spreadsheet edits.
- 🥣 **Prep data for visualization or machine learning**: Get our data ready for libraries like `matplotlib` (data visualization) and `scikit-learn` (machine learning).
## DataFrame
A **DataFrame** is the heart of the Pandas library. Think of it like an Excel spreadsheet or SQL table we can control with Python code. It's a 2-dimensional data structure made up of _rows_ and _columns_. Each column has a name and a data type (like numbers, text, or even dates).

### Create from a Dictionary (Common)

This is the most popular way to build a DataFrame from scratch:

``` Python
import pandas as pd

data = {
  'city': ['Brooklyn', 'Seoul', 'Barcelona', 'Mexico City'],
  'country': ['US', 'South Korea', 'Spain', 'Mexico'],
  'population': [2646000, 9411000, 1636000, 9209944]
}

df = pd.DataFrame(data)
```

each _key_ in the `data` dictionary (`city`, `country`, `population`) becomes a column, and each _index_ in the lists will become a row.

Once the dictionary is created, we can pass the dictionary to `pd.DataFrame()` to create the DataFrame. Here, we stored it in a variable named `df`, short for DataFrame.

We can display the DataFrame with its name:
``` Python
df
```


### Create from a List of Lists
Sometimes it’s easier to think in rows. We can do that like this with a 2D list:

``` Python 
data = [
  ['Brooklyn', 'US', 2646000],
  ['Seoul', 'South Korea', 9411000],
  ['Barcelona', 'Spain', 1636000],
  ['Mexico City', 'Mexico', 9209944]
]

df = pd.DataFrame(data, columns=['city', 'country', 'population'])
```

Here, each inner list is a row. Don’t forget to name our columns with the `columns` parameter!


###  Import from a CSV File
Let's say we have a **.csv** (Comma-Separated Values) file sitting on our computer that we want to bring into Python. We can load it into Pandas in one line with `.read_csv()`:
``` Python
df = pd.read_csv('my_filename.csv')
```

Replace `my_filename.csv` with the name of your file. If it’s in the same folder as the code, we gucci.

## Data Exploration
Pandas is great for working with datasets containing thousands of rows. But when you're staring at a massive table, it can be hard to know where to begin.

Here are four `pandas` methods that can help with some basic data exploration:
- `.head()` & `.tail()`
- `.info()`
- `.describe()`


### View Rows with .head() and .tail()
If your dataset is huge, printing the whole thing would flood your screen with way too much info. This is where `.head()` and `.tail()` come in. These methods display the first 5 and last 5 rows (by default) of the DataFrame, respectively.

Assume we have a DataFrame named `df`:
``` Python
df.head()     # Displays the first 5 rows
df.tail()     # Displays the last 5 rows
```

If you want more than 5 rows, you can pass in a specific number. For example, this will display the first `10` rows:
``` Python
df.head(10)   # Displays the first 10 rows
```

### Data Types and Missing Values with .info()
The `.info()` method will show you information about each column in the DataFrame.

If you call `movies.info()`, you'll get the following output:
``` Python
<class 'pandas.core.frame.DataFrame'>
RangeIndex: 5 entries, 0 to 4
Data columns (total 8 columns):
 #   Column           Non-Null Count  Dtype
---  ------           --------------  -----
 0   title            5 non-null      object
 1   release_date     5 non-null      object
 2   genre            5 non-null      object
 3   studio           5 non-null      object
 4   budget           4 non-null      float64
 5   box_office       4 non-null      float64
 6   runtime_minutes  5 non-null      int64
 7   rating           5 non-null      float64
dtypes: float64(3), int64(1), object(4)
memory usage: 312.0+ bytes
```

There are a few notable pieces of information in this output:
- `5 entries` means that there are 5 rows in the dataset.
- The `budget` and `box_office` columns are each missing 1 value (only 4 non-null).
- The `Dtype` data describes the data type of each column.
    - Decimal numbers are stored as `float64` and whole numbers are stored as `int64`.
    - Columns that store strings are represented by `object`. If the columns store other complex data types, like dictionaries, dates, or user-defined objects, they would also appear as `object`.

**In short, `.info()` can be used to gain a quick understanding of the data types stored in your DataFrame as well as how much data is missing.**

### Summary Statistics with .describe()
Let's say you wanted to find the average budget of movies in your DataFrame. You can use `.describe()` to get a printout of summary statistics (mean, min, max, standard deviation, etc.) for every numeric column:
``` Python
movies.describe()
```
![[Pasted image 20260210091229.png]]
This shows that the average budget of our movies is `7.3250000e+07`, or 73,250,000.

`.describe()` only calculates summary statistics for numeric columns since many of these stats wouldn't make sense for Strings.

However, adding `include='all'` inside allows us to view stats about non-numeric columns:
![[Pasted image 20260210091304.png]]