# What is Monolithic And Microlithic Service Architecture ?

![image](https://github.com/naveensilver/Docker/assets/120022254/07428a02-98df-4185-a6da-56e2eb875d68)

## Monolithic 

- If the application contains N number of services.

    - Ex: Paytm has Money Transaction, Movie ticket, Train Ticket.. etc 

- If all the services are included in one server then it will be called as Monolithic Architecture.

- Every Monolithic has only one database for all the services.

## Micro-Service 

- If the application contains N number of services.

    - Ex: Paytm has Money Transaction, Movie ticket, Train Ticket.. etc

- If every service has its own individual servers then it is called Microservices.

- Every Micro service architecture has its own database for each service.

# Introduction to Docker

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

![Screenshot (105)](https://github.com/naveensilver/Docker/assets/120022254/7cacb8e2-c5c4-4800-bc58-25a2906899d3)

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

- `Containerisation` used to pack the application along with dependencies in one container to run application is called Containerization.

- `Container` is nothing but it is a virtual machine which does not have any OS. 

- Instead of OS, we will use images to create multiple container.

- Docker engine is used to create multiple containers in same machine.

- Container will take care of everything. which is required to run our application.

- Containers are lightweight and We can run multiple containers at a time.

### Advantages Over Virtualisation:

- Containers on same OS kernel are lighter & smaller 

- Better resource utilisation compared to VM 

- Short Boot-up process (1/20th of a second)


## Containers vs Virtual Machine [Containerisation vs Virtualisation]

Containers and virtual machines are both technologies used to isolate applications and their dependencies, but they have some key differences:

    1. Resource Utilization: Containers share the host operating system kernel, making them lighter and faster than VMs. VMs have a full-fledged OS and hypervisor, making them more resource-intensive.

    2. Portability: Containers are designed to be portable and can run on any system with a compatible host operating system. VMs are less portable as they need a compatible hypervisor to run.

    3. Security: VMs provide a higher level of security as each VM has its own operating system and can be isolated from the host and other VMs. Containers provide less isolation, as they share the host operating system.
    
    4.  Management: Managing containers is typically easier than managing VMs, as containers are designed to be lightweight and fast-moving.


## Why are containers light weight ?

Containers are lightweight because they use a technology called containerization, which allows them to share the host operating system's kernel and libraries, while still providing isolation for the application and its dependencies. This results in a smaller footprint compared to traditional virtual machines, as the containers do not need to include a full operating system. Additionally, Docker containers are designed to be minimal, only including what is necessary for the application to run, further reducing their size.

Let's try to understand this with an example:

Below is the screenshot of official ubuntu base image which you can use for your container. It's just ~ 22 MB, isn't it very small ? on a contrary if you look at official ubuntu VM image it will be close to ~ 2.3 GB. So the container base image is almost 100 times less than VM image.

![Screenshot 2023-02-08 at 3 12 38 PM](https://user-images.githubusercontent.com/43399466/217493284-85411ae0-b283-4475-9729-6b082e35fc7d.png)


To provide a better picture of files and folders that containers base images have and files and folders that containers use from host operating system (not 100 percent accurate -> varies from base image to base image). Refer below.



### Files and Folders in containers base images

```
    /bin: contains binary executable files, such as the ls, cp, and ps commands.

    /sbin: contains system binary executable files, such as the init and shutdown commands.

    /etc: contains configuration files for various system services.

    /lib: contains library files that are used by the binary executables.

    /usr: contains user-related files and utilities, such as applications, libraries, and documentation.

    /var: contains variable data, such as log files, spool files, and temporary files.

    /root: is the home directory of the root user.
```



### Files and Folders that containers use from host operating system

```
    The host's file system: Docker containers can access the host file system using bind mounts, which allow the container to read and write files in the host file system.

    Networking stack: The host's networking stack is used to provide network connectivity to the container. Docker containers can be connected to the host's network directly or through a virtual network.

    System calls: The host's kernel handles system calls from the container, which is how the container accesses the host's resources, such as CPU, memory, and I/O.

    Namespaces: Docker containers use Linux namespaces to create isolated environments for the container's processes. Namespaces provide isolation for resources such as the file system, process ID, and network.

    Control groups (cgroups): Docker containers use cgroups to limit and control the amount of resources, such as CPU, memory, and I/O, that a container can access.
    
```

It's important to note that while a container uses resources from the host operating system, it is still isolated from the host and other containers, so changes to the container do not affect the host or other containers.

**Note:** There are multiple ways to reduce your VM image size as well, but I am just talking about the default for easy comparision and understanding.

so, in a nutshell, container base images are typically smaller compared to VM images because they are designed to be minimalist and only contain the necessary components for running a specific application or service. VMs, on the other hand, emulate an entire operating system, including all its libraries, utilities, and system files, resulting in a much larger size. 

I hope it is now very clear why containers are light weight in nature.

### Conclusion 

- Docker is Containerization Software
 	
- Docker will take care of application and application dependencies to run application.

- Deployments into multiple environments will become easy if we use docker containers concept.

# Before Docker & After Docker 

![image](https://github.com/naveensilver/Docker/assets/120022254/d5681b9f-676b-47f2-839e-48770446e83c)
![image](https://github.com/naveensilver/Docker/assets/120022254/1c53922f-ffad-4f61-a586-60cc4987c94a)

# Docker

## What is Docker ?

Docker is a containerization platform that provides easy way to containerize your applications, which means, using Docker you can build container images, run the images to create containers and also push these containers to container regestries such as DockerHub, Quay.io and so on.

In simple words, you can understand as `containerization is a concept or technology` and `Docker Implements Containerization`.

# Docker Complete Architecture 

![image](https://github.com/naveensilver/Docker/assets/120022254/8c27fbeb-8271-4328-b5e4-d0b7840f5860)

## Docker Architecture ?

![image](https://user-images.githubusercontent.com/43399466/217507877-212d3a60-143a-4a1d-ab79-4bb615cb4622.png)

The above picture, clearly indicates that Docker Deamon is brain of Docker. If Docker Deamon is killed, stops working for some reasons, Docker is brain dead :p (sarcasm intended).

### Understanding the terminology

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

# Install Docker in Amazon-Linux

To install Docker on Amazon Linux, you can follow these steps:

1. Connect to your Amazon Linux instance using SSH.

2. Update the package manager to ensure that you have the latest version of the package list:
```
sudo yum update -y
```
3. Install the Docker package and its dependencies:
```
sudo yum install docker -y
```
4. To check docker version 
```
sudo docker version 
```
5. Start the Docker service:
```
sudo service docker start
```
(OR)
```
sudo systemctl start docker
```
6. Add your user to the docker group to be able to run Docker commands without using sudo:
```
sudo usermod -aG docker ec2-user
```
Note: Replace ec2-user with your username.

7. Verify that Docker is running by running the following command:
```
sudo systemctl status docker 
```
8. To stop the docker service
```
sudo systemctl stop docker
```
9. To get Docker Info

```
sudo docker info 
```

That's it! You have now successfully installed Docker on Amazon Linux. You can now start using Docker to build, run, and manage containers

-----------------------------------

Note: If you use MobaXterm to install docker  

After adding user to group `$ sudo usermod -aG docker ec2-user`

Run command `$ exit` #Exit from the session 

Then press 'R' to restart the session (MobaXterm)

Q) Execute Hello-World Image (Or) Create image and Container using Docker Commands:
------------------------------------------------------------------------------------

- Check the docker info `$ docker info`

- Now Pull the image `$ docker pull <ImageName>` i.e., `$ docker pull hello-world`

    - Here, docker pull is used to pull/download images from Docker-Hub
    - hello-world is the default image stored in Docker-Hub

- To see list of docker images `$ docker images `

- To run docker image `$ docker run <image-id/name>` i.e., `$ docker run hello-world `

> hello world image got executed and created a new container.

- check the list of containers `$ docker ps`

Q) How This Docker image got executed 
------------------------------------

1. When ever you give docker "docker run, docker pull, docker Build" in CLI. The docker client contacted the docker daemon.

2. Whenever you give " docker pull <hello-world>". docker daemon pull "hello-world" image from docker hub.

3. whenever you give 'docker run <hello-world>' docker daemon created a new container to start our application by using that image.

4. The Container application provides infomation to docker engine, The docker engine/daemon sent the output to docker client in the terminal (CLI)

# Docker File Architecture | Docker Architecture:

![Screenshot (103)](https://github.com/naveensilver/Docker/assets/120022254/9abd688c-6ed9-41ed-bd88-a21cb932ecc1)

There are three important things,

1. docker build -> builds docker images from Dockerfile
2. docker run   -> runs container from docker images
3. docker push  -> push the container image to public/private regestries to share the docker images.

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

## Docker Build [Pending]


# Image And Containers



# Docker Commands

docker -v 

docker info # To see docker info

docker help 

docker login # To Connect Docker Hub Account 

docker images  # To see list of docker images

docker ps # To See List of Container

docker pull <image-id> #download the docker image from docker-hub

docker run <image-id> 

docker push <image-id> # To store the image in Docker Hub

docker build # used to build the image from docker file

docker tag #Image Versions

docker rmi <image-id>

- To Check Images List : `$ docker images`

- To Check Container list : `$ docker ps -a`

- To pull the image from Docker hub : `docker pull <imageName>`

- To Create image as well as Container : `docker run <ImageName>`

- To Start container :  `docker start <container_ID/ContainerName>`

- To Delete stopped container (few) : `docker rm <container_ID/ContainerName> `
- To Delete all the stopped/Exited containers (Multiple) : `docker container prune`

Note : we can't remove running containers 

- To Remove Image : $ docker rmi <ImageName>

# Docker Image Commands:

# Docker Container Commands

Q) How to create a Image from Container?

```
docker commit <contName> <imageName>
```

Q) How to copy Data/Files from one Container to Multiple Containers

- Create container using Nginx image 

```
    docker run -it --name cont1 Nginx
```

- Enter into cont1, add some files inside cont1 and exit from cont1

```
    docker exec -it cont1 /bin/bash  
    touch file{1..5}
    exit
```
- Now check the container list 

```
    docker ps -a
```
- Now Create image1 from cont1
```
    docker commit cont1 image1
```
Image ID got generated Ex: sha6874676761697

- Check image list
```
docker images
```
Here, you can see the "image1"

If you create containers from this image1. You will get all the image1 files inside container.

Note: We can share the data from container to multiple containers by using image.


Q) How To Change Container Port Number

- First Stop that Container 

```
    docker stop <contName>
```
- Go To Docker default Directory Path
```
    cd /var/lib/docker/
```
- Go to container directory (you can see the container ID’s)

```
    cd containers/
```
- Go to suitable container ID 

```
    cd h54fdasdfae68df6vvbthehenbscfrt6ryh64846fv
```
- Open host config file
```
    vim hostconfig.json 
```

- Change the Host Port number and save & exit the file forcefully and run below commands 
```
    :wq! 
    systemctl restart docker 
    docker start cont1
    docker ps 
```
Q) Why Host Port is 80 for Every Container 

- Because all the webserver like Nginx, Apache are running in default 80 port. 


## Docker HUB

- Docker Hub is Cloud-based repository provided by Docker.

- Docker hub is free and open source Centralised platform.

- Docker Hub allows users to store, retrieve and share the docker images.

- Additionally, it allows user to upload the docker images and make them available to other in the community

### Why Docker Hub

-	In real time, We write the docker file and build the image using docker file 

-	By using docker hub, we store that image.

-	We can Pull & Run the image in any environment. Ex: Dev, Test, Prod

Q) How to Create Docker Hub 

- Search ‘hub.docker.com’ in Browser

- Create Account

Q) How to Connect and login Docker-Hub 

- Run the command in CLI 
```
    docker login 
```
Now Enter Docker Hub Username & Password.

Note: The Password stored Unencrypted in /home/ec2-user/.docker/config.json


# Docker File 