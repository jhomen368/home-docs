
manual node startup:

set jumbo frames on secondary NIC:

```
sudo vi /etc/netplan/99-netcfg-vmware.yaml
```

```
sudo netplan apply
```

add packages if necessary to node (should be in cloud-init)

```
sudo apt-get update
sudo apt install open-iscsi cloud-utils cloud-initramfs-growroot nfs-common -y
```


https://kubernetes.io/docs/tasks/configure-pod-container/assign-pods-nodes/