@emreokul0 ➜ /workspaces/PrometheusAsDataSource (main) $ kubectl get svc -A
NAMESPACE     NAME                                  TYPE        CLUSTER-IP       EXTERNAL-IP   PORT(S)                  AGE
default       kubernetes                            ClusterIP   10.96.0.1        <none>        443/TCP                  142m
kube-system   kube-dns                              ClusterIP   10.96.0.10       <none>        53/UDP,53/TCP,9153/TCP   142m
monitoring    grafana                               ClusterIP   10.100.182.82    <none>        80/TCP                   133m
monitoring    prometheus-alertmanager               ClusterIP   10.105.218.53    <none>        9093/TCP                 134m
monitoring    prometheus-alertmanager-headless      ClusterIP   None             <none>        9093/TCP                 134m
monitoring    prometheus-kube-state-metrics         ClusterIP   10.110.19.5      <none>        8080/TCP                 134m
monitoring    prometheus-prometheus-node-exporter   ClusterIP   10.111.165.244   <none>        9100/TCP                 134m
monitoring    prometheus-prometheus-pushgateway     ClusterIP   10.108.159.118   <none>        9091/TCP                 134m
monitoring    prometheus-server                     ClusterIP   10.106.199.240   <none>        80/TCP                   134m