# Docker Storage 
Storage in Docker can be classified as 
- Non Persistent Data
  - This is ephemeral data, if is deleted it is not an issue
  - Every container has non persistent data which is linked to the container, when the container is deleted the data is deleted.
- Persistant Data
  - This is data that is not ephemeral, it is stored permanently
  - Persistant data is not linked to the container lifecycle so if the container is deleted the data is not deleted.
  - Docker uses Volumes for persistant data which is stored outside of the container
  - On Linux systems storage is located under ```var/lib/docker/<Storage-Driver>```
  - On Windows systems storage is located under ```c:\ProgramData\Docker\windowsfilter\```
  - The version of the Operating system defines which storage driver docker will use 
    - RHEL uses overlay2
    - Ubuntu uses overlay2 or aufs
    - SUSE uses btrf
    - Windows has its own driver
  
## Volume Commands
- To list all volumes on the host:
  - ```docker volume ls```
- To create a volume:
  - ```docker volume create volume_name```
- To inspect a volume run:
  - ```docker volume inspect volume_name``` 
- To delete a volume run:
  - ```docker volume rm volume_name```
- To remove all unised volumes run:
  - ```docker volume prune```



[back](ReadMe.md)