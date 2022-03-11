# Docker Networking Demo
The below describes how to create a solution with twom containers , one for the front end application and one for the database. To improve security this solution will implement two networks, public network and a private network that is not publicly accessible. The frontend (Nginx)  will be connected to the public network and the databadse (MySQL) will be connected to the private network

1. Create a bridge network called frontend:
   1. ```docker network create frontend```
2. Create a bridge network called localhost. This network will be internal so you neet to use the internal flag
   1. ````docker network create network localhost --internal```
3. Create the MySQL container that will use the localhost network. We will also use thefollowing options:
   1.  ```-d ``` option to run the container in the background.
   2.  ```-name``` to assign a name of database to our container 
   3.  ```--network ```to a add the container to the local network
   4.  ```-e MYSQL_ROOT_PASSWORD = ``` to assign a password to the MY_SQL_ROOT_PASSWORD environment variable
   5. ```docker containe run -d --name database --network localhost -e MYSQL_ROOT_PASSWORD=password123 mysql:latest```
4. Create an Nginx container with the following options:
   1. ```-d```to run in detached mode
   2. ```--name``` to assign frontend-app as the name 
   3. ```--network``` frontend to add the container to the frontend network
   4. ```docker container run -d --name frontend-app --network frontend nginx:latest```
5. To confirm containers are running run:
   1. ```docker container ls```
6. If you run docker ```docker network connect localhost frontend-app``` you will connect the frontend-app container to both networks which will allow the Nginx server to be accessible to the internet but the MySQL server only accessible on the local network. You can verify this by running ```docker container inspect frontend-app```


[back](ReadMe.md)