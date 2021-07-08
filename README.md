# Learning Pandas

## [Pandas Cheat Sheet](pandas_cheat_sheet.pdf)


## First Steps

Upload the data.
```python
nba = pd.read_csv("../data/nba_all_elo.csv")
type(nba)
```

Some first information.
```python
len(nba)
nba.shape
```

Head of the data.
```python
nba.head()
```

In order to show all the columns:
```python
pd.set_option("display.max.columns", None)
nba.head()
```

While it’s practical to see all the columns, you probably won’t need six decimal places! Change it to two:
```python
pd.set_option("display.precision", 2)
nba.head()
```

The tail.
```python
nba.tail()
```

## Displaying Data Types
The first step in getting to know your data is
to discover the different data types it contains.
```python
nba.info()
```
Output:
```
<class 'pandas.core.frame.DataFrame'>
RangeIndex: 126314 entries, 0 to 126313
Data columns (total 23 columns):
 #   Column         Non-Null Count   Dtype
---  ------         --------------   -----
 0   gameorder      126314 non-null  int64
 1   game_id        126314 non-null  object
 2   lg_id          126314 non-null  object
 3   _iscopy        126314 non-null  int64
 4   year_id        126314 non-null  int64
 5   date_game      126314 non-null  object
 6   seasongame     126314 non-null  int64
 7   is_playoffs    126314 non-null  int64
 8   team_id        126314 non-null  object
 9   fran_id        126314 non-null  object
 10  pts            126314 non-null  int64
 11  elo_i          126314 non-null  float64
 12  elo_n          126314 non-null  float64
 13  win_equiv      126314 non-null  float64
 14  opp_id         126314 non-null  object
 15  opp_fran       126314 non-null  object
 16  opp_pts        126314 non-null  int64
 17  opp_elo_i      126314 non-null  float64
 18  opp_elo_n      126314 non-null  float64
 19  game_location  126314 non-null  object
 20  game_result    126314 non-null  object
 21  forecast       126314 non-null  float64
 22  notes          5424 non-null    object
dtypes: float64(6), int64(7), object(10)
memory usage: 22.2+ MB
```

### Showing Basics Statistics
```python
nba.describe()

# with a specific time:
nba.describe(include=object)
```

### Exploring Your Dataset
For example, you can examine how often specific values occur in a column:
```python
#%%
nba["team_id"].value_counts()

nba["fran_id"].value_counts()
```

## Getting to Know Pandas’ Data Structures

While a DataFrame provides functions that can feel quite intuitive,
the underlying concepts are a bit trickier to understand.
For this reason, you’ll set aside the vast NBA DataFrame and
build some smaller Pandas objects from scratch.
```python
revenues = pd.Series([5555, 7000, 1980])
revenues
```

You’ve used the list [5555, 7000, 1980] to create a Series object called revenues. A Series object wraps two components:

- A sequence of values
- A sequence of identifiers, which is the index

You can access these components with `.values` and `.index`, respectively:
```python
revenues.values
#array([5555, 7000, 1980])
revenues.index
# RangeIndex(start=0, stop=3, step=1)
```

While Pandas builds on NumPy, a significant difference is in
their indexing. Just like a NumPy array,
a Pandas Series also has an integer index that’s implicitly defined.
This implicit index indicates the element’s position in the Series.

However, a Series can also have an arbitrary type of index.
You can think of this explicit index as labels for a specific row:

```python
city_revenues = pd.Series(
    [4200, 8000, 6500],
    index=["Amsterdam", "Toronto", "Tokyo"]
)
city_revenues
```

1. revenues: This Series behaves like a Python list because it only has a positional index.

1. city_revenues: This Series acts like a Python dictionary because it features both a positional and a label index.

```python
city_employee_count = pd.Series({"Amsterdam": 5, "Tokyo": 8})
city_employee_count
# Amsterdam    5
# Tokyo        8
# dtype: int64

city_employee_count.keys()
# Index(['Amsterdam', 'Tokyo'], dtype='object')

"Tokyo" in city_employee_count
# True

"New York" in city_employee_count
#False
```

```python
```

```python
```

```python
```

```python
```

```python
```

```python
```

```python
```

```python
```

```python
```

```python
```

```python
```

```python
```

```python
```

```python
```

```python
```

```python
```

```python
```

```python
```

```python
```

```python
```

```python
```

```python
```

```python
```

```python
```

```python
```

```python
```

```python
```

```python
```

```python
```

```python
```

```python
```

```python
```

```python
```



## [Some Pandas Examples](scripts/examples.ipynb)

___

## Credits:

- [Pandas Python Explore Dataset - Real Python](https://realpython.com/pandas-python-explore-dataset)
- [Pandas Python Visualization - Real Python](https://realpython.com/pandas-plot-python/)