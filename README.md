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

`Scenario`, if you have bug in one service.

U need to fix the issue, 

if you use Monolythic, we have to stop the entire server and fix the bug.

if you use Micro-service, we have to stop only one service and users can access other services and fix that issue.

In Monolythic, Maintaining one server is esay 

In Micro-services, Maintaining multiple services is difficult.

For that, we use `Docker`

# Introduction to Docker

- Docker is Open-source containerization platform to create, deploy and run application.

- Docker is written in GO language.

- Docker uses containers on host OS to run applications. It allows applications to use the same Linux kernel as system on the host computer, rather than creating a whole virtual OS.

- We can install Docker on any OS but Docker engines runs only on Linux distribution.

- Docker performs OS level virtualisation also called as containerisation.

- Docker packages software into standard units called as Container that have everything that need to run application, including code, run time, system tools, libraries and dependencies.

- Before docker many user face problems that a particular code is running in the developer system but not in the user system.

- It was initially released in march 2013 and developed by Solomon-Hykes and Sebastian Pahl.

- Docker is set of Platform as a service(PAAS) that use OS level virtualisation, whereas VM ware uses hard-ware level virtualisation.

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

![image](https://github.com/naveensilver/Docker/assets/120022254/3c17c3e7-0dfe-49b7-9fbf-911f19f8545d)

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

![image](https://github.com/naveensilver/Docker/assets/120022254/0fc2bb25-366d-4789-8928-72144b96c5f0)

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
```
1. Resource Utilization: Containers share the host operating system kernel, making them lighter and faster than VMs. VMs have a full-fledged OS and hypervisor, making them more resource-intensive.

2. Portability: Containers are designed to be portable and can run on any system with a compatible host operating system. VMs are less portable as they need a compatible hypervisor to run.

3. Security: VMs provide a higher level of security as each VM has its own operating system and can be isolated from the host and other VMs. Containers provide less isolation, as they share the host operating system.
    
4. Management: Managing containers is typically easier than managing VMs, as containers are designed to be lightweight and fast-moving.

```
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

Docker is a containerization platform that provides easy way to containerize your applications, which means, using Docker you can build container images, run the images to create containers and also push these containers to container regestries such as DockerHub, Query.io and so on.

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

1. Docker client: The Docker client is a command-line interface (CLI) tool that allows users to interact with the Docker daemon. The client sends commands to the daemon, which in turn executes them.

2. Docker Host: It is machine where we installed docker engine/docker

- `Docker daemon:` The Docker daemon (Dockerd) is the core component of Docker architecture. Daemon runs on the host operating system and manages all the containers, images, networks, and volumes on the Docker host. Daemon is also called as Docker Engine.

    - `Docker images:` Docker image is a package which contains everything needed to run an application. Which includes App code, Dependencies/Software, Libraries, Env, configuration files.

    - `Docker containers:` Docker containers are the runtime instances of Docker images. They are isolated environments that run the application and its dependencies. Multiple containers can run on the same host, each container with its own isolated environment.

    - `Docker networks:` Docker networks are used to connect multiple containers together, enabling communication between them.

    - `Docker volumes:` Docker volumes are used to persist data between containers. They are stored outside of the container, allowing data to be shared between containers or to be stored on the host.

3. Docker registry: Docker registry is a place where we can store and retrieve docker images. which is free and open source. we can download the images and used to create the containers. docker registry is also called as Docker Hub.

There are two types of Registry are available 

- Public - Docker Hub is a public registry. Everybody can store and retrieve images

- Private - Nexus, JFrog, AWS ECR (Elastic container registry) are private registries - company specific

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

Tasks
=====

### Build your First Docker Image

Q) Deploying Python Code Hello-World Application 
--------------------------------------------------

- Get the source code from GitHub 
```
https://github.com/naveensilver/Docker.git
```
Now, Go to Directory where our Dockerfile and app.py directory present.

Note: We need to run the docker commands where the docker file is present.

- Now, Execute the Dockerfile using `docker build` 

```
docker build -t naveensilver/my-first-docker-image:latest .
```
It will create a image name called `naveensilver/my-first-docker-image:latest` and Check the images list `docker images`

- Now Run the image or Create Container using this Image
```
docker run -it naveensilver/my-first-docker-image:latest
```
It shows "Hello World" and docker container created we can check the container list `docker ps -a`

- Now, Push the Image in Docker Registry. For that we have to login docker hub from cli.
```
docker login
```
Enter Docker Hub User name:  and Password: 

- Now, Push the image using 
```
docker push naveensilver/my-first-docker-image:latest
```
It will generate a `Sha_ID` and Image got pushed. Go and Check in Docker Hub

Q) How to get the image from Docker Hub
---------------------------------------

- Check the docker info `$ docker info`

- Now Pull the image `$ docker pull <ImageName>` i.e., `$ docker pull hello-world`

    - Here, docker pull is used to pull/download images from Docker-Hub
    - hello-world is the default image stored in Docker-Hub

- To see list of docker images `$ docker images `

- To run docker image `$ docker run <image-id/name>` i.e., `$ docker run hello-world`

> hello world image got executed and created a new container.

- check the list of containers `$ docker ps`

Q) How This Docker image got executed 
------------------------------------

1. When ever you give docker "docker run, docker pull, docker Build" in CLI. The docker client contacted the docker daemon.

2. Whenever you give " docker pull <hello-world>". docker daemon pull "hello-world" image from docker hub.

3. whenever you give 'docker run <hello-world>' docker daemon created a new container to start our application by using that image.

4. The Container application provides infomation to docker engine, The docker engine/daemon sent the output to docker client in the terminal (CLI)

# Docker File Architecture | Docker Life Cycle:

![Screenshot (103)](https://github.com/naveensilver/Docker/assets/120022254/9abd688c-6ed9-41ed-bd88-a21cb932ecc1)

There are three important things,

1. docker build - builds docker images from Dockerfile
2. docker run   - runs container from docker images
3. docker push  - push the container image to public/private regestries to share the docker images.

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

# Image And Containers



# Docker Commands

docker -v 

docker info # To see docker info

docker help 

docker login # To Connect Docker Hub Account 

docker images  # To see list of docker images

docker ps # To See List of Container

docker pull <image-id> # download the docker image from docker-hub

docker run <image-id>  # To create container (default name)

docker run -it --name contName imageName # create container and enter into container 

    [-it : interactive terminal] 
    [ctrl + p+q : exit from container without stopping container]

docker push <image-id> # To store the image in Docker Hub

docker build # used to build the image from docker file

docker tag #Image Versions

docker rmi <image-id>

- To Check Images List : `docker images`

- To Check Container list : `docker ps -a`

- To pull the image from Docker hub : `docker pull <imageName>`

- To Create image as well as Container : `docker run <ImageName>`

- To Start container :  `docker start <container_ID/ContainerName>`

- To Delete stopped container (few) : `docker rm <container_ID/ContainerName> `
- 
- To Delete all the stopped/Exited containers (Multiple) : `docker container prune`

Note : we can't remove running containers 

- To Remove Image : $ docker rmi <ImageName>

Q) Create A Container From Image in Diff ways / Running a Container using IMAGE :

docker run -it --name [container] [image]            

docker run -it --name cont1 -p 8077:80 image1 # with port number 

 	(it – interactive terminal (Container Up state) | -p – port | 8077 – host port(any no.) | 80 – container port [constant])

Note: You can access container in Browser = Host Public_IP:8077

docker run -it --name cont1 -d ubuntu = de tact mode (-d)

