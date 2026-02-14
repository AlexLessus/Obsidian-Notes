Tags: [[Pandas]] [[Python]]
## Importing CSV Files
**CSV** (**C**omma-**S**eparated **V**alues) files are everywhere. They’re simple, lightweight, and probably the first data format you’ll encounter in the wild as a beginner.

For example, we found a **[pokemon.csv](https://raw.githubusercontent.com/codedex-io/datasets/refs/heads/main/pokemon/pokemon.csv)** file containing information about Pokémon on [Kaggle](https://www.kaggle.com/datasets/rounakbanik/pokemon), an amazing resource for the Data Science community.

The beginning of the CSV file looks something like this:

``` csv
pokedex_number,name,type1,type2,attack,defense,speed
1,Bulbasaur,grass,poison,49,49,45
2,Ivysaur,grass,poison,62,63,60
3,Venusaur,grass,poison,82,83,80
4,Charmander,fire,,52,43,65
5,Charmeleon,fire,,64,58,80
6,Charizard,fire,flying,84,78,100
```

Each line represents a row. Notice that the first row contains the column names. This is the header.

The following rows contain data separated by commas, hence the name "CSV". This data is essentially:

|pokedex_number|name|type1|type2|attack|defense|speed|
|---|---|---|---|---|---|---|
|1|Bulbasaur|grass|poison|49|49|45|
|2|Ivysaur|grass|poison|62|63|60|
|3|Venusaur|grass|poison|82|83|80|
|4|Charmander|fire|-|52|43|65|
|5|Charmeleon|fire|-|64|58|80|
|6|Charizard|fire|flying|84|78|100|
If we wanted to import this dataset into a Pandas DataFrame, it's very easy.
Create a new Python program and add:

``` Python
import pandas as pd

df = pd.read_csv('pokemon.csv')
```

This code assumes **pokemon.csv** file is in the same directory as our Python script.

If it is in a different directory, we can always use the full path instead of the filename inside the single quotes, which might look something like this:

- **Windows:** `C:\Users\alex\Documents\projects\pokemon\pokemon.csv`
- **macOS:** `/Users/alex/Documents/projects/pokemon/pokemon.csv`

Here's a secret: You don't even need to download the file first!

Pandas can read directly from a URL:

``` python
url = 'https://raw.githubusercontent.com/codedex-io/datasets/refs/heads/main/pokemon/pokemon.csv'

df = pd.read_csv(url)
```

To make sure it worked, we can see what the DataFrame output looks like by running `print(df)`.

The output should look like:

```
no           name    type1   type2  attack  defense   speed 
0      1      Bulbasaur    grass  poison      49       49      45 
1      2        Ivysaur    grass  poison      62       63      60  
2      3       Venusaur    grass  poison      82       83      80 
3      4     Charmander     fire     NaN      52       43      65 
..   ...            ...      ...     ...     ...      ...     ...
```

### Other Separators

Not all CSV-style files use commas. **TSV** (**T**ab-**S**eparated **V**alues) files are fairly common, but in theory, the data could use any symbol as its separator.

To load data from these file types, we'll still use the `.read_csv()` method, but with the `sep` parameter:

```
df = pd.read_csv('pokemon.tsv', sep='\t')
```

In this case `'\t'` represents tab. We have to use this **escape character**, because Python wouldn't know how to interpret a literal tab.

But if the data was separated by something like a semicolon, then we would use `sep=';'`.

### Funky Headers
Occasionally, you will find a file that has done something odd with its header.

In business documents, it's fairly common for a file to begin with some metadata like `Report Generated on 1/24/2026`. If we were to import this into Pandas by default, we would get very confusing results. It would think that the first row were the column names!

To fix this, we'll want to ignore that row using the `header` parameter:

```
df = pd.read_csv('data.csv', header=1)
```

In this case, we're telling Pandas to consider row 1 the header, rather than row 0.

Another issue that you might run across is a file with no header at all. When this happens, if we don't include any parameters, Pandas will assume that the first row of actual data are our column names. For our Pokémon dataset, we'd suddenly have a column named `Bulbasaur`!

To fix this, we can use `header=None`. Then, after the import, we can give `df.columns` a list to manually set the column names:

``` python
df = pd.read_csv('pokemon.csv', header=None)

df.columns = ['pokedex_number', 'name', 'type1', 'type2', 'attack', 'defense', 'speed']
```

## Importing Excel Files
Sometimes, you'll be working with **Microsoft Excel** files, especially in a business setting.

Excel files can be a bit more complicated than CSV files because there can be multiple sheets within a single Excel file. For example, your company may have a document called **sales.xlsx** that has a different sheet for each quarter's sales.

Luckily, we can import these files into Pandas using `pd.read_excel()`:

``` Python
df = pd.read_excel('sales.xlsx')
```

By default, this will import the first sheet in the Excel file. But if you want to import a different sheet, we can use the `sheet_name` parameter:

``` python
df = pd.read_excel('sales.xlsx', sheet_name='Q1 2026')
```

If you want to import all sheets at once, we can use `sheet_name=None`. This will return a dictionary of DataFrames; the key will be the name of the sheet and the value is the DataFrame associated with that name.

``` python
df = pd.read_excel("sales.xlsx", sheet_name=None)
```

All of the strategies we used to deal with unusual headers can be applied to Excel files as well!

Finally, if you're working with Google Sheets or **.numbers** files from Numbers (the macOS spreadsheet software), there are unfortunately no native ways to import those into Pandas.

That being said, you should be able to export your Google Sheet or Numbers file as a **.csv** or **.xlsx** file, and then use that new file with Pandas!

## Importing JSON Files
**[JSON](https://en.wikipedia.org/wiki/JSON)** is the language of the web. When you pull data from TikTok, Reddit, or Spotify, you get JSON back.

Here's an example of what a JSON file might look like when getting data from the TikTok API:

``` JSON
{
  "data": {
    "videos": [
      {
        "id": "7080213458555737986",
        "title": "3 Projects You Can Code in a Day",
        "video_description": "Happy coding & gaming!",
        "duration": 2,
        "create_time": 1633823999,
      },
      {
        "id": "7080213458555737987",
        "title": "3 New Reads on Codedex",
        "video_description": "From new website features to project tutorials",
        "duration": 5,
        "create_time": 1633830000,
      }
    ],
    "has_more": true,
  },
  "error": {
    "code": "0",
    "message": "ok"
  }
}
```

There are a few ways to get this into Pandas, and the best strategy depends on what the JSON response looks like.

One option is to use `pd.read_json()`:

``` python
df = pd.read_json('tiktok.json')
```

If we use this method, a DataFrame will be created where each column is named after the keys at the top level of the JSON file. So in the case of the TikTok example, we'd have a column named `data` and a column named `error`.

For this particular example, that is probably not what we were going for. We want a DataFrame where each row is a video, and each column is a piece of information about that video like `view_count`.

To get this result, it will be easier to load the JSON from the `json` library, and then do some processing before moving it into a DataFrame:

```python
import pandas as pd
import json

# Load JSON file
with open('tiktok.json', 'r') as f:
  raw_json = json.load(f)

# Convert the list of videos to a DataFrame
df = pd.DataFrame(raw_json['data']['videos'])

print(df)
```

In this example, we load the JSON file into a variable named `raw_json` and then access only the values stored in `['data']['videos']`. By putting that data into Pandas, we get a DataFrame where every row contains information about a video.