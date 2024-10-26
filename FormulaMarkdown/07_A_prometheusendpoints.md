Prometheus exposes a variety of endpoints that provide information about its own state, metrics it has collected, and configuration details. Here’s a list of commonly used Prometheus HTTP endpoints:

### 1. **/metrics**
   - **Description**: This endpoint exposes Prometheus’s own internal metrics. It’s useful for monitoring Prometheus itself (e.g., query times, memory usage).
   - **Usage**: Access via `http://<prometheus-server>:9090/metrics`

### 2. **/federate**
   - **Description**: This endpoint allows Prometheus to federate metrics from other Prometheus servers, aggregating data across multiple instances.
   - **Usage**: Access via `http://<prometheus-server>:9090/federate`

### 3. **/api/v1/query**
   - **Description**: Executes a single PromQL (Prometheus Query Language) query.
   - **Usage**: `http://<prometheus-server>:9090/api/v1/query?query=<promql_expression>`

### 4. **/api/v1/query_range**
   - **Description**: Executes a PromQL query over a specified time range. Ideal for extracting data for graphing or analysis.
   - **Usage**: `http://<prometheus-server>:9090/api/v1/query_range?query=<promql_expression>&start=<start_timestamp>&end=<end_timestamp>&step=<interval>`

### 5. **/api/v1/alerts**
   - **Description**: Returns a list of active alerts managed by Prometheus.
   - **Usage**: `http://<prometheus-server>:9090/api/v1/alerts`

### 6. **/api/v1/rules**
   - **Description**: Lists all active recording and alerting rules, along with their statuses.
   - **Usage**: `http://<prometheus-server>:9090/api/v1/rules`

### 7. **/api/v1/targets**
   - **Description**: Displays information on all configured targets, their states (up/down), and metadata.
   - **Usage**: `http://<prometheus-server>:9090/api/v1/targets`

### 8. **/api/v1/targets/metadata**
   - **Description**: Lists metadata for all active time series, including labels and metrics names.
   - **Usage**: `http://<prometheus-server>:9090/api/v1/targets/metadata`

### 9. **/api/v1/series**
   - **Description**: Returns time series data for matching label sets over a specified time range.
   - **Usage**: `http://<prometheus-server>:9090/api/v1/series?match[]=<label_matcher>&start=<start_timestamp>&end=<end_timestamp>`

### 10. **/api/v1/label/\<label_name>/values**
   - **Description**: Lists possible values for a specific label name across time series in the current dataset.
   - **Usage**: `http://<prometheus-server>:9090/api/v1/label/<label_name>/values`

### 11. **/api/v1/status/config**
   - **Description**: Displays the current Prometheus configuration, useful for debugging and verification.
   - **Usage**: `http://<prometheus-server>:9090/api/v1/status/config`

### 12. **/api/v1/status/flags**
   - **Description**: Shows Prometheus runtime flag values, including configuration flags.
   - **Usage**: `http://<prometheus-server>:9090/api/v1/status/flags`

### 13. **/api/v1/status/runtimeinfo**
   - **Description**: Provides runtime information on the Prometheus server, including storage usage, memory, and goroutine counts.
   - **Usage**: `http://<prometheus-server>:9090/api/v1/status/runtimeinfo`

### 14. **/api/v1/status/buildinfo**
   - **Description**: Shows build information for Prometheus, including version and build date.
   - **Usage**: `http://<prometheus-server>:9090/api/v1/status/buildinfo`

### 15. **/api/v1/metadata**
   - **Description**: Retrieves metric metadata (e.g., types, help descriptions) for all active time series.
   - **Usage**: `http://<prometheus-server>:9090/api/v1/metadata`

### 16. **/graph**
   - **Description**: Prometheus web UI for exploring time series data graphically.
   - **Usage**: Access via `http://<prometheus-server>:9090/graph`

### 17. **/alerts**
   - **Description**: Prometheus web UI page displaying active alerts.
   - **Usage**: Access via `http://<prometheus-server>:9090/alerts`

### 18. **/targets**
   - **Description**: Prometheus web UI page listing all targets and their statuses.
   - **Usage**: Access via `http://<prometheus-server>:9090/targets`

These endpoints allow access to a range of Prometheus data and administrative information. Make sure to replace `<prometheus-server>` with the actual hostname or IP address of your Prometheus server.