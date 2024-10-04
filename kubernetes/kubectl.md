```yaml
kubectl get nodes
```

1) First drain the node

```yaml
kubectl drain <node-name>
```

You might have to ignore daemonsets and local-data in the machine

```yaml
kubectl drain <node-name> --ignore-daemonsets --delete-local-data
```

2) Finally delete the node

```yaml
kubectl delete node <node-name>
```




Commands:

Scale Down Pods to 0

```
kubectl scale deploy -n sabnzbd --replicas=0 --all
```


rollout a change

```
 kubectl rollout restart deployment sabnzbd -n sabnzbd
```

1. A Kubernetes service is assigned a DNS A record for each IP address and an SRV record for each port on which the service is exposed. The DNS A record follows a specific naming convention: `<service-name>.<namespace-name>.svc.cluster.local`.

Force Terminate all Pods in terminating state

```
kubectl get pods --all-namespaces | awk '{if ($4=="Terminating") print "kubectl delete pod " $2 " -n " $1 " --force --grace-period=0 ";}' | sh
```

