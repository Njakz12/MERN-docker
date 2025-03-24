# Containerizing a MERN Stack Application and Deploying using Docker Compose

IN this project we would containerize a MERN Stack app and create a network where the containers can communicate and deploy it using docker compose.

Docker Compose is a tool for defining and running multi-container Docker applications using a single configuration file (docker-compose.yml). It simplifies orchestrating interconnected services (like databases, backends, frontends) without manual docker run commands.

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

## 5. Centralized Configuration
Problem: Managing environment variables, volumes, and ports across multiple docker run commands is messy.

Solution: Compose consolidates all configs in one file


