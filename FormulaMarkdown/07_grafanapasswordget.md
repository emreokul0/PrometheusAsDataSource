Get the Grafana admin password:

```bash
kubectl get secret --namespace monitoring grafana -o jsonpath="{.data.admin-password}" | base64 --decode ; echo
```

**Output**

@emreokul0 ➜ /workspaces/PrometheusAsDataSource (main) $ kubectl get secret --namespace monitoring grafana -o jsonpath="{.data.admin-password}" | base64 --decode ; echo
8v0bd6rWu9uKFqCKWkxJM2BeintsW6Xy8IsDmyFf

```
admin is the default username
password : 8v0bd6rWu9uKFqCKWkxJM2BeintsW6Xy8IsDmyFf
```