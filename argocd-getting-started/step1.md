Set up Helm repository to install Argo CD in Kubernetes by executing following command:

`helm repo add argo https://argoproj.github.io/argo-helm`{{execute}}

Install Argo CD by executing following command:

`helm install argocd argo/argo-cd -f <(echo {"configs": {"params": {"server.insecure": true}}})`{{execute}}

This config is overwritten so that Argo CD can accept HTTP traffic, which the environment can forward.
Installing takes minutes.
Execute following command until the pod status shows up `Running`:

`kubectl get po -l app.kubernetes.io/name=argocd-server`{{execute}}

Argo CD creates initial admin account which name is `admin`.
Get its password by executing following command:

`kubectl -n default get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d; echo`{{execute}}

Forward the environment's port to access Argo CD's Web UI by executing following command:

`kubectl port-forward svc/argocd-server 80:80 --address 0.0.0.0 &> /dev/null &`{{execute}}

[Click here]({{TRAFFIC_HOST1_80}}) to access Argo CD dashboard and log in as `admin`.

![Argo CD Login Page](./argocd_login.png)

You can see no applications in the dashboard.

![Argo CD Applications](./argocd_applications.png)

Next, create your own Git repository to push your own deployment configuration.
