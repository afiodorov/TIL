# Multiprocessing module is very limited

Turns out python's built-in function `Pool.map` from multiprocessing module
uses pickle to share functions across threads. However, plenty of functions
are not pickle-able, such as class methods and many others.

The following code doesn't work as a result:

```python
from multiprocessing import Pool, cpu_count
import pandas as pd

n_jobs = cpu_count()

# returns list of slices
def buckets(n, len):
    pass

axis = 1
with Pool(n_jobs) as p:
    ret_list = p.map(lambda b: df[b].apply(func, axis=axis),
                     buckets(n_jobs, len(df)))
    return pd.concat(ret_list, axis=1 - axis)
```

Fortunately there's a more sane `multiprocess` module as drop-in replacement
that uses `dill` instead of `pickle`. So calling `pip install multiprocess` and
replacing the import to `multiprocess` fixes the issue.
