# Monitoring ansible setup

Role to setup a new monitoring server. This stack is modular and comes with:

- Grafana
- Prometheus
- Node_exporter
- Loki
- Promtail

This has been tested on:

- AlmaLinux 8.8
- AlmaLinux 9.0
- AlmaLinux 9.1
- Debian 11.8
- Ubuntu 20.04
- Ubuntu 22.04

## Requirements

Minimum `AlmaLinux 9.0` node.

## Role Variables

The variables are defined in `defaults/main.yml`. These should be configured as needed:

| Variable | Default | Info |
| :------- | :------ | :--- |
| `hostname`                      | `grafana-server` | Hostname of the system                            |
| `download_location`             | `/tmp`           | Download location                                 |
| `packages`                      | `[]`             | General packages that should be installed         |
| ---      |         |      |
| `prometheus_install`            | `true`           | Should prometheus be installed?                   |
| `prometheus_user`               | `prometheus`     | User for prometheus installation                  |
| `prometheus_version`            | `2.47.2`         | Version that should be installed                  |
| ---      |         |      |
| `exporter_install`              | `true`           | Should node_exporter be installed?                |
| `exporter_user`                 | `node_exporter`  | User for node_exporter installation               |
| `exporter_version`              | `1.6.1`          | Version that should be installed                  |
| ---      |         |            |
| `loki_install`                  | `true`           | Should loki be installed?                         |
| `loki_user`                     | `loki`           | User for loki installation                        |
| `loki_version`                  | `2.9.2`          | Version that should be installed                  |
| ---      |         |      |
| `promtail_install`              | `true`           | Should promtail be installed?                     |
| `promtail_user`                 | `promtail`       | User for promtail installation                    |
| `promtail_version`              | `2.9.2`          | Version that should be installed                  |

## Warnings

The ports can also be changed for more security (might be a future variable).

## Example playbook

```yml
---
- name: test playbook
  hosts: general

  roles:
  - role: ansible-monitoring
```
