# Lab2
## 1-How do I trigger a Prometheus alert?
an alerting rule must be defined in the Prometheus configuration. This is done by adding a new section for alerting rules in the prometheus.yml file, and creating a new file to define the alerting rules. The alerting rule specifies the conditions that should trigger the alert, as well as the notification targets to send the alert to. Once the rule is defined and the configuration is reloaded, Prometheus will evaluate the rule and fire an alert if the conditions are met.


## 2-What is the difference between node exporter and mysql exporter ?
Node Exporter and MySQL Exporter are both Prometheus exporters that allow Prometheus to collect metrics from different sources.there are some differences between them:
- Node Exporter: Node Exporter is used to collect system-level metrics from a host machine, such as CPU usage, memory usage, disk usage, network traffic, and more. It exports these metrics in Prometheus format, allowing Prometheus to scrape and store them for later analysis.
- MySQL Exporter: MySQL Exporter is used to collect metrics from a MySQL database, such as queries per second, slow queries, connections, network traffic, and more. It exports these metrics in Prometheus format, allowing Prometheus to scrape and store them for later analysis.

## 3-what is the maximum retention period to save data in Prometheus and how to increase it ?
Prometheus is a time-series database that stores metric data for a certain period of time, which is called the retention period. By default, Prometheus stores data for 15 days. However, the retention period can be increased by modifying the retention time in the Prometheus configuration file.

The retention time is defined in the storage configuration section of the prometheus.yml file. The duration can be specified in various units, such as hours, days, and years. Once the retention period has been set, Prometheus will continue to store data for the specified duration.

It is important to note that increasing the retention period will also increase the amount of disk space required to store the data. Therefore, it is recommended to monitor the disk usage regularly and ensure that there is enough disk space available to accommodate the increased retention period.


## 4-What are the different PromQL data types available in Prometheus Expression language?
The different PromQL data types available in Prometheus Expression Language are:
- Scalars: This includes numbers, strings, and booleans.
- Vectors: A vector is a set of time series data, identified by their metric names and a set of labels.
- Strings: A string data type stores text data

## 5-How To calculate the average request duration over the last 5 minutes from a histogram ?
To calculate the average request duration over the last 5 minutes from a histogram, you can use the histogram_quantile function to calculate the 95th percentile, and then divide it by the count of observations to get the average. Here's an example PromQL query:
``` sum(rate(http_request_duration_seconds_bucket{job="myjob"}[5m])) by (le)
/ sum(rate(http_request_duration_seconds_count{job="myjob"}[5m])) by (le)
```
## 6-What is Thanos Prometheus?
Thanos is a set of components that adds high availability, scalability, and long-term storage to Prometheus. It extends Prometheus by allowing you to store and query historical data across multiple Prometheus servers, as well as providing a centralized view of all metrics across all servers.

## 7-what is promtool and how i can use it ?
promtool is a command-line tool that is included with Prometheus. It provides various utilities for working with Prometheus configuration files, such as validating rules, checking for configuration errors, and testing alerting rules. To use promtool, simply run it from the command line and specify the appropriate subcommand and arguments.

## 8-What types of Monitoring can be done via Grafana?
Grafana can be used for a wide range of monitoring and visualization tasks, including:
- Infrastructure monitoring: Grafana can be used to monitor various aspects of infrastructure, such as CPU usage, memory usage, disk usage, and network traffic.
- Application monitoring: Grafana can be used to monitor various metrics related to application performance, such as response times, error rates, and throughput.
- Log analysis: Grafana can be used to analyze logs from various sources, such as application logs, system logs, and network logs.
- Business intelligence: Grafana can be used to create dashboards and reports to help monitor key performance indicators (KPIs) and other business metrics.

## 9-Can we see different Servers CPU comparison in Grafana
Yes, Grafana can be used to compare the CPU usage of different servers. This can be done by using the Prometheus data source to query the CPU usage data from each server, and then creating a graph or dashboard in Grafana to compare the data.
