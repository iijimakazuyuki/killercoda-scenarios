There is a Spring Boot demo application in the demo directory.

First, install JRE by executing following command:

`apt install openjdk-17-jre-headless -y`{{execute}}

And install nerdctl by executing following commands:

`curl -LO https://github.com/containerd/nerdctl/releases/download/v1.6.2/nerdctl-1.6.2-linux-amd64.tar.gz`{{execute}}

`tar zxf nerdctl-1.6.2-linux-amd64.tar.gz`{{execute}}

`sudo mv nerdctl /usr/local/bin`{{execute}}

Then build and load container image by executing following commands:

`cd demo`{{execute}}

`chmod +x gradlew`{{execute}}

`./gradlew jibBuildTar --image=localhost/demo:0.0.1`{{execute}}

`nerdctl -n k8s.io image load -i build/jib-image.tar`{{execute}}

Run the demo application on kubernetes by executing following commands:

`cd ../manifests`{{execute}}

`kubectl apply -f .`{{execute}}

Execute the following command until the status of a pod shows up `Running`:

`kubectl get po -l app=demo`{{execute}}

Forward the environment's port to access the app by executing following command:
`kubectl port-forward svc/demo 8080:8080 --address 0.0.0.0 &> /dev/null &`{{execute}}

[Click here]({{TRAFFIC_HOST1_8080}}/hello) to access the app
or [click here]({{TRAFFIC_HOST1_8080}}/actuator/prometheus) to access its prometheus metrics.
