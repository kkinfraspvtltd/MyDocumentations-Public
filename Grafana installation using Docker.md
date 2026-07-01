How to install Grafana using Docker
The steps below will show you how to install and start Grafana using Docker. We will be using Docker for most practical examples throughout the course.
Docker Installation
You will need to have Docker running on your machine. Install Docker by following the relevant instructions for your operating system: https://docs.docker.com/engine/install/.
Using Docker Compose
1. Confirm that Docker Compose is available. If it isn’t, verify your Docker installation.
docker compose version
2. Create a compose file docker-compose.yaml with the following contents:
services:
    	    grafana:
    	        image: grafana/grafana
    		   container_name: grafana
    		   restart: unless-stopped
    		   ports:
              - '3000:3000'
3. Start up the container using the Docker Compose command and view the logs.
docker-compose up -d
docker-compose logs -f
Once the container is running, you can access Grafana from your browser window at http://localhost:3000. It is recommended to use Volumes to persist the Grafana data, but we will do that in subsequent examples.
You can stop the running containers using the docker-compose down command.
Using the Docker CLI
You also have the option of running Grafana directly using a single Docker command. You can provide all the options you would typically do using a compose file, but with command-line flags.
docker run -d -p 3000:3000 --name=grafana grafana/grafana
After this, Grafana will be available on your browser at http://localhost:3000.

After this, Grafana will be available on your browser at http://localhost:3000.
 
