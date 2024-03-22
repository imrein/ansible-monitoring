# Monitoring ansible setup

Role to setup a new monitoring server. This stack is modular and comes with:

- Grafana
- Prometheus
- Node_exporter
- Loki
- Promtail

This has been tested on:

- RHEL based distros
- Debian
- Ubuntu

## Requirements

A machine with an SSH connection.

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
| ---      |         |      |
| `exporter_install`              | `true`           | Should node_exporter be installed?                |
| `exporter_user`                 | `node_exporter`  | User for node_exporter installation               |
| ---      |         |            |
| `loki_install`                  | `true`           | Should loki be installed?                         |
| `loki_user`                     | `loki`           | User for loki installation                        |
| ---      |         |      |
| `promtail_install`              | `true`           | Should promtail be installed?                     |
| `promtail_user`                 | `promtail`       | User for promtail installation                    |

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
