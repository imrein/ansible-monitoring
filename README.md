# Monitoring ansible setup

<p align="center">
<img src="https://ansible.readthedocs.io/projects/ansible-core/devel/_static/images/Ansible-Mark-RGB_White.png" width=100>
<img src="https://grafana.com/media/docs/grafana-cloud/infrastructure/grafanalogo.svg" width=90 style="margin: 0 10px;">
&nbsp;
<img src="https://github.com/prometheus/prometheus/raw/main/documentation/images/prometheus-logo.svg" width=100 style="margin: 0 5px;">
&nbsp;
<img src="https://grafana.com/static/img/logos/logo-loki.svg" width=80>
</p>

## Overview
[![CI](https://github.com/imrein/ansible-monitoring/actions/workflows/ci.yml/badge.svg)](https://github.com/imrein/ansible-monitoring/actions/workflows/ci.yml)

Role to setup a new monitoring server. This stack is modular and comes with:

- Grafana
- Prometheus
- Loki
- Node_exporter
- Promtail

This has been tested on:

- RHEL based distros
- Debian
- Ubuntu

> [!TIP]
> The testing will be done using [molecule](https://ansible.readthedocs.io/projects/molecule/) and is automated using github-actions.

## Requirements

A machine with an SSH connection.

## Role Variables

The variables are defined in `defaults/main.yml`. These should be configured as needed:

| Variable | Default | Info |
| :------- | :------ | :--- |
| `download_location`               | `/tmp`           | Download location                                 |
| `packages`                        | `[]`             | General packages that should be installed         |
| ---      |         |      |
| `grafana_version`                 | `x.x.x`          | Package version to be installed                   |
| `grafana_datasources`             | `[]`             | Datasources that should be added                  |
| ---      |         |      |
| `prometheus_user`                 | `prometheus`     | User for prometheus installation                  |
| `prometheus_version`              | `x.x.x`          | Package version to be installed                   |
| `prometheus_scrape_config_jobs`   | `[]`             | Define scrap jobs                                 |
| ---      |         |      |
| `node_exporter_user`              | `node_exporter`  | User for node_exporter installation               |
| `node_exporter_version`           | `x.x.x`          | Package version to be installed                   |
| `node_exporter_architecture`      | `amd64`          | Package architecture                              |
| ---      |         |              |
| `loki_user`                       | `loki`           | User for loki installation                        |
| `loki_version`                    | `x.x.x`          | Package version to be installed                   |
| ---      |         |      |
| `fluentbit_user`                  | `fluentbit`      | User for fluentbit installation                   |
| `fluentbit_loki_server`           | `127.0.0.1`      | Loki server to ship to                            |
| `fluentbit_scrape_configs`        | `[]`             | Files to scrape for logging                       |
| `fluentbit_config_service`        | `[]`             | Config for fluentbit service                      |
| `fluentbit_config_input`          | `[]`             | Config for fluentbit input                        |
| `fluentbit_config_output`         | `[]`             | Config for fluentbit output                       |

## Example playbook

> [!NOTE]
> Use [ansible tags](https://docs.ansible.com/ansible/latest/playbook_guide/playbooks_tags.html#selecting-or-skipping-tags-when-you-run-a-playbook) to select which components to setup. Multiple ones can be selected at once.

```yml
---
- name: test playbook
  hosts: general

  roles:
  - role: ansible-monitoring -b --tags 'prometheus'
```
