# Read Me!!!

## Setting up environment for development

Below are components and the steps to build the development environment for "Infra Admin Server". Infra Admin Server has following two major components,

* Front End Server: Taking request for creating/updating/deleting stack over http/https protocol
* Provisioning Server: Processing request for creating/updating/deleting stack
 

### Prerequisites and Common dependencies for both components
1. JDK Version: 1.7
2. Gradle Version: 1.12
3. RabbitMQ
4. External Libraries: should be placed in the libs folder
  1. IAS_CommonModel-0.0.3.jar
  2. queue-api-1.1.2.jar

### Dependencies for Front End Server
1. application.properties (src/main/resources)
2. defaultConfig.properties (src/main/resources)
3. amqp_constants.properties (/opt/interdigital/configurations/rrm/ folder)

### Dependencies for Provisioning Server
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
12. MongoDB Version: 2.6.3 (Source compiled for SSL)

### Building the project
#### Using Command Line:
 First go to the project folder (E.g. /home/dennis/infraadminserver/IAS_ProviosingServer) where build.gradle is placed  and run the following command
 
 `gradle build` 
 `gradle build -x test` (If running tests to be skipped. Not Recommended)
 
#### Through Eclipse:
 1. Right click on the project and go to "Run As" and the Click on "Gradle build..."
 2. Type command ":clean :build" on the Task editor window.
 3. Click on "Arguments" tab and specify "-x text" as program argument in the "Program Args" window and then Click on      "Apply" button.
 4. And Click on "Run" button to compile and make war file.

### Running the project
#### Using Command Line:
 First go to "build\libs" folder inside project folder (E.g. /home/dennis/infraadminserver/IAS_ProviosingServer) and    run the following command
 
 `java -jar <Name of the Jar>`
 
#### Through Eclipse:
 1. Right click on the project and go to "Run As" and the Click on "Java Application".
 2. Search for "Application-com.interdigital.infraserver.frontend" or "Application-com.interdigital.infraserver.provisioning".
 3. And Click on "OK".

### Enabling and Disabling Https for Front End Server.

#### Enable Https
 To enable https for Front End Server, we need to provide information about SSL and then Spring Boot will automatically  configure Tomcat for https. We need to include following lines in the file "application.properties".

server.port=8443

server.ssl.key-alias=frontendkey

server.ssl.key-password=interdigital

server.ssl.key-store=/opt/interdigital/certificates/frontend/server.jks

server.ssl.key-store-password=interdigital

server.ssl.key-store-type=JKS 
 

For generating the file "server.jks" and copying the file to predefined location, run following commands

`keytool -genkeypair -alias frontendkey -keyalg RSA -keysize 2048 -dname "CN=Server,OU=Application Development,O=Home,L=Auckland,S=AK,C=NZ" -keypass "interdigital" -storepass "interdigital" -keystore server.jks`

`cp server.jks /opt/interdigital/certificates/frontend`
 
#### Disable Https
 For disabling https comment out all the lines in the "application.properties" file, which we included for enabling     Https and include the following line
 
 server.port=8080
 
 
