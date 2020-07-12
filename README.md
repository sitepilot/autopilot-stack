# Autopilot Stack

![Autopilot Stack](https://github.com/sitepilot/autopilot-stack/workflows/run-tests/badge.svg)

Run the latest version of [Autopilot](https://github.com/sitepilot/autopilot) and additional services with Docker and Docker Compose.

## Requirements

* [Laravel Nova License](https://nova.laravel.com/)
* [Docker Engine](https://docs.docker.com/get-docker/) version 17.05 or newer
* [Docker Compose](https://docs.docker.com/compose/install/) version 1.20.0 or newer

## Installation

* Clone this repository.
* Copy `.env.example` to `.env` and modify it to your needs.
* Run `./autopilot install` to start the Docker containers and install Autopilot.

## Containers

The Autopilot Stack consists out of the following containers:

* [Autopilot](https://github.com/sitepilot/autopilot)
* [MariaDB 10.4 (by Bitnami)](https://hub.docker.com/r/bitnami/mariadb)
* [Redis 6.0 (by Bitnami)](https://hub.docker.com/r/bitnami/redis)
* [Grafana 7 (by Bitnami)](https://hub.docker.com/r/bitnami/grafana)
* [Prometheus 2 (by Bitnami)](https://hub.docker.com/r/bitnami/grafana)
* [Alertmanager 0.21.0 (by Bitnami)](https://hub.docker.com/r/bitnami/alertmanager)
* [Blackbox Exporter 0.17.0 (by Bitnami)](https://hub.docker.com/r/bitnami/blackbox-exporter)

## Access

* Autopilot - `https://<server-ip>`
* Grafana - `https://<server-ip>/status/`.
* Prometheus - `https://<server-ip>/monitor/prometheus`.
* Alertmanager - `https://<server-ip>/monitor/alertmanager`.
* Blackbox Exporter - `https://<server-ip>/monitor/blackbox`.

### Login

* Email: `admin@sitepilot.io`
* Password: `supersecret`

*NOTE: The monitor service URLS are protected with HTTP Basic Authentication. User: `autopilot`, password: `supersecret`.*

## Configuration

### Environment Variables

Refer to the [Autopilot repository](https://github.com/sitepilot/autopilot) for a list of available environment variables.

### Service Configuration

Create a `docker-compose.override.yml` file to override the configuration of any service in the Autopilot Stack and run `./autopilot restart` to restart all services. 

Example:

```yaml
alertmanager:
  volumes:
    - "./custom/alertmanager/alertmanager.yml:/opt/bitnami/alertmanager/conf/config.yml"
```