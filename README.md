# Dockerize a Three Tier MERN Stack Application

This repository demonstrates how to Dockerize a three-tier MERN (MongoDB, Express.js, React, Node.js) stack application using Docker Compose. The application is hosted on an EC2 instance and exposed using an Elastic IP.

**Frontend:** A React.js application running in a development environment. It listens on port 3000 and automatically reloads changes thanks to volume mounting. It is connected to the backend via the react-express network.

**Backend:** An Express.js server configured for development. It communicates with both the frontend and the MongoDB service through custom bridge networks (react-express and express-mongo). It is also set up to handle dependencies on MongoDB.

**MongoDB:** A MongoDB instance running version 4.2.0, with data persisted using Docker volumes. This service is crucial for storing the application's data and is connected through the express-mongo network.

## Commands to Run :

### 1. Launch AWS EC2 Instance
Create a new EC2 instance and choose **Amazon Linux 2 Kernel 5.10 AMI** and configure the instance type and security groups. Ensure that port 8080 is open for HTTP traffic.Use an existing key pair or create a new one for SSH access.

---
### 2. Install Docker on EC2 Instance
Run the following commands to install and configure Docker
``` bash
# Docker install
sudo yum update -y
sudo amazon-linux-extras install docker
sudo service docker start
sudo usermod -a -G docker ec2-user
pwd

# Docker compose install
sudo curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
```
---

### 3. Clone the Repository
Clone this repository to your EC2 instance:

```bash
git clone https://github.com/your-username/mern-stack-docker.git
cd mern-stack-docker

```
---

### 4.  Build and Run the Application
Run the following commands to build and start the Docker containers:

``` bash
docker-compose up --build -d
```
Run the Docker container, mapping port 80 on the host to port 3000 in the container
   
This will start your Node.js app in the Docker container, accessible via the EC2 instance's public IP.

---

### 5. Attach Elastic IP Address 
Go to the Elastic IPs in the AWS EC2,Allocate a new Elastic IP address.And Associate the Elastic IP with your EC2 instance.After attaching the Elastic IP, your Node.js application will be accessible via the Elastic IP at port 80.

---
