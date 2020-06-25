# Ansible role - `prometheus_server`

Setup a Prometheus server running as a Docker container.

If you whish to setup a local Prometheus server on a Kubernetes cluster, you should use the role `k8s_prometheus`.

## Tags

| Tag        | Description                                |
|------------|--------------------------------------------|
| `setup`    | Deploy Prometheus and associated resources |
| `teardown` | Remove Prometheus and associated resources |
| `remove`   | Remove Prometheus and associated resources |

## Variables

| Variable                          | Type     | Required | Default             | Description |
|-----------------------------------|----------|----------|---------------------|-------------|
| `prometheus_server_tag`           | `string` | No       | `latest`            |             |
| `prometheus_server_project_name`  | `string` | No       | `prometheus-server` |             |
| `prometheus_server_port`          | `string` | No       | `9090`              |             |
| `prometheus_server_tls_crt`       | `string` | No       | `""` (empry string) |             |
| `prometheus_server_tls_key`       | `string` | No       | `""` (empry string) |             |
| `prometheus_server_config_volume` | `string` | No       | `/opt/prometheus`   |             |
| `prometheus_server_config_mount`  | `string` | No       | `/etc/prometheus`   |             |
| `prometheus_config`               | `string` | No       | `{}`                |             |
