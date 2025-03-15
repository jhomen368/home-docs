
delete all files older then a year 

```bash
find /path/to/directory -type f -mtime +365 -delete
```

For directories older than a year, after ensuring they are empty:

``` bash
find /path/to/directory -type d -mtime +365 -empty -delete
```


if f you need to delete files and directories in a single command, you can use:

``` bash
find /path/to/directory -type f -mtime +365 -delete -o -type d -mtime +365 -empty -delete
```
