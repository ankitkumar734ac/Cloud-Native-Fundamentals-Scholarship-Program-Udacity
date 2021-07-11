# Cloud-Native-Fundamentals-Scholarship-Program-Udacity
     Monolith: application design where all application tiers are managed as a single unit
     Microservice: application design where application tiers are managed as independent, smaller units

# Introduction to Cloud-Native
Cloud-native refers to the set of practices that empowers an organization to build and manage applications at scale. They can achieve this goal by using private, hybrid, or public cloud providers. In addition to scale, an organization needs to be agile in integrating customer feedback and adapting to the surrounding technology ecosystem.

Containers are closely associated with cloud-native terminology. Containers are used to run a single application with all required dependencies. The main characteristics of containers are easy to manage, deploy, and fast to recover. As such, often, a microservice-based architecture is chosen in tandem with cloud-native tooling. Microservices are used to manage and configure a collection of small, independent services that can be easily packaged and executed within a container.

# CNCF and Cloud-Native Tooling
Kubernetes had its first initial release in 2014 and it derives from Borg, a Google open-source container orchestrator. Currently, Kubernetes is part of CNCF or Cloud Native Computing Foundation. CNCF was founded in 2015, and it provides a vendor-neutral home to open-source projects such as Kubernetes, Prometheus, ETCD, Envoy, and many more.

Overall, Kubernetes is a container orchestrator that is capable to solutionize the integration of the following functionalities:
+ Runtime
+ Networking
+ Storage
+ Service Mesh
+ Logs and metrics
+ Tracing
# Stakeholders
An engineering team can use cloud-native tooling to enable quick delivery of value to customers and easily extend to new features and technologies. These are the main reasons why an organization needs to adopt cloud-native technologies. However, when trialing cloud-native tooling, there are two main perspectives to address: business and technical stakeholders.

From a business perspective, the adoption of cloud-native tooling represents:
+ Agility - perform strategic transformations
+ Growth - quickly iterate on customer feedback
+ Service availability - ensures the product is available to customers 24/7
From a technical perspective, the adoption of cloud-native tooling represents:
+ Automation - release a service without human intervention
+ Orchestration - introduce a container orchestrator to manage thousands of services with minimal effort
+ Observability - ability to independently troubleshoot and debug each component

# Design Considerations for Cloud-Native Applications
When building an application it is important to allocate time for context discovery. This includes listing all necessary functionalities of the application and enumerating any resources that can enable its buildout. This phase sets the fundamentals of the project. If properly implemented, it can enable the creation of services that are scalable, resilient, and extensible.

The first step in the context discovery process is to list the functional requirements, or what application capabilities should deliver to the end-users. For example, a good starting point is to expand on the following:
+ Stakeholders
+ Functionalities
+ End users
+ Input and output process
+ Engineering teams
The second step is to enumerate the available resources that facilitates the implementation of the project. For example, a good starting point is to list available:
+ Engineering resources
+ Financial resources
+ Timeframes
+ Internal knowledge
Having a good understanding of functional requirements and available resources can lead to a simpler choice between monolithic and microservice-based architectures.

# Monoliths and Microservices
Prior to an organization delivers a product, the engineering team needs to decide on the most suitable application architecture. In most of the cases 2 distinct models are referenced: monoliths and microservices. Regardless of the adopted structure, the main goal is to design an application that delivers value to customers and can be easily adjusted to accommodate new functionalities.

Also, each architecture encapsulates the 3 main tires of an application:
+ UI (User Interface) - handles HTTP requests from the users and returns a response
+ Business logic - contained the code that provides a service to the users
+ Data layer - implements access and storage of data objects
# Monoliths
In a monolithic architecture, application tiers can be described as:
+ part of the same unit
+ managed in a single repository
+ sharing existing resources (e.g. CPU and memory)
+ developed in one programming language
+ released using a single binary
<img width="221" alt="screenshot-2020-12-18-at-21 57 06 (1)" src="https://user-images.githubusercontent.com/71343747/123580484-8e58a480-d7f7-11eb-8122-2a7c93ef4975.png">
# Microservices
In a microservice architecture, application tiers are managed independently, as different units. Each unit has the following characteristics:
+ managed in a separate repository
+ own allocated resources (e.g. CPU and memory)
+ well-defined API (Application Programming Interface) for connection to other units
+ implemented using the programming language of choice
+ released using its own binary
<img width="435" alt="screenshot-2020-12-18-at-22 01 07" src="https://user-images.githubusercontent.com/71343747/123580522-a5979200-d7f7-11eb-8669-642a562a97d0.png">

  ### New terms
     Monolith: application design where all application tiers are managed as a single unit
     Microservice: application design where application tiers are managed as independent, smaller units
     
     
 
 # What’s the Difference Between Monolith and Microservices?
 
 
 
 
 
 
 
 
 
 # Trade-offs for Monoliths and Microservices
 An application can be designed using both, monolithic or microservice-based architectures. Each architecture has a set of trade-offs, that need to be thoroughly examined before deciding on the final structure of the application. These trade-offs cover development complexity, scalability, time to deploy, flexibility, operational cost, and reliability. Let's examine each trade-off in more detail!
