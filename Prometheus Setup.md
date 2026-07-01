# Prometheus Installation

## How to Install Prometheus

In this course, we’ll also need a working Prometheus installation. We will use this to retrieve metrics for use in examples, labs, and so on. We will primarily run it as part of a Docker Compose environment.

If you’re interested in other ways to install Prometheus, visit the Prometheus website or revisit the Chapter One video of the Prometheus Essential Training course.

**Prometheus Installation Documentation:**

https://prometheus.io/docs/prometheus/latest/installation/

**Using Docker Compose**

### 1. Confirm that Docker Compose is available.

If it isn’t, verify your Docker installation.

```bash
docker compose version
```

### 2. Create a `prometheus.yml` file with the following contents.

This will create a sample scrape configuration.

```yaml
global:
  scrape_interval: 15s
  evaluation_interval: 15s

scrape_configs:
  - job_name: "prometheus"
    scrape_interval: 15s
    static_configs:
      - targets:
          - "localhost:9090"
```

### 3. Add the following to the existing `docker-compose.yaml` file.

```yaml
prometheus:
  image: prom/prometheus
  volumes:
    - ./prometheus.yml:/etc/prometheus/prometheus.yml
  ports:
    - "9090:9090"
  restart: unless-stopped
```

### 4. Start up the container using the Docker Compose command and view the logs.

```bash
docker compose up -d
docker compose logs -f
```

Once the container is running, you can access Prometheus from your browser at:

```text
http://localhost:9090
```

You can stop the running containers using:

```bash
docker compose down
```
