# Docker Example 13 – ENTRYPOINT and CMD

## Objective  
Understand how ENTRYPOINT and CMD work together in a Dockerfile.

## Why  
- Demonstrates default command behavior  
- Shows how arguments can override CMD  
- Helps design flexible container execution  

## What this does  
- Uses BusyBox image  
- Sets `ping` as ENTRYPOINT  
- Provides default argument using CMD  
- Allows overriding target host at runtime  

## Create Dockerfile
```dockerfile
FROM busybox:latest
ENTRYPOINT [ "ping" ]
CMD ["google.com"]
```

## Build Docker image
```bash
docker build -t test1 .
```

## Run container (default behavior)
```bash
docker run -it test1
```

## Stop execution
```bash
CTRL+C
```

## Override default argument
```bash
docker run -it test1 yahoo.com
```

## Stop execution
```bash
CTRL+C
```

## Additional details  
- ENTRYPOINT defines the main command (`ping`)  
- CMD provides default argument (`google.com`)  
- Passing argument overrides CMD but not ENTRYPOINT  
- Useful for creating flexible CLI-like containers  
