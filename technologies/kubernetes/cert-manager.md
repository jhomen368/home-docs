https://technotim.live/posts/kube-traefik-cert-manager-le/#cert-manager

```
helm repo add jetstack https://charts.jetstack.io
```

```
kubectl create namespace cert-manager
```

```
kubectl apply -f https://github.com/cert-manager/cert-manager/releases/download/v1.12.8/cert-manager.crds.yaml
```

```
helm install cert-manager jetstack/cert-manager --namespace cert-manager --values=values.yaml --version v1.12.8
```

issuers folder:

```
kubectl apply -f secret-cf-token.yaml
```

```
kubectl apply -f letsencrypt-production.yaml
```

From `certificates/prdouction` folder

```
kubectl apply -f jhomen-org.yaml
```

```
kubectl apply -f local-jhomen-org.yaml
```

```
kubectl get challenges
```

kubectl describe order local-jhomen-org-lkg6v-2793190267-1191576107