First, install the latest Docker Compose by executing following commands:

`curl -Lo docker-compose https://github.com/docker/compose/releases/latest/download/docker-compose-linux-x86_64`{{execute}}

`chmod +x docker-compose`{{execute}}

`sudo mv docker-compose $(which docker-compose)`{{execute}}

Clone OpenTelemetry demo repository by executing following command:

`git clone https://github.com/open-telemetry/opentelemetry-demo.git`{{execute}}

Install OpenTelemetry demo by executing following command:

`docker-compose -f opentelemetry-demo/docker-compose.minimal.yml up -d --no-build`{{execute}}

Installing takes minutes.

[Click here]({{TRAFFIC_HOST1_8080}}) to access the frontend
or [click here]({{TRAFFIC_HOST1_8080}}/grafana) to access the Grafana.
