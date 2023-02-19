# Grafana, Prometheus & Node_exporter ansible setup

Simple role to setup a new Grafana & Prometheus server with a node_exporter. This has only been tested on:

- AlmaLinux 9.0
- AlmaLinux 9.1

## Requirements

Minimum `AlmaLinux 9.0` node.

## Role Variables

The variables are defined in `defaults/main.yml`. These should be configured as needed:

- `hostname`
- `packages`
- `prometheus_user`
- `prometheus_download_location`
- `prometheus_version`
- `exporter_user`
- `exporter_download_location`
- `exporter_version`

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
