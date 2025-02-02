## File System Usage Summary

```
sudo du -hsx /* | sort -rh | head -n 40
```
### Syntax Breakdown
#### `du` Options:
* `-h`: Human-readable file sizes (e.g., 1K, 2M)
* `-s`: Summarize the file system usage
* `-x`: Include only files and directories, excluding special files
#### `sort` Options:
* `-r`: Reverse the sort order (largest to smallest)
* `-h`: Human-readable output for numbers
#### `head` Option:
* `-n 40`: Show only the first 40 lines of output