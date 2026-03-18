# tanishq-selfie-app-dockerized
Dockerized Spring Boot (WAR) application with MySQL using Docker Compose, demonstrating containerization, environment-based configuration, and service communication.
# 🚀 Tanishq Selfie App - Dockerized Spring Boot System

A production-style backend system built using **Spring Boot (WAR)**, containerized with **Docker**, and connected to a **MySQL container** using Docker Compose.

---

## 🧠 Project Overview

This project demonstrates how to:

* Containerize a Spring Boot WAR application
* Connect services using Docker networking
* Externalize configuration using environment variables
* Simulate a real-world backend deployment setup

---

## 🏗️ Architecture

```
User → Browser → Spring Boot App (Docker) → MySQL (Docker)
```

---

## ⚙️ Tech Stack

* Java 11
* Spring Boot (WAR)
* Docker
* Docker Compose
* MySQL 8

---

## 📂 Project Structure

```
tanishq_selfie_app/
├── target/
│   └── *.war
├── Dockerfile
├── docker-compose.yml
└── application.properties
```

---

## 🐳 Docker Setup

### Dockerfile

```
FROM eclipse-temurin:11-jdk
WORKDIR /app
COPY target/*.war app.war
CMD ["java", "-jar", "app.war"]
```

---

### docker-compose.yml

```
version: '3.8'

services:
  app:
    build: .
    ports:
      - "3000:3000"
    environment:
      - SPRING_PROFILES_ACTIVE=local
      - DB_URL=jdbc:mysql://mysql-container:3306/Tanishq
      - DB_USERNAME=root
      - DB_PASSWORD=admin
    depends_on:
      - mysql-container

  mysql-container:
    image: mysql:8
    environment:
      - MYSQL_ROOT_PASSWORD=admin
      - MYSQL_DATABASE=Tanishq
    ports:
      - "3306:3306"
```

---

## ▶️ Run the Project

```
docker-compose down -v
docker-compose up --build
```

---

## 🌐 Access

👉 http://localhost:3000

---

## 🧠 Key Learnings

* Docker container networking
* Environment-based configuration
* Running WAR inside Docker
* Debugging real-world deployment issues

---

## ⚠️ Challenges Solved

* Fixed Dockerfile detection issue
* Solved MySQL connection inside container
* Handled environment-specific configuration
* Reduced rebuild dependency

---

## 🚀 Future Enhancements

* CI/CD (GitHub Actions)
* Nginx reverse proxy
* AWS deployment
* Kubernetes

---

## 👨‍💻 Author

Abhishek Singh