docker run -it --name cont2 -d -p 8080:80 ubuntu = de tact(-d) mode with port number (-p)

docker exec -it cont1 /bin/bash  = entering into container and exit without stopping a container


# Docker Image Commands:
```
docker ps / docker container ls – To see only running/up containers

docker ps -a / docker container ls -a [ ps=processor -a=all]  - To see all containers (Running containers as well as exited container)

docker container ls -n 2 – To see latest 2 containers

docker container ls --latest – To see latest containers

docker container ls -a -q – To see only container ID (-q is ID)

docker container ls -a -s : To see containers along with Size

docker run <ubuntu/image> - To get the image as well as create a container

docker pull <ubuntu/image> - To get the image from docker hub

docker container prune

docker image prune/docker rmi <image>

docker rmi <nginx ubuntu>

docker commit <cont1> <image1> = create a image from container 

docker image prune = remove only existed images all at a time

docker rmi nginx ubuntu  = remove multiple images

docker image inspect <image1> = every detail of a image  
```

# Docker Container Commands
``` 
docker start [cont1]

docker start [cont1] [cont2]

docker stop <cont1> - To stop container

docker stop <cont1> <cont2>

docker stop $(docker ps -a -q) = To stop all the containers at a time 

docker rm <cont1> = To delete container

docker rm <cont1> <cont2> 

docker container prune = To remove all exited/stopped containers

docker rm $(docker ps -a -q) = To delete all the containers at a time 

docker attach <cont1> = enter into container 

    ctrl+p+q = exit from container without stopping a container 

docker rename <old_cont> <new_cont>

docker inspect <cont1>
```

Tasks:
======

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

Q) Where is default docker directory path in Host server ?

- cd /var/lib/docker/

```
drwx--x--x  4 root root  120 Mar 12 15:11 buildkit
drwx--x---  9 root root 4096 Mar 19 09:31 containers # container info 
drwx------  3 root root   22 Mar 12 15:11 image # image info
drwxr-x---  3 root root   19 Mar 12 15:11 network # network info
drwx--x--- 35 root root 4096 Mar 19 09:36 overlay2
drwx------  4 root root   32 Mar 12 15:11 plugins
drwx------  2 root root    6 Mar 19 09:36 runtimes
drwx------  2 root root    6 Mar 12 15:11 swarm
drwx------  2 root root    6 Mar 19 09:36 tmp
drwx------  2 root root    6 Mar 12 15:11 trust
drwx-----x  3 root root   65 Mar 19 09:36 volumes # volume info
```

Q) Why Host Port is 80 for Every Container 

- Because all the webserver like Nginx, Apache are running in default 80 port. 


# Registry 

- Registry is used to store and destributing container images.

- Registries are two types :

1. Cloud Based Registry 

    - Docker Hub 

    - Elastic container registry (AWS ECR)
    
    - Google container registry (GCR)

2. Local Registry 

    - Nexus 
    
    - jFrog

    - Docker trusted registry (DTR)

## Docker HUB

- Docker Hub is Cloud-based repository provided by Docker.

- Docker hub is free and open source Centralised platform.

- Docker Hub allows users to store, retrieve and share the docker images.

- Additionally, it allows user to upload the docker images and make them available to other in the community

### Why Docker Hub

![Screenshot (111)](https://github.com/naveensilver/Docker/assets/120022254/e6c432c7-11e1-4447-8a89-4483121e224d)

-	In real time, We write the docker file and build the image using docker file 

-	By using docker hub, we store that image.

-	We can Pull & Run the image in any environment. Ex: Dev, Test, Prod

Q) How to Create Docker Hub 

- Search ‘hub.docker.com’ in Browser

- Create Account

Q) How to Connect and login Docker-Hub from CLI ?

- Run the command in CLI 
```
    docker login 
```
Now, Enter Docker Hub Username & Password.

Note: The Password stored Unencrypted in /home/ec2-user/.docker/config.json

Q) How to push Images to Docker Hub

- First TAG the image 
```
 docker tag <local-image:tagname> <DockerHub_UserName>/<Repo_Name>:<TagName>
```
- Push the Image `docker push <DockerHub_UserName>/<Repo_Name>:tagName`

```
    docker push naveensilver/repo-1:version1
```

Note: We can't push Multiple Image at a time. Each Repo is having only one image version. If you push same image version in same repo, old image version will be deleted.

Using `docker pull naveensilver/repo-1:version1` can get image from docker registry.

# Docker File 

Docker file is a text file. which contains some set of instructions to build docker image.

Docker file is automation of docker image creation.

Docker file is used to create our own image.

In docker file, we will use DSL (Docker Specific Language) keywords.

Docker Engine will process Dockerfile instructions from Top to Bottom

Docker command should run where your docker file exists.

Below are the Dockerfile Keywords/Components >>

```
FROM 
MAINTAINER 
COPY 
ADD 
RUN 
CMD 
ENTRYPOINT 
WORKDIR 
ENV 
LABEL 
USER 
EXPOSE 
VOLUME 
```
Note: The components should be in Capital letters and also 'D' is capital in "Dockerfile".

Docker File Architecture | How Docker File Works 
-------------------------------------------------

Using Docker file, we can create our own image.

1. Create Docker file : In the docker file, we will write some set of instructions.

```	
    vi Dockerfile
``` 
Add below instructions inside Dockerfile
```
	FROM ubuntu 
	RUN echo "run one"
	RUN echo "run two"
	CMD echo "echo from image'
	CMD echo "echo from latest"
```

2. Build Docker File : Using docker file, we will create our own image by executing below command 
```
    docker build -t <imageName> .    
```
Here, 

- `-t` used to specify the image name.

- `.`represents current directory. it will search for Dockerfile in the current location.

- Then the docker image created. and check the docker image list 
```
    docker images
```

3. We will store that Docker image in Docker Hub using 
```
    docker push
```

- Whenever, you want to push the image to public repo. first u need to tag that image and push the image.

- By using Image Tag command (Tag means giving ID) `docker tag <imageName> username/<RepoName>`

```
    docker tag image1 naveensilver/myrepo
```
- Now, Push that image in Docker Hub
```
    docker push naveensilver/myrepo
```
4. Create a container by using this image.

- First, we can pull that image from Docker hub using 
```
    docker pull naveensilver/myrepo : latest'
```
- Then, we can create container using
```
    docker run -it --name cont1 naveensilver/myrepo'
```
Note: We can Create No. of containers using that image.

5. Then the container will be created successfully. Check the containers list 
```
    docker ps -a'
```

In real time also, we store that image in Project Docker Hub

So, We can Pull & Run the image in Multiple Environments. Ex: Dev, Test, Prod

Note: If you inspect image `docker image inspect <image1>`. We can see the layers. i.e, No of tasks in Dockerfile = No. of layers.

```
        "RootFS": {
            "Type": "layers",
            "Layers": [
                "sha256:5498e8c22f6996f25ef193ee58617d5b37e2a96decf22e72de13c3b34e147591"
```

---------------------

### Docker File Components/Keywords :

1. FROM 

- It indicates Base image to run our application.

- Base images are required to create our own images. Base images are already stored in Docker Hub.

- `FROM` must be on the top of the Dockerfile.

- Syntax: `FROM <Base-imageName>`

Ex: 
```
	FROM ubuntu 	      #i want to run my app using ubuntu OS
	FROM java:jdk-1.8.0   #For java application we need jdk 
	FROM tomcat:9.2	      #Server - For accessing application
```
Note: We can configure more than one base image and maintained in new line.


