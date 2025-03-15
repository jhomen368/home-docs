---
tags:
  - windows
---

## Running System Maintenance Commands

### Disabling Windows Boot Record (DBR) During System Restore

``` cmd
DISM.exe /Online /Cleanup-image /Restorehealth
```

- **Purpose**: This command is used to disable the Windows Boot Record (DBR) during a system restore operation. It helps in isolating issues related to the boot record by cleaning up unnecessary entries and restoring system health.

### Checking for System File Corruptions

``` cmd
sfc /scannow
```

- **Purpose**: This command scans your system for any file corruptions that might be preventing proper booting or operation. It helps identify potential issues before they cause significant problems.

### Checking Disk Space on All Drives

``` cmd
chkdsk
```

- **Purpose**: This command scans all drives to check disk space availability and free capacity. It ensures there is enough space for your operating system and applications, preventing future errors due to insufficient storage.

### Fixing the System Boot Record (DBR)

``` cmd
bootrec /fixmbrbootrec /fixboot
```

- **Purpose**: This command fixes issues with the system boot record by rebuilding it. It ensures that the boot sector contains valid entries for all drives, allowing the system to start properly.

## Rebuilding the Basic Configuration Directory (BCD)

``` cmd
bootrec /rebuildbcd
```

- **Purpose**: This command rebuilds the Basic Configuration Directory (BCD), which stores information about disk partitions and logical drives. It ensures that the system has accurate drive mappings for proper operation.