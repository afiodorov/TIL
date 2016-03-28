# List jobs

Turns out listing current jobs is quite easy:

```.bash
bq ls -j -n10
```

`-n10` shows only last 10 jobs. If you want to see why a particular job failed
type

```.bash
bq show -j [[JOB_ID]]
```

TODO: Customise [fzf](https://github.com/junegunn/fzf) completions to make the
process more interactive, akin to `kill -9<TAB>`, i.e. `bq show -j<TAB>`.
