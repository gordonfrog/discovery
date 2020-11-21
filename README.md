# discovery

App/Dev
---

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

Dockerize

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