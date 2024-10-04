
https://coder.com/docs/v2/latest/install/kubernetes
https://coder.com/docs/v2/latest/templates/docker-in-workspaces

```
kubectl create namespace coder
```

# Install PostgreSQL

```
helm repo add bitnami https://charts.bitnami.com/bitnami
helm install coder-db bitnami/postgresql \
    --namespace coder \
    --set auth.username=coder \
    --set auth.password=g7YycaghbUhHkBvS6jk5 \
    --set auth.database=coder \
    --set persistence.size=10Gi
```

Create Database URL

```
# Uses Bitnami PostgreSQL example. If you have another database,
# change to the proper URL.
kubectl create secret generic coder-db-url -n coder \
   --from-literal=url="postgres://coder:g7YycaghbUhHkBvS6jk5@coder-db-postgresql.coder.svc.cluster.local:5432/coder?sslmode=disable"
```

Install stable coder
```
helm install coder coder-v2/coder \
    --namespace coder \
    --values values.yaml \
    --version 2.9.2
```

upgrade

```
helm upgrade coder coder-v2/coder \
    --namespace coder \
    --values values.yaml \
    --version 2.9.2
```