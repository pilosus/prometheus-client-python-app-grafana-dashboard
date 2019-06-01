Grafana dashboard designed for a Flask web application that exposes
metrics with
[flask_prometheus_metrics](https://github.com/pilosus/flask_prometheus_metrics)
Flask extension

Dashboard aimed at the apps deployed with Kubernetes, although it can
be easily tweaked to be infrastructure-agnostic.

## Screenshots ##

![Flask Web App Grafana Dashboard 1](/docs/flask-app-1.png?raw=true "RPS and Latency panels")
![Flask Web App Grafana Dashboard 2](/docs/flask-app-2.png?raw=true "Error panels, CPU, Memory, file descriptors usage ")
![Flask Web App Grafana Dashboard 3](/docs/flask-app-3.png?raw=true "App's uptime, version, deployment env, Python interpretor info")

## Usage ##

1. Install [flask_prometheus_metrics](https://github.com/pilosus/flask_prometheus_metrics) exporter to your Flask application
2. Make Prometheus scraping your app's ``/metrics`` endpoint
3. Import [flask-web-app.json](flask-web-app.json) at ``https://<your-grafana-domain>.tld/dashboard/import``

If you do not deploy your app in Kubernetes you may need to tweak
[flask-web-app.json](flask-web-app.json) ``pod`` labels to meet your
needs. Instead of ``pod`` you may use ``instance`` or ``hostname`` or
other label names in depending on how your Prometheus handle your
app's hostname.

## Panel ##

12 panels covers the following metrics:

- Requests per second
- Latency
- Percentiles (latency within which certain percent of requests served)
- Number of 4xx, 5xx errors per second
- Error count by endpoint
- CPU usage
- Memory usage
- Open file descriptors
- App's uptime
- App's version
- App's deployment environment (e.g. development, staging, production)
- Python interpretor version

Dashboard provides variables:

- Prometheus datasource
- Time interval
- Kubernetes pod name
- App's endpoint
- HTTP method
- Percentile
- HTTP status code for errors

The variables allow to change some panels charts grouing, intervals,
labels selection.
