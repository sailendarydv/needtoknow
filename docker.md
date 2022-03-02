# Commands

## Containers
- view running containers
    ```
        docker ps
    ```

- view all containers
    ```
        docker ps -a
    ```

- view all containers ids
    ```
        docker ps -a -q
    ```

- view all running containers ids
    ```
        docker ps -q
    ```

- remove a stopped specific container
    ```
        docker rm <container_id>
    ```

- stop a running specific container
    ```
        docker stop <container_id>
    ```  

- stop all running specific container
    ```
        docker stop $(docker ps -q)
    ```  

- pause all running specific container
    ```
        docker pause $(docker ps -q)
    ```  

- unpause/restart all paused specific container
    ```
        docker pause|restart $(docker ps -q)
    ```  

- start all stopped specific container
    ```
        docker start $(docker ps -q)
    ``` 

- filter on containers
    ```
        docker ps -a -f "status=<status>" | docker ps -a -q -f "<status>=0"
    ``` 

## Images
- view all images
    ```
        docker images
    ```

- remove a specific image
    ```
        docker rmi <image_id>
    ``` 

- remove multiple images
    ```
        docker rmi $(docker images -q)
    ``` 

## Running a container

- Running a container command in detached mode [-d] or interactive mode [-it]
    ```
        docker run --name <container_name> -d -p <host_port>:<container_port> <image_name>:<version> -U <username>
    ```
    - example:
        - running a container in detached with specific version of postgres with a defined username password and port mapping
            ```
                docker run --name postgres10.20.v2 -d -e  POSTGRES_PASSWORD=1234567890 -p 5432:5432 postgres:10.20   
            ```
        - running a rabbitmq with username and password/port mapped/hostname
            ```
                docker run --name rabbitmq3.8.v1 -d -h rammitmq-users -e RABBITMQ_DEFAULT_USER=guest -e RABBITMQ_DEFAULT_PASS=guest -p 5672:5672 -p 15672:15672 rabbitmq:3.8
            ```
        - running mongodb
            ```
                docker run --name mongodb.v1 -d -p 27017:27017 mongo:3.2-jessie
            ```

## View Container Logs
```
    docker logs <container_name>
```

## Postgres
- ssh into running postgres container 
    ```
        psql -h locahost -U postgres -W
    ```
- show tables
    ```
        \l
    ```
- get out of the show tables
    ```
        w or q
    ```
- connect to one of the database
    ```
        \c <database_name>
    ```
- describe tables in a database
    ```
        \dt
    ```
- view all commands 
    ```
        \?
    ```
- quit psql 
    ```
        \q
    ```