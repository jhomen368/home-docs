
```
helm repo add rancher-latest https://releases.rancher.com/server-charts/latest
kubectl create namespace cattle-system
```


if cert manager not installed yet (should be)
```
kubectl apply -f https://github.com/cert-manager/cert-manager/releases/download/v1.13.2/cert-manager.crds.yaml
helm repo add jetstack https://charts.jetstack.io
helm repo update
helm install cert-manager jetstack/cert-manager \
--namespace cert-manager \
--create-namespace \
--version v1.14.3
```

```
helm install rancher rancher-stable/rancher \
  --namespace cattle-system \
  --set hostname=rancher.home.jhomen.org \
  --set bootstrapPassword=admin \
  --set ingress.tls.source=local-jhomen-org-tls
```

```
kubectl -n cattle-system rollout status deploy/rancher
```