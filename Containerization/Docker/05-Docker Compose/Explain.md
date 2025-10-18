# Explain

## Microservices

> Microservices = an architecture style where each part of the app is built as a small, independent service.
> 

### Instead of one big app (monolith), you split your app into:

- **Frontend** (e.g., React or Nginx)
- **Backend APIs** (e.g., Node.js, Django)
- **Database** (e.g., MySQL, PostgreSQL)
- **Auth Service**, **Payment Service**, etc.

Each microservice:

- Runs on its **own container**
- Can be developed, updated, and scaled **independently**
- Communicates with others via **HTTP or internal Docker network**

## Docker compose

**Docker Compose** is a tool that lets you define and manage **multi-container Docker applications** using a **YAML** file.

- We use it to automate running the containers with all its services like networks and volumes  in one YAML file
- Each container starts with the name of application
- Containers can communicate with each others by name of service
- When the file is down → all containers will be stopped and deleted with all its services except the volume