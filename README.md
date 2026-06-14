# MultiEnv Ticket Management System

A full-stack application using Flask for both frontend and backend services, demonstrating environment-specific ticket management deployed via Docker.

## Project Structure

```text
MultienvApp/
├── backend/
│   ├── dev/
│   │   ├── Dockerfile, app.py, requirements.txt, .env
│   └── prod/
│       ├── Dockerfile, app.py, requirements.txt, .env
├── frontend/
│   ├── Dockerfile, package.json, (src/ folders)
├── evidence/              <-- Create this folder
│   ├── status.png
│   ├── connectivity.png
│   └── browser.png
├── submission/            <-- Create this folder
│   └── submission-info.txt
├── docker-compose.yml
├── DOCUMENTATION.md       <-- Copy-pasted from above
└── README.md              <-- A brief version of DOCUMENTATION.md
## Environment Configuration

### Backend Development Environment (.env)
```
PORT=3001
MONGO_URI=your_dev_mongodb_uri
```

### Backend Production Environment (.env)
```
PORT=3002
MONGO_URI=your_prod_mongodb_uri
```



### Requirements
```
flask==2.0.1
flask-cors==3.0.10
python-dotenv==0.19.0
pymongo==3.12.0
requests==2.26.0
```



### Using Docker Compose
```bash
docker-compose up
```

## Accessing the Application

- Frontend: http://localhost:3000/
- Development Environment: http://localhost:3001/dev
- Production Environment: http://localhost:3002/prod



## Security Considerations

- Never commit `.env` files to version control
- Use different MongoDB databases for dev and prod
- Implement proper authentication
- Use secure headers


