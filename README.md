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

# Flask Docker Project 

## Overview
This project runs a simple Flask web application inside a Docker container.

## Steps to Run
1. Build the image: `docker build -t flask-app .`
2. Run the container: `docker run -d -p 5000:5000 flask-app`
3. Visit **http://localhost:5000** 

## Technologies Used
- Python & Flask
- Docker
- GitHub

   

**Day 4 : -Docker Compose & Multi-Container Apps**

1. What is Docker Compose?
     Docker Compose is a tool that allows us to define, configure, and run multi-container applications using a single YAML file (docker-compose.yml). It simplifies managing multiple services         with a single command (docker compose up).
   Command:- docker compose -f <.yaml file> up   (This will start all the services mentioned in file)
             docker compose -f <.yaml file> down  (This removes all containers)

     Yaml file should have proper indentation then only it will run.

   2. Dockerizing an application means packaging it into a Docker container, making it portable, scalable, and easy to deploy.
   
  3.  Why Dockerize an Application?
    a. Consistency: Runs the same across different environments (dev, test, production)
    b. Portability: Works on any system with Docker installed 
    c. Isolation: Prevents dependency conflicts between applications
    d. Scalability: Easily deployable in microservices & cloud environments

**Day 5 : Docker Volumes**
  1. What is Docker Volumes?
       Whenever we restart our container all the data in our virtual system gets lost, to overcome this we have docker volumes ensuring files and databases don’t disappear when a container is          removed or restarted.. Docker Volumes are used for persistence of data.

     Commands:
     1. To create volume:  docker volume create <vol_name>
     2. To list the volume : docker volume ls
     3. To delete the volume : docker volume rm <vol_name>
     4. e.g Attach a volume to mysql container
        docker run -d --name <mysql-container> -e MYSQL_ROOT_PASSWORD=rootpass -v mydata:/var/lib/mysql mysql:latest
        mydata is volume name.

    * Volumes can be attached to multiple containers.
      docker run -it -v /Users/data:/test/data ubuntu
        -v is for volume. /Users/data is absolute path of container and /test/data is voulme path.
      * To open docker container:
      docker exec -it <cont_id>

      Default path:
      Windows: C:\ProgramData\docker\volumes
      Mac/Linux: /var/lib/docker/volumes


      * Docker Prune:- It will remove the unused docker resources like images, containers, volumes and networks.
        Command :-1. docker system prune -a   ( removes docker resources)
                  2. docker image prune -a  (removes docker images)
                  3. docker volume prune  (removes docker volumes)
                  
      * Docker Volume Types: 
        1. Named Volumes → Created explicitly for persistent storage
            docker volume create my_named_volume
            
        2. Anonymous Volumes → Created automatically without a name, typically for short-term use 
            docker run -v /data busybox
            
        3.Bind Mounts → Directly maps a host directory to a container
            docker run -v $(pwd)/logs:/var/log/nginx nginx

        *Docker Networking Types:
        
        1.Bridge Network (Default) → Isolates containers while allowing communication within the same bridge.
        2.Host Network → Containers share the host’s network namespace, removing isolation (useful for performance-sensitive apps).
        3.None Network → Completely disables networking for security/isolation.
     
