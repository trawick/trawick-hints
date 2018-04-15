# Pandas

## Series

```python
import pandas as pd

# will have indexes 0-3
s = pd.Series([1, 3, 5, 7])
# will return "array([1, 3, 5, 7])"
print(s.values)
print(s.index)

s = pd.Series([1, 3, 5, 7], index=['a', 'b', 'c', 'd'])
print(s.index)
print(s['a'] == s[0])  # True
s['b'] = 3
print(s[['a', 'c']])
# check if value in index of s
print('c' in s)

# create series from dict; keys will become the index
s = pd.Series({'Raleigh': 10, 'Durham': 8, 'Carrboro': 1})

cities = ['Raleigh', 'Carrboro', 'Chapel Hill', 'Durham']

# cities index value 'Chapel Hill' not in s, so value will be NaN
s2 = pd.Series(s, index=cities)

# returns boolean array, with True for 'Chapel Hill' and False for others
print(pd.isnull(s2))

# other series methods:
print(s2.isnull())
```

## Dataframes

```python
import numpy as np
import pandas as pd

df = pd.DataFrame({
    'city': ['Raleigh', 'Chapel Hill', 'Durham'],
    'pop': [0.6, 0.09, 2.9]
})

# arrange columns in different order
df = pd.DataFrame({
    # same as above
}, columns=['pop', 'city'])

# no 'founded' column in dictionary, so NaN for all rows
df = pd.DataFrame({
    # same as above
}, columns=['pop', 'city', 'founded'])

# replace column names
df.columns = ['population', 'city', 'founded']

# access a column as a series
df.city
df['city']

# set all rows in column to same value
df['founded'] = 1820

# set rows in column to values 0.0 - n-1
df['founded'] = np.arange(3.0)

```

## Loading external data into dataframes

```python
import pandas as pd

df = pd.read_csv('./foo.csv')
# huge number of options, for traditional CSV flavors,
# how to interpret dates or other data, etc.
df = pd.read_csv('./foo.csv', sep=',', nrows=5)

df = pd.read_excel('./foo.xlsx', sheet_name='Foo')

```
