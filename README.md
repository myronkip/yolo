# YOLO Full Stack Application Deployment using Vagrant and Ansible

This README outlines the procedures for deploying a containerized full stack YOLO (You Only Look Once) application using Vagrant and Ansible. This project leverages Vagrant for environment management, Docker for containerization, and a YOLO model for object detection tasks.

## Table of Contents

- [Prerequisites](#prerequisites)
- [Installation Steps](#installation-steps)
- [Provisioning Vagrant using Ansible Playbook](#provisioning-vagrant-using-ansible-playbook)
- [Running the Application](#running-the-application)
- [Accessing the Application](#accessing-the-application)
- [Troubleshooting](#troubleshooting)

## Prerequisites

Before you begin, ensure you have the following installed:

- [Vagrant](https://www.vagrantup.com/downloads)
- [VirtualBox](https://www.virtualbox.org/wiki/Downloads)
- [Docker](https://www.docker.com/get-started)
- [Ansible](https://www.ansible.com/resources/get-started)
- [Git](https://git-scm.com/downloads)

## Installation Steps

1. **Clone the Repository**

   First, clone the repository to your local machine:

   ```bash
   git clone https://github.com/myronkip/yolo.git
   git checkout test
   ```

2. **Vagrant Setup**

   Open the `Vagrantfile` and ensure that it is configured correctly. You may need to adjust settings such as the base box and network settings as per your requirements.

   ```ruby
   Vagrant.configure("2") do |config|
     config.vm.box = "ubuntu/focal64"
     config.vm.network "forwarded_port", guest: 8090, host: 8090

     # Ansible provisioner
     config.vm.provision "ansible" do |ansible|
       ansible.playbook = "ansible/playbook.yml"
     end
   end
   ```

3. **Create the Ansible Playbook**

   Create a directory named `ansible` and within that directory, create a file named `playbook.yml`. This playbook will define the tasks to provision your Vagrant VM.


## Provisioning Vagrant using Ansible Playbook

1. **Start the Vagrant Environment**

   Run the following command to start the Vagrant environment and provision it using the Ansible playbook:

   ```bash
   vagrant up --provision
   ```

   This command will create a virtual machine, provision it with Ansible, and install Docker and Docker Compose.

2. **SSH into Vagrant**

   Once the VM is up, SSH into it:

   ```bash
   vagrant ssh
   ```

3. **Navigate to the Project Directory**

   Inside the Vagrant VM, navigate to the project directory:

   ```bash
   cd /opt/yolo
   ```

4. **Build and Run Docker Containers**

   Use Docker Compose to build and run the containers (if the containers are running, skip to running application):

   ```bash
   docker-compose up --build
   ```

   This command will build the backend and frontend services defined in the `docker-compose.yml` file and start them.

## Running the Application

The application consists of a backend service (which handles YOLO model requests) and a frontend service (which provides the user interface). 

1. **Backend Service**: The backend runs on port 5000.
2. **Frontend Service**: The frontend runs on port 8090.

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

---
