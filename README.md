# Ansible Role:  nginx

[![Lint](https://github.com/dcjulian29/ansible-role-nginx/actions/workflows/lint.yml/badge.svg)](https://github.com/dcjulian29/ansible-role-nginx/actions/workflows/lint.yml) [![GitHub Issues](https://img.shields.io/github/issues-raw/dcjulian29/ansible-role-nginx.svg)](https://github.com/dcjulian29/ansible-role-nginx/issues)

This an Ansible role to install Nginx HTTP and reverse proxy server. I primarily use as a static web site or a reverse proxy to other services either locally or via upstream servers.

## Requirements

- None

## Installation

To use, use `requirements.yml` with the following git source:

```yaml
---
roles:
- name: dcjulian29.nginx
  src: https://github.com/dcjulian29/ansible-role-nginx.git
  version: main
  ```

Then download it with `ansible-galaxy`:

```shell
ansible-galaxy install -r requirements.yml
```

## Dependencies

- None