2. MAINTAINER / LABEL: 

- It Represents who is author of Dockerfile

- Labelling like Author Name, Email.. etc 

- Syntax :  `MAINTAINER <EMP ID>` OR `LABEL <Emp ID>`

Ex: 
```
MAINTAINER Naveensilver <naveensilver@gmail.com>
```

3. COPY : 

- It is used to copy files/folder from local to Docker VM while creating image.

- Syntax: `COPY <source> <destination>`

Ex: Copying war file from target directory to tomcat/webapp directory

```
    COPY target/maven-web-app.war /usr/local/tomcat/webapp/maven-web-app.war 
```
4. ADD

- ADD used to copy files to image while creating an image.

- Syntax: `ADD <source> <dest>`

ADD keyword can download the files from internet and extract files.

ADD keyword will extract tar file while copying to image.

- Syntax:  `ADD <url-to-download> <dest>`

Ex:
```
ADD http://dlcdn.apache.org/maven/maven-3/3.8.7/binaries/apache-maven-3.8.7-bin.tar.gz myfolder/maven
```
Note: zip files, we have to extract manually.

Q) Diff B/w RUN, CMD & ENTRYPOINT 

5. RUN 

- RUN used to execute the commands on top of base image.

- RUN instructions will execute while creating an image `docker build -t <imageName> .`

- We can write multiple RUN instructions, they will execute in order (Top-Bottom)

- Syntax : RUN `<Commands>`

Ex: 
```
 		RUN mkdir foldername
		RUN yum install git -y 
```

6. CMD 

- CMD is also used to execute commands.

- CMD instruction will execute while creating container (Running a image) `docker run -it <image> <Container>`

- We Can write multiple CMD instructions in Dockerfile but docker will execute only last CMD instructions.

Note: There is no use of writing multiple CMD instructions in Dockerfile.

Syntax: `CMD sudo start tomcat`

Ex: Sample Dockerfile 
```
From Ubuntu
MAINTAINER Naveen 2269305
RUN echo "run one"
RUN echo "run two"
CMD yum install git -y            # [“yum”, “install”, “git”,”-y”] 
CMD echo "cmd one"                # ["echo","cmd one"]
CMD echo "cmd two"
RUN echo "run three"
```
- Build image using docker file `docker build -t image1 .` 

- Check the image list `docker images`

- To run the image | To creating a container
```
    docker run image1    #O/p : cmd two 
```
Note : CMD instruction we can overwrite using runtime CMD	
```
    docker run image1 date #It will print only time & date 
    docker run image1 whoami #O/p : root (Ubuntu) 
```

7. ENTRYPOINT

- Entrypoint instructions will execute while creating container(Run a image) `docker run`

- ENTRYPOINT has high priority than CMD because it will overwrite the values of CMD.

- We can't Overwrite ENTRYPOINT instructions.

Syntax : ENTRYPOINT ["echo" , "Welcome to My world"]

Ex1: 
```
    FROM centos:centos7
    CMD [“yum”, “install”, “tree”,”-y”] 
    ENTRYPOINT [“yum”, “install”, “git”,”-y”] 
```
- Build image `docker build -t <imageName> .`

- Run the image/ Create container `docker run <imageName>`

- ENTRYPOINT will execute while creating a container.

Note: If we give `CMD` and `ENTRYPOINT` in Dockerfile. Docker will execute only ENTRYPOINT. Bcz it has high priority.

Ex2: Using ENTRYPOINT, We can Perform tasks in CLI.
```
    FROM centos:centos7
    ENTRYPOINT [“yum”, “install”, “tree”,”-y”] 
    ENTRYPOINT [“yum”, “install”, “git”,”-y”] 
```
- Only latest task will perform. If you want to run multiple ENTRYPOINT we can perform in CLI.

- Now, Build the image `docker build -t <imageName> .`

- Run the Image/Create Container `docker run <imageName> tree maven`

- Now Check the Container list `docker ps -a` 

- We can see tree, git and maven also. maven is executed through CLI.

Note: We can't perform these activities in CMD.

Ex3: 
```
    FROM centos:centos7
    ENTRYPOINT [“yum”, “install”,”-y”] 
    CMD [‘tree”]

```
- It will run CMD bcz we have not mentioned anything in Entrypoint. So,it will install tree.

- If u give the package name in command line while building the container.`docker run image httpd` => it will install only httpd 

8. WORKDIR 

- Used to set working directory for an image/container[Project files]

- Syntax: `WORKDIR <Dir-Path>`

Note: The dockerfile instructions which are available after WORKDIR those instructions will be process from given working directory.

Ex: Create Dockerfile 

```
    FROM centos:centos7
    LABEL silver "silver@gmail.com"
    WORKDIR "/MY PROJECT"
    RUN touch /file1
    RUN mkdir myfolder
    RUN echo "hai i am adding some data in file1" > file1
    COPY /file1 myfolder/file1
    ADD http://dlcdn.apache.org/maven/maven-3/3.8.7/binaries/apache-maven-3.8.7-bin.tar.gz myfolder/maven
    CMD ["yum","install","git","-y"]
    ENTRYPOINT ["yum","install","-y"]
    CMD ["tree"]
```
```
    docker build -t image1 .
    docker run -it --name cont1 image1 
```
Note: These Dockerfile actions should perform inside a container. We can check the o/p inside container.
```
    docker attach cont1
```

Q) Difference B/w ARG and ENV ?

9. ARG 

- Used to assign the values to the variables, it will not available once we build it.

- In container also it's not possible to access it.

Syntax: 
```
    ARG branch = developer
	LABEL branch $branch
    RUN echo "i am $branch"
```
Note : we can change argument values in RUNTIME/CLI `docker build -t <ImageName> --build-arg <var_name>=<value>`
```
docker build -t image1 --build-arg branch=feature
```
10. ENV 

- ENV is used to set Environment variables.

- These variables are used for inside the container.

- Syntax: `ENV <key> = <value>`

Note: We can't change the values in command line arguments. we need to change the ENV variable using CMD line then we have to use ARG and place ARG variable.
```
ARG abc=devops 
ENV xyz=aws 
RUN echo $abc 
RUN echo $xyz
```

11. LABEL 

- Label will reprsents the data in key-value pair

- Label is used to add metadata from our image

- Syntax: `LABEL branchName release`

12. USER 

- We can set user for an image/container

- Note: After user instruction, remaining instructions will be processed with give USER


13. EXPOSE

- Expose is used to maintain the port no. of our application.

- It is just like a documentation to understand container running port number.

Syntax : 
```
    EXPOSE 8080  #For Tomcat 
	EXPOSE 80    #For Nginx
```


14. VOLUME 

- Used for data storage (data mount)

- To create a volume folder inside container and we can create multiple Volumes.

- Basically when you run the image, container will generate some data. If you kill container we will lose the data. if you want to store the data permanently. we can go for volume.

- Syntax: `VOLUME /myvol`

# Tasks

1. Deploy a spring-boot application Using Docker Container 
==========================================================

- github.com/ashokitschool/spring-boot-docker-app 

- Docker video-4 (timelaps- 01:20) [Pending]

2.Dockerizing Java WEB Application
==================================

- Docker Video-5 (Timelaps - 4:00) [Pending]

3.Dockerizing Python flask applicatiom 
======================================

- Docker -5 (28:00) [Pending]

4. Docker Containerization for Django 

