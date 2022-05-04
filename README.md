# Mongo db 4.4

## Requirements
- Docker
- Docker compose

## To run
To run just run the following command in the root of the project
```
docker-compose up -d
```

-d flag to run it in detach mode

## Populate database with a mongo dump folder
To populate mongo db with a mongo dump folder we need to follow the next steps
1. Add mongo dump folder (named as mongo_dump_db) inside the folder `mongo-seed`
2. Edit `mongo-seed/import.sh` and set `mongo-db-name` to match with the desire name of the db. In the next example we named it as `my-test-db`
     ```bash
     #! /bin/bash

     mongorestore -d my-test-db ./mong_dump_db/
     ```
3. Start mongo db using the next command
    ```
    docker-compose up
    ```
we run it in attach session to have a visual output of the status of our mongo

4. Connect to our mongo container instance
  - run the following command to find the name of our running mongo container
    ```
    docker ps
    ```
    you will see some output like the next one
    ```
    a1be8ecad7be   mongo:4.4   "docker-entrypoint.s…"   About an hour ago  Up 22 minutes   0.0.0.0:27017->27017/tcp   mongo4_4_mongodb_1
    ```
    in this case our container name is `mongo4_4_mongodb_1`
  - run next command
    ```
    docker exec -it mongo4_4_mongodb_1 /bin/bash 
    ```
5. Give exec permissions to import.sh script
  - navigate to src path
    ```
    # cd src
    ```
  - run next command
    ```
    # chmod +x import.sh
    ```
6. Run the script
   ```
   # ./import.sh
   ```

