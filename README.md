# Ansible Role:  nginx

[![CI](https://github.com/dcjulian29/ansible-role-nginx/actions/workflows/ci.yml/badge.svg)](https://github.com/dcjulian29/ansible-role-nginx/actions/workflows/ci.yml) [![GitHub Issues](https://img.shields.io/github/issues-raw/dcjulian29/ansible-role-nginx.svg)](https://github.com/dcjulian29/ansible-role-nginx/issues)

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

None

## Role Variables

The `defaults` variables define the default values used in the play. These variables can be overridden using `group_vars` or `host_vars` or from the playbook itself.

| Variable | Default Value | Description |
| --: | :-- | :-- |
| nginx_package_name | `nginx` | The name of the package to install. |
| nginx_service_state | `started` | The state of the service when this play is finished. |
| nginx_service_enabled | `true` | The service is enabled to start on boot. |
| nginx_conf_path | `/etc/nginx/conf.d` | The location of the configuration files. |
| nginx_conf_file_path | `/etc/nginx/nginx.conf` | The location of the primary server configuration. |
| nginx_remove_default_vhost | `true` | Remove the default installation page. |
| nginx_error_log | `"/var/log/nginx/error.log warn"` | The default location of the primary error log and the log level to send. |
| nginx_worker_processes | `<ProcessorCount>` | The number of worker process to start. |
| nginx_worker_connections | `1024` | The number of connections per worker allowed. |
| nginx_multi_accept | `"off"` | Have no idea what this is. |
| nginx_server_names_hash_bucket_size | `128` | The size of the hash bucket. |
| nginx_client_max_body_size | `"64m"` | The maximum size the client can send in the body of the request. |
| nginx_ssl_ecdh_curve | `secp384r1` | The elliptic curve this server will use. |
| nginx_ssl_enabled | `false` | Should this server serve HTTPS? |
| nginx_ssl_dhparams_size | `2048` | The size in bits for the dhparams file used to harden TLS. |
| nginx_ssl_ciphers | `EECDH+AESGCM EDH+AESGCM kEECDH+ECDSA+AES256 kEECDH+AES256` | The TLS ciphers that the server will use. |
| nginx_ssl_protocols | `TLSv1.1 TLSv1.2 TLSv1.3` | Which protocols will this server support? |
| nginx_access_log | `/var/log/nginx/access.log main buffer=16k flush=2m` | The default location of the primary access log. |
| nginx_log_format | `$remote_addr - $remote_user [$time_local] "$request" $status $body_bytes_sent "$http_referer" "$http_user_agent" "$http_x_forwarded_for"` | The default format for logging |
| nginx_gzip | `"on"` | Turn on gzip compression. |
| nginx_sendfile | `"on"` | Elimate the step of copying the data into a buffer before sending. |
| nginx_tcp_nopush | `"on"` | Optimize the amount of data sent at once. |
| nginx_tcp_nodelay | `"on"` | Send data without delay regardless of packet length. |
| nginx_keepalive_timeout | `65` | How long to allow keepalive. |
| nginx_keepalive_requests | `100` | Sets the maximum number of requests that can be served through one keep-alive connection. |
| nginx_server_tokens | `"off"` | Include server tokens in response. |
| nginx_extra_conf_options | `""` | Extra main options, used within the main nginx context. |
| nginx_extra_http_options | `""` | Extra http options, printed inside the main server http config. |
| nginx_upstreams | `[]` | The default is for no upstreams, but the following can be included to form an array. |
|| strategy | `ip_hash`, `least_conn`, etc. |
|| keepalive | Optional value to override global keepalive |
|| servers | An array of strings that identify the upstream servers along with their weight optionally. |
| nginx_vhosts | `[]` | An array containing each virtual host that this server will serve. |
|| listen | Port to listen on. |
|| listen_ipv6 | Listen on IPv6 stack. |
|| server_name | The name for the server, primarily used with host headers and SNI. |
|| root | The root folder of the web site. |
|| index | The default page to serve when none is specified.
|| filename | Can be used to set the vhost filename. |
|| acme | If true, add .well-known location for HTTP validation of ACME certificates. |
|| acme_challenge | Folder path to use for .well-known location. |
|| hsts | Add Strict-Transport-Security header to HTTPS Pinning. |
|| hsts_age | Number of days until HSTS expiration. |
|| ocsp | Use OCSP stapling. |
|| ocsp_cert | Path to HTTPS stapling OCSP certificate. |
|| ssl_cert | File path to SSL certificate file. |
|| ssl_key | File path to SSL key file. |
|| ssl_listen | The port to listen on for HTTPS. |
|| server_name_redirect | URL to redirect to. |
|| error_page | Custom error page to serve. |
|| access_log | Custom access log for site. |
|| error_log | Custom error log for site. |
|| extra_parameters | Can be used to add extra config blocks (multiline). |
|| state | Use `absent` to remove the vhost configuration. |
|| protect_content_sniffing | Add header to protect from content sniffing. |
|| protect_frame_embedded | Add header to protect page from being embedded in IFRAME. |
|| protect_frame_option | `DENY` or `SAMEORIGIN` to enable use within domain. |
|| protect_cross_site_scripting | Add header to protect from XSS. |
|| protect_robots | Add header to protect against robot sniffing. |

## Example Playbook

The examples directory include one or more example playbooks.
