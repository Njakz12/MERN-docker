# Containerizing a MERN Stack Application and Deploying using Docker Containers

IN this project we would containerize a MERN Stack app and create a network where the containers can communicate 

A MERN stack application is a full-stack JavaScript web application built using four key technologies:

MongoDB – A NoSQL database for storing data in flexible, JSON-like documents.

Express.js – A backend framework for Node.js that simplifies API and server development.

React – A frontend library for building dynamic, interactive user interfaces.

Node.js – A JavaScript runtime that executes server-side code.

How It Works
Frontend (React): Handles the UI and user interactions.

Backend (Node.js + Express.js): Manages API requests, business logic, and database operations.

Database (MongoDB): Stores and retrieves application data.



### Create a network for the docker containers

Creating a custom network for Docker containers offers several advantages in terms of communication, security, and manageability.

```docker network create demo```

Verify if the network was created 

```docker network ls```

### Build the frontend 
Firstly install the latest version of npm. An older version of npm was used for this project. npm (Node Package Manager) is the default package manager for Node.js, used to install, manage, and share JavaScript libraries/tools.
```sudo apt install npm```
Afterwards run this below
```cd mern/frontend
docker build -t mern-frontend .
```

### Run the frontend

```docker run --name=frontend --network=demo -d -p 5173:5173 mern-frontend```

### Verify if the frontend is running
Ensure port 5173 is open in the security group settings
Open your browser and type `http://localhost:5173`

### Run the mongodb container
Since we would be running Mongodb as a container we have to pull it first before running it 
```docker pull mongo```
```docker run --name my-mongodb --network=demo -d -p 27017:27017 -v ~/opt/data:/data/db mongo:latest```

### Verify if the db is running
Ensure port 27017 is open in the security group settings
Open your browser and type `http://localhost:27017`

### Build the backend

```
cd mern/backend
docker build -t mern-backend .
```

### Run the backend server

```docker run --name=backend --network=demo -d -p 5050:5050 mern-backend```

### Verify if the server is running
Ensure port 5050 is open in the security group settings
Open your browser and type `http://localhost:5050`


## Switch to my compose branch to see a better way for running a MERN stack application



