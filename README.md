[Grafana](https://grafana.com/grafana) Dashboard for
[Prometheus](https://prometheus.io/) official [Python
client](https://github.com/prometheus/client_python) with Flask Web
Application metrics in focus.

## Screenshots ##

![Flask Web App Grafana Dashboard 1](/docs/flask-app-1.png?raw=true "RPS and Latency panels")
![Flask Web App Grafana Dashboard 2](/docs/flask-app-2.png?raw=true "Error panels, CPU, Memory, file descriptors usage ")
![Flask Web App Grafana Dashboard 3](/docs/flask-app-3.png?raw=true "App's uptime, version, deployment env, Python interpretor info")

## About ##

The dashboard designed for a [Flask](http://flask.pocoo.org/) web
application. Specifically it's been used in
[Pili](https://github.com/pilosus/pili/blob/master/pili/app.py#L62)
web app developed with [Kubernetes](https://kubernetes.io/)
orchestration in mind.

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

## Usage ##

1. Tweak dashboard JSON file ``flask-web-app.json`` to fit your
   metrics and needs (take a look at the original app's metrics
   [here](https://github.com/pilosus/pili/blob/master/pili/app.py))
2. Import JSON at ``/dashboard/import``

## License ##

The dashboard configuration licensed under the MIT License (MIT). See
``LICENSE`` file.