## Development Complexity
Development complexity represents the effort required to deploy and manage an application.
+ Monoliths - one programming language; one repository; enables sequential development
+ Microservice - multiple programming languages; multiple repositories; enables concurrent development
### Scalability
Scalability captures how an application is able to scales up and down, based on the incoming traffic.
+ Monoliths - replication of the entire stack; hence it's heavy on resource consumption
+ Microservice - replication of a single unit, providing on-demand consumption of resources
### Time to Deploy
Time to deploy encapsulates the build of a delivery pipeline that is used to ship features.
+ Monoliths - one delivery pipeline that deploys the entire stack; more risk with each deployment leading to a lower velocity rate
+ Microservice - multiple delivery pipelines that deploy separate units; less risk with each deployment leading to a higher feature development rate
## Flexibility
Flexibility implies the ability to adapt to new technologies and introduce new functionalities.
+ Monoliths - low rate, since the entire application stack might need restructuring to incorporate new functionalities
+ Microservice - high rate, since changing an independent unit is straightforward
### Operational Cost
Operational cost represents the cost of necessary resources to release a product.
+ Monoliths - low initial cost, since one code base and one pipeline should be managed. However, the cost increases exponentially when the application needs to operate at scale.
+ Microservice - high initial cost, since multiple repositories and pipelines require management. However, at scale, the cost remains proportional to the consumed resources at that point in time.
### Reliability
Reliability captures practices for an application to recover from failure and tools to monitor an application.
+ Monoliths - in a failure scenario, the entire stack needs to be recovered. Also, the visibility into each functionality is low, since all the logs and metrics are aggregated together.
+ Microservice - in a failure scenario, only the failed unit needs to be recovered. Also, there is high visibility into the logs and metrics for each unit.
 
 # Edge Case: Amorphous Applications
 Some of the most encountered operations in the maintenance phase are listed below:
<img width="709" alt="screenshot-2020-12-19-at-13 28 38" src="https://user-images.githubusercontent.com/71343747/123729065-02f01980-d8b2-11eb-87d4-939d48e583ce.png">
+ A split operation - is applied if a service covers too many functionalities and it's complex to manage. Having smaller, manageable units is preferred in this context.
+ A merge operation- is applied if units are too granular or perform closely interlinked operations, and it provides a development advantage to merge these together. For example, merging 2 separate services for log output and log format in a single service.
+ A replace operation - is adopted when a more efficient implementation is identified for a service. For example, rewriting a Java service in Go, to optimize the overall execution time.
+ A stale operation - is performed for services that are no longer providing any business value, and should be archived or deprecated. For example, services that were used to perform a one-off migration process.
 Performing any of these operations increases the longevity and continuity of a project. Overall, the end goal is to ensure the application is providing value to customers and is easy to manage by the engineering team. But more importantly, it can be observed that the structure of a project is not static. It amorphous and it evolves based on new requirements and customer feedback.
 
 # Transitions from VMs to Containers
 <img width="388" alt="screenshot-2020-12-19-at-17 29 28" src="https://user-images.githubusercontent.com/71343747/124047957-eb8c6a00-da32-11eb-9245-79655a77c76e.png">

# VMs
In the past years, VMs (Virtual Machines) were the main mechanism to host an application. VMs encapsulate the code, configuration files, and dependencies necessary to execute the application.
In essence, a VM is composed of an operating system (OS) with a set of pre-installed libraries and packages. During execution, an application utilizes an OS filesystem, resources, and packages.

A set of VMs is managed through a hypervisor. A hypervisor provides the virtualization of the infrastructure which is composed of physical servers. As a result, a hypervisor is capable of creating, configuring, and managing multiple VMs on the available servers. For example, we are able to running applications A, B, and C on 3 separate VMs.
 The utilization of VMs introduced standardization in infrastructure provisioning, in association with efficient use of available infrastructure. Instead of running an application per server, a hypervisor enables multiple VMs to run at the same time to host multiple applications. However, there is one downside to this mechanism: it is not efficient enough. For example, applications A, B, and C uses the same Operating System. Replicating an OS consumes a lot of resources, and the more applications we run the more space we allocate to the replication of the operating systems alone.

