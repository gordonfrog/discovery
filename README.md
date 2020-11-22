# Discovery Micro

## App/Dev

**microservices with Go, Spring and RaspPi**


Run jar from HOST

```
mvn clean install
java -jar target/discovery.jar
```
http://localhost:8761/

```
git add .
git commit -m "dockerized"
git push -u origin master
```

### Dockerize

```
git pull
```

Run from RasPI

```
mvn clean install
mvn clean package docker:build -DskipTests
docker images
docker ps
docker run -p 8761:8761 xdevices/discovery
```

```
docker stats
```

Access from anywhere:

http://pf4devicesdev1.local:8761/

### Jenkins on RasPi

Installing Jenkins key:

wget -q -O - https://jenkins-ci.org/debian/jenkins-ci.org.key | sudo apt-key add -

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys FCEF32E745F2C3D5

adding Jenkins to sources list:

sudo sh -c 'echo deb http://pkg.jenkins-ci.org/debian binary/ > /etc/apt/sources.list.d/jenkins.list'

updating package manager:

sudo apt-get update

installing jenkins:

sudo apt-get install jenkins -y

checking if Jenkins service is running:

systemctl status jenkins.service

http://pf4devicesdev1.local:8080
 
configuring Jenkins:

sudo cat /var/lib/jenkins/secrets/initialAdminPassword

Adding Jenkins to docker:

sudo gpasswd -a jenkins docker

stopping Jenkins: 

service jenkins stop

systemctl status jenkins.service

restarting RasPi:

sudo shutdown -r -t -f now

#### build discover build

create project - new item - discovery build - free style project

source code mgmt - git - https://github.com/gordonfrog/discovery.git

credentials - username/pass - add - select

build - add build step - execute shell - 

mvn clean package docker:build -DskipTests

apply/save

dashboard - discovery build - configure

ssh pi@pf4devicesde1.local

sudo gpasswd -a jenkins docker

dashboard - manage jenkins - shutdown

service jenkins stop

systemctl status jenkins.service

restarting RasPi:

sudo shutdown -r -t -f now

ssh pi@pf4devicesde1.local

http://pf4devicesdev1.local:8080/ - dashboard - discovery build - build now

console output

#### run container

dashboard - new item - freestyle project - start containers

this project is parameterized - add parameter - string parameter

PORTS

add parameter - string parameter

IMAGE_NAME

build - execute shell

docker run -d -p ${PORTS} ${IMAGE_NAME}

apply/save

dashboard - start containers - build with parameters

PORTS: 8761:8761

IMAGE_NAME: xdevices/discovery

Build

docker container ls

docker container stop 2612f90b5a70

docker container ls

http://pf4devicesdev1.local:8761/

dashboard - start containers - build with parameters

PORTS: 8761:8761

IMAGE_NAME: xdevices/discovery

Build

docker container ls

docker logs -f fc7748870dba

http://pf4devicesdev1.local:8761/

#### stop container

docker container ls

docker stats

docker container ls -f ancestor=xdevices/discovery -q

dashboard - new item - stop containers - freestyle project

this project is parameterized - add parameter - string parameter

IMAGE_NAME

build - add build step - execute shell - 

docker container stop ${docker container ls -f ancestor=${IMAGE_NAME} -q}

apply/save

build with parameters -

IMAGE_NAME: xdevices/discovery

Build

docker container ls




