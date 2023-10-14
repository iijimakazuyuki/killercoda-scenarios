Set up Helm repository to install Grafana in Kubernetes.

Add Grafana Helm repository by executing following command:

`helm repo add grafana https://grafana.github.io/helm-charts`{{execute}}

Install Grafana by executing following command:

`helm install grafana grafana/grafana`{{execute}}

Execute following command until the pod status shows up `Running`:

`kubectl get po -l app.kubernetes.io/name=grafana`{{execute}}

Forward the environment's port to access Grafana's Web UI by executing following command:

`kubectl port-forward svc/grafana 3000:80 --address 0.0.0.0 &> /dev/null &`{{execute}}

[Click here]({{TRAFFIC_HOST1_3000}}) to access Grafana's Web UI and log in as `admin`.