- Abhishek.veeramalla@Youtube [Day-25]  [https://youtu.be/3IAvr_O6vao?si=OCy7xLAWeoe_E96p]

5. MultiStage Docker Build  [Most Important]

- Abhishek.veeramalla@Youtube [Day-26] [https://youtu.be/yyJrZgoNal0?si=ZEGISJmMzXxaAWsw]

```
This Video Covers:

1. Multi Stage Docker Builds
2. Reduce Docker Image Size
3. Distro Less Images
4. Containers Security
5. Interview Questions with Answers
6. Scenario Based Production Q & A
```

# Docker Volumes

Docker volumes are a way to persist data generated by and used by Docker containers. They are separate from the container's filesystem, allowing data to persist even after a container is stopped or removed. Volumes can also be shared among multiple containers.

![image](https://github.com/naveensilver/Docker/assets/120022254/5152f75e-f55c-4406-8fc2-98e25d507cdc)


In Simple, 

- Docker volumes are used to store/persist the data generated by docker containers in the host machine.

- Using docker volume, we can de-couple data storage from docker container

- Using docker volume, we can share the data among multiple container.

- On deletion of container, docker volume will not be deleted.

## Rules To create a volume

- It is not possible to create a volume on existing containers.

- We can share the volume to multiple containers. Data will be updated in all the containers at a time. if the cont1 volume shared to cont2 the changes made by cont2 will be also reflect in con1

- Volume will not be reflected when you update an image.

- Even if we stop the container, we can access the volume.

- We can declare a volume directory while creating a container.

- Volume is simply called as a directory inside a container.

### Difference b/w Volume and Directory

- Volumes can't be deleted, But directories can. 

- volumes is used to share the data to multi container at a time.

- Folder will not share the data among containers.

It is not possible to create a volume on existing container.

We can share the vol to multi container, the data will be updated in all the containers at a time.

We update/creating a new image from vol container, only container data shared but vol data will not included  docker commit <cont1> <image1>


### You can map volumes in two ways 

1. Container to Container [Volume mounting]
2. Host Machine to Container [Bind Mounting]


### Docker Volume Commands

$ docker volume --help #To display docker volume commands

$ docker volume create <vol-name>  #To create docker volume 

$ docker volume ls  #To display docker volumes list

$ docker volume inspect <vol-name> #To display info of one or more vol 

$ docker volume rm <vol-name> #To delete one or more docker volumes  

$ docker volume prune #To delete all the unused docker volume

## Why Mount Volume

Lets Understand the scenario,

- Pulling nginx webserver image from Docker Hub
```
    docker pull nginx  #nginx is web server 
```
- Running nginx image using Docker container name as "cont1" 
```
    docker run --name=cont1 -d -p 80:80 nginx
```
Note: Access static website using EC2 VM Public IP which is hosted by Nginx. i.e., 123.457.54.1

>>  " Welcome to Nginx "

- Modify statsic website content in index.html (file available in cont1)
```
docker exec -it cont1 bash  #Enter into a container 
```
```
cd /usr/share/nginx/html  #File path  >> ls -l 

$ echo " Welcome to Silver World" > index.html
```
Note: Access static website using EC2 VM Public IP which is hosted by Nginx. i.e., 123.457.54.1

>>  " Welcome to Silver World " # Modified content

```
$ exit  #Exit from container 
$ docker stop <cont-id> #Stop the cont1 and Check nginx server
```
Now i want to Run Nginx in Another container 

- Start another docker container with name as "cont2"
```
docker run --name=cont2 -d -p 80:80 nginx 
```
Note: Access static website using EC2 VM Public IP which is hosted by Nginx.

>> " Welcome to Nginx "

In index.html file, The Changes we made in the cont1. it will not be available for cont2. It is giving default data of a file.
```
    exit && docker stop cont2
```
`To overcome this problem, we use "Docker mount Volume`

## Docker Mounting

Mounting in Docker volumes is the process of attaching a directory from the host machine or another container to a directory inside a Docker container. This allows the container to access and manipulate/manage the files in the attached directory.

Docker volumes provides secure data storage in containers. 

In Docker volumes, the data to be shared in two ways 

1) Container to container [Volume mount]

2) Host Machine to container [Bind mount]


We can mount the volume to multiple containers.

When a volume is mounted to a container, the data in the volume can be read and written by the container.

If we modify the data in the mount volume. The Data will be updated in all the containers at a time. 

Ex: if the cont1 volume shared to cont2 the changes made by cont2 will be also reflect in con1.
 

1) Volume Mount (Container to Container) 

- Volume mounts create a new volume that can be shared between containers or persisted independently of any containers. 

- The Data in the volume is not deleted when a container is removed. 

- Volume mounts are a better than bind mounts when you want to share data between containers or when you want to persist data independently of any containers.
```
$ docker volume create my_volume
$ docker run -v my_volume:/path/on/container my_image
```
This command creates a new volume named `my_volume` and starts a container using my_image as the image. The volume `my_volume` is mounted to the `/path/on/container` directory inside the container. Any data written to this directory by the container is stored in `my_volume`.

Ex:

- Create Docker volume 
```
    docker volume create my-volume  
```
- Docker volume list 
```
    docker volume ls 
```
- Check the Image (nginx should present or pull the nginx image )
```
    docker images 
```

- Start docker container by mounting docker volume
```
    docker run -d --name=cont3 --mount source=my-volume,destination=/usr/share/nginx/html -p 80:80 nginx
```
(OR) 

```
docker run -d --name cont3 -v my-volume : /usr/share/nginx/html -p 80:80 nginx
```

What ever the data is generated in "/usr/share/nginx/html" that is mounted to "my-volume". So, this is called mounting docker container to docker volume

Note: Access static website using EC2 VM Public IP which is hosted by Nginx.

>> "Welcome To Nginx"

- Modify the content of index.html 
```
$ docker exec -it cont3 bash 
$ cd /usr/share/nginx/html
$ echo " Welcome to Silver World" > index.html
```
Note: Access static website using EC2 VM Public IP which is hosted by Nginx 

>> "Welcome To Silver World"

- Exit and Stop the Container 

- Run another docker container and mount "my-volume"(modified data should reflect)

```
docker run -d --name=cont4 --mount source=my-volume,destination=/usr/share/nginx/html -p 80:80 nginx
```
Note: Access static website using EC2 VM Public IP which is hosted by Nginx 

>> "Welcome To Silver World"

So, we are able share the files from one container to another container by using "docker volume". That file data is stored in "my-volume"

Another Way
-----------

Task-1
------

- Creating a volume with container
```
    docker run -it --name cont1 -v /myvolume ubuntu
```
- Go inside a container /myvolume and add some files
```
    cd /my volume
    touch file{1..5}
```
- Exist from container 
```
    exit
```
- Create new container "Cont2" and share "/myvolume" to cont2
```
docker run -it --name cont2 --privileged=true --volumes-from cont1 ubuntu 
```

- Now check the "/myvolume" directory files.

Task-2
------

Make changes in cont2 and check the data is reflecting in cont1 or not ?


Q) How many ways to Create Docker Volumes ?

Volume Creation Can be done in Two ways 

1. Through Command Line

- Creating a volume with container
```
docker run -it --name cont1 -v /myvolume ubuntu
```
- Create new "Cont3" and sharing existed "volume" to cont2
```
docker run -it --name cont3 --privileged=true --volumes-from cont2 ubuntu  
```
- Sharing volume as well as creating container and creating new volume. 

```
docker run -it --name cont4 --privileged=true --volumes-from cont3 -v /vol image1 
```
2. Using Dockerfile

