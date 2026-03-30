# Docker Example 11 – Deploy WAR File on Tomcat

## Objective  
Deploy a Java web application (WAR file) on a Tomcat server using Docker.

## Why  
- Demonstrates containerizing Java web applications  
- Simplifies deployment of WAR files  
- Uses lightweight Tomcat image for faster startup  

## What this does  
- Uses Tomcat 9 with JDK 8 slim image  
- Removes default web applications  
- Deploys custom WAR file as ROOT application  
- Exposes port 8080 for web access  

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

## Run container
```bash
docker run -d -p 8080:8080 --name container-example-11 tomcat-game-app
```

## Access the application
```bash
curl http://localhost:8080
```

## Stop and remove container
```bash
docker stop container-example-11
docker rm container-example-11
```

## Additional details  
- Base image: `tomcat:9-jdk8-slim`  
- Port exposed: `8080`  
- WAR file deployed as ROOT application  
- Removes default Tomcat apps for clean deployment  
- Suitable for Java web applications (Servlet/JSP)  
