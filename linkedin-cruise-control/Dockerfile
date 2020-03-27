FROM openjdk:11-jdk-slim

RUN cd /home && apt update && apt install git -y && git clone https://github.com/linkedin/cruise-control.git && cd cruise-control
WORKDIR /home/cruise-control

VOLUME ["./config","./logs"]

RUN ./gradlew jar copyDependantLibs
EXPOSE 9090
ENTRYPOINT [ "./kafka-cruise-control-start.sh" ]
CMD ["config/cruisecontrol.properties"]
