```markdown
# Multi-Environment Application Deployment Documentation

## 1. Environment Specifications
* **Infrastructure:** AWS EC2 Instance (Ubuntu)
* **Networking:** AWS Security Group configured to allow TCP traffic on ports 3000, 3001, and 3002 from 0.0.0.0/0.
* **Deployment Tool:** Docker Engine v29.1.3 and Docker Compose v2.29.0.

## 2. Deployment Process
### Step-by-Step Instructions
1. **Clone the Repository:**
   ```bash
   git clone <your-repository-url>
   cd MultienvApp

```

2. **Build and Start Services:**
Run the following command to build the Docker images and start the containers in detached mode:
```bash
sudo docker-compose up -d --build

```


3. **Verification:**
Confirm all services are running:
```bash
sudo docker-compose ps

```



## 3. Access URLs

| Service | URL | Port |
| --- | --- | --- |
| **Frontend** | `http://13.235.77.9:3000` | 3000 |
| **Dev Backend** | `http://13.235.77.9:3001` | 3001 |
| **Prod Backend** | `http://13.235.77.9:3002` | 3002 |

## 4. Testing Evidence

* **Docker Container Status:**
(Insert screenshot of `sudo docker-compose ps`) (can find inside in repo screenshots folder)
* **Connectivity Test:**
(Insert screenshot of `curl -I http://localhost:3000`)
* **Browser Access:**
(Insert screenshot of browser viewing `http://13.235.77.9:3000`) (can find in repo screenshots folder)

## 5. Assumptions & Troubleshooting

### Assumptions

* The EC2 instance has port access enabled in the AWS Security Group.
* The Docker service is active and the user has sufficient permissions.

### Troubleshooting Guide

* **Service Not Starting:** Check logs using `sudo docker-compose logs <service-name>`.
* **Connection Reset:** Ensure the host port in `docker-compose.yml` matches the container's internal listening port (e.g., Frontend mapped 3000:80).
* **Permission Denied:** If Docker commands fail, use `sudo` or run `newgrp docker` to refresh session group permissions.

## 6. Deployment Summary

The application utilizes a multi-stage build process for the React frontend to ensure an optimized production image, and independent Flask environments for development and production backend services. All services are orchestrated via Docker Compose for streamlined inter-service communication.

```

***

**Pro-tip:** Before saving, make sure to replace `<your-repository-url>` with your actual GitHub link and `[EC2_PUBLIC_IP]` with your instance's real Public IPv4 address. Good luck with your VIVA!

```
