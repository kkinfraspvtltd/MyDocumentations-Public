# Grafana Installation

## How to Install Grafana on Linux Debian or Ubuntu

The steps below will show you how to install and start Grafana on any Linux Debian or Ubuntu machine. This could be your laptop or a cloud server. Feel free to skip to the relevant instruction text for your needs. We will be using Docker for most practical examples throughout the course.

The recommended method for installing Grafana on Debian is by leveraging the official Grafana APT repository. You can do so using the following steps:

### 1. Ensure that the package lists are up-to-date.

```bash
sudo apt update
```

### 2. Install prerequisite packages that are required for using HTTPS repositories and GPG keys.

```bash
sudo apt-get install -y apt-transport-https software-properties-common wget
```

### 3. Add the Grafana GPG key to the system's list of trusted keys.

```bash
sudo mkdir -p /etc/apt/keyrings/

wget -q -O - https://apt.grafana.com/gpg.key | gpg --dearmor | sudo tee /etc/apt/keyrings/grafana.gpg > /dev/null
```

### 4. Add the official Grafana APT repository to the system's list of software sources.

```bash
echo "deb [signed-by=/etc/apt/keyrings/grafana.gpg] https://apt.grafana.com stable main" | sudo tee -a /etc/apt/sources.list.d/grafana.list
```

### 5. Update the list of available packages.

```bash
sudo apt update
```

### 6. Install either Grafana Open Source or Enterprise.

**Grafana Open Source**

```bash
sudo apt install grafana
```

**Grafana Enterprise**

```bash
sudo apt install grafana-enterprise
```

### 7. After installation, start the Grafana server.

```bash
sudo systemctl start grafana-server
```

### 8. Confirm that the server is running by checking the status.

```bash
sudo systemctl status grafana-server
```

### 9. Optionally configure Grafana to start every time the system boots.

```bash
sudo systemctl enable grafana-server
```

Once Grafana is installed and the server is running, the web interface can be accessed through a web browser. By default, Grafana's web interface listens on port **3000**.

To access the interface, open a web browser and navigate to the IP address or hostname of the server where Grafana is installed, followed by the port number.

```text
http://<Your_Server_IP>:3000
```

If you did this on your local machine, the URL would be:

```text
http://localhost:3000
```
