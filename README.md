# Cloud-Native-Fundamentals-Scholarship-Program-Udacity


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
 
