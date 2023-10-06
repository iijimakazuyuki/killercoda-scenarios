Tanka and Jsonnet Bundler are required to install Grafana TNS.
Install Tanka and Jsonnet Bundler by executing following commands:

`sudo curl -Lo /usr/local/bin/tk https://github.com/grafana/tanka/releases/latest/download/tk-linux-amd64`{{execute}}

`sudo chmod a+x /usr/local/bin/tk`{{execute}}

`sudo curl -Lo /usr/local/bin/jb https://github.com/jsonnet-bundler/jsonnet-bundler/releases/latest/download/jb-linux-amd64`{{execute}}

`sudo chmod a+x /usr/local/bin/jb`{{execute}}

Clone TNS repository by executing following command:

`git clone https://github.com/grafana/tns`{{execute}}

Install TNS by executing following command:

`tns/install kubernetes-admin@kubernetes`{{execute}}

When prompted `Please type 'yes' to confirm:`, answer `yes`{{execute}}.

Installing takes minutes.
Execute the following command until the status of all pods shows up `Running`:

`kubectl get po -A`{{execute}}

Forward the environment's port to access the nginx of TNS by executing following command:

`kubectl port-forward svc/nginx 80:80 --address 0.0.0.0 &> /dev/null &`{{execute}}

[Click here]({{TRAFFIC_HOST1_80}}) to access the frontend
or [click here]({{TRAFFIC_HOST1_80}}/grafana) to access the Grafana.
