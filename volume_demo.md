# Creating a Volume
In this example we will be creating be creating a volume to persistently store MySQL database files.
1. Create a new volume called mysql_data:
   1. ```docker volume create mysql_data```
2. Create a MySQL container:
   1. ```docker container create run -d --name app-database --mount type=volume, source=mysql_data, target=/var/lib/mysql -e MYSQL_ROOT_PASSWORD=testpassword mysql:latest```
   2. ```-d``` runs the container in detached mode
   3. ```-nname``` assignes a name to the container, in this example app_database
   4. ```--mount``` specifies the ___type___ which is volume and the name of the ___volume___ to mount
   5. ```-e``` sets the password for the ___MYSQ_ROOT_PASSWORD___ environment variable , this is the root password that will be initialised for MySQL
3. Confirm everything is working correctly by running ```docker container inspect app-database```