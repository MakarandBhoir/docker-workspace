# Docker Example 7 – Volume Mount (Bind Mount)

## Objective  
Mount a local directory into a container to serve static content using NGINX.

## Why  
- Demonstrates data persistence outside container  
- Allows real-time updates without rebuilding images  
- Useful for development and testing static content  

## What this does  
- Creates a local directory with an HTML file  
- Mounts it into the NGINX container  
- Serves content directly from host machine  
- Uses read-only (`:ro`) mount for safety  

## Run on Docker Desktop (Windows)

```bash
d:
mkdir demo
cd demo
notepad index.html
docker run -p 8080:80 -d --name container-example-07 -v d:\demo:/usr/share/nginx/html:ro nginx:1.13.0
```

## Access the application
```bash
curl http://localhost:8080
```

## Stop and remove container
```bash
docker stop container-example-07
docker rm container-example-07
```

## Run on Docker Playground / Linux

```bash
mkdir demo
cd demo
touch index.html
# Edit index.html and add HTML content
docker run -p 8080:80 -d --name container-example-07 -v /root/demo:/usr/share/nginx/html:ro nginx:1.13.0
```

## Access the application
```bash
curl http://localhost:8080
```

## Stop and remove container
```bash
docker stop container-example-07
docker rm container-example-07
```

## Additional details  
- Volume type: Bind mount  
- Host path (Windows): `d:\demo`  
- Host path (Linux): `/root/demo`  
- Container path: `/usr/share/nginx/html`  
- `:ro` makes mount read-only  
- Changes in host files reflect instantly in container  
