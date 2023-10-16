There is a Spring Boot demo application in the current directory.
This application can be built as a container image and run in kubernetes.

First, build the application container image by executing following command:

`docker run -it --rm -v $PWD:/src -w /src gradle:8-jdk17 gradle jibBuildTar --image=localhost/demo:0.0.1`{{execute}}

Now the container image is located in `build/jib-image.tar`.

The container runtime of this environment's kubernetes is containerd.
Install nerdctl, which is a command line tool of containerd, by executing following commands:

`curl -LO https://github.com/containerd/nerdctl/releases/download/v1.6.2/nerdctl-1.6.2-linux-amd64.tar.gz`{{execute}}

`tar zxf nerdctl-1.6.2-linux-amd64.tar.gz`{{execute}}

`sudo mv nerdctl /usr/local/bin`{{execute}}

Then load the container image to containerd by executing following commands:

`nerdctl -n k8s.io image load -i build/jib-image.tar`{{execute}}

Run the demo application on kubernetes by executing following command:

`kubectl apply -f manifests`{{execute}}

Execute the following command until the status of a pod shows up `Running`:

`kubectl get po -l app=demo`{{execute}}

Forward the environment's port to access the app by executing following command:
`kubectl port-forward svc/demo 8080:8080 --address 0.0.0.0 &> /dev/null &`{{execute}}

[Click here]({{TRAFFIC_HOST1_8080}}/hello) to access the app
or [click here]({{TRAFFIC_HOST1_8080}}/actuator/prometheus) to access its prometheus metrics.
