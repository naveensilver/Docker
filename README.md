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

## Virtualisation :

# 
# Virtualisation And Containerisation - Architecture 

# Docker 

# Before Docker & After Docker 

# Docker Architecture 

# Image And Containers

#
