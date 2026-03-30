# Docker Example 10 – Run Java Application using Dockerfile

## Objective  
Create and run a Java application inside a Docker container.

## Why  
- Demonstrates how to containerize a Java application  
- Ensures consistent runtime with specific JDK version  
- Simplifies execution using interactive mode  

## What this does  
- Uses OpenJDK 17 base image  
- Sets working directory inside container  
- Copies compiled Java classes  
- Runs Java main class interactively  

## Dockerfile
```dockerfile
FROM openjdk:17
WORKDIR /app
COPY bin/com /app/com
CMD [ "java", "com.synergetics.Game" ]
# java com.synergeics.Game
```

## Build image
```bash
sudo docker build -t game:latest .
```

## Run container in interactive mode
```bash
sudo docker run -it game:latest
```

## Additional details  
- Base image: `openjdk:17`  
- Working directory: `/app`  
- Copies compiled classes from `bin/com`  
- Main class: `com.synergetics.Game`  
- Runs in interactive mode (`-it`)  
