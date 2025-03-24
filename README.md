# Containerizing a MERN Stack Application and Deploying using Docker Compose

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

```docker network create demo```

### Build the client 

```sh
cd mern/frontend
docker build -t mern-frontend .
```

### Run the client

```docker run --name=frontend --network=demo -d -p 5173:5173 mern-frontend```

### Verify the client is running

Open your browser and type `http://localhost:5173`

### Run the mongodb container

```docker run --network=demo --name mongodb -d -p 27017:27017 -v ~/opt/data:/data/db mongodb:latest```

### Build the server

```sh
cd mern/backend
docker build -t mern-backend .
```

### Run the server

```docker run --name=backend --network=demo -d -p 5050:5050 mern-backend```

## Using Docker Compose

```docker compose up -d```

