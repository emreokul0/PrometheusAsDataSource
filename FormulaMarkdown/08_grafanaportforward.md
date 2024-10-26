@emreokul0 ➜ /workspaces/PrometheusAsDataSource (main) $ kubectl port-forward svc/grafana 3000:80 -n monitoring
Forwarding from 127.0.0.1:3000 -> 3000
Forwarding from [::1]:3000 -> 3000
Handling connection for 3000
Handling connection for 3000
Handling connection for 3000
Handling connection for 3000
Handling connection for 3000
Handling connection for 3000
Handling connection for 3000
Handling connection for 3000

source: 3000 >>>> load minikube port
destination: 80 >>>> load balancer entry

- **Local Environment:** Access Grafana at `http://localhost:3000`.
- Development ports > accessed over load balancer
- Development ports > accessed over the bridge
- **CodeSpaces Environment:** Access Grafana at `https://secret-spooky-tomb-r67g9q6675pcpwgg-3000.app.github.dev/?orgId=1`.
- Cloud spaces environment > https://fictional-space-fiesta-675v46v6q35vpw-3000.app.github.dev/connections/datasources/edit/ce1ci1ipttkw0e