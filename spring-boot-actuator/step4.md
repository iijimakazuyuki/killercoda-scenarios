[Click here]({{TRAFFIC_HOST1_3000}}/connections/datasources/prometheus) to add a Prometheus datasource to Grafana.

Click `Add new data source` button

![Add new data source](add_new_data_source.png)

and input `http://prometheus-server` in `HTTP > Prometheus server URL`,

![Prometheus server URL](prometheus_server_url.png)

and click `Save & test` button at the end of the page.

![Save & test](save_and_test.png)

[Click here]({{TRAFFIC_HOST1_3000}}/dashboard/import) to add a dashboard to Grafana.

Input `11378` in `Import via grafana.com`

![Import via grafana.com](import_dashboard_1.png)

and click `Load` button.

Select Prometheus data source from the pull down list, and click `Import` button.

![Import dashboard](import_dashboard_2.png)

You can see a dashboard.

![Dashboard](dashboard.png)
