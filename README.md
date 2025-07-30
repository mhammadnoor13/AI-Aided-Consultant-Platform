# Project Overview

This project is structured as a set of microservices, a gateway service, and a front‑end application, each maintained in its own GitHub repository. We use Docker Compose (version 3.9) to build and run all components together, including infrastructure services (RabbitMQ and MongoDB).

## Directory Layout

```
project-root/
├── Back-End/
│   ├── Services/
│   │   ├── AuthService            # file with Git clone URL for AuthService
│   │   ├── CaseService            # file with Git clone URL for CaseService
│   │   ├── ConsultantService      # file with Git clone URL for ConsultantService
│   │   ├── AI-Service             # file with Git clone URL for AI-Service
│   │   └── Embedding-Service      # file with Git clone URL for Embedding-Service
│   └── Gateway                   # file with Git clone URL for Gateway service
├── Front-End/                    # directory containing front‑end code and Dockerfile
└── docker-compose.yml           # Docker Compose configuration (includes RabbitMQ & MongoDB)
```

## Prerequisites

- Git (on your PATH)
- Docker Engine
- Docker Compose (v3.9 syntax supported)

> Tested on Windows 10/11, Linux, and macOS.

---

## Setup & Run Instructions

1. **Clone the root repository**:
   ```bash
   git clone https://github.com/your-org/project-root.git
   cd project-root
   ```

2. **Prepare Back-End repositories**:

   Navigate into the `Back-End` folder:
   ```bash
   cd Back-End
   ```

   **Clone microservices**:

   - **Linux/macOS**:
     ```bash
     cd Services
     for file in *; do
       url=$(cat "$file")
       git clone "$url" "$file"
     done
     ```

   - **Windows PowerShell**:
     ```powershell
     cd Services
     Get-ChildItem -File | ForEach-Object {
       git clone (Get-Content $_.FullName) $_.BaseName
     }
     ```

   **Clone the Gateway service**:
   ```bash
   cd ../Gateway
   url=$(cat Gateway)
   git clone "$url" Gateway
   ```

   After this, you should have directories `Services/` and `Gateway/` populated with code.

3. **Return to project root**:
   ```bash
   cd ../../
   ```

4. **Build and start all services** (including RabbitMQ & MongoDB):
   ```bash
   docker-compose build
   docker-compose up -d
   ```

5. **Verify** that containers are healthy and running:
   ```bash
   docker-compose ps
   ```

6. **Access the services** at URLs and ports defined in `docker-compose.yml`:
   - Front‑end: http://localhost:3000
   - Gateway:   http://localhost:5100
   - Case API:  http://localhost:5010
   - Consultant API: http://localhost:5020
   - Auth API:  http://localhost:5030
   - AI Service: http://localhost:5040
   - Embedding Service: http://localhost:5050

---

## Troubleshooting

- **Port conflicts**: Check `docker-compose.yml` for port mappings; adjust if needed.
- **Build errors**: Ensure each service directory has the correct branch or tag; run `git pull` inside the service directory.
- **Logs**: Follow logs with:
  ```bash
  docker-compose logs -f <service_name>
  ```

---

Happy coding! 🚀

