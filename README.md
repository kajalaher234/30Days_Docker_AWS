# AWS
**Day 1: Docker installed and first container run/pull and hands-on prcatice**

**What is Docker?**
  ->Docker is a platform which helps to create containers.
    Docker -> Containers + Images
    * Image :- A docker image is a executable file which contains set of instructions to build containers. (Blueprint of a container)
   * Container :- It is a single packaged unit of our application/code + its dependencies ( software components required by application like library,packages, utilities,etc).
  
 **Properties :**
  1. Portable
  2. Light-weight

2. **Docker Commands:**
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
