On Each Storage Node

```
sudo apt update
sudo apt install nfs-common open-iscsi
#start the service now and on reboot
sudo systemctl enable open-iscsi --now
```

https://longhorn.io/docs/1.6.2/deploy/install/install-with-helm/

```
helm install longhorn longhorn/longhorn --namespace longhorn-system --create-namespace --version 1.6.2
```


```
kubectl apply -f https://raw.githubusercontent.com/longhorn/longhorn/master/deploy/longhorn.yaml
```

```
kubectl apply -f https://raw.githubusercontent.com/longhorn/longhorn/v1.6.2/deploy/longhorn.yaml
```

longhorn RWX

https://longhorn.io/docs/1.5.3/advanced-resources/rwx-workloads/
https://longhorn.io/docs/1.5.3/deploy/install/#installing-nfsv4-client
https://kubernetes.io/docs/reference/kubernetes-api/config-and-storage-resources/persistent-volume-claim-v1/


```
kubectl apply -f https://raw.githubusercontent.com/longhorn/longhorn/v1.5.3/deploy/prerequisite/longhorn-nfs-installation.yaml
```

```fallback
kubectl get pod | grep longhorn-nfs-installation
```

- If you need to write to the volume, and you may have multiple Pods needing to write to the volume where you'd prefer the flexibility of those Pods being scheduled to different nodes, and `ReadWriteMany` is an option given the volume plugin for your K8s cluster, use `ReadWriteMany`.
- If you need to write to the volume but either you don't have the requirement that multiple pods should be able to write to it, or `ReadWriteMany` simply isn't an available option for you, use `ReadWriteOnce`.
- If you only need to read from the volume, and you may have multiple Pods needing to read from the volume where you'd prefer the flexibility of those Pods being scheduled to different nodes, and `ReadOnlyMany` is an option given the volume plugin for your K8s cluster, use `ReadOnlyMany`.
- If you only need to read from the volume but either you don't have the requirement that multiple pods should be able to read from it, or `ReadOnlyMany` simply isn't an available option for you, use `ReadWriteOnce`. In this case, you want the volume to be read-only but the limitations of your volume plugin have forced you to choose `ReadWriteOnce` (there's no `ReadOnlyOnce` option). As a good practice, consider the `containers.volumeMounts.readOnly` setting to `true` in your Pod specs for volume mounts corresponding to volumes that are intended to be read-only.

```
sudo apt-get update
sudo apt-get install cloud-utils cloud-initramfs-growroot -y
```


nfs://192.168.88.10:/volume1/backup/longhorn

random troubleshooting commands:

kubectl -n longhorn-system delete pod -l app=longhorn-manager

kubectl delete validatingwebhookconfigurations longhorn-webhook-validator

kubectl delete mutatingwebhookconfigurations longhorn-webhook-mutator

https://stackoverflow.com/questions/51585649/cancel-or-undo-deletion-of-persistent-volumes-in-kubernetes-cluster