# Docker/AWS
**Day 1: Docker installed and first container run/pull and hands-on prcatice**

**What is Docker?**
  ->Docker is a platform which helps to create containers.
    Docker -> Containers + Images
    * Image :- A docker image is a executable file which contains set of instructions to build containers. (Blueprint of a container)
   * Container :- It is a single packaged unit of our application/code + its dependencies ( software components required by application like library,packages, utilities,etc).
  
 **Properties :**
  1. Portable
  2. Light-weight

2. **Docker Commands  :**
     1.  docker -v                    (To check docker version)
     2.  docker login -u <username>  (and then it will ask a one-time password)  
     3.  docker logout
     4.  docker pull <image-name>       e.g docker pull hello-world       (To create image)
     5.  docker images     (To check all docker images present )
     6.  docker run <image-name>         (This will create docker container)
     7.  docker ps -a       (This will display all docker containers with their status)
     8.  docker run -it <image-name>     (in interactive mode)
     9.  docker start <container-name> or <container-id>    ( This will restart the container)
     10. docker stop <container-name> or <container-id>    ( This will stop the container)
     11. docker rmi <image-name>      (To delete docker image)
     12. docker rm <container-name>    (To delete docker container. First container needs to be deleted then only image)
  

  ##  Day 2 – Building My First Docker Image & Core Concepts

****Tasks Completed
- Created a custom Dockerfile and built my first image
- Ran the container and understood container lifecycle
- Practiced key commands: `docker build`, `run`, `images`, `ps -a`
- Explored Docker architecture: versioning, layers, port binding
- Compared Docker vs Virtual Machines (tiffin box vs portable kitchen)

**Learnings**
- Docker builds images using layered caching (faster rebuilds!)
- Port binding lets containers talk to the outside world
- Containers are lighter and faster than traditional VMs
- Dockerfiles give total control over packaging your app

**Docker Commands  :**
  1. docker logs <container-id>
  2. docker exec -it <container-id> /bin/bash
  3.  docker exec -it <container-id> /bin/sh   (This helps to run additional commands in existing container)
  4.  docker network ls  ( To list docker networks present)
  5.  docker network create <network-name>  ( To create a own docker network)
  6.  docker run -d -p 8080:80 <image-name>
       p 8080:80   (port binding)
       80 is the container port
      8080 is the host port


    ##  Day 3 – Docker Networking & Container Communication

    **Tasks Completed**
    1. Created network in docker
    2. Created and connected multiple containers
    3. Tested container-to-container communication

    **Docker Commands  :**
    1. docker network create my-network          (Created "my-network" network)
    2. docker -d --name busy-network --network my-network busybox sleep 3600      (created "busy-container" container on "my-network" network")
    3. docker -d --name alpine-network --network my-network alpine sleep 3600      (created "alpine-container" container on "my-network" network")
    4. docker exec -it busy-conatiner sh      (enter busy-container)
    5. ping alpine-container       (test was succesful)
    6. docker network inspect my-network      (container connections, IP address and network details)

    

    
   
