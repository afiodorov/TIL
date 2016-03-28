# Memory-efficient selection of CSV columns

Sometimes a data scientists needs to select a few columns from a massive file.
Reading in entire data set into memory, however, is not always feasible. If
only there was `awk`-like or `cut`-like utility for a csv? There's one!

Haskell's [lazy-csv](https://hackage.haskell.org/package/lazy-csv) module does
just that. After running `cabal install lazy-csv` a `csvSelect` binary appeared
in my `~/.cabal/bin` which can efficiently filter through csv files:

```
Usage: csvSelect [OPTION...] (num|fieldname)...
    select numbered/named columns from a CSV file
  -v, -V   --version      show version number
  -o FILE  --output=FILE  output FILE
  -i FILE  --input=FILE   input FILE
  -u       --unchecked    ignore CSV format errors
  -d @     --delimiter=@  delimiter char is @
```

csvSelect can also be used without `-i` and `-o` flags in a unix fashion:

```.bash
cat data.csv | csvSelect id
```

I also discovered that Panda's `read_csv` function also supports `usecols=`
flag for speeding-up data loading. The flag renders `csvSelect` to be not as
useful as I originally thought it would be.
