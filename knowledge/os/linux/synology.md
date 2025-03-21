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

- **Permissions**: Ensure you have write permissions in the target directory.
- **Time Parameters**: Use `-atime` for access time or `-ctime` for change time if needed.
- **Testing**: Always test commands in a non-critical environment first.
