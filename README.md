# Dockerize a Three Tier MERN Stack Application

This project demonstrates how to containerize a full Three-Tier MERN (MongoDB, Express, React, Node.js) stack application using Docker Compose.Docker Compose is a tool for defining and running multi-container Docker applications. The setup includes three primary services (Docker Images).

**Frontend:** A React.js application running in a development environment. It listens on port 3000 and automatically reloads changes thanks to volume mounting. It is connected to the backend via the react-express network.

**Backend:** An Express.js server configured for development. It communicates with both the frontend and the MongoDB service through custom bridge networks (react-express and express-mongo). It is also set up to handle dependencies on MongoDB.

**MongoDB:** A MongoDB instance running version 4.2.0, with data persisted using Docker volumes. This service is crucial for storing the application's data and is connected through the express-mongo network.

## Commands to Run :

1.Build and run the application
    
    docker compose up -d

2.Listing containers must show containers running and the port mapping as below

![image](https://github.com/user-attachments/assets/20c57aff-d84b-445c-88a9-e74692865118)

3.Access the Application

    http://localhost:3000/

4.Stop and Remove Container

    docker-compose down

## Expected Result :

![image](https://github.com/user-attachments/assets/7703a5e0-e26e-4fae-bd4b-252e7b3274aa)
