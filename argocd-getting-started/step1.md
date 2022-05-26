Set up Helm repository to install Argo CD in Kubernetes.

First, install Helm by executing following command:

`curl https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3 | bash`{{execute}}

Then add Argo Helm repository by executing following command:

`helm repo add argo https://argoproj.github.io/argo-helm`{{execute}}

Then update repository information in the local environment by executing following command:

`helm repo update`{{execute}}

Install Argo CD by executing following command:

`helm install argocd argo/argo-cd`{{execute}}

Installing takes minutes.
Execute following command until the pod status shows up `Running`:

`kubectl get po -l app.kubernetes.io/name=argocd-server`{{execute}}

Argo CD creates initial admin account which name is `admin`.
Get its password by executing following command:

`kubectl -n default get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d; echo`{{execute}}

Though Argo CD accepts only HTTPS traffic, the environment cannot forward it.
Deploy Nginx as a reverse proxy to convert Argo CD's HTTPS traffic to HTTP by executing following commands:

`kubectl apply -f nginx-cm.yaml`{{execute}}

`kubectl apply -f nginx-deploy.yaml`{{execute}}

`kubectl apply -f nginx-svc.yaml`{{execute}}

Forward the environment's port to access Argo CD's Web UI via Nginx by executing following command:

`kubectl port-forward svc/nginx 80:80 --address 0.0.0.0 &> /dev/null &`{{execute}}

[Click here]({{TRAFFIC_HOST1_80}}) to access Argo CD dashboard and log in as `admin`.

![Argo CD Login Page](argocd_login.png)

You can see no applications in the dashboard.

![Argo CD Applications](argocd_applications.png)

Next, create your own Git repository to push your own deployment configuration.
