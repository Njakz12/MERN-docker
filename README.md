# Containerizing a MERN Stack Application and Deploying using Docker Compose

IN this project we would containerize a MERN Stack app and create a network where the containers can communicate and deploy it using docker compose.

In my main branch i deployed the MERN stack application using docker containers. 

A MERN stack application is a full-stack JavaScript web application built using four key technologies:

MongoDB – A NoSQL database for storing data in flexible, JSON-like documents.

Express.js – A backend framework for Node.js that simplifies API and server development.

React – A frontend library for building dynamic, interactive user interfaces.

Node.js – A JavaScript runtime that executes server-side code.

How It Works
Frontend (React): Handles the UI and user interactions.

Backend (Node.js + Express.js): Manages API requests, business logic, and database operations.

Database (MongoDB): Stores and retrieves application data.



### Why Use Docker Compose Over Individual Containers for MERN Stack?
## 1. Simplified Multi-Container Management
Running separate docker run commands for each service (Frontend, Backend, DB) is tedious and error-prone. Docker Compose defines all services in a single docker-compose.yml file.

## 2. Automated Networking
Manually creating networks and linking containers is complex. Compose auto-creates a network for all services, enabling seamless communication by service name (e.g., backend can connect to mongodb via mongodb:27017).

## 3. Dependency Management
Problem: Starting containers in the correct order (e.g., MongoDB before backend) requires manual scripting.
Solution: Compose handles dependencies with depends_on

## 4. Single-Command Workflow
Start all services	```docker-compose up -d```	 Multiple docker run commands
Stop all services	```docker-compose down``` 	Manually stop/rm each container
View logs	```docker-compose logs -f```	Check logs per container
Rebuild images	```docker-compose up --build```	Rebuild/restart each container
 


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


## Using Docker Compose

```docker compose up -d```

