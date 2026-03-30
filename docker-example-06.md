# Docker Example 6 – Copy Files to Running Container

## Objective  
Copy files from host machine to a running container and create a new image with those changes.

## Why  
- Demonstrates how to transfer files into a container  
- Useful for quick updates without rebuilding images  
- Helps understand container-to-image workflow  

## What this does  
- Runs an NGINX container  
- Copies a local file into the container  
- Commits the container as a new image  
- Runs a new container using updated image  

## Run container
```bash
docker run --name container-example-06 -d -p 8080:80 nginx:alpine
```

## Copy file into container
```bash
docker cp index.html container-example-06:/usr/share/nginx/html/index.html
```

## Stop container
```bash
docker stop container-example-06
```

## Create new image from container
```bash
docker commit container-example-06 app1
```

## Remove container
```bash
docker rm container-example-06
```

## Test the new image
```bash
docker run -d -p 8080:80 --name container-example-06-test app1
```

## Access the application
```bash
curl http://localhost:8080
```

## Stop and remove test container
```bash
docker stop container-example-06-test
docker rm container-example-06-test
```

## Additional details  
- Base image: `nginx:alpine`  
- New image name: `app1`  
- File copied: `index.html`  
- Demonstrates `docker cp` and `docker commit` workflow  
- Changes persist only in new image, not original container  