# Containers
<img width="702" alt="screenshot-2020-12-19-at-22 10 50" src="https://user-images.githubusercontent.com/71343747/124048161-5178f180-da33-11eb-91f9-ede640aadb5e.png">
There was a clear need to optimize the usage of the available infrastructure. As a result, the virtualization of the Operating System was introduced. This prompted the appearance of containers, which represent the bare minimum an application requires for a successful execution e.g. code, config files, and dependencies. By default, there is a better usage of available infrastructure.

Multiple VMs on a hypervisor are replaced by multiple containers running on a single host operating system. The processes in the containers are completely isolated but are able to access the OS filesystem, resources, and packages. The creation and execution of containers is delegated to a container management tool, such as Docker.

The appearance of containers is unlocked by OS-level virtualization and as a result, multiple applications can run on the same OS. By nature, containers are lightweight, as these encapsulate only the application code and essential dependencies. Consequently, there is a better usage of available infrastructure and a more efficient pathway to release a product to consumers.
# Docker for Application Packaging
To containerize an application using Docker, 3 main components are distinguished: Dockerfiles, Docker images, and Docker registries

## Dockerfile
A Dockerfile is a set of instructions used to create a Docker image. Each instruction is an operation used to package the application, such as installing dependencies, compile the code, or impersonate a specific user. A Docker image is composed of multiple layers, and each layer is represented by an instruction in the Dockerfile. All layers are cached and if an instruction is modified, then during the build process only the changed layer will be rebuild. As a result, building a Docker image using a Dockerfile is a lightweight and quick process.
To construct a Dockerfile, it is necessary to use the pre-defined instructions, such as:
```sh
FROM -  to set the base image
RUN - to execute a command
COPY & ADD  - to copy files from host to the container
CMD - to set the default command to execute when the container starts
EXPOSE - to expose an application port 
```
Below is an example of a Dockerfile that targets to package a Python hello-world application:
```sh
# set the base image. Since we're running 
# a Python application a Python base image is used
FROM python:3.8
# set a key-value label for the Docker image
LABEL maintainer="Katie Gamanji"
# copy files from the host to the container filesystem. 
# For example, all the files in the current directory
# to the  `/app` directory in the container
COPY . /app
#  defines the working directory within the container
WORKDIR /app
# run commands within the container. 
# For example, invoke a pip command 
# to install dependencies defined in the requirements.txt file. 
RUN pip install -r requirements.txt
# provide a command to run on container start. 
# For example, start the `app.py` application.
CMD [ "python", "app.py" ]
```

Once a Dockerfile is constructed, these instructions are used to build a Docker image. A Docker image is a read-only template that enables the creation of a runnable instance of an application. In a nutshell, a Docker image provides the execution environment for an application, including any essential code, config files, and dependencies.

A Docker image can be built from an existing Dockerfile using the<b> docker build</b> command. Below is the syntax for this command:
```sh
# build an image
# OPTIONS - optional;  define extra configuration
# PATH - required;  sets the location of the Dockefile and  any referenced files 
docker build [OPTIONS] PATH

# Where OPTIONS can be:
-t, --tag - set the name and tag of the image
-f, --file - set the name of the Dockerfile
--build-arg - set build-time variables

# Find all valid options for this command 
docker build --help
```
 For example, to build the image of the Python hello-world application from the Dockerfile, the following command can be used:
 ```sh
     # build an image using the Dockerfile from the current directory
docker build -t python-helloworld .

# build an image using the Dockerfile from the `lesson1/python-app` directory
docker build -t python-helloworld lesson1/python-app
```
Before distributing the Docker image to a wider audience, it is paramount to test it locally and verify if it meets the expected behavior. To create a container using an available Docker image, the <b>docker run</b> command is available. Below is the syntax for this command:
```sh
# execute an image
# OPTIONS - optional;  define extra configuration
# IMAGE -  required; provides the name of the image to be executed
# COMMAND and ARGS - optional; instruct the container to run specific commands when it starts 
docker run [OPTIONS] IMAGE [COMMAND] [ARG...]

# Where OPTIONS can be:
-d, --detach - run in the background 
-p, --publish - expose container port to host
-it - start an interactive shell

# Find all valid options for this command 
docker run --help
```
Note: To access the application in a browser, we need to bind the Docker container port to a port on the host or local machine. In this case, 5111 is the host port that we use to access the application e.g. http://127.0.0.1:5111/. The 5000 is the container port that the application is listening to for incoming requests.
```sh
# run the `python-helloworld` image, in detached mode and expose it on port `5111`
docker run -d -p 5111:5000 python-helloworld``
```
To retrieve the Docker container logs use the docker logs {{ CONTAINER_ID }} command. For example:

