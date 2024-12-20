# Setting Up a Minikube Cluster with Helm, Prometheus, Grafana, and Thanos
## Prerequisites
- 🖥️ Minikube installed
- 🛠️ kubectl installed
- 🎛️ Helm installed
## Steps
### 1. 🚀 Start Minikube
```bash
minikube start
minikube status
```
### 2. 🔍 Verify Helm Installation
Helm should already be installed as per the prerequisites. Verify the installation:
```bash
helm version
```
### Helm Version Output
```bash
@emreokul0 ➜ /workspaces/PrometheusAsDataSource (main) $ helm version
version.BuildInfo{Version:"v3.16.1", GitCommit:"5a5449dc42be07001fd5771d56429132984ab3ab", GitTreeState:"clean", GoVersion:"go1.22.7"}
```
### 3. ➕ Add Helm Repositories
```bash
helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
helm repo add grafana https://grafana.github.io/helm-charts
helm repo update
echo "Helm repositories added successfully!"
```
Important always use a namespace never use default

```bash
kubectl create namespace monitoring
```

### 4. 📈 Install Prometheus
```bash
helm install prometheus prometheus-community/prometheus -n monitoring
```
### 5. 📊 Install Grafana
```bash
helm install grafana grafana/grafana -n monitoring
```
@emreokul0 ➜ /workspaces/PrometheusAsDataSource (main) $ kubectl get pods -A
NAMESPACE     NAME                                                READY   STATUS              RESTARTS        AGE
kube-system   coredns-6f6b679f8f-wwrn4                            1/1     Running             0               8m50s
kube-system   etcd-minikube                                       1/1     Running             0               8m55s
kube-system   kube-apiserver-minikube                             1/1     Running             0               8m55s
kube-system   kube-controller-manager-minikube                    1/1     Running             0               8m55s
kube-system   kube-proxy-scm6d                                    1/1     Running             0               8m51s
kube-system   kube-scheduler-minikube                             1/1     Running             0               8m55s
kube-system   storage-provisioner                                 1/1     Running             1 (8m19s ago)   8m53s
monitoring    grafana-57794cd967-tz92r                            0/1     ContainerCreating   0               20s
monitoring    prometheus-alertmanager-0                           1/1     Running             0               31s
monitoring    prometheus-kube-state-metrics-7b97cb57c6-rc4cr      1/1     Running             0               31s
monitoring    prometheus-prometheus-node-exporter-t2dxj           1/1     Running             0               31s
monitoring    prometheus-prometheus-pushgateway-9f8c968d6-k46f9   1/1     Running             0               31s
monitoring    prometheus-server-7d64c54f54-zrr7m                  1/2     Running             0               31s
# Port forward Grafana
# initial Port forward setup 
```bash
kubectl port-forward svc/grafana 3000:80 -n monitoring
```
- **Local Environment:** Access Grafana at `http://localhost:3000`.
- Development ports > accessed over load balancer
- Development ports > accessed over the bridge
- **CodeSpaces Environment:** Access Grafana at `https://secret-spooky-tomb-r67g9q6675pcpwgg-3000.app.github.dev/?orgId=1`.
- Cloud spaces environment > https://fictional-space-fiesta-675v46v6q35vpw-3000.app.github.dev/connections/datasources/edit/ce1ci1ipttkw0e
### 6. 🔄 Port Forward Prometheus
```bash
kubectl port-forward svc/prometheus-server 9090:80 -n monitoring
```
- **Local Environment:** Access Prometheus at `http://localhost:9090`.
- **CodeSpaces Environment:** Access Prometheus at `https://secret-spooky-tomb-r67g9q6675pcpwgg-9090.app.github.dev/graph?g0.expr=&g0.tab=1&g0.display_mode=lines&g0.show_exemplars=0&g0.range_input=1h`.
- Development ports > accessed over load balancer
- Development ports > accessed over the bridge
### 7. 🌐 Access Grafana
Get the Grafana admin password:
```bash
kubectl get secret --namespace monitoring grafana -o jsonpath="{.data.admin-password}" | base64 --decode ; echo
```
```
admin is the default username
password : 8v0bd6rWu9uKFqCKWkxJM2BeintsW6Xy8IsDmyFf
```
Access Grafana at `http://localhost:3000` and log in with `admin` and the retrieved password.
> Use the ports in the tabs in codespaces
### 8. 🌐 Access Prometheus
Forward the Prometheus port:
```bash
kubectl port-forward svc/prometheus-server 9090:80 -n monitoring
```
- **Local Environment:** Access Prometheus at `http://localhost:9090`.
- **CodeSpaces Environment:** Access Prometheus at `https://secret-spooky-tomb-r67g9q6675pcpwgg-9090.app.github.dev/graph?g0.expr=&g0.tab=1&g0.display_mode=lines&g0.show_exemplars=0&g0.range_input=1h`. Check ports with 9090.
### 9. ➕ Add Prometheus as a Data Source in Grafana
1. **Local:** Open Grafana in your browser at `http://localhost:3000`.
    **CodeSpaces:** Open Grafana at `https://secret-spooky-tomb-r67g9q6675pcpwgg-3000.app.github.dev/?orgId=1`.
2. Log in with `admin` and the retrieved password.
3. Go to **Connections** > **Data Sources**.
4. Click **Add data source**.
5. Select **Prometheus**.
6. Set the URL to `https://secret-spooky-tomb-r67g9q6675pcpwgg-9090.app.github.dev/`.
7. Click **Save & Test** to verify the connection.
### 10. ✅ Verify Installations
Check the status of the pods:
```bash
kubectl get pods
kubectl get -n monitoring
```
MISSING CONFIG
You should see pods for Prometheus, Grafana, and Thanos running.
### 🔄 Upgrade Instructions
If you encounter an error, upgrade Prometheus:
```bash
helm install prometheus prometheus-community/prometheus -f /workspaces/PrometheusAsDataSource/SymbolicCode/prometheus.yml
```
For upgrade:
```bash
helm upgrade prometheus prometheus-community/prometheus -f /workspaces/PrometheusAsDataSource/SymbolicCode/prometheus.yaml
```
For Grafana upgrade:
```bash
helm upgrade grafana grafana/grafana -f /workspaces/PrometheusAsDataSource/SymbolicCode/grafana.yaml
```
Release "grafana" has been upgraded. Happy Helming!