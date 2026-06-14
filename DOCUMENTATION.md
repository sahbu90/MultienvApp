Here's a clean **Markdown (.md) paste-ready version**:

# Multi-Environment Application Deployment Documentation

## 1. Environment Specifications

* **Infrastructure:** AWS EC2 Instance (Ubuntu)
* **Networking:** AWS Security Group configured to allow TCP traffic on ports **3000**, **3001**, and **3002** from `0.0.0.0/0`.
* **Deployment Tool:** Docker Engine v29.1.3 and Docker Compose v2.29.0.

---

## 2. Deployment Process

### Step 1: Clone the Repository

```bash
git clone <your-repository-url>
cd MultienvApp
```

### Step 2: Build and Start Services

Run the following command to build Docker images and start all containers in detached mode:

```bash
sudo docker-compose up -d --build
```

### Step 3: Verify Running Services

Confirm that all services are running successfully:

```bash
sudo docker-compose ps
```

---

## 3. Access URLs

| Service      | URL                                                | Port |
| ------------ | -------------------------------------------------- | ---- |
| Frontend     | [http://13.235.77.9:3000](http://13.235.77.9:3000) | 3000 |
| Dev Backend  | [http://13.235.77.9:3001](http://13.235.77.9:3001) | 3001 |
| Prod Backend | [http://13.235.77.9:3002](http://13.235.77.9:3002) | 3002 |

---

## 4. Testing Evidence

### Docker Container Status

Insert screenshot of:

```bash
sudo docker-compose ps
```

*(Screenshot available in the repository's `screenshots` folder.)*

### Connectivity Test

Insert screenshot of:

```bash
curl -I http://localhost:3000
```

### Browser Access

Insert screenshot showing successful access to:

```text
http://13.235.77.9:3000
```

*(Screenshot available in the repository's `screenshots` folder.)*

---

## 5. Assumptions & Troubleshooting

### Assumptions

* The EC2 instance has the required port access enabled in its AWS Security Group.
* Docker service is running.
* The user executing deployment commands has sufficient permissions.

### Troubleshooting Guide

#### Service Not Starting

Check service logs:

```bash
sudo docker-compose logs <service-name>
```

#### Connection Reset / Unable to Access Service

Verify that the host port in `docker-compose.yml` matches the application's listening port inside the container.

Example:

```yaml
ports:
  - "3000:80"
```

#### Permission Denied

If Docker commands fail due to permissions:

```bash
sudo docker-compose up -d
```

Or refresh Docker group permissions:

```bash
newgrp docker
```

---

## 6. Deployment Summary

The application uses:

* A **multi-stage Docker build** for the React frontend, producing an optimized production image.
* Separate **Flask backend environments** for development and production.
* **Docker Compose** for service orchestration and inter-container networking.

This setup enables consistent deployments, simplified management, and environment isolation while exposing services through dedicated ports.

---

## Notes

Before final submission:

1. Replace `<your-repository-url>` with the actual GitHub repository URL.
2. Replace the IP address if the EC2 Public IPv4 address changes.
3. Ensure all screenshots referenced above are included in the repository or report submission package.

**Deployment Status:** Successfully deployed and accessible through the configured EC2 public endpoints.
