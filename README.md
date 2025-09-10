# Docker - Softy Pinko Project

## Description
This project introduces **Docker** and containerization by building a complete application infrastructure that includes:
- A reverse proxy
- A load balancer
- Two back-end API servers
- One front-end server

Through progressive tasks, you will learn how to build Docker images, run containers, connect services together, and use Docker Compose to manage multiple services.

---

## Learning Objectives
By the end of this project, you should be able to explain (without Google):
- What Docker is and why it is used
- How to build and run a Docker image
- The difference between images, containers, and services
- How to set up a back-end using Flask inside Docker
- How to set up a front-end with Nginx
- How to connect front-end and back-end containers
- How to configure a proxy server
- How to scale horizontally using multiple containers
- How to use Docker Compose to orchestrate multi-container applications

---

## Requirements
- Docker Desktop installed on your local computer (Linux, Mac, or Windows)
- All Dockerfiles must be based on the **latest ubuntu** or **latest nginx**
- Each task is placed in its own directory (`task0`, `task1`, …)
- A mandatory `README.md` file at the root of the project
- Each container must run properly and be accessible at the required port
- Code must be clean and structured

---

## Tasks

### 0. Create Your First Docker Image
- Create a Dockerfile that:
  - Uses `ubuntu:latest`
  - Runs `apt-get update` and `apt-get upgrade -y`
  - When executed, the container must print: `Hello, World!`

### 1. Back-end
- Copy `task0` to `task1`
- Install `python3`, `pip3`, and `flask`
- Add a simple Flask API (`api.py`) with endpoint `/api/hello` returning `Hello, World!`
- Container must listen on **port 5252**

### 2. Front-end
- Copy `task1` to `task2`
- Create two folders: `back-end` and `front-end`
- Use the provided **softy-pinko-front-end** code
- Build a front-end Docker image using **nginx**
- Serve files on **port 9000**

### 3. Connecting Front-end and Back-end
- Copy `task2` to `task3`
- Update the front-end to fetch data from `/api/hello`
- Add **flask-cors** to back-end
- Confirm that front-end displays dynamic data from the back-end

### 4. Making it Simpler with Docker Compose
- Copy `task3` to `task4`
- Create a `docker-compose.yml` file to run both front-end and back-end with one command
- Use `docker-compose build` and `docker-compose up`

### 5. Proxy Server
- Copy `task4` to `task5`
- Add a new `proxy` service using **nginx**
- Proxy server must:
  - Route `/` → front-end service
  - Route `/api` → back-end service
- Front-end JS code updated to fetch `/api/hello` through the proxy

### 6. Scale Horizontally
- Copy `task5` to `task6`
- Run **two or more back-end servers**
- Proxy must load-balance requests between them using **Round Robin**
- Create a file `2-api-servers.txt` containing the exact `docker-compose` command used to scale the API

---

## Usage

### Build and Run a Task
```bash
# Example for task1 (Back-end)
cd task1
docker build -t softy-pinko:task1 .
docker run -p 5252:5252 -it softy-pinko:task1
```

### Run with Docker Compose (task4+)
```bash
cd task4
docker-compose build
docker-compose up
```

### Scale Back-end Servers (task6)
```bash
docker-compose up --scale back-end=2
```

---

## Project Structure
```
holbertonschool-softy-pinko-docker/
│── task0/
│── task1/
│── task2/
│── task3/
│── task4/
│── task5/
│── task6/
│── README.md
```

---

## Author
Project by **Holberton School**
Part of the **Web Back-End Specialization**
