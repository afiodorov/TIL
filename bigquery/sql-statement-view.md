# See SQL statement behind a view

bq utility provides a show command for examining a table. It only works for
genuine tables. However, the `--view` flag allows one to see the SQL statement
behind views.

Piping the output to vim allows for a nice display of an SQL statement:

```.bash
bq show --view [TABLE_NAME] | tail -n+5 | vim -c "set ft=sql" -
```

The `-c "set ft=sql"` command line argument enables sql syntax highlighting.
