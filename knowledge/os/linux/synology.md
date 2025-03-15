---
tags:
  - nas
  - maintenance
---

### Deleting Files Older Than a Year

```bash
find /path/to/directory -type f -mtime +365 -delete
```

- **Explanation**: This command deletes files (`-type f`) modified more than 365 days ago (`-mtime +365`).
- **Safety Tip**: Use `-print` instead of `-delete` for a dry run:

```bash
find /path/to/directory -type f -mtime +365 -print
```

### Deleting Empty Directories Older Than a Year

```bash
find /path/to/directory -type d -mtime +365 -empty -delete
```

- **Explanation**: Deletes empty directories (`-type d`, `-empty`) older than a year.
- **Note**: Non-empty directories are skipped. Consider deleting contents first.

### Combined Command with Safety

```bash
find /path/to/directory -depth -type f -mtime +365 -delete -o -type d -mtime +365 -empty -delete
```

- **Explanation**: Uses `-depth` to process files before directories, ensuring correct deletion order.
- **Safety Tip**: Replace `-delete` with `-print` for a dry run:

```bash
find /path/to/directory -depth -type f -mtime +365 -print -o -type d -mtime +365 -empty -print
```

### Additional Considerations

- **Permissions**: Ensure you have write permissions in the target directory.
- **Time Parameters**: Use `-atime` for access time or `-ctime` for change time if needed.
- **Testing**: Always test commands in a non-critical environment first.
