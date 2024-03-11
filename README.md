# Monolithic And Microlithic Service Architecture 

Pending {FLM}

# Docker

- Docker is Open-source containerization platform to create, deploy and run application.

- Docker is written in GO language.

- Docker uses containers on host OS to run applications. It allows applications to use the same Linux kernel as system on the host computer, rather than creating a whole virtual OS.

- We can install Docker on any OS but Docker engines runs only on Linux distribution.

- Docker performs OS level virtualisation also called as containerisation.

- Docker packages software into standard units called as Container that have everything that need to run application, including code, run time, system tools, libraries and dependencies.

- Before docker many user face problems that a particular code is running in the developer system but not in the user system.

- It was initially released in march 2013 and developed by Solomon-Hykes and Sebastian Pahl.

- Docker is set of Platform as a service that use OS level virtualisation, whereas VM ware uses hard-ware level virtualisation.

- The Main advantage of docker methodologies is shipping, testing and deploying code quickly. so, we can eliminate the differences between development and production environments.

- Using docker we will create image for our application.

- Docker images we can share easily to multiple machines

- Using Docker image, we can create docker container and we can run multiple containers using single image.

# Why Docker 

- Let’s assume that we are developing a software project.

- The Collection of programs is called as software project and every Software project contains several components.

	1. Front end components (User interface logic)
		- Angular, React, HTML & CSS, J Query

	2. Backend components (Business logic)
		- Java 1.8v, Spring boot

	3. Database (Persistence login)
		- MySQL DB, Mango DB

- To develop the application, we need to install those dependencies to run our code.

- In order to deploy our application in a machine, we need to setup all the Software. which are required to run our application.

	- Ex: OS, Java 11v, MySQL DB, Tomcat Webserver 9.0v etc..

- In real time, Project should be deployed into multiple env for testing purpose.

    - Ex: DEV, SIT, UAT, PILOT and PROD 

        - Dev env will be used by developers to perform integration testing.

        - SIT (System Integration Testing) env will be used by testing team to test functionality of the application.

        - UAT (User Acceptance Testing) env will be used by Client to test functionality of the application.

        - PILOT env means pre-production testing env.

        - PROD env means live env where public can access the application. (It is used to deliver the project)

- After some time, i need another version of java, react and mango DB for my application to run the code.

- So, its difficult situation to maintain multiple versions of same tool in our system.

### `To overcome this problem, we use Virtualisation`

## Virtualisation | Virtualisation - Architecure :