```
FROM ubuntu
VOLUME ["/myvolume]
VOLUME ["/myvolume2]
```
>> Build it & Create container

Q) How To Access Volumes 

We can access the volumes in two ways 

1. Entering into container  

- we can access and update volume only when container is running

```
docker exec -it <contName> /bin/bash
```

2. Local docker path 

- we can access and update volume at any time when the container is running or not.

- Docker volumes default path 

```
cd  /var/lib/docker/volumes/<Volume_Id 86dc65900c95235f6a102a>/_data
```

- Go to _data > Here, we can see all volumes 


<Class-6 Ashokit>

`Instead of giving the volume name, we can give the path of our ec2 also that is called "Hosted Volume"`

2. Bind Mount (Host To Container)

- Bind mounts allow a directory or file on the host machine to be mounted to a container. 

- The files in the mounted directory are accessible to the container, and any changes made by the container are visible on the host machine. 

- Similarly, any changes made on the host machine to the mounted directory are visible in the container.

>> Scenario, 

First We need to create a Directory in Host Machine and then we can mount

```
    mkdir myfolder
    docker run -v </path/on/host> : </path/on/container> my_image 
```

This command starts a container using `my_image` as the base image and mounts the directory located at `/path/on/host` on the host machine to the `/path/on/container` directory inside the container. 

Any files or directories in `/path/on/host` on the host machine are now accessible in the container.

Ex: 

- Select the specific path in Host Machine
```
cd /home/ec2-user
```
- Create a directory in host machine

```
mkdir -p /tmp/nginx/html  
```
- Run docker container for nginx image with directory mounting (Container name is c1)
```
    docker run -t -d -p 80:80 -v /tmp/nginx/html:/usr/share/nginx/html --name c1 nginx:latest  #mounting local directory 
```

>> [ -v host-dir-path : cont-dir-path ]
>> [ -p host-port : cont-port]

- See the containers which are running (c1 should be running)

```
    docker container ls 
```
Note: Access Nginx webserver using Host Machine Public IP 
(It will not be displayed bcz index.html file not available in container)

- Go to Mounted Directory in host machine 
```
    cd /tmp/nginx/html
```

- create index.html file 
```
    vi index.html 
	<h1> Welcome to Docker Volume </h1>
```
Note: Access Nginx webserver using Host Machine Public IP (Changes will be reflected)


If you modify changes in host-directory index.html file then automatically the changes will be reflected in container is called " Host Directory Mounting to Docker Container"


Another way 
-----------

Mounting Folders To Container/ Create a folder and attach to container 

- Create a folder  `mkdir folder1`

- Go inside a folder1 and create some files 

- Inside folder1 Run command 
```
docker run -it --name cont6 -v "$(pwd)":/myfoldervolume ubuntu
```
- Attach to container and check the data inside myfoldervolume 

### Conclusion 

Overall, mounting in Docker volumes provides a flexible and efficient way to store and share data between containers and the host machine.


Task 
----

Q) How to mount volume to multiple containers ?

- First Create a volume 
```
    docker volume create my_shared_volume
```
- Then Mount Volume to containers 

```
    docker run -it --name container1 -v my_shared_volume:/path/to/mount my_image

    docker run -it --name container2 -v my_shared_volume:/path/to/mount my_image
```
Note: Both "container1" and "container2" will now have access to the same files and directories that are stored in the "my_shared_volume" volume.

Any changes made to the volume from one container will be immediately visible to the other container.


Q) State-Less Container vs State-Full Container


We are going to loose the data which is generated by the container. by default all containers are stateless containers.

whenever the docker container got created. it will generate some data. That data can be database or log files or other some files... 

When you stop/delete the container - we are going to loose the data 
 
But i dont want to loose the data. i want to make my container as statefull container.

I want to store the data permanently even if the container got deleted/stopped.

To Make docker container as statefull container by using docker volumes 

Docker Volume are used to store the data which is generated by Docker container.

Two way to store the data by mounting the volume

	1. Volume Mount 
	2. Binded Mount Volume

# Docker Network

- Docker Networking is all about communication among processes.(Communication from one container to another container using networking)

- Docket network allows containers to connect/communicate with each other and to external networks such as the host network or the internet.

- Docker Network enables a user to link docker container to as many networks as they required.

- Docker network is used to provide complete isolation/IP Address for Docker container

- It allows you to attach your container into many networks

![Docker-Networks](https://github.com/naveensilver/Docker/assets/120022254/8cd42d02-deff-4944-9477-98544e09f4bf)


### Advantages Of docker Networking

1) They share single operating system and maintain containers in isolated manner.

2) It requires fewer OS instance to run the workload.

3) It helps in fast delivery of the software.

4) It helps in application Portability.

`Scenario,`

When Docker installed in a machine by default 3 docker network drivers will be configured.

	1. None
	2. Host 
	3. Bridge

Note: One container, we can attach to multiple networks

- when container is attached to multiple networks then those containers can communicate.

- Docker providing networking to containers using network drivers.

### Docker Network Drivers

1. Bridge Driver
2. Host 
3. None 
4. Overlay
5. Macvlan

-----

1. Bridge : This is the default network driver created on the Docker host machine.

Note: Bridge Network driver are very useful when application running in standalone container(Only one container).

We can see more details about bridge driver using below command 
```
docker network inspect bridge
```
2. Host Driver : It is useful when standalone container is available.

The container will not get any IP address when we enable Host Driver.

Note: For example a container is executed that binds to port 80 with host network driver. In this case, we no need to map container port to host machine port.

This is useful when we are running our container with large no.of ports.

3. None Driver (null)

In this type of network, the containers will have no access to network.

The None driver simply disable networking for a container, making it isonlate from other containers.

4. Overlay Driver

We will use docker swarm to orchestrate our Docker Containers 

Overlay Driver will be used when we have Docker Swarm Cluster.

5. MacvLan Driver

This network Driver will assign a MAC address to a container

MAC address will make our device as Physical 

Using this MAC address Docker engine routes the traffic to Particular Route.

Macvlan driver simplifies communication between container

### Working With Docker Networking Commands

- To list all the network 
```
    docker network ls 
```
- Running docker container with default network 
```
    docker run --name nginx -d -p 80:80 nginx 
```

- if you inspect Nginx Image (By default bridge network available)
```
    docker inspect nginx 
```
- To Remove docker network 
```
    docker network rm <network-id>
```
- To remove unused networks ALL at a time 
```
    docker network prune
```
- Creating our own bridge network
``` 
    docker network create --driver bridge <network-name>
```
Note : If we don't specify driver then by default it will take bridge driver.

- Run the docker container using custom network which we have created
```
    docker run --name cont1 -d --network my-network -p 7070:80 nginx
```
- To check the containers attached to my-network 
```
    docker network inspect my-network
```
========================= `Exercise` ========================

1. Running Container Using Bridge Network Driver
================================================

Now i want to check commununication between containers is happening or not ?

First i will create two containers using nginx image 

	>> nginx1
    
	>> nginx2

Both containers will be attached to single network (i.e my-network)

After attaching to single network, then i want to ping one container from another container.

If we are able to ping from one container to another container. then network is success.

>> Process:

- Pulling base image from Docker Hub 
```
    docker pull nginx
```
- Running 2 Docker containers using My-network and check connectivity b/w 2 container using ping command.
```
    docker run --name nginx1 -d --network my-network -p 8080:80 nginx

    docker run --name nginx2 -d --network my-network -p 9090:80 nginx
```
- Get IP address of docker container 

