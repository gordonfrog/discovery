FROM balenalib/raspberrypi3-debian-openjdk:8-jdk-build-20190612
RUN mkdir -p /usr/local/discovery
ADD @project.build.finalName@.jar /usr/local/discovery/
ADD run.sh run.sh
RUN chmod +x run.sh
CMD ./run.sh
