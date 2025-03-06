<b>Task_1 PostgreSQL</b>

Pre-build image of PostgreSQL can be downloaded from docker hub by executing following command: 
```
docker pull postges:latest
```

Documentation for PostgreSQL image can be found on the following link https://hub.docker.com/_/postgres. 
 
To persist some future data in the database the docker volume needs to be created
```
docker volume create postgres-data
```

The PostgreSQL image uses several environment variables. The only required variable is POSTGRES_PASSWORD.
The following command can be executed to create a PostgreSQL container:
# -e is used for environment variables
# -p is used for port mapping
# -v is used for volume mapping
# --name <custom_name_of_the_container>

```
 docker run -d --name postgres-db -e POSTGRES_USER=test -e POSTGRES_PASSWORD=test -e POSTGRES_DB=main_db -p 5432:5432 -v postgres_data:/var/lib/postgresql/data postgres:latest 
```

 To check the status of containers:
```
docker ps -a
```
 ![alt text](images/image.png)

Terminal connection to container via psql:
```
docker exec -it postgres-db psql -d main_db -U test </i> # -it interactive terminal, -d database name, -U username
```

 The containerized postgres-db is listening on 0.0.0.0:5432<

![alt text](images/image-2.png)

Simple test can be done via pgAdmin.

Incoming packets to the server(to the containerized postgres) can be dumped by executing the following command:
```
tcpdump -nli any port 5432 
```
The test ran successfully.

![alt text](images/image-6.png)

![alt text](images/image-5.png)

I designed a SQL querie to create a table and then I executed it in pgAdmin.

```
CREATE TABLE users ( 
    username varchar(255) PRIMARY KEY,
     password_hash varchar(72) NOT NULL, 
     email varchar(255) NOT NULL, 
     status varchar(255) NOT NULL
);
```
To list all the tables in the current schema:
```
docker exec -it postgres-db psql -d main_db -U test -c "\dt" I got:
```

![alt text](images/image1.png)
</br>