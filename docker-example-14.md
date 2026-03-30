# Docker Example 14 – Push Image to Docker Hub

## Objective  
Build a Docker image and push it to Docker Hub for sharing and reuse.

## Why  
- Enables sharing images across teams and environments  
- Allows deployment from any system  
- Centralized image repository  

## What this does  
- Builds a Tomcat-based image  
- Tags the image with Docker Hub username  
- Pushes the image to Docker Hub  

## Dockerfile
```dockerfile
FROM tomcat:9-jdk8-slim
EXPOSE 8080
WORKDIR "/usr/local/tomcat/"
RUN rm -r webapps/*
ADD web-game.war webapps/ROOT.war
```

## Build Docker image
```bash
docker build -t tomcat-game-app .
```

## Tag image for Docker Hub
```bash
docker tag tomcat-game-app <your-dockerhub-username>/tomcat-game-app:latest
```

## Login to Docker Hub
```bash
docker login
```

## Push image to Docker Hub
```bash
docker push <your-dockerhub-username>/tomcat-game-app:latest
```

## Verify image
```bash
docker images
```

## Pull and run from Docker Hub
```bash
docker run -d -p 8080:8080 --name container-example-14 <your-dockerhub-username>/tomcat-game-app:latest
```

## Access the application
```bash
curl http://localhost:8080
```

## Stop and remove container
```bash
docker stop container-example-14
docker rm container-example-14
```

## Additional details  
- Replace `<your-dockerhub-username>` with your Docker Hub username  
- Image is stored in remote repository  
- Can be pulled from any machine with Docker installed  
- Useful for CI/CD pipelines and deployments  