```
    docker inspect <ContainerName>
```
Here, Check Ip address of conatiner and it is a Bridge network
```
    docker inspect -f '{{range.NetworkSettings.Networks}} {{.IPAddress}} {{end}}' <cont-id/cont-name>
```
>> nginx1 Container IP : 172.19.0.1
>> nginx2 Container IP : 170.19.0.2

- Connect to Nginx1 Container and Ping Nginx2 Container IP
```
    docker exec -it nginx1 /bin/bash
```
Note: Here, we need to install Ping package
```
    apt-get update
    apt-get install iputils-ping
    ping -V
```
```
    ping 172.19.0.2
```
Ping is successfull means Nginx1 container attached to Nginx2 container

Now, Exit from nginx1 Container `exit` 

- Connect to Nginx2 Container and Ping Nginx1 Container IP
```
    docker exec -it nginx2 /bin/bash
    apt-get update
    apt-get install iputils-ping
    ping 172.19.0.1
```
Here, Ping Success means Communication between containers is Happening 

Q) How can you secure your container/app Using Concept of networking 

- Using Bridge Networking

Case-1) Container-1 should communicate with Container-2

Case-2) Container-3 should not communicate with Conatiner-1 and 2 [Isolation]

![image](https://github.com/naveensilver/Docker/assets/120022254/6f57d8fa-1677-462f-b1a1-853312058ef2)

Case-1) Container-1 should communicate with Container-2

- Here, I am Creating a container-1 as `login` and Container-2 as `logout` using nginx image

```
    docker run -d --name login nginx
    docker run -d --name logout nginx
```
- Lets understand the Ip address of both the container `docker inspect <ContainerName>` and Default Network

Now, Inspect `login` container 
```
    docker inspect login
```
```
            "Networks": {
                "bridge": {
                    "IPAMConfig": null,
                    "Links": null,
                    "Aliases": null,
                    "NetworkID": "422bbb8272dff0d84e8ef515aebbe2420507c712d561c1e94ad08d130bfda1ab",
                    "EndpointID": "6b5a276ed6a69119c6ae740596a12ba982acf7c6e5b0e82d3ff309feea49f226",
                    "Gateway": "172.17.0.1",
                    "IPAddress": "172.17.0.2",
                    "IPPrefixLen": 16,
                    "IPv6Gateway": "",
                    "GlobalIPv6Address": "",
                    "GlobalIPv6PrefixLen": 0,
                    "MacAddress": "02:42:ac:11:00:02",
                    "DriverOpts": null
                }
```
Here, we can see default netwrok `bridge` and Ip Address of login `172.17.0.2`

Now, Inspect `logout` container
```
    docker inspect logout
```
```
            "Networks": {
                "bridge": {
                    "IPAMConfig": null,
                    "Links": null,
                    "Aliases": null,
                    "NetworkID": "422bbb8272dff0d84e8ef515aebbe2420507c712d561c1e94ad08d130bfda1ab",
                    "EndpointID": "5b018ca41cfd184798e0c0645dd326ec769699e9029eb1bd420f564b918ace8c",
                    "Gateway": "172.17.0.1",
                    "IPAddress": "172.17.0.3",
                    "IPPrefixLen": 16,
                    "IPv6Gateway": "",
                    "GlobalIPv6Address": "",
                    "GlobalIPv6PrefixLen": 0,
                    "MacAddress": "02:42:ac:11:00:03",
                    "DriverOpts": null
```
Here, we can see default netwrok `bridge` and Ip Address of login `172.17.0.3`

- Now, Entering into container and try to communicate with other container using `ping`

```
    docker exec -it login /bin/bash
```
By default ping package is not available for that we have to install ping.

```
    apt-get update                       #ubuntu
    apt-get install iputils-ping
    ping -V
```
- Now, We are inside `login` Container and Try to Ping with logout container using `ping <logout_IP_Address>`

```
    ping 172.17.0.3
```
Here, ping got success means One container can access the another container which is on Same Host. Case-1 is Working.

Case-2) Container-3 should not communicate with Conatiner-1 and 2 [Isolation]

Now, I want to create a Conatiner-3 as `finance`. This Container-3 has to `logically Isolated` from cont-1 and conat-2. Why because i want my `finance` container more Secure.

- For that, i am creating custom network i.e., bridge network 
```
    docker network create <networkName>
    docker network create secure_bridge
```
- check, the list of docker network 
```
    docker network ls
```
Here, we can see newly created `secure_network` as `bridge` driver

- Now, try to assign this `secure_network` to `finance` container and let us see if the `login` and `logout` container can talk to `finance` container or not and my expectation would be, They should not be able to communicate with each-other because `finance` cont has some sensitive information and i want to keep this container secure.

```
    docker run -d --name finance --network secure_bridge nginx
```
- Now, Check the Containers list 
```
docker ps
``` 
Here, we can see `login`,`logout` and `finance` container

- Now, Inspect `finance` container
```
    docker inspect finance
```
```
            "Networks": {
                "secure_bridge": {
                    "IPAMConfig": null,
                    "Links": null,
                    "Aliases": [
                        "4b971120f45c"
                    ],
                    "NetworkID": "b9d3f2bd85afe87698075ddb84d157dd4309903d2334f11f5a408bb9c72bca33",
                    "EndpointID": "4b445bc79061524584cea2ee46f4ffa887b0fd31b5f3ff866a3649f1a66172eb",
                    "Gateway": "172.18.0.1",
                    "IPAddress": "172.18.0.2",
                    "IPPrefixLen": 16,
                    "IPv6Gateway": "",
                    "GlobalIPv6Address": "",
                    "GlobalIPv6PrefixLen": 0,
                    "MacAddress": "02:42:ac:12:00:02",
                    "DriverOpts": null
```
Here, we can see custom netwrok `secure_bridge` and Ip Address of login `172.18.0.2`

- Copy the Ip_Address of Finance and try to ping it from `login` and `logout` container and you will not able to communicate with `finance`

So, `login` and `logout` containers by default 'BRIDGE NETWORK'. So, they were able to communicate with each other. Where as the `finance` container is with custom 'secure network' that we have created. It is completely isolated. this is how you will make your container secure using the concept of Netwroking.

2. Running Container Using Host Network Driver
==============================================

- When we use Host network driver, port mapping is not required.

```
    docker run -d --name demo_host --network host nginx
```
- Inspect the container 
```
    docker inspect demo_host
```

```
            "Networks": {
                "host": {
                    "IPAMConfig": null,
                    "Links": null,
                    "Aliases": null,
                    "NetworkID": "bb6afdabb370c698ec6404cff82aaec047f04c9476facf4b6ca1403997e600eb",
                    "EndpointID": "e8ba5becc6f070ffc54423ed6f0a6923d23d18c4c408ef354d47b348a4f76896",
                    "Gateway": "",
                    "IPAddress": "",
                    "IPPrefixLen": 0,
                    "IPv6Gateway": "",
                    "GlobalIPv6Address": "",
                    "GlobalIPv6PrefixLen": 0,
                    "MacAddress": "",
                    "DriverOpts": null
```
There is No Ip_Address available because we are Using Host Network

- We can Access it with Host_IP in browser. 54.91.134.194

>> Welcome To Nginx 

Note: We are running nginx container without port mapping because we are using Host Network driver and we can't assign ports to host network.

3. Running a Container using Macvlan Network Driver
====================================================

In docker, a common question that usually comes up is 'how do i expose my containers directly to my local physical network?' This is especially so when you are running monitoring aplications that are collecting network statistics and want to connect container legacy applications. a possible solution to this question is to create and implement the macvlan network type.

