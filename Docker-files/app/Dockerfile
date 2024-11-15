FROM maven:eclipse-temurin:21-jdk-jammy AS BUILD_IMAGE
RUN git clone https://github.com/Fazakarim007/vprofile-project.git
RUN cd vprofile-project && git checkout containers && mvn install

FROM tomcat:10-jdk.21
RUN rm -rf /usr/local/tomcat/webapp/*
COPY --from=BUILD_IMAGE vprofile-project/target/vprofile-v2.war /usr/local/tomcat/webapp/ROOT.war

EXPOSE 8080
CMD [ "catalina.sh", "run" ]