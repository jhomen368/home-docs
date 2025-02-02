### Displaying Disk Usage of Files and Directories

```
sudo du -hsx /* | sort -rh | head -n 40
```

* `du`: Estimate file size (human-readable, largest files first)
	+ `-h`: Human-readable sizes (e.g., MB, GB)
	+ `-s`: Summarize disk usage for each directory
	+ `-x`: Only consider directories and files with execute permission
* `sort`: Sort the output by size in reverse order (largest to smallest)
	+ `-r`: Reverse order (smallest to largest)
* `head`: Show the first 40 lines of output