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

Head of the data. The tail.
```python
nba.head()
nba.tail()
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

## Displaying Data Types
The first step in getting to know your data is
to discover the different data types it contains.
```python
nba.info()
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
nba["team_id"].value_counts()
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
```

## Understanding DataFrame Objects
While a Series is a pretty powerful data structure, it has its limitations.
For example, you can only store one attribute per key.
As you’ve seen with the nba dataset, which features 23 columns,
the Pandas Python library has more to offer with its **DataFrame**.
This data structure is a sequence of Series objects that share the same index.

If you’ve followed along with the Series examples, then you should already have two Series objects with cities as keys:

1. city_revenues
1. city_employee_count

You can combine these objects into a DataFrame by providing a dictionary in the constructor.
The dictionary keys will become the column names, and the values should contain the Series objects:
```python
city_data = pd.DataFrame({
    "revenue": city_revenues,
    "employee_count": city_employee_count
})
city_data
           revenue  employee_count
Amsterdam     4200             5.0
Tokyo         6500             8.0
Toronto       8000             NaN
```

You can also refer to the 2 dimensions of a DataFrame as axes:
```python

city_data.axes
[Index(['Amsterdam', 'Tokyo', 'Toronto'], dtype='object'),
 Index(['revenue', 'employee_count'], dtype='object')]
city_data.axes[0]
 Index(['Amsterdam', 'Tokyo', 'Toronto'], dtype='object')
city_data.axes[1]
Index(['revenue', 'employee_count'], dtype='object')
```

A DataFrame is also a dictionary-like data structure, so it also supports .keys() and the in keyword.
However, for a DataFrame these don’t relate to the index, but to the columns:
```python
>>> city_data.keys()
Index(['revenue', 'employee_count'], dtype='object')
>>> "Amsterdam" in city_data
False
>>> "revenue" in city_data
True
```

## Accessing Series Elements

Recall that a Series has two indices:

1. A positional or implicit index, which is always a RangeIndex
1. A label or explicit index, which can contain any hashable objects

You can conveniently access the values in a Series with both the label and positional indices:
```python
>>> city_revenues["Toronto"]
8000
>>> city_revenues[1]
8000
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