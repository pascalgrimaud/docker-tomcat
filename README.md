[![logo](https://raw.githubusercontent.com/pascalgrimaud/docker-tomcat/master/tomcat.png)]
(https://tomcat.apache.org/)

[![Circle CI](https://circleci.com/gh/pascalgrimaud/docker-tomcat.svg?style=shield)]
(https://circleci.com/gh/pascalgrimaud/docker-tomcat)



# Information

The base docker image :

  * [pascalgrimaud/ubuntu](https://registry.hub.docker.com/u/pascalgrimaud/ubuntu/)

The GitHub project :

  * [pascalgrimaud/docker-tomcat](https://github.com/pascalgrimaud/docker-tomcat/)


# Installation

You can clone this project and build with docker command :

```
git clone https://github.com/pascalgrimaud/docker-tomcat.git
cd docker-tomcat
docker build -t pascalgrimaud/tomcat:8.0.23 .
```

You can build directly from the [GitHub project](https://github.com/pascalgrimaud/docker-tomcat/) :

```
docker build -t pascalgrimaud/tomcat:8.0.23 github.com/pascalgrimaud/docker-tomcat.git
```



# Help

To display usage :

```
docker run pascalgrimaud/tomcat:8.0.23 /help
```



# Usage

Quick start with binding to port 8080 and random password :

```
docker run -d -p 8080:8080 pascalgrimaud/tomcat:8.0.23
```

To get the password :

```
docker logs <container id>
```

Start and set a specific password for Tomcat admin user :

```
docker run -d -p 8080:8080 -e TOMCAT_PASS="pass" pascalgrimaud/tomcat:8.0.23
```


If you forget the admin password, delete the file .password and restart the container :

```
docker exec -it <container id> rm /.password
```


# Deploy a war

To deploy a specific file.war, you need to make another container.
Create a new directory and put your file.war.
Then, create a new Dockerfile :

```
FROM pascalgrimaud/tomcat:8.0.23
ADD file.war /opt/apache-tomcat-8.0.23/webapps/file.war
```
