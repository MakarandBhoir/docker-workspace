# Docker Example 5 – Create Custom Image using Docker Commit

## Objective  
Create a new Docker image by modifying a running container and saving the changes.

## Why  
- Demonstrates how to create custom images quickly  
- Helps understand Docker image layering  
- Useful for quick experiments without writing a Dockerfile  

## What this does  
- Runs an NGINX container  
- Modifies the default web page inside container  
- Saves the container as a new image using `docker commit`  
- Removes the original container  

## Run container
```bash
docker run -d --name container-example-05 nginx:1.13.0
```

## Access the container shell
```bash
docker exec -it container-example-05 bash
```

## Modify the web page
```bash
cd /usr/share/nginx/html
echo "<h1>Hello World</h1>" > index.html
exit
```

## Create new image from container
```bash
docker commit container-example-05 testapp
```

## Stop and remove container
```bash
docker stop container-example-05
docker rm container-example-05
```

## Test the new image
```bash
docker run -d --name container-example-05-test -p 8080:80 testapp
```

## Additional details  
- New image name: `testapp`  
- Changes are saved as a new image layer  
- Based on existing image: `nginx:1.13.0`  
- Demonstrates image layering concept  
- Not recommended for production; use Dockerfile instead  
