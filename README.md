# Read Me!!!

## Creating environment for development

Below are components and the steps to build the development environment for "Infra Admin Server". Infra Admin Server has following two major components,

* Front End Server: Taking request for creating/updating/deleting stack over http/https protocol
* Provisioning Server: Processing request for creating/updating/deleting stack
 

### Prerequisites and Common dependency for both components
----
1. JDK Version: 1.7
2. Gradle Version: 1.12
3. MongoDB Version : 2.6.3 (source compiled for SSL)
4. RabbitMQ
5. External Libraries: should be placed in the libs folder
  1. IAS_CommonModel-0.0.3.jar
  2. queue-api-1.1.2.jar
6. 
