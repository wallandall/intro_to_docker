# Docker Networking
One of the reasons Docker containers and services are so powerful is that you can connect them together, or connect them to non-Docker workloads. Docker containers and services do not even need to be aware that they are deployed on Docker, or whether their peers are also Docker workloads or not. Whether your Docker hosts run Linux, Windows, or a mix of the two, you can use Docker to manage them in a platform-agnostic way.


There are three components that make up Docker Networking:
1. Container Network Model(CNM) defines the fundamental building blocks of a Docker Network:
   1. Sandbox: Isolates the network stack and includes network inerfaces, ports, rout tables and DNS
   2. Endpoint: Virtual network interfaces which connects the sandbox to the network
   3. Networks
2. The libnetwork impplementation
3. Driver extended model by network topology

## Network Drivers
Docker’s networking subsystem is pluggable, using drivers. Several drivers exist by default, and provide core networking functionality:

- bridge: The default network driver. If you don’t specify a driver, this is the type of network you are creating. Bridge networks are usually used when your applications run in standalone containers that need to communicate
- host: For standalone containers, remove network isolation between the container and the Docker host, and use the host’s networking directly.
- overlay: Overlay networks connect multiple Docker daemons together and enable swarm services to communicate with each other. You can also use overlay networks to facilitate communication between a swarm service and a standalone container, or between two standalone containers on different Docker daemons. This strategy removes the need to do OS-level routing between these containers. 
- ipvlan: IPvlan networks give users total control over both IPv4 and IPv6 addressing. The VLAN driver builds on top of that in giving operators complete control of layer 2 VLAN tagging and even IPvlan L3 routing for users interested in underlay network integration.
- macvlan: Macvlan networks allow you to assign a MAC address to a container, making it appear as a physical device on your network. The Docker daemon routes traffic to containers by their MAC addresses. Using the macvlan driver is sometimes the best choice when dealing with legacy applications that expect to be directly connected to the physical network, rather than routed through the Docker host’s network stack.
- none: For this container, disable all networking. Usually used in conjunction with a custom network driver. none is not available for swarm services.
- Network plugins: You can install and use third-party network plugins with Docker. These plugins are available from Docker Hub or from third-party vendors.

## Networking Commands
- To list all network commands: 
  - ```docker network -h```
- List all docker networks:
  - ```docker network ls```
- Inspect a docker network :
  - ```docker network inspect network_name```
- To create a network run:
  - ```docker network create network_name```
- To delete a network run:
  - ```docker network rm network_name```
  - ___Do not delete dfault networks___
- To delete al unused networks run:
  - ```docker network prune```
- To add a container to a network run:
  - ```docker network connect network_name container_name```
- To remove a container from a network run:
  - ```docker network disconnect network_name container_name```

[back](ReadMe.md)
