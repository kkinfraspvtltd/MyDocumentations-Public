# Grafana Installation

## Basic Grafana Configuration

In this section, we will explore basic configuration options available in Grafana. We will use the Docker Compose environment, but these configurations apply anywhere Grafana is installed.

In Docker, the recommended way to configure Grafana is by using environment variables. You can override configuration options using environment variables that follow a specific naming convention:

```text
GF_<SectionName>_<KeyName>
```

Where:

- `<SectionName>` corresponds to the section in the `grafana.ini` file (for example, `server`).
- `<KeyName>` is the specific configuration key within that section (for example, `http_port`).

Some examples include:

- `GF_SECURITY_ADMIN_USER`
- `GF_SECURITY_ADMIN_PASSWORD`

These can be used to set the initial username and password for the administrator user.

You can also configure:

- `GF_SERVER_HTTP_PORT`
- `GF_SERVER_ROOT_URL`

These are useful if you are running Grafana behind a reverse proxy.

In the Docker Compose file, you can set these environment variables using additional key-value pairs:

```yaml
services:
  grafana:
    image: grafana/grafana:latest
    ports:
      - "3000:3000"
    environment:
      - GF_SECURITY_ADMIN_USER=mygrafanaadmin
      - GF_SECURITY_ADMIN_PASSWORD=securepassword
```

To learn more, visit the Grafana documentation:

https://grafana.com/docs/grafana/latest/setup-grafana/configure-grafana/

In Chapter Nine, we will also do a deep dive into Grafana configuration, especially the `grafana.ini` configuration file.
