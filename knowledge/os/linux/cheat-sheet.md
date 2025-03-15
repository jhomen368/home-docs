---
tags:
  - linux
  - general-cli
---
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

### Entering Interactive Shell for Docker Container

To enter an interactive shell for a running Docker container, you can use the following command:

```
docker exec -it <container_name> /bin/bash
```

Replace `<container_name>` with the name of your container. This will open a new terminal session within the container, allowing you to interact with it as if you were logged in directly.

Alternatively, you can also use the `-n` option to specify the command to run inside the container:

```
docker exec -it -n <container_name> /bin/bash
```

### Checking File Size Human Readable Ubuntu CLI

To check the file size in a human-readable format using the Ubuntu command-line interface (CLI), you can use the `humanize` package and the `du` command.

Here are some examples:

* To display the file size in bytes, kilobytes, megabytes, or gigabytes:
```
du -h filename
```
This will show the file size in a human-readable format, such as "1.2M" for 1.2 megabytes or "4K" for 4 kilobytes.

* To display the total disk usage of a directory and its subdirectories:
```
du -sh /path/to/directory
```
This will show the total disk usage in a human-readable format, including the size of files and directories within the specified path.

Note: The `-h` option stands for "human-readable" and is used to display file sizes in a more readable format.
