There is a Spring Boot demo application in the demo directory.
First, build container image by executing following commands:

`cd demo`{{execute}}

`./gradlew jibDockerBuild --image=localhost/demo:0.0.1`{{execute}}

Run the demo application on kubernetes by executing following commands:

`cd ../manifests`{{execute}}

`kubectl apply -f .`{{execute}}

Execute the following command until the status of a pod shows up `Running`:

`kubectl get po`{{execute}}

Forward the environment's port to access the app by executing following command:
`kubectl port-forward svc/demo 8080:8080 --address 0.0.0.0 &> /dev/null &`{{execute}}

[Click here]({{TRAFFIC_HOST1_8080}}/hello) to access the app
or [click here]({{TRAFFIC_HOST1_8080}}/actuator/prometheus) to access its prometheus metrics.