![image](https://github.com/naveensilver/Docker/assets/120022254/295f0631-3b24-47f2-9a5d-fd388f30a31c)

- Installing multiple Guest OS in one Host OS is called Virtualisation.

- Using Hypervisor, we will create multiple virtual machines in our machine

- In that Virtual Machine, we can host Guest OS in our Machine

- By using Guest OS, we can run multiple Application in same machine.

- It is old technique to run the application.

- System performance will become slow in this process.

### Advantages:

- Multiple OS in same machine.

- Easy Maintenance & Recovery 

- Lower total cost of Ownership

### Dis-Advantages:

- It is old method to run the application.

- If we use multiple VM then the performance of the system is low.

- Long boot-up process (Approx 1 min)

### `To over-come this virtualisation, we use Containerization Concept`

## Containerisation | Containerisation - Architecure :

![image](https://github.com/naveensilver/Docker/assets/120022254/b1c14ca7-27b2-43d6-8b4f-fecab691d59b)

- Instead of installing multiple VM on host OS. we will use Containerisation.

- Containerisation used to pack the application along with dependencies in one container to run application is called Containerization.

- Container is nothing but it is a virtual machine which does not have any OS. 

- Instead of OS, we will use images to create multiple container.

- Docker engine is used to create multiple containers in same machine.

- Container will take care of everything. which is required to run our application.

- Containers are lightweight and We can run multiple containers at a time.

### Advantages Over Virtualisation:

- Containers on same OS kernel are lighter & smaller 

- Better resource utilisation compared to VM 

- Short Boot-up process (1/20th of a second)

### Conclusion 

- Docker is Containerization Software
 	
- Docker will take care of application and application dependencies to run application.

- Deployments into multiple environments will become easy if we use docker containers concept.

# Before Docker & After Docker 

![image](https://github.com/naveensilver/Docker/assets/120022254/d5681b9f-676b-47f2-839e-48770446e83c)
![image](https://github.com/naveensilver/Docker/assets/120022254/1c53922f-ffad-4f61-a586-60cc4987c94a)

# Docker Architecture 

![image](https://github.com/naveensilver/Docker/assets/120022254/c17d27c7-59f1-4e81-ab63-0b1c313a0a99)

The architecture of Docker consists of several components that work together to create a container environment:

1. Docker Client 

2. Docker Host / Docker Daemon / Docker Engine >> Containers & Images, network, volumes

3. Docker Registry / Docker Hub

------------

1.	Docker client: The Docker client is a command-line interface (CLI) tool that allows users to interact with the Docker daemon. The client sends commands to the daemon, which in turn executes them.

2.	Docker Host: It is machine where we installed docker engine/docker

- `Docker daemon:` The Docker daemon is the core component of Docker architecture. Daemon runs on the host operating system and manages all the containers, images, networks, and volumes on the Docker host. Daemon is also called as Docker Engine.

    - `Docker images:` Docker image is a package which contains everything needed to run an application. Which includes App code, Dependencies/Software, Libraries, Env, configuration files.

    - `Docker containers:` Docker containers are the runtime instances of Docker images. They are isolated environments that run the application and its dependencies. Multiple containers can run on the same host, each with its own isolated environment.

    - `Docker networks:` Docker networks are used to connect multiple containers together, enabling communication between them.

    - `Docker volumes:` Docker volumes are used to persist data between container restarts. They are stored outside of the container, allowing data to be shared between containers or to be stored on the host.

3.	Docker registry: Docker registry is a place where we can store and retrieve docker images. which is free and open source. we can download the images and used to create the containers. docker registry is also called as Docker Hub.

There are two types of Registry are available 

- Public - Docker Hub is a public registry. Everybody can store and retrieve images

- Private - Nexus, J frog, AWS ECR (Elastic container registry) are private registries - company specific

Overall, Docker architecture provides a powerful and flexible platform for building, deploying, and managing applications in containers.

### Points To Be Followed in Docker

- You can’t use docker directly, you need to start/restart docker (Observe the docker version before and after restart)

- You need a base image for creating a container.

- You can’t enter directly to a container, you need to start/up container.

![image](https://github.com/naveensilver/Docker/assets/120022254/2cfdd07a-b49e-4d73-a22e-97138bb56692)


[RE-Check] Here

docker info 

docker pull hello-world 

>> docker images

docker run hello-world 

>> hello world image got executed and created a new container.

Q) How This Docker image got executed 
------------------------------------

1. When ever you give docker "docker run, docker pull, docker Build" in CLI. The docker client contacted the docker daemon.

2. Whenever you give " docker pull <hello-world>". docker daemon pull "hello-world" image from docker hub.

3. whenever you give 'docker run <hello-world>' docker daemon created a new container to start our application by using that image.

4. The Container application provides infomation to docker engine, The docker engine/daemon sent the output to docker client in the terminal (CLI)

### Understand the Difference:

Docker Build 

Docker Run

Docker Pull 


Q) Diff b/w Docker Run & Docker Pull 
------------------------------------

## Docker Run: 

- When we give “docker run” command for particular image in Client, The client will connect with Daemon and It will check related image.

    - If the image is available in Daemon, it will return to Client and Execute that image.

    - If the image is not available in Daemon, it will go to Docker Registry, Pull the image from central to Local and Execute that Image.

- When we Run an Image, It will create a default container.

- Docker run used to create image as well as container.

- Syntax : ```docker run [imageNAME]```

- Types of Images : mysql, tomcat, ubuntu...etc

## Docker Pull: 

- When we give “docker pull” command for particular image. it will directly go to Registry/Central and return to data to Client/Local.

- When we Pull an image, it will not create any container.

- Docker pull is used to get image from docker hub.

- Syntax : ``` docker pull [imageName] ```

# Docker File Architecture :


# Image And Containers

