Grafana Installation 

How to install Grafana on Linux Debian or Ubuntu

The steps below will show you how to install and start Grafana on any Linux Debian or Ubuntu machine. This could be your laptop or a cloud server. Feel free to skip to the relevant instruction text for your needs. We will be using Docker for most practical examples throughout the course.

The recommended method for installing Grafana on Debian is by leveraging the official Grafana Apt repository. You can do so using the following steps:

1. Ensure that the package lists are up-to-date.

sudo apt update

2. Install prerequisite packages that are required for using HTTPS repositories and GPG keys.

sudo apt-get install -y apt-transport-https software-properties-common wget

3. Next, add the Grafana GPG key to the system's list of trusted keys.

sudo mkdir -p /etc/apt/keyrings/
wget -q -O - https://apt.grafana.com/gpg.key | gpg --dearmor | sudo tee /etc/apt/keyrings/grafana.gpg > /dev/null

4. Add the official Grafana APT repository to the system's list of software sources.

echo "deb [signed-by=/etc/apt/keyrings/grafana.gpg] https://apt.grafana.com stable main" | sudo tee -a /etc/apt/sources.list.d/grafana.list

5. Update the list of available packages.

sudo apt update

6. Install either Grafana Open Source or Enterprise.

sudo apt install grafana
sudo apt install grafana-enterprise

 7. After installation, you can start the Grafana server.

sudo systemctl start grafana-server

 8. Confirm that the server is running by checking the status.

sudo systemctl status grafana-server

9. Optionally configure Grafana to start every time the system boots.

sudo systemctl enable grafana-server

Once Grafana is installed and the server is running, the web interface can be accessed through a web browser. By default, Grafana's web interface listens on port 3000. To access the interface, open a web browser and navigate to the IP address or hostname of the server where Grafana is installed, followed by the port number. The format for the URL is http://<Your_Server_IP>:3000.

If you did this on your local machine, the URL would be http://localhost:3000.
