# MultiEnv Ticket Management System

A full-stack application using Flask for both frontend and backend services, demonstrating environment-specific ticket management.

## Project Structure

```
multienv/
├── docker-compose.yml
├── backend/
│   ├── dev/
│   │   ├── app.py
│   │   ├── requirements.txt
│   │   ├── Dockerfile
│   │   └── .env
│   └── prod/
│       ├── app.py
│       ├── requirements.txt
│       ├── Dockerfile
│       └── .env
└── frontend/
    ├── app.py
    ├── requirements.txt
    ├── Dockerfile
    └── .env
```

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

## 📡 Endpoints and Target Ports Network Matrix

| Deployment Profile View | Host Machine Port Access | Internal Container Mapping Target |
| :--- | :--- | :--- |
| **Frontend Portal Engine** | `http://localhost:5000` | Port 80 (Served via Nginx Stack) |
| **Development Environment UI** | `http://localhost:5000/dev` | Routed internally to Backend Dev |
| **Production Environment UI** | `http://localhost:5000/prod` | Routed internally to Backend Prod |

*Engineering Infrastructure Note: The local workstation gateway mapping was successfully configured to host port 5000 to resolve an unexpected system-level WSL loopback allocation block on ports 3001 and 3002, successfully preserving internal microservice network communications.*


## Security Considerations

- Never commit `.env` files to version control
- Use different MongoDB databases for dev and prod
- Implement proper authentication
- Use secure headers


