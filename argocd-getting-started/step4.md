Open your Git repository which is synced to Kubernetes and edit `podinfo-application.yaml`.
You can do in GitHub Web UI.

Podinfo is deployed using its Helm chart.
The Helm chart's configuration is written in `spec.source.helm.values`.

Edit `ui.color` and `ui.message` and push to Git.
Argo CD will detect the changes and syncing to Kubernetes.
You can click `Refresh` to detect changes manually.

Wait until syncing is completed.
Syncing status is seen in the Argo CD dashboard.

Forward the environment's port to access podinfo's Web UI by executing following command:

`kubectl port-forward svc/podinfo 9898:9898 --address 0.0.0.0 &> /dev/null`{{execute}}

Open `Podinfo` tab and confirm its Web UI is changed.

Excellent!
Now you can see the latest configuration and its history in your repository, and update via Git easily.
You can also use pull requests to deploy applications.
