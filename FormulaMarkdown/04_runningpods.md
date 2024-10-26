@emreokul0 ➜ /workspaces/PrometheusAsDataSource (main) $ kubectl get pods -A
NAMESPACE     NAME                                                READY   STATUS    RESTARTS      AGE
kube-system   coredns-6f6b679f8f-wwrn4                            1/1     Running   0             17m
kube-system   etcd-minikube                                       1/1     Running   0             17m
kube-system   kube-apiserver-minikube                             1/1     Running   0             17m
kube-system   kube-controller-manager-minikube                    1/1     Running   0             17m
kube-system   kube-proxy-scm6d                                    1/1     Running   0             17m
kube-system   kube-scheduler-minikube                             1/1     Running   0             17m
kube-system   storage-provisioner                                 1/1     Running   1 (16m ago)   17m
monitoring    grafana-57794cd967-tz92r                            1/1     Running   0             8m35s
monitoring    prometheus-alertmanager-0                           1/1     Running   0             8m46s
monitoring    prometheus-kube-state-metrics-7b97cb57c6-rc4cr      1/1     Running   0             8m46s
monitoring    prometheus-prometheus-node-exporter-t2dxj           1/1     Running   0             8m46s
monitoring    prometheus-prometheus-pushgateway-9f8c968d6-k46f9   1/1     Running   0             8m46s
monitoring    prometheus-server-7d64c54f54-zrr7m                  2/2     Running   0             8m46s