Argo CD's declarative configuration is described as `Application` resources.

Open the configuration file following:

`manifest-application.yaml`{{open}}

It contains the line including Git repository URL as following:

```
    repoURL: https://github.com/<your name>/<your repository's name>.git
```

Replace `<your name>` of your GitHub account and replace `<your repository's name>` of your own repository's name.

Then apply the file to Kubernetes by executing following command:

`kubectl apply -f manifest-application.yaml`{{execute}}

You can see `manifest` and `podinfo` applications in the Argo CD dashboard.
Podinfo is an open source Web application. cf. `https://github.com/stefanprodan/podinfo`

Wait until `podinfo` is `Synced` and `Healthy` in the dashboard, which means podinfo is deployed successfully.

Forward the environment's port to access podinfo's Web UI by executing following command:

`kubectl port-forward svc/podinfo 9898:9898 --address 0.0.0.0 &> /dev/null`{{execute}}

Open `Podinfo` tab and you will see its Web UI.

Stop port-forwarding by <kbd>Ctrl</kbd>+<kbd>C</kbd> or execute following command:

`^C`{{execute ctrl-seq}}

Congratulations!
You deployed the podinfo to Kubernetes using Argo CD.
Now configuration is in your Git repository and Kubernetes is synced the repository.
Next, push changes to your repository to deploy a new version.
