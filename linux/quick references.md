### Disk Usage (du) Command with Filtering and Sorting

```
sudo du -hsx /* | sort -rh | head -n 40
```

#### Syntax Breakdown

* `du`:
	+ `-h`: human-readable file sizes (e.g., 1K, 2M)
	+ `-s`: display total size instead of individual sizes
	+ `-x`: only consider directories and files in the current directory tree
	+ `/*`: specify the root directory (`/`) as the starting point for the analysis
* `sort`:
	+ `-r`: reverse the sort order (largest to smallest)
	+ `-h`: human-readable file sizes (e.g., 1K, 2M)
	+ `|`: pipe output to the next command
* `head`:
	+ `-n 40`: display only the first 40 lines of the output