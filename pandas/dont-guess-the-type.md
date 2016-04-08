# Don't guess the type when calling read_csv

When calling `pd.read_csv` without `dtype` it really easy to run out of memory
with big dataset as pandas is trying to guess the type, which is really memory
hungry. So always supply `dtype` when possible.
