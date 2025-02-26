
To install and configure Dependency Track using Docker and Docker Compose with persistent storage using volumes, follow the guide below. This setup includes a backend API server and a frontend service, and utilizes Docker volumes for data persistence.

## 1. Ensure Docker and Docker Compose are Installed
Before proceeding, make sure you have Docker and Docker Compose installed on your machine. You can follow these official guides to install them:

- Docker 
  
- Docker Compose

## 2. Clone the Repository
First, clone the repository to your local machine:

- git clone https://github.com/jkiala2/Dependency_Track.git

2. Navigate to the Docker Directory

Change to the Docker directory where the docker-compose.yml file is located:

- cd Dependency_Track/Docker

## 4. Review the docker-compose.yml File

Before proceeding with the deployment, it’s good to open and review the docker-compose.yml file to ensure it suits your needs (such as verifying ports, IP addresses, and configurations). You can open it with a text editor:

- nano docker-compose.yml

Make any necessary adjustments, such as updating the IP address of your machine or any environment variables that you need to change.

## 5. Start the Docker Containers

Once you're ready, run the following command to start the containers in detached mode:

docker-compose up -d

This command will:

Download the necessary Docker images for Dependency Track.

Start the containers as defined in the docker-compose.yml file.

6. Check if the Containers are Running

To confirm that the containers are up and running, you can use:

docker-compose ps

This will show you the list of running containers, including dtrack-apiserver and dtrack-frontend.

## 7. Access Dependency Track UI

After the containers are running, you can access the Dependency Track frontend UI in your browser. If you're using the default configuration, navigate to:

- http://yourIP:8080

Replace <yourIP> with your server’s IP address.

## 8. Login to Dependency Track

Username: admin

Password: admin

After logging in for the first time, you will be prompted to change the password for security.

## 9. Stopping the Containers

To stop the services, run the following command:

- docker-compose down

This will stop the containers and remove the network created by Docker Compose, but it will retain the volume for persistent data.

## 10. Viewing Logs

To view logs from the running containers, use:

- docker-compose logs -f

This will display logs for both the API server and frontend service.
