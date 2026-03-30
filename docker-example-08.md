# Docker Example 8 – Container Networking (Custom Bridge Network)

## Objective  
Create a custom Docker network and enable communication between containers.

## Why  
- Demonstrates container-to-container communication  
- Helps understand Docker networking concepts  
- Shows isolation between different networks  

## What this does  
- Creates a custom bridge network with a defined subnet  
- Runs multiple containers inside the same network  
- Verifies communication using container names  
- Demonstrates isolation with containers outside the network  

## Create custom network
```bash
docker network create -d bridge net-n --subnet 13.0.0.0/8
```

## Inspect network
```bash
docker inspect net-n
```

## Run containers in custom network
```bash
docker run -d --name t1 --net net-n nginx:alpine
docker run -d --name t2 --net net-n nginx:alpine
docker run -d --name t3 --net net-n nginx:alpine
docker run -d --name t4 nginx
```

## Test communication inside network
```bash
docker exec -it t1 sh
ping t2
ping t3
exit
```

## Test isolation (container outside network)
```bash
docker exec -it t4 sh
ping t1
# This will fail
exit
```

## Clean up
```bash
docker network inspect net-n
docker stop t1 t2 t3 t4
docker rm t1 t2 t3 t4
docker network rm net-n
```

## Additional details  
- Network type: Bridge  
- Custom subnet: `13.0.0.0/8`  
- Containers in same network can communicate using names  
- Containers outside network cannot access internal containers  
- Demonstrates network isolation and DNS-based service discovery  
