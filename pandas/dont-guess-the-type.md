# Don't guess the type when calling read_csv

When calling `pd.read_csv` without `dtype` it really easy to run out of memory
with big dataset as pandas is trying to guess the types of various columns.
This process is really memory hungry. So always supply with `dtype` when
possible.
