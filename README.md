# YOLO Full Stack Application Deployment using Vagrant

This README outlines the procedures for deploying a containerized full stack YOLO application using Vagrant. This project leverages Vagrant for environment management, Docker for containerization, and a YOLO model for object detection tasks.

## Table of Contents

- [Prerequisites](#prerequisites)
- [Installation Steps](#installation-steps)
- [Running the Application](#running-the-application)
- [Accessing the Application](#accessing-the-application)
- [Troubleshooting](#troubleshooting)

## Prerequisites

Before you begin, ensure you have the following installed:

- [Vagrant](https://www.vagrantup.com/downloads)
- [VirtualBox](https://www.virtualbox.org/wiki/Downloads)
- [Docker](https://www.docker.com/get-started)
- [Git](https://git-scm.com/downloads)


## Installation Steps

1. **Clone the Repository**

   First, clone the repository to your local machine:

   ```bash
   git clone https://github.com/myronkip/yolo.git
   checkout branch name test
   ```

2. **Vagrant Setup**

   Open the `Vagrantfile` and ensure that it is configured correctly. You may need to adjust settings such as the base box and network settings as per your requirements.

   ```ruby
   Vagrant.configure("2") do |config|
     config.vm.box = "ubuntu/focal64
     config.vm.network "forwarded_port", guest: 8090, host: 8090
   end
   ```

3. **Start the Vagrant Environment**

   Run the following command to start the Vagrant environment:

   ```bash
   vagrant up
   ```

   This command will create a virtual machine and provision it with Docker.

4. **SSH into Vagrant**

   Once the VM is up, SSH into it:

   ```bash
   vagrant ssh
   ```

5. **Navigate to the Project Directory**

   Inside the Vagrant VM, navigate to the project directory:

   ```bash
   cd /opt/yolo
   ```

6. **Build and Run Docker Containers**

   Use Docker Compose to build and run the containers:(if the containers are running,skip to running application)

   ```bash
   docker-compose up --build
   ```

   This command will build the backend and frontend services defined in the `docker-compose.yml` file and start them.

## Running the Application

The application consists of a backend service (which handles YOLO model requests) and a frontend service (which provides the user interface). 

1. **Backend Service**: The backend runs on port 5000.
2. **Frontend Service**: The frontend runs on port 8090 (or any port configured in the `docker-compose.yml`).

## Accessing the Application

Once the containers are up and running, you can access the application by opening your web browser and navigating to:

- Frontend: [http://localhost:8090](http://localhost:8090)
- Backend: [http://localhost:5000](http://localhost:5000)

## Troubleshooting

- If you encounter any issues during the deployment, check the logs of the Docker containers for error messages:

  ```bash
  docker-compose logs
  ```

- Ensure that Docker and VirtualBox are correctly installed and running on your machine.



