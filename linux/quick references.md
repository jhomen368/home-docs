### Disk Usage by File System

```
sudo du -hsx /* | sort -rh | head -n 40
```

**Syntax:**
* `du`: display the amount of disk space used by each file and directory
	+ `-h`: human-readable format (e.g., MB, GB)
	+ `-s`: summary mode (display total for each directory)
	+ `-x`: skip directories that are not executable
* `sort`: sort the output in reverse order (descending)
	+ `-r`: reverse order
	+ `-h`: same as above (human-readable format)
* `head`: display the first n lines of the output
	+ `-n 40`: show only the first 40 lines