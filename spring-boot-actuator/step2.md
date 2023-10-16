Set up Helm repository to install Prometheus in Kubernetes.

First, install Helm by executing following command:

`curl https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3 | HELM_INSTALL_DIR=/usr/bin bash`{{execute}}

Add Prometheus community Helm repository by executing following command:

`helm repo add prometheus-community https://prometheus-community.github.io/helm-charts`{{execute}}

Install Prometheus by executing following command:

`helm install prometheus prometheus-community/prometheus --set prometheus-node-exporter.enabled=false --set prometheus-pushgateway.enabled=false --set alertmanager.enabled=false --set kube-state-metrics.enabled=false --set server.persistentVolume.enabled=false`{{execute}}

Execute following command until the pod status shows up `Running`:

`kubectl get po -l app.kubernetes.io/name=prometheus`{{execute}}

Forward the environment's port to access Prometheus's Web UI by executing following command:

`kubectl port-forward svc/prometheus-server 9090:80 --address 0.0.0.0 &> /dev/null &`{{execute}}

[Click here]({{TRAFFIC_HOST1_9090}}) to access Prometheus's Web UI.