Macvlan networks are special virtual network that allow you to create "clone" of the physical network interface attached to your Linux servers and attach containers directly your Lan. To ensure this happens, simple designate a physical network interface on your server to a macvlan network which has its own subnet and gateways.


- To check list of network drivers `docker network ls`

- Get IP address of Docker Host Machine `ifconfig`

Note: Take IP Address From `eth0` (Subnet & Gateway)

>> inet : 172.31.13.126

Depending on inet we will take Subnet and gate way as 

- Subnet : 172.31.13.0/24

- Gate Way : 172.31.13.1 

Note: AWS Always use '1' as a Gate Way IP

- Create Macvlan network using subnet and gateway
```
    docker network create -d macvlan \
	--subnet=172.31.13.0/24 \
	--gateway=172.31.13.1 \
	-o parent=eth0 \
	my-macvlan
```
- Check list of network drivers `docker network ls`

- To inspect network drivers
```
    docker network inspect <network-id/network-name>
```
If you inspect, there is no container is attached to this network.

- Now Run docker container using macvlan network that we have created
```
    docker run --rm -itd \
    --network=my-macvlan \
    --ip=172.31.13.110 \
    alpine:latest \
    /bin/bash
```
- Now Inspect the created Macvlan Network
``` 
    docker network inspect <my-macvlan/network-id>
```
In Inspect, one container is attached to Macvlan network.

Note: whenever we use this macvlan network, it is going to assign "MacAddress" for our container.

4. None driver : Nothing will be used (No network available)
===========================================================

5. Overlay Driver : Used in docker Swarm Concept 
================================================

## Real World Applications 

1. Monolithic Architecture Based App

- If the application contains 'N' no. of services (Ex: Paytm has Money Transactions, Movie Tickets, Train Tickets). If all these servers included in one server then it will called as Monolithic Architecture.

- Every Monolithic Architecture has only one database for all services.

- Architecture : 
```
		1-Server >> Multiple servicess >> 1-Database
```
2. Micro-service Architecture Based App 

- If the application contains No. of services. (Ex: Paytm has Money Transactions, Movie Tickets, Train Tickets). if every service has its own servers then it is called Micro-services.

- Every Microservice architecture has its own database for each service.

- Architecture:
```
				 Microservice-1		>> Database 
User Interface >>     
				 Microservice-2	    >> Database
```

- In real world,applications are getting developed using Microservices Architecture.

- In Microservices Architecture Multiple Services/API's will be Available.

- Ex: Amazon/ Flipkart Big Project. we have diff sub-project Services. 
	
    - Product Service 
	- Cart Service
	- Payment Service
	- Tracking Service

- Every Service/API(Application Programming Interface) is a Project and it should run in a container.

- Running multiple containers manually for all Services is difficult Job.

`To solve this problem "Docker Compose" came into Picture`

# Docker Compose

- Docker compose is tool which is used to manage (build, run and ship) multi container for applications.

- It used to create a multiple containers in a single host.

- Using Docker compose, we can define & deploy multi container based applications easily.

- We will give input to docker compose using YAML file to manage multiple containers as a single service.

- Docker compose YML file should have information related to all our service. (database, caches,webservic API..)


### Sample Docker-Compose YML 

- The Docker compose default file name : docker-compose.yml

- In this Docker Compose file. we are going to specify the information about versions, services, networks and volumes, configs. 

    - version : we can specify the version of docker compose file

    - services : we can Specify the services of applications
		>> Product API Image 
		>> Cart API Image

    - network : we can define the networking set-up of app.
		>>Run the containers with Isolation

    - volumes: we can define the volumes used by your applications.
		>> Making the containers as Statefull 

    - Configs: we can add external configuration to our containers. keeping configurations external will make container more generic.

Note: The default path of docker compose file is `./docker-compose.yml`.
it contains a service defination which configures each container started for that service.

### Docker-Compose Commands

- Create and start all the containers/services 
```
    docker-compose up 
```
- List Docker container started by docker compose 
```
    docker-compose ps 
```
- Run docker compose file 
```
    docker compose up -d 
```
- Stop and Remove all containers/services
```
    docker-compose down
```
- List of running container images
```
    docker-compose images
```
- Using different file 
```
    docker-compose -f <filename> up/down
```


### Docker Compose Set-up


- Download Docker compose file 
```
sudo curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
```

- Give Executable Permission 
```
sudo chmod +x /usr/local/bin/docker-compose
```
- Check the Docker-compose Version 
```
dokcer-compose --version
```
=========================
### Task-FLM-docker 7(33min) [Pending]


### Task - Docker 6 (1:20 Time) [Pending]
=========================================

Q) Create a docker compose file for setting up dev envronment. Mysql container is linked with wordpress container.

```
    vim docker-compose.yml
```
```
---
services:
  mydb:
    environment:
        .......
	...........
[Pending]
```
>> 

- To start above services from yml file
```
    docker-compose up 
```
- To Access the Wordpress site

>> VM_Public_IP: 9090   (Make sure 9090 port enable in Security Group)

- To Stop the both container at a time 
```
    docker-compose stop 
```
- To run the container in detached mode. 
```
    docker-compose up -d   
```
- To remove all the container
```
    docker rm -f $(docker ps -aq)
```

- To stop and delete the container 
```
    docker-compose down
```
We got lot of logs coming on the screen. To avoid it we use '-d' option.
```
    docker-compose stop
```
- To get Docker compose log info 
```
    docker-compose logs
```
- To get the docker compose contaiers
```
    docker-compose ps 
```

<Class-7>

Task:
------

Deploying Spring boot app with MySql DB using docker compose

    Spring boot app ==> 1 container 

    MySql DB ==> 1 container

>>>>

1. To run Spring Boot App. We will use below Dockerfile
```
FROM openjdk:jdk1.8

COPY target/sb-app.jar  /usr/local/sb-app.jar

WORKDIR /usr/local/

EXPOSE 8080

ENTRYPOINT ["java", "-jar", "sb-app.jar"]
```

2. If we are using MySQL DB in Spring Boot App then we need to MySQL DB in Container.

So here we need two containers. i.e Spring boot container and MySql DB container.

In future, we may have multiple containers. So, managing multiple container manually is a difficult process. 

Note: Instead of managing two containers separatley we can use Docker Compose.

Docker Compose Configuration :
```
    docker-compose.yml 
```
```
version : '3'

services :

  boot-app:                                    # boot app as one container 
	image: sb-rest-api
	ports:
	- "8080" : 8080
	depends_on:
	- mysql-db
 
  mysql-db:                                    #mysql-db as another container
	image: mysql:8
	environment:
	- MYSQL_ROOT_PASSWORD  = root       #we can set any password
	- MYSQL_DATABASE = bootdb 
 
```
=========> Later 

# Docker Swarm

Docker swarm is an Orchestration tool provided by Docker software.

Orchestaration means managing Processes/Containers.

It is a group of services that runs the docker application.

it is used to manage the containers on multiple servers.

This can be implemented by the cluster.

All the activities of the cluster are controlled by docker swarm manager and the machines that have joined in cluster is called swarm workers.

In Simple, 

Docker swarm is used to maintain the multiple containers inside one service.

Each container having one service.

<Swarm Image FLM>

Docker swarm is used to setup Docker Cluster (Load balancing)

- Cluster means group of servers used for load balancing 

Docker swarm is embedded in Docker engine.

- No need to install docker swarm separatley. it will install with docker.

