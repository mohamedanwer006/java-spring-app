# Java Spring boot application

- #### A simple java application using spring boot for testing **CI/CD** pipeline.
- #### Use jenkins for automated build and deployment.
- #### Use github as source control tool.
- #### Use nexus as artifacts manager.
---
## Build artifacts and deploy to nexus with out jenkins

### Build app using maven tool
#### run on local machine
```bash
mvn install
```
#### Run app on localhost [**Test Application**](#test-the-application)

```bash
java -jar ./target/<app name>.jar
```

#### Build artifacts and deploy to nexus
#### Edit **pom.xml**

```xml
<!-- ...-->
	<groupId>com.example</groupId>
	<artifactId>demo</artifactId>
	<version>0.0.1-SNAPSHOT</version>
	<name>demo</name>
	<description>Demo project for Spring Boot</description>


	<distributionManagement>
    <repository>
        <id>nexus-repo</id>
        <url>http://20.123.134.231:8081/repository/maven-snapshots/</url>
    </repository>
	</distributionManagement>
<!-- ... -->
```
##### Create or edit ~/.m2/settings.xml
> The **id** should be the same on pom.xml and settings.xml
```xml
<settings>
<servers>
    <server>
        <id>nexus-repo</id>
        <username>mohamed</username>
        <password>123456</password>
    </server>
</servers>
</settings>
```
#### Run the following command to deploy artifacts to nexus

```bash
mvn clean package
mvn deploy
```

## Build artifacts and deploy to nexus with jenkins.

>TODO:
-----
## Build docker image from artifact (jar)

### build image
```bash
docker build . -t java-demo
```
### Run container
```bash
docker run -d -p 8080:8080 java-demo 
```

## Test the Application

- Now that the web site is running, visit http://localhost:8080/ .

- visit http://localhost:8080/hello , where you should see `Hello, World!`

- Provide a `name` query string parameter by visiting

- http://localhost:8080/hello?name=User .Notice how the message changes from "`Hello, World!`" to "`Hello, User!`":
