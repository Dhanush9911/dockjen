FROM openjdk:12 AS BUILD_IMAGE
RUN apt update
RUN apt install maven -y
RUN git clone https://github.com/Dhanush9911/dockjen.git
RUN cd dockjen
RUN git checkout docker 
RUN mvn install

FROM tomcat:9-jre11

RUN rm -rf /usr/local/tomcat/webapps/*

COPY --from=BUILD_IMAGE dockjen/target/vprofile-v2.war /usr/local/tomcat/webapps/ROOT.war

EXPOSE 8080
CMD ["catalina.sh", "run"]
