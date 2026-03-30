# Docker Example 3 – Run NGINX Container (Attached Mode or Terminal Mode)

## Objective  
Run an NGINX container in terminal mode and observe live logs while accessing it.

## Why  
- Demonstrates running containers in foreground (interactive mode)  
- Helps understand real-time log streaming  
- Useful for debugging and monitoring container behavior  

## What this does  
- Starts an NGINX container in terminal mode  
- Maps host port 8080 to container port 80  
- Streams logs directly in the terminal  
- Automatically removes container on stop using `--rm`  

## Run container in terminal mode
```bash
docker run -p 8080:80 -t --name container-example-03 --rm nginx:1.13.0
```

## Access the application
```bash
curl http://localhost:8080
```

## Verify logs  
- Logs will be displayed directly in the terminal in real time  

## Open another terminal to stop the container
```bash
docker stop container-example-03
```

## Remove the container (if not auto-removed)
```bash
docker rm container-example-03
```

## Additional details  
- Container name: `container-example-03`  
- Port mapping: `8080 (host) → 80 (container)`  
- Logs are streamed live in terminal  
- Container is automatically deleted after stop because of `--rm`  
- Terminal remains attached to the container process  
