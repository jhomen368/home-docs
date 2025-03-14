
## recovery

https://windowsreport.com/how-to-repair-windows-server-when-it-doesnt-boot-up/

integrity

``` cmd
DISM.exe /Online /Cleanup-image /Restorehealth
```

```cmd
sfc /scannow
```

```cmd
chkdsk
```

system boot record

```cmd
bootrec /fixmbrbootrec /fixboot
```

```cmd
bootrec /rebuildbcd
```