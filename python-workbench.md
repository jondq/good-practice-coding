# PYTHON WORKBENCH

## PANDAS	

### lambda & apply
**Creating a column**

The general structure is:

+ You define a function that will take the column values you want to play with to come up with your logic.
+ You use an apply function with lambda along the row with axis=1. The general syntax is:

`df['new_col']= df.apply(lambda x: func(x['col1'],x['col2']),axis=1)`

**Filtering a dataframe**

```
#create a new column
df['num_words_title'] = df.apply(lambda x : len(x['Title'].split(" ")),axis=1)#simple filter on new column
new_df = df[df['num_words_title']>=4]
```
Or
```
new_df = df[df.apply(lambda x : len(x['Title'].split(" "))>=4,axis=1)]
```

**Change columns types**

```
df['Price'] = df.apply(lambda x: int(x['Price'].replace(',', '')),axis=1)
```