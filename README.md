# Grafana, Prometheus & Node_exporter ansible setup

Simple role to setup a new Grafana & Prometheus server with a node_exporter. This has only been tested on:

- AlmaLinux 9.0
- AlmaLinux 9.1

## Requirements

Minimum `AlmaLinux 9.0` node.

## Role Variables

The variables are defined in `defaults/main.yml`. These should be configured as needed:

| Variable | Default | Info |
| :------- | :------ | :--- |
| `hostname`                      | `grafana-server` | Hostname of the system                            |
| `packages`                      | `[]`             | General packages that should be installed         |
| ---      |         |      |
| `prometheus_install`            | `true`           | Should prometheus be installed?                   |
| `prometheus_user`               | `prometheus`     | User for prometheus installation                  |
| `prometheus_download_location`  | `/tmp`           | Download location                                 |
| `prometheus_version`            | `2.41.0`         | Version that should be installed                  |
| ---      |         |      |
| `exporter_install`            | `true`             | Should node_exporter be installed?                |
| `exporter_user`               | `node_exporter`    | User for node_exporter installation               |
| `exporter_download_location`  | `/tmp`             | Download location                                 |
| `exporter_version`            | `1.5.0`            | Version that should be installed                  |

## Warnings

The ports can also be changed for more security (might be a future variable).

## Example playbook

```yml
---
- name: test playbook
  hosts: general

  roles:
  - role: ansible-grafana
```
