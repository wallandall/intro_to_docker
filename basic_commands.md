# Basic Commands

To run Docker Commands from the CLI you use the ```docker ``` command. You can run ```docker -h | more``` to get a list of all Docker Commands. This will display the Docker Options, Docker Management Commands and Docker Commands that can be run from the CLI

## Docker Image
- List Images: 
  - ```docker image ls```
- Pull an image from a repository:
  - ```docker image pull image_name```
- Push an image to a registry:
  - ```docker image push```
- To get low level information of a docker image use the inspect command:
  - ```docker image inspect image_id```
  

## Docker Container
- List contianers:
  - ```docker container ls```
- To display detailed information about a container:
  - ```docker container inspect container_id```
- To display the running processes in a container run:
  - ```docker conatiner top container_id```
- To start/stop a container run:
  - ```docker container start container_id```
  - ```docker container stop container_id```
- To attach local standard input , output and error streams to a running container run:
  - ```docker container attach container_id```
- To remove all stoped contianers:
  - ```docker container prune container_id```
- To fetch logs from a container run:
  - ```docker container logs container_id```
- To run commands inside a container run:
  - ```docker container exec -it container_id /bin/bash```
    - exec lets ou run commands in the containe
    - -it lets you run commands in interactive mode
    - /bin/bash runs the bash command
    - Type exit to exit the container
  - To remove a container run:
    - ```docker container rm container_id```
    - if you run rm on a running container use the -f flag to force the removal
  

##  Docker run reference
Docker runs processes in isolated containers. A container is a process which runs on a host. The host may be local or remote. When an operator executes docker run, the container process that runs is isolated in that it has its own file system, its own networking, and its own isolated process tree separate from the host.

The basic docker run command takes this form:

``` docker run [OPTIONS] IMAGE[:TAG|@DIGEST] [COMMAND] [ARG...]```

With the docker run [OPTIONS] an operator can add to or override the image defaults set by a developer. And, additionally, operators can override nearly all the defaults set by the Docker runtime itself. The operator’s ability to override image and Docker runtime defaults is why ___run___ has more options than any other docker command.
- To get a list of option available to __docker run__ you can use the follow flag
  - ```docker run --help```
- To run a container :
  - ```docker run container_name```
- To automatically remove a docker image after execution run:
  - ```docker run --rm container_name```
- To run the container in the background and print the container id:
  - ```docker container run -d container_name```
- For interactive processes (like a shell), you must use -i -t together in order to allocate a tty for the container process. -i -t is often written -it 
  - -i Keeps STDIN open even if not attached
  - -t allocates a pseudo TTY
  - ```docker container run -it container_name```
- To assign a name to a containe use the -name option
  - ```docker run --name name_you_want_to_assign container_name```


