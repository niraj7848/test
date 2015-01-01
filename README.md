# Read Me!!!

## Creating environment for development

Below are components and the steps to build the development environment for "Infra Admin Server". Infra Admin Server has following two major components,

* Front End Server: Taking request for creating/updating/deleting stack over http/https protocol
* Provisioning Server: Processing request for creating/updating/deleting stack
 

### Prerequisites and Common dependency for both components
1. JDK Version: 1.7
2. Gradle Version: 1.12
3. RabbitMQ
4. External Libraries: should be placed in the libs folder
  1. IAS_CommonModel-0.0.3.jar
  2. queue-api-1.1.2.jar
5. 

### Dependency for Front End Server
1. application.properties (src/main/resources)
2. defaultConfig.properties (src/main/resources)
3. amqp_constants.properties (/opt/interdigital/configurations/rrm/ folder)

### Dependency for Provisioning Server
1. application.properties (src/main/resources)
2. defaultConfig.properties (src/main/resources)
3. chefserverconfig.properties (/opt/interdigital/configurations/chefserver/ folder)
4. amqp_constants.properties (/opt/interdigital/configurations/rrm/ folder)
5. admin.pem (/opt/interdigital/configurations/chefserver/ folder)
6. chef-validator.pem (/opt/interdigital/configurations/chefserver/ folder)
7. rackspace-credentials.properties (src/main/resources)
8. frontend_user_data.yaml (src/main/resources)
9. mongo_user_data.yaml (src/main/resources)
10. rabbit_user_data.yaml (src/main/resources)
11. rrm_user_data.yaml (src/main/resources)

### Building the project
#### Using Command Line:
 First go to the project folder (E.g. /home/niraj/infraadminserver/IAS_ProviosingServer) where build.gradle is placed   and run following command
 
 `gradle build -x test`
 
#### Through Eclipse:
 1. Right click on the project and go to "Run As -> Gradle build..."
 2. Type command ":clean :build" on the window.
 3. Go to argument window and specify "-x text" as program argument and then Click on "Apply" button.
 4. And Click on "Run" button to compile and make war file.

### Running the project
#### Using Command Line:
 First go to  
