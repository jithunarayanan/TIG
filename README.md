# TIG Docker deployment

<p align="center">
    <img src="./example.png" alt="Image" style="display:block; margin:auto;">
</p>

TIG Stack stand for Telegraf, InfluxDB, and Grafana.

*InfluxDB* is an open-source time series database written in Go. Optimized for fast, high-availability storage and used as a data store for any use case involving large amounts of time-stamped data, including DevOps monitoring, log data, application metrics and real-time analytics.

*Telegraf* is an agent for collecting, processing, aggregating, and writing metrics. It supports various output plugins such as influxdb, Graphite, Kafka,etc.

*Grafana* is an open source data visualization and monitoring suite. It offers support for Graphite, Elasticsearch, Prometheus, influxdb, and many more databases. The tool provides a beautiful dashboard and metric analytics, with the ability to manage and create your own dashboard for your apps or infrastructure performance monitoring.

## Pre requisites

* Make sure the latest docker version is installed.


## Start the stack with docker compose

```bash
$ docker-compose up
```

## Services and Ports

### Grafana
- URL: http://localhost:3000 
- User: admin 
- Password: admin 

### Telegraf
- Port: 8125 UDP (StatsD input)

### InfluxDB
- Port: 8086 (HTTP API)
- User: admin 
- Password: admin 
- Database: influx


Run the influx client:

```bash
$ docker-compose exec influxdb influx -execute 'SHOW DATABASES'
```

Run the influx interactive console:

```bash
$ docker-compose exec influxdb influx
```

If you want to [Import](https://docs.influxdata.com/influxdb/v1.8/tools/shell/#import-data-from-a-file-with-import) data from a file with -import:

```bash
$ docker-compose exec -w /imports influxdb influx -import -path=data.txt -precision=s
```

## Finishing touches
1. Ceate or [import](https://grafana.com/grafana/dashboards/) your own dashboards.
2. If your host is not a docker environment Install telegraf from [here](https://docs.influxdata.com/telegraf/v1.21/introduction/installation/).

## License
GPL
