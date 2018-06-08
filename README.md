# mule4-skeleton-jms-producer-consumer
This is a Mule 4.1 example of a jms producer and consumer flows using ActiveMQ. 

Note, the scope features of minimal-logging are not displayed correctly by Studio 7.1 or 7.2. Support for displaying SDK connector scopes is expected in Studio 7.3.

## Uses

The project contains examples using:

* JMS Connector
* The minimal-logging connector, 
* The secure property connector (formally called the secure-property-placeholder),
* Maven deployment using the mule-maven-plugin descriptor,
* Using the Maven filter "feature" to add Maven properties to code in files stored in the resources-filtered directory...specifically, updating the api.base and log4j2 configurations with the project name.

## Purpose

This project is an example that can be deployed and will run when properly configured. 

### Configuration Properties

The configuration properties are stored in the src/main/resources-filtered/mule4-skeleton-proxy-${mule.env}.yaml file:

* my.client-id is the client id this API uses to call other APIs
* my.client-secret is the client secret registered for this API to use for calling other APIs
* message.queue is the name of the JMS queue to use


## Runtime properties

The properties mule.env and mule.key need to be set in the Mule runtime in order for the property configurations to be located. Additionally, if the Mule runtime is not configured to connect to API Manager, the API will be disabled (by default).

For Studio, add the following VM command line values when running the API:

 -Danypoint.platform.gatekeeper=disabled -Dmule.env=local -Dmule.key=Mulesoft12345678

## Maven Settingss

The Mule deployment assumes that certain deployment properties will come from profiles specified when the mvn command is executed. An example-settings.xml is provided as a reference
for creating your own settings.xml file. This is a standard feature of Maven and is described in its online documentation. Once the settings.xml file has been created, export a u and a p shell environment variables containing your Anypoint user name and password. Then use this maven command to deploy the API project:

```
mvn clean install deploy -Denv=xxx -DmuleDeploy
```
Replacing the xxx's with the appropriate values.

