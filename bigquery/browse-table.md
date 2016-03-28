# Browse table

Python's [tabview](https://github.com/firecat53/tabview) module provides an
excellent way of viewing csv files. It works really well with `bq head`
command. Execute:

```.bash
bq --format=csv head -n10 [TABLE_NAME] | tabview -
```

to quickly browse though first 10 rows of a table.
