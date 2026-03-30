# Docker Example 12 – MySQL Image with Preloaded Schema and Data

## Objective  
Build a MySQL Docker image with preloaded database schema and data.

## Why  
- Automates database setup  
- Ensures consistent schema and seed data  
- Useful for development and testing environments  

## What this does  
- Creates a SQL file with schema and data  
- Uses MySQL base image  
- Initializes database during container startup  
- Loads data automatically  

## Create SQL file
```sql
CREATE TABLE employees
( empid int primary key auto_increment,
firstname nvarchar(20),
lastname nvarchar(30));

INSERT into employees (firstname, lastname)
VALUES ('Donald','Duck');

INSERT into employees (firstname, lastname)
VALUES ('Micky','Mouse');
```

## Create Dockerfile
```dockerfile
FROM mysql:5.7

ENV MYSQL_DATABASE=mydata MYSQL_USER=makarand MYSQL_PASSWORD=pass@1234 MYSQL_ROOT_PASSWORD=pass@12345 

ADD mydata.sql /docker-entrypoint-initdb.d/
```

## Build Docker image
```bash
docker build -t mydata .
```

## Run container
```bash
docker run --name db1 -d mydata
```

## View logs
```bash
docker logs db1
```

## Access MySQL inside container
```bash
docker exec -it db1 bash
mysql -u makarand -p pass@1234
```

## Run SQL queries
```sql
use mydata;
show tables;
select * from employees;
exit
```

## Stop and remove container
```bash
docker stop db1
docker rm db1
```

## Additional details  
- Base image: `mysql:5.7`  
- Database name: `mydata`  
- Data initialized using `/docker-entrypoint-initdb.d/`  
- SQL runs only on first container startup  
