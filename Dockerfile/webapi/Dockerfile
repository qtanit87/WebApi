#pull rokylinux with specific version (cannot download latest image at the moment)
FROM rockylinux:9.1.20230215
#install java jdk
RUN dnf install java-11-openjdk-devel -y
#install git
RUN dnf install git -y
#install maven
RUN dnf install maven -y
#install wget
RUN dnf install wget -y
#install unzip
RUN dnf install unzip -y
#change workdir to /wepapi
WORKDIR /webapi
#download tomcat package
RUN wget https://dlcdn.apache.org/tomcat/tomcat-8/v8.5.87/bin/apache-tomcat-8.5.87.zip
#unzip tomcat package
RUN unzip apache-tomcat-8.5.87.zip
#grant execution permission on tomcat directory
RUN chmod -R +x apache-tomcat-8.5.87
#clone Web Api source code
RUN git clone https://github.com/qtanit87/WebApi.git
#change workdir to Web Api directory
WORKDIR /webapi/WebApi
#use maven to compile code
RUN mvn clean install
#copy compiled package to tomcat folder
RUN cp /webapi/WebApi/target/MyWebSite-0.0.1-SNAPSHOT.war /webapi/apache-tomcat-8.5.87/webapps
#start tomcat service
CMD ["/webapi/apache-tomcat-8.5.87/bin/catalina.sh" , "run"]