docker logs 95173091eb5e

 ```sh
 ## Example output from a Flask application
 * Serving Flask app "app" (lazy loading)
 * Environment: production
   WARNING: This is a development server. Do not use it in a production deployment.
   Use a production WSGI server instead.
 * Debug mode: off     
 ```  
 # Docker Registry
 The last step in packaging an application using Docker is to store and distribute it. So far, we have built and tested an image on the local machine, which does not ensure that other engineers have access to it. As a result, the image needs to be pushed to a public Docker image registry, such as DockerHub, Harbor, Google Container Registry, and many more. However, there might be cases where an image should be private and only available to trusted parties. As a result, a team can host private image registries, which provides full control over who can access and execute the image.

Before pushing an image to a Docker registry, it is highly recommended to tag it first. During the build stage, if a tag is not provided (via the -t or --tag flag), then the image would be allocated an ID, which does not have a human-readable format (e.g. 0e5574283393). On the other side, a defined tag is easily scalable by the human eye, as it is composed of a registry repository, image name, and version. Also, a tag provides version control over application releases, as a new tag would indicate a new release.

To tag an existing image on the local machine, the docker tag command is available. Below is the syntax for this command:
 ```sh
# tag an image
# SOURCE_IMAGE[:TAG]  - required and the tag is optional; define the name of an image on the current machine 
# TARGET_IMAGE[:TAG] -  required and the tag is optional; define the repository, name, and version of an image
docker tag SOURCE_IMAGE[:TAG] TARGET_IMAGE[:TAG]
```
For example, to tag the Python hello-world application, to be pushed to a repository in DockerHub, the following command can be used:
```sh
# tag the `python-helloworld` image, to be pushed 
# in the `pixelpotato` repository, with the `python-helloworld` image name
# and version `v1.0.0`
docker tag python-helloworld pixelpotato/python-helloworld:v1.0.0
```
Once the image is tagged, the final step is to push the image to a registry. For this purpose, the docker push command can be used. Below is the syntax for this command:
```sh
# push an image to a registry 
# NAME[:TAG] - required and the tag is optional; name, set the image name to be pushed to the registry
docker push NAME[:TAG]
```
For example, to push the Python hello-world application to DockerHub, the following command can be used:
```sh
# push the `python-helloworld` application in version v1.0.0 
# to the `pixelpotato` repository in DockerHub
docker push pixelpotato/python-helloworld:v1.0.0
```
# New terms
<b>Docker file</b> - set of instructions used to create a Docker image
<b>Docker image</b> - a read-only template used to spin up a runnable instance of an application
<b>Docker registry </b>- a central mechanism to store and distribute Docker images
 # Summary
Docker provides a rich set of actions that can be used to build, run, tag, and push images. Below is a list of handy Docker commands used in practice.

Note: In the following commands the following arguments are used:

+ OPTIONS - define extra configuration through flags
+ IMAGE - sets the name of the image
+ NAME- set the name of the image
+ COMMAND and ARG - instruct the container to run specific commands associated with a set of arguments
## Build Images
To build an image, use the following command, where PATH sets the location of the Dockerfile and referenced application files:
```sh
 docker build [OPTIONS] PATH
```
## Run Images
To run an image, use the following command:
```sh
docker run [OPTIONS] IMAGE [COMMAND] [ARG...]
```
## Get Logs
To get the logs from a Docker container, use the following command:
```sh
docker logs CONTAINER_ID
 ```
Where the CONTAINER_ID is the ID of the Docker container that runs an application.

## List Images
To list all available images, use the following command:
```sh
docker images
 ```
### List Containers
To list all running containers, use the following command:
```sh
docker ps
 ```
## Tag Images
To tag an image, use the following command, where SOURCE_IMAGE defines the name of an image on the current machine and TARGET_IMAGE defines the repository, name, and version of an image:
```sh
docker tag SOURCE_IMAGE[:TAG] TARGET_IMAGE[:TAG]
```
## Login to DockerHub
To login into DockerHub, use the following command:
```sh
docker login
```
## Push Images
To push an image to DockerHub, use the following command:
```sh
docker push NAME[:TAG]
```
## Pull Images
To pull an image from DockerHub, use the following command:
```sh
docker pull NAME[:TAG] 
```

 
  
 
  
  
     
 
     
     
