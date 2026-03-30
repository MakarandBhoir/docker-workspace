# Docker Example 9 – Build Node.js App using Dockerfile

## Objective  
Create and run a Node.js application inside a Docker container.

## Why  
- Demonstrates how to containerize a Node.js app  
- Provides consistent runtime environment  
- Simplifies deployment and portability  

## What this does  
- Uses official Node.js base image  
- Sets working directory inside container  
- Copies application files  
- Runs Node.js server  

## Dockerfile
```dockerfile
FROM node:slim
WORKDIR /app
COPY . .
CMD [ "node", "server" ]
#node server.js
```

## Build Docker image
```bash
docker build -t node-app-example .
```

## Run container
```bash
docker run -d --name container-example-09 node-app-example
```

## Stop and remove container
```bash
docker stop container-example-09
docker rm container-example-09
```

## Additional details  
- Base image: `node:slim`  
- Working directory: `/app`  
- Default command runs Node.js server  
- `server` refers to entry file (e.g., server.js)  
