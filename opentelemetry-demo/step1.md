Set up Helm repository to install OpenTelemetry Demo in Kubernetes.

First, install Helm by executing following command:

`curl https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3 | HELM_INSTALL_DIR=/usr/bin bash`{{execute}}

Then add Argo Helm repository by executing following command:

`helm repo add open-telemetry https://open-telemetry.github.io/opentelemetry-helm-charts`{{execute}}

Install OpenTelemetry Demo by executing following command:

`helm install otel-demo open-telemetry/opentelemetry-demo`{{execute}}

Installing takes minutes.
Execute the following command until the status of all pods shows up `Running`:

`kubectl get po -l app.kubernetes.io/instance=otel-demo`{{execute}}

Forward the environment's port to access the frontend of OpenTelemetry Demo by executing following command:

`kubectl port-forward svc/otel-demo-frontendproxy 8080:8080 --address 0.0.0.0 &> /dev/null &`{{execute}}

[Click here]({{TRAFFIC_HOST1_8080}}) to access the frontend or [click here]({{TRAFFIC_HOST1_8080}}/grafana) to access the Grafana.
