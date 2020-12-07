# Ansible role - `prometheus_server`

Setup a Prometheus server running as a Docker container.

If you whish to setup a local Prometheus server on a Kubernetes cluster, you should use the role `k8s_prometheus`.

## Tags

| Tag        | Description                                |
|------------|--------------------------------------------|
| `setup`    | Deploy Prometheus and associated resources |
| `update`   | Update Prometheus configuration            |
| `teardown` | Remove Prometheus and associated resources |
| `remove`   | Remove Prometheus and associated resources |

## Variables

| Variable                                | Type     | Required | Default                | Description                                     |
|-----------------------------------------|----------|----------|------------------------|-------------------------------------------------|
| `prometheus_server_tag`                 | `string` | No       | `latest`               | Prometheus Docker image tag                     |
| `prometheus_server_project_name`        | `string` | No       | `prometheus-server`    | Docker compose project name                     |
| `prometheus_server_port`                | `string` | No       | `9090`                 | Prometheus server port                          |
| `prometheus_server_tls_crt`             | `string` | No       | `""` (empty string)    | Prometheus server SSL certificate               |
| `prometheus_server_tls_key`             | `string` | No       | `""` (empty string)    | Prometheus server SSL key                       |
| `prometheus_server_tsdb_retention_size` | `string` | No       | `"200GB"`              | Retention size in GB                            |
| `prometheus_server_tsdb_retention_time` | `string` | No       | `"365d"`               | Retention time                                  |
| `prometheus_server_config_volume`       | `string` | No       | `/opt/prometheus`      | Prometheus configuration file path on host      |
| `prometheus_server_config_mount`        | `string` | No       | `/etc/prometheus`      | Prometheus configuration file path in container |
| `prometheus_server_config`              | `string` | No       | `{}` (empty YAML map)  | Prometheus server configuration (YAML string)   |
| `prometheus_server_data_volume`         | `string` | No       | `/opt/prometheus/data` | Prometheus server data path on host             |
| `prometheus_server_data_mount`          | `string` | No       | `/prometheus`          | Prometheus server data path in container        |
| `prometheus_server_HostRegexps`         | `list`   | No       | `{host:.*}`            | Traefik routing rule                            |

## Templates

| Template                | Description                            |
|-------------------------|----------------------------------------|
| `docker-compose.yml.j2` | Docker compose project file            |
| `prometheus.yml.j2`     | Prometheus configuration file template |
| `traefik.yml.j2`        | Traefik configuration file template    |

---

## Ho to

## How is it deployed ?

The Prometheus server instance is deployed through a Dokcer compose stack made
of two containers:

| Container    | Description           |
|--------------|-----------------------|
| `traefik`    | HTTP(s) load balancer |
| `prometheus` | Prometheus server     |

## How to update or change the configuration ?

Edit the variabe `prometheus_server_config`, which should contains the
Prometheus YAML confguration. This varibale is set at host level in your
inventory most of the time.
