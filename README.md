# AI-Aided Consultant Platform
## 1. Project Overview

AI-Aided Consultant Platform is a web-based application designed to support the consultation process between users and consultants.

The platform allows users to submit cases describing a problem, question, or situation where they need guidance. Instead of relying only on manual analysis, the system uses AI-assisted processing to analyze the submitted case, retrieve relevant knowledge, and generate possible recommendations or draft advice.

The generated suggestions are not intended to replace the consultant. Instead, they are provided as decision-support material. A human consultant reviews the AI-generated output, selects or adapts the most relevant suggestion, or writes a custom response before sending the final advice to the user.

The goal of the platform is to make the consultation process more efficient, structured, and knowledge-driven by combining human expertise with AI-assisted recommendation and retrieval techniques.

## 2. Main Workflow

The platform follows this general workflow:

1. A *user* submits a *case* through the front-end application.
2. The system stores and manages the submitted *case*.
3. AI services analyze the *case* and retrieve relevant information from available references or previous knowledge a.k.a *experience*.
4. The system generates possible *recommendations* or draft advice.
5. A *consultant* reviews the AI-generated suggestions.
6. The *consultant* either selects one of the generated suggestions, modifies it, or writes a custom response.
7. The final advice is sent back to the *user*.

In this workflow, AI acts as an assistant to the consultant. The consultant remains responsible for validating the generated output and providing the final response.

## 3. System Architecture

The AI-Aided Consultant Platform is implemented using a microservices architecture. The system is divided into multiple independent services, where each service is responsible for a specific part of the application.

The front-end application communicates with the backend through an API Gateway. The API Gateway acts as the main entry point for client requests and routes them to the appropriate backend services.

The backend is organized around separate services for authentication, case management, consultant management, AI processing, and embedding-related operations. Each service focuses on its own responsibility and communicates with other services through defined communication contracts, such as APIs or asynchronous messages.

This architecture keeps the system modular because each service represents a separate functional component with a clear responsibility. As a result, services can be developed, tested, maintained, and deployed independently as the project evolves.


## 4. Tech Stack

The platform is built using a combination of backend, frontend, AI, messaging, database, and containerization technologies.

| Area | Technology |
|---|---|
| Backend Services | ASP.NET Core / .NET |
| AI/ML Backend Services | FastAPI / Python |
| Front-End | React |
| API Gateway | ASP.NET Core-based gateway |
| Messaging | RabbitMQ |
| Databases | MongoDB, PostgreSQL with pgvector |
| Containerization | Docker |
| Local Orchestration | Docker Compose |

> **Note:** This table provides only a high-level overview of the technologies used across the platform.  
> For detailed information about the implementation, dependencies, configuration, and setup of each service, refer to the README file inside the corresponding service repository.

## 5. Services Overview

The platform is composed of several services, where each service is responsible for a specific part of the system. This separation keeps the application modular and allows each service to be developed, tested, and maintained independently.

| Service | Responsibility |
|---|---|
| Front-End | Provides the user interface for users and consultants. |
| API Gateway | Acts as the main entry point and reverse proxy for client requests, routing them to the appropriate backend services. |
| Auth Service | Handles authentication, authorization, and user access management. |
| Case Service | Manages case submission, case data, and the case lifecycle. |
| Consultant Service | Manages consultant profiles and consultant-related operations, including selecting the most suitable consultant to process a submitted case. |
| AI Service | Processes submitted cases and generates AI-assisted recommendations or draft advice. |
| Embedding Service | Generates and manages embeddings used for retrieval and similarity-based search. |

> **Note:** Each service is maintained in its own repository. For detailed setup instructions, implementation details, dependencies, and API documentation, refer to the README file of the corresponding service repository.

## 6. Repository Strategy

This project follows a multirepo structure. Each main component of the platform is maintained in its own GitHub repository.

This repository acts as the central entry point for the complete system. It does not contain the full source code of every service. Instead, it provides the system-level documentation and orchestration needed to understand, configure, and run the platform as a whole.

Using a multirepo structure allows each service to have its own codebase, Git history, and development lifecycle. This makes the services easier to maintain independently while keeping clear boundaries between different parts of the system.

At the same time, because the services must work together as one application, this repository provides a common place for:

- the overall project documentation
- the local Docker Compose configuration
- links to all service repositories
- the expected workspace structure
- setup and run instructions for the complete system

## 7. Service Repositories

| Component | Repository |
|---|---|
| Front-End | https://github.com/mhammadnoor13/Front-End |
| API Gateway | https://github.com/mhammadnoor13/APIGateway |
| Auth Service | https://github.com/mhammadnoor13/Auth-Service |
| Case Service | https://github.com/mhammadnoor13/Case-Service |
| Consultant Service | https://github.com/mhammadnoor13/Consultant-Service |
| AI Service | https://github.com/mhammadnoor13/AI-Service |
| Embedding Service | https://github.com/mhammadnoor13/Embedding-Service |

## 8. Local Development Setup

To run the complete platform locally, all service repositories should be cloned inside the same workspace folder.

The recommended local structure is:

```text
AI-Aided-Consultant-Platform/
├── ai-aided-consultant-platform/     # main repository: documentation and orchestration
├── Front-End/
├── APIGateway/
├── Auth-Service/
├── Case-Service/
├── Consultant-Service/
├── AI-Service/
└── Embedding-Service/
```

The ai-aided-consultant-platform repository contains the Docker Compose configuration used to run the full system locally. The other directories contain the source code of the individual services.

Clone the main repository first: 

``` bash
git clone https://github.com/mhammadnoor13/AI-Aided-Consultant-Platform.git
```

Then clone each service repository inside the same workspace folder:

``` bash

git clone https://github.com/mhammadnoor13/Front-End.git
git clone https://github.com/mhammadnoor13/APIGateway.git
git clone https://github.com/mhammadnoor13/Auth-Service.git
git clone https://github.com/mhammadnoor13/Case-Service.git
git clone https://github.com/mhammadnoor13/Consultant-Service.git
git clone https://github.com/mhammadnoor13/AI-Service.git
git clone https://github.com/mhammadnoor13/Embedding-Service.git

```

After cloning all repositories, move into the main repository:

``` bash
cd Ai-Aided-Consultant-Platform
```

Build and start all services using Docker Compose:

``` bash
docker compose up --build -d
```

Check that the containers are running:
``` bash
docker compose ps
```

View logs for all services:

``` bash
docker compose logs -f
``` 

View logs for a specific service:

``` bash
docker compose logs -f <service-name>
```

Stop all running containers:
``` bash
docker compose down
```

## 9. Local Service URLs

After starting the system with Docker Compose, the services can be accessed locally using the following URLs:

| Component | URL |
|---|---|
| Front-End | http://localhost:3000 |
| API Gateway | http://localhost:5100 |
| Case Service | http://localhost:5010 |
| Consultant Service | http://localhost:5020 |
| Auth Service | http://localhost:5030 |
| AI Service | http://localhost:5040 |
| Embedding Service | http://localhost:5050 |

The API Gateway should be used as the main entry point for backend requests. Direct service URLs are mainly useful for development, testing, and debugging.

---

Happy coding! 🚀

