FROM openjdk:11 AS BUILD_IMAGE
RUN apt upate && apt install maven -y
RUN git clone https://github.com/manojreddy-evuri/vprofile-project.git
RUN cd vprofile-project && git checkout docker && mvn install

FROM tomact:9-jre11 
LABEL ""project""="vprofile"
LABEL "Author"="Manoj"
RUN rm -rf /usr/local/tomact/webapps/*
COPY --from=BUILD_IMAGE vprofile-project/target/vprofile-v2.war /usr/local/tomact/webapps/ROOT.var

EXPOSE 8080
CMD ["catalina.sh", "run"]
