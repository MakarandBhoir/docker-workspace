# Docker Example 4 – Ephemeral Container Changes (Detached Mode)

## Objective  
Run an NGINX container, modify files inside it, and observe that changes are lost after termination.

## Why  
- Demonstrates that containers are ephemeral by default  
- Helps understand why data persistence is needed  
- Shows how to access and modify running containers  

## What this does  
- Starts an NGINX container in detached mode  
- Accesses the container using interactive shell  
- Modifies the default web page  
- Shows that changes are temporary and lost after container removal  

## Run container in detached mode
```bash
docker run -p 8080:80 -d --name container-example-04 --rm nginx:1.13.0
```

## Access the container shell
```bash
docker exec -it container-example-04 sh
```

## Modify the web page inside container
```bash
cd /usr/share/nginx/html
echo "<h1>Hello World</h1>" > index.html
exit
```

## Access the application
```bash
curl http://localhost:8080
```

## Stop the container
```bash
docker stop container-example-04
```

## Remove the container (if not auto-removed)
```bash
docker rm container-example-04
```

## Additional details  
- Container name: `container-example-04`  
- Port mapping: `8080 (host) → 80 (container)`  
- Changes are temporary and will be lost after container stops  
- `--rm` ensures automatic cleanup  
- Demonstrates need for volumes for persistent storage  