We will setup Master and Worker Nodes using docker swarm cluster.

The worker nodes are connected to the Master node.

Master will schedule the tasks(Container) and manage the nodes and node failures

Worker nodes will perform the action (Containers will run here)

Each worker node will work on an individual service for better performance

### Docker Swarm Components

- Service: Represents a part of the feature of an application.

- Task: A single part of work

- Manager: Manages the work among different nodes

- Worker: Works for a specific purpose of the service.

### Swarm Features

1. Cluster management 
2. Decentralise Design 
3. Declarative Service Model 
4. Scaling 
5. Multi Host Network
6. Service Discovery
7. Load Balancing 
8. Secure by default 
9. Rolling Updates 


### Docker-Swarm Setup 

- Create 3 Ec2 Instances (ubuntu)

Note: Enable 2377 Port for Swarm Cluster Communications

>> 1-Master Node
>> 2-Worker Nodes

- Download and Install docker in Master and Worker nodes

```
    curl -fsSL https://get.docker.com -o get-docker.sh
    sudo sh get-docker.sh
    sudo docker info  # we can see status of swarm : active
```
- Connect to Master Machine and Execute Below Command
>> Initialising Ec2 instance as Master 

```
    sudo docker swarm init --advertise-addr <Master-Private-IP>
```
Now, current node is working as Manager and one token got generated.

```
    docker swarm join --token <Token_ID> 172.76.34.3:2377
```
- To get a Generated token for adding a worker 
```
    sudo docker swarm join-token worker 
```
>> It will generate a token for workder node, Copy Token and Execute in Worker Node Ec2 Instance

If you want to Add Another Manager for High- Availability. use below command.

- Generate a token for adding a manager
```
    sudo docker swarm join-token manager
```
 
>> It will generate a token for manager node, Copy Token and Execute in another Ec2 Instance.

>>> Successfully Docker Swarm Cluster is created

- To Left from Manager node & Remove worker node from manager node
```
    docker swarm leave 
```
- List of nodes 
```
    docker node ls 
```
- To remove node 
```
    docker node rm <node ID>
```
>> Must be in stopped state
>> Delete after 10sec

====> 

`When we are Creating Multiple Master Nodes, we use Docker swarm manager quarm`

Q) What is docker swarm manager quarm ?

Ans: If we run 1 master node then we can't gaurantee High Availability for application.

Formula: (n-1)/2

If we take 2 Master Node

2-1/2 = 0.5 (It can't become master)

3-1/2 = 1 (It can be leader when the main leader is down)

Note : Always use odd number for master machines when we are using Docker swarm Cluster.

<<<====

If we use `docker run` command then our application will executed in one container.

if i run in one container. if the container fails then the application will stops.

So, i want perform Orchestration for my application.

By using Orchestration if the one container(replica) is fail and another container should start automatically 

In Docker swarm we need to deploy our application as a service.

## Docker Swarm Service

Service is collection of one or more container of same image.

There are 2 types of services in docker swarm 

1. Replica (default mode)
2. Global 

### Working with Docker service

- To run docker application as service 
`sudo docker service create --name <serviceName> -p <hostPort>:<containerPort> <ImageName>`

```
sudo docker service create --name java-web-app -p 8080:8080 ashokit/javawebapp
```
Note: By default 1 replicas will be created

>> Access the Application in Browser Using IP 

- To check the services list 
```
    sudo docker service ls 
```
- We can scale the docker service (To Increase Replicas)
```
    sudo docker service scale <serviceName>=<no.of.Replicas>
    sudo docker service scale java-web-app = 3
```
- Check docker service list `sudo docker service ls`

Here, We can see 3/3 Replicas.

- To check Service Replicas list details 
```
    sudo docker service ps <serviceName>
```
- Inspect Docker service 
```
    sudo docker service inspect --pretty <serviceName>
```
Note: Here, Inside java-web-app service 3 replicas are running

>> In one node we can run multiple replicas but load will be increased. so that's why we will destribute the load by creating multiple worker nodes.

Q) what heppens if the node got failed/stopped ?

- Go to any Worker node and Leave From Swarm Cluster/Master Node 

```
    sudo docker swarm leave

    sudo docker service ls 

    sudo docker service ps <java-web-app>
```
Here, Automatically 4th replicas got started.

Conclution:
-----------
- Can we say that Node failure handled by Swarm Cluster 

- Can we say Swarm is managing Docker Cluster 


Q) Create a docker service with replicas (Container)

```
docker service create --name <serviceName> --replicas 2 --publish 80:80 <imageName>
```
- List of Docker Swarm Commands `sudo docker swarm --help`

- To Stop/Remove docker service Application `sudo docker service rm <serviceName>`

- To get a particular service containers list `docker service ps <serviceName>`

- To update the image for docker service `docker service update --image <imageName> <serviceName>`

- To get the docker service login details `docker service log <serviceName>`

#To inspect a docker service `docker service inspect <serviceName>`


## Docker-Compose Container Load Balancing Concept 

<FLM Video -9>

Multiple Container in Single Server we use Docker-Compose 

- Install docker in instance 

- lets assume 2 services 
```
mkdir swiggy zomato 
```
- Go to Swiggy and Create a Docker file  
```
    cd swiggy     # service 1
    vim Dockerfile 
```
```
FROM nginx 
COPY . /usr/share/nginx/html/
```
:wq

- Create index.html file with code `vim index.html` 
```	
    <h1> This is app1 </h1>
```
:wq

- Now Build the image `$ docker build -t image1 .`

cd ..

Now, Go To another service and Create Dockerfile
```
cd zomato           # service-2
vim Dockerfile 
```
```
FROM nginx 
COPY . /usr/share/nginx/html/
```
:wq
```
vim index.html 
```
```	
    <h1> This is app2 </h1>
```
:wq

- Now Build the image `$ docker build -t image2 .`

cd ..

We have 2 images.

We need to configure the balancing in nginx 

$ mkdir nginx # Creating another service for Load balancing 

$ cd nginx 

$ vim nginx.conf

```
upstream loadbalancer {
		server 172.17.0.1:5000 weight=6; #60% load 
		server 172.17.0.1:5001 weight=4; #40% load
}

server {
		location / {
				proxy_pass http://loadbalancer;
		}}
```
:wq

$ vim Dockerfile 

```
    FROM nginx 
    RUN rm /etc/nginx/conf.d/default.conf   # To remove default nginx config file
    COPY nginx.conf /etc/nginx/conf.d/default.conf # Copy our nginx config file
```
:wq

$ cd ..

Now, Create Docker compose file 

Install docker-compose 

$ vim docker-compose.yml 

```
version: "3"
services:
	swiggy:
		image: image1
		ports:
			- "5000:80"

	zomato:
		image: image2
		ports:
			- "5001:80"

	nginx:
		build: ./nginx
		ports:
			- "8080:80"
		depends_on:
			- swiggy 
			- zomato 
```
:wq

$ docker-compose up -d

$ docker ps # All container up state 

Now access application using instance public_id:8080

If you refresh, The request will be switched one after another.

Task: add another service and access in browser ex: uber 

		

----------------------------


## Docker Commands:

- How to change Docker file name 
 
```
    mv Dockerfile Dockerfile_one
```
- Creating Docker image using Dockerfile_one
```
    docker build -f Dockerfile_one -t image2 .
```
Here, `-f `: file name | `-t` : image name 

--------------------


`Image:` image is a package which contains the application along with required dependencies (code, softwares, libraries,... )to run the application  


Creating container nothing but application execution.





