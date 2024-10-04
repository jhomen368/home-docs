https://technotim.live/posts/kube-traefik-cert-manager-le/#cert-manager

https://doc.traefik.io/traefik/routing/providers/kubernetes-crd/
https://doc.traefik.io/traefik/routing/services/

helm repo add traefik https://helm.traefik.io/traefik

```
kubectl create namespace traefik
```

```
helm install --namespace=traefik traefik traefik/traefik --values=values.yaml
```

```
kubectl get svc --all-namespaces -o wide
```

```
kubectl apply -f default-headers.yaml
```

```
kubectl get certificate
```



kubectl apply -f default-headers.yaml