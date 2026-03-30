# Docker Example 1 – Run NGINX Container (Detached Mode)

## Objective  
Run an NGINX container in detached mode and access it via browser or curl.

## Why  
- Demonstrates how to run containers in background  
- Shows container running and logging capabilities  
- Introduces basic lifecycle commands (run, logs, stop)

## What this does  
- Starts an NGINX container on 80 port inside the container  
- Runs in background using `-d`  
- Auto-removes container on stop using `--rm`

## Run container in detached mode
```bash
docker run -d --name container-example-01 --rm nginx:latest
```

## Access the application
```bash
curl http://localhost:80
```

## Check container logs
```bash
docker logs container-example-01
```

## List running containers
```bash
docker ps
```

## Stop the container
```bash
docker stop container-example-01
```

## Additional details  
- Container name: `container-example-01`  
- Container is automatically deleted after stop because of `--rm`  
- Detached mode allows terminal to remain free
