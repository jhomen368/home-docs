https://kubernetes.io/docs/concepts/workloads/controllers/deployment/
https://kubernetes.io/docs/reference/kubernetes-api/workload-resources/pod-v1/
https://kubernetes.io/docs/concepts/services-networking/service/#defining-a-service
https://kubernetes.io/docs/tutorials/services/connect-applications-service/
https://kubernetes.io/docs/concepts/storage/persistent-volumes/
https://kubernetes.io/docs/reference/kubernetes-api/config-and-storage-resources/persistent-volume-claim-v1/


```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: my-nginx
  # namespace: my-nginx
  labels:
    app: nginx
spec:
  replicas: 3
  selector:
    matchLabels:
      app: nginx
  template:
    metadata:
      labels:
        app: nginx
    spec:
      containers:
      - name: nginx
        image: nginx:1.14.2
        ports:
        - containerPort: 80
```


Secrets

https://kubernetes.io/docs/tasks/configmap-secret/managing-secret-using-config-file/
https://kubernetes.io/docs/tasks/inject-data-application/distribute-credentials-secure/#define-container-environment-variables-using-secret-data